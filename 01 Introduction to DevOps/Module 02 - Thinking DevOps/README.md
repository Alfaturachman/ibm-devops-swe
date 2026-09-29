# Module 02: Thinking DevOps

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 02: Thinking DevOps pada kursus Introduction to DevOps, mencakup pergeseran pola pikir melalui prinsip social coding, alur pencabangan Git, alur satu bagian dalam kelompok kecil (*single-piece flow*), pemanfaatan MVP berorientasi pembelajaran, metodologi TDD dan BDD, arsitektur layanan mikro berbasis cloud-native, serta perancangan sistem tangguh menghadapi kegagalan (*designing for failure*).

---

### Ringkasan Konsep Inti

- **Social Coding dan Budaya Inner Source:**
  - Menerapkan prinsip keterbukaan sumber terbuka (*open source*) ke dalam repositori internal perusahaan (*inner source*).
  - Mengeliminasi inefisiensi duplikasi pekerjaan (*reinventing the wheel*) melalui mekanisme kolaboratif: membuka tiket tugas (*issue*), melakukan *fork*, membuat *branch*, dan mengajukan *pull request* (PR).
  - Pemilik repositori (*repository owner*) memegang kendali penuh atas persetujuan kode dan standar kualitas pengujian.
- **Praktik Pair Programming:**
  - Dua pemrogram berbagi satu stasiun kerja: peran *Driver* (menulis kode) dan *Navigator* (meninjau arah, arsitektur, dan referensi) yang bertukar peran setiap 20 menit.
  - Membawa manfaat terukur: mendeteksi galat lebih awal melalui *programming out loud*, mempercepat transfer pengetahuan lintas level senioritas, serta menghilangkan titik kegagalan tunggal pemahaman kode.
- **Git Feature Branch Workflow:**
  - Menerapkan struktur satu repositori per komponen atau layanan mikro; menghindari *mono-repo* untuk kode produksi.
  - Menggunakan cabang fitur berumur pendek (*short-lived feature branches*) yang dihapus segera setelah digabungkan ke cabang utama.
  - Aturan mutlak integrasi: dilarang menggabungkan *pull request* buatan sendiri (*never merge your own pull request*) demi menjamin peninjauan rekan kerja (*code review*).
- **Alur Satu Bagian (Single-Piece Flow) vs Batch Besar:**
  - Konsep manufaktur *Lean*: bekerja dalam kelompok kecil (*small batches*) menghasilkan umpan balik seketika dan menekan pemborosan waktu.
  - Pada analogi pelipatan brosur: pendekatan kelompok besar (batch 50 unit) baru menghasilkan produk jadi pertama setelah lebih dari 15 menit, sedangkan alur satu bagian (*single-piece flow*) memvalidasi kualitas produk pertama hanya dalam 24 detik.
  - Ukuran tugas di *backlog* idealnya dapat diselesaikan dalam rentang waktu satu pekan atau kurang.

---

### Metodologi dan Pendekatan Rekayasa

- **Minimum Viable Product (MVP) Berorientasi Pembelajaran:**
  - MVP adalah eksperimen berbiaya terendah untuk menguji hipotesis nilai (*value hypothesis*) bersama pengguna nyata.
  - Berfokus pada pembelajaran (*learning*), bukan sekadar jadwal pengiriman (*delivery*), guna mengarahkan keputusan objektif untuk beralih strategi (*pivot*) atau melanjutkan rencana (*persevere*).
  - Menghindari jebakan rilis bertahap tanpa nilai fungsional (analogi pengiriman mobil merah: dari papan luncur, skuter, sepeda motor, hingga mobil atap terbuka).
- **Test-Driven Development (TDD) dari Dalam ke Luar (*Inside-Out*):**
  - Kasus uji mengarahkan desain arsitektur kode (*test case drives the design and development*).
  - Mengadopsi siklus *Red, Green, Refactor*: tulis tes yang gagal (*Red*), buat kode minimal agar tes lolos (*Green*), lalu bersihkan struktur kode (*Refactor*).
  - Memberikan perspektif pemanggil (*caller's perspective*) dan menjadi prasyarat mutlak dalam membangun pipa rilis otomatis CI/CD.
- **Behavior-Driven Development (BDD) dari Luar ke Dalam (*Outside-In*):**
  - Memvalidasi perilaku sistem tingkat tinggi sebagaimana diamati oleh pengguna bisnis dan sistem eksternal (*ensuring building the right thing*).
  - Menggunakan notasi bahasa alami Gherkin (*Given... When... Then... And...*) yang dapat dieksekusi langsung oleh perkakas otomatis (seperti Behave atau Cucumber) sebagai kriteria penerimaan resmi (*acceptance criteria*).

---

### Arsitektur dan Pola Ketahanan Sistem

- **Cloud-Native Microservices:**
  - Mengikuti prinsip *The Twelve-Factor App* di mana aplikasi dipecah menjadi kumpulan layanan independen yang berkomunikasi melalui antarmuka REST API.
  - Setiap layanan mikro bersifat nir-status (*stateless*) dan mengelola statusnya pada basis data terpisah (*database per service*). Berbagi basis data langsung antarlayanan adalah anti-pola monolit terdistribusi (*distributed monolith*).
  - Menerapkan filosofi *cattle, not pets*: instans server dan kontainer yang bermasalah langsung dimatikan dan digantikan oleh instans baru yang bersih.
- **Pola Perancangan Sistem Tangguh (Designing for Failure):**
  - Paradigma rekayasa bergeser dari upaya mencegah kegagalan menuju percepatan pemulihan kegagalan (*Mean Time to Recovery* / MTTR).
  - **Retry Pattern dengan Exponential Backoff:** Mengatasi kegagalan sementara dengan meningkatkan jeda waktu percobaan ulang secara bertingkat untuk memberi waktu sistem target pulih.
  - **Circuit Breaker Pattern:** Meniru sekring listrik (*Closed, Open, Half-Open*) untuk memutus aliran panggilan ke layanan yang rusak dan mencegah kegagalan berantai (*cascading failures*).
  - **Bulkhead Pattern:** Meniru sekat kedap air kapal laut untuk mengisolasi sumber daya kritis (seperti kolam koneksi atau alokasi memori) agar gangguan pada satu fitur tidak melumpuhkan seluruh aplikasi.
  - **Chaos Engineering:** Pengujian proaktif dengan sengaja menyuntikkan kegagalan ke lingkungan produksi (seperti *Chaos Monkey* oleh Netflix) untuk membuktikan ketahanan otomatis sistem.
