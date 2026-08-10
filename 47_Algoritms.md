# C++ Algorithms (`<algorithm>`)

C++ da **Algorithms (Algoritmlar)** — STL konteynerlari (`vector`, `list`, `deque`, `array` va h.k.) ustida saralash, qidirish, o'zgartirish va hisoblash kabi amallarni bajaruvchi tayyor funksiyalar to'plamidir.

Algoritmlar konteynerlar bilan **iteratorlar** orqali ishlaydi. Ulardan foydalanish uchun **`<algorithm>`** kutubxonasini ulash kerak.

---

### 1. Sort an Array / Vector (Saralash)

**`sort()`** funksiyasi konteyner elementlarini o'sish tartibida saralaydi:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> numbers = {5, 2, 8, 1, 3};

    // O'sish tartibida saralash
    sort(numbers.begin(), numbers.end());

    for (int num : numbers) {
        cout << num << " "; // Natija: 1 2 3 5 8
    }

    return 0;
}

```

> **Kamayish tartibida saralash uchun:** `sort(numbers.begin(), numbers.end(), greater<int>());` ishlatiladi.

---

### 2. Reverse an Array / Vector (Teskari o'girish)

**`reverse()`** funksiyasi elementlar ketma-ketligini teskari tartibga o'giradi:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> numbers = {1, 2, 3, 4, 5};

    // Elementlar tartibini teskari o'girish
    reverse(numbers.begin(), numbers.end());

    for (int num : numbers) {
        cout << num << " "; // Natija: 5 4 3 2 1
    }

    return 0;
}

```

---

### 3. Search for an Element (Qidirish)

* **`find()`** — Konteynerdan ko'rsatilgan qiymatni chiziqli qidiradi va unga mos iterator qaytaradi ($O(n)$).
* **`binary_search()`** — **Saralangan** konteynerda ikkilik qidiruv o'tkazadi va element bor-yo'qligini `bool` (`true`/`false`) shaklida qaytaradi ($O(\log n)$).

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> numbers = {10, 20, 30, 40, 50};

    // 1. find() yordamida qidirish
    auto it = find(numbers.begin(), numbers.end(), 30);
    if (it != numbers.end()) {
        cout << "30 topildi!\n";
    }

    // 2. binary_search() yordamida tekshirish (saralangan vector uchun)
    if (binary_search(numbers.begin(), numbers.end(), 40)) {
        cout << "40 vector ichida bor!\n";
    }

    return 0;
}

```

---

### 4. Find Min and Max Element (Eng kichik va eng katta element)

* **`min_element()`** — Eng kichik elementga ko'rsatuvchi iterator qaytaradi.
* **`max_element()`** — Eng katta elementga ko'rsatuvchi iterator qaytaradi.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> numbers = {15, 3, 42, 8, 23};

    // Iteratorlarni olish va '*' yordamida qiymatni o'qish
    auto minIt = min_element(numbers.begin(), numbers.end());
    auto maxIt = max_element(numbers.begin(), numbers.end());

    cout << "Eng kichik: " << *minIt << "\n"; // Natija: 3
    cout << "Eng katta: " << *maxIt << "\n";   // Natija: 42

    return 0;
}

```

---

### 5. Fill and Copy Elements (To'ldirish va Nusxalash)

* **`fill()`** — Konteynerning ma'lum oralig'ini bir xil qiymat bilan to'ldiradi.
* **`copy()`** — Bir konteynerdagi elementlarni boshqasiga nusxalaydi.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> numbers(5); // 5 ta elementli vector

    // Barcha elementlarni 7 bilan to'ldirish
    fill(numbers.begin(), numbers.end(), 7); // [7, 7, 7, 7, 7]

    vector<int> copiedNumbers(5);
    // Elementlarni yangi vectorga nusxalash
    copy(numbers.begin(), numbers.end(), copiedNumbers.begin());

    return 0;
}

```

---

### 6. Count Elements (Sanoq)

**`count()`** funksiyasi ko'rsatilgan qiymat konteynerda nechta marta uchraganini sanab beradi:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> numbers = {1, 2, 2, 3, 2, 4, 5};

    // 2 qiymati nechta marta qatnashganini sanaymiz
    int cnt = count(numbers.begin(), numbers.end(), 2);

    cout << "2 soni " << cnt << " marta qatnashgan.\n"; // Natija: 3

    return 0;
}

```

---

### 7. Algorithms Functions Table (Funksiyalar jadvali)

| Method | Description (Tavsifi) | Time Complexity |
| --- | --- | --- |
| **`sort(beg, end)`** | Elementlarni o'sish tartibida saralaydi | $O(n \log n)$ |
| **`reverse(beg, end)`** | Elementlar tartibini teskarisiga o'giradi | $O(n)$ |
| **`find(beg, end, val)`** | Qiymatga mos keladigan birinchi iteratorni qaytaradi | $O(n)$ |
| **`binary_search(beg, end, val)`** | Element bor-yo'qligini ikkilik qidiruv bilan tekshiradi (`bool`) | $O(\log n)$ |
| **`min_element(beg, end)`** | Eng kichik elementga iterator qaytaradi | $O(n)$ |
| **`max_element(beg, end)`** | Eng katta elementga iterator qaytaradi | $O(n)$ |
| **`count(beg, end, val)`** | Qiymat nechta marta uchraganini sanaydi | $O(n)$ |
| **`fill(beg, end, val)`** | Oraliqni ko'rsatilgan qiymat bilan to'ldiradi | $O(n)$ |
| **`copy(beg, end, dest)`** | Elementlarni boshqa konteynerga nusxalaydi | $O(n)$ |
| **`replace(beg, end, old, new)`** | Eski qiymatni yangi qiymatga almashtiradi | $O(n)$ |
