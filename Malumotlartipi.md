# C++ Ma'lumot Turlari: Hayotiy Misol (Data Types Real-Life Example)

Dasturlashda ma'lumot turlari hayotiy loyihalarda birgalikda ishlatiladi. Quyida xarid cheki (order receipt) tizimi misolida barcha asosiy ma'lumot turlari (`string`, `int`, `double`, `char`, `bool`) qanday qo'llanilishini ko'rib chiqamiz.

---

## 1. Hayotiy Kod Namunasi

```cpp
#include <iostream>
#include <string> // string bilan ishlash uchun
using namespace std;

int main() {
    // 1. Matnli ma'lumotlar (string)
    string customer_name = "Shoxboz";
    string item_name = "Simsiz Sichqoncha";

    // 2. Butun sonlar (int)
    int items_count = 50;

    // 3. O'nlik / Kasr sonlar (double)
    double cost_per_item = 9.99;
    double total_cost = items_count * cost_per_item;

    // 4. Bitta belgi (char)
    char currency = '$';

    // 5. Mantiqiy qiymat (bool)
    bool is_in_stock = true;
    bool is_vip_customer = true;

    // --- EKRANGA CHIQARISH ---
    cout << "=== XARID CHEKI ===" << "\n";
    cout << "Mijoz: " << customer_name << "\n";
    cout << "Mahsulot: " << item_name << "\n";
    cout << "Mavjudligi: " << (is_in_stock ? "Omborda bor" : "Tugagan") << "\n";
    cout << "--------------------" << "\n";
    cout << "Soni: " << items_count << " ta\n";
    cout << "Dona narxi: " << cost_per_item << currency << "\n";
    cout << "Jami summa: " << total_cost << currency << "\n";
    cout << "VIP chegirma qo'llanildimi: " << (is_vip_customer ? "Ha" : "Yo'q") << "\n";

    return 0;
}

```

---

## 2. Ishlatilingan Ma'lumot Turlari Tahlili

| Tur (Data Type) | O'zgaruvchi | Hayotiy Ma'nosi | Qiymat Misoli |
| --- | --- | --- | --- |
| **`string`** | `customer_name`, `item_name` | So'zlar va matnli nomlar | `"Shoxboz"`, `"Sichqoncha"` |
| **`int`** | `items_count` | Donalab sanaladigan butun miqdorlar | `50` |
| **`double`** | `cost_per_item`, `total_cost` | Aniqlik talab qiladigan pul/narx qiymatlari | `9.99`, `499.5` |
| **`char`** | `currency` | Bitta belgi yoki valyuta belgisi | `'$'` |
| **`bool`** | `is_in_stock`, `is_vip_customer` | Ha/Yo'q (`true`/`false`) ko'rinishidagi holatlar | `true` (1), `false` (0) |

---

## 3. Konsoldagi Natija

```text
=== XARID CHEKI ===
Mijoz: Shoxboz
Mahsulot: Simsiz Sichqoncha
Mavjudligi: Omborda bor
--------------------
Soni: 50 ta
Dona narxi: 9.99$
Jami summa: 499.5$
VIP chegirma qo'llanildimi: Ha

```
