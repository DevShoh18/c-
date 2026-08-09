# C++ O'zgaruvchilari (Variables)
**O'zgaruvchilar** — ma'lumotlarni kompyuter operativ xotirasida (RAM) saqlash uchun mo'ljallangan "idishlar" (konteynerlar).
---
## 1. Asosiy Turlar va Ularning Xotiradagi Hajmi
C++ da har bir o'zgaruvchining o'z turi bo'ladi. Har bir tur xotiradan ma'lum miqdorda joy egallaydi:
| Tur (Type) | Nima saqlaydi | Misol | Xotiradagi hajmi |
| --- | --- | --- | --- |
| **`int`** | Butun sonlar (kasrsiz) | `15`, `-123` | **4 Byte** (32-bit) |
| **`double`** | O'nlik / Kasr sonlar | `19.99`, `-3.14` | **8 Byte** (64-bit) |
| **`char`** | Bitta belgi (yakkalik `' '` tirnoqda) | `'A'`, `'%'` | **1 Byte** (8-bit) |
| **`string`** | Matnlar (juft `" "` tirnoqda) | `"Salom"`, `"C++"` | Dinamik (~24 Byte) |
| **`bool`** | Mantiqiy qiymat (`true` / `false`) | `true` (1), `false` (0) | **1 Byte** (8-bit) |
---
## 2. O'zgaruvchi Yaratish (Sintaksis)
O'zgaruvchi yaratish uchun uning **turi**, **nomi** va **qiymati** ko'rsatiladi:
```cpp
tur o'zgaruvchi_nomi = qiymat;
```
### Misollar:
```cpp
int myNum = 5;             // Butun son
double myFloatNum = 5.99;   // Kasr son
char myLetter = 'D';        // Bitta belgi
string myText = "Salom";    // Matn
bool myBoolean = true;      // Mantiqiy qiymat
```
Qiymatni keyinchalik berish ham mumkin:
```cpp
int myNum;
myNum = 15;
```
---
## 3. Qiymatni O'zgartirish
O'zgaruvchiga yangi qiymat biriktirilsa, eski qiymat o'chib o'rniga yangisi yoziladi:
```cpp
int myNum = 15;  // myNum hozir 15
myNum = 10;      // Endi myNum 10 ga teng bo'ldi
cout << myNum;   // Ekranga 10 chiqadi
```
---
## 4. O'zgaruvchilarni Ekranga Chiqarish
`cout` va `<<` operatori orqali matn hamda o'zgaruvchilarni birlashtirib ko'rsatish mumkin:
```cpp
string name = "John";
int age = 35;
double height = 6.1;
cout << name << " is " << age << " years old and " << height << " feet tall.";
// Natija: John is 35 years old and 6.1 feet tall.
```
---
## 5. O'zgaruvchilar Bilan Hisoblash
Matematik operatorlar (`+`, `-`, `*`, `/`) orqali o'zgaruvchilar ustida amallar bajariladi:
```cpp
int x = 5;
int y = 6;
int sum = x + y; // 5 + 6 = 11
cout << sum;     // Natija: 11
```
