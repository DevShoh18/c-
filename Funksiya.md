# C++ Funksiyalari (Functions)

**Funksiya** — ma'lum bir vazifani bajarishga mo'ljallangan va bir necha marta qayta ishlatilishi mumkin bo'lgan kod blokidir.

Funksiyalar dasturchilarni bir xil kodni qayta-qayta yozishdan qutqaradi va dasturni modulli, tartibli hamda o'qish uchun oson tuzilishga keltirishga xizmat qiladi.

---

## 1. Funksiya Yaratish va Uni Chaqirish (Declaration & Call)

C++ da funksiyani yaratish uchun uning **qaytaradigan ma'lumot turi**, **nomi** hamda **qavslar `()**` ko'rsatiladi:

```cpp
return_type functionName(parameters) {
    // Bajariladigan kod bloki
}

```

* **`return_type`** — Funksiya o'z ishini yakunlagach qaytaradigan qiymat turi (`int`, `double`, `string`, `bool`). Agar funksiya hech qanday qiymat qaytarmasa, **`void`** ishlatiladi.
* **`functionName`** — Funksiyaga beriladigan unikal nom.
* **`parameters`** — Funksiyaga tashqaridan uzatiladigan o'zgaruvchilar (ixtiyoriy).

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

// Funksiya e'lon qilish (void - qiymat qaytarmaydi)
void myFunction() {
    cout << "Funksiya muvaffaqiyatli bajarildi!" << endl;
}

int main() {
    // Funksiyani chaqirish (Call)
    myFunction();
    myFunction(); // Istalgancha marta chaqirish mumkin

    return 0;
}

```

---

## 2. Funksiya Prototipi (Declaration vs Definition)

C++ kompilyatori kodni yuqoridan pastga qarab o'qiydi. Agar funksiya `main()` funksiyasidan pastda yozilgan bo'lsa, kompilyator uni topa olmay xatolik beradi.

Buni hal qilish uchun **Funksiya Prototipi (Declaration)** `main()` dan tepada e'lon qilinadi, uning to'liq kodi (Definition) esa `main()` dan pastda yoziladi:

```cpp
#include <iostream>
using namespace std;

// 1. Funksiya prototipi (Declaration)
void sayHello();

int main() {
    sayHello(); // Chaqirish
    return 0;
}

// 2. Funksiyaning to'liq kodi (Definition)
void sayHello() {
    cout << "Salom, C++!" << endl;
}

```

---

## 3. Parametrlar va Argumentlar (Parameters & Arguments)

Funksiyaga ishlashi uchun tashqaridan ma'lumot (o'zgaruvchi) uzatish mumkin.

* **Parametr** — Funksiya e me'yorida e'lon qilingan o'zgaruvchi.
* **Argument** — Funksiya chaqirilayotganda unga berilgan haqiqiy qiymat.

```cpp
#include <iostream>
#include <string>
using namespace std;

// 'fname' - parametr
void printName(string fname) {
    cout << "Ism: " << fname << endl;
}

int main() {
    // "Shoxboz", "Ali" - argumentlar
    printName("Shoxboz");
    printName("Ali");

    return 0;
}

```

---

## 4. Boshlang'ich Qiymatli Parametrlar (Default Parameters)

Agar funksiyaga argument uzatilmasa, ishlatiladigan zaxira (default) qiymatni belgilab qo'yish mumkin:

```cpp
#include <iostream>
#include <string>
using namespace std;

void myCountry(string country = "O'zbekiston") {
    cout << "Mamlakat: " << country << endl;
}

int main() {
    myCountry("Turkiya");    // Mamlakat: Turkiya
    myCountry();             // Mamlakat: O'zbekiston (Default qiymat ishlatildi)
    myCountry("AQSH");       // Mamlakat: AQSH

    return 0;
}

```

---

## 5. Qiymat Qaytaruvchi Funksiyalar (`return`)

Agar funksiya hisob-kitob natijasini qaytarishi kerak bo'lsa, `void` o'rniga kerakli ma'lumot turi yoziladi va **`return`** kalit so'zidan foydalaniladi.

```cpp
#include <iostream>
using namespace std;

// int turida qiymat qaytaruvchi funksiya
int addNumbers(int a, int b) {
    return a + b;
}

int main() {
    int sum = addNumbers(15, 25);
    cout << "Yig'indi: " << sum << endl; // Natija: 40

    // Yoki to'g'ridan-to'g'ri cout ichida ishlatish
    cout << "Ko'paytma: " << addNumbers(5, 5) << endl; // Natija: 10

    return 0;
}

```

---

## 6. Havola Bo'yicha Uzatish (Pass-by-Reference)

Odatiy holatda funksiyaga argument uzatilganda uning **nusxasi (copy)** olinadi. Agar argumentning asliy qiymatini funksiya ichida o'zgartirmoqchi bo'lsak, **`&` (reference)** dan foydalanamiz:

```cpp
#include <iostream>
using namespace std;

void swapNum(int& x, int& y) {
    int z = x;
    x = y;
    y = z;
}

int main() {
    int firstNum = 10;
    int secondNum = 20;

    cout << "Almashtirishdan oldin: " << firstNum << " " << secondNum << endl;

    // Asliy o'zgaruvchilar o'rni almashadi
    swapNum(firstNum, secondNum);

    cout << "Almashtirishdan keyin: " << firstNum << " " << secondNum << endl;

    return 0;
}
// Natija: 20 10

```

---

## 7. Funksiyalarni Qayta Yuklash (Function Overloading)

C++ da bir xil nomli bir nechta funksiyalar yaratish mumkin, faqat sharti — ularning **parametrlar soni yoki ma'lumot turlari** har xil bo'lishi kerak.

```cpp
#include <iostream>
using namespace std;

// Butun sonlarni qo'shish
int plusFunc(int x, int y) {
    return x + y;
}

// O'nlik kasr sonlarni qo'shish (bir xil nomli funksiya)
double plusFunc(double x, double y) {
    return x + y;
}

int main() {
    int myNum1 = plusFunc(8, 5);          // int versiyasi ishlaydi
    double myNum2 = plusFunc(4.3, 6.26);   // double versiyasi ishlaydi

    cout << "Int: " << myNum1 << endl;
    cout << "Double: " << myNum2 << endl;

    return 0;
}

```

---

## 8. Hayotiy Misol: Yoshni va Kirish Huquqini Tekshirish

```cpp
#include <iostream>
#include <string>
using namespace std;

// Foydalanuvchi yoshiga qarab ruxsat berish
bool checkAccess(int age) {
    if (age >= 18) {
        return true;
    } else {
        return false;
    }
}

int main() {
    int userAge;
    cout << "Yoshingizni kiriting: ";
    cin >> userAge;

    if (checkAccess(userAge)) {
        cout << "Xush kelibsiz! Tizimdan foydalanishingiz mumkin." << endl;
    } else {
        cout << "Poydevor cheklovi: Yoshingiz 18 dan kichik!" << endl;
    }

    return 0;
}

```

---

## Qisqa Xulosa

| Tushuncha | Sintaksis | Izoh |
| --- | --- | --- |
| **Qiymat qaytarmaydigan funksiya** | `void showMsg() { ... }` | Hech narsa qaytarmaydi |
| **Qiymat qaytaruvchi funksiya** | `int getAge() { return 25; }` | Natijani `return` qiladi |
| **Pass-by-Value** | `void func(int x)` | Argument kopiyasini oladi |
| **Pass-by-Reference** | `void func(int& x)` | Asliy o'zgaruvchi ustida ishlaydi |
| **Function Overloading** | `int add(int, int)` / `double add(double, double)` | Bir xil nomli turli parametrli funksiyalar |
