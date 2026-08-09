# C++ Kirish Cheklovchilari (Access Specifiers)

**Access Specifiers (Kirish cheklovchilari)** — klass a'zolariga (o'zgaruvchilar va metodlarga) qayerdan va qanday tartibda murojaat qilish mumkinligini belgilaydigan kalit so'zlardir.

Ular **Inkapsulatsiya (Encapsulation)** konsepsiyasining asosini tashkil qiladi va ma'lumotlarni tashqi noto'g'ri o'zgartirishlardan xavfsiz himoyalashga xizmat qiladi.

---

## 1. Uchta Asosiy Cheklovchi

C++ tilida 3 ta asosiy access specifier mavjud:

1. **`public` (Ochiq):** A'zolarga klass ichidan ham, klass tashqarisidagi har qanday joydan ham to'g'ridan-to'g'ri murojaat qilish mumkin.
2. **`private` (Yopiq / Shaxsiy):** A'zolarga **faqat shu klass ichidagi** metodlar orqali murojaat qilish mumkin. Tashqaridan to'g'ridan-to'g'ri kirish taqiqlanadi (Default holatda `class` a'zolari `private` bo'ladi).
3. **`protected` (Himoyalangan):** A'zolarga klass ichidan hamda **ushbu klassdan voris (Inheritance) olgan bola klasslar** ichidan murojaat qilish mumkin. Tashqaridan to'g'ridan-to'g'ri kirib bo'lmaydi.

---

## 2. Kirish Huquqlari Jadvali

| Cheklovchi (Specifier) | Klass Ichidan | Voris Sinflardan (Derived) | Tashqaridan (main) |
| --- | --- | --- | --- |
| **`public`** |  Ha |  Ha |  Ha |
| **`protected`** |  Ha |  Ha |  Yo'q |
| **`private`** |  Ha |  Yo'q |  Yo'q |

---

## 3. Kod Namunasi: `public`, `private` va `protected`

```cpp
#include <iostream>
using namespace std;

class BaseClass {
public:
    int publicVar = 1;     // Barcha joydan ochiq

protected:
    int protectedVar = 2;  // Faqat shu klass va bola klasslar uchun

private:
    int privateVar = 3;    // Faqat shu klass ichi uchun
};

class DerivedClass : public BaseClass {
public:
    void testAccess() {
        cout << publicVar << endl;    //  To'g'ri (public)
        cout << protectedVar << endl; //  To'g'ri (protected - voris sinf ichi)
        // cout << privateVar << endl; //  XATOLIK! (private - voris sinfda ko'rinmaydi)
    }
};

int main() {
    BaseClass obj;

    cout << obj.publicVar;    //  To'g'ri
    // cout << obj.protectedVar; //  XATOLIK! Tashqarida ruxsat yo'q
    // cout << obj.privateVar;   //  XATOLIK! Tashqarida ruxsat yo'q

    return 0;
}

```

---

## 4. Getter va Setter Metodlari Bilan Ishlash

Amaliyotda ma'lumotlar xavfsizligini ta'minlash uchun o'zgaruvchilar **`private`** qilinadi, ularga qiymat berish va o'qish uchun esa **`public`** bo'lgan **Getter** va **Setter** metodlari yoziladi:

```cpp
#include <iostream>
using namespace std;

class Employee {
private:
    double salary; // Private o'zgaruvchi (xavfsiz saqlanadi)

public:
    // Setter: Ma'lumotni mantiqiy tekshirib keyin biriktirish
    void setSalary(double s) {
        if (s > 0) {
            salary = s;
        } else {
            cout << "Xatolik: Maosh manfiy bo'lishi mumkin emas!" << endl;
        }
    }

    // Getter: Qiymatni xavfsiz qaytarish
    double getSalary() {
        return salary;
    }
};

int main() {
    Employee emp;
    emp.setSalary(5000.0); // Setter orqali qiymat beramiz
    cout << "Xodim maoshi: $" << emp.getSalary() << endl; // Getter orqali o'qiymiz

    return 0;
}

```

---

## 5. `class` vs `struct` Farqi

C++ tilida `class` va `struct` deyarli bir xil imkoniyatga ega (ikkalasi ham metodlar hamda konstruktorlarga ega bo'lishi mumkin). Asosiy farqi — ularning **default (sukunat bo'yicha)** access specifier'ida:

* **`class`** — agar cheklovchi ko'rsatilmassa, barcha a'zolar avtomatik **`private`** bo'ladi.
* **`struct`** — agar cheklovchi ko'rsatilmassa, barcha a'zolar avtomatik **`public`** bo'ladi.

---
