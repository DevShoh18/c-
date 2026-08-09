# C++ Shart Operatorlari (If ... Else)

C++ da mantiqiy shartlarga tayangan holda kodingizning muayyan qismlarini ishga tushirish yoki o'tkazib yuborish uchun **`if`**, **`else`** va **`else if`** operatorlaridan foydalaniladi.

C++ quyidagi shart operatorlarini qo'llab-quvvatlaydi:

* **`if`** — Ko'rsatilgan shart `true` (rost) bo'lsa, kod blokini bajaradi.
* **`else`** — Xuddi shu shart `false` (yolg'on) bo'lsa, boshqa kod blokini bajaradi.
* **`else if`** — Birinchi shart `false` bo'lsa, yangi shartni tekshirish uchun ishlatiladi.
* **`switch`** — Bajarilishi kerak bo'lgan ko me'mordagi ko'plab muqobil kod bloklaridan birini tanlaydi (keyingi darslarda o'tiladi).

---

## 1. `if` Operator

Ager shart `true` bo'lsa, `{}` ichidagi kod bajariladi.

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 20;
    int y = 18;

    if (x > y) {
        cout << "x soni y dan katta!";
    }

    return 0;
}

```

---

## 2. `else` Operator

Agarda `if` ichidagi shart bajarilmasa (`false` bo'lsa), `else` bloki ishga tushadi.

```cpp
#include <iostream>
using namespace std;

int main() {
    int time = 20;

    if (time < 18) {
        cout << "Xayrli kun!";
    } else {
        cout << "Xayrli kech!";
    }
    // Natija: Xayrli kech!

    return 0;
}

```

---

## 3. `else if` Operator

Ketma-ket bir nechta shartlarni tekshirish uchun ishlatiladi.

```cpp
#include <iostream>
using namespace std;

int main() {
    int score = 85;

    if (score >= 90) {
        cout << "Baho: A (A'lo)";
    } else if (score >= 80) {
        cout << "Baho: B (Yaxshi)";
    } else if (score >= 70) {
        cout << "Baho: C (Qoniqarli)";
    } else {
        cout << "Baho: F (Yiqildi)";
    }

    return 0;
}

```

---

## 4. Qisqa Shart Operator (Ternary Operator)

Oddiy `if...else` blokining o'rniga **Ternar operator (`? :`)** orqali 1 qatorli qisqartirilgan shakldan foydalanish mumkin:

```cpp
o'zgaruvchi = (shart) ? qiymat_agar_true : qiymat_agar_false;

```

### Taqqoslash:

**Odatiy usul:**

```cpp
int time = 20;
string result;

if (time < 18) {
    result = "Xayrli kun!";
} else {
    result = "Xayrli kech!";
}

```

**Qisqa usul (Ternary Operator):**

```cpp
int time = 20;
string result = (time < 18) ? "Xayrli kun!" : "Xayrli kech!";
cout << result; // Natija: Xayrli kech!

```

---

## 5. Ichma-ich Shartlar (Nested If)

`if` bloki ichida boshqa bir `if...else` blokini joylashtirish mumkin:

```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 20;
    bool hasLicense = true;

    if (age >= 18) {
        if (hasLicense) {
            cout << "Avtomobil haydashingiz mumkin.";
        } else {
            cout << "Yoshingiz yetarli, lekin haydovchilik guvohnomangiz yo'q.";
        }
    } else {
        cout << "Yoshingiz hali 18 ga yetmagan.";
    }

    return 0;
}

```

---

## 6. Hayotiy Misol: Bankomat (ATM) Dan Pul Yechish

```cpp
#include <iostream>
using namespace std;

int main() {
    double balance = 500.0; // Hisobdagi pul ($)
    double withdrawAmount;

    cout << "Mavjud balans: $" << balance << endl;
    cout << "Qancha pul yechmoqchisiz: $";
    cin >> withdrawAmount;

    if (withdrawAmount <= 0) {
        cout << "Xatolik: Noto'g'ri summa kiritildi!" << endl;
    } else if (withdrawAmount > balance) {
        cout << "Xatolik: Hisobingizda yetarli mablag' mavjud emas!" << endl;
    } else {
        balance -= withdrawAmount;
        cout << "Muvaffaqiyatli! Yechildi: $" << withdrawAmount << endl;
        cout << "Qolgan balans: $" << balance << endl;
    }

    return 0;
}

```

---

## Qisqa Xulosa

| Operator / Usul | Qo'llanilishi | Sintaksis Namuna |
| --- | --- | --- |
| **`if`** | Yagona shartni tekshirish | `if (shart) { ... }` |
| **`else`** | Shart bajarilmagan holat uchun | `if (shart) { ... } else { ... }` |
| **`else if`** | Ko'p bosqichli shartlarni ketma-ket tekshirish | `if (1) { ... } else if (2) { ... }` |
| **Ternary (`? :`)** | Bir qatorli ixcham shart biriktirish | `(shart) ? true_qiymat : false_qiymat` |
