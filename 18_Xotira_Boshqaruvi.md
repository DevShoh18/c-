# C++ Xotirani Boshqarish (Memory Management)

C++ dasturlash tilining eng katta ustunliklaridan biri — bu kompyuter operativ xotirasini (RAM) to'g'ridan-to'g'ri va moslashuvchan boshqarish imkoniyatidir.

Dastur ishga tushganda unga ajratilgan xotira asosan ikkita muhim sohaga bo'linadi: **Stack** va **Heap**.

---

## 1. Stack va Heap Xotira Farqi

| Xususiyat | Stack (Stek) | Heap (Xip / Dinamik xotira) |
| --- | --- | --- |
| **Boshqarish** | Avtomatik (Kompilyator va OS tomonidan) | Qo'lda (Dasturchi tomonidan `new` / `delete`) |
| **Tezlik** | Juda tez (LIFO — Last In, First Out) | Nisbatan sekinroq |
| **Hajmi** | Cheklangan (Odatda bir necha Megabayt) | Juda katta (Kompyuterning mavjud RAM hajmi) |
| **Xizmat muddati** | Funksiya / Scope tugashi bilan avtomatik o'chiriladi | `delete` qilinmaguncha yoki dastur tugaguncha saqlanadi |

---

## 2. Dinamik Xotira Ajratish (`new` va `delete`)

Sikl va dastur bajarilishi jarayonida xotiradan joy ajratish **Dinamik xotira ajratish** deyiladi. Buning uchun **`new`** va **`delete`** operatorlaridan foydalaniladi.

* **`new`** — Heap xotiradan joy ajratadi va o'sha joyning xotira manzilini (ko'rsatkichni) qaytaradi.
* **`delete`** — `new` orqali ajratilgan xotirani tozalaydi va operatsion tizimga qaytaradi.

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

int main() {
    // Heap xotiradan int uchun joy ajratish va 25 qiymatini biriktirish
    int* ptr = new int(25);

    cout << "Manzil: " << ptr << endl;
    cout << "Qiymat: " << *ptr << endl;

    // Xotirani tozalash (SHART!)
    delete ptr;

    // Xavfsizlik uchun ko'rsatkichni nullptr ga tenglashtiramiz
    ptr = nullptr;

    return 0;
}

```

---

## 3. Dinamik Massivlar (`new[]` va `delete[]`)

Agar massiv o'lchami dastur ishga tushganidan keyin (masalan, foydalanuvchi kiritgan songa qarab) aniqlanishi kerak bo'lsa, dinamik massiv yaratiladi.

> **Diqqat:** Dinamik massivlarni bo'shatish uchun `delete` emas, **`delete[]`** ishlatiladi!

### Kod Namunasi:

```cpp
#include <iostream>
using namespace std;

int main() {
    int size;
    cout << "Massiv o'lchamini kiriting: ";
    cin >> size;

    // Dinamik massiv yaratish
    int* arr = new int[size];

    // Qiymatlarni to'ldirish
    for (int i = 0; i < size; i++) {
        arr[i] = (i + 1) * 10;
    }

    // Ekranga chiqarish
    cout << "Massiv elementlari: ";
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    // Dinamik massiv xotirasini bo'shatish
    delete[] arr;
    arr = nullptr;

    return 0;
}

```

---

## 4. Xotira Boshqaruvidagi Kritik Xatolar (Common Pitfalls)

Xotirani qo'lda boshqarishda uchraydigan 3 ta eng xavfli xatolik:

### A. Memory Leak (Xotira Sizib Chiqishi)

`new` orqali ajratilgan xotira `delete` qilib bo'shatilmasa, RAM to'lib boradi va dastur/tizim qotib qoladi.

```cpp
void badFunction() {
    int* ptr = new int(100);
    // delete ptr; unutilgan!
} // Funksiya tugadi, ptr o'chirildi, lekin Heap dagi xotira egallanganicha qoldi!

```

### B. Dangling Pointer (Osilib Qolgan Ko'rsatkich)

Xotira `delete` qilingandan so'ng ham ko'rsatkich o'sha o'chirilgan manzilga ishora qilib turishi.

```cpp
int* ptr = new int(50);
delete ptr; // Xotira bo'shatildi

//  Xatolik: O'chirilgan manzilga murojaat qilish (Undefined Behavior)
cout << *ptr; 

//  Yechim: delete dan keyin darhol ptr = nullptr; qilish

```

### C. Double Free (Ikki Marta Bo'shatish)

Bitta xotira manzilini ketma-ket ikki marta `delete` qilish dasturning birdaniga crash bo'lishiga olib keladi.

```cpp
int* ptr = new int(10);
delete ptr;
delete ptr; //  Crash: double free or corruption!

```

---

## 5. Zamonaviy C++: Aqlli Ko'rsatkichlar (Smart Pointers)

Zamonaviy C++ (C++11 va undan yuqori) da xotira sizib chiqishi (`Memory Leak`) xavfini yo'qotish uchun **Smart Pointers** (`std::unique_ptr`, `std::shared_ptr`) kiritilgan. Ular xotirani otomatizatsiyalashgan holda (Scope tugagach) o'zi `delete` qiladi.

```cpp
#include <iostream>
#include <memory> // Smart pointers uchun
using namespace std;

int main() {
    // Unique pointer yaratish
    unique_ptr<int> ptr = make_unique<int>(100);

    cout << *ptr << endl; // 100

    // 'delete' yozish shart emas! main() tugashi bilan xotira avtomatik tozalanadi.
    return 0;
}

```

---

## Qisqa Xulosa

| Amal | Operatsiyasi | Tozalash Usuli |
| --- | --- | --- |
| **Yagona obyekt yaratish** | `int* p = new int;` | `delete p;` |
| **Dinamik massiv yaratish** | `int* a = new int[10];` | `delete[] a;` |
| **Bo'shatgandan keyin** | `delete p;` | `p = nullptr;` |
| **Zamonaviy xavfsiz usul** | `std::unique_ptr` | Avtomatik tozalanadi |
