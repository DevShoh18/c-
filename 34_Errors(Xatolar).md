C++ tilida xatoliklar (**Errors**) yuz berish vaqti va sababiga qarab **3 ta asosiy turga** bo'linadi:

---

### 1. Syntax Errors (Sintaktik xatoliklar)

* **Nima:** C++ tili qoidalari va grammatikasining buzilishi.
* **Qachon aniqlanadi:** Kompilyatsiya vaqtida (**Compile-time**). Dastur kodi ishga tushmaydi.
* **Misol:** Nuqta-vergul `;` unutilishi yoki qavslar noto'g'ri yopilishi.

```cpp
int main() {
    cout << "Salom" //  Xatolik: ';' tushirib qoldirilgan
    return 0;
}

```

---

### 2. Runtime Errors (Bajarilish vaqtidagi xatoliklar)

* **Nima:** Kod sintaktik to'g'ri, lekin dastur bajarilayotgan vaqtda kutilmagan holat sababli majburiy to'xtashi (**crash** bo'lishi).
* **Qachon aniqlanadi:** Dastur ishlayotgan vaqtda (**Runtime**).
* **Misol:** Sonni 0 ga bo'lish, massiv chegarasidan chiqish yoki `nullptr` ga murojaat qilish.

```cpp
int a = 10;
int b = 0;
int c = a / b; //  Xatolik: Sonni 0 ga bo'lib bo'lmaydi (Dastur avariyaviy to'xtaydi)

```

---

### 3. Logical Errors (Mantiqiy xatoliklar)

* **Nima:** Dastur muvaffaqiyatli kompilyatsiya bo'ladi va o'chib ketmay ishlaydi, lekin **xato natija** beradi.
* **Qachon aniqlanadi:** Dasturchi natijani tekshirganda.
* **Misol:** Formulada `*` o'rniga `+` ishlatib qo'yish.

```cpp
int width = 5, height = 10;
int area = width + height; //  Mantiqiy xatolik: Yuza uchun '*' bo'lishi kerak edi

```

---
