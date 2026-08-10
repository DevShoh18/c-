# C++ Stringlar (Strings)
C++ da matnlar bilan ishlash uchun **`std::string`** ma'lumot turidan foydalaniladi. Matnlar bir nechta belgilardan iborat ketma-ketlik bo'lib, har doim juft qo'shtirnoq (`" "`) ichida yoziladi.
> **Eslatma:** Dasturda matnlar bilan to'liq va xatosiz ishlash uchun `#include <string>` sarlavha faylini qo'shish tavsiya etiladi.
---
## 1. Matnlarni Birlashtirish (Concatenation)
Ikki yoki undan ortiq matnlarni bir-biriga qo'shish uchun **`+`** operatori yoki **`append()`** funksiyasidan foydalaniladi.
```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    string firstName = "Sardor";
    string lastName = "";

    // 1-usul: '+' operatori yordamida
    string fullName1 = firstName + " " + lastName;
    cout << fullName1 << endl; // Natija: Shoxboz Tojaliyev

    // 2-usul: append() funksiyasi yordamida
    string fullName2 = firstName.append(" ").append(lastName);
    cout << fullName2 << endl; // Natija: Shoxboz Tojaliyev

    return 0;
}

```

> **Diqqat:** Sonlar va matnlarni qo'shishda ehtiyot bo'ling! Matn va son birlashtirilganda xatolik yuz beradi. `string x = "10"; int y = 20; string z = x + y;` (Xato!).

---

## 2. Matn Uzunligini Aniqlash (Length / Size)

Matndagi belgilar sonini bilish uchun **`.length()`** yoki **`.size()`** funksiyalari ishlatiladi. Ikkala funksiya ham mutlaqo bir xil vazifani bajaradi.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    
    cout << "Matn uzunligi (length): " << txt.length() << endl; // 26
    cout << "Matn uzunligi (size): " << txt.size() << endl;     // 26

    return 0;
}

```

---

## 3. Belgilarga Murojaat va O'zgartirish (Access & Modify)

Matn ichidagi har bir belgiga uning indeksi (tartib raqami) orqali murojaat qilish mumkin. Indekslash **`0`** dan boshlanadi.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string myString = "Hello";

    // Birinchi belgini o'qish (0-indeks)
    cout << myString[0] << endl; // Natija: H

    // Oxirgi belgini o'qish
    cout << myString[myString.length() - 1] << endl; // Natija: o

    // Belgini o'zgartirish
    myString[0] = 'J';
    cout << myString << endl; // Natija: Jello

    return 0;
}

```

---

## 4. Maxsus Belgilar (Escape Characters)

Qo'shtirnoq ichida maxsus belgilarni (masalan, qo'shtirnoqning o'zini yoki yangi qatorni) ishlatish uchun teskari slesh (`\`) belgisidan foydalaniladi:

| Maxsus Ketma-ketlik | Natija | Tavsifi |
| --- | --- | --- |
| **`\"`** | `"` | Matn ichida juft qo'shtirnoq chiqarish |
| **`\'`** | `'` | Matn ichida tekshiruv tirnog'i chiqarish |
| **`\\`** | `\` | Matn ichida teskari slesh chiqarish |
| **`\n`** | *Yangi qator* | Kursorni yangi qatordan o'tkazish |
| **`\t`** | *Tab* | Katta bo'sh joy (Tabulation) tashlash |

### Misol:

```cpp
string txt1 = "Biz \"Kiberxavfsizlik\" yo'nalishida o'qiymiz.";
string txt2 = "Fayl manzili: C:\\Program Files\\C++";

```

---

## 5. Klaviaturadan Matn O'qish (`cin` va `getline`)

Matnlarni klaviaturadan o'qib olishda **`cin`** va **`getline()`** o'rtasida katta farq bor:

1. **`cin >> o'zgaruvchi;`** — Faqat **birinchi bo'sh joygacha (probelgacha)** bo'lgan so'zni o'qiydi.
2. **`getline(cin, o'zgaruvchi);`** — Bo'sh joylar bilan birga **butun satrni (Enter tugmasigacha)** o'qiydi.

### Amaliy Misol:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string fullName;

    cout << "To'liq ismingizni kiriting: ";
    // cin >> fullName; // Agar "Shoxboz Tojaliyev" kiritilsa, faqat "Shoxboz" ni oladi!

    getline(cin, fullName); // Butun ism va familiyani to'liq o'qiydi
    cout << "Sizning ismingiz: " << fullName;

    return 0;
}

```
