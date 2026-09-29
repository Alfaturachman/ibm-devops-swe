# Thinking DevOps

Dokumen ini menyajikan rangkuman komprehensif mengenai transformasi pola pikir dalam DevOps, mencakup prinsip *social coding*, alur kerja cabang Git, pengiriman dalam *small batches*, pemanfaatan *minimum viable product* (MVP), metodologi TDD dan BDD, arsitektur *cloud-native microservices*, serta strategi perancangan sistem yang tangguh terhadap kegagalan (*designing for failure*).

---

### 1. Social Coding Principles and Collaborative Culture

#### A. Konsep Inner Source dalam Lingkungan Enterprise
- **Penerapan Nilai Open Source secara Internal:**
  - *Social coding* adalah adopsi filosofi dan praktik komunitas sumber terbuka (*open source*) ke dalam lingkungan pengembangan internal korporasi (*inner source*).
  - Pada model tradisional, tim pengembang bekerja di dalam repositori privat yang tertutup rapat, di mana hak akses diatur ketat berdasarkan asas kebutuhan mendesak (*strict need-to-know basis*).
  - Keterisolasian ini menimbulkan masalah duplikasi: tim lain tidak mengetahui keberadaan modul yang telah dibangun, sehingga perusahaan berulang kali menciptakan ulang hal yang sama (*reinventing the wheel*).
- **Keterbukaan Repositori:**
  - Dalam budaya *social coding*, seluruh repositori kode internal bersifat terbuka untuk dibaca oleh seluruh pengembang di perusahaan.
  - Setiap pengembang didorong untuk menyalin repositori (*fork*), memodifikasi kode, dan berkontribusi kembali tanpa memicu anarki karena kendali persetujuan integrasi tetap berada penuh di tangan pemilik repositori (*repository owner*).

#### B. Mekanisme Kolaborasi dan Efisiensi Sumber Daya
- **Menghindari Perangkap Duplikasi:**
  - Ketika sebuah tim membutuhkan modul yang 80% fiturnya telah tersedia pada repositori tim lain, terdapat dua pilihan konvensional:
    - Mengajukan permohonan fitur (*feature request*) dengan risiko diletakkan pada prioritas terbawah atau dibatalkan karena pemotongan anggaran.
    - Menulis ulang 100% kode secara mandiri hanya demi memperoleh 20% fungsionalitas tambahan untuk menghindari ketergantungan.
  - Solusi *social coding* adalah berkolaborasi: tim pemohon berdiskusi dengan pemilik repositori, membuka tiket tugas (*issue*) di GitHub, menetapkan penugasan ke diri sendiri, membuat cabang kerja (*branch*), lalu mengimplementasikan fitur tersebut.
- **Manfaat Hubungan Saling Menguntungkan (*Win-Win*):**
  - Tim kontributor memperoleh fungsionalitas yang dibutuhkan dengan memanfaatkan 80% fondasi yang telah teruji.
  - Tim pemilik repositori mendapatkan penambahan fitur baru secara cuma-cuma tanpa membebani kapasitas kerja internal mereka.
  - Korporasi menghemat anggaran dan waktu berkat penggunaan ulang perangkat lunak (*software reuse*).

#### C. Praktik Pair Programming dan Peningkatan Kualitas
- **Definisi dan Pembagian Peran:**
  - Berasal dari metodologi *Extreme Programming* (XP), *pair programming* melibatkan dua pemrogram yang bekerja bersama pada satu stasiun kerja tunggal (satu layar, satu papan ketik, dan satu tetikus).
  - **Driver:** Bertindak sebagai eksekutor yang mengetik kode pada papan ketik dan berfokus pada detail implementasi baris demi baris.
  - **Navigator:** Berfokus pada gambaran besar arsitektur, memeriksa kekeliruan sintaksis, menelusuri referensi dokumentasi, dan merencanakan langkah selanjutnya.
  - Kedua peran bertukar posisi secara berkala (rata-rata setiap 20 menit) agar masing-masing pemrogram merasakan sudut pandang eksekusi dan tinjauan strategis.
- **Keuntungan Terukur bagi Organisasi:**
  - **Kualitas Kode Lebih Tinggi:** Berpikir dan berbicara secara terbuka (*programming out loud*) mendorong kejernihan logika berpikir. Banyak galat (*bugs*) terdeteksi seketika saat kode diucapkan dan dijelaskan kepada rekan pasangan.
  - **Penurunan Biaya Perbaikan Cacat:** Semakin awal cacat perangkat lunak terdeteksi, semakin rendah biaya pemeliharaannya di masa mendatang.
  - **Transfer Pengetahuan dan Keterampilan (*Skills Transfer*):** Pasangan pemrogram junior dan senior mempercepat proses pembelajaran praktis mengenai konvensi kode, jalan pintas pengembangan, dan pola penyelesaian masalah.
  - **Eliminasi Ketergantungan Individu (*No Single Point of Failure*):** Memastikan minimal dua orang memahami setiap baris kode yang masuk ke produksi, sehingga operasional sistem tidak lumpuh ketika salah satu personel berhalangan hadir.

---

### 2. Git Repository Guidelines and Workflow

#### A. Struktur Repositori Terpisah vs Mono-Repo
- **Satu Repositori per Komponen:**
  - Setiap komponen mandiri atau layanan mikro (*microservice*) wajib memiliki repositori terdedikasi sendiri.
  - Menggabungkan banyak layanan mikro ke dalam satu repositori tunggal (*mono-repo*) sangat tidak disarankan untuk lingkungan produksi, karena memaksa pengembang mengunduh basis kode yang tidak relevan dengan tanggung jawab tugas mereka.

#### B. Git Feature Branch Workflow
- **Cabang Ringan dan Fana (*Lightweight Feature Branches*):**
  - Di Git, pencabangan kode bersifat sangat ringan. Struktur cabang idealnya hanya terdiri dari cabang utama (*main* atau *master*) dan cabang-cabang fitur individual (*feature branches*).
  - Setiap pekerjaan pembaruan fitur atau perbaikan *bug* wajib dikaitkan dengan tiket permasalahan (*GitHub Issue*) dan dibuatkan cabang terpisah.
  - Hindari keberadaan cabang pengembangan berumur panjang (*long-lived development branches*) yang menampung tumpukan perubahan tanpa integrasi berkala.
  - Setelah cabang fitur selesai ditinjau dan digabungkan ke cabang utama, cabang tersebut harus langsung dihapus.

#### C. Disiplin Integrasi Melalui Pull Request
- **Pintu Gerbang Tunggal Integrasi:**
  - Satu-satunya jalur yang diizinkan untuk memasukkan kode ke cabang utama adalah melalui pengajuan *Pull Request* (PR).
- **Aturan Emas Peninjauan Kode (*Golden Rule*):**
  - Pengembang dilarang keras menggabungkan *pull request* yang dibuatnya sendiri (*never merge your own pull request*).
  - Setiap PR harus ditinjau oleh rekan tim lain sebagai sarana penjaminan mutu (*code review*), memastikan kode dapat dipahami orang lain, serta memvalidasi kelengkapan uji sebelum digabungkan.

---

### 3. Working in Small Batches and Single-Piece Flow

#### A. Landasan Lean Manufacturing dan Umpan Balik Cepat
- **Mereduksi Pemborosan (*Waste Reduction*):**
  - Bekerja dalam kelompok kecil (*small batches*) merupakan prinsip adaptasi dari manufaktur *Lean* untuk menghasilkan siklus umpan balik sesegera mungkin.
  - Mengembangkan fitur dalam skala besar (*large batches*) yang membutuhkan waktu berbulan-bulan berisiko tinggi menghasilkan produk yang tidak diinginkan oleh pasar, membuang sumber daya secara percuma.
- **Akselerasi Pengiriman Menuju Produksi:**
  - Pendekatan kelompok kecil memungkinkan progresi cepat dari tahap pengembangan, pengujian, hingga penerapan di produksi dalam hitungan menit, mendukung terwujudnya CI/CD.

#### B. Analogi Proses Pengiriman Surat: Batch Besar vs Single-Piece Flow
Untuk memahami dampak ukuran *batch*, perhatikan perbandingan proses penanganan 1.000 surat brosur yang melibatkan empat tahapan berurutan: melipat brosur, memasukkan ke amplop, merekatkan lem, dan menempelkan prangko. Asumsikan setiap langkah membutuhkan durasi 6 detik (kecepatan 10 operasi per menit).

- **Skenario Batch Besar (Ukuran Batch = 50 Unit):**
  - Melipat 50 brosur membutuhkan waktu:

$$t_{\text{lipat}} = 50 \times 6\text{ detik} = 300\text{ detik } (5\text{ menit})$$

  - Memasukkan 50 brosur ke amplop membutuhkan tambahan 5 menit (akumulasi waktu mencapai 10 menit).
  - Merekatkan lem pada 50 amplop membutuhkan tambahan 5 menit (akumulasi waktu mencapai 15 menit).
  - Penempelan prangko dimulai pada menit ke-15, sehingga produk jadi pertama baru selesai pada:

$$t_{\text{produk pertama (batch besar)}} = 15\text{ menit} + 6\text{ detik} = 906\text{ detik} \approx 15{,}1\text{ menit}$$

  - **Risiko Kerugian:** Jika amplop ternyata cacat tanpa perekat lem, kesalahan baru terdeteksi pada menit ke-11. Jika brosur memiliki kesalahan ketik (*typo*), seluruh 50 brosur telah terlanjur dilipat dan harus dibuang, memicu pemborosan kerja 15 menit.

- **Skenario Alur Satu Bagian (*Single-Piece Flow*):**
  - Satu brosur dilipat (6 detik), dimasukkan ke amplop (6 detik), direkatkan lem (6 detik), dan ditempel prangko (6 detik).
  - Produk jadi pertama selesai dan siap diinspeksi dalam durasi:

$$t_{\text{produk pertama (single-piece)}} = 4 \times 6\text{ detik} = 24\text{ detik}$$

  - **Keunggulan Umpan Balik:** Kualitas produk dapat divalidasi langsung dalam 24 detik. Jika amplop tidak berlem, kegagalan terdeteksi dalam 18 detik; jika terdapat salah ketik pada brosur, koreksi dapat dilakukan setelah 24 detik tanpa merusak sisa material lainnya.

#### C. Penerapan Ukuran Batch pada Rekayasa Perangkat Lunak
- **Dekomposisi Backlog:**
  - Ukuran *batch* dalam rekayasa perangkat lunak tercermin dari ukuran *user stories* di dalam *backlog*.
  - Sebuah fitur perangkat lunak harus dipecah sedemikian rupa agar dapat diselesaikan secara tuntas dalam waktu satu pekan atau kurang (maksimal satu siklus *sprint*).
  - Mengirimkan subset fungsional yang bernilai secara bertahap jauh lebih menguntungkan daripada menahan pengiriman hingga seluruh target akhir selesai dibangun.

---

### 4. Minimum Viable Product: Building to Learn

#### A. Hakikat Sejati MVP: Pembelajaran vs Pengiriman
- **Koreksi Miskonsepsi:**
  - *Minimum Viable Product* (MVP) bukan sekadar fase pertama dari suatu proyek, bukan versi pengujian alfa/beta, dan bukan produk setengah jadi berkualitas rendah.
  - MVP adalah upaya minimal yang dapat dilakukan untuk menguji hipotesis nilai (*value hypothesis*) serta memperoleh pemahaman empiris mengenai kebutuhan pengguna dengan biaya serendah mungkin.
- **Fokus pada Pembelajaran (*Learning*):**
  - Rilis bertahap tradisional berfokus pada pertanyaan: *"Apa yang akan kita kirimkan?"* (*delivery-oriented*).
  - Pendekatan MVP berfokus pada pertanyaan: *"Apa yang dapat kita pelajari dari respons pengguna?"* (*learning-oriented*).
- **Keputusan Strategis: Pivot atau Persevere:**
  - Di akhir setiap pengujian MVP, tim menganalisis data riil untuk menentukan arah langkah:
    - **Pivot:** Mengubah strategi, asumsi, atau fitur produk jika hipotesis awal terbukti salah.
    - **Persevere:** Melanjutkan dan memperdalam pengembangan fitur jika hipotesis terbukti memberikan nilai nyata.

#### B. Analogi Evolusi Kendaraan: Siklus Tradisional vs Pendekatan MVP
- **Pendekatan Iteratif Tanpa Pemahaman MVP (Kasus Mobil Merah):**
  - Klien meminta sebuah mobil berwarna merah:
    - Iterasi 1: Tim mengirimkan sebuah roda tunggal. Klien tidak dapat menggunakannya untuk transportasi.
    - Iterasi 2: Tim mengirimkan sasis logam. Klien tetap tidak dapat memanfaatkannya.
    - Iterasi 3: Tim mengirimkan badan mobil tanpa kemudi.
    - Iterasi 4: Mobil lengkap diserahkan di akhir periode.
  - **Kelemahan:** Klien tidak dapat memberikan umpan balik fungsional di sepanjang proses; tim hanya menjalankan rencana kaku tanpa validasi bertahap.
- **Pendekatan Berbasis MVP Berorientasi Nilai:**
  - Klien meminta solusi transportasi cepat dengan mobil berwarna merah:
    - **MVP 1 (Papan Luncur Merah):** Menguji kenyamanan warna dan mobilitas dasar. Klien mengonfirmasi warna merah sangat disukai, namun kendali arah sulit dilakukan.
    - **MVP 2 (Skuter dengan Stang):** Menambahkan mekanisme kemudi. Klien merasa kendali membaik, namun membutuhkan kecepatan lebih tinggi untuk jarak jauh.
    - **MVP 3 (Sepeda Motor):** Menambahkan mesin penggerak bertenaga. Saat berkendara dan merasakan hembusan angin, klien menyadari kebutuhan emosional dan fungsionalnya yang sesungguhnya: mereka tidak menginginkan sedan tertutup, melainkan mobil atap terbuka (*convertible*).
  - **Hasil Akhir:** Klien memperoleh produk yang benar-benar mereka dambakan (*what they really desire*), bukan sekadar apa yang mereka asumsikan di awal perencanaan.

---

### 5. Test-Driven Development: Designing from the Inside Out

#### A. Landasan Filosofis TDD
- **Kaidah Pengujian:**
  - Prinsip fundamental pengembangan: jika suatu kode layak untuk dibangun, kode tersebut mutlak layak untuk diuji (*if it is worth building, it is worth testing*).
- **Definisi TDD:**
  - Kasus uji mengarahkan desain arsitektur dan penulisan kode sumber secara langsung (*test cases drive the design and development*).
  - Pengembang menulis kasus uji untuk perilaku kode yang diharapkan ada (*code you wish you had*), baru kemudian menulis kode implementasi untuk meloloskan pengujian tersebut.
- **Perspektif Pemanggil (*Caller's Perspective*):**
  - Menulis pengujian terlebih dahulu memaksa pengembang memposisikan diri sebagai pihak luar yang mengonsumsi modul atau API tersebut.
  - Hal ini mencegah rancangan API yang buruk, seperti fungsi dengan terlalu banyak parameter yang sulit disediakan oleh pemanggil.

#### B. Menjawab Alasan Penolakan Penulisan Tes
- **Alasan 1: "Saya sudah yakin kode saya berfungsi dengan baik."**
  - Kode mungkin berfungsi saat ini, namun pengembang lain atau diri kita sendiri di masa mendatang (*future you*) tidak memiliki jaminan saat memodifikasi bagian sistem terkait. Menjalankan pengujian adalah langkah pertama sebelum dan sesudah menyentuh repositori.
- **Alasan 2: "Saya tidak menulis kode yang rusak."**
  - Lingkungan di bawah aplikasi terus bergerak: versi dependensi diperbarui dan celah keamanan ditambal (seperti bencana kebocoran data Equifax akibat kerentanan pustaka Apache Struts). Tanpa rangkaian uji otomatis, pembaruan pustaka keamanan menjadi aktivitas yang sangat berbahaya.
- **Alasan 3: "Saya tidak memiliki waktu untuk menulis pengujian."**
  - Mengabaikan pengujian adalah ilusi penghematan waktu. Menulis beberapa kasus uji di awal menghemat puluhan jam pelacakan galat (*debugging*) manual di kemudian hari.

#### C. Alur Kerja Red, Green, Refactor
- **1. Red (Kasus Uji Gagal):**
  - Tulis kasus uji untuk fungsionalitas baru sebelum kode implementasi dibuat. Jalankan pengujian dan pastikan uji tersebut gagal (*output* berwarna merah) guna memvalidasi bahwa kasus uji berfungsi mendeteksi ketidakhadiran fitur.
- **2. Green (Lolos Pengujian):**
  - Tulis kode implementasi seminimal mungkin hanya agar pengujian berhasil lolos (*output* berwarna hijau). Kode tidak perlu elegan pada tahap ini.
- **3. Refactor (Penyempurnaan Struktur):**
  - Rapikan struktur kode, hilangkan duplikasi, dan tingkatkan keterbacaan serta performa dengan keyakinan penuh bahwa perilaku sistem tetap terjaga selama pengujian tetap berstatus hijau.
- **Peran Kritis dalam CI/CD:**
  - Pipa rilis otomatis (*automated CI/CD pipeline*) mustahil diwujudkan tanpa otomatisasi pengujian. Menerapkan integrasi dan penerapan berkelanjutan tanpa pengujian otomatis hanya akan mempercepat pengiriman galat (*bugs*) ke lingkungan produksi.

---

### 6. Behavior-Driven Development: Collaborating from the Outside In

#### A. Esensi BDD dan Perbandingannya dengan TDD
- **Perspektif Luar ke Dalam (*Outside-In*):**
  - *Behavior-Driven Development* (BDD) memusatkan perhatian pada perilaku sistem sebagaimana diamati oleh pengguna akhir atau sistem eksternal.
  - BDD menyatukan pemahaman antara pakar domain bisnis, pemilik produk (*product owner*), tim penguji (*QA*), dan pengembang melalui notasi bahasa tunggal yang mudah dipahami.
- **Komparasi Fundamental:**
  - **TDD (Inside-Out):** Menguji fungsionalitas komponen internal secara mendalam, memastikan bahwa sistem dibangun dengan benar (*building the thing right*).
  - **BDD (Outside-In):** Menguji perilaku antarmuka dan integrasi tingkat tinggi, memastikan bahwa sistem yang dibangun adalah produk yang tepat sesuai kebutuhan bisnis (*building the right thing*).

#### B. Format Bahasa Gherkin
Dokumen BDD ditulis menggunakan sintaks bahasa alami terstruktur yang disebut Gherkin (*Given... When... Then...*):
- **Given (Konteks Awal):**
  - Menetapkan prakondisi sistem ke dalam status awal yang telah diketahui sebelum interaksi dimulai.
- **When (Aksi/Peristiwa):**
  - Menggambarkan tindakan utama atau peristiwa pemicu yang dilakukan oleh pengguna atau sistem eksternal.
- **Then (Hasil yang Dapat Divalidasi):**
  - Memverifikasi luaran, perubahan status, atau manfaat bisnis yang dihasilkan dari aksi tersebut.
- **And (Penghubung Tambahan):**
  - Digunakan untuk menambahkan konteks, aksi, atau hasil validasi lanjutan secara terstruktur.

#### C. Contoh Skenario dan Eksekusi Otomatis
Berikut adalah contoh berkas fitur (*feature file*) untuk manajemen inventaris toko:

```gherkin
Feature: Returns go to stock
  As a store owner
  I need returned items to be added back to inventory
  So that stock levels remain accurate

  Scenario: Refunded items should be returned to stock
    Given that a customer previously bought a black sweater from me
    And I have 3 black sweaters in stock
    When they return the black sweater for a refund
    Then I should have 4 black sweaters in stock
```

- **Eksekusi Pengujian Langsung:**
  - Berkas spesifikasi di atas bukan sekadar dokumentasi pasif; perkakas BDD (seperti Behave pada Python, Cucumber pada Ruby, atau jBehave pada Java) dapat mengeksekusi teks tersebut secara langsung sebagai skrip pengujian penerimaan otomatis (*automated acceptance tests*).
  - Menghilangkan ambiguitas penentuan kriteria selesai (*definition of done*) di akhir siklus *sprint*: kode dinyatakan selesai jika dan hanya jika seluruh skenario lolos uji.

---

### 7. Cloud-Native Microservices Architecture

#### A. Prinsip Layanan Mikro dan The Twelve-Factor App
- **Definisi Martin Fowler dan James Lewis:**
  - Arsitektur layanan mikro adalah pendekatan pengembangan perangkat lunak sebagai kesatuan layanan-layanan kecil independen.
  - Setiap layanan berjalan dalam proses komputasi mandiri dan berkomunikasi menggunakan mekanisme berbobot ringan, umumnya berbasis antarmuka HTTP REST API.
  - Dibangun berdasarkan kapabilitas domain bisnis (*business capabilities*) dan dapat diterapkan ke produksi secara independen melalui otomatisasi penuh.
- **Karakteristik Cloud-Native dan The Twelve-Factor App:**
  - Aplikasi dirancang sejak awal untuk memanfaatkan elastisitas dan skalabilitas horizontal komputasi awan, mengikuti metodologi *The Twelve-Factor App* yang dirumuskan oleh pengembang Heroku pada tahun 2011.

#### B. Pemisahan Status dan Skalabilitas Independen
- **Layanan Nir-Status (*Stateless Microservices*):**
  - Layanan mikro tidak boleh menyimpan status sesi (*session state*) di dalam memori lokal secara tersembunyi.
  - Setiap layanan bertanggung jawab penuh mengelola statusnya sendiri pada basis data atau penyimpanan objek persisten terpisah (*database per service*).
  - **Peringatan Anti-Pola:** Jika beberapa layanan berbagi akses langsung ke tabel basis data yang sama, arsitektur tersebut bukanlah layanan mikro, melainkan monolit terdistribusi (*distributed monolith*).
- **Prinsip Ternak vs Hewan Peliharaan (*Cattle, Not Pets*):**
  - Instans komputasi awan diposisikan sebagai komoditas yang dapat digantikan seketika (*cattle*), bukan entitas istimewa yang harus dirawat secara manual saat rusak (*pets*).
  - Jika satu instans bermasalah, instans tersebut langsung dimatikan dan digantikan oleh instans baru secara otomatis.
- **Skalabilitas Granular:**
  - Jika modul notifikasi mengalami lonjakan beban kerja, tim cukup melipatgandakan jumlah instans modul notifikasi secara horizontal tanpa perlu memboroskan sumber daya untuk memperbesar modul pembayaran atau profil pengguna.

#### C. Perbandingan Arsitektur: Monolitik vs Layanan Mikro
- **Aplikasi Monolitik:**
  - Seluruh modul logika bisnis, komputasi, dan basis data terikat menjadi satu kesatuan biner raksasa.
  - Perubahan pada satu skema tabel basis data (misalnya tabel pelanggan) menuntut koordinasi rumit antartim pemesanan, tim pengiriman, dan tim penagihan, serta mewajibkan pengujian regresi menyeluruh dan rilis ulang seluruh sistem secara masif.
- **Aplikasi Layanan Mikro:**
  - Komunikasi antarlayanan terisolasi melalui kontrak REST API yang jelas.
  - Tim pengelola layanan pelanggan bebas mengubah struktur penyimpanan internal (misalnya beralih dari basis data relasional SQL ke basis data dokumen NoSQL) tanpa memengaruhi layanan pemesanan, selama kontrak keluaran REST API tetap konsisten.

---

### 8. Designing for Failure: Building Resilient Systems

#### A. Paradigma Merangkul Kegagalan
- **Kegagalan adalah Kepastian:**
  - Dalam sistem terdistribusi berskala besar dengan ratusan layanan mikro yang saling terhubung melalui jaringan, kegagalan infrastruktur, lonjakan latensi, dan pemadaman layanan (*outages*) pasti akan terjadi.
  - Pola pikir rekayasa harus bergeser dari upaya mustahil mencegah kegagalan menuju perancangan sistem yang mampu mendeteksi kegagalan dan pulih secara instan (*design for failure*).
- **Pergeseran Metrik: MTTF ke MTTR:**
  - Tolok ukur keandalan tidak lagi berpusat pada durasi rata-rata sebelum terjadinya kerusakan (*Mean Time to Failure* / MTTF), melainkan pada kecepatan pemulihan sistem saat insiden terjadi (*Mean Time to Recovery* / MTTR).
- **Kesiapan Menghadapi Throttling:**
  - Layanan komputasi awan memberlakukan batas kuota konsumsi (*rate limits*). Ketika kuota terlampaui, sistem penyedia akan menolak permintaan dengan kode status `429 Too Many Requests`.
  - Aplikasi harus dirancang memiliki logika penurunan performa secara anggun (*graceful degradation*) serta mengimplementasikan mekanisme penyimpanan sementara (*caching*) untuk data statis guna menekan panggilan jaringan yang tidak perlu.

#### B. Pola Desain Ketahanan Arsitektur (Resilience Design Patterns)
- **1. Retry Pattern dengan Exponential Backoff:**
  - Digunakan untuk menangani kegagalan sementara (*transient failures*) seperti gangguan jaringan sesaat.
  - Hindari melakukan percobaan ulang (*retry*) secara agresif dalam interval waktu yang rapat karena akan membanjiri layanan target yang sedang tertekan.
  - Terapkan penundaan eksponensial (*exponential backoff*):

$$t_{\text{tunggu}} = t_0 \times 2^{n}$$

  - Di mana $t_0$ adalah basis durasi awal dan $n$ adalah urutan percobaan (misalnya jeda 1 detik, 2 detik, 4 detik, 8 detik). Setelah batas toleransi terlampaui, sistem mengembalikan status galat tanpa merusak antrean.
- **2. Circuit Breaker Pattern:**
  - Terinspirasi dari sakelar pemutus sirkuit listrik rumah tangga, pola ini mencegah terjadinya kegagalan berantai (*cascading failures*) di mana kelumpuhan satu layanan merembet ke layanan lain.
  - Memiliki tiga kondisi kerja:
    - **Closed (Normal):** Permintaan diteruskan ke layanan target sembari sistem memantau frekuensi keberhasilan dan kegagalan.
    - **Open (Terputus):** Jika ambang batas kegagalan terlampaui, sirkuit memutus jalur. Seluruh panggilan berikutnya langsung dibatalkan atau dialihkan ke respons cadangan tanpa menghubungi layanan target yang sedang rusak.
    - **Half-Open (Uji Coba):** Setelah interval waktu tertentu terlewati (*timeout*), sistem mengizinkan sejumlah kecil permintaan percobaan untuk memastikan apakah layanan target telah pulih. Jika berhasil, status kembali ke *Closed*; jika gagal, status kembali ke *Open*.
- **3. Bulkhead Pattern:**
  - Terinspirasi dari dinding sekat kedap air (*bulkhead*) pada lambung kapal laut. Jika lambung kapal bocor, air hanya memenuhi satu kompartemen tertutup tanpa menenggelamkan seluruh kapal.
  - Dalam perangkat lunak, pola ini mengisolasi alokasi sumber daya kritis (seperti penyediaan kolam utas /*thread pools* terpisah atau kuota koneksi basis data independen antarfitur). Jika salah satu kolam koneksi lumpuh, fitur lain tetap beroperasi tanpa gangguan.

#### C. Chaos Engineering: Pengujian Ketahanan Proaktif
- **Pembuktian Ketahanan Empiris:**
  - *Chaos engineering* adalah disiplin pengujian proaktif dengan sengaja menyuntikkan kegagalan ke dalam sistem produksi guna memvalidasi efektivitas pola-pola ketahanan yang telah dipasang.
- **Inovasi Netflix Simian Army:**
  - Netflix mengembangkan perangkat otomatis bernama *Chaos Monkey* yang bertugas mematikan instans produksi secara acak selama jam kerja.
  - Pendekatan ini memastikan bahwa para pengembang membangun sistem yang secara inheren mampu pulih secara mandiri ketika instans atau zona ketersediaan komputasi awan mendadak hilang.

---

### 9. Key Takeaways and Summary

#### A. Poin-Poin Pokok Modul 02
- **Kolaborasi Terbuka Melalui Social Coding:**
  - Repositori internal yang terbuka dan praktik *pair programming* meningkatkan kualitas kode, mempercepat pembelajaran tim, serta memangkas biaya pemeliharaan.
- **Disiplin Pencabangan Git:**
  - Penggunaan cabang fitur berumur pendek (*feature branches*) yang diverifikasi melalui *Pull Request* dan tinjauan rekan kerja menjamin stabilitas cabang utama.
- **Efisiensi Alur Kerja Small Batches:**
  - Pendekatan *single-piece flow* mempercepat siklus deteksi kesalahan dari hitungan menit/jam menjadi detik, menekan pemborosan sumber daya secara drastis.
- **Orientasi Pembelajaran pada MVP:**
  - MVP adalah sarana eksperimen untuk memvalidasi hipotesis nilai bersama pelanggan, mengarahkan tim untuk mengambil keputusan *pivot* atau *persevere* secara objektif.
- **Sinergi TDD dan BDD:**
  - TDD menjamin kode dibangun dengan benar dari dalam ke luar (*inside-out*), sedangkan BDD memastikan produk yang dibangun sesuai dengan ekspektasi bisnis dari luar ke dalam (*outside-in*).
- **Arsitektur Cloud-Native dan Ketahanan Sistem:**
  - Layanan mikro nir-status (*stateless*) memaksimalkan skalabilitas horizontal komputasi awan.
  - Karena kegagalan tidak dapat dihindari, sistem modern menerapkan pola *retry with backoff*, *circuit breaker*, *bulkhead*, serta validasi berkala melalui *chaos engineering*.