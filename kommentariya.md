# C++ Izohlari (Comments)
C++ da izohlar (kommentariyalar) kodni tushuntirish, o'qishni osonlashtirish va sinov jarayonida ma'lum koddagi buyruqlarni vaqtincha o'chirish uchun ishlatiladi. Kompilyator izohlarni e'tiborsiz qoldiradi.
---
## 1. Bir Qatorli Izohlar (Single-line Comments)
Bir qatorli izohlar ikkita o'ngga og'ish chizig'i (`//`) bilan boshlanadi. `//` va qator oxirigacha bo'lgan barcha matn kompilyator tomonidan o'qilmaydi.
### Kod Usti Izohi:

```cpp
// Bu bir qatorli izoh
cout << "Hello World!";
```
### Qator Oxiridagi Izoh:
```cpp
cout << "Hello World!"; // Bu qator oxiridagi izoh
```
---
## 2. Ko'p Qatorli Izohlar (Multi-line Comments)
Ko'p qatorli izohlar `/*` bilan boshlanib, `*/` bilan tugaydi. `/*` va `*/` orasidagi barcha matnlar kompilyator tomonidan e'tiborsiz qoldiriladi.
```cpp
/* Quyidagi kod ekranga Hello World!
so'zini chiqaradi va bu juda qulay */
cout << "Hello World!";
```
---
