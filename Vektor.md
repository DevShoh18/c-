

# C++ Lists (`std::list`)

C++ da **`std::list`** — bu **Doubly Linked List (Ikki tomonlama bog'langan ro'yxat)** ma'lumotlar tuzilmasidir.

`std::vector` dan farqli o'laroq, `list` elementlari xotirada ketma-ket joylashmaydi. Har bir element xotiraning ixtiyoriy joyida bo'ladi va o'zidan **oldingi** hamda **keyingi** elementga ko'rsatkich (`pointer`) orqali bog'lanadi.

---

## 1. List Yaratish va Ishga Tushirish

List bilan ishlash uchun `<list>` kutubxonasini ulash kerak:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    // String turidagi list yaratish
    list<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    // List elementlarini chiqarish
    for (string car : cars) {
        cout << car << " ";
    }
    // Natija: Volvo BMW Ford Mazda

    return 0;
}

```

---

## 2. Elementlarga Kirish (Access Elements)

`list` xotirada ketma-ket joylashmagani uchun unga **`cars[0]` yoki `cars.at(0)` deb indeks orqali murojaat qilib bo'lmaydi**.

Elementlarni faqat birinchi va oxirgi qiymati orqali olish mumkin:

```cpp
list<string> cars = {"Volvo", "BMW", "Ford"};

cout << cars.front(); // Birinchi element: Volvo
cout << cars.back();  // Oxirgi element: Ford

```

---

## 3. Element Qo'shish va O'chirish (Add & Remove)

`list` ning eng katta afzalligi — uning **boshiga ham, oxiriga ham** $O(1)$ tezlikda element qo'shish va o'chirish mumkin.

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<string> cars = {"BMW", "Ford"};

    // Boshiga va oxiriga qo'shish
    cars.push_front("Tesla"); // ["Tesla", "BMW", "Ford"]
    cars.push_back("Toyota");  // ["Tesla", "BMW", "Ford", "Toyota"]

    // Boshidagi va oxiridagi elementni o'chirish
    cars.pop_front(); // ["BMW", "Ford", "Toyota"]
    cars.pop_back();  // ["BMW", "Ford"]

    return 0;
}

```

---

## 4. List Maxsus Funksiyalari (Special Methods)

`std::list` o'zining ichki saralash va tartiblash metodlariga ega:

| Funksiya | Vazifasi | Misol |
| --- | --- | --- |
| **`sort()`** | Elementlarni o'sish tartibida saralaydi | `numbers.sort();` |
| **`reverse()`** | Ro'yxat elementlari tartibini teskarisiga o'giradi | `numbers.reverse();` |
| **`unique()`** | Yonma-yon kelgan bir xil (dublikat) elementlarni o'chiradi | `numbers.unique();` |
| **`merge()`** | Ikkita saralangan listni bir-biriga qo'shadi | `list1.merge(list2);` |

### Maxsus Funksiyalar Kodu:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> numbers = {5, 2, 8, 2, 1, 5};

    // 1. Saralash
    numbers.sort(); // [1, 2, 2, 5, 5, 8]

    // 2. Takrorlangan qo'shnilarni o'chirish
    numbers.unique(); // [1, 2, 5, 8]

    // 3. Teskari o'girish
    numbers.reverse(); // [8, 5, 2, 1]

    for (int num : numbers) {
        cout << num << " "; // Natija: 8 5 2 1
    }

    return 0;
}

```

---

## 5. List Funksiyalari Jadvali

| Funksiya | Ta'rifi | Vaqt Murakkabligi |
| --- | --- | --- |
| **`push_front(val)`** | Boshiga element qo'shadi | $O(1)$ |
| **`push_back(val)`** | Oxiriga element qo'shadi | $O(1)$ |
| **`pop_front()`** | Boshidagi elementni o'chiradi | $O(1)$ |
| **`pop_back()`** | Oxiridagi elementni o'chiradi | $O(1)$ |
| **`front()`** | Birinchi elementni qaytaradi | $O(1)$ |
| **`back()`** | Oxirgi elementni qaytaradi | $O(1)$ |
| **`size()`** | Elementlar sonini qaytaradi | $O(1)$ |
| **`empty()`** | List bo'shligini tekshiradi (`true`/`false`) | $O(1)$ |
| **`clear()`** | Barcha elementlarni o'chirib tozalaydi | $O(n)$ |
| **`insert(pos, val)`** | Ko'rsatilgan iterator o'rniga element qo'shadi | $O(1)$ |
| **`erase(pos)`** | Ko'rsatilgan iterator o'rnidagi elementni o'chiradi | $O(1)$ |

---

## `std::vector` vs `std::list` (Qachon qaysi birini ishlatish kerak?)

| Xususiyat | `std::vector` | `std::list` |
| --- | --- | --- |
| **Xotira tuzilishi** | Ketma-ket (Contiguous) | Tarqoq (Pointers bilan bog'langan) |
| **Indeks orqali kirish (`[i]`)** | Juda tez ($O(1)$) | **Mavjud emas** |
| **Boshiga element qo'shish** | Sekin ($O(n)$) | **Juda tez ($O(1)$)** |
| **O'rtasiga element qo'shish/o'chirish** | Sekin ($O(n)$) | **Juda tez ($O(1)$)** |
| **Xotira sarfi** | Kamroq | Ko'proq (pointerlar sababli) |
