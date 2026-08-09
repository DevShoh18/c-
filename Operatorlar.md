# C++ Operatorlari (Operators)

**Operatorlar** — o'zgaruvchilar va qiymatlar ustida turli matematik, mantiqiy va solishtirish amallarini bajarish uchun ishlatiladigan maxsus belgilar.

---

## 1. Arifmetik Operatorlar (Arithmetic Operators)

Matematik hisob-kitoblarni bajarish uchun ishlatiladi.

| Operator | Nomi | Tavsifi | Misol (`x = 10, y = 3`) |
| --- | --- | --- | --- |
| **`+`** | Qo'shish | Ikki qiymatni qo'shadi | `x + y` $\rightarrow$ `13` |
| **`-`** | Ayrish | Biri ikkinchisidan ayiradi | `x - y` $\rightarrow$ `7` |
| **`*`** | Ko'paytirish | Ikki qiymatni ko'paytiradi | `x * y` $\rightarrow$ `30` |
| **`/`** | Bo'lish | Biri ikkinchisiga bo'ladi (butun qismi) | `x / y` $\rightarrow$ `3` |
| **`%`** | Qoldiq (Modulo) | Bo me'yoridagi qoldiqni qaytaradi | `x % y` $\rightarrow$ `1` |
| **`++`** | Inkrement | Qiymatni 1 ga oshiradi | `++x` $\rightarrow$ `11` |
| **`--`** | Dekrement | Qiymatni 1 ga kamaytiradi | `--x` $\rightarrow$ `9` |

### Kichik Misol:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 3;
    
    cout << "Qo'shish: " << a + b << endl; // 13
    cout << "Qoldiq: " << a % b << endl;   // 1
    
    a++; // a endi 11
    cout << "Inkrement: " << a << endl;   // 11
    return 0;
}

```

---

## 2. Biriktirish Operatorlari (Assignment Operators)

O'zgaruvchilarga qiymat biriktirish va bir vaqtning o'zida amal bajarish uchun ishlatiladi.

| Operator | Tenglamasi | Uning to'liq ko'rinishi | Misol (`x = 10`) | Natija |
| --- | --- | --- | --- | --- |
| **`=`** | `x = 5` | `x = 5` | `x = 5` | `x = 5` |
| **`+=`** | `x += 3` | `x = x + 3` | `10 += 3` | `x = 13` |
| **`-=`** | `x -= 3` | `x = x - 3` | `10 -= 3` | `x = 7` |
| **`*=`** | `x *= 3` | `x = x * 3` | `10 *= 3` | `x = 30` |
| **`/=`** | `x /= 2` | `x = x / 2` | `10 /= 2` | `x = 5` |
| **`%=`** | `x %= 3` | `x = x % 3` | `10 %= 3` | `x = 1` |

### Kichik Misol:

```cpp
#include <iostream>
using namespace std;

int main() {
    int score = 50;
    score += 20; // score = score + 20 (70)
    score /= 2;  // score = score / 2  (35)
    
    cout << "Natijaviy ball: " << score; // 35
    return 0;
}

```

---

## 3. Taqqoslash Operatorlari (Comparison Operators)

Ikki qiymatni o'zaro solishtiradi va mantiqiy natija (`1` - `true` yoki `0` - `false`) qaytaradi.

| Operator | Nomi | Tavsifi | Misol (`x = 5, y = 3`) | Natija |
| --- | --- | --- | --- | --- |
| **`==`** | Tenglik | Qiymatlar teng bo'lsa `true` | `x == y` | `0` (false) |
| **`!=`** | Teng emas | Qiymatlar teng bo'lmasa `true` | `x != y` | `1` (true) |
| **`>`** | Katta | Chap qiymat o'ngdagidan katta bo'lsa `true` | `x > y` | `1` (true) |
| **`<`** | Kichik | Chap qiymat o'ngdagidan kichik bo'lsa `true` | `x < y` | `0` (false) |
| **`>=`** | Katta yoki teng | Katta yoki teng bo'lsa `true` | `x >= 5` | `1` (true) |
| **`<=`** | Kichik yoki teng | Kichik yoki teng bo'lsa `true` | `y <= 2` | `0` (false) |

### Kichik Misol:

```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 20;
    bool isAdult = (age >= 18);
    
    cout << "Kattalashganmi: " << isAdult; // 1 (true)
    return 0;
}

```

---

## 4. Mantiqiy Operatorlar (Logical Operators)

Mantiqiy shartlarni bir-biriga bog'lash uchun ishlatiladi.

| Operator | Nomi | Tavsifi | Misol (`x = 5`) | Natija |
| --- | --- | --- | --- | --- |
| **`&&`** | Logical AND (VA) | Har ikkala shart ham `true` bo'lsa `true` qaytaradi | `x > 2 && x < 10` | `1` (true) |
| **`||`** | Logical OR (YOKI) | Kamida bitta shart `true` bo'lsa `true` qaytaradi | `x == 5 || x == 10` | `1` (true) |
| **`!`** | Logical NOT (EMAS) | Natijani qarama-qarshisiga o'zgartiradi | `!(x == 5)` | `0` (false) |

### Kichik Misol:

```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 22;
    bool hasLicense = true;

    // Haydash uchun yoshi 18 dan katta VA prava bo'lishi kerak
    bool canDrive = (age >= 18) && hasLicense;
    cout << "Ruxsat bormi: " << canDrive; // 1 (true)
    return 0;
}

```

---

## 5. Bitli Operatorlar (Bitwise Operators)

Sonlarning ikkilik (binary - `0` va `1`) ko'rinishidagi har bir bit ustida amallar bajaradi.

| Operator | Nomi | Tavsifi | Misol (`A = 5 (0101)`, `B = 3 (0011)`) |
| --- | --- | --- | --- |
| **`&`** | Bitwise AND | Har ikki bit `1` bo'lgandagina `1` beradi | `A & B` $\rightarrow$ `1` (`0001`) |
| **`|`** | Bitwise OR | Kamida bitta bit `1` bo'lsa `1` beradi | `A | B` $$\rightarro$ `7` (`0111`) |
| **`^`** | Bitwise XOR | Bitlar har xil bo'lsa `1` beradi | `A ^ B` $\rightarrow$ `6` (`0110`) |
| **`~`** | Bitwise NOT | Barcha bitlarni qarama-qarshisiga o'giradi | `~A` $\rightarrow$ `-6` |
| **`<<`** | Left Shift | Bitlarni chapga suradi (2 ga ko'paytiradi) | `A << 1` $\rightarrow$ `10` (`1010`) |
| **`>>`** | Right Shift | Bitlarni o'ngga suradi (2 ga bo'ladi) | `A >> 1` $\rightarrow$ `2` (`0010`) |

### Kichik Misol:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 5;  // Binary: 0101
    int b = 3;  // Binary: 0011

    cout << "AND: " << (a & b) << endl; // 1
    cout << "OR:  " << (a | b) << endl; // 7
    cout << "Left Shift: " << (a << 1) << endl; // 10
    return 0;
}

```
