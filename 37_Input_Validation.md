**C++ Input Validation (Kiritilgan ma'lumotlarni tekshirish)** — foydalanuvchi tomonidan kiritilgan ma'lumotlarning to'g'ri formatda (`int`, `double` va h.k.) hamda mantiqiy diapazonda ekanligini tekshirish usulidir.

Noto'g'ri ma'lumot kiritilganda (masalan, `int` o'zgaruvchiga harf kiritilsa), `std::cin` oqimi xatolik holatiga (`failbit`) tushadi va dastur cheksiz siklga (`infinite loop`) kirib qoladi yoki noto'g'ri ishlaydi.

---

### 1. Kirish Oqimini Tozalashning 3 Ta Asosiy Qadami

Ma'lumotni to'g'ri validation qilish uchun quyidagi 3 amaldan foydalaniladi:

1. **`cin.fail()`** — Kiritilgan ma'lumot turi o'zgaruvchi turiga mos kelmasa, `true` qaytaradi.
2. **`cin.clear()`** — `cin` oqimidagi xatolik bayrog'ini (`failbit`) tozalaydi va uni yana ma'lumot qabul qiladigan holatga keltiradi.
3. **`cin.ignore(numeric_limits<streamsize>::max(), '\n')`** — Kiritish buferida qolib ketgan keraksiz belgilarni (`\n` gacha) to'liq o'chirib tashlaydi.

---

### 2. Ma'lumot Turini Tekshirish (Type Validation)

Foydalanuvchi faqat butun son kiritishini ta'minlaydigan va noto'g'ri kiritsa qayta so'raydigan sikl:

```cpp
#include <iostream>
#include <limits> // numeric_limits uchun
using namespace std;

int getValidInteger() {
    int value;

    while (true) {
        cout << "Butun son kiriting: ";
        cin >> value;

        if (cin.fail()) { // Agar harf yoki belgi kiritilsa
            cin.clear(); // Xatolik holatini tozalaymiz
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); // Buferni tozalaymiz
            cout << "Xatolik: Siz son kiritmadingiz! Qayta urinib ko'ring.\n";
        } else {
            // Buferda qolgan keraksiz belgilarni tozalash (masalan: 12abc bo'lsa)
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            return value;
        }
    }
}

int main() {
    int num = getValidInteger();
    cout << "Muvaffaqiyatli kiritildi: " << num << endl;
    return 0;
}

```

---

### 3. Diapazonni Tekshirish (Range Validation)

Ma'lumot turi to'g'ri bo'lishi bilan birga, u ma'lum bir oralikda (masalan, yosh `1` dan `120` gacha) bo'lishini tekshirish:

```cpp
#include <iostream>
#include <limits>
using namespace std;

int getValidAge() {
    int age;

    while (true) {
        cout << "Yoshingizni kiriting (1-120): ";
        cin >> age;

        // Ham tur, ham diapazon tekshiriladi
        if (!cin.fail() && age >= 1 && age <= 120) {
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            return age;
        }

        cout << "Noto'g'ri yosh kiritildi! Qayta kiriting.\n";
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
    }
}

int main() {
    int age = getValidAge();
    cout << "Tasdiqlangan yosh: " << age << endl;
    return 0;
}

```

---
