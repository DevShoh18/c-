# C++ Ko'rsatkichlari (Pointers)

**Ko'rsatkich (Pointer)** — bu boshqa o'zgaruvchining **xotira manzilini (memory address)** o'zida saqlaydigan maxsus o'zgaruvchi.

Ko'rsatkichlar C++ ning eng qudratli va muhim tushunchalaridan biri bo'lib, xotirani quyi darajada (low-level) to'g'ridan-to'g'ri va samarali boshqarish imkonini beradi.

---

## 1. Ko'rsatkich Yaratish va Sintaksisi

Ko'rsatkich e'lon qilish uchun o'zgaruvchi turi oldidan **`*`** (yulduzcha) belgisi qo'yiladi:

```cpp
tur* ko'rsatkich_nomi = &o'zgaruvchi;

```

### Kod Namunasi:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string food = "Pizza";  // Oddiy o'zgaruvchi
    string* ptr = &food;    // 'food' ning xotira manzilini saqlaydigan ko'rsatkich

    // 1. O'zgaruvchining qiymati
    cout << "food: " << food << endl;    // Natija: Pizza

    // 2. O'zgaruvchining xotiradagi manzili
    cout << "&food: " << &food << endl;  // Natija: 0x61ff00 (RAM dagi manzil)

    // 3. Ko'rsatkichda saqlanayotgan manzil
    cout << "ptr: " << ptr << endl;      // Natija: 0x61ff00 (bir xil manzil)

    return 0;
}

```

---

## 2. Dereferencing (`*` Qiymatni O'qish Operatori)

Ko'rsatkich o'zida xotira manzilini saqlaydi. Agar shu manzil ichida **qanday qiymat turganini o'qish yoki uni o'zgartirish** kerak bo'lsa, ko'rsatkich oldiga **`*`** operatori qo'yiladi. Bu jarayon **Dereferencing** deyiladi.

> **Eslatma:** `*` belgisi kontekstga qarab 2 xil ma'noni beradi:
> 1. E'lon qilishda (`string* ptr`): **Ko'rsatkich turi**.
> 2. Ishlatishda (`*ptr`): **Manzildagi qiymatni ko'rsatish (Dereference)**.
> 
> 

### Kod Namunasi:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string food = "Pizza";
    string* ptr = &food;

    // Manzilni chiqarish
    cout << "ptr (Manzil): " << ptr << endl;    // 0x61ff00

    // Manzildagi qiymatni o'qish (Dereference)
    cout << "*ptr (Qiymat): " << *ptr << endl;  // Pizza

    // Ko'rsatkich orqali asliy o'zgaruvchi qiymatini O'ZGARTIRISH
    *ptr = "Burger";

    cout << "\n*ptr = 'Burger' qilingandan keyin:\n";
    cout << "*ptr: " << *ptr << endl; // Burger
    cout << "food: " << food << endl; // Burger (asliy o'zgaruvchi ham o'zgardi!)

    return 0;
}

```

---

## 3. `nullptr` (Nol Ko me'yoridagi Ko'rsatkich)

Agar ko'rsatkich hali hech qanday xotira manziliga bog'lanmagan bo'lsa, unga **`nullptr`** (C++11 va undan yuqori) biriktirish shart. Axlat (random) xotira manziliga ishora qilib turgan ko'rsatkichdan foydalanish dastur crash bo'lishiga olib keladi.

```cpp
int* ptr = nullptr; // Xavfsiz e'lon qilish

if (ptr != nullptr) {
    cout << *ptr; // Faqat manzil mavjud bo'lsagina ishlatamiz
} else {
    cout << "Ko'rsatkich hech qanday manzilga ishora qilmayapti!";
}

```

---

## 4. Ko'rsatkichlar va Massivlar (Pointers and Arrays)

C++ da massiv nomi aslida massivning **birinchi elementiga (0-indeksga) ishora qiluvchi ko'rsatkich** hisoblanadi.

```cpp
#include <iostream>
using namespace std;

int main() {
    int myNumbers[3] = {10, 20, 30};

    // Massiv nomi 0-element manzilini beradi
    cout << "myNumbers manzili: " << myNumbers << endl;
    cout << "&myNumbers[0] manzili: " << &myNumbers[0] << endl;

    // Ko'rsatkich arifmetikasi (Pointer Arithmetic)
    cout << "0-element: " << *myNumbers << endl;       // 10
    cout << "1-element: " << *(myNumbers + 1) << endl; // 20
    cout << "2-element: " << *(myNumbers + 2) << endl; // 30

    return 0;
}

```

---

## 5. Pass-by-Pointer (Funksiyaga Ko'rsatkich Uzatish)

Funksiyalarga o'zgaruvchining manzilini uzatish orqali uning qiymatini funksiya ichida o'zgartirish mumkin:

```cpp
#include <iostream>
using namespace std;

void swapValues(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 5, y = 10;

    cout << "O'rin almashtirishdan oldin: x = " << x << ", y = " << y << endl;

    // Manzillarni uzatamiz
    swapValues(&x, &y);

    cout << "O'rin almashtirishdan keyin: x = " << x << ", y = " << y << endl;

    return 0;
}
// Natija: x = 10, y = 5

```

---

## Qisqa Xulosa

| Operator / Sintaksis | Ma'nosi | Vazifasi |
| --- | --- | --- |
| **`&x`** | Address-of | `x` o'zgaruvchisining RAM dagi manzilini oladi |
| **`int* ptr`** | Pointer Declaration | Manzil saqlovchi ko'rsatkich o'zgaruvchisi e'lon qiladi |
| **`*ptr`** | Dereference | `ptr` manzilida turgan qiymatni o'qiydi yoki o'zgartiradi |
| **`nullptr`** | Null Pointer | Ko'rsatkich bo'sh ekanligini xavfsiz bildiradi |
