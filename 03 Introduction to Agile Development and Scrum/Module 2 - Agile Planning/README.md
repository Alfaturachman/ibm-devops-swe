# Module 02: Agile Planning

Dokumen ini berisi silabus terstruktur, ringkasan konsep teoritis, dan panduan navigasi catatan pembelajaran untuk **Module 2: Agile Planning** pada kursus *Introduction to Agile Development and Scrum* (bagian dari *IBM DevOps and Software Engineering Professional Certificate* di Coursera).

---

## 1. Daftar Catatan Pembelajaran

Modul ini terdiri dari tiga catatan studi mendalam yang membahas strategi perencanaan adaptif, teknik rekayasa kebutuhan berbasis pengguna, serta proses estimasi bobot kerja secara konsensus:

1. **01 Planning to be Agile.md**:
   - Filosofi perencanaan berulang (*iterative planning*) yang menerima perubahan kebutuhan sebagai keunggulan kompetitif, bukan ancaman proyek.
   - Konsep hierarki perencanaan berlapis (*the planning onion*): Perencanaan Strategi, Portofolio, Produk, Rilis, Sprint, hingga Perencanaan Harian.
   - Penerapan teknik *Rolling Wave Planning*: merencanakan aktivitas jangka pendek dengan detail tinggi dan aktivitas jangka panjang dengan gambaran umum.
   - Disiplin pembatasan waktu (*timeboxing*) untuk menetapkan batas pengerjaan tetap, menjaga fokus tim, membatasi risiko, dan mencegah kelumpuhan akibat analisis berlebihan (*analysis paralysis*).

2. **02 User Stories.md**:
   - Hakikat cerita pengguna sebagai alat komunikasi kolaboratif melalui konsep Tiga C (*Card, Conversation, Confirmation*).
   - Struktur templat narasi Connextra: `As a... I need... So that...` yang memfokuskan implementasi pada nilai bisnis nyata.
   - Evaluasi kualitas cerita menggunakan standar industri INVEST (*Independent, Negotiable, Valuable, Estimable, Small, Testable*).
   - Penulisan kriteria penerimaan formal (*Acceptance Criteria*) berbasis sintaks Behavior-Driven Development (BDD) menggunakan format Gherkin: `Given... When... Then...`.
   - Dekomposisi hierarki kebutuhan perangkat lunak: *Themes* (inisiatif strategis tingkat tinggi), *Epics* (blok fungsionalitas besar), *User Stories* (unit kebutuhan yang dapat diselesaikan dalam satu sprint), hingga *Technical Tasks* (tugas teknis spesifik).

3. **03 Planning Process.md**:
   - Perbandingan antara estimasi ukuran relatif (*relative sizing*) berbasis kompleksitas versus estimasi berbasis durasi jam (*absolute hours*).
   - Satuan estimasi *Story Points* dan pemanfaatan deret modifikasi Fibonacci (1, 2, 3, 5, 8, 13, 20...) untuk mencerminkan ketidakpastian yang meningkat seiring besarnya tugas.
   - Teknik estimasi konsensus tim: *Planning Poker* untuk menyamakan persepsi teknis secara anonim dan memicu diskusi produktif, serta *T-Shirt Sizing* untuk pemilahan cepat (*affinity estimation*).
   - Pengelolaan simpanan produk melalui upacara penghalusan berkala (*Backlog Refinement / Grooming*).
   - Penentuan kapasitas tim (*capacity planning*) dan penghitungan kecepatan historis (*velocity*) sebagai panduan komitmen sprint yang realistis.

---

## 2. Hubungan Antar Materi dan Peta Konseptual

Alur pembelajaran pada Modul 2 mencerminkan siklus hidup perencanaan tangkas:
- **Dari Strategi Menuju Kebutuhan**: Memahami prinsip perencanaan fleksibel pada dokumen pertama (*Planning to be Agile*) membuka jalan untuk merumuskan fitur perangkat lunak ke dalam bahasa bisnis pada dokumen kedua (*User Stories*).
- **Dari Kebutuhan Menuju Eksekusi Terukur**: Cerita pengguna yang telah memenuhi kriteria INVEST dan dilengkapi spesifikasi Gherkin kemudian dinilai tingkat kerumitannya pada dokumen ketiga (*Planning Process*). Melalui teknik estimasi relatif dan *Backlog Refinement*, cerita-cerita tersebut siap dipilih ke dalam *Sprint Backlog* dengan komitmen beban kerja yang terukur dan dapat dipertanggungjawabkan.
