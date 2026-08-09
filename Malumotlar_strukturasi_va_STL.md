# C++ Data Structures va STL (Standard Template Library)

**STL (Standard Template Library)** — C++ tilining standart kutubxonasi bo'lib, eng ko'p ishlatiladigan ma'lumotlar tuzilmalari va algoritmlarning samarali, universal (generic) va tayyor realizatsiyasini taqdim etadi.

STL arxitekturasi **3 ta asosiy ustun** va 1 ta yordamchi komponentdan iborat:

1. **Containers (Konteynerlar):** Ma'lumotlarni xotirada saqlovchi ma'lumotlar tuzilmalari.
2. **Iterators (Iteratorlar):** Konteyner elementlari bo'ylab harakatlanish va ularga kirish uchun ko'rsatkichsimon (`pointer-like`) interfeys.
3. **Algorithms (Algoritmlar):** Konteynerlardagi ma'lumotlarni saralash, qidirish, o'zgartirish va filtrlash uchun tayyor funksiyalar to'plami.
4. **Functors / Function Objects:** Algoritmlar xatti-harakatini moslashtirish uchun ishlatiladigan funksiya ob'ektlari.

---

## C++ Konteynerlari (Ma'lumotlar Tuzilmalari) Tasnifi

STL konteynerlari ma'lumotlarni xotirada saqlash va ularga murojaat qilish mantiqiga qarab **4 ta asosiy guruhga** bo'linadi:

### 1. Sequence Containers (Ketma-ket Konteynerlar)

Ma me'yorida ma'lumotlarni chiziqli (linear) ketma-ketlikda saqlaydi.

* **`std::array`:** Ruxsat berilgan hajmi o'zgarmas (static) bo me'yordagi xotira massivi.
* **`std::vector`:** Dinamik ravishda hajmi o'suvchi va qisqaruvchi massiv ($O(1)$ indeksi bo'yicha kirish).
* **`std::deque` (Double-ended Queue):** Ikki tomonlama dinamik navbat (boshi va oxiridan element qo'shish/o'chirish $O(1)$).
* **`std::list`:** Ikki tomonlama bog'langan ro'yxat (Doubly Linked List).
* **`std::forward_list`:** Bir tomonlama bog'langan ro'yxat (Singly Linked List).

### 2. Container Adapters (Konteyner Moslashtiruvchilar / Adapterlar)

Mavjud ketma-ket konteynerlar ustiga qurilgan, ma'lum bir mantiqiy cheklov va tartib bilan ishlaydigan tuzilmalar.

* **`std::stack`:** LIFO (Last-In, First-Out) tamoyilida ishlaydigan stek.
* **`std::queue`:** FIFO (First-In, First-Out) tamoyilida ishlaydigan navbat.
* **`std::priority_queue`:** Prioritetli navbat (elementlar har doim ustuvorligi bo'yicha saralanib turadi, odatda Heap / Piramida tuzilmasi).

### 3. Associative Containers (Tartiblangan Assotsiativ Konteynerlar)

Ma'lumotlarni kalit (`key`) yoki qiymat bo'yicha **daraxt simon (Red-Black Tree)** ko me'morda tartiblangan holda saqlaydi ($O(\log n)$ vaqt murakkabligi).

* **`std::set`:** Unikal (takrorlanmas) elementlar to'plami.
* **`std::multiset`:** Takrorlanuvchi elementlarni qabul qiluvchi to'plam.
* **`std::map`:** Unikal Kalit-Qiymat (`key-value`) juftliklari.
* **`std::multimap`:** Bitta kalitga bir nechta qiymat biriktirishga ruxsat beruvchi `key-value` lug'ati.

### 4. Unordered Associative Containers (Tartiblanmagan Assotsiativ Konteynerlar)

Ma'lumotlarni **Hesh-jadval (Hash Table)** tuzilmasi bo'yicha saqlaydi ($O(1)$ o'rtacha vaqt murakkabligi).

* **`std::unordered_set`:** Tartiblanmagan unikal to'plam.
* **`std::unordered_multiset`:** Tartiblanmagan takrorlanuvchi to'plam.
* **`std::unordered_map`:** Tartiblanmagan unikal `key-value` hesh-lug'ati.
* **`std::unordered_multimap`:** Tartiblanmagan takrorlanuvchi `key-value` hesh-lug'ati.

---
