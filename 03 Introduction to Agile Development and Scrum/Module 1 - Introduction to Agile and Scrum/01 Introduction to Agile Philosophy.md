# Introduction to Agile Philosophy

Dokumen ini memuat rangkuman komprehensif mengenai filosofi dasar *Agile*, evolusi metodologi pengembangan perangkat lunak dari model sekuensial *Waterfall* menuju model iteratif seperti *Extreme Programming* (XP) dan *Kanban*, empat pilar nilai dalam *Agile Manifesto*, serta lima praktik operasional kunci untuk merealisasikan kelincahan dalam rekayasa perangkat lunak modern.

---

## 1. Konsep Dasar dan Filosofi Agile

### A. Definisi dan Karakteristik Pendekatan Iteratif
*Agile* adalah pendekatan iteratif dalam manajemen proyek dan rekayasa perangkat lunak yang dirancang untuk memungkinkan tim merespons perubahan secara cepat serta menghantarkan nilai (*value*) nyata kepada pelanggan secara berkelanjutan:
- **Pendekatan Iteratif vs Perencanaan Tahunan:**
  - Pada metodologi perencanaan tradisional, organisasi menyusun rencana kerja tahunan secara kaku di awal proyek sebelum pekerjaan dimulai.
  - Pada filosofi *Agile*, proyek dipecah menjadi inkremen-inkremen kecil (*small increments*). Setiap inkremen diselesaikan dalam siklus pendek, diserahkan kepada pelanggan untuk memperoleh umpan balik (*feedback*), lalu arah pengembangan disesuaikan secara berkesinambungan.
- **Prinsip Utama:**
  - Membangun apa yang benar-benar dibutuhkan oleh pelanggan (*build what is needed*), bukan sekadar memaksakan apa yang telah direncanakan di masa lalu (*not what was planned*). Jika produk dibangun sesuai rencana awal namun tidak diminati pelanggan, maka upaya tersebut sia-sia.

### B. Lima Karakteristik Penentu Agile
1. **Perencanaan Adaptif (*Adaptive Planning*):**
   - Rencana kerja tidak bersifat statis, melainkan adaptif terhadap temuan baru, perubahan strategi bisnis, dan dinamika kebutuhan pengguna akhir.
2. **Pengembangan Evolusioner (*Evolutionary Development*):**
   - Perangkat lunak tidak dibangun sekaligus dalam satu skala masif (*big bang*), melainkan bertumbuh dan berevolusi secara bertahap melalui serangkaian inkremen fungsional.
3. **Penyerahan Dini (*Early Delivery*):**
   - Merupakan komponen paling esensial dalam *Agile*. Mengembangkan fitur secara berulang tanpa menyerahkannya ke tangan pelanggan bukanlah *Agile*. Penyerahan produk nyata sejak dini memungkinkan validasi arah bisnis secara konkret.
4. **Perbaikan Berkelanjutan (*Continuous Improvement*):**
   - Tim secara rutin mengevaluasi kualitas produk dan efektivitas proses kerja internal mereka untuk menemukan area optimalisasi pada setiap siklus.
5. **Responsif terhadap Perubahan (*Responsive to Change*):**
   - Karena rencana tidak dikunci terlalu jauh ke masa depan, tim memiliki fleksibilitas tinggi untuk menyusun ulang prioritas kerja (*re-planning*) secara cepat saat terjadi perubahan persyaratan.

### C. Empat Nilai Inti Agile Manifesto
Diformulasikan pada tahun 2001 di Snowbird, Utah oleh 17 praktisi perangkat lunak terkemuka, *Agile Manifesto* menetapkan empat nilai fundamental:
1. **Individu dan Interaksi lebih bernilai daripada Proses dan Alat Bantu (*Individuals and interactions over processes and tools*):**
   - Kolaborasi langsung antar manusia dan komunikasi yang cair diutamakan daripada keterikatan kaku pada aturan administratif atau alat bantu perangkat lunak.
2. **Perangkat Lunak yang Berfungsi lebih bernilai daripada Dokumentasi yang Komprehensif (*Working software over comprehensive documentation*):**
   - Tolok ukur utama kemajuan proyek adalah perangkat lunak yang berjalan dengan baik. Dokumentasi teknis tetap penting untuk memandu penggunaan produk, namun dokumentasi tidak dapat dioperasikan oleh pengguna di lingkungan produksi.
3. **Kolaborasi dengan Pelanggan lebih bernilai daripada Negosiasi Kontrak (*Customer collaboration over contract negotiation*):**
   - Hubungan dengan klien diposisikan sebagai kemitraan kerja sama yang fleksibel untuk mencapai keberhasilan produk, bukan sebatas perdebatan klausul hukum kontrak.
4. **Merespons Perubahan lebih bernilai daripada Mengikuti Rencana (*Responding to change over following a plan*):**
   - Kemampuan beradaptasi terhadap realitas baru dipandang sebagai keunggulan kompetitif, bukan sebagai kegagalan manajemen.

Pernyataan di atas menegaskan bahwa meskipun terdapat nilai pada aspek di sisi kanan (proses, dokumentasi, kontrak, dan rencana), praktisi *Agile* menghargai aspek di sisi kiri secara lebih tinggi (*we value the items on the left more*).

### D. Struktur Tim Pengembang Agile
Untuk menjalankan prinsip-prinsip tersebut secara efektif, tim *Agile* dibangun dengan karakteristik operasional spesifik:
- **Ukuran Kecil (*Small*):** Terdiri dari kelompok kompak untuk meminimalkan jalur birokrasi komunikasi.
- **Berlokasi Sama (*Co-located*):** Berada dalam satu ruangan fisik atau terhubung secara intensif guna memaksimalkan komunikasi langsung tatap muka.
- **Lintas Fungsi (*Cross-functional*):** Memiliki seluruh keterampilan yang dibutuhkan untuk menyelesaikan produk (pengembang, penguji, analis bisnis, hingga spesialis operasional) tanpa bergantung pada divisi lain.
- **Mengatur dan Mengelola Diri Sendiri (*Self-organizing and Self-managing*):** Tim memiliki wewenang penuh untuk menentukan cara terbaik dalam mencapai target tanpa intervensi mikro (*micromanagement*).

---

## 2. Tinjauan dan Evolusi Metodologi Pengembangan Perangkat Lunak

### A. Pendekatan Tradisional Waterfall
Model *Waterfall* mengadopsi tahapan sekuensial yang diturunkan dari disiplin rekayasa sipil dan manufaktur perangkat keras:
- **Tahapan Sekuensial Linier:**
  - *Requirements Phase:* Pengumpulan dan dokumentasi seluruh spesifikasi kebutuhan sistem secara lengkap di awal.
  - *Design Phase:* Perancangan arsitektur dan sistem secara menyeluruh oleh tim arsitek.
  - *Coding Phase:* Penulisan kode program oleh tim pengembang berdasarkan dokumen desain.
  - *Integration Phase:* Penggabungan modul-modul kode yang sebelumnya dikerjakan secara terisolasi.
  - *Testing Phase:* Pengujian fungsional dan pelaporan cacat program (*bugs*).
  - *Deployment Phase:* Penyerahan sistem kepada tim operasional untuk dirilis ke lingkungan produksi.
- **Karakteristik dan Aturan Fase:**
  - Setiap fase memiliki kriteria masuk (*entrance criteria*) dan kriteria keluar (*exit criteria*) yang ketat. Suatu fase hanya dapat dimulai setelah fase sebelumnya dinyatakan selesai secara formal.
- **Kelemahan dan Risiko Mendasar Model Waterfall:**
  - *Analogi Arus Air Terjun:* Sangat sulit dan mahal untuk "berenang melawan arus air terjun". Jika kecacatan arsitektur baru ditemukan pada fase pengujian atau integrasi, tim harus kembali ke fase desain yang membutuhkan biaya sangat besar.
  - *Ketiadaan Ruang Perubahan:* Tidak ada mekanisme untuk memperbarui kebutuhan di tengah jalan karena seluruh fase telah terkunci.
  - *Ketiadaan Validasi Menengah:* Produk baru dapat dilihat dan diuji oleh pengguna pada ujung akhir siklus (*last step*), sehingga risiko kegagalan sistem terakumulasi hingga akhir.
  - *Terjadinya Silo dan Kehilangan Konteks:* Setiap kelompok bekerja dalam kotak isolasi masing-masing tanpa menyadari dampak pekerjaan mereka terhadap tahap berikutnya. Tim operasional yang berada paling jauh dari kode program dipaksa memelihara sistem yang tidak mereka pahami.
  - *Waktu Tunggu Sangat Panjang (Long Lead Times):* Membutuhkan waktu berbulan-bulan bahkan bertahun-tahun antara inisiasi proyek hingga sistem beroperasi nyata.

### B. Extreme Programming (XP)
Diperkenalkan oleh Kent Beck pada tahun 1996, *Extreme Programming* (XP) merupakan salah satu metodologi pelopor gerakan *Agile* yang memusatkan perhatian pada peningkatan kualitas kode teknis dan kecepatan adaptasi:
- **Konsep Lingkaran Umpan Balik Konsentris (*Concentric Feedback Loops*):**
  - *Outer Loop (Release Plan):* Siklus perencanaan rilis skala besar dalam hitungan bulan.
  - *Iteration Plan:* Siklus iterasi pengerjaan fitur dalam hitungan pekan.
  - *Acceptance Testing:* Validasi kriteria fungsional dalam hitungan hari.
  - *Stand-up Meetings:* Rapat penyelarasan tim harian dalam hitungan menit.
  - *Pair Negotiation:* Sinkronisasi desain antar pengembang dalam hitungan jam.
  - *Unit Testing:* Pengujian otomatis modul kode dalam hitungan menit.
  - *Pair Programming:* Peninjauan dan perancangan kode seketika dalam hitungan detik.
- **Lima Nilai Inti Extreme Programming:**
  - **Kesederhanaan (*Simplicity*):** Buat apa yang dibutuhkan saat ini dan hindari rekayasa berlebihan (*no over-engineering* atau *over-coding*).
  - **Komunikasi (*Communication*):** Mendorong interaksi verbal intensif dan terbuka di antara seluruh anggota tim.
  - **Umpan Balik (*Feedback*):** Mengoptimalkan siklus umpan balik secepat mungkin melalui pengujian otomatis dan demonstrasi berkala.
  - **Rasa Hormat (*Respect*):** Setiap anggota tim dihargai sebagai rekan setara tanpa hierarki kaku; setiap masukan teknis diperlakukan adil.
  - **Keberanian (*Courage*):** Kejujuran penuh dalam estimasi waktu dan kemampuan teknis tanpa memanipulasi data atau menjanjikan komitmen yang tidak realistis.

### C. Sistem Kanban
Berasal dari sistem manufaktur ramping (*lean manufacturing*) Toyota di Jepang, *Kanban* secara harfiah bermakna "papan tanda" (*billboard sign*):
- **Lima Prinsip Inti Kanban:**
  1. **Visualisasikan Alur Kerja (*Visualize the Workflow*):**
     - Seluruh aktivitas proyek harus ditampilkan pada papan kerja visual (*Kanban board*). Pekerjaan yang tidak terlihat tidak dapat dikelola dengan optimal.
  2. **Batasi Pekerjaan dalam Proses (*Limit Work in Progress / WIP*):**
     - Mencegah penumpukan tugas pada satu stasiun kerja. Menyelesaikan 100% dari satu fitur jauh lebih bernilai daripada menyelesaikan 50% dari dua fitur sekaligus.
  3. **Kelola dan Tingkatkan Aliran (*Manage and Enhance the Flow*):**
     - Memantau kelancaran perpindahan tugas dari satu kolom ke kolom berikutnya serta mengeliminasi hambatan (*bottlenecks*).
  4. **Buat Kebijakan Proses Eksplisit (*Make Policies Explicit*):**
     - Seluruh kriteria kerja dan standar kualitas (seperti kriteria *Definition of Done*) harus disepakati secara terbuka dan dipahami bersama.
  5. **Lakukan Perbaikan Berkelanjutan (*Continuously Improve*):**
     - Menggunakan metrik empiris untuk mengidentifikasi inefisiensi dan melakukan eksperimen perbaikan secara berkesinambungan (*Kaizen*).

---

## 3. Praktik Utama dalam Bekerja Secara Agile

### A. Bekerja dalam Batch Kecil (*Small Batches*) dan Aliran Satuan (*Single-Piece Flow*)
Filosofi *Lean Manufacturing* membuktikan bahwa bekerja dalam ukuran *batch* besar menciptakan pemborosan (*waste*) dan memperlambat deteksi cacat:
- **Studi Kasus Pengiriman 1.000 Brosur:**
  - Aktivitas terdiri dari 4 langkah: melipat brosur, memasukkan ke amplop, merekatkan amplop, dan menempelkan prangko.
  - Asumsi durasi setiap langkah: 6 detik per item (kapasitas 10 item per menit).
- **Skenario 1: Ukuran Batch Besar (50 item per batch):**
  - Langkah 1 (Melipat 50 brosur): membutuhkan waktu 5 menit.
  - Langkah 2 (Memasukkan 50 brosur): membutuhkan tambahan 5 menit (total waktu berlalu: 10 menit).
  - Langkah 3 (Merekatkan 50 amplop): membutuhkan tambahan 5 menit (total waktu berlalu: 15 menit).
  - Langkah 4 (Menempelkan prangko pada item pertama): produk jadi pertama baru selesai pada menit ke-16.
  - *Dampak Cacat:* Jika lem amplop rusak atau terjadi salah ketik (*typo*) pada brosur, kesalahan baru terdeteksi setelah 11 hingga 16 menit, mengakibatkan 50 item rusak dan harus dikerjakan ulang dari awal.
- **Skenario 2: Aliran Satuan / Single-Piece Flow (Ukuran Batch = 1):**
  - Langkah 1 s.d. Langkah 4 dikerjakan secara berurutan untuk 1 brosur hingga tuntas.
  - Produk jadi pertama selesai dalam waktu 24 detik:
    $$\text{Durasi Produk Pertama} = 4 \times 6\text{ detik} = 24\text{ detik}$$
  - *Dampak Cacat:* Ketiadaan lem pada amplop terdeteksi pada detik ke-18, dan kesalahan cetak brosur terdeteksi pada detik ke-24. Pemborosan ditekan hingga mendekati nol.
- **Kesimpulan Praktik:**
  - Bekerja dalam *batch* kecil menghasilkan umpan balik instan, mempercepat waktu siklus (*cycle time*), dan memungkinkan tim melakukan manuver arah (*pivot*) secara murah.

### B. Konsep dan Implementasi Minimum Viable Product (MVP)
- **Miskonsepsi Umum:**
  - MVP sering disalahartikan sebagai "Fase 1 dari proyek", produk setengah jadi, atau sekadar versi uji coba (*beta release*).
- **Definisi Sejati MVP:**
  - MVP adalah eksperimen terkecil dan teringan yang dapat dibangun untuk membuktikan hipotesis bisnis, memperoleh pembelajaran nyata (*gain learning*), dan memutuskan arah strategis: beralih haluan (*pivot*) atau melanjutkan rencana (*persevere*).
- **Studi Kasus Analogi Kendaraan:**
  - *Tim 1 (Miskonsepsi Pengembangan Bertahap):*
    - Kebutuhan pelanggan: Kendaraan transportasi.
    - Iterasi 1: Menyerahkan sebuah roda (pelanggan tidak dapat menggunakannya).
    - Iterasi 2: Menyerahkan sasis rangka (pelanggan tetap tidak dapat memanfaatkannya).
    - Iterasi 3: Menyerahkan badan mobil tanpa setir.
    - Iterasi 4: Menyerahkan mobil *coupe*.
    - *Evaluasi:* Tim 1 sekadar memecah pembangunan mobil tanpa pernah memberikan nilai yang bisa diuji atau dirasakan pelanggan di setiap siklus.
  - *Tim 2 (Penerapan MVP Sejati):*
    - Iterasi 1: Menyerahkan papan seluncur (*skateboard*) untuk menguji preferensi warna dan konsep transportasi dasar. Pelanggan menyukai warnanya namun kesulitan mengendalikan arah.
    - Iterasi 2: Menambahkan stang kemudi (menjadi skuter). Pelanggan dapat berbelok, namun membutuhkan kecepatan lebih tinggi.
    - Iterasi 3: Menambahkan pedal dan rantai (menjadi sepeda).
    - Iterasi 4: Menambahkan mesin (menjadi sepeda motor). Saat mengendarai motor dan merasakan hembusan angin, pelanggan menyadari kebutuhan sejatinya: *"Saya menginginkan mobil konvertibel (atap terbuka)"*.
    - *Evaluasi:* Pelanggan mendapatkan produk yang benar-benar memuaskan keinginannya karena tim berinteraksi secara aktif dan mengevolusikan produk berdasarkan umpan balik nyata.

### C. Behavior-Driven Development (BDD)
- **Prinsip Dasar:**
  - Menguji dan mendeskripsikan perilaku sistem dari luar ke dalam (*outside-in approach*).
  - Berfokus pada perspektif pengguna akhir dan pemangku kepentingan bisnis, umumnya diuji pada level integrasi dan antarmuka pengguna (*User Interface / UI*).
- **Sintaksis Gherkin:**
  - Menggunakan bahasa terstruktur yang dipahami bersama oleh pengembang, penguji, dan pemilik bisnis (*ubiquitous language*):
    - `Given`: Kumpulan prakondisi awal sistem (*preconditions*).
    - `When`: Tindakan atau peristiwa spesifik yang sedang diuji (*action/event*).
    - `Then`: Hasil atau dampak yang dapat diamati secara objektif (*observable outcome*).
  - *Contoh Skenario:*
    ```gherkin
    Given keranjang belanja memiliki 2 item produk
    When pengguna menekan tombol "Kosongkan Keranjang"
    Then keranjang belanja harus menampilkan status kosong (0 item)
    ```

### D. Test-Driven Development (TDD)
- **Prinsip Dasar:**
  - Menguji sistem dari dalam ke luar (*inside-out approach*) pada level unit modul kode (*unit testing*).
  - Pengembang menulis kasus uji (*test case*) terlebih dahulu sebelum menulis baris kode implementasi.
- **Siklus Red, Green, Refactor:**
  - **Red (Merah):** Tulis kasus uji untuk fungsionalitas yang diinginkan. Jalankan pengujian dan pastikan pengujian gagal (berwarna merah) karena kode belum dibuat.
  - **Green (Hijau):** Tulis baris kode program seminimal mungkin hanya untuk membuat kasus uji tersebut berhasil lolos (berwarna hijau).
  - **Refactor (Penyempurnaan):** Tata ulang dan rapikan struktur kode, hilangkan duplikasi, dan tingkatkan performa tanpa mengubah fungsionalitas eksternal. Kasus uji otomatis menjamin tidak ada regresi fungsional yang terjadi.

### E. Pemrograman Berpasangan (*Pair Programming*)
- **Mekanisme Operasional:**
  - Dua pengembang bekerja bersama pada satu komputer.
  - *Driver:* Orang yang mengetik kode dan berfokus pada implementasi taktis mekanis.
  - *Navigator:* Orang yang meninjau kode secara seketika (*second pair of eyes*), memikirkan arsitektur strategis, penamaan variabel, skenario batas (*edge cases*), dan mencari referensi teknis.
  - Peran ditukar secara berkala, umumnya setiap interval 20 menit.
- **Justifikasi Biaya dan Efisiensi:**
  - Menulis kode adalah tahapan termurah dalam siklus hidup perangkat lunak; menemukan dan memperbaiki kutu di lingkungan produksi adalah tahapan yang paling mahal.
  - Kualitas kode meningkat drastis karena setiap baris telah melalui penelaahan sejawat secara langsung (*instant code review*).
  - Mempercepat transfer pengetahuan teknis (*knowledge transfer*) antara pengembang senior dan junior serta memangkas waktu orientasi anggota tim baru.

---

## 4. Rangkuman dan Poin Pembelajaran Kunci

1. **Hakikat Utama Agile:** Pendekatan pengembangan kolaboratif, adaptif, dan berulang yang mengedepankan fleksibilitas, interaktivitas tim, dan transparansi di atas kepatuhan rencana buta.
2. **Kelemahan Model Waterfall:** Sifat sekuensial yang kaku, ketiadaan produk fungsional menengah, tingginya biaya perbaikan galat di akhir, dan terbentuknya isolasi antar departemen.
3. **Pilar Extreme Programming (XP):** Lingkaran umpan balik konsentris yang ketat dengan nilai kesederhanaan, komunikasi, umpan balik, rasa hormat, dan keberanian moral.
4. **Keunggulan Sistem Kanban:** Pengelolaan alur kerja visual, pembatasan ketat beban kerja dalam proses (WIP), dan perbaikan inkremental berkelanjutan.
5. **Esensi Bekerja Secara Agile:** Bekerja dalam *batch* kecil untuk deteksi dini galat, merilis MVP untuk pembelajaran hipotesis pasar, memastikan pembangunan sistem yang benar melalui BDD (*outside-in*), memastikan pembangunan sistem secara benar melalui TDD (*inside-out*), serta menaikkan kualitas kode melalui *Pair Programming*.
