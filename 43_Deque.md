# C++ Deque (`std::deque`)

C++ da **`std::deque` (Double-Ended Queue — Ikki tomonlama navbat)** — bu elementlarni **boshidan** ham, **oxiridan** ham qo'shish va o'chirish imkonini beruvchi ma'lumotlar tuzilmasidir.

---

### 1. Create a Deque (Deque yaratish)

Deque bilan ishlash uchun `<deque>` kutubxonasini ulash kerak:

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    // String turidagi deque yaratish
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    return 0;
}

```

---

### 2. Access Deque Elements (Elementlarga kirish)

Deque elementlariga birinchi (`front()`), oxirgi (`back()`) yoki indeks (`[]` va `.at()`) orqali murojaat qilinadi:

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    cout << cars[0] << "\n";       // Indeks orqali: Volvo
    cout << cars.at(1) << "\n";   // at() orqali: BMW
    cout << cars.front() << "\n"; // Birinchi element: Volvo
    cout << cars.back() << "\n";  // Oxirgi element: Mazda

    return 0;
}

```

---

### 3. Change Deque Elements (Elementlarni o'zgartirish)

Element qiymatini indeks orqali yoki `.front()` / `.back()` yordamida o'zgartirish mumkin:

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<string> cars = {"Volvo", "BMW", "Ford"};

    cars[0] = "Tesla";       // "Volvo" o'rniga "Tesla"
    cars.at(1) = "Hyundai";  // "BMW" o'rniga "Hyundai"
    cars.back() = "Kia";     // "Ford" o'rniga "Kia"

    cout << cars[0] << "\n"; // Natija: Tesla

    return 0;
}

```

---

### 4. Add Deque Elements (Element qo'shish)

Deque'ning **boshiga** element qo'shish uchun `push_front()`, **oxiriga** qo'shish uchun `push_back()` ishlatiladi:

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<string> cars = {"BMW", "Ford"};

    cars.push_front("Tesla"); // Boshiga qo'shish: ["Tesla", "BMW", "Ford"]
    cars.push_back("Toyota");  // Oxiriga qo'shish: ["Tesla", "BMW", "Ford", "Toyota"]

    return 0;
}

```

---

### 5. Remove Deque Elements (Elementni o'chirish)

Boshidagi elementni o'chirish uchun `pop_front()`, oxiridagisini o'chirish uchun `pop_back()` ishlatiladi:

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<string> cars = {"Tesla", "BMW", "Ford", "Toyota"};

    cars.pop_front(); // Boshidagi "Tesla" o'chib ketadi
    cars.pop_back();  // Oxiridagi "Toyota" o'chib ketadi

    return 0;
}

```

---

### 6. Deque Size & Empty (Hajmi va bo'shligini tekshirish)

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<string> cars = {"Volvo", "BMW", "Ford"};

    cout << cars.size() << "\n";  // Elementlar soni: 3
    cout << cars.empty() << "\n"; // Bo'sh bo'lsa 1 (true), aks holda 0 (false)

    return 0;
}

```

---

### 7. Loop Through a Deque (Deque bo'ylab aylanish)

Deque elementlarini ekranga chiqarish uchun `Range-based for` yoki indeksli `for` siklidan foydalaniladi:

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    // 1. Range-based for sikli
    for (string car : cars) {
        cout << car << " ";
    }
    cout << "\n";

    // 2. Indeksli for sikli
    for (size_t i = 0; i < cars.size(); i++) {
        cout << cars[i] << " ";
    }

    return 0;
}

```

---

### 8. Deque Functions Table (Funksiyalar jadvali)

| Method | Description (Tavsifi) | Time Complexity |
| --- | --- | --- |
| **`push_front(val)`** | Deque boshiga element qo'shadi | $O(1)$ |
| **`push_back(val)`** | Deque oxiriga element qo'shadi | $O(1)$ |
| **`pop_front()`** | Deque boshidagi elementni o'chiradi | $O(1)$ |
| **`pop_back()`** | Deque oxiridagi elementni o'chiradi | $O(1)$ |
| **`operator[i]`** | `i`-indeksdagi elementga kiradi | $O(1)$ |
| **`at(i)`** | `i`-indeksdagi elementga xavfsiz kiradi | $O(1)$ |
| **`front()`** | Birinchi elementni qaytaradi | $O(1)$ |
| **`back()`** | Oxirgi elementni qaytaradi | $O(1)$ |
| **`size()`** | Elementlar sonini qaytaradi | $O(1)$ |
| **`empty()`** | Deque bo'shligini tekshiradi (`true`/`false`) | $O(1)$ |
| **`clear()`** | Barcha elementlarni o'chirib tozalaydi | $O(n)$ |
