# C++ Massivlari (Arrays)

**Massiv (Array)** — bir xil ma'lumot turiga ega bo'lgan bir nechta qiymatni bitta o'zgaruvchi nomi ostida ketma-ket saqlash uchun mo'ljallangan konteyner.

Aytaylik, 100 ta sonni saqlash kerak bo'lsa, 100 ta alohida o'zgaruvchi (`x1, x2, ..., x100`) yaratish o'rniga bitta massivdan foydalanish ancha qulay.

---

## 1. Massiv E'lon Qilish va Qiymat Berish

Massiv yaratishda uning **ma'lumot turi**, **nomi** va kvadrat qavs `[]` ichida **elementlar soni (o'lchami)** ko'rsatiladi:

```cpp
tur massiv_nomi[o'lcham] = {qiymat1, qiymat2, ...};

```

### Misollar:

```cpp
// 4 ta matnli elementdan iborat massiv
string cars[4] = {"Volvo", "BMW", "Ford", "Mazda"};

// 3 ta butun sondan iborat massiv
int myNum[3] = {10, 20, 30};

```

### O'lchamini Ko'rsatmasdan Yaratish:

Massiv e'lon qilinayotgan vaqtda qiymatlari aniq bo'lsa, o'lchamini ko'rsatmaslik ham mumkin (kompilyator elementlar sonini avtomatik aniqlaydi):

```cpp
string cars[] = {"Volvo", "BMW", "Ford"}; // O'lchami avtomatik 3 bo'ladi

```

---

## 2. Elementlarga Murojaat va Ularni O'zgartirish

Massiv elementlariga uning **indeksi (tartib raqami)** orqali murojaat qilinadi. Massivlarda indekslash har doim **`0`** dan boshlanadi.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string cars[4] = {"Volvo", "BMW", "Ford", "Mazda"};

    // Birinchi elementni o'qish (0-indeks)
    cout << cars[0] << endl; // Natija: Volvo

    // Element qiymatini o'zgartirish
    cars[0] = "Opel";
    cout << cars[0] << endl; // Natija: Opel

    return 0;
}

```

---

## 3. Massiv Elementlarini Sikl Bilan Chiqarish (Looping)

Massivdagi barcha elementlarni birma-bir ekranga chiqarish yoki ularni qayta ishlash uchun `for` sikllaridan foydalaniladi.

### A. Standart `for` Sikli Yordamida:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string cars[4] = {"Volvo", "BMW", "Ford", "Mazda"};

    for (int i = 0; i < 4; i++) {
        cout << i << "-indeks: " << cars[i] << endl;
    }

    return 0;
}

```

### B. Range-based `for` Sikli Yordamida (C++11 va undan yuqori):

Massiv bo'ylab indekslarsiz, sodda aylanib chiqish usuli:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string cars[4] = {"Volvo", "BMW", "Ford", "Mazda"};

    for (string car : cars) {
        cout << car << endl;
    }

    return 0;
}

```

---

## 4. Massiv O'lchami va `sizeof` Operatori

Massiv nechta elementdan iborat ekanligini bilish uchun `sizeof()` operatoridan foydalaniladi. `sizeof()` massivning xotiradagi umumiy hajmini **baytlarda** qaytaradi.

Elementlar sonini topish uchun massivning umumiy hajmini bitta elementining hajmiga bo'lish kerak:

```cpp
#include <iostream>
using namespace std;

int main() {
    int myNumbers[5] = {10, 20, 30, 40, 50};

    // int = 4 bayt. 5 * 4 = 20 bayt
    int getArrayByteSize = sizeof(myNumbers); // 20

    // Elementlar sonini hisoblash formula:
    int getArrayLength = sizeof(myNumbers) / sizeof(myNumbers[0]); // 20 / 4 = 5

    cout << "Elementlar soni: " << getArrayLength << endl;

    return 0;
}

```

---

## 5. Hayotiy Misol: O'rtacha Bahoni va Eng Yuqori Bahoni Topish

Keling, talabaning 5 ta fandan olgan baholari bo'yicha o'rtacha ballini hamda eng yuqori bahosini hisoblaydigan dastur tuzaylik:

```cpp
#include <iostream>
using namespace std;

int main() {
    int grades[5] = {85, 92, 78, 95, 88};
    int sum = 0;
    int maxGrade = grades[0];

    int length = sizeof(grades) / sizeof(grades[0]);

    for (int i = 0; i < length; i++) {
        sum += grades[i]; // Jami summani hisoblash

        if (grades[i] > maxGrade) {
            maxGrade = grades[i]; // Eng yuqori bahoni topish
        }
    }

    double average = (double)sum / length;

    cout << "Jami baholar yig'indisi: " << sum << endl;
    cout << "O'rtacha ball: " << average << endl;
    cout << "Eng yuqori ball: " << maxGrade << endl;

    return 0;
}
/* Natija:
Jami baholar yig'indisi: 438
O'rtacha ball: 87.6
Eng yuqori ball: 95
*/

```

---

## Qisqa Xulosa

| Amaliyot | Sintaksis | Izoh |
| --- | --- | --- |
| **Massiv e'lon qilish** | `int arr[5];` | 5 ta butun son uchun xotiradan joy ajratadi |
| **Boshlang'ich qiymat berish** | `int arr[] = {1, 2, 3};` | O'lchami 3 ga teng massiv hosil qiladi |
| **Murojaat qilish** | `arr[0]` | Birinchi elementni oladi (indeks 0 dan boshlanadi) |
| **O'lchamini topish** | `sizeof(arr) / sizeof(arr[0])` | Massivdagi elementlar sonini hisoblaydi |
