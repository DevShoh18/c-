# C++ Lambda Funksiyalari (Lambda Expressions)

**Lambda funksiyasi** — C++11 standartida kiritilgan bo'lib, alohida nom berilmagan **anonim funksiya (anonymous function)** yaratish imkonini beradi.

Lambda funksiyalari asosan qisqa, bir marta ishlatiladigan va boshqa funksiyalarga (masalan, STL algoritmlariga) argument sifatida uzatiladigan kod bloklari uchun ishlatiladi.

---

## 1. Lambda Sintaksisi

Lambda funksiyasining umumiy ko'rinishi 4 ta asosiy qismdan iborat:

```cpp
[capture_clause](parameters) -> return_type {
    // Funksiya tanasi (kod bloki)
};

```

1. **`[capture_clause]` (Tashqi o'zgaruvchilarni qamrab olish):** Lambda joylashgan doiradagi (scope) tashqi o'zgaruvchilarni Lambda ichida ishlatish huquqini beradi.
2. **`(parameters)` (Parametrlar):** Oddiy funksiyalar kabi uzatiladigan argumentlar (ixtiyoriy).
3. **`-> return_type` (Qaytariladigan tur):** Qaytariluvchi ma'lumot turi (ixtiyoriy, aksar hollarda kompilyator o'zi avtomatik aniqlaydi).
4. **`{ body }` (Tana):** Bajariladigan kod bloki.

---

## 2. Asosiy Kod Namunasi

```cpp
#include <iostream>
using namespace std;

int main() {
    // 1. Eng oddiy lambda funksiya va uni darhol chaqirish
    []() {
        cout << "Salom, Lambda!" << endl;
    }(); // Oxiridagi () lambdani ishga tushiradi

    // 2. Lambdani auto o'zgaruvchiga saqlash va chaqirish
    auto greet = []() {
        cout << "Nomsiz funksiyadan salom!" << endl;
    };
    greet(); // Chaqirish

    // 3. Parametr va return bilan ishlash
    auto add = [](int a, int b) -> int {
        return a + b;
    };

    cout << "5 + 10 = " << add(5, 10) << endl; // Natija: 15

    return 0;
}

```

---

## 3. Capture Clause (`[...]` — Tashqi o'zgaruvchilarni ushlash)

Lambda funksiyasi o'zidan tashqaridagi local o'zgaruvchilarni default holatda ko'rmaydi. Ulardan foydalanish uchun Capture qavsida ko'rsatish kerak:

| Capture Sintaksisi | Ma'nosi / Tavsifi |
| --- | --- |
| **`[]`** | Tashqi o'zgaruvchilarni ushlamaydi (Bo'sh) |
| **`[x]`** | `x` o'zgaruvchisini **qiymat bo'yicha (Pass-by-value)** ko'chirib oladi (fath qilib o'zgartirib bo'lmaydi) |
| **`[&x]`** | `x` o'zgaruvchisini **havola bo'yicha (Pass-by-reference)** ushlaydi (o'zgartirish mumkin) |
| **`[=]`** | Barcha tashqi local o'zgaruvchilarni **qiymat bo'yicha** avtomatik ko'chirib oladi |
| **`[&]`** | Barcha tashqi local o'zgaruvchilarni **havola bo'yicha** avtomatik ushlaydi |
| **`[a, &b]`** | `a` ni qiymat bo'yicha, `b` ni havola bo'yicha ushlaydi |

### Capture Misoli:

```cpp
#include <iostream>
using namespace std;

int main() {
    int factor = 3;
    int total = 0;

    // 'factor' qiymat bo'yicha, 'total' havola bo'yicha ushlandi
    auto multiplyAndAdd = [factor, &total](int number) {
        total += number * factor;
    };

    multiplyAndAdd(5); // total = 0 + (5 * 3) = 15
    multiplyAndAdd(2); // total = 15 + (2 * 3) = 21

    cout << "Jami total: " << total << endl; // Natija: 21

    return 0;
}

```

---

## 4. `mutable` Kalit So'zi

Odatiy holatda, qiymat bo'yicha ushlangan (`[x]`) o'zgaruvchilarni lambda ichida o'zgartirib bo'lmaydi (ular `const` bo'ladi). Agar nusxalangan qiymatni lambda ichida o'zgartirish kerak bo'lsa, **`mutable`** so'zi qo'shiladi:

```cpp
#include <iostream>
using namespace std;

int main() {
    int count = 10;

    // 'mutable' sababli 'count' ning lambda ichidagi nusxasini o'zgartirish mumkin
    auto counter = [count]() mutable {
        count++;
        cout << "Lambda ichida count: " << count << endl;
    };

    counter(); // Lambda ichida count: 11
    counter(); // Lambda ichida count: 12

    cout << "Tashqarida asliy count: " << count << endl; // Tashqarida asliy count: 10 (O'zgarmadi)

    return 0;
}

```

---

## 5. Hayotiy va Amaliy Misol: STL Algoritmlari Bilan Ishlash

Lambda funksiyalari ko'pincha `std::sort`, `std::for_each`, `std::find_if` kabi standart kutubxona algoritmlarida saralash yoki filtrlash shartini yozish uchun ishlatiladi.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> numbers = {5, 2, 8, 1, 9, 4};

    // 1. Vector elementlarini kamayish tartibida saralash (Lambda Predicate)
    sort(numbers.begin(), numbers.end(), [](int a, int b) {
        return a > b; // Katta son birinchi kelsin
    });

    cout << "Kamayish tartibida saralash: ";
    for (int n : numbers) {
        cout << n << " ";
    }
    cout << endl; // Natija: 9 8 5 4 2 1

    // 2. Faqat juft sonlarni sanash (count_if)
    int evenCount = count_if(numbers.begin(), numbers.end(), [](int n) {
        return n % 2 == 0;
    });

    cout << "Juft sonlar soni: " << evenCount << endl; // Natija: 3 (8, 4, 2)

    return 0;
}

```

---

## Qisqa Xulosa

| Qism | Sintaksis | Vazifasi |
| --- | --- | --- |
| **Capture Clause** | `[]`, `[=]`, `[&]` | Tashqi o'zgaruvchilarni ko'rish huquqini beradi |
| **Parameter List** | `(int a, int b)` | Lambdaga uzatiladigan argumentlar |
| **Mutable** | `[]() mutable {}` | Qiymat bo'yicha ushlangan nusxalarni lambda ichida o'zgartirishga ruxsat beradi |
| **STL Integratsiya** | `std::sort`, `std::count_if` | Anonim Predicate sifatida qisqa kod yozish uchun eng qulay yechim |
