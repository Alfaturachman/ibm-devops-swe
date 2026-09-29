# Organizing for DevOps

Dokumen ini menyajikan rangkuman komprehensif mengenai strategi pengorganisasian tim dalam DevOps, dampak Hukum Conway terhadap arsitektur sistem, restrukturisasi tim berbasis domain bisnis, bahaya anti-pola pembentukan tim DevOps terpisah, serta penanaman rasa tanggung jawab bersama melalui prinsip kepemilikan ujung ke ujung (*end-to-end ownership*).

---

### 1. Organizational Impact of DevOps and Conway's Law

#### A. Kriteria Struktur Tim DevOps yang Efektif
- **Fondasi Pola Pikir Agile:**
  - Keberhasilan transformasi *DevOps* berakar dari adopsi pola pikir tangkas (*Agile mindset*) di tingkat organisasi secara menyeluruh.
- **Karakteristik Pokok Tim Berperforma Tinggi:**
  - **1. Berukuran Kecil (*Small Teams*):**
    - Ukuran optimal tim berkisar antara 5 hingga 7 insinyur, dengan batas maksimal 10 orang (selaras dengan aturan *two-pizza team*).
    - Membatasi ukuran tim meminimalkan ledakan jumlah jalur komunikasi antarpribadi yang dapat dihitung dengan rumus:

$$C = \frac{n(n - 1)}{2}$$

  - Pada tim beranggotakan $n = 7$ orang, hanya terdapat $C = 21$ jalur komunikasi; sedangkan pada tim beranggotakan $n = 20$ orang, jalur komunikasi melonjak drastis menjadi $C = 190$ jalur, memicu inefisiensi koordinasi.
  - **2. Berdedikasi Penuh (*Dedicated*):**
    - Anggota tim tidak boleh dibagi ke dalam banyak proyek secara bersamaan. Pergantian konteks (*context switching*) merusak konsentrasi, memperlambat kecepatan rilis, dan mengaburkan fokus jangka panjang.
  - **3. Lintas Fungsi (*Cross-Functional*):**
    - Sebuah tim pengembangan sejati mencakup seluruh keahlian yang dibutuhkan untuk melahirkan produk: pengembang perangkat lunak, teknisi pengujian (*test engineers*), teknisi operasional (*operations engineers*), analis bisnis, hingga spesialis keamanan.
    - Kolaborasi terjalin secara langsung antaranggota tim tanpa melalui sistem birokrasi antrean tiket (*ticket queues*).
  - **4. Swakelola (*Self-Organizing*):**
    - Tim memiliki otonomi untuk mengorganisasi cara kerja mereka sendiri dan berkomitmen menyelesaikan paket tugas per siklus *sprint*.

#### B. Implikasi Hukum Conway (Conway's Law)
- **Pernyataan Hukum Conway (Melvin Conway, 1968):**
  - *"Setiap organisasi yang merancang suatu sistem (didefinisikan secara luas) akan menghasilkan desain yang strukturnya merupakan salinan dari struktur komunikasi organisasi tersebut."*
- **Manifestasi Hukum Conway pada Sistem Tiga Lapis:**
  - Jika sebuah perusahaan menugaskan 4 tim terpisah untuk membangun sebuah kompilator, maka hasil akhirnya pasti berupa *four-pass compiler*.
  - Ketika organisasi membagi departemen teknologi berdasarkan lapisan keahlian teknis:
    - Tim antarmuka pengguna (*front-end team*).
    - Tim logika aplikasi (*back-end team*).
    - Tim pengelola basis data (*database administrators* / DBA).
  - Maka arsitektur perangkat lunak yang tercipta pasti berupa arsitektur monolitik tiga lapis (*three-tier architecture*). Setiap penambahan fitur sekecil apa pun menuntut koordinasi antartiga silo fungsional melalui pembukaan tiket birokratis.

#### C. Restrukturisasi Berbasis Domain Bisnis (Business Domains)
- **Penyelarasan Arsitektur dengan Struktur Organisasi:**
  - Jika organisasi ingin mengadopsi arsitektur layanan mikro (*microservices*), langkah pertama yang wajib dilakukan adalah merestrukturisasi tim pengembang agar selaras dengan arsitektur target (*Reverse Conway Maneuver*).
- **Pembagian Tim Berorientasi Domain:**
  - Tim tidak lagi dikelompokkan berdasarkan teknologi horizontal, melainkan berdasarkan kapabilitas domain bisnis vertikal:
    - **Tim Akun (*Account Team*):** Mengelola alur pendaftaran, autentikasi login, dan profil pengguna dari antarmuka, logika bisnis, hingga basis data tersendiri.
    - **Tim Personalisasi (*Personalization Team*):** Merancang algoritma rekomendasi bertenaga kecerdasan buatan (AI) beserta antarmuka dan penyimpanan data mandiri.
    - **Tim Pergudangan (*Warehouse Team*):** Membangun kapabilitas penerimaan barang, pengiriman logistik, dan manajemen inventaris secara tuntas dari hulu ke hilir.
- **Model Perusahaan Rintisan Mini (*Mini Start-up*):**
  - Setiap tim domain memiliki otonomi penuh layaknya *startup* independen.
  - Memegang tanggung jawab penuh siklus hidup layanan (*commit, build, deploy, maintain, operate*) tanpa hambatan ketergantungan antartim.
  - Memiliki misi jangka panjang (*long-term mission*) yang menumbuhkan rasa kepemilikan mendalam (*ownership*) dan kebanggaan atas kualitas karya mereka.

---

### 2. The Anti-Pattern: There Is No DevOps Team

#### A. Miskonsepsi Seputar Peran dan Judul Pekerjaan
- **Kekeliruan Pemandangan Industri:**
  - Banyak korporasi salah mengartikan *DevOps* sebagai posisi pekerjaan individual (*job title*) atau sekadar ekstensi modern dari divisi operasional (*Technical Ops*).
- **Esensi Huruf D-E-V:**
  - Elemen "Dev" dalam *DevOps* merepresentasikan rekayasa pengembangan perangkat lunak (*software development*).
  - Jika suatu peran hanya berkutat pada pemeliharaan server dan perkakas tanpa menyentuh rekayasa kode perangkat lunak, aktivitas tersebut hanyalah operasional tradisional (*Ops*), bukan *DevOps*.

#### B. Bahaya Membentuk "Tim DevOps" Terpisah
- **Kritik Keras Jez Humble:**
  - Jez Humble menegaskan bahwa gerakan *DevOps* lahir untuk mengatasi disfungsi organisasi yang disebabkan oleh keberadaan silo-silo fungsional.
  - Membentuk satu silo baru bernama "Tim DevOps" yang berada di antara tim pengembang (*Dev*) dan tim operasional (*Ops*) merupakan solusi yang sangat keliru, ironis, dan memperparah birokrasi komunikasi.
- **Mengapa Tim DevOps Merupakan Anti-Pola (*Antipattern*):**
  - Tim *DevOps* terpisah hanya menjadi perantara baru yang memperpanjang jarak komunikasi.
  - Bukannya meruntuhkan Tembok Kebingungan (*wall of confusion*), pembentukan tim ini justru menciptakan dua tembok pemisah baru: antara *Dev* dengan *DevOps*, serta antara *DevOps* dengan *Ops*.
- **Analogi dengan Transformasi Agile:**
  - Organisasi tidak pernah membentuk "tim Agile" khusus untuk menjadikan perusahaan tangkas.
  - Seluruh organisasi secara holistik mengadopsi prinsip dan cara kerja tangkas. Hal yang sama berlaku mutlak bagi *DevOps*: *DevOps* adalah transformasi budaya pada skala organisasi, bukan unit departemen tersendiri.

#### C. Pilar Budaya Kerja Kolaboratif
- **Satu Kesatuan Tim dan Metrik:**
  - Praktik *DevOps* yang sejati menyatukan teknisi *Dev* dan *Ops* ke dalam satu tim lintas fungsi yang sama, bekerja di sepanjang siklus hidup perangkat lunak dengan sasaran dan tolok ukur kesuksesan bersama.
- **Tiga Fondasi Perilaku:**
  - **1. Keterbukaan (*Openness*):** Kesiapan untuk saling berbagi informasi dan menerima masukan lintas disiplin.
  - **2. Transparansi (*Transparency*):** Seluruh metrik operasional, riwayat rilis, dan kendala sistem dapat dilihat secara terbuka oleh seluruh anggota organisasi.
  - **3. Rasa Percaya (*Trust*):** Manajemen memercayai tim untuk mengambil keputusan teknis terbaik secara mandiri tanpa rantai persetujuan berlapis.

---

### 3. Fostering Accountability: Everyone Is Responsible for Success

#### A. Dampak Pemisahan Tindakan dari Konsekuensi
- **Akar Sikap Apatis (*Apathy*):**
  - Jez Humble merumuskan kaidah mendasar: *"Perilaku buruk muncul ketika manusia dipisahkan dari konsekuensi atas tindakan yang mereka perbuat."*
  - Bekerja dalam sekat silo membebaskan individu dari melihat dan merasakan secara langsung dampak negatif kesalahan pekerjaan mereka terhadap departemen lain.
- **Studi Kasus Pembentukan Tim QA Terpisah:**
  - Sebuah perusahaan yang mengalami kendala kualitas kode memutuskan untuk membentuk divisi penjaminan mutu (*Quality Assurance* / QA) terpisah.
  - Secara mengejutkan, kualitas perangkat lunak justru merosot tajam setelah tim QA dibentuk.
  - **Analisis Penyebab:**
    - Para pengembang merasa tidak lagi bertanggung jawab atas pengujian kode mereka sendiri.
    - Fokus pengembang bergeser dari membangun kode bermutu menjadi sekadar melempar fitur sebanyak mungkin ke fase pengujian secepatnya, dengan asumsi bahwa pengujian adalah urusan tim QA.
    - Tim QA kewalahan menangani volume pengujian masif dan cacat logika yang tidak terdeteksi sejak dini, sehingga kode bermasalah merembes ke lingkungan produksi.

#### B. Menumbuhkan Empati dan Tanggung Jawab Lintas Disiplin
- **1. Pengembang Bertanggung Jawab Penuh Atas Pengujian:**
  - Mengeliminasi divisi QA terpisah dan membebankan tanggung jawab penulisan pengujian unit, pengujian integrasi, dan pengujian penerimaan otomatis langsung kepada para pengembang perangkat lunak.
- **2. Rotasi Peran dan Keterlibatan Langsung (*Empathy Building*):**
  - Jika tim lintas fungsi belum terbentuk seutuhnya, lakukan rotasi kerja berkala di mana pengembang ditugaskan ke bagian operasional untuk merasakan tantangan pemeliharaan sistem produksi secara nyata.
  - Teknisi operasional diundang untuk menghadiri pertemuan harian (*daily standup*) dan demonstrasi produk (*showcase*) pengembang.
- **3. Kebijakan Siaga Darurat Pengembang (*On-Call Rotation / Pager Duty*):**
  - Menetapkan jadwal piket darurat bagi pengembang untuk menangani insiden kegagalan aplikasi di lingkungan produksi secara langsung.
  - Pengalaman menangani panggilan darurat sistem pada pukul 03.00 dini hari di akhir pekan akan secara instan mengubah pola pikir pengembang untuk menulis kode yang lebih tangguh, memiliki penanganan galat yang solid, dan mudah dipantau pada hari kerja berikutnya.

#### C. Sasaran Organisasi: Kesadaran Bersama dengan Kendali Lokal
- **Shared Consciousness with Distributed, Local Control:**
  - Setiap individu memahami arah strategis dan visi besar yang dituju organisasi (*shared consciousness*).
  - Namun, wewenang pengambilan keputusan teknis mengenai cara mencapai tujuan tersebut didelegasikan sepenuhnya kepada tim lokal di garis depan (*distributed, local control*).
- **Prinsip Kepemilikan Amazon:**
  - Menghidupi prinsip legendaris dari Werner Vogels (CTO Amazon):

$$\text{"You build it, you run it!"}$$

  - Hilangkan dikotomi antara pembuat sistem dan pemelihara sistem. Seluruh personel memiliki wewenang sekaligus tanggung jawab penuh untuk menghantarkan nilai nyata yang stabil bagi pelanggan.

---

### 4. Key Takeaways and Summary

#### A. Poin-Poin Strategis Modul 04
- **Ukuran dan Otonomi Tim:**
  - Bentuk tim kecil (5-7 orang), berdedikasi penuh, lintas fungsi, dan swakelola guna meminimalkan jalur komunikasi dan inefisiensi.
- **Manfaatkan Hukum Conway:**
  - Atur ulang struktur tim mengelilingi domain bisnis mandiri (*business domains*) untuk melahirkan arsitektur layanan mikro yang modular dan terisolasi.
- **DevOps Bukanlah Tim Terpisah:**
  - Hindari anti-pola pembentukan divisi "Tim DevOps". Transformasi harus merata di seluruh organisasi melalui penyatuan *Dev* dan *Ops* di bawah metrik kinerja bersama.
- **Kaitkan Tindakan dengan Konsekuensi:**
  - Tumbuhkan empati dan integritas mutu dengan melibatkan pengembang dalam tanggung jawab pengujian serta rotasi panggilan siaga operasional (*pager duty*).
- **Kepemilikan Penuh Siklus Hidup:**
  - Terapkan filosofi *you build it, you run it* dengan memberikan otonomi lokal bagi tim untuk merancang, menguji, menerapkan, dan mengoperasikan produk mereka secara mandiri.
