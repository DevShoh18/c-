# C++ Funksiya Parametrlari va Qayta Yuklash (Parameters & Overloading)

Funksiyalar bilan ishlashda parametrlarni to'g'ri uzatish hamda bir xil nomli funksiyalarni turli ma'lumot turlariga moslashtirish (Overloading) C++ dasturlash tilining eng asosiy va muhim qoidalaridan biridir.

---

## 1. Parametr va Argument Farqi

Dasturchilar ko'pincha bu ikki tushunchani aralashtirib yuborishadi:

* **Parametr (Parameter):** Funksiya e'lon qilinayotganda qavs `()` ichida ko'rsatiladigan o'zgaruvchidir.
* **Argument (Argument):** Funksiya chaqirilayotganda parametrlarga uzatiladigan **haqiqiy qiymat**.

```cpp
void greet(string name) { // 'name' — PARAMETR
    cout << "Salom, " << name;
}

int main() {
    greet("Shoxboz");    // "Shoxboz" — ARGUMENT
    return 0;
}

```

---

## 2. Parametrlarni Uzatish Usullari

C++ da funksiyalarga ma'lumot uzatishning 3 xil asosiy usuli mavjud:

### A. Qiymat Bo'yicha Uzatish (Pass-by-Value)

Odatiy holatda argument uzatilganda uning **nusxasi (copy)** olinadi. Funksiya ichida parametr o'zgarsa ham, tashqaridagi asliy o'zgaruvchi **o'zgarmaydi**.

```cpp
void increment(int x) {
    x = x + 1; // Faqat nusxasi o'zgaradi
}

int main() {
    int num = 10;
    increment(num);
    cout << num; // Natija: 10 (Asliy qiymat o'zgarmadi)
}

```

### B. Havola Bo'yicha Uzatish (Pass-by-Reference)

Parametr oldiga **`&`** belgisi qo'yiladi. Nusxa olinmaydi, balki asliy o'zgaruvchining xotira manziliga bog'lanadi. Funksiya ichidagi har qanday o'zgarish asliy o'zgaruvchida ham aks etadi.

```cpp
void increment(int& x) {
    x = x + 1; // Asliy o'zgaruvchi o'zgaradi
}

int main() {
    int num = 10;
    increment(num);
    cout << num; // Natija: 11 (Asliy qiymat o'zgardi)
}

```

### C. Const Havola Bo'yicha Uzatish (Pass-by-Const-Reference)

Katta hajmdagi obyektlarni (masalan, `std::string`, `struct`, `vector`) funksiyaga uzatganda xotiradan nusxa ko'chirmaslik (tezlikni oshirish) va uning qiymati funksiya ichida tasodifan o'zgarib ketmasligi uchun **`const type&`** ishlatiladi.

```cpp
// Katta matn nusxalanmaydi (tez ishlaydi) va uni o'zgartirib bo'lmaydi (xavfsiz)
void printMessage(const string& msg) {
    // msg = "Yangi matn"; //  Xatolik! 'const' bo'lgani uchun o'zgartirib bo'lmaydi.
    cout << msg << endl;
}

```

---

## 3. Boshlang'ich Qiymatli Parametrlar (Default Parameters)

Agar funksiya chaqirilganda argument berilmasa, zaxiradagi (default) qiymat ishlatiladi. Default parametrlar har doim parametrlarning **oxirida (o'ng tarafida)** yozilishi shart.

```cpp
#include <iostream>
using namespace std;

// 'country' parametri uchun default qiymat berilgan
void showInfo(string name, string country = "O'zbekiston") {
    cout << name << " — " << country << "dan\n";
}

int main() {
    showInfo("Ali", "Turkiya"); // Natija: Ali — Turkiyadan
    showInfo("Vali");            // Natija: Vali — O'zbekistondan (default ishlatildi)

    return 0;
}

```

---

## 4. Funksiyalarni Qayta Yuklash (Function Overloading)

**Function Overloading** — bir xil nomga ega bo'lgan, lekin parametrlarining **soni yoki ma'lumot turlari** har xil bo'lgan bir nechta funksiyalarni yaratish imkoniyatidir.

Kompilyator qaysi funksiyani chaqirish kerakligini argumentlar turiga qarab o'zi avtomatik aniqlaydi.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

// 1-versiya: Ikkita int sonni qo'shish
int add(int a, int b) {
    return a + b;
}

// 2-versiya: Ikkita double sonni qo'shish
double add(double a, double b) {
    return a + b;
}

// 3-versiya: Uchta int sonni qo'shish (Parametrlar soni har xil)
int add(int a, int b, int c) {
    return a + b + c;
}

int main() {
    cout << add(5, 10) << endl;       // 1-versiya ishlaydi (Natija: 15)
    cout << add(2.5, 4.3) << endl;   // 2-versiya ishlaydi (Natija: 6.8)
    cout << add(1, 2, 3) << endl;     // 3-versiya ishlaydi (Natija: 6)

    return 0;
}

```

---

## 5. Overloading Qoidalari va Muhim Cheklovlar

1. **Parametrlar mosligi:** Qayta yuklangan funksiyalar kamida bitta xususiyat bo'yicha farq qilishi shart:
* Parametrlar **soni** har xil bo'lishi kerak.
* Yoki parametrlar **ma'lumot turi** har xil bo'lishi kerak.


2. **Qaytariladigan tur (Return Type) yetarli emas:** Faqat qaytariladigan ma'lumot turini (`int` yoki `double`) o'zgartirish orqali Overloading qilib bo'lmaydi!
```cpp
int getValue(int x);
double getValue(int x); //  XATOLIK! Parametrlar bir xil bo'lgani uchun kompilyator ajrata olmaydi.

```


3. **Noaniqlik Xatosi (Ambiguity Error):** Default parametrlar va avtomatik tur o'girishlar sababli kompilyator qaysi birini chaqirishni bilmay qolishi mumkin:
```cpp
void print(int x);
void print(double x);

print(5.0f); //  Xavf: float 5.0f int ga ham, double ga ham o'girilishi mumkin.

```



---

## Qisqa Xulosa

| Usul / Tushuncha | Sintaksis | Asosiy Xususiyati |
| --- | --- | --- |
| **Pass-by-Value** | `void fn(int x)` | Argument kopiyasini oladi, asliy o'zgaruvchi o'zgarmaydi |
| **Pass-by-Reference** | `void fn(int& x)` | Asliy o'zgaruvchining o'zini o'zgartirish imkonini beradi |
| **Pass-by-Const-Ref** | `void fn(const string& s)` | Tezkor (kopiyasiz) va xavfsiz (o'zgarmas) uzatish |
| **Default Parameter** | `void fn(int x = 0)` | Argument kiritilmaganda zaxira qiymat ishlatiladi |
| **Function Overloading** | `int add(int, int)` / `double add(double, double)` | Bir xil nomli, lekin turli parametrli funksiyalar |
