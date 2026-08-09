# C++ Shablonlari (Templates)

**Shablon (Template)** — ma'lumot turidan (data type) qat'i nazar ishlaydigan umumiy (**generic**) kod yozish imkonini beruvchi C++ ning qudratli mexanizmidir.

Shablonlar yordamida bir xil mantiqqa ega bo'lgan funksiya yoki klasslarni har bir ma'lumot turi (`int`, `double`, `float`, `string`) uchun alohida qayta-qayta yozib o'tirmasdan, bitta umumiy **qolip (blueprint)** sifatida yaratish mumkin. Bu **DRY (Don't Repeat Yourself)** tamoyiliga to'liq mos keladi.

---

## 1. Funksiya Shablonlari (Function Templates)

Agar sizga ikkita sonning eng kattasini topuvchi funksiya kerak bo'lsa, `int`, `double` va `float` turlari uchun alohida Overloading qilish o'rniga bitta funksiya shabloni yoziladi.

Sintaksisda **`template <typename T>`** yoki **`template <class T>`** ishlatiladi (`T` — ixtiyoriy ma'lumot turining o'rniga o'tuvchi generic tur).

### Kod Namunasi:

```cpp
#include <iostream>
#include <string>
using namespace std;

// Funksiya shabloni
template <typename T>
T getMax(T a, T b) {
    return (a > b) ? a : b;
}

int main() {
    // int turi uchun
    cout << "Max (int): " << getMax<int>(10, 20) << endl; // 20

    // double turi uchun
    cout << "Max (double): " << getMax<double>(5.5, 2.3) << endl; // 5.5

    // char turi uchun (Kompilyator turini avtomatik aniqlaydi)
    cout << "Max (char): " << getMax('a', 'z') << endl; // z

    return 0;
}

```

---

## 2. Bir Nechta Parametrli Shablonlar (Multiple Template Parameters)

Funksiya yoki klass bir vaqtning o'zida har xil ma'lumot turlari bilan ishlashi kerak bo'lsa, bir nechta parametr ko'rsatiladi:

```cpp
#include <iostream>
#include <string>
using namespace std;

// Ikkita har xil turdagi parametrlarni qabul qiluvchi shablon
template <typename T, typename U>
void printPair(T first, U second) {
    cout << "1-qiymat: " << first << " | 2-qiymat: " << second << endl;
}

int main() {
    printPair(101, "Shoxboz"); // int va string
    printPair("GPA", 3.95);      // string va double
    printPair('A', 100);         // char va int

    return 0;
}

```

---

## 3. Klass Shablonlari (Class Templates)

Klass shablonlari generic ma'lumotlar tuzilmalarini (masalan: `Vector`, `Stack`, `Queue`, `LinkedList`) yaratishda ishlatiladi.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

// Klass shabloni
template <typename T>
class Number {
private:
    T val;

public:
    Number(T v) : val(v) {}

    T getValue() const {
        return val;
    }

    T square() {
        return val * val;
    }
};

int main() {
    // int turi uchun obyekt
    Number<int> intNum(7);
    cout << "Int kvadrat: " << intNum.square() << endl; // 49

    // double turi uchun obyekt
    Number<double> doubleNum(2.5);
    cout << "Double kvadrat: " << doubleNum.square() << endl; // 6.25

    return 0;
}

```

---

## 4. Shablon Ixtisoslashuvi (Template Specialization)

Ba'zan umumiy shablon mantiqiy ravishda ma'lum bir ma'lumot turi uchun to'g'ri kelmasligi mumkin. Shunday paytda o'sha aniq tur uchun **alohida maxsus mantiq (specialization)** yoziladi.

```cpp
#include <iostream>
using namespace std;

// 1. Umumiy shablon
template <typename T>
class Printer {
public:
    void print(T val) {
        cout << "Umumiy qiymat: " << val << endl;
    }
};

// 2. Aniq 'char' turi uchun ixtisoslashgan shablon (Template Specialization)
template <>
class Printer<char> {
public:
    void print(char val) {
        cout << "Belgi (char): '" << val << "' (ASCII: " << (int)val << ")" << endl;
    }
};

int main() {
    Printer<int> p1;
    p1.print(100); // Umumiy qiymat: 100

    Printer<char> p2;
    p2.print('A'); // Belgi (char): 'A' (ASCII: 65)

    return 0;
}

```

---
