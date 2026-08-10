# C++ Queue (`std::queue`)

C++ da **`std::queue`** — bu **FIFO (First-In, First-Out — Birinchi kirgan, birinchi chiqadi)** tamoyili asosida ishlaydigan ma'lumotlar tuzilmasidir.

Tasavvur qiling, do'kondagi navbat: navbatga birinchi bo'lib kelgan xaridor birinchi bo'lib xizmat ko'rsatilib chiqib ketadi. Queue'da elementlar navbatning oxiridan (**`back`**) qo'shiladi va boshidan (**`front`**) olib tashlanadi.

---

### 1. Create a Queue (Queue yaratish)

Queue bilan ishlash uchun `<queue>` kutubxonasini ulash kerak:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    // String turidagi queue yaratish
    queue<string> cars;
    return 0;
}

```

---

### 2. Add Queue Elements (Element qo'shish)

Queue'ga elementlar **`push()`** yordamida navbatning **oxiriga** qo'shiladi:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");
    cars.push("Mazda"); // Navbatning eng oxirida "Mazda" turadi

    return 0;
}

```

---

### 3. Access Queue Elements (Elementlarga kirish)

Queue'da ham indeks (`cars[0]`) yo'q. Elementlarga navbatning birinchi kelgani (**`front()`**) va eng oxirida kelgani (**`back()`**) orqali murojaat qilinadi:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");

    cout << cars.front() << "\n"; // Navbat boshidagi: Volvo
    cout << cars.back() << "\n";  // Navbat oxiridagi: Ford

    return 0;
}

```

---

### 4. Change Queue Elements (Elementlarni o'zgartirish)

`front()` va `back()` orqali birinchi hamda oxirgi element qiymatini o'zgartirish mumkin:

```cpp
queue<string> cars;

cars.push("Volvo");
cars.push("BMW");

cars.front() = "Tesla";   // "Volvo" o'rniga "Tesla" bo'ladi
cars.back() = "Hyundai";  // "BMW" o'rniga "Hyundai" bo'ladi

cout << cars.front();     // Natija: Tesla

```

---

### 5. Remove Queue Elements (Elementni o'chirish)

**`pop()`** funksiyasi navbatning eng **boshida (birinchi bo'lib kirgan)** turgan elementni o'chiradi:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");

    cars.pop(); // Birinchi kirgan "Volvo" o'chib ketadi

    cout << cars.front(); // Natija: BMW

    return 0;
}

```

---

### 6. Queue Size & Empty (Hajmi va bo'shligini tekshirish)

```cpp
queue<string> cars;

cars.push("Volvo");
cars.push("BMW");

cout << cars.size();  // Elementlar soni: 2
cout << cars.empty(); // Bo'sh bo'lsa 1 (true), aks holda 0 (false)

```

---

### 7. Loop Through a Queue (Queue bo'ylab aylanish)

Queue'da ham iteratorlar va indekslar yo'qligi sababli oddiy `for` sikli ishlamaydi. Barcha elementlarni chiqarish uchun navbat bo'shaguncha boshidagisini ko'rib, `pop()` qilib boriladi:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");

    // Queue bo'shaguncha birinchi turganini ko'rib, pop() qilib boramiz
    while (!cars.empty()) {
        cout << cars.front() << "\n";
        cars.pop();
    }

    return 0;
}
/* Natija:
Volvo
BMW
Ford
*/

```

---

### 8. Queue Functions Table (Funksiyalar jadvali)

| Method | Description (Tavsifi) | Time Complexity |
| --- | --- | --- |
| **`push(val)`** | Navbat oxiriga yangi element qo'shadi | $O(1)$ |
| **`pop()`** | Navbat boshidagi elementni o'chiradi | $O(1)$ |
| **`front()`** | Navbat boshidagi (birinchi) elementni qaytaradi | $O(1)$ |
| **`back()`** | Navbat oxiridagi (oxirgi) elementni qaytaradi | $O(1)$ |
| **`size()`** | Navbatdagi elementlar sonini qaytaradi | $O(1)$ |
| **`empty()`** | Navbat bo'shligini tekshiradi (`true`/`false`) | $O(1)$ |
| **`emplace(args)`** | Elementni navbat oxirida joyida yaratib qo'shadi | $O(1)$ |
