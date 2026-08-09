
### Bosqichlar Tahlili:

1. **Preprocessing (Oldindan qayta ishlash):**
   * Preprocessor `#` belgisi bilan boshlanadigan barcha komandalarni bajardi (masalan, `#include`, `#define`).
   * Barcha `#include <iostream>` kabi kutubxonalar va makroslar kodi kengaytirilib, bitta yaxlit `.i` faylga yig'iladi.

2. **Compilation (Kompilatsiya):**
   * Kompilyator `.i` fayldagi C++ kodi sintaksisini tekshiradi va uni protsessorga mos **Assembly** (assambleya) kodiga (`.s` fayl) o'giradi.
   * Sintaktik xatolar (masalan, nuqta-vergul qolib ketishi) aynan shu bosqichda aniqlanadi.

3. **Assembling (Ikkilik kodga o'tkazish):**
   * Assembler dasturi `.s` assembly kodini mashina tushunadigan ikkilik (0 va 1 lardan iborat) **Obyekt kodiga** (`.o` yoki `.obj`) o'tkazadi.

4. **Linking (Bog'lash):**
   * **Linker** (bog'lovchi) dastur siz yozgan obyekt fayllarni hamda C++ standart kutubxonalarining (masalan, `std::cout` kodi joylashgan) tayyor obyekt kodlarini bitta ishga tushuvchi (**Executable**) faylga birlashtiradi.

---

## 3. Ishchi Muhitni Sozlash (Development Environment)

C++ da kod yozish uchun bizga ikkita narsa kerak:
1. **Matn muharriri (IDE/Code Editor)** — kod yozish uchun.
2. **Kompilyator (GCC, Clang yoki MSVC)** — kodni kompilatsiya qilish uchun.

---

### A. Windows Tizimida Sozlash

#### 1-Usul: Visual Studio (Tavsiya etiladi - Professional)
* [Visual Studio Official Website](https://visualstudio.microsoft.com/) sahifasidan Community versiyasini yuklab oling.
* O'rnatgichda (Installer) **"Desktop development with C++"** bo'limini tanlang va o'rnating. U kompyuteringizga MSVC kompilyatori va barcha zaruriy muhitni avtomatik o'rnatadi.

#### 2-Usul: VS Code + MinGW-w64 (Yengil va Moslashuvchan)
1. **MinGW-w64 (GCC kompilyatori) o'rnatish:**
   * MSYS2 (https://www.msys2.org/) orqali GCC va GDB sozlamalarini o'rnating.
   * Terminalda: `pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain`
   * Windows `PATH` muhit o'zgaruvchilariga `C:\\msys64\\ucrt64\\bin` manzilini qo'shing.
2. **Terminalda tekshirish:**
   ```bash
   g++ --version
