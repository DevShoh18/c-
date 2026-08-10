# C++ For va Range-Based For Sikllari (For Loops)

Agarda siz sikl (loop) **necha marta takrorlanishini an'iq bilsangiz**, `while` o'rniga **`for`** siklidan foydalanish ancha ixcham va qulaydir.

---

## 1. `for` Sikli va Sintaksisi

```cpp
for (boshlanish; shart; qadam) {
    // Takrorlanuvchi kod bloki
}

```

### Parametrlar Tahlili:

1. **`boshlanish` (Initialization):** Sikl hisoblagichiga boshlang'ich qiymat beriladi (masalan, `int i = 0`). Bu qism **faqat bir marta** (sikl boshida) bajariladi.
2. **`shart` (Condition):** Har bir takrorlanishdan (iteratsiyadan) oldin tekshiriladi. Agar `true` bo'lsa, kod bloki bajariladi. Agar `false` bo'lsa, sikl to'xtaydi.
3. **`qadam` (Increment/Decrement):** Kod bloki bajarib bo'lingach, hisoblagich qiymati o'zgartiriladi (masalan, `i++` yoki `i--`).

---

## 2. Asosiy Kod Namunasi

1 dan 5 gacha bo'lgan sonlarni ekranga chiqarish:

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        cout << "Son: " << i << endl;
    }

    return 0;
}
/* Natija:
Son: 1
Son: 2
Son: 3
Son: 4
Son: 5
*/

```

---

## 3. Qadam O'lchamini O'zgartirish

Hisoblagichni faqat 1 ga emas, xohlagan songa oshirish yoki kamaytirish mumkin:

### Juft Sonlarni Chiqarish (`i += 2`):

```cpp
// 0 dan 10 gacha bo'lgan juft sonlar
for (int i = 0; i <= 10; i += 2) {
    cout << i << " ";
}
// Natija: 0 2 4 6 8 10

```

### Orqaga Sanash (`i--`):

```cpp
// 5 dan 1 gacha kamayib borish
for (int i = 5; i >= 1; i--) {
    cout << i << " ";
}
// Natija: 5 4 3 2 1

```

---

## 4. Ichma-ich `for` Sikllari (Nested Loops)

Sikl ichida boshqa bir siklni joylashtirish mumkin. Tashqi sikl 1 marta aylanganda, ichki sikl to'liq bajarilib tugaydi.

```cpp
#include <iostream>
using namespace std;

int main() {
    // Tashqi sikl 2 marta aylanadi
    for (int i = 1; i <= 2; i++) {
        cout << "Tashqi sikl: " << i << endl;

        // Ichki sikl 3 marta aylanadi
        for (int j = 1; j <= 3; j++) {
            cout << "   Ichki sikl: " << j << endl;
        }
    }

    return 0;
}

```

---

## 5. Range-Based For Loop (C++11 va Undan Yuqori)

Massivlar (Arrays) yoki to'plamlar ustida indekslarsiz, sodda va xavfsiz ravishda elementma-element aylanish uchun ishlatiladi.

### Sintaksis:

```cpp
for (tur o'zgaruvchi_nomi : massiv_nomi) {
    // Har bir element uchun bajariladigan kod
}

```

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

int main() {
    int myNumbers[5] = {10, 20, 30, 40, 50};

    // Massivdagi har bir 'x' elementi bo'ylab aylanish
    for (int x : myNumbers) {
        cout << x << endl;
    }

    return 0;
}

```

---

## 6. Hayotiy Misol: Ko'paytirish Jadvali

1 dan 5 gacha bo'lgan sonlar uchun karra jadvalini chiqarish:

```cpp
#include <iostream>
using namespace std;

int main() {
    int number = 5;

    cout << number << " ning ko'paytirish jadvali:\n";
    for (int i = 1; i <= 10; i++) {
        cout << number << " x " << i << " = " << (number * i) << endl;
    }

    return 0;
}

```

---
