**C++ Exceptions (Istisnolar)** — dastur bajarilish vaqtida (runtime) yuzaga keladigan xatoliklarni ushlash va dastur majburiy to'xtab (`crash`) qolishining oldini olish mexanizmi.

---

### 1. Asosiy 3 Ta Kalit So'z

* **`try`** — xatolik yuzaga kelishi mumkin bo'lgan kod blokini ajratadi.
* **`throw`** — xatolik yuz berganida istisno (exception) obyektini yoki qiymatini otadi (yuboradi).
* **`catch`** — otilgan istisnoni tutib oladi va uni qayta ishlaydi.

---

### 2. Oddiy Misol (Sintaksis)

```cpp
#include <iostream>
using namespace std;

int main() {
    try {
        int age = 15;

        if (age < 18) {
            throw 403; // Int turidagi xatolik kodi otiladi
        }

        cout << "Tizimga xush kelibsiz!";
    }
    catch (int errorCode) { // Otilgan xatolik ushlanadi
        cout << "Kirish taqiqlangan! Xatolik kodi: " << errorCode << endl;
    }

    return 0; // Dastur crash bo'lmay, tinch yakunlanadi
}

```

---

### 3. Standart Istisnolar (`std::exception`)

C++ da tayyor xatolik sinflari mavjud (`<stdexcept>` kutubxonasi). Ulardan foydalanish va `.what()` metodi orqali xatolik matnini olish tavsiya etiladi.

```cpp
#include <iostream>
#include <stdexcept> // Standart istisnolar uchun
using namespace std;

double divide(double a, double b) {
    if (b == 0) {
        throw runtime_error("Nolga bo'lish taqiqlangan!");
    }
    return a / b;
}

int main() {
    try {
        cout << divide(10, 0) << endl;
    }
    catch (const exception& e) {
        // e.what() xatolik matnini qaytaradi
        cout << "XATOLIK USHLANDI: " << e.what() << endl;
    }

    return 0;
}

```

---

### 4. Barcha Xatoliklarni Ushlash (Catch-All)

Agar otilayotgan xatolik turini aniq bilmasangiz, **`catch (...)`** barcha turdagi istisnolarni tutib oladi:

```cpp
try {
    // Shubhali kod
}
catch (const runtime_error& e) {
    // Faqat runtime_error uchun
}
catch (...) {
    // Qolgan BARCHA turdagi xatoliklar uchun
    cout << "Noma'lum xatolik yuz berdi!" << endl;
}

```

---
