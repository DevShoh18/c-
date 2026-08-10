# C++ Fayllar Bilan Ishlash (Files & Streams)

C++ dasturlash tilida fayllarga ma'lumot yozish yoki ulardan ma'lumotni o'qish uchun **`<fstream>`** standart kutubxonasidan foydalaniladi.

Fayllar bilan ishlash ma'lumotlarni kompyuter xotirasida (diskda) doimiy saqlash va dastur qayta ishga tushganda ham ulardan foydalanish imkonini beradi.

---

## 1. `<fstream>` Kutubxonasining 3 Ta Asosiy Sinflari

`<fstream>` kutubxonasi o'z ichiga 3 ta asosiy sinfni oladi:

1. **`ofstream` (Output File Stream):** Fayl yaratish va unga ma'lumot **yozish** uchun ishlatiladi.
2. **`ifstream` (Input File Stream):** Fayldan ma'lumotlarni **o'qish** uchun ishlatiladi.
3. **`fstream` (File Stream):** Bir vaqtning o'zida ham **yozish**, ham **o'qish** imkonini beradi.

---

## 2. Fayl Yaratish va Unga Yozish (`ofstream`)

Faylga ma'lumot yozish xuddi `cout <<` orqali ekranga ma'lumot chiqarish kabi oson kechadi.

```cpp
#include <iostream>
#include <fstream> // Fayllar bilan ishlash kutubxonasi
using namespace std;

int main() {
    // 1. 'ofstream' obyekti yaratiladi va fayl ochiladi (yoki yangi yaratiladi)
    ofstream myFile("filename.txt");

    // 2. Faylga ma'lumot yoziladi
    myFile << "Salom, C++ Fayllar bo'limiga xush kelibsiz!\n";
    myFile << "Bu ikkinchi qator matni.";

    // 3. Fayl yopiladi (Xotirani bo'shatish va ma'lumot saqlanishi uchun SHART)
    myFile.close();

    cout << "Faylga ma'lumot muvaffaqiyatli yozildi!" << endl;

    return 0;
}

```

---

## 3. Fayldan Ma'lumotni O'qish (`ifstream`)

Fayldan matnlarni qatorma-qator o'qib olish uchun **`getline()`** funksiyasidan foydalaniladi.

```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    // 1. Faylni o'qish rejimidida ochamiz
    ifstream myReadFile("filename.txt");
    string myText;

    // 2. Fayl muvaffaqiyatli ochilganini tekshiramiz
    if (myReadFile.is_open()) {
        // Fayl oxiriga yetguncha qatorma-qator o'qiymiz
        while (getline(myReadFile, myText)) {
            cout << myText << endl;
        }

        // 3. Faylni yopamiz
        myReadFile.close();
    } else {
        cout << "Xatolik: Faylni ochib bo'lmadi!" << endl;
    }

    return 0;
}

```

---

## 4. Fayl Ochish Rejimlari (File Open Modes)

Faylni ochishda unga qanday maqsadda murojaat qilinayotganini **`ios::`** bayroqlari (flags) orqali ko'rsatish mumkin:

| Rejim | Tavsifi |
| --- | --- |
| **`ios::out`** | Yozish rejimi (sukunat bo'yicha). Fayl bor bo'lsa, ichidagini o'chirib qayta yozadi. |
| **`ios::in`** | O'qish rejimi (sukunat bo'yicha). |
| **`ios::app`** | **Append (Qo'shish):** Fayl ichidagi mavjud ma'lumotlarni o'chirmasdan, **oxiriga** yangi ma'lumot qo'shadi. |
| **`ios::trunc`** | Fayl mavjud bo'lsa, uning ichini to'liq tozalab tashlaydi (Truncate). |
| **`ios::binary`** | Faylni matn shaklida emas, ikkilik (binary) formatda ochadi. |

### Fayl Oxiriga Ma'lumot Qo'shish (`ios::app`) Misoli:

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    // 'ios::app' bayrog'i ma'lumotni fayl oxiriga ulashni bildiradi
    ofstream myFile("filename.txt", ios::app);

    if (myFile.is_open()) {
        myFile << "\nBu yangi qo'shilgan 3-qator.";
        myFile.close();
        cout << "Ma'lumot fayl oxiriga qo'shildi!" << endl;
    }

    return 0;
}

```

---

## 5. Fayl Bilan Ishlashda Xavfsizlik Qoidalari

1. **Doim `is_open()` bilan tekshiring:** Fayl diskda mavjud bo'lmasligi, boshqa dastur tomonidan band bo'lishi yoki ruxsat yetarli bo'lmasligi mumkin.
2. **Doim `close()` qiling:** Fayl yopilmasa, ma'lumotlar diskka to'liq yozilmay xotirada (buffer) qolib ketishi va fayl korrupsiyaga uchrashi mumkin.
3. **Mavjudligini tekshirish:** `ifstream` orqali ochilgan fayl diskda bo'lmasa, dastur kutilmagan holatga tushmasligi uchun holatni nazorat qiling.

---

## 6. Amaliy Misol: Log (Kiritish-Chiqarish) Tizimi

Foydalanuvchi kiritgan matnlarni sanasi va vaqtsiz oddiy log shaklida saqlab boruvchi dastur:

```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

void addLog(const string& message) {
    ofstream logFile("app.log", ios::app);
    if (logFile.is_open()) {
        logFile << "[LOG]: " << message << "\n";
        logFile.close();
    }
}

int main() {
    addLog("Dastur ishga tushirildi.");
    addLog("Foydalanuvchi tizimga kirdi.");
    addLog("Dastur muvaffaqiyatli yakunlandi.");

    cout << "Loglar 'app.log' fayliga saqlandi." << endl;

    return 0;
}

```

---

## Qisqa Xulosa

| Sinf / Metod | Vazifasi |
| --- | --- |
| **`ofstream`** | Faylga yozish sinfi |
| **`ifstream`** | Fayldan o'qish sinfi |
| **`fstream`** | Ham o'qish, ham yozish sinfi |
| **`is_open()`** | Fayl muvaffaqiyatli ochilganini tekshiradi (`bool`) |
| **`getline(file, str)`** | Fayldan matnni qatorma-qator o'qiydi |
| **`close()`** | Faylni yopadi va resursni bo'shatadi |
