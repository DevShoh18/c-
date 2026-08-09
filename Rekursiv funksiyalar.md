# C++ Rekursiya (Recursion)

**Rekursiya** — funksiyaning o'z-o'zini chaqirish jarayonidir. Rekursiv funksiya murakkab va katta muammolarni kichikroq o'xshash bo me'yordagi qismlarga bo'lib yechish imkonini beradi.

---

## 1. Rekursiyaning Asosiy Strukturasi

Har qanday to'g'ri yozilgan rekursiv funksiya **2 ta asosiy qismdan** iborat bo'lishi shart:

1. **To'xtash Sharti (Base Case):** Rekursiya o'z-o me me'yorini to'xtatishi kerak bo'lgan eng sodda holat. Agar to'xtash sharti yozilmasa, funksiya cheksiz ravishda o'zini chaqirib, **Stack Overflow (Stek to'lib ketishi)** xatoligini keltirib chiqaradi.
2. **Rekursiv Qadam (Recursive Step):** Funksiyaning o'zini kichiklashtirilgan (yoki o'zgartirilgan) parametrlar bilan qayta chaqirish qismi.

```cpp
void recursiveFunction(int n) {
    if (n <= 0) { // 1. TO'XTASH SHARTI (Base Case)
        return;
    }
    
    // Bajariladigan kod
    
    recursiveFunction(n - 1); // 2. REKURSIV QADAM (Recursive Call)
}

```

---

## 2. Oddiy Misol: 1 dan N gacha Bo'lgan Sonlar Yig'indisi

1 dan $N$ gacha bo'lgan sonlar yig'indisini hisoblashni `for` siklisiz, rekursiya yordamida yozib ko'raylik:

```cpp
#include <iostream>
using namespace std;

// Rekursiv funksiya
int sum(int k) {
    if (k > 0) {
        return k + sum(k - 1); // Rekursiv chaqiriq
    } else {
        return 0; // To'xtash sharti (k = 0 bo'lganda)
    }
}

int main() {
    int result = sum(10); // 10 + 9 + 8 + ... + 1 + 0
    cout << "1 dan 10 gacha yig'indi: " << result << endl; // Natija: 55
    return 0;
}

```

### Ishlash Mantiqi (Call Stack):

`sum(5)` chaqirilganda xotirada quyidagicha zanjir hosil bo'ladi:

```text
sum(5) = 5 + sum(4)
sum(4) = 4 + sum(3)
sum(3) = 3 + sum(2)
sum(2) = 2 + sum(1)
sum(1) = 1 + sum(0)
sum(0) = 0 (Base Case yetib kelindi!)

```

So'ngra qiymatlar orqaga qaytib hisoblanadi:
`0 -> 1 -> 3 -> 6 -> 10 -> 15`

---

## 3. Klassik Misol: Faktorialni Hisoblash ($N!$)

$N! = N \times (N-1) \times (N-2) \times \dots \times 1$

```cpp
#include <iostream>
using namespace std;

long long factorial(int n) {
    // To'xtash sharti: 0! va 1! har doim 1 ga teng
    if (n <= 1) {
        return 1;
    }
    // Rekursiv chaqiriq: n * (n - 1)!
    return n * factorial(n - 1);
}

int main() {
    int number = 5;
    cout << number << "! = " << factorial(number) << endl; // Natija: 120
    return 0;
}

```

---

## 4. Fibonachchi Ketma-ketligi

Fibonachchi sonlari: `0, 1, 1, 2, 3, 5, 8, 13, 21, ...` (Har bir son o'zidan oldingi ikkita sonning yig'indisiga teng).

```cpp
#include <iostream>
using namespace std;

int fibonacci(int n) {
    // To'xtash shartlari
    if (n <= 0) return 0;
    if (n == 1) return 1;

    // Rekursiv chaqiriq: F(n) = F(n-1) + F(n-2)
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    int pos = 6;
    cout << pos << "-o'rindagi Fibonachchi soni: " << fibonacci(pos) << endl; // Natija: 8
    return 0;
}

```

---

## 5. Rekursiya vs Sikllar (Iteration)

Dasturlashda ko'pincha rekursiv yechimni oddiy sikllar (`for`, `while`) orqali ham yozish mumkin. Ularning asosiy farqlari:

| Xususiyat | Rekursiya (Recursion) | Sikl (Iteration / Loops) |
| --- | --- | --- |
| **Kod uzunligi** | Kaltaroq va tushunarliroq (Daraxtlar, Graflar uchun) | Biroq ko'proq kod yozilishini talab qilishi mumkin |
| **Xotira sarfi** | Yuqori (Har bir chaqiriq uchun Stack xotiradan joy ajratiladi) | Kam (Faqat bitta hisoblagich o'zgaruvchisi uchun joy) |
| **Tezlik** | Funktsiya chaqiriqlari xarajatlari sababli sekinroq | Juda tez ishlaydi |
| **Cheksiz holat xavfi** | **Stack Overflow** (Dastur avariyaviy to'xtaydi) | Cheksiz sikl (Dastur javob bermay qoladi) |

---

## 6. Kritik Xatolar: Stack Overflow

Rekursiyada to'xtash sharti unutib qoldirilsa yoki noto'g'ri yozilsa, kompyuterning Stek xotirasi (Stack Memory) to'lib ketadi va dastur majburiy to'xtatiladi.

```cpp
//  XATO CODE: To'xtash sharti yo'q!
void badFunction(int n) {
    cout << n << " ";
    badFunction(n - 1); // Cheksiz chaqirilaveradi va Stack Overflow beradi
}

```

---

## Qisqa Xulosa

* **Rekursiya** — funksiyaning o'zini qayta-qayta chaqirishi.
* Har bir rekursiv funksiyada albatta **To'xtash sharti (Base Case)** bo'lishi shart.
* Murakkab strukturalar (Daraxtlar, Graflar, Binar qidiruv, Rekursiv saralash algoritmlari) bilan ishlashda rekursiya muqobilsiz qulaylik beradi.
* Oddiy arifmetik takrorlanishlar uchun xotira va tezlik nuqtai nazaridan klassik **sikllar (`for`/`while`)** ishlatgan ma'qul.
