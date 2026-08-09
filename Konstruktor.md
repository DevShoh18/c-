# C++ Konstruktorlari (Constructors)

**Konstruktor (Constructor)** — bu klassdan yangi obyekt yaratilgan zahoti **avtomatik ravishda ishga tushadigan** maxsus a'zo funksiya (metod).

Konstruktordan asosiy maqsad — obyektning xususiyatlariga (a'zo o'zgaruvchilariga) **boshlang'ich qiymat berish (initsializatsiya qilish)** va obyekt ishlashi uchun zarur bo'lgan resurslarni ajratishdir.

---

## 1. Konstruktorning Qat'iy Qoidalari

1. **Nomi:** Konstruktor nomi **klass nomi bilan bir xil** bo'lishi shart.
2. **Qaytarilish turi:** Konstruktor **hech qanday ma'lumot turini qaytarmaydi** (hatto `void` ham yozilmaydi).
3. **Avtomatik chaqirilishi:** Obyekt yaratilishi bilan kompilyator uni o'zi avtomatik chaqiradi.
4. **Kirish doirasi:** U har doim **`public`** bo'limida joylashishi kerak (aks holda tashqaridan obyekt yaratib bo me'yorda bo'lmaydi).

---

## 2. Konstruktor Turlari

C++ da konstruktorlarning 3 ta asosiy turi mavjud:

### A. Default Constructor (Parametrsiz / Odatiy Konstruktor)

Hech qanday parametr qabul qilmaydi. Agar siz klass ichida birorta ham konstruktor yozmasangiz, C++ kompilyatori o'zi avtomatik tarzda bo'sh `Default Constructor` yaratib beradi.

### B. Parameterized Constructor (Parametrli Konstruktor)

Obyekt yaratilayotgan vaqtda unga tashqaridan boshlang'ich qiymatlarni uzatish imkonini beradi.

### C. Copy Constructor (Nusxalash Konstruktori)

Mavjud bir obyektning nusxasini olib, uning ma'lumotlari asosida yangi obyekt hosil qilish uchun ishlatiladi.

---

## 3. Kod Namunasi: Barcha Konstruktor Turlari

```cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
public:
    string name;
    int age;
    double gpa;

    // 1. Default Constructor (Parametrsiz)
    Student() {
        name = "Noma'lum";
        age = 0;
        gpa = 0.0;
        cout << "Default Konstruktor ishladi!" << endl;
    }

    // 2. Parameterized Constructor (Parametrli)
    Student(string sName, int sAge, double sGpa) {
        name = sName;
        age = sAge;
        gpa = sGpa;
        cout << "Parametrli Konstruktor ishladi (" << name << " uchun)!" << endl;
    }

    // 3. Copy Constructor (Nusxalash)
    Student(const Student& existingStudent) {
        name = existingStudent.name;
        age = existingStudent.age;
        gpa = existingStudent.gpa;
        cout << "Copy Konstruktor ishladi (" << name << " ning nusxasi o olindi)!" << endl;
    }

    void displayInfo() {
        cout << "Ism: " << name << ", Yosh: " << age << ", GPA: " << gpa << endl << endl;
    }
};

int main() {
    // 1. Default konstruktor orqali yaratish
    Student st1;
    st1.displayInfo();

    // 2. Parametrli konstruktor orqali yaratish
    Student st2("Shoxboz", 22, 4.0);
    st2.displayInfo();

    // 3. Copy konstruktor orqali st2 dan st3 nusxa yaratish
    Student st3 = st2;
    st3.displayInfo();

    return 0;
}

```

---

## 4. Initsializatsiya Ro'yxati (Member Initializer List)

C++ da o'zgaruvchilarga konstruktor tanasi `{}` ichida qiymat berishdan ko'ra, **Initsializatsiya Ro'yxati (Initializer List)** orqali qiymat berish tavsiya etiladi.

### Nima uchun Initializer List ishlatish kerak?

* **Tezlik:** O'zgaruvchi xotirada yaratilishi bilan bir vaqtda initsializatsiya bo'ladi (ikki marta qiymat biriktirish xarajatining oldi olinadi).
* **Majburiylik:** `const` o'zgaruvchilar va `reference (&)` a'zolarga faqat Initializer List orqali boshlang'ich qiymat berish mumkin.

### Sintaksis:

```cpp
class Rectangle {
private:
    const double width;
    double height;

public:
    // Initializer List sintaksisi: : width(w), height(h)
    Rectangle(double w, double h) : width(w), height(h) {
        // Konstruktor tanasi bo'sh bo'lishi mumkin
    }

    void showArea() {
        cout << "Yuzasi: " << width * height << endl;
    }
};

```

---

## 5. Konstruktorlarni Qayta Yuklash (Constructor Overloading)

Klass ichida bir xil nomli (lekin parametrlar soni yoki turi har xil bo'lgan) bir nechta konstruktorlarni e'lon qilish **Constructor Overloading** deyiladi.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Point {
public:
    int x, y;

    // 1-konstruktor: Boshlang'ich nuqta (0, 0)
    Point() : x(0), y(0) {}

    // 2-konstruktor: Ikkala koordinatani tayinlash
    Point(int xVal, int yVal) : x(xVal), y(yVal) {}

    // 3-konstruktor: Ikkala koordinataga bir xil qiymat berish
    Point(int val) : x(val), y(val) {}

    void print() {
        cout << "(" << x << ", " << y << ")" << endl;
    }
};

int main() {
    Point p1;        // (0, 0)
    Point p2(10, 20);// (10, 20)
    Point p3(5);     // (5, 5)

    p1.print();
    p2.print();
    p3.print();

    return 0;
}

```

---
