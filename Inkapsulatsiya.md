# C++ Inkapsulatsiya (Encapsulation)

**Inkapsulatsiya (Encapsulation)** — bu ma'lumotlarni (a'zo o'zgaruvchilarni) va ular ustida ishlaydigan metodlarni **bitta birlik (klass)** ichida jamlash hamda ma'lumotlarga to'g'ridan-to'g'ri tashqaridan kirishni cheklash (yashirish) konsepsiyasidir.

Inkapsulatsiyaning oltin qoidasi:

1. Klass o'zgaruvchilarini **`private`** qilish.
2. Ushbu o'zgaruvchilar qiymatini o'qish va o'zgartirish uchun **`public` Getter va Setter** metodlaridan foydalanish.

---

## 1. Inkapsulatsiya Nima Uchun Kerak?

* **Nazorat va Validatsiya:** O'zgaruvchiga mantiqsiz qiymat biriktirilishining oldi olinadi (masalan, yosh yoki maoshga manfiy son berilishini taqiqlash).
* **Ma'lumotlar Xavfsizligi:** Muhim ma'lumotlar tashqi kod tomondan kutilmaganda o'zgartirib yuborilishidan himoyalanadi.
* **Faqat O'qiladigan (Read-Only) yoki Faqat Yoziladigan (Write-Only) Ma'lumotlar:** Agar `Setter` metodini yozmasangiz, o'zgaruvchini faqat o'qish mumkin bo'ladi.
* **Kodni Qo'llab-quvvatlash Osonligi:** Klass ichidagi mantiq va realizatsiya o'zgarsa ham, tashqi kodga zarar yetmaydi.

---

## 2. To'liq Kod Namunasi (Getter va Setter)

```cpp
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    // 1. Private o'zgaruvchilar (Tashqaridan berk)
    string ownerName;
    double balance;

public:
    // Konstruktor
    BankAccount(string name, double initialBalance) {
        ownerName = name;
        if (initialBalance >= 0) {
            balance = initialBalance;
        } else {
            balance = 0;
        }
    }

    // 2. Getter for ownerName (Read-Only)
    string getOwnerName() const {
        return ownerName;
    }

    // 3. Getter for balance
    double getBalance() const {
        return balance;
    }

    // 4. Setter/Method for balance (Validatsiya bilan xavfsiz to'ldirish)
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "$" << amount << " hisobga qo'shildi." << endl;
        } else {
            cout << "Xatolik: Qo'shiladigan summa 0 dan katta bo'lishi kerak!" << endl;
        }
    }

    // Money Withdrawal (Validatsiya bilan yechish)
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            cout << "$" << amount << " hisobdan yechildi." << endl;
        } else {
            cout << "Xatolik: Yetarli mablag' yo'q yoki noto'g'ri summa!" << endl;
        }
    }
};

int main() {
    BankAccount myAccount("Shoxboz", 1000.0);

    // myAccount.balance = 50000;  XATOLIK! 'private' a'zoga to'g'ridan-to'g'ri kirib bo'lmaydi

    // Getter orqali xavfsiz o'qiymiz
    cout << "Hisob egasi: " << myAccount.getOwnerName() << endl;
    cout << "Boshlang'ich balans: $" << myAccount.getBalance() << endl;

    // Metodlar orqali xavfsiz amallar bajaramiz
    myAccount.deposit(500.0);
    myAccount.withdraw(300.0);
    myAccount.withdraw(2000.0); // Xatolik beradi (balans yetmaydi)

    cout << "Yakuniy balans: $" << myAccount.getBalance() << endl;

    return 0;
}

```
---
## 3. Read-Only va Write-Only Tizim Yaratish
Metodlarni cheklash orqali kirish rejimini sozlashingiz mumkin:

| Kirish Rejimi | Getter Metodi | Setter Metodi | Vazifasi |
| --- | --- | --- | --- |
| **Read-Write** |  Mavjud |  Mavjud | Ma'lumotni ham o'qish, ham o'zgartirish mumkin |
| **Read-Only** |  Mavjud |  Yo'q | Ma'lumotni faqat o'qish mumkin (o'zgartirib bo'lmaydi) |
| **Write-Only** |  Yo'q |  Mavjud | Parol kabi ma'lumotlarni faqat yangilash mumkin, lekin o'qib bo'lmaydi |
---
