
---

# C++ Maps (`std::map`)

C++ da **`std::map`** — bu ma'lumotlarni **Kalit-Qiymat (Key-Value)** juftligi shaklida saqlaydigan assotsiativ konteynerdir.

Har bir kalit (`key`) **unikal (takrorlanmas)** bo'ladi va o'zining tegishli qiymatiga (`value`) ega bo'ladi. `std::map` elementlarni kalitlari bo'yicha avtomatik ravishda **o'sish tartibida saralab** saqlaydi.

---

### 1. Create a Map (Map yaratish)

Map bilan ishlash uchun `<map>` kutubxonasini ulash kerak:

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    // Key: string, Value: int bo'lgan map
    map<string, int> people = {{"Anvar", 25}, {"Sardor", 30}, {"Jasur", 22}};
    return 0;
}

```

---

### 2. Add Map Elements (Element qo'shish)

Map'ga elementlarni `[]` operatori yoki `.insert()` funksiyasi orqali qo'shish mumkin:

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> people;

    // [] operatori orqali qo'shish
    people["Anvar"] = 25;
    people["Sardor"] = 30;

    // insert() va initializer list orqali qo'shish
    people.insert({"Jasur", 22});

    return 0;
}

```

---

### 3. Access Map Elements (Elementlarga kirish)

Map elementlariga uning kaliti (`key`) orqali `[]` yoki `.at()` yordamida murojaat qilinadi:

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> people = {{"Anvar", 25}, {"Sardor", 30}};

    cout << people["Anvar"] << "\n";    // Natija: 25
    cout << people.at("Sardor") << "\n"; // Natija: 30

    return 0;
}

```

---

### 4. Change Map Elements (Elementlarni o'zgartirish)

Kalit orqali unga biriktirilgan qiymatni osongina o'zgartirish mumkin:

```cpp
map<string, int> people = {{"Anvar", 25}};

people["Anvar"] = 26; // Qiymat 26 ga o'zgaradi
cout << people["Anvar"]; // Natija: 26

```

---

### 5. Remove Map Elements (Elementni o'chirish)

**`.erase()`** funksiyasi ko'rsatilgan kalit bo'yicha elementni o'chirib tashlaydi:

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> people = {{"Anvar", 25}, {"Sardor", 30}, {"Jasur", 22}};

    people.erase("Sardor"); // "Sardor" kaliti va uning qiymati o'chadi

    return 0;
}

```

---

### 6. Check if an Element Exists (Element mavjudligini tekshirish)

Kalit mavjudligini **`.count()`** funksiyasi orqali tekshirish mumkin (kalit bo'lsa `1`, bo'lmasa `0` qaytaradi):

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> people = {{"Anvar", 25}, {"Sardor", 30}};

    if (people.count("Anvar")) {
        cout << "Anvar map'da mavjud!\n";
    }

    return 0;
}

```

---

### 7. Map Size & Empty (Hajmi va bo'shligini tekshirish)

```cpp
map<string, int> people = {{"Anvar", 25}, {"Sardor", 30}};

cout << people.size();  // Juftliklar soni: 2
cout << people.empty(); // Bo'sh bo'lsa 1 (true), aks holda 0 (false)

```

---

### 8. Loop Through a Map (Map bo'ylab aylanish)

Map bo'ylab aylanishda har bir element `pair` (juftlik) ko'rinishida bo'ladi: `first` — kalit, `second` — qiymat.

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> people = {{"Anvar", 25}, {"Sardor", 30}, {"Jasur", 22}};

    // Structured binding (C++17) yordamida kalit va qiymatni o'qish
    for (auto const& [key, value] : people) {
        cout << key << " : " << value << "\n";
    }

    return 0;
}
/* Natija (avtomatik saralangan):
Anvar : 25
Jasur : 22
Sardor : 30
*/

```

---

### 9. Map Functions Table (Funksiyalar jadvali)

| Method | Description (Tavsifi) | Time Complexity |
| --- | --- | --- |
| **`operator[]`** | Kalit bo'yicha qiymatga kiradi yoki yangi element yaratadi | $O(\log n)$ |
| **`at(key)`** | Kalit bo'yicha qiymatga xavfsiz kiradi | $O(\log n)$ |
| **`insert({key, val})`** | Kalit-qiymat juftligini qo'shadi | $O(\log n)$ |
| **`erase(key)`** | Kalit bo'yicha elementni o'chiradi | $O(\log n)$ |
| **`count(key)`** | Kalit bor-yo'qligini tekshiradi (`1` yoki `0`) | $O(\log n)$ |
| **`find(key)`** | Kalitga mos iterator qaytaradi | $O(\log n)$ |
| **`size()`** | Elementlar (juftliklar) sonini qaytaradi | $O(1)$ |
| **`empty()`** | Map bo'shligini tekshiradi (`true`/`false`) | $O(1)$ |
| **`clear()`** | Barcha elementlarni o'chirib tozalaydi | $O(n)$ |
