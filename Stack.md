# C++ Stack (`std::stack`)

C++ da **`std::stack`** — bu **LIFO (Last-In, First-Out — Oxirgi kirgan, birinchi chiqadi)** tamoyili asosida ishlaydigan ma'lumotlar tuzilmasidir.

Tasavvur qiling, ustma-ust taxlangan likopchalar: eng oxirgi qo'yilgan likopcha har doim birinchi bo'lib olinadi. Stack'da element faqat eng yuqoridan (**`top`**) qo'shiladi va olib tashlanadi.

---

### 1. Create a Stack (Stack yaratish)

Stack bilan ishlash uchun `<stack>` kutubxonasini ulash kerak:

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    // String turidagi stack yaratish
    stack<string> cars;
    return 0;
}

```

---

### 2. Add Stack Elements (Element qo'shish)

Stack'ga elementlar **`push()`** yordamida faqat tepasiga qo'shiladi:

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");
    cars.push("Mazda"); // Eng tepada "Mazda" turadi

    return 0;
}

```

---

### 3. Access Stack Elements (Elementga kirish)

Stack'da indeks (`cars[0]`) yo'q. Faqat **eng tepadagi (oxirgi qo'shilgan)** elementni **`top()`** orqali ko'rish mumkin:

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");

    cout << cars.top(); // Natija: Ford

    return 0;
}

```

---

### 4. Change Top Element (Tepadagi elementni o'zgartirish)

`top()` orqali eng tepadagi element qiymatini o'zgartirish mumkin:

```cpp
stack<string> cars;

cars.push("Volvo");
cars.push("BMW");

cars.top() = "Tesla"; // "BMW" o'rniga "Tesla" bo'ladi
cout << cars.top();   // Natija: Tesla

```

---

### 5. Remove Stack Elements (Elementni o'chirish)

**`pop()`** funksiyasi faqat eng tepada turgan elementni o'chiradi:

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");

    cars.pop(); // Eng tepadagi "Ford" o'chib ketadi

    cout << cars.top(); // Natija: BMW

    return 0;
}

```

---

### 6. Stack Size & Empty (Hajmi va bo'shligini tekshirish)

```cpp
stack<string> cars;

cars.push("Volvo");
cars.push("BMW");

cout << cars.size();  // Elementlar soni: 2
cout << cars.empty(); // Bo'sh bo'lsa 1 (true), aks holda 0 (false)

```

---

### 7. Loop Through a Stack (Stack bo'ylab aylanish)

Stack'da indeks va iteratorlar yo'qligi uchun oddiy `for` sikli ishlamaydi. Barcha elementlarni chiqarish uchun stack bo'shaguncha tepasidagini ko'rib, `pop()` qilib boriladi:

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<string> cars;

    cars.push("Volvo");
    cars.push("BMW");
    cars.push("Ford");

    // Stack bo'shaguncha tepasidagilarni o'qib, o'chirib boramiz
    while (!cars.empty()) {
        cout << cars.top() << "\n";
        cars.pop();
    }

    return 0;
}
/* Natija:
Ford
BMW
Volvo
*/

```

---

### 8. Stack Functions Table (Funksiyalar jadvali)

| Method | Description (Tavsifi) | Time Complexity |
| --- | --- | --- |
| **`push(val)`** | Stack tepasiga yangi element qo'shadi | $O(1)$ |
| **`pop()`** | Stack tepasidagi elementni o'chiradi | $O(1)$ |
| **`top()`** | Stack tepasidagi elementni qaytaradi | $O(1)$ |
| **`size()`** | Stack'dagi elementlar sonini qaytaradi | $O(1)$ |
| **`empty()`** | Stack bo'shligini tekshiradi (`true`/`false`) | $O(1)$ |
| **`emplace(args)`** | Elementni tepadagi o'rnida joyida yaratib qo'shadi | $O(1)$ |
