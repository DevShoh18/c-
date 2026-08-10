# C++ Break va Continue Operatorlari

Sikllar (`for`, `while`, `do...while`) hamda `switch` blokida dastur bajarilish oqimini tezkor va moslashuvchan boshqarish uchun **`break`** va **`continue`** operatorlaridan foydalaniladi.

---

## 1. `break` Operatori

**`break`** operatori sikl yoki `switch` blokining ishini **muddatidan oldin to'liq to'xtatadi**. Kompilyator `break` ga duch kelganda, siklning qolgan barcha takrorlanishlari bekor qilinadi va boshqaruv sikldan keyingi qatordan davom ettiriladi.

### Kod Namunasi (`for` siklida):

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i == 5) {
            break; // i 5 ga teng bo'lganda sikl to'liq to'xtaydi
        }
        cout << i << " ";
    }

    return 0;
}
// Natija: 1 2 3 4

```

---

## 2. `continue` Operatori

**`continue`** operatori siklni to'liqligicha to'xtatmaydi, balki **joriy takrorlanishni (iteratsiyani) o'tkazib yuboradi** va darhol siklning keyingi takrorlanishiga o'tib ketadi.

### Kod Namunasi (`for` siklida):

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i == 5) {
            continue; // i 5 ga teng bo'lganda faqat 5 ni o'tkazib yuboradi
        }
        cout << i << " ";
    }

    return 0;
}
// Natija: 1 2 3 4 6 7 8 9 10

```

---

## 3. `while` Siklida `continue` va Cheksiz Sikl Xavfi

`while` yoki `do...while` sikllarida `continue` ishlatilganda juda ehtiyot bo'lish kerak. Agar hisoblagich qiymatini oshirish (`i++`) `continue` dan pastda qolib ketsa, sikl hisoblagichi yangilanmaydi va **cheksiz sikl (infinite loop)** hosil bo'ladi.

### To'g'ri Qo'llash Namunasi:

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            i++; // MUHIM: continue dan oldin i ni oshirish shart!
            continue;
        }
        cout << i << " ";
        i++;
    }

    return 0;
}
// Natija: 0 1 2 3 5 6 7 8 9

```
---

## Qisqa Xulosa

| Operator | Vazifasi | Sikl Taqdiri |
| --- | --- | --- |
| **`break`** | Sikl yoki `switch` blokini **butunlay to'xtatadi** | Sikldan darhol chiqib ketiladi |
| **`continue`** | Joriy takrorlanishni **o'tkazib yuboradi** | Sikl keyingi takrorlanishdan davom etadi |
