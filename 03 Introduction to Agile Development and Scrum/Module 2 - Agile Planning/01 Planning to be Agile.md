# Planning to Be Agile

Dokumen ini memuat rangkuman komprehensif mengenai strategi perencanaan *Agile*, mitigasi risiko ketidakpastian dalam proyek perangkat lunak (*navigating the unknown*), dekonstruksi transisi peran organisasional beserta kebutuhan pelatihan, serta pemanfaatan papan kerja *Kanban* dan perkakas *ZenHub* yang terintegrasi langsung dengan ekosistem *GitHub*.

---

## 1. Menghadapi Ketidakpastian Proyek (Navigating the Unknown)

### A. Dilema Tenggat Waktu dan Kegagalan Perencanaan Awal
Dalam manajemen proyek tradisional (*Waterfall*), organisasi kerap terjebak dalam ilusi kepastian dengan mematok jadwal dan tenggat waktu (*deadlines*) jangka panjang di awal proyek:
- **Paradoks Tenggat Waktu:**
  - Penulis Douglas Adams pernah menyatakan secara satire: *"I love deadlines. I love the whooshing sound they make as they fly by"* (Saya menyukai tenggat waktu. Saya menyukai suara melesat yang dihasilkannya saat tenggat waktu itu terlewat begitu saja).
  - Realitas industri membuktikan bahwa semakin kaku sebuah tenggat waktu tahunan ditetapkan di awal proyek, semakin tinggi probabilitas tenggat waktu tersebut terlewati.
- **Penyebab Utama Kegagalan:**
  - Organisasi mencoba memutuskan seluruh variabel teknis dan anggaran pada saat mereka berada pada titik pemahaman paling rendah (*at the point you know the least*), yaitu pada hari pertama proyek dimulai.

### B. Analogi Ladang Penguin yang Bergerak
Untuk menggambarkan ketidakpastian dalam pengembangan perangkat lunak, perhatikan analogi menyeberangi ladang yang dipenuhi kawanan penguin yang terus bergerak:
- **Dinamika Medan yang Terus Bergeser:**
  - Saat seseorang melangkahkan kaki pertama kali, ia hanya dapat melihat ruang kosong di sekitarnya. Begitu ia melangkah ke tengah, kawanan penguin telah berpindah posisi, mengubah rute yang sebelumnya tampak terbuka.
- **Korelasi dengan Ekosistem Perangkat Lunak:**
  - Lingkungan rekayasa perangkat lunak tidak pernah statis. Sistem operasi menerima pembaruan berkala (*OS patches*), pustaka dependensi (*library packages*) mengalami pembaruan versi, protokol keamanan diperketat, dan kebutuhan pasar pelanggan terus berubah.
- **Strategi Sudut Pandang Baru (*New Vantage Points*):**
  - Praktisi tidak dapat memetakan seluruh langkah kaki dari tepi awal hingga tepi akhir. Setiap kali tim mengambil satu langkah kecil ke depan, mereka memperoleh sudut pandang baru yang lebih jelas (*vantage point*), sehingga perencanaan langkah berikutnya menjadi jauh lebih realistis.

### C. Prinsip Komitmen Tertunda (Deferred Commitment)
- **Aksioma Inti Perencanaan Agile:**
  - Jangan mengunci keputusan final pada saat tim memiliki data dan pengetahuan paling minim (*don't decide everything at the point you know the least*).
- **Pendekatan Bertahap:**
  - Buat rencana kerja mendalam hanya untuk apa yang telah dipahami secara pasti saat ini. Seiring berjalannya waktu dan bertambahnya pemahaman teknis melalui eksperimen nyata, rencana kerja jangka panjang disesuaikan dan diperjelas secara bertahap.

### D. Perencanaan Iteratif dan Peningkatan Akurasi Estimasi
- **Gradasi Akurasi Estimasi Waktu:**
  - Jika tim diminta memperkirakan aktivitas mereka 3 bulan ke depan, tingkat akurasi estimasi tersebut umumnya hanya berkisar sekitar 50% akibat tingginya variabel yang belum diketahui.
  - Sebaliknya, jika tim diminta memprediksi pekerjaan untuk kurun waktu 2 pekan ke depan, tingkat akurasi dapat mencapai mendekati 100%.
- **Koreksi Arah Berkelanjutan (*Course Correction*):**
  - Perencanaan berulang (*iterative planning*) memungkinkan tim melakukan kalibrasi arah secara konstan tanpa menimbulkan kerugian finansial masif akibat pembatalan rencana tahunan.

---

## 2. Transformasi Peran Agile dan Kebutuhan Pelatihan

Menempatkan personel lama ke dalam struktur peran baru *Agile* tanpa pembekalan pelatihan yang tepat merupakan salah satu penyebab utama kegagalan transformasi organisasi:

### A. Transisi Product Manager Menjadi Product Owner
- **Perbedaan Karakteristik:**
  - *Product Manager:* Merupakan sebutan posisi struktural bisnis (*job title*). Fokus kerjanya berpusat pada pengelolaan anggaran (*budget*), analisis pasar makro, dan operasional bisnis harian.
  - *Product Owner (PO):* Merupakan peran resmi dalam kerangka kerja *Scrum* (*Scrum role*). PO bertindak sebagai visioner yang memimpin serangkaian eksperimen fungsional untuk mencapai sasaran *sprint* (*sprint goal*), mengelola prioritas *backlog*, dan menjembatani kebutuhan pemangku kepentingan dengan bahasa teknis tim pengembang.
- **Risiko Kegagalan:**
  - Menempatkan *Product Manager* konvensional langsung menjadi PO tanpa pelatihan sering kali menghasilkan PO yang hanya sibuk mengawasi biaya operasional alih-alih mengeksplorasi nilai fungsional produk.

### B. Transisi Project Manager Menjadi Scrum Master
- **Perbedaan Paradigma Manajemen:**
  - *Project Manager Tradisional:* Mengadopsi pola pikir komando dan kontrol (*command-and-control*), mengarahkan anggota tim berdasarkan bagan jadwal (*Gantt charts*), membagi-bagikan tugas secara individual, dan mencatat risiko pada lembar sebar (*spreadsheets*). Saat tim menghadapi hambatan, manajer proyek biasanya bertanya: *"Apa yang akan Anda lakukan untuk menyelesaikan hambatan tersebut?"*
  - *Scrum Master (SM):* Bertindak sebagai pelatih proses (*Agile coach*) dan fasilitator. SM tidak pernah menugaskan pekerjaan kepada anggota tim karena tim bersifat mandiri (*self-managing*). Ketika tim melaporkan adanya rintangan (*blocker*), SM secara proaktif mengambil alih hambatan tersebut: *"Biar saya yang menuntaskan rintangan ini untuk Anda; silakan Anda kembali fokus pada pekerjaan teknis yang produktif."*
- **Risiko Kegagalan:**
  - Mantan *Project Manager* yang belum terlatih cenderung memaksakan papan *Kanban* agar berfungsi seperti *Gantt Chart*, merusak otonomi tim, dan menciptakan iklim kerja kaku.

### C. Transisi Development Team Menjadi Scrum Team
- **Perbedaan Komposisi Tim:**
  - *Development Team Tradisional:* Biasanya hanya terdiri dari kelompok programmer atau rekayasawan perangkat lunak (*software engineers*) yang mengisolasi diri dari fungsi bisnis lainnya.
  - *Scrum Team:* Merupakan tim lintas fungsi (*cross-functional*) yang menyatukan seluruh keterampilan dalam satu kesatuan kerja: pengembang, spesialis pengujian mutu (*QA/testers*), analis bisnis (*business analysts*), spesialis keamanan (*security*), hingga insinyur operasional (*DevOps/operations*).
- **Risiko Kegagalan:**
  - Jika tim *Scrum* hanya berisi pembuat kode tanpa didukung spesialis pengujian dan operasional, siklus integrasi dan rilis produk akan tetap mengalami kemacetan parah di ujung siklus.

### D. Paradigma Kepemimpinan Eksekutif dan Kutipan Bill Cantor
Kutipan terkenal dari pakar industri Bill Cantor menegaskan prasyarat keberhasilan adopsi *Agile*:
> *"Until and unless business leaders accept the idea that they are no longer managing projects with fixed functions, timeframes, and costs as they did with Waterfall, they will struggle to use Agile as it was designed to be used."*
> (Sebelum para pemimpin bisnis menerima gagasan bahwa mereka tidak lagi mengelola proyek dengan fungsi, jangka waktu, dan biaya yang terkunci kaku seperti pada model Waterfall, mereka akan terus kesulitan memanfaatkan Agile sebagaimana mestinya).

- **Perubahan Pertanyaan Manajemen Puncak:**
  - Alih-alih menanyakan: *"Fitur apa saja yang akan selesai pada akhir tahun ini?"*
  - Pimpinan eksekutif harus beralih menanyakan: *"Apa yang dapat Anda selesaikan dalam dua pekan ke depan untuk menghadirkan nilai dan memuaskan pelanggan kita pada akhir sprint berikutnya?"*

---

## 3. Papan Kerja Kanban dan Perkakas Perencanaan ZenHub

### A. Hubungan Alat Bantu dan Pola Pikir Agile
- **Alat Bantu Tidak Menciptakan Kelincahan:**
  - Mengadopsi perangkat lunak manajemen proyek tercanggih tidak serta merta membuat organisasi menjadi lincah. *Mindset* dan budaya kerja adaptif harus mendahului pemilihan alat bantu (*tools support the process, but the process and mindset come first*).
- **Anti-Pola Bagan Gantt:**
  - Praktisi yang belum memahami esensi *Agile* kerap berupaya mereplikasi logika ketergantungan sekuensial *Gantt Chart* ke dalam papan *Kanban*, yang pada akhirnya membatalkan seluruh fleksibilitas *Agile*.

### B. Hirarki Perencanaan Esensial: Epics dan Stories
- **Menghindari Jebakan Mikromanajemen:**
  - Banyak perkakas manajemen proyek memecah pekerjaan ke dalam struktur yang terlalu rumit: inisiatif, tema, *epics*, *stories*, *tasks*, hingga *subtasks*.
  - Pemecahan ke tingkat tugas mikro sering kali menjebak tim ke dalam mikromanajemen yang tidak efisien.
- **Struktur Cukup Dua Tingkat:**
  - Dalam perencanaan *Agile* yang ramping, organisasi hanya membutuhkan dua tingkat hierarki kerja:
    - *Epics:* Gagasan atau inisiatif bisnis berskala besar yang membutuhkan waktu lebih dari satu *sprint* untuk diselesaikan.
    - *Stories:* Unit kebutuhan fungsional kecil yang dapat dituntaskan dan diuji dalam satu siklus *sprint*.

### C. Integrasi ZenHub dan GitHub: Sumber Kebenaran Tunggal
- **Masalah Penggunaan Terlalu Banyak Perkakas Terpisah:**
  - Jika pengembang diwajibkan membuka perkakas eksternal untuk memperbarui status pekerjaan, status tersebut dipastikan akan kedaluwarsa (*out of date*), karena pengembang segera beralih menulis kode setelah tugas selesai.
- **Keunggulan Ekosistem ZenHub:**
  - *ZenHub* beroperasi sebagai ekstensi langsung di dalam antarmuka *GitHub*.
  - Menggunakan *GitHub Issues* sebagai cerita pengguna (*stories*). Pengembang dapat mengelola kode, meninjau *Pull Requests*, dan memindahkan kartu *Kanban* di satu tempat yang sama (*one version of the truth*).

### D. Konsep Dasar Papan Kanban: Aliran Kiri ke Kanan
- **Prinsip Inti Visualisasi Kerja:**
  - Inti papan *Kanban* sangat sederhana: memvisualisasikan apa yang perlu dikerjakan (*To Do*), apa yang sedang dikerjakan (*Doing*), dan apa yang telah selesai (*Done*).
  - Papan fisik berbasis papan tulis putih (*whiteboard*) dan catatan tempel (*sticky notes*) memiliki nilai fungsional yang sama efektifnya dengan perkakas digital canggih.
- **Arah Aliran Kerja:**
  - Seluruh pekerjaan mengalir dari kiri ke kanan (*left to right*). Cerita baru masuk dari sisi paling kiri dan keluar sebagai inkremen selesai (*done increment*) di sisi paling kanan.

### E. Tujuh Saluran (Pipelines) Default pada ZenHub
1. **New Issues (Kotak Masuk / Inbox):**
   - Saluran penampungan awal bagi setiap isu atau kebutuhan baru yang diajukan. Harus ditriase (*triage*) secara berkala saat *backlog refinement*; item segera dialihkan ke saluran lain atau ditolak agar kotak masuk tetap bersih.
2. **Icebox (Penyimpanan Dingin):**
   - Tempat penyimpanan ide, fitur potensial, atau aspirasi jangka panjang yang belum akan dikerjakan dalam waktu dekat, sehingga tidak mengotori alur kerja aktif.
3. **Product Backlog:**
   - Kumpulan seluruh cerita pengguna fungsional yang belum masuk ke dalam siklus *sprint*, disusun berdasarkan urutan prioritas bisnis.
4. **Sprint Backlog:**
   - Kumpulan tugas terkomitmen yang disepakati untuk diselesaikan dalam iterasi 2 pekan berjalan. Pengembang memusatkan perhatian penuh pada saluran ini.
5. **In Progress:**
   - Cerita yang sedang aktif dikerjakan oleh anggota tim. Penugasan diri (*self-assignment*) ditandai dengan munculnya avatar profil pengembang pada kartu.
6. **Review / QA:**
   - Tahap pengujian dan peninjauan kode (*code review*). Integrasi otomatis menghubungkan *Pull Request* (PR) di *GitHub* ke saluran ini agar rekan tim dapat memvalidasi standar kualitas sebelum kode digabungkan (*merged*).
7. **Done:**
   - Kode telah berhasil digabungkan ke cabang utama (*base branch*). Menandakan penyelesaian teknis dari sisi pengembang, sebelum diverifikasi secara resmi oleh *Product Owner* pada sesi *Sprint Review*.

---

## 4. Rangkuman dan Poin Pembelajaran Kunci

1. **Perencanaan Adaptif vs Prediksi Buta:** Perencanaan jangka panjang di awal proyek menciptakan risiko kegagalan tenggat waktu; perencanaan iteratif bertahap memberikan akurasi estimasi tinggi dan ruang koreksi arah.
2. **Transformasi Peran yang Benar:** Peran PO, SM, dan Tim *Scrum* menuntut perubahan pola pikir mendalam mengenai visi, fasilitasi non-hierarkis, dan kolaborasi lintas fungsi, bukan sekadar pergantian jabatan.
3. **Komitmen Pimpinan Eksekutif:** Keberhasilan *Agile* bertumpu pada kesiapan manajemen puncak untuk berhenti menuntut kepastian fungsi, biaya, dan waktu tetap, serta beralih fokus pada penciptaan nilai dua mingguan.
4. **Kesederhanaan Struktur Perencanaan:** Membatasi hierarki perencanaan pada *Epics* dan *Stories* guna mencegah birokrasi mikromanajemen.
5. **Efisiensi Alur Kerja Terpadu:** Penggunaan *Kanban* terintegrasi seperti *ZenHub* di dalam *GitHub* menjaga keterkinian data dan transparansi status kerja dari kiri ke kanan secara alami.
