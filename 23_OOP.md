# C++ Obyektga Yo'naltirilgan Dasturlash (OOP)

**Obyektga Yo'naltirilgan Dasturlash (Object-Oriented Programming — OOP)** — dasturlash konsepsiyasi bo'lib, u dasturni funksiyalar va mantiqlar to'plami sifatida emas, balki **Klasslar (Classes)** va **Obyektlar (Objects)** deb ataluvchi tuzilmalar atrofida quradi.

OOP murakkab dasturlarni real olamdagi obyektlar ko'rinishida modellashtirish, kodni qayta ishlatish (reusability) va loyihani qo'llab-quvvatlashni osonlashtirish uchun xizmat qiladi.

---

## 1. Klass va Obyekt (Class & Object)

OOP ning ikki asosiy ustuni:

* **Klass (Class):** Obyekt yaratish uchun mo'ljallangan **qolip (blueprint / chizma)**. U o'zida obyektning **xususiyatlarini (Attributes / Variables)** va **xatti-harakatlarini (Methods / Functions)** jamlaydi.
* **Obyekt (Object):** Klass qolipidan yaratilgan **real xotiradagi nusxa (instance)**.

### Analogiya:

* `Class`: "Moshina" chizmasi (qanday rangi, tezligi va motor hajmi borligi yozilgan).
* `Object`: Bitta aniq ko me'morda turgan "Qora Chevrolet Gentra" (real obyekt).

---

## 2. Asosiy Sintaksis va Boshlang'ich Misol

```cpp
#include <iostream>
#include <string>
using namespace std;

// 1. Klass e'lon qilish
class Car {
public: // Kirish huquqi
    // Xususiyatlar (Attributes)
    string brand;
    string model;
    int year;

    // Metod (Method / Klass ichidagi funksiya)
    void startEngine() {
        cout << brand << " " << model << " motori o't oldi!" << endl;
    }
};

int main() {
    // 2. Obyekt yaratish
    Car myCar;

    // 3. Xususiyatlariga qiymat berish
    myCar.brand = "Chevrolet";
    myCar.model = "Gentra";
    myCar.year = 2023;

    // 4. Metodni chaqirish
    myCar.startEngine(); // Natija: Chevrolet Gentra motori o't oldi!

    return 0;
}

```

---

## 3. OOP ning 4 Ta Asosiy Ustuni (The 4 Pillars of OOP)

C++ OOP konsepsiyasi 4 ta asosiy tamoyilga tayanadi:

```
           +---------------------------------+
           |      OOP 4 Ta Ustuni           |
           +---------------------------------+
             |          |          |        |
    Encapsulation  Abstraction Inheritance Polymorphism

```

---

### A. Encapsulation (Inkapsulatsiya)

Ma'lumotlarni (o'zgaruvchilarni) to'g'ridan-to'g'ri tashqaridan o'zgartirishdan himoyalash va ularga kirishni faqat maxsus metodlar (Getter/Setter) orqali berish konsepsiyasi.

Buning uchun **Access Specifiers (Kirish Cheklovchilari)** ishlatiladi:

* **`public`** — Barcha joydan (klass ichidan ham, tashqaridan ham) kirish mumkin.
* **`private`** — Faqat klass ichidan kirish mumkin (tashqaridan berk).
* **`protected`** — Klass ichidan va undan voris olgan sinflardan kirish mumkin.

#### Inkapsulatsiya Misoli:

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    double balance; // Hisob balansi tashqaridan himoyalangan (private)

public:
    // Setter (Balansni xavfsiz o'zgartirish)
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    // Getter (Balansni xavfsiz o'qish)
    double getBalance() {
        return balance;
    }
};

int main() {
    BankAccount account;
    // account.balance = 1000;  XATOLIK! 'private' bo'lgani uchun to'g'ridan-to'g me'yorida kirib bo'lmaydi.
    account.deposit(500);      //  To'g'ri usul
    cout << "Balans: $" << account.getBalance(); // Natija: $500
    return 0;
}

```

---

### B. Abstraction (Abstraksiya)

Foydalanuvchiga faqat kerakli funksionallikni ko'rsatib, ortiqcha murakkab ichki tafsilotlar va ishlov berish mantiqlarini yashirish.

Masalan, siz mashinani tormozini bosganingizda uning orqasida qanday gidravlika va ishqalanish sodir bo'layotganini bilishingiz shart emas — shunchaki pedalni bosasiz.

C++ da abstraksiyaga **Abstrakt Klasslar (`virtual` funksiyalar)** orqali erishiladi.

---

### C. Inheritance (Vorislik)

Mavjud klassning xususiyatlari va metodlarini yangi yaratilayotgan klassga o'tkazish (meros qilib olish). Bu kod takrorlanishini oldini oladi.

* **Base Class (Ota / Baza klass):** Meros beruvchi.
* **Derived Class (Bola / Voris klass):** Meros oluvchi (`:` belgisi orqali voris olinadi).

#### Vorislik Misoli:

```cpp
#include <iostream>
#include <string>
using namespace std;

// Baza klass (Ota)
class Animal {
public:
    void eat() {
        cout << "Bu hayvon ovqatlanmoqda..." << endl;
    }
};

// Voris klass (Bola)
class Dog : public Animal {
public:
    void bark() {
        cout << "Vov-vov!" << endl;
    }
};

int main() {
    Dog myDog;
    myDog.eat();  // Otasidan meros qolgan metod (Natija: Bu hayvon ovqatlanmoqda...)
    myDog.bark(); // O'zining metodi (Natija: Vov-vov!)

    return 0;
}

```

---

### D. Polymorphism (Polimorfizm)

Polimorfizm — "ko'p shakllilik" degani. U bir xil nomli metod yoki operatsiyaga turli situatsiyalarda har xil xatti-harakat qilish imkoniyatini beradi.

Polimorfizmning 2 turi bor:

1. **Compile-time Polymorphism (Kompilyatsiya vaqtida):**
* *Function Overloading* (Bir xil nomli turli parametrli funksiyalar).
* *Operator Overloading* (Operatorlarga yangi ma'no biriktirish).


2. **Runtime Polymorphism (Bajarilish vaqtida):**
* *Method Overriding* — Ota klassdagi metodni bola klassda **`virtual`** kalit so'zi yordamida qayta yozish.



#### Polimorfizm Misoli (Runtime):

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    // 'virtual' kalit so'zi polimorfizmni ta'minlaydi
    virtual void makeSound() {
        cout << "Hayvon biror ovoz chiqarmoqda." << endl;
    }
};

class Cat : public Animal {
public:
    void makeSound() override { // Otasidagi metodni qayta yozish
        cout << "Miyov-miyov!" << endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() override {
        cout << "Vov-vov!" << endl;
    }
};

int main() {
    Animal* a1 = new Cat();
    Animal* a2 = new Dog();

    a1->makeSound(); // Natija: Miyov-miyov!
    a2->makeSound(); // Natija: Vov-vov!

    delete a1;
    delete a2;
    return 0;
}

```

---

## 4. Konstruktor va Destruktor (Constructors & Destructors)

* **Constructor (Konstruktor):** Obyekt yaratilgan zahoti avtomatik ravishda ishga tushadigan maxsus metod. U klass bilan bir xil nomlanadi va qaytarish turiga ega bo'lmaydi.
* **Destructor (Destruktor):** Obyekt xotiradan o'chirilayotganida (Scope tugaganda) avtomatik ishlaydi. Nomi oldiga `~` (tilda) belgisi qo'yiladi.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
public:
    string name;

    // Konstruktor (Parametrli)
    Student(string sName) {
        name = sName;
        cout << name << " uchun xotiradan joy ajratildi (Object Created)." << endl;
    }

    // Destruktor
    ~Student() {
        cout << name << " xotiradan o'chirildi (Object Destroyed)." << endl;
    }
};

int main() {
    Student st1("Shoxboz"); // Konstruktor avtomatik ishlaydi
    
    return 0; // main() tugashi bilan destruktor ishlaydi
}

```

---

## Qisqa Xulosa

| Tushuncha | Qisqa Ma'nosi | Misol / Kalit So'z |
| --- | --- | --- |
| **Class** | Obyekt yaratish uchun qolip (Blueprint) | `class Car { ... };` |
| **Object** | Klassdan olingan real xotiradagi nusxa | `Car gentra;` |
| **Encapsulation** | Ma'lumotlarni yashirish va himoyalash | `private`, `public`, `get/set` |
| **Abstraction** | Ortiqcha detallarni yashirib, muhim funksiyalarni ko'rsatish | `virtual`, Abstract Class |
| **Inheritance** | Ota klass xususiyatlarini bola klassga o'tkazish | `class Dog : public Animal` |
| **Polymorphism** | Bir xil metod nomining har xil vazifada ishlashi | `virtual`, `override` |
| **Constructor** | Obyekt tug'ilganda ishlaydigan metod | `Car() { ... }` |
| **Destructor** | Obyekt o'layotganda ishlaydigan metod | `~Car() { ... }` |
