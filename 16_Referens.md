# C++ Havolalari (References)

**Havola (Reference)** — bu mavjud bo'lgan o'zgaruvchining **ikkinchi nomi (taxallusi / alias)**. U xotirada yangi joy egallamaydi, balki o'zi biriktirilgan asli o'zgaruvchining xotira manziliga to'g'ridan-to'g'ri ishora qiladi.

Havolani yaratish uchun o'zgaruvchi turi va nomi orasida **`&`** (ampersand) belgisidan foydalaniladi.

---

## 1. Havola Yaratish va Ishlatish

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string food = "Pizza";  // Asliy o'zgaruvchi
    string& meal = food;    // 'food' uchun 'meal' nomli havola

    // Ikkalasi ham bir xil qiymatni ko'rsatadi
    cout << "food: " << food << endl; // Pizza
    cout << "meal: " << meal << endl; // Pizza

    // Havola orqali qiymat o'zgartirilsa, asliy o'zgaruvchi ham o'zgaradi
    meal = "Burger";

    cout << "\nO'zgartirilgandan keyin:\n";
    cout << "food: " << food << endl; // Burger
    cout << "meal: " << meal << endl; // Burger

    return 0;
}

```

---

## 2. Manzil Operatori (`&` Address-of Operator)

`&` belgisi ikki xil vazifada keladi:

1. Tur yonida kelganda (`string&`): **Havola e'lon qilish**.
2. O'zgaruvchi oldida kelganda (`&food`): O'zgaruvchining **RAM (operativ xotira) dagi manzilini** olish.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string food = "Pizza";
    string& meal = food;

    // Asliy o'zgaruvchi va havolaning xotiradagi manzili BIR XIL
    cout << "food manzili: " << &food << endl; // Masalan: 0x61ff00
    cout << "meal manzili: " << &meal << endl; // Masalan: 0x61ff00

    return 0;
}

```

---

## 3. Havolalarning Qat'iy Qoidalari

1. **E'lon qilinishi bilan biriktirilishi shart:**
Havolani qiymatsiz e'lon qilib bo'lmaydi.
```cpp
int x = 10;
int& ref = x; // ✅ To'g'ri

int& ref2;    // ❌ Xatolik! (error: 'ref2' declared as reference but not initialized)

```


2. **Qayta biriktirib bo'lmaydi (Cannot be reseated):**
Havola bir marta o'zgaruvchiga bog'landimi, uni keyinchalik boshqa o'zgaruvchiga bog'lab bo'lmaydi.
```cpp
int a = 5, b = 20;
int& ref = a; // ref a ga bog'landi

ref = b; // ⚠️ Bu ref ni b ga bog'lamaydi! Bu a ning qiymatini 20 ga o'zgartiradi (a = b).

```


3. **`NULL` bo'la olmaydi:**
Havola har doim real mavjud bo'lgan xotira obyektiga ishora qilishi kerak (`nullptr` biriktirib bo'lmaydi).

---

## 4. Havolalarning Asosiy Qo'llanilishi: Funksiyaga Parametr Uzatish (Pass-by-Reference)

Dasturlashda havolalar asosan funksiyalarga argument uzatishda ishlatiladi. Bu xotiradan unumli foydalanish va asliy o'zgaruvchilar qiymatini funksiya ichida o'zgartirish imkonini beradi.

### Qiymat bo'yicha vs Havola bo'yicha uzatish:

```cpp
#include <iostream>
using namespace std;

// 1. Qiymat bo'yicha uzatish (Pass-by-Value) -> Kopiya olinadi
void updateByValue(int num) {
    num = 100;
}

// 2. Havola bo me'yorida uzatish (Pass-by-Reference) -> Asliy o'zgaruvchi ustida ishlanadi
void updateByRef(int& num) {
    num = 100;
}

int main() {
    int a = 10;
    int b = 10;

    updateByValue(a);
    cout << "a ning qiymati: " << a << endl; // 10 (O'zgarmadi)

    updateByRef(b);
    cout << "b ning qiymati: " << b << endl; // 100 (O'zgardi)

    return 0;
}

```

---

## 5. Havola (Reference) va Ko'rsatkich (Pointer) Farqi

C++ da ham **Reference**, ham **Pointer** xotira bilan ishlashga xizmat qiladi, lekin ularning sezilarli farqlari bor:

| Xususiyat | Havola (Reference) | Ko'rsatkich (Pointer) |
| --- | --- | --- |
| **Sintaksis** | `int& ref = x;` | `int* ptr = &x;` |
| **Qayta biriktirish** | Mumkin emas (doimiy bog'langan) | Boshqa manzilga o'zgarsa bo'ladi |
| **`NULL` qiymat** | Qabul qilmaydi | `nullptr` bo'lishi mumkin |
| **Xotira manzili** | O'zining alohida manzili bo'lmaydi | Alohida xotira manzili va hajmiga ega |
| **Bilvosita murojaat (Dereferencing)** | Avtomatik (`ref`) | Qo'lda bajariladi (`*ptr`) |

---

## Qisqa Xulosa

* **`&` (Reference):** O'zgaruvchiga ikkinchi nom beradi, nusxa ko'chirmaydi.
* **`&x` (Address-of):** `x` o'zgaruvchisining RAM dagi xotira manzilini qaytaradi.
* **Pass-by-Reference:** Funksiyalarda katta ma'lumotlarni (`string`, `struct`, `vector`) nusxalamasdan, tezkor va unumli qayta ishlash uchun xizmat qiladi.
