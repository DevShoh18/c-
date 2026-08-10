# C++ While va Do...While Sikllari (Loops)

**Sikllar (Loops)** — ko'rsatilgan mantiqiy shart `true` (rost) bo'lib turgunga qadar ma'lum bir kod blokini takroran qayta-qayta bajarish uchun ishlatiladi. Ular bir xil kodni ko'p marta qayta yozishdan xalos etadi va vaqtni tejaydi.

---

## 1. `while` Sikli

`while` sikli **har bir takrorlanishdan (iteratsiyadan) oldin** shartni tekshiradi. Agar shart `true` bo'lsa, kod bloki bajariladi. Agar shart `false` bo'lib qolsa, sikl to'xtaydi.

### Sintaksis:

```cpp
while (shart) {
    // Shart true bo'lganda bajariladigan kod
}

```

### Kod Namunasi:

1 dan 5 gacha bo'lgan sonlarni ekranga chiqarish:

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;

    while (i <= 5) {
        cout << i << endl;
        i++; // Hisoblagichni 1 ga oshirish (Inkrement)
    }

    return 0;
}
/* Natija:
1
2
3
4
5
*/

```

> **Diqqat (Cheksiz Sikl / Infinite Loop):** Agar sikl ichida hisoblagichni (`i++`) oshirishni unutib qoldirsangiz, shart har doim `true` bo'lib qoladi va dastur cheksiz to'xtamay ishlayveradi!

---

## 2. `do...while` Sikli

`do...while` sikli `while` ning varianti bo'lib, u shartni **kod bloki bajarilgandan keyin (oxirida)** tekshiradi.

Bu shuni anglatadiki: Shart `false` (yolg'on) bo'lgan taqdirda ham, `do...while` ichidagi kod **kamida bir marta** baribir bajariladi.

### Sintaksis:

```cpp
do {
    // Bajariladigan kod bloki
} while (shart);

```

### Kod Namunasi:

Shart (`i < 1`) boshidanoq xato bo'lsa ham, kod 1 marta baribir ishlaydi:

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 10;

    do {
        cout << "i ning qiymati: " << i << endl;
        i++;
    } while (i < 5); // 10 < 5 xato (false)

    return 0;
}
// Natija: i ning qiymati: 10

```

---

## 3. `while` va `do...while` Farqi

| Xususiyat | `while` | `do...while` |
| --- | --- | --- |
| **Shartni tekshirish vaqti** | Sikl **boshida** (kirishdan oldin) | Sikl **oxirida** (chiqishdan oldin) |
| **Minimal bajarilish soni** | **0 marta** (agar shart boshidanoq `false` bo'lsa) | Kamida **1 marta** (shart `false` bo'lsa ham) |
| **Sintaksis oxiri** | Qavsdan so'ng `;` qo'yilmaydi | `while(shart);` oxirida `;` qo'yiladi |

---

## 4. Hayotiy Misol: Bankomat PIN-kodini Tekshirish

Foydalanuvchi to'g'ri PIN-kod kiritmaguncha qayta-qayta so'rayveradigan dastur (bu yerda kamida 1 marta kiritish kerakligi uchun `do...while` eng ma'qul yechimdir):

```cpp
#include <iostream>
using namespace std;

int main() {
    const int correctPIN = 7788;
    int userPIN;

    do {
        cout << "PIN-kodni kiriting: ";
        cin >> userPIN;

        if (userPIN != correctPIN) {
            cout << "Xato PIN! Qayta urinib ko'ring.\n\n";
        }
    } while (userPIN != correctPIN);

    cout << "\nMuvaffaqiyatli! Tizimga xush kelibsiz." << endl;

    return 0;
}

```

---
