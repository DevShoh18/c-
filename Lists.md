# C++ Lists (`std::list`)

C++ da **`std::list`** — bu **Doubly Linked List (Ikki tomonlama bog'langan ro'yxat)** ma'lumotlar tuzilmasidir.

`vector` dan farqli ravishda, `list` elementlari xotirada ketma-ket emas, tarqoq joylashadi va bir-biriga ko'rsatkichlar (`pointer`) orqali bog'lanadi.

---

### 1. Create a List (List yaratish)

List bilan ishlash uchun `<list>` kutubxonasini ulash kerak:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    // String turidagi list yaratish
    list<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    return 0;
}

```

---

### 2. Access List Elements (Elementlarga kirish)

`list` xotirada tarqoq joylashgani uchun unga **indeks (`cars[0]` yoki `cars.at(0)`) orqali murojaat qilib bo'lmaydi**.

Elementlarga faqat birinchi (`front()`) va oxirgi (`back()`) qiymatlar orqali kiriladi:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<string> cars = {"Volvo", "BMW", "Ford"};

    cout << cars.front() << "\n"; // Birinchi element: Volvo
    cout << cars.back() << "\n";  // Oxirgi element: Ford

    return 0;
}

```

---

### 3. Change a List Element (Elementni o'zgartirish)

Birinchi yoki oxirgi element qiymatini o'zgartirish uchun `.front()` va `.back()` dan foydalaniladi:

```cpp
list<string> cars = {"Volvo", "BMW", "Ford"};

cars.front() = "Toyota"; // Birinchi element "Toyota" ga o'zgaradi
cars.back() = "Tesla";   // Oxirgi element "Tesla" ga o'zgaradi

```

---

### 4. Add List Elements (Element qo'shish)

`list` ning **boshiga** ham, **oxiriga** ham element qo'shish juda tez ($O(1)$) ishlaydi:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<string> cars = {"BMW", "Ford"};

    cars.push_front("Tesla"); // Boshiga qo'shish: ["Tesla", "BMW", "Ford"]
    cars.push_back("Toyota");  // Oxiriga qo'shish: ["Tesla", "BMW", "Ford", "Toyota"]

    return 0;
}

```

---

### 5. Remove List Elements (Elementni o'chirish)

Boshidagi yoki oxiridagi elementlarni olib tashlash:

```cpp
list<string> cars = {"Tesla", "BMW", "Ford", "Toyota"};

cars.pop_front(); // Boshidagi "Tesla" o'chadi
cars.pop_back();  // Oxiridagi "Toyota" o'chadi

```

---

### 6. List Size & Empty (Hajmi va bo'shligini tekshirish)

```cpp
list<string> cars = {"Volvo", "BMW", "Ford"};

cout << cars.size();  // Elementlar soni: 3
cout << cars.empty(); // Bo'sh bo'lsa 1 (true), aks holda 0 (false)

```

---

### 7. Loop Through a List (List bo'ylab aylanish)

List elementlarini ekranga chiqarish uchun **Range-based for** siklidan foydalaniladi:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    for (string car : cars) {
        cout << car << "\n";
    }

    return 0;
}

```

---

### 8. Special List Methods (Maxsus Metodlar)

`list` o'zining ichki saralash va tartiblash metodlariga ega:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> numbers = {5, 2, 8, 2, 1};

    numbers.sort();   // 1. Saralash: [1, 2, 2, 5, 8]
    numbers.unique(); // 2. Dublikat qo'shnilarni o'chirish: [1, 2, 5, 8]
    numbers.reverse();// 3. Teskari o'girish: [8, 5, 2, 1]

    for (int num : numbers) {
        cout << num << " "; // Natija: 8 5 2 1
    }

    return 0;
}

```

---

### 9. List Functions Table (Funksiyalar jadvali)

| Method | Description (Tavsifi) | Time Complexity |
| --- | --- | --- |
| **`push_front(val)`** | Boshiga element qo'shadi | $O(1)$ |
| **`push_back(val)`** | Oxiriga element qo'shadi | $O(1)$ |
| **`pop_front()`** | Boshidagi elementni o'chiradi | $O(1)$ |
| **`pop_back()`** | Oxiridagi elementni o'chiradi | $O(1)$ |
| **`front()`** | Birinchi elementni qaytaradi | $O(1)$ |
| **`back()`** | Oxirgi elementni qaytaradi | $O(1)$ |
| **`size()`** | Elementlar sonini qaytaradi | $O(1)$ |
| **`empty()`** | List bo'shligini tekshiradi (`true`/`false`) | $O(1)$ |
| **`sort()`** | Elementlarni o'sish tartibida saralaydi | $O(n \log n)$ |
| **`reverse()`** | Ro'yxatni teskari tartibga o'giradi | $O(n)$ |
| **`unique()`** | Yonma-yon kelgan bir xil elementlarni o'chiradi | $O(n)$ |
| **`clear()`** | Barcha elementlarni o'chirib tozalaydi | $O(n)$ |
