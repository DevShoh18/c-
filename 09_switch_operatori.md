# C++ Tanlash Operatori (Switch)

**`switch`** operatori bitta o'zgaruvchining qiymatiga qarab ko'plab muqobil kod bloklaridan birini tanlab ishga tushirish uchun ishlatiladi. U uzundan-uzun `if...else if` zanjirlarining o'rnini bosib, kodni o'qish va tushunishni ancha osonlashtiradi.

---

## 1. Sintaksis

```cpp
switch (ifoda) {
    case qiymat1:
        // ifoda == qiymat1 bo'lganda bajariladigan kod
        break;
    case qiymat2:
        // ifoda == qiymat2 bo'lganda bajariladigan kod
        break;
    default:
        // hech qaysi case mos kelmaganda bajariladigan kod
}

```

---

## 2. Asosiy Kod Namunasi

Hafta kunining tartib raqamiga qarab, kun nomini ekranga chiqaruvchi dastur:

```cpp
#include <iostream>
using namespace std;

int main() {
    int day = 4;

    switch (day) {
        case 1:
            cout << "Dushanba";
            break;
        case 2:
            cout << "Seshanba";
            break;
        case 3:
            cout << "Chorshanba";
            break;
        case 4:
            cout << "Payshanba";
            break;
        case 5:
            cout << "Juma";
            break;
        case 6:
            cout << "Shanba";
            break;
        case 7:
            cout << "Yakshanba";
            break;
        default:
            cout << "Noto'g'ri kun raqami kiritildi!";
    }

    return 0;
}
// Natija: Payshanba

```

---

## 3. `switch` Ning Asosiy Elementlari

* **`switch(ifoda)`** — Tekshirilishi kerak bo'lgan o'zgaruvchi yoki qiymat.
* **`case qiymat:`** — O'zgaruvchi ushbu qiymatga teng bo'lganda ishga tushadigan bo'lim.
* **`break`** — `switch` blokidan o'sha zohirda chiqib ketish buyrug'i.
> **Muhim:** Agar `break` yozilmasa, dastur keyingi `case` lardagi kodlarni ham (mos kelish-kelmasligidan qat'i nazar) ketma-ket bajarib ketadi (*Fall-through* hodisasi).


* **`default`** — Hech bir `case` mos kelmagan holatda ishlaydi (xuddi `else` kabi). U majburiy emas, lekin xatoliklarni oldini olish uchun yozish tavsiya etiladi.

---

## 4. Muhim Cheklovlar va Qoidalar

1. **Ma'lumot turlari:** `switch` faqat **butun sonlar** (`int`, `short`, `long`) hamda **belgilar (`char`)** bilan ishlaydi.
2. **`string` va `double` taqiqlangan:** C++ da `switch` ichiga `string` matnlari yoki o'nlik kasr sonlarni (`double`, `float`) to'g'ridan-to'g'ri qo'yib bo'lmaydi.
3. **Takrorlanmas case-lar:** Bir xil qiymatli ikkita `case` bo'lishi mumkin emas (masalan, ikkita `case 1:` xatolik beradi).

---

## 5. Hayotiy Misol: Mini Kalkulyator

`char` belgisiga qarab arifmetik amalni bajaruvchi dastur:

```cpp
#include <iostream>
using namespace std;

int main() {
    char op;
    double num1, num2;

    cout << "Amalni kiriting (+, -, *, /): ";
    cin >> op;

    cout << "Ikkita son kiriting: ";
    cin >> num1 >> num2;

    switch (op) {
        case '+':
            cout << "Natija: " << num1 + num2;
            break;
        case '-':
            cout << "Natija: " << num1 - num2;
            break;
        case '*':
            cout << "Natija: " << num1 * num2;
            break;
        case '/':
            if (num2 != 0) {
                cout << "Natija: " << num1 / num2;
            } else {
                cout << "Xatolik: Nolga bo'lish mumkin emas!";
            }
            break;
        default:
            cout << "Noto'g'ri matematik operator kiritildi!";
    }

    return 0;
}

```

---

## Qisqa Xulosa

| Kalit So'z | Vazifasi |
| --- | --- |
| **`switch`** | Tekshiriladigan ifodani va blokni e'lon qiladi |
| **`case`** | Aniq bir qiymat varianti va shartini belgilaydi |
| **`break`** | Shart bajarilgach, switch blokini tark etadi |
| **`default`** | Barcha variantlar mos kelmaganda zaxira kodi sifatida ishlaydi |
