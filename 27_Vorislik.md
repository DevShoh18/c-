# C++ Vorislik (Inheritance)

**Vorislik (Inheritance)** — C++ Obyektga Yo'naltirilgan Dasturlash (OOP) ning asosiy ustunlaridan biri bo'lib, bir klassning (Base/Parent Class) xususiyatlari va metodlarini boshqa bir klassga (Derived/Child Class) o'tkazish (meros berish) imkonini beradi.

Vorislikning asosiy maqsadi — kodni qayta ishlatish (**Code Reusability**) va klasslar o'rtasida mantiqiy iyerarxiya hosil qilishdir.

---

## 1. Asosiy Tushunchalar va Sintaksis

* **Base Class (Ota / Baza klass):** Xususiyat va metodlarini meros beruvchi klass.
* **Derived Class (Bola / Voris klass):** Ota klassdan xususiyat va metodlarni meros oluvchi klass.

Sintaksisda vorislik olish uchun **`:` (ikki nuqta)** va kirish rejimlaridan (`public`, `protected`, `private`) foydalaniladi:

```cpp
class OtaKlass {
    // ...
};

class BolaKlass : public OtaKlass {
    // ...
};

```

---

## 2. Oddiy Kod Namunasi

```cpp
#include <iostream>
#include <string>
using namespace std;

// Base Class (Ota klass)
class Vehicle {
public:
    string brand = "Chevrolet";

    void honk() {
        cout << "Beep beep!" << endl;
    }
};

// Derived Class (Bola klass) - Vehicle dan public voris oladi
class Car : public Vehicle {
public:
    string model = "Gentra";
    int year = 2023;
};

int main() {
    Car myCar;

    // Ota klassdan meros qolgan metod va xususiyatlar
    myCar.honk(); // Beep beep!
    cout << "Brend: " << myCar.brand << endl; // Chevrolet

    // O'zining xususiyatlari
    cout << "Model: " << myCar.model << " (" << myCar.year << ")" << endl;

    return 0;
}

```

---

## 3. Vorislik Rejimlari (Inheritance Access Modes)

Ota klassdan voris olayotganda `public`, `protected` yoki `private` belgilanishiga qarab, ota klass a'zolarining bola klassdagi ko'rinish darajasi o'zgaradi:

| Ota Klassdagi A'zo | `public` Vorislikda | `protected` Vorislikda | `private` Vorislikda |
| --- | --- | --- | --- |
| **`public`** | `public` bo'lib o'tadi | `protected` bo'lib o'tadi | `private` bo'lib o'tadi |
| **`protected`** | `protected` bo'lib o'tadi | `protected` bo'lib o'tadi | `private` bo'lib o'tadi |
| **`private`** | *To'g'ridan-to'g'ri ko'rinmaydi* | *To'g'ridan-to'g'ri ko'rinmaydi* | *To'g'ridan-to'g'ri ko'rinmaydi* |

> **Eslatma:** Ota klassning `private` a'zolari hech qachon bola klassga to'g'ridan-to'g'ri o'tmaydi (ular faqat ota klassning `public`/`protected` metodlari orqali bilvosita ishlatilishi mumkin).

---

## 4. Vorislik Turlari (Types of Inheritance)

C++ tilida vorislikning 5 xil ko'rinishi mavjud:

```
1. Single          2. Multilevel        3. Multiple         4. Hierarchical
   [A]                 [A]               [A]   [B]                [A]
    |                   |                  \   /                 /   \
   [B]                 [B]                  [C]                [B]   [C]
                        |
                       [C]

```

### A. Single Inheritance (Yagona vorislik)

Bitta bola klass bitta ota klassdan meros oladi (`A -> B`).

### B. Multilevel Inheritance (Ko'p bosqichli vorislik)

Klass voris olingan boshqa bir voris klassdan meros oladi (`A -> B -> C`).

```cpp
class Animal {
public:
    void eat() { cout << "Ovqatlanmoqda..." << endl; }
};

class Dog : public Animal {
public:
    void bark() { cout << "Vov-vov!" << endl; }
};

class GermanShepherd : public Dog {
public:
    void guard() { cout << "Qriqlamoqda..." << endl; }
};

```

### C. Multiple Inheritance (Ko'p otali vorislik)

Bitta bola klass **bir nechta ota klasslardan** bir vaqtning o me'yorida meros oladi:

```cpp
class Camera {
public:
    void takePhoto() { cout << "Rasmga olindi." << endl; }
};

class Phone {
public:
    void makeCall() { cout << "Qo'ng'iroq qilinmoqda..." << endl; }
};

// Ikkala klassdan ham birdek meros oladi
class SmartPhone : public Camera, public Phone {};

int main() {
    SmartPhone myPhone;
    myPhone.takePhoto();
    myPhone.makeCall();
    return 0;
}

```

---

## 5. Konstruktor va Destruktorlarning Bajarilish Tartibi

Vorislikda obyekt yaratilayotganda va o'chirilayotganda konstruktor hamda destruktorlar ma'lum bir tartibda ishlaydi:

1. **Konstruktorlar:** Avval **Ota klass**, so'ng **Bola klass** konstruktori ishlaydi.
2. **Destruktorlar:** Avval **Bola klass**, so'ng **Ota klass** destruktori ishlaydi (teskari tartibda).

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    Base() { cout << "1. Base Konstruktor" << endl; }
    ~Base() { cout << "4. Base Destruktor" << endl; }
};

class Derived : public Base {
public:
    Derived() { cout << "2. Derived Konstruktor" << endl; }
    ~Derived() { cout << "3. Derived Destruktor" << endl; }
};

int main() {
    Derived obj;
    return 0;
}

```

---
