# C++ Destruktorlari (Destructors)

**Destruktor (Destructor)** — bu obyektning hayot sikli tugaganida (ya'ni obyekt xotiradan o'chirilayotganda) **avtomatik ravishda ishga tushadigan** maxsus a'zo funksiya.

Konstruktor obyekt uchun resurslar va xotira ajratgan bo'lsa, destruktor o'sha ajratilgan resurslarni (dinamik xotira, ochiq fayllar, tarmoq ulanishlari) bo'shatish va tozalash (**cleanup**) uchun xizmat qiladi.

---

## 1. Destruktorning Qat'iy Qoidalari

1. **Nomi:** Destruktor nomi klass nomi bilan bir xil bo'ladi, faqat uning oldiga **`~` (tilda)** belgisi qo'yiladi (masalan: `~Car()`).
2. **Parametrlar va Qaytarish turi:** Destruktor **hech qanday parametr qabul qilmaydi** va qiymat qaytarmaydi (`void` ham yozilmaydi).
3. **Qayta yuklab bo'lmaydi (No Overloading):** Bitta klassda **faqat bitta** destruktor bo'lishi mumkin.
4. **Avtomatik chaqirilishi:** Obyekt ko'rinish doirasidan (`scope`) chiqqanda yoki `delete` operatori qo'llanilganda kompilyator destruktorni avtomatik chaqiradi.

---

## 2. Oddiy Misol: Bajarilish Ketma-ketligi

```cpp
#include <iostream>
using namespace std;

class Test {
public:
    // Konstruktor
    Test() {
        cout << "1. Konstruktor ishladi: Obyekt yaratildi!" << endl;
    }

    // Destruktor
    ~Test() {
        cout << "2. Destruktor ishladi: Obyekt xotiradan o'chirildi!" << endl;
    }
};

int main() {
    cout << "main() boshlandi..." << endl;

    {
        Test obj; // 'obj' local scope ichida yaratildi
    } // Block tugadi -> 'obj' xotiradan o'chiriladi va destruktor avtomatik ishlaydi

    cout << "main() tugamoqda..." << endl;

    return 0;
}
/* Natija:
main() boshlandi...
1. Konstruktor ishladi: Obyekt yaratildi!
2. Destruktor ishladi: Obyekt xotiradan o'chirildi!
main() tugamoqda...
*/

```

---

## 3. Amaliy Misol: Dinamik Xotirani Bo'shatish (Memory Leak ning Oldini Olish)

Destruktordan eng ko'p foydalaniladigan o'rin — bu `new` operatori orqali `Heap` xotiradan ajratilgan resurslarni `delete` qilib bo'shatishdir.

```cpp
#include <iostream>
using namespace std;

class ArrayHandler {
private:
    int* arr;
    int size;

public:
    // Konstruktorda dinamik xotira ajratamiz
    ArrayHandler(int s) {
        size = s;
        arr = new int[size]; // Heap xotiradan joy ajratish
        cout << size << " ta elementli dinamik massiv yaratildi." << endl;
    }

    // Destruktorda ajratilgan xotirani tozalaymiz
    ~ArrayHandler() {
        delete[] arr; // Xotira sizib chiqishi (Memory Leak) ning oldi olindi
        cout << "Dinamik xotira muvaffaqiyatli bo'shatildi!" << endl;
    }
};

int main() {
    ArrayHandler handler(1000); // 1000 ta int uchun joy ajratiladi

    return 0; // main() tugashi bilan destruktor ishga tushadi va xotira tozalanadi
}

```

---

## 4. Virtual Destruktorlar (Polimorfizmda Muhim!)

Agar sizda Vorislik (Inheritance) va Polimorfizm mavjud bo'lsa, ota klassning destruktorini **`virtual`** qilib e'lon qilish **shart**.

Aks holda, ota klass ko'rsatkichi (`Base pointer`) orqali bola klass obyekti o'chirilganda, bola klassning destruktori ishlamay qoladi va xotira sizib chiqishi (`Memory Leak`) yuzaga keladi.

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    Base() { cout << "Base Konstruktor\n"; }
    // Virtual destruktor!
    virtual ~Base() { cout << "Base Destruktor\n"; }
};

class Derived : public Base {
private:
    int* data;
public:
    Derived() { 
        data = new int[100];
        cout << "Derived Konstruktor\n"; 
    }
    ~Derived() override { 
        delete[] data;
        cout << "Derived Destruktor\n"; 
    }
};

int main() {
    Base* ptr = new Derived(); // Ota ko'rsatkichi orqali bola obyekt
    
    delete ptr; // 'virtual' bo'lgani uchun ketma-ket: Derived ~ -> Base ~ ishlaydi
    return 0;
}

```

---
