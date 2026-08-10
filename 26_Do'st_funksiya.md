# C++ Do'st Kalit So'zi (The `friend` Keyword)

C++ tilida **`friend`** kalit so'zi klassning **`private`** va **`protected`** a'zolariga (o'zgaruvchilar va metodlarga) tashqi funksiya yoki boshqa bir klassga to'g'ridan-to me'yorida **kirish ruxsatini (access authority)** berish uchun ishlatiladi.

Inkapsulatsiya qoidasiga ko'ra `private` a'zolar faqat klass ichidan ko'rinadi. Lekin ba'zi holatlarda ikkita alohida klass yoki tashqi funksiya bir-biri bilan juda yaqin ishlashi talab etiladi. Shunday paytda `friend` so'zi qo'llaniladi.

---

## 1. `friend` Funksiya (Friend Function)

Tashqi funksiya klass ichida `friend` sifatida e'lon qilinsa, u ushbu klassning barcha `private` va `protected` a'zolariga to'g'ridan-to'g'ri murojaat qila oladi.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

class Distance {
private:
    int meters;

public:
    Distance() : meters(0) {}

    // 1. friend funksiyani e'lon qilish
    friend int addFive(Distance d);
};

// 2. Tashqi funksiya tana qismi (Klass a'zosi emas!)
int addFive(Distance d) {
    // 'friend' bo'lgani uchun 'private' o'zgaruvchi 'meters' ga to'g'ridan-to'g'ri kiradi
    d.meters += 5;
    return d.meters;
}

int main() {
    Distance dist;
    cout << "Masofa: " << addFive(dist) << " metr" << endl; // Natija: 5 metr
    return 0;
}

```

---

## 2. `friend` Klass (Friend Class)

Bitta klass boshqa bir klass ichida `friend` qilib e'lon qilinsa, usha ikkinchi klassning barcha `private` va `protected` a'zolari birinchi klass uchun ochiq bo'ladi.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

class Square; // Forward Declaration (Oldindan e'lon qilish)

class Rectangle {
private:
    int width, height;

public:
    int area() {
        return width * height;
    }

    // Square klassidagi metoddan ma'lumot olish uchun 'friend' qilamiz
    void convert(Square a);
};

class Square {
private:
    int side;

public:
    Square(int a) : side(a) {}

    // Rectangle klassini 'friend' sifatida e'lon qilamiz
    friend class Rectangle;
};

void Rectangle::convert(Square a) {
    // Rectangle 'Square' ning private 'side' o'zgaruvchisiga bemalol kiradi
    width = a.side;
    height = a.side;
}

int main() {
    Square sq(4);
    Rectangle rect;

    rect.convert(sq);
    cout << "Kvadratdan hosil bo'lgan to'rtburchak yuzi: " << rect.area() << endl; // Natija: 16

    return 0;
}

```

---

## 3. `friend` Muhim Qoidalari va Hususiyatlari

1. **Bir tomonlama bo'lishi (Not Symmetric):**
Agar `Class A` `Class B` ni o'ziga `friend` qilsa, `Class B` avtomatik tarzda `Class A` ni o'ziga `friend` hisoblamaydi. (A B ga do'st deb ishonsa ham, B A ga avtomatik ishonmaydi).
2. **Uzatilmasligi (Not Transitive):**
Agar A B ning do'sti bo'lsa va B C ning do'sti bo'lsa, A C ning do'sti bo'la olmaydi.
3. **Meros qolmasligi (Not Inherited):**
Ota klassning `friend` funksiyasi yoki klassi bola klass uchun avtomatik `friend` bo'lib o'tmaydi.

---

## 4. Qachon va Qayerda Ishlatiladi?

* **Operatorlarni qayta yuklashda (Operator Overloading):**
Ayniqsa `<<` (cout) va `>>` (cin) operatorlarini o'zingiz yaratgan klasslar uchun qayta yuklashda `friend` funksiyalar keng qo'llaniladi:
```cpp
friend ostream& operator<<(ostream& output, const MyClass& obj);

```
