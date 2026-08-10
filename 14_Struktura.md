# C++ Strukturalari (struct)

**Struktura (`struct`)** — har xil ma'lumot turlariga ega bo'lgan bir nechta o'zgaruvchilarni bitta umumiy nom ostida guruhlash imkonini beruvchi maxsus ma'lumot turi.

Massivlardan (`arrays`) farqli o'laroq, struktura bir vaqtning o'zida ham `int`, ham `string`, ham `double` va `bool` kabi har xil turdagi ma'lumotlarni bir joyda saqlay oladi.

---

## 1. Struktura Yaratish va Sintaksisi

Struktura **`struct`** kalit so'zi orqali e'lon qilinadi va uning ichidagi o'zgaruvchilar **a'zolar (members)** deb ataladi.

```cpp
struct StrukturaNomi {
    int myNum;        // A'zo o'zgaruvchi
    string myString;  // A'zo o'zgaruvchi
}; // Nuqta-vergul (;) qo'yish SHART!

```

---

## 2. A'zolarga Murojaat Qilish (Dot Operator)

Struktura a me'yorlariga kirish va ularga qiymat biriktirish uchun **nuqta (`.`)** operatoridan foydalaniladi.

```cpp
#include <iostream>
#include <string>
using namespace std;

// 1. Struktura tipini e'lon qilish
struct Car {
    string brand;
    string model;
    int year;
};

int main() {
    // 2. Car turidagi o'zgaruvchi (obyekt) yaratish
    Car myCar1;

    // 3. Nuqta (.) orqali qiymatlar berish
    myCar1.brand = "BMW";
    myCar1.model = "X5";
    myCar1.year = 2023;

    // 4. Qiymatlarini ekranga chiqarish
    cout << "Brend: " << myCar1.brand << endl;
    cout << "Model: " << myCar1.model << endl;
    cout << "Yil: " << myCar1.year << endl;

    return 0;
}

```

---

## 3. Bir Nechta Struktura O'zgaruvchilarini Yaratish

Bitta e'lon qilingan `struct` qolipidan istalgancha o'zgaruvchilar hosil qilish mumkin:

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Car {
    string brand;
    string model;
    int year;
};

int main() {
    // Birinchi avtomobil
    Car myCar1;
    myCar1.brand = "BMW";
    myCar1.model = "X5";
    myCar1.year = 2023;

    // Ikkinchi avtomobil
    Car myCar2;
    myCar2.brand = "Chevrolet";
    myCar2.model = "Gentra";
    myCar2.year = 2022;

    cout << myCar1.brand << " " << myCar1.model << " (" << myCar1.year << ")\n";
    cout << myCar2.brand << " " << myCar2.model << " (" << myCar2.year << ")\n";

    return 0;
}

```

---

## 4. Qisqartirilgan Rekvizitli Boshlang'ich Qiymat Berish (Initialization)

Har bir a'zoga birma-bir nuqta orqali qiymat berish o'rniga figurali qavslar `{}` yordamida ketma-ket bir qatorda qiymat biriktirish ham mumkin:

```cpp
// Ketma-ketlik strukturadagi a'zolar tartibiga mos kelishi kerak
Car myCar1 = {"Tesla", "Model S", 2024};
Car myCar2 = {"BYD", "Song Plus", 2023};

```

---

## 5. Hayotiy Misol: Talaba Profilini Boshqarish

Tizimda talaba ma me'lumotlarini saqlash va qayta ishlash dasturi:

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Student {
    int id;
    string fullName;
    double gpa;
    bool isGrant;
};

int main() {
    Student st1 = {1001, "Aliyev Vali", 4.2, true};
    Student st2 = {1002, "Karimov Hasan", 3.8, false};

    cout << "=== TALABA MA'LUMOTLARI ===" << endl;
    cout << "ID: " << st1.id << endl;
    cout << "Ism: " << st1.fullName << endl;
    cout << "GPA: " << st1.gpa << endl;
    cout << "Ta'lim shakli: " << (st1.isGrant ? "Davlat granti" : "Kontrakt") << endl;

    return 0;
}

```

---

## Qisqa Xulosa

| Amaliyot | Sintaksis Namuna | Izoh |
| --- | --- | --- |
| **Struktura e'lon qilish** | `struct Car { string brand; int year; };` | Yangi tur qolipini yaratadi |
| **O'zgaruvchi hosil qilish** | `Car c1;` | Struktura turidagi o'zgaruvchi ajratadi |
| **A'zoga kirish / o'zgartirish** | `c1.brand = "BMW";` | Nuqta (`.`) operatori orqali kiriladi |
| **Tezkor qiymat berish** | `Car c1 = {"BMW", 2023};` | Qavslar ichida tartib bo'yicha qiymat biriktiradi |
