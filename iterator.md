# C++ Iterators (Iteratorlar)

C++ da **Iterator (Iterator)** — bu STL konteynerlari (`vector`, `list`, `deque`, `map`, `set` va h.k.) elementlari bo'ylab harakatlanish (aylanib chiqish) va ularga murojaat qilish uchun ishlatiladigan ko'rsatkichsimon (**pointer-like**) ob'ektdir.

Iteratorlar barcha konteynerlar uchun bir xil (standart) interfeys taqdim etadi.

---

### 1. Create an Iterator (Iterator yaratish)

Iterator e'lon qilish uchun tegishli konteyner turidan va `::iterator` kalit so'zidan foydalaniladi (yoki C++11 dan boshlab `auto` ishlatiladi):

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    // Vector uchun iterator e'lon qilish
    vector<string>::iterator it;

    return 0;
}

```

---

### 2. Loop Through a Vector Using Iterators (Konteyner bo'ylab aylanish)

Konteyner elementlari bo'ylab harakatlanishda ikkita asosiy metod ishlatiladi:

* **`begin()`** — Birinchi elementga ko'rsatuvchi iterator qaytaradi.
* **`end()`** — Oxirgi elementdan **keyingi** xotira manziliga ko'rsatuvchi iterator qaytaradi.
* **`*it`** — Iterator ko me'yorda ko'rsatib turgan joydagi qiymatni o'qiydi (Dereference).

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    // begin() dan end() gacha aylanish (auto ishlatilgan)
    for (auto it = cars.begin(); it != cars.end(); ++it) {
        cout << *it << "\n";
    }

    return 0;
}
/* Natija:
Volvo
BMW
Ford
Mazda
*/

```

---

### 3. Change Element Value via Iterator (Element qiymatini o'zgartirish)

Iterator ko'rsatib turgan element qiymatini `*it` orqali o'zgartirish mumkin:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<string> cars = {"Volvo", "BMW", "Ford"};

    auto it = cars.begin(); // Birinchi elementga ko'rsatadi
    *it = "Tesla";          // Birinchi elementni "Tesla" ga o'zgartiramiz

    cout << cars[0] << "\n"; // Natija: Tesla

    return 0;
}

```

---

### 4. Reverse Iterators (Teskari Iteratorlar)

Konteynerni oxiridan boshiga qarab bosib o'tish uchun **`rbegin()`** (Reverse Begin) va **`rend()`** (Reverse End) ishlatiladi:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    // Oxiridan boshiga qarab aylanish
    for (auto it = cars.rbegin(); it != cars.rend(); ++it) {
        cout << *it << "\n";
    }

    return 0;
}
/* Natija:
Mazda
Ford
BMW
Volvo
*/

```

---

### 5. Constant Iterators (O'zgarmas Iteratorlar)

Elementlar qiymati kutilmaganda o'zgartirib yuborilishining oldini olish uchun (faqat o'qish rejimida) **`cbegin()`** va **`cend()`** ishlatiladi:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> numbers = {10, 20, 30};

    for (auto it = numbers.cbegin(); it != numbers.cend(); ++it) {
        // *it = 50; ❌ XATOLIK! Constant iterator orqali qiymatni o'zgartirib bo'lmaydi
        cout << *it << " ";
    }

    return 0;
}

```

---

### 6. Iterating Through Other Containers (Boshqa konteynerlarda ishlatish)

`std::map` va `std::set` kabi konteynerlarda indeks (`[i]`) bo'lmagani uchun ularda iteratorlar bilan ishlash juda muhim hisoblanadi:

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> people = {{"Anvar", 25}, {"Sardor", 30}};

    // Map bo'ylab iterator yordamida aylanish
    for (auto it = people.begin(); it != people.end(); ++it) {
        cout << it->first << " : " << it->second << "\n";
    }

    return 0;
}
/* Natija:
Anvar : 25
Sardor : 30
*/

```

---

### 7. Iterator Methods & Operators Table (Metodlar va Operatorlar jadvali)

| Method / Operator | Description (Tavsifi) |
| --- | --- |
| **`begin()`** | Birinchi elementga ko'rsatuvchi iterator qaytaradi |
| **`end()`** | Oxirgi elementdan keyingi xotiraga ko'rsatuvchi iterator qaytaradi |
| **`rbegin()`** | Oxirgi elementga ko'rsatuvchi teskari iterator qaytaradi |
| **`rend()`** | Birinchi elementdan oldingi xotiraga ko'rsatuvchi teskari iterator qaytaradi |
| **`cbegin()` / `cend()**` | Faqat o'qish uchun Constant iterator qaytaradi |
| **`*it`** | Iterator ko'rsatib turgan element qiymatini qaytaradi (Dereference) |
| **`it->member`** | Iterator ko'rsatib turgan obyekt a'zosiga kiradi (masalan, `it->first`) |
| **`++it` / `--it**` | Iteratorni keyingi / oldingi elementga suradi |
| **`it + n` / `it - n**` | Iteratorni `n` ta qadam oldinga / orqaga suradi (Random Access) |
