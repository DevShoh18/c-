**C++ Debugging** — dasturdagi mantiqiy yoki runtime xatoliklarni (bug) topish, ularning sababini aniqlash va tuzatish jarayoni.

---

### 1. Asosiy Debugging Usullari

#### A. Output (Print) Debugging (`cout` orqali)

Eng sodda usul. Kod orasiga `cout` qo'yib, dastur qaysi nuqtagacha yetib kelganini va o'zgaruvchilar qiymatini tekshirish.

```cpp
cout << "DEBUG: i = " << i << " nuqtaga yetib keldi\n";

```

#### B. IDE Visual Debugger (VS Code, Visual Studio, CLion)

Eng qulay va professional usul. Dasturni qatorma-qator to'xtatib, xotiradagi holatni vizual kuzatish imkonini beradi.

#### C. GDB / LLDB (Terminal Debugger)

Linux va buyruqlar satrida ishlaydigan utilitalar.

* Kompilyatsiyada `-g` bayrog'i qo'shiladi (debug ma'lumotlarini biriktirish uchun):
```bash
g++ -g main.cpp -o main
gdb ./main

```



#### D. Sanitizers (Xotira xatolarini topuvchilar)

Xotira sizib chiqishi (`Memory Leak`) va noqonuniy xotiraga murojaatni avtomatik tutib beradi.

```bash
g++ -fsanitize=address -g main.cpp -o main

```

---

### 2. IDE Debugger Asosiy Buyruqlari

| Tushuncha / Tugma | Vazifasi |
| --- | --- |
| **Breakpoint** | Dastur bajarilishini ma'lum bir qatorda vaqtincha to'xtatish nuqtasi |
| **Step Over (F10)** | Keyingi qatorga o'tish (funksiya chaqiruvi bo'lsa, ichiga kirmaydi) |
| **Step Into (F11)** | Chaqirilayotgan funksiya ichiga kirib borish |
| **Step Out (Shift+F11)** | Joriy funksiyadan chiqib, uni chaqirgan joyga qaytish |
| **Continue (F5)** | Keyingi Breakpoint nuqtasigacha dasturni erkin davom ettirish |
| **Watch / Variables** | O'zgaruvchilar va ko'rsatkichlar (`pointers`) qiymatini real vaqtda kuzatish oynasi |

---

### 3. GDB Buyruqlar Ketma-ketligi (Cheatsheet)

| Buyruq | Qisqartmasi | Vazifasi |
| --- | --- | --- |
| `break main` | `b main` | `main` funksiyasiga to'xtash nuqtasi qo'yish |
| `break 15` | `b 15` | 15-qatorga breakpoint qo'yish |
| `run` | `r` | Dasturni ishga tushirish |
| `next` | `n` | Keyingi qatorga o'tish (Step Over) |
| `step` | `s` | Funksiya ichiga kirish (Step Into) |
| `print x` | `p x` | `x` o'zgaruvchisi qiymatini chop etish |
| `backtrace` | `bt` | Dastur qaysi funksiyada crash bo'lganini ko'rsatuvchi Call Stack |
| `quit` | `q` | GDB dan chiqish |
