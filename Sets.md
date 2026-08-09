# C++ Sets (`std::set`)

C++ da **`std::set`** — bu faqat **unikal (takrorlanmas)** elementlarni saqlaydigan va ularni avtomatik ravishda **saralangan (tartiblangan)** holda ushlaydigan assotsiativ konteynerdir.

`set` ning 2 ta asosiy xususiyati bor:

1. **Takrorlanmaslik:** Bir xil qiymatli element bir necha marta qo'shilsa ham, faqat 1 tasi saqlanadi.
2. **Avtomatik saralanish:** Elementlar qo'shilganda har doim o'sish (alifbo yoki sonlar) tartibida saralanadi.

---

### 1. Create a Set (Set yaratish)

Set bilan ishlash uchun `<set>` kutubxonasini ulash kerak:

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    // String turidagi set yaratish
    set<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};
    return 0;
}

```

---

### 2. Unique Elements & Automatic Sorting (Unikallik va Avtomatik Saralash)

Set bir xil qiymatlarni o'z-o'zidan e'tiborsiz qoldiradi va har doim o'sish tartibida joylashtiradi:

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    // Takroriy elementlar va tartibsiz sonlar
    set<int> numbers = {5, 2, 8, 2, 1, 5};

    for (int num : numbers) {
        cout << num << " ";
    }

    return 0;
}
/* Natija: 1 2 5 8 (Dublikatlar o'chirildi, sonlar saralandi) */

```

---

### 3. Add Set Elements (Element qo'shish)

Set'ga yangi element **`.insert()`** funksiyasi orqali qo'shiladi:

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<string> cars = {"Volvo", "BMW"};

    cars.insert("Ford");
    cars.insert("Tesla");
    cars.insert("BMW"); // "BMW" allaqachon bor, qayta qo'shilmaydi

    return 0;
}

```

---

### 4. Remove Set Elements (Elementni o'chirish)

Elementni qiymati bo'yicha o'chirish uchun **`.erase()`** ishlatiladi:

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    cars.erase("BMW"); // "BMW" o'chib ketadi

    return 0;
}

```

---

### 5. Check if an Element Exists (Element mavjudligini tekshirish)

Element set ichida bor-yo'qligini **`.count()`** funksiyasi orqali tekshirish mumkin (element bor bo'lsa `1`, bo'lmasa `0` qaytaradi):

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<string> cars = {"Volvo", "BMW", "Ford"};

    if (cars.count("Volvo")) {
        cout << "Volvo set'da mavjud!\n";
    } else {
        cout << "Volvo topilmadi.\n";
    }

    return 0;
}

```

---

### 6. Set Size & Empty (Hajmi va bo'shligini tekshirish)

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<string> cars = {"Volvo", "BMW", "Ford"};

    cout << cars.size() << "\n";  // Elementlar soni: 3
    cout << cars.empty() << "\n"; // Bo'sh bo'lsa 1 (true), aks holda 0 (false)

    return 0;
}

```

---

### 7. Loop Through a Set (Set bo'ylab aylanish)

Set elementlariga indeks (`cars[0]`) orqali kirib bo'lmaydi. Ularni o'qish uchun `Range-based for` sikli ishlatiladi:

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<string> cars = {"Volvo", "BMW", "Ford", "Mazda"};

    for (string car : cars) {
        cout << car << "\n";
    }

    return 0;
}
/* Natija (alifbo tartibida):
BMW
Ford
Mazda
Volvo
*/

```

---

### 8. Sort a Set in Descending Order (Kamayish tartibida saralash)

Odatiy holatda set o'sish tartibida saralaydi. Kamayish tartibida saralash uchun **`greater<type>`** parametri qo'shiladi:

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    // Kamayish tartibida saralanuvchi set
    set<int, greater<int>> numbers = {1, 5, 2, 8};

    for (int num : numbers) {
        cout << num << " "; // Natija: 8 5 2 1
    }

    return 0;
}

```

---

### 9. Set Functions Table (Funksiyalar jadvali)

| Method | Description (Tavsifi) | Time Complexity |
| --- | --- | --- |
| **`insert(val)`** | Set'ga yangi element qo'shadi | $O(\log n)$ |
| **`erase(val)`** | Qiymat bo'yicha elementni o'chiradi | $O(\log n)$ |
| **`count(val)`** | Element bor-yo'qligini tekshiradi (`1` yoki `0`) | $O(\log n)$ |
| **`find(val)`** | Elementga mos iterator qaytaradi | $O(\log n)$ |
| **`size()`** | Elementlar sonini qaytaradi | $O(1)$ |
| **`empty()`** | Set bo'shligini tekshiradi (`true`/`false`) | $O(1)$ |
| **`clear()`** | Barcha elementlarni o'chirib tozalaydi | $O(n)$ |
