# C++ Foydalanuvchi Kiritishi (User Input)
Ekranga ma'lumot chiqarish uchun `cout` ishlatilgan bo'lsa, foydalanuvchidan klaviatura orqali ma'lumot o'qib olish uchun **`cin`** obyekti ishlatiladi.
`cin` obyekti ma'lumotlarni o'zgaruvchiga saqlash uchun **chiqarish operatori (`>>` — extraction operator)** bilan birga ishlaydi.
---
## 1. Asosiy Kod Namunasi
Quyidagi misolda foydalanuvchi konsolga son kiritadi, kiritilgan qiymat `x` o'zgaruvchisida saqlanadi va so'ngra ekranga qayta chiqariladi:
```cpp
#include <iostream>
using namespace std;
int main() {
    int x; 
    cout << "Biror son kiriting: "; // Ekranga ko'rsatma chiqarish
    cin >> x;                      // Klaviaturadan ma'lumotni x ga o'qib olish
    cout << "Siz kiritgan son: " << x; // Kiritilgan qiymatni ekranga chiqarish
    return 0;
}
```
---
## 2. Operatorlar Farqi

| Obyekt | Operator | Maqsadi / Harakati |
| --- | --- | --- |
| **`cout`** | **`<<`** *(Insertion)* | Ma'lumotni o'zgaruvchidan ekranga (konsolga) uzatadi |
| **`cin`** | **`>>`** *(Extraction)* | Klaviaturadan kiritilgan ma'lumotni o'zgaruvchiga oladi |
---
## 3. Amaliy Misol: Oddiy Kalkulyator (2 ta sonni qo'shish)
`cin` yordamida ketma-ket bir nechta o'zgaruvchiga ma me'yorida ma'lumot kiritish mumkin:
```cpp
#include <iostream>
using namespace std;
int main() {
    int x, y;
    int sum;

    cout << "Birinchi sonni kiriting: ";
    cin >> x;

    cout << "Ikkinchi sonni kiriting: ";
    cin >> y;

    sum = x + y;
    cout << "Yig'indi: " << sum;

    return 0;
}
```
