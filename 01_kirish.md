# 1.1-Dars: C++ Dasturlash Tili: Kirish, Qo'llanilish Sohasi va Ishlatilish Holatlari
---
## 1. C++ Dasturlash Tili Nima?

**C++** — 1979-yilda daniyalik olim **Bjarne Stroustrup** tomonidan **Bell Labs** laboratoriyasida yaratilgan, kompilatsiya qilinadigan (compiled) va statik tiplangan (statically typed) umumiy maqsadli dasturlash tilidir. 

Dastlab u **"C with Classes"** (Klasslarga ega C tili) deb atalgan, chunki muallif mashhur **C tili**ning apparat va xotira bilan pastki darajada (low-level) ishlash tezligini **Obyektga Yo'naltirilgan Dasturlash (OOP)** konsepsiyasi bilan birlashtirishni maqsad qilgan. 1983-yilda bu til rasman **C++** nomini oldi (`++` belgisi C tilida qiymatni 1 ga oshirish inkrement operatoridir).

### C++ ning Asosiy Texnik Xususiyatlari:

1. **Kompilatsiya Qilinadigan Til (Compiled Language):**
   C++ kodi interpretsiya qilinmaydi (Python yoki JavaScript kabi). U kompilator vositasida to'g'ridan-to'g'ri protsessor va operatsion tizim tushunadigan ikkilik (binary) mashina kodiga o'giriladi.
2. **Statik Tiplash (Statically Typed):**
   Har bir o'zgaruvchining ma'lumot turi (`int`, `double`, `char` va h.k.) kompilatsiya vaqtida aniq ko'rsatiladi va tekshiriladi. Bu koddagi ko'plab mantiqiy va xotira xatolarini hali dastur ishga tushmasidanoq ushlash imkonini beradi.
3. **Nol-Xarajatli Abstraksiya (Zero-overhead Abstraction):**
   C++ ning oltin qoidasi: *"Siz ishlatmagan narsangiz uchun haq tolaysiz (resurs sarflamaysiz). Ishlatgan narsangizni esa qo'lda assemblyda yozganingizdan ko'ra yaxshiroq optimizatsiya qila olmaysiz"*.
4. **Xotirani To'g'ridan-to'g'ri Boshqarish:**
   C++ da dasturchi kompyuterning operativ xotirasini (RAM) ko'rsatkichlar (pointers) va adreslar orqali to'g'ridan-to'g'ri boshqaradi. Unda avtomatik axlat yig'uvchi (Garbage Collector) yo'q, bu esa resurslardan maksimal unumdorlikda foydalanishni ta'minlaydi.
5. **Ko'p Konseptlilik (Multi-paradigm):**
   C++ procedural (prosedurali), OOP (Obyektga yo'naltirilgan), Generic (shablonlar bilan ishlash) va Functional (funksional) dasturlash uslublarining barchasini qo'llab-quvvatlaydi.

---

## 2. C++ Qayerlarda Ishlatiladi?

C++ har qanday oddiy loyiha uchun ishlatilavermaydi. U asosan **"Resurs va Tezlik Cheklangan"** hamda **"Apparat apparaturasiga to'g'ridan-to'g'ri kirish kerak bo'lgan"** murakkab sohalarda qo'llaniladi.

### A. Game Development (O'yin Sanoati)
O'yin sanoatidagi eng yetakchi o'yin dvigatellari (Game Engines) va yuqori darajadagi grafikali murakkab o'yinlar C++ da yoziladi:
* **Unreal Engine** — Dunyodagi eng mashhur o'yin dvigateli to'liq C++ da yozilgan va o'yin mantiqini yozish uchun C++ ishlatiladi.
  
### B. Operatsion Tizimlar va Drayverlar (OS & Hardware Drivers)
Biz har kuni ishlatadigan operatsion tizimlarning yadro (kernel) va asosiy modullari C hamda C++ da qurilgan:
* **Windows OS:** Interfeys va yadro tizimlarining salmoqli qismi.
* **macOS va iOS:** Quyi darajadagi drayverlar hamda grafik freymvorklar.
* **Linux Kernel modullari:** Apparat vositalari (grafik karta, tarmoq adapterlari) drayverlari.

### C. Moliya va Yuqori Chastotali Savdo (High-Frequency Trading - HFT)
Moliya birjalarida millisekund emas, **nanosekundlar** rol o'ynaydi. 
* Birja algoritmlari va avtomatlashtirilgan kotirovka tizimlarida (HFT) buyurtmalarni zudlik bilan qayta ishlash uchun C++ muqobilsiz til hisoblanadi.

### D. Brauzerlar va Ularning Dvigatellari
Zamonaviy brauzerlar ulkan va murakkab operatsion tizim kabi ishlaydi:
* **Google Chrome (V8 Engine):** JavaScript kodini chaqmoqday tezlikda interpretatsiya qiluvchi va dvigateli, Chrome kodi C++ da yozilgan.
* **Mozilla Firefox (Gecko Engine):** Sahifalarni render qilish va JS ishlash dvigateli.

### E. Sun'iy Intellekt va Ma'lumotlar Tahlili (AI & ML Frameworks)
Python tili AI va ML sohasida juda mashhur bo'lsada, u faqat **interfeys (qobiq)** vazifasini o'taydi.
* **PyTorch**, **TensorFlow**, **OpenCV** kabi gigant kutubxona va freymvorklarning eng og'ir matematik va matritsali hisob-kitoblarni bajaradigan ichki **back-end qismi** to'liqligicha C++ da yozilgan.

### F. Ma'lumotlar Bazasi Dvigatellari (Database Engines)
Ma'lumotlar ombori terabaytlab ma'lumotlarni sekundiga millionlab so'rovlar orqali qayta ishlashi kerak:
* **MySQL**, **PostgreSQL** (yadro qismlari), **MongoDB** hamda **Redis** kabi yuqori yuklanishga bardosh beruvchi bazalar C++ da qurilgan.

### G. O'rnatilgan Tizimlar (Embedded Systems & IoT)
Resurslari nihoyatda cheklangan qurilmalar:
* Avtomobil boshqaruv bloklari (ECU), tibbiyot apparatlari, robototexnika, dronlar, maishiy texnikalar mikrokontrollerlari va aerokosmik (NASA, SpaceX) tizimlari.

---

## 3. Qanday Holatlarda C++ Tanlanadi? 

To'g'ri texnologiyani tanlash dasturchining eng muhim ko'nikmasidir.

###  Qanday Holatlarda C++ Tanlash Kerak?

1. **Vaqt va Kechikish (Latency) Kritik Bo'lganda:**
   Dasturingiz real vaqt rejimida (Real-time System) javob berishi shart bo'lsa (masalan, avtopilot tormozlanish tizimi, tibbiy apparat).
2. **Apparat Resurslari (RAM/CPU) Cheklangan Bo'lganda:**
   Mikrokontrollerda atigi 512 KB operativ xotira bo'lsa va unda ortiqcha runtime yoki Garbage Collectorlarni ishlatish imkoni bo'lmaganda.
3. **Hardware (Apparat) Bilan To'g'ridan-to'g'ri Ishlash Kerak Bo'lganda:**
   Videokarta xotirasi yoki tarmoq kartasi buferiga bevosita kirish talab qilinganda.
4. **Maksimal Hisoblash Quvvati Talab Qilinganda:**
   3D grafikani render qilish, video-kodlash (video compression), murakkab fizik va matematik simulyatsiyalar.

---

### ❌ Qanday Holatlarda C++ Tanlanmasligi Kerak?

1. **Oddiy Veb-saytlar va CRUD API-lar:**
   E-commerce sayt, blog yoki telegram bot yaratish uchun C++ ishlatish vaqtni behuda sarflashdir. Bular uchun *Python (Django/FastAPI), JavaScript (Node.js), Go* yoki *PHP* o'n barobar tezroq va qulayroq yechim beradi.
2. **Tezkor Startup MVP Yaratishda:**
   Agarda mahsulotni 1-2 haftada bozorga chiqarish va sinab ko'rish kerak bo'lsa, C++ dagi past darajadagi xotira boshqaruvi va uzoq kompilatsiya vaqti ishni sevlashtirib yuboradi.
3. **Oddiy Skriptlar va Avtomatlashtirishda:**
   Fayllarni saralash, matnlarni parsing qilish kabi yumushlar uchun *Python* yoki *Bash/Shell* skriptlari ancha mos keladi.

---
