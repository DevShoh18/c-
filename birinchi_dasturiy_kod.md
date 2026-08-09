# Ishchi Muhitni Sozlash (IDE) va Birinchi Dasturni Ishga Tushirish

Ushbu qismda biz C++ kodlarini yozish va ishga tushirish uchun kerak bo'ladigan ishchi muhitni (Development Environment) sozlashni hamda kompyuteringizda birinchi C++ dasturini yaratishni qadamma-qadam ko'rib chiqamiz.

---

## 1. Onlayn Muharrirlar (Hech narsani o'rnatmasdan sinab ko'rish)

C++ dasturlash tilini o'rganishni boshlash uchun kompyuteringizga dasturlar o'rnatish shart emas. Kodni bevosita brauzerning o'zida yozib, natijani ko'rish imkonini beruvchi **Online C++ Editor**lar mavjud:

* **W3Schools Online C++ Editor** — Boshlovchilar uchun sodda va tezkor.
* **OnlineGDB** — Interaktiv konsol va nosozliklarni tuzatish (debug) imkoniyatiga ega.
* **Compiler Explorer (godbolt.org)** — Kodning Assembly darajasida qanday kompilatsiya bo'lishini ko'rish uchun professional vosita.

---

## 2. Mahalliy Muhit (Local Environment): IDE Nima?

Agarda siz doimiy va mukammal dasturlar yaratmoqchi bo'lsangiz, kompyuteringizga mahalliy ishchi muhitni o'rnatishingiz kerak. Buning uchun 2 ta asosiy komponent talab etiladi:

1. **Matn Muharriri (Text Editor):** Kod yozish uchun (`.cpp` fayllar bilan ishlash).
2. **Kompilyator (Compiler):** Siz yozgan kodni kompyuter tushunadigan mashina tiliga (0 va 1 larga) o'giruvchi dastur (masalan, GCC/MinGW, Clang, MSVC).

Ushbu ikki vositani va nosozliklarni tuzatuvchi (Debugger) tizimni bitta dasturga biriktirilgan shakli **IDE (Integrated Development Environment — Integratsiyalashgan Rivojlanish Muhiti)** deb ataladi.

### Ommabop C++ IDE va Muharrirlari:
* **Code::Blocks:** Boshlovchilar uchun juda yengil, bepul va qulay IDE.
* **Visual Studio (Community Edition):** Windows uchun Microsoft tomonidan yaratilgan eng mukammal, professional IDE.
* **VS Code (Visual Studio Code):** Juda mashhur va moslashuvchan muharrir (C++ kengaytmalari hamda MinGW kompilyatori bilan ishlatiladi).

---

## 3. Code::Blocks IDE sini O'rnatish (Tavsiya etiladi)

Biz o'quv jarayonining ushbu bosqichida **Code::Blocks** dasturidan foydalanamiz, chunki u o'zi bilan birga **MinGW (GCC)** kompilyatorini ham avtomatik o'rnatadi.

### O'rnatish Bosqichlari:

1. Rasmiy saytga o'ting: **http://www.codeblocks.org/downloads/binaries/**
2. **Windows** bo'limidan aynan **`codeblocks-XX.XXmingw-setup.exe`** faylini yuklab oling.
   > **MUHIM:** Fayl nomida **`mingw-setup`** so'zi bo'lishi SHART! Aks holda kompyuteringizga kompilyator o'rnatilmaydi va kodingiz ishlamaydi.
3. Yuklab olingan `.exe` faylini ishga tushiring va standart ko'rsatmalarga amal qilib (`Next` -> `I Agree` -> `Install`) o'rnatishni yakunlang.

---

## 4. Birinchi C++ Loyihasini Yaratish va Ishga Tushirish (Quickstart)

Endi o'zingizning birinchi C++ faylingizni yaratamiz va ishga tushiramiz:

### 1-Qadam: Fayl Yaratish
1. **Code::Blocks** dasturini oching.
2. Yuqori menyudan **File > New > Empty File** (yoki klaviaturadan `Ctrl + Shift + N`) tugmalarini bosing.

### 2-Qadam: Kodni Kiriting
Ochilgan bo'sh sahifaga quyidagi C++ kodini yozing:

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello World!";
    return 0;
}
```
### 3-Qadam: Faylni Saqlash
1. Menyudan **File > Save File as...** bo'limini tanlang (yoki `Ctrl + S`).
2. Fayl nomini **`myfirstprogram.cpp`** deb nomlang va kompyuteringizdagi qulay papkaga saqlang.
   > **Eslatib o'tamiz:** Fayl kengaytmasi albatta **`.cpp`** bo'lishi kerak!
---
### 4-Qadam: Kompilatsiya va Ishga Tushirish (Build & Run)
1. Yuqori uskunalar panelidagi **Yashil O'q va G'ildirakcha** piktogrammasini (**Build and run**) bosing (yoki klaviaturadan **F9** tugmasini bosing).
2. Dastur kompilatsiya bo'ladi va qora konsol oynasi (Terminal) paydo bo'lib, ekranga quyidagi yozuv chiqadi:

## Qisqa Tahlil

* **`#include <iostream>`** — Kiritish-chiqarish (`cout`, `cin`) kutubxonasi.
* **`using namespace std;`** — Standart nomlar fazosidan (`std::cout` o'rniga `cout`) foydalanish.
* **`int main()`** — Dasturning kirish nuqtasi (asosiy funksiya).
* **`cout << "..."`** — Matnni ekranga chiqarish obyekti va operatori (`<<`).
* **`return 0;`** — Funksiyani yakunlaydi, dastur xatosiz ishlaganini bildiradi.
* **`{}`** — Kod blokining boshlanishi va yakuni.

## Muhim Qoidalar

* **`;` (Nuqta-vergul):** Har bir buyruq oxirida qo'yilishi **shart**.
* **Case-sensitive:** Katta-kichik harflar farq qiladi (`cout` $\neq$ `Cout`).
* **Bo'sh joylar (White space):** Kompilyator bo'sh qator va joylarni e'tiborsiz qoldiradi.
