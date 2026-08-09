# C++ Polimorfizm (Polymorphism)

**Polimorfizm (Polymorphism)** — grekcha "poly" (ko'p) va "morph" (shakl) so'zlaridan olingan bo'lib, **"ko'p shakllilik"** degan ma'noni anglatadi.

OOP da polimorfizm bir xil nomli metod yoki operatsiyaga turli obyektlarda turlicha xatti-harakat (mantiq) bajarish imkoniyatini beradi. Masalan, `Animal` klassidagi `makeSound()` metodi `Dog` obyekti uchun "Vov-vov", `Cat` obyekti uchun esa "Miyov" ovozini chiqarishi polimorfizmdir.

---

## 1. Polimorfizm Turlari

C++ tilida polimorfizm 2 ta asosiy turga bo'linadi:

```
                  C++ Polimorfizm
                        |
       +----------------+----------------+
       |                                 |
Compile-time Polymorphism        Runtime Polymorphism
(Statik / Early Binding)         (Dinamik / Late Binding)
   |              |                      |
Function       Operator               Function
Overloading    Overloading            Overriding (`virtual`)

```

---

## 2. Compile-Time Polymorphism (Kompilyatsiya Vaqtidagi Polimorfizm)

Dastur kompilyatsiya bo'layotgan vaqtda qaysi funksiya yoki operator chaqirilishi aniq hal bo'ladi.

### A. Function Overloading (Funksiyalarni qayta yuklash)

Bir xil nomli, lekin parametrlar soni yoki turi har xil bo'lgan funksiyalar:

```cpp
int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }

```

### B. Operator Overloading (Operatorlarni qayta yuklash)

C++ dagi standart operatorlarga (`+`, `-`, `<<`, `==`) o'zingiz yaratgan klasslar bilan ishlash ma'nosini biriktirish:

```cpp
#include <iostream>
using namespace std;

class Complex {
public:
    int real, imag;

    Complex(int r = 0, int i = 0) : real(r), imag(i) {}

    // '+' operatorini Complex klassi uchun qayta yuklaymiz
    Complex operator + (const Complex& obj) {
        Complex res;
        res.real = real + obj.real;
        res.imag = imag + obj.imag;
        return res;
    }
};

int main() {
    Complex c1(10, 5), c2(2, 4);
    Complex c3 = c1 + c2; // '+' operatori ikkita obyektni qo'shadi

    cout << c3.real << " + " << c3.imag << "i" << endl; // Natija: 12 + 9i
    return 0;
}

```

---

## 3. Runtime Polymorphism (Bajarilish Vaqtidagi Polimorfizm)

Dastur **ishga tushganida (runtime)** o'zgaruvchi tegishli bo'lgan obyekt turiga qarab qaysi metod ishlatilishi aniqlanadi. Bu mexanizm **`virtual`** funksiyalar va **Function Overriding** orqali amalga oshiriladi.

### Asosiy Qoidalar:

1. Vorislik (Inheritance) mavjud bo'lishi kerak.
2. Ota klassdagi metod oldiga **`virtual`** kalit so'zi qo'yiladi.
3. Bola klassdagi metod imzosi bir xil bo'lib, uning oxiriga **`override`** qo'shiladi.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

// Base Class (Ota klass)
class Animal {
public:
    // 'virtual' kalit so'zi late binding (kech bog'lanish) hosil qiladi
    virtual void makeSound() {
        cout << "Hayvon biror ovoz chiqarmoqda..." << endl;
    }
};

// Derived Class 1
class Pig : public Animal {
public:
    void makeSound() override { // Ota klass metodini qayta yozamiz
        cout << "Cho'chqa: Xur-xur!" << endl;
    }
};

// Derived Class 2
class Dog : public Animal {
public:
    void makeSound() override { // Ota klass metodini qayta yozamiz
        cout << "It: Vov-vov!" << endl;
    }
};

int main() {
    // Ota klass ko'rsatkichi (pointer) orqali turli bola obyektlarni boshqarish
    Animal* myAnimal;

    Pig myPig;
    Dog myDog;

    myAnimal = &myPig;
    myAnimal->makeSound(); // Natija: Cho'chqa: Xur-xur!

    myAnimal = &myDog;
    myAnimal->makeSound(); // Natija: It: Vov-vov!

    return 0;
}

```

---

## 4. Sof Virtual Funksiyalar va Abstrakt Klasslar (Pure Virtual Functions)

Ba'zan ota klassda metodning umumiy mantig'ini yozishning imkoni bo'lmaydi (masalan, shunchaki `Shape` (Shakl) klassi bo'lsa, uning yuzasini hisoblab bo'lmaydi, har bir shakl `Circle`, `Rectangle` o'zi hisoblashi kerak).

Bunday holatda **Pure Virtual Function** ishlatiladi:

```cpp
virtual void draw() = 0; // Sof virtual funksiya

```

* Kamida bitta sof virtual funksiyaga ega bo'lgan klass **Abstrakt Klass (Abstract Class)** deyiladi.
* Abstrakt klassdan to'g'ridan-to'g'ri obyekt yaratib bo'lmaydi (`Shape s;`  Xatolik).
* Voris olgan bola klasslar ushbu sof virtual funksiyani **albatta `override` qilib yozishi shart**.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

// Abstrakt Klass
class Shape {
public:
    // Pure Virtual Function
    virtual void draw() = 0; 
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Doira chizildi." << endl;
    }
};

class Rectangle : public Shape {
public:
    void draw() override {
        cout << "To'rtburchak chizildi." << endl;
    }
};

int main() {
    // Shape s;  XATOLIK! Abstrakt klassdan obyekt olib bo'lmaydi.

    Shape* shape1 = new Circle();
    Shape* shape2 = new Rectangle();

    shape1->draw(); // Doira chizildi.
    shape2->draw(); // To'rtburchak chizildi.

    delete shape1;
    delete shape2;

    return 0;
}

```

---
