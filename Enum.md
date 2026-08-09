# C++ Enum (Enumeration)

**`enum` (Enumeration — sanoqli tur)** — o'zgarmas nomlangan konstantalar to'plamini bitta umumiy nom ostida biriktiruvchi maxsus ma'lumot turi.

U koddagi tushunarsiz sonlar (masalan, `0`, `1`, `2`) o'rniga mantiqiy so'zlardan foydalanish imkonini beradi va kodning o'qilishini ancha soddalashtiradi.

---

## 1. Oddiy Enum Yaratish va Sintaksisi

Enum **`enum`** kalit so'zi orqali e'lon qilinadi:

```cpp
enum Level {
    LOW,    // Avtomatik 0 ga teng
    MEDIUM, // Avtomatik 1 ga teng
    HIGH    // Avtomatik 2 ga teng
};

```

Sikl va default holatda kompilyator `enum` ichidagi har bir elementga **0 dan boshlab** ketma-ket butun sonli (`int`) qiymatlarni biriktiradi.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

enum Level {
    LOW,    // 0
    MEDIUM, // 1
    HIGH    // 2
};

int main() {
    Level myVar = MEDIUM;

    // Ekranga uning butun sonli qiymati (1) chiqadi
    cout << "Daraja qiymati: " << myVar << endl; // Natija: 1

    return 0;
}

```

---

## 2. Konstantalar Qiymatini O'zgartirish

Enum elementlariga o'zingiz xohlagan butun sonli qiymatlarni biriktirishingiz mumkin:

```cpp
enum Level {
    LOW = 25,
    MEDIUM = 50,
    HIGH = 100
};

```

Agar faqat birinchi elementga qiymat berilsa, qolganlari avtomatik ravishda 1 ga oshib boradi:

```cpp
enum Level {
    LOW = 1, // 1
    MEDIUM,  // 2
    HIGH     // 3
};

```

---

## 3. `enum` va `switch` Operatori

Enum bilan ishlashning eng ko'p tarqalgan usullaridan biri — uni `switch` shart operatorida ishlatishdir:

```cpp
#include <iostream>
using namespace std;

enum Level {
    LOW = 1,
    MEDIUM,
    HIGH
};

int main() {
    Level myVar = HIGH;

    switch (myVar) {
        case LOW:
            cout << "Past daraja";
            break;
        case MEDIUM:
            cout << "O'rta daraja";
            break;
        case HIGH:
            cout << "Yuqori daraja";
            break;
    }

    return 0;
}
// Natija: Yuqori daraja

```

---

## 4. Zamonaviy C++: `enum class` (Scoped Enums)

Klassik `enum` dagi eng katta muammo — **nomlar toqnashuvi (Name Conflict)**. Agar ikkita turli `enum` ichida bir xil nomli kalit so'z bo'lsa, kompilyator xatolik beradi.

C++11 standartida bu muammoni hal qilish uchun **`enum class`** kiritilgan.

### Klassik va Scoped Enum Farqi:

```cpp
//  Klassik enum (Xatolik beradi, chunki 'GREEN' takrorlanyapti)
enum Color { RED, GREEN, BLUE };
enum TrafficLight { RED, YELLOW, GREEN }; 

//  Zamonaviy enum class (Xavfsiz va xatolik bo'lmaydi)
enum class Color { RED, GREEN, BLUE };
enum class TrafficLight { RED, YELLOW, GREEN };

int main() {
    // Qo'llanilishi: Chegara (Scope) aniq ko'rsatiladi
    Color myColor = Color::GREEN;
    TrafficLight myLight = TrafficLight::GREEN;

    return 0;
}

```

---

## 5. Hayotiy Misol: Buyurtma Holatini Boshqarish (Order Status)

Internet-do'konda buyurtma holatini kuzatish dasturi:

```cpp
#include <iostream>
using namespace std;

enum class OrderStatus {
    Pending,   // Kutilmoqda
    Processing,// Qayta ishlanmoqda
    Shipped,   // Yo'lga chiqdi
    Delivered, // Yetkazib berildi
    Cancelled  // Bekor qilindi
};

int main() {
    OrderStatus currentStatus = OrderStatus::Shipped;

    if (currentStatus == OrderStatus::Shipped) {
        cout << "Buyurtmangiz kuryer tomonidan yetkazilmoqda!" << endl;
    } else if (currentStatus == OrderStatus::Delivered) {
        cout << "Buyurtma topshirildi. Xaridingiz uchun rahmat!" << endl;
    }

    return 0;
}

```

---

## Qisqa Xulosa

| Tur | Sintaksis | Boshlang'ich Qiymat | Kirish Usuli | Xavfsizlik |
| --- | --- | --- | --- | --- |
| **Klassik `enum**` | `enum Level { LOW, HIGH };` | `0` | `LOW` | Past |
| **Scoped `enum class**` | `enum class Level { LOW, HIGH };` | `0` | `Level::LOW` | Yuqori (Tavsiya etiladi) |
