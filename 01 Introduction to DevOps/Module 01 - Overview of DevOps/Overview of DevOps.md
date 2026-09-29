# Overview of DevOps

Dokumen ini menyajikan rangkuman komprehensif mengenai konsep dasar DevOps, urgensi bisnis di era disrupsi, pilar-pilar agilitas, transisi historis dari Waterfall dan Agile, hingga tokoh dan tonggak penting yang membentuk gerakan DevOps modern.

---

### 1. Introduction to DevOps and Cultural Transformation

#### A. Tantangan Perubahan Budaya vs Keterampilan Teknis
- **Tingginya Kebutuhan Talenta:**
  - Laporan dari *DevOps Institute* memproyeksikan bahwa permintaan terhadap keterampilan *DevOps* diperkirakan tumbuh hingga 122% dalam lima tahun, menjadikannya salah satu keahlian dengan pertumbuhan tercepat di dunia industri.
- **Penyebab Utama Kegagalan Inisiatif:**
  - Riset Gartner memprediksi bahwa 75% inisiatif *DevOps* akan gagal memenuhi ekspektasi organisasi bukan karena kekurangan keterampilan teknis atau keterbatasan alat bantu (*tools*), melainkan akibat kendala dalam pembelajaran organisasi (*organizational learning*) serta perubahan budaya kerja (*cultural change*).
  - George Spafford (Senior Director Analyst di Gartner) menegaskan bahwa faktor manusia (*people-related factors*) merupakan rintangan terbesar yang dihadapi perusahaan, bukan faktor teknologi.
- **Korelasi Budaya dan Kinerja Bisnis:**
  - Laporan *Accelerate State of DevOps Report* 2021 oleh tim DORA (*DevOps Research and Assessment*) yang mengolah data selama 7 tahun dari 32.000 lebih praktisi di seluruh dunia menyatakan bahwa budaya tim (*team culture*) menjadi pembeda paling signifikan terhadap kapasitas organisasi dalam mengirimkan perangkat lunak dan melampaui target bisnis.

#### B. Esensi dan Filosofi DevOps
- **Bukan Sekadar Peran atau Alat:**
  - *DevOps* bukan nama posisi pekerjaan (*job title*) dan bukan sebuah produk perangkat lunak atau perkakas tunggal (*tool*).
  - *DevOps* merupakan perpaduan budaya dan praktik kolaboratif antara teknisi pengembang (*development*) dan tim operasional (*operations*) di sepanjang siklus hidup pengembangan perangkat lunak (*software development lifecycle* / SDLC).
- **Prinsip Utama:**
  - Mengadopsi prinsip *Lean* dan *Agile* untuk menghantarkan perangkat lunak secara cepat (*rapid*), teratur, dan berkesinambungan (*continuous*).
  - Mengubah paradigma dari sekadar menjalankan *DevOps* secara mekanis menjadi menghidupi budaya kolaboratif (*we do not "do" DevOps, we "become" DevOps*).
- **Pola Pikir Kegagalan:**
  - Menumbuhkan budaya *fail fast*: kegagalan dalam eksperimen adalah hal wajar karena setiap kegagalan diposisikan sebagai peluang belajar (*learning opportunity*).
  - Memupuk nilai-nilai inti tim berupa kerja sama tim (*teamwork*), akuntabilitas bersama (*accountability*), dan transparansi serta rasa saling percaya (*trust*).

#### C. Empat Pilar Transformasi Budaya
- **1. Berpikir Berbeda (*How to Think*):**
  - Mengembangkan budaya *social coding*, keterbukaan kode, serta meningkatkan penggunaan ulang (*software reuse*) dan berbagi komponen perangkat lunak antartim.
  - Menerapkan konsep *Lean manufacturing*, seperti bekerja dalam kelompok kerja kecil (*small batches*) guna menekan pemborosan (*waste*).
- **2. Bekerja Berbeda (*How to Work*):**
  - Menggunakan pendekatan *minimum viable product* (MVP) untuk menguji hipotesis dan memperoleh wawasan bernilai secara cepat dari pengguna.
  - Mengimplementasikan praktik *test-driven development* (TDD) dan *behavior-driven development* (BDD) guna menjamin kualitas kode serta perilaku sistem yang teruji secara konsisten.
  - Menerapkan *Continuous Integration* (CI) dan *Continuous Delivery* (CD) agar setiap perubahan kode berpotensi menjadi fitur yang siap dirilis ke produksi (*potentially shippable feature*).
- **3. Mengorganisasi Tim Berbeda (*How to Organize*):**
  - Struktur pengorganisasian tim berpengaruh langsung terhadap arsitektur dan rancangan perangkat lunak yang dihasilkan (sesuai hukum Conway).
  - Mengubah struktur hierarki silo menjadi tim lintas fungsi (*cross-functional teams*) yang mandiri dan berfokus pada produk (*product-oriented*).
- **4. Mengukur Berbeda (*How to Measure*):**
  - Menyelaraskan sistem metrik agar menghargai perilaku yang tepat (*you get what you measure*).
  - Menghindari metrik semu (*vanity metrics*) yang hanya terlihat bagus di atas kertas namun tidak merefleksikan nilai nyata.
  - Memprioritaskan metrik yang dapat ditindaklanjuti (*actionable metrics*) guna menarik wawasan mendalam mengenai kepuasan pelanggan dan stabilitas produk.

---

### 2. Business Case for DevOps: Navigating Disruption

#### A. Realitas Disrupsi Bisnis Fortune 500
- **Tingkat Kepunahan Perusahaan Besar:**
  - Sejak tahun 2000, sebanyak 52% perusahaan yang terdaftar dalam Fortune 500 telah hilang dari daftar atau gulung tikar akibat ketidakmampuan menghadapi gelombang disrupsi.
  - Pertanyaan strategis bagi setiap organisasi saat ini bukan lagi perihal *apakah* mereka akan terdisrupsi, melainkan *kapan* disrupsi tersebut akan datang (*not if, but when*).
- **Urgensi Kecepatan Rilis di Sektor Tradisional:**
  - Institusi mapan seperti perbankan kerap merasa aman dari ancaman disrupsi luar.
  - Ketika sebuah bank pesaing meluncurkan fitur setoran cek melalui kamera ponsel (*mobile check deposit*), bank petahana yang memerlukan waktu 6 bulan hanya untuk merilis pembaruan serupa akan kehilangan nasabah dalam jumlah masif.

#### B. Teknologi sebagai Pemungkin vs Model Bisnis Inovatif
- **Teknologi sebagai Enabler:**
  - Teknologi hanyalah instrumen pemungkin inovasi (*enabler of innovation*), bukan pendorong mandiri (*driver of innovation*).
  - Perusahaan pendobrak (*disruptors*) dan institusi petahana (*incumbents*) memiliki akses ke tumpukan teknologi yang serupa, terutama karena mayoritas perangkat lunak modern dibangun di atas perangkat lunak sumber terbuka (*open source*).
- **Peran Model Bisnis:**
  - Keunggulan kompetitif disrupsi lahir dari model bisnis baru yang inovatif dalam menyelesaikan permasalahan pelanggan, bukan dari kepemilikan teknologi eksklusif.

#### C. Studi Kasus Industri: Menang, Kalah, dan Beradaptasi
- **Uber vs Industri Taksi Konvensional:**
  - Komponen teknologi yang digunakan Uber bukanlah barang baru:
    - *Global Positioning System* (GPS): Sudah lama digunakan pada perangkat navigasi seperti Garmin atau TomTom.
    - Pembayaran elektronik (*electronic payments*): Telah eksis selama beberapa dekade.
    - Ponsel pintar (*smartphones*): Perangkat yang sudah umum dimiliki oleh masyarakat luas.
  - Inovasi sejati Uber adalah menggabungkan ketiga teknologi tersebut ke dalam model bisnis baru: memanggil pengemudi terdekat via aplikasi, melacak posisi penjemputan secara waktu nyata, dan melakukan pembayaran otomatis tanpa uang tunai.
  - Respons industri taksi yang melobi parlemen untuk membatasi operasional Uber terbukti tidak efektif, karena yang dibutuhkan publik adalah adaptasi model layanan, bukan regulasi proteksionis.
- **Kamera Saku vs Kamera Ponsel Pintar:**
  - Industri kamera saku (*point-and-shoot*) terdisrupsi total ketika teknologi kamera pada ponsel pintar mencapai kualitas tinggi.
  - Prinsip utamanya adalah kamera terbaik merupakan kamera yang selalu tersedia di dalam saku setiap saat.
- **Blockbuster vs Netflix:**
  - Blockbuster memandang diri mereka berada dalam bisnis persewaan kaset video (*video rental business*), mengandalkan pendapatan dari denda keterlambatan pengembalian (*late fees*).
  - Netflix memahami bahwa mereka sejatinya berada dalam bisnis industri hiburan (*entertainment business*).
  - Netflix bertransformasi secara bertahap:
    - Pengiriman DVD lewat pos tanpa beban denda keterlambatan.
    - Berpindah ke layanan penyiaran digital (*streaming*) ketika jaringan pita lebar (*broadband internet*) meluas ke rumah tangga.
    - Memproduksi konten film dan serial orisinal.
  - Blockbuster mengalami kebangkrutan karena terpaku pada model bisnis fisik lama.
- **Kemampuan Garmin Melakukan Pivot:**
  - Ketika ponsel pintar mengambil alih fungsi navigasi GPS pada mobil, Garmin menyadari bahwa bisnis inti mereka bukan peta (*mapping*), melainkan pelacakan lokasi (*tracking*).
  - Garmin beralih memproduksi jam tangan pintar dan perangkat pelacak kebugaran (*wearable fitness trackers*), sehingga mampu bertahan dan berkembang.

---

### 3. DevOps Adoption in Modern Enterprises

#### A. Pola Pikir Eksperimentasi dan Reduksi Risiko
- **Proses Melepas Kebiasaan Lama (*Unlearning*):**
  - Menerapkan *DevOps* menuntut organisasi untuk menanggalkan budaya kerja konvensional yang kaku (*unlearn what you have learned*).
  - Perusahaan rintisan (*startup*) memiliki keuntungan karena memulai langsung dengan budaya lincah (*agile*), sedangkan perusahaan besar (*enterprises*) harus berjuang keras membongkar birokrasi yang mengakar.
- **Membatasi Dampak Kerusakan (*Blast Radius*):**
  - Mengembangkan arsitektur yang memungkinkan tim menerapkan perubahan kecil, menguji secara cepat (*fail fast*), dan melakukan pemulihan seketika (*rollback quickly*).
  - Jika terjadi kesalahan pada kode baru di lingkungan produksi, dampaknya terisolasi pada area terbatas tanpa meruntuhkan stabilitas seluruh sistem.
- **Pengujian Langsung di Pasar (*Testing in Market*):**
  - Menghindari perdebatan spekulatif internal yang memakan waktu berbulan-bulan dengan cara menjalankan pengujian langsung ke pengguna (*A/B testing*).
  - Fitur baru hanya disajikan kepada sebagian kecil pengguna (*subset of customers*) untuk mengamati respons dan metrik performa secara objektif sebelum diluncurkan ke seluruh pasar.
- **Modularitas Komponen (Studi Kasus Spotify):**
  - Spotify tidak dirancang sebagai satu kesatuan aplikasi monolitik raksasa (*monolith*), melainkan kumpulan layanan mikro (*microservices*).
  - Tim mesin rekomendasi (*recommendation engine*) dapat memperbarui dan merilis algoritma baru tanpa memengaruhi modul pemutar musik inti. Jika algoritma tersebut bermasalah, pengguna tetap dapat mendengarkan musik dengan normal.

#### B. Tonggak Sejarah Adopsi: Dari Startup ke Unicorn
- **Presentasi Bersejarah di Velocity Conference (2009):**
  - John Allspaw dan Paul Hammond menyampaikan presentasi bertajuk *"10+ Deploys per Day: Dev and Ops Cooperation at Flickr"*.
  - Gagasan rilis sepuluh kali atau lebih dalam sehari mengejutkan industri, di mana rata-rata perusahaan saat itu hanya mampu melakukan rilis sekali setiap enam bulan.
  - Flickr membuktikan bahwa dalam sepekan di bulan Desember 2008, 18 personel berhasil melakukan 67 kali *deployment* yang mencakup 496 perubahan individual tanpa insiden besar.
  - Kunci keberhasilan Flickr terletak pada desain aplikasi yang modular dan kerja sama erat antara *Dev* dan *Ops*, bukan merilis ulang seluruh sistem aplikasi monolitik secara sekaligus.
- **Keberhasilan Etsy (2011):**
  - Pada Januari 2011, Etsy mencatatkan 517 kali rilis produksi dalam satu bulan dengan volume lalu lintas melampaui satu miliar tayangan halaman (*page views*).
  - Kode dikontribusikan oleh 76 individu berbeda dan dirilis rata-rata setiap 25 menit.
  - Estimasi matematis frekuensi penerapan kode di Etsy dapat dihitung sebagai berikut:

$$\text{Frekuensi Rilis} = \frac{31 \text{ hari} \times 24 \text{ jam} \times 60 \text{ menit}}{517 \text{ rilis}} \approx 86{,}3 \text{ menit per rilis}$$

  - Dengan pola kerja jam kantor aktif, frekuensi riil rilis berada pada kisaran satu kali setiap 25 menit.
  - Chad Dickerson (CTO Etsy) menegaskan bahwa lingkungan rilis berkala ini ditopang oleh empat fondasi utama: rasa percaya (*trust*), keterbukaan (*transparency*), komunikasi aktif (*communication*), dan kedisiplinan kerja (*discipline*).

#### C. Keberhasilan DevOps pada Skala Enterprise
- **DevOps Enterprise Summit (2016):**
  - Diprakarsai oleh Gene Kim dari IT Revolution, menghadirkan 1.300 praktisi korporat global.
  - Mematahkan anggapan bahwa *DevOps* hanya berlaku bagi perusahaan teknologi murni (*unicorns*) dan membuktikan keberhasilannya pada industri perbankan, ritel, dan asuransi berakar tradisional.
- **Pencapaian Korporasi Global:**
  - **Ticketmaster:** Berhasil memangkas waktu rata-rata pemulihan sistem saat insiden (*mean time to recovery* / MTTR) sebesar 98%:

$$\Delta \text{MTTR}_{\text{Ticketmaster}} = -98\%$$

  - **Nordstrom:** Mempersingkat durasi tunggu siklus pengiriman perangkat lunak (*lead time*) sebesar 20%.
  - **Target:** Mempercepat proses rilis tumpukan penuh (*full-stack deployment*) dari 3 bulan menjadi hitungan menit melalui otomatisasi serta pemangkasan birokrasi *Change Review Board* (CRB).
  - **USAA:** Menekan siklus rilis layanan asuransi dari 28 hari menjadi 7 hari.
  - **CSG:** Menurunkan volume insiden per rilis secara drastis dari 200 insiden menjadi 18 insiden.
  - **ING:** Mengembangkan dan mengoperasikan *DevOps* secara serentak pada lebih dari 500 tim aplikasi perbankan.

---

### 4. Definition and Core Concepts of DevOps

#### A. Asal-Usul Istilah dan Makna Fundamental
- **Pencetusan Istilah (2009):**
  - Patrick Debois mencetuskan frasa *"development operations"* yang kemudian disingkat menjadi *DevOps*.
  - Ia mendefinisikannya sebagai perluasan dari lingkungan pengembangan *Agile* yang berorientasi pada penyempurnaan proses penghantaran perangkat lunak secara menyeluruh (*Agile for Ops*).
- **Definisi Formal:**
  - *DevOps* adalah praktik kolaborasi erat antara teknisi pengembang (*development*) dan tim operasional (*operations*) di sepanjang siklus hidup pengembangan perangkat lunak secara utuh, dengan menerapkan prinsip-prinsip *Lean* dan *Agile* guna menghantarkan sistem secara cepat, terukur, dan berkesinambungan.

#### B. Prasyarat Teknis Pendukung DevOps
- **Budaya Kolaborasi Terbuka:**
  - Menghilangkan sekat antarruang kerja (*silos*) guna menciptakan lingkungan yang menjunjung tinggi transparansi, rasa saling menghormati, dan kepemilikan bersama.
- **Arsitektur Modular (*Loosely Coupled Architecture*):**
  - Menerapkan arsitektur layanan mikro (*microservices*) agar pembaruan suatu fungsi tidak menuntut perilisan ulang seluruh infrastruktur sistem.
- **Otomatisasi Penuh (*End-to-End Automation*):**
  - Mengotomatiskan rangkaian pengujian, integrasi, dan penerapan kode. Ketika aplikasi dipecah menjadi puluhan hingga ratusan modul kecil, deployment manual menjadi mustahil dilakukan manusia secara konsisten.
- **Platform Dinamis Berbasis Kode (*Programmable Platform*):**
  - Menyediakan infrastruktur yang dapat diprogram secara dinamis (*software-defined platform* atau *cloud infrastructure*). Pengembang dapat menginisiasi lingkungan kerja baru secara mandiri dalam hitungan menit tanpa harus menunggu berpekan-pekan untuk konfigurasi server manual.

#### C. Apa yang Bukan Termasuk DevOps
- **Bukan Sekadar Menggabungkan Dua Tim:**
  - *DevOps* bukan sekadar mendudukkan personel *Dev* dan *Ops* dalam satu ruangan tanpa mengubah cara kerja dan paradigma mereka.
- **Bukan Membentuk Tim Terpisah Bernama "Tim DevOps":**
  - Sama halnya dengan filosofi *Agile* di mana perusahaan tidak membuat "tim Agile" khusus, organisasi tidak boleh mengisolasi fungsi *DevOps* ke dalam tim silo baru. Seluruh organisasi harus bertransformasi menjadi entitas *DevOps*.
- **Bukan Produk Perangkat Lunak:**
  - *DevOps* tidak dapat dibeli dalam bentuk paket instalasi perangkat lunak (*cannot buy DevOps in a box*). Perkakas hanya memperkuat budaya yang telah terbentuk.
- **Bukan Pendekatan Tunggal untuk Semua Kasus (*No One-Size-Fits-All*):**
  - Strategi implementasi bergantung pada karakteristik luaran bisnis: apakah berupa perangkat lunak paket terpasang (*shrink-wrap software*), *Software as a Service* (SaaS), aplikasi terunduh, atau layanan fisik yang didukung perangkat lunak.
- **Bukan Sekadar Otomatisasi Pekerjaan Operasional (*Ops Automation*):**
  - Menugaskan seorang teknisi untuk menulis skrip otomasi konfigurasi server sementara alur kerja pengembang tetap terisolasi bukanlah esensi *DevOps*. *DevOps* adalah satu kesatuan tim dengan satu tolok ukur kesuksesan bersama.

---

### 5. Essential Characteristics and Agility Pillars

#### A. Tiga Pilar Agilitas (The Perfect Storm)
Tujuan utama organisasi perangkat lunak modern adalah mencapai agilitas (*agility*): bergerak cepat di pasar dengan kecepatan maksimum (*maximum velocity*) dan risiko seminimal mungkin (*minimum risk*) guna memperoleh wawasan bernilai secara konsisten. Agilitas ini ditopang oleh sinergi tiga pilar:

- **1. DevOps:**
  - Menyediakan transformasi budaya kolaboratif, pipa rilis otomatis (*automated delivery pipelines*), pengelolaan infrastruktur berbasis kode (*Infrastructure as Code* / IaC), dan infrastruktur kekal (*immutable infrastructure*).
- **2. Microservices:**
  - Desain aplikasi terdistribusi yang terikat secara longgar (*loosely coupled*), berkomunikasi menggunakan antarmuka REST API terstandarisasi, dirancang tahan kegagalan, dan diuji secara agresif melalui prinsip *fail fast*.
- **3. Containers:**
  - Menyediakan lingkungan eksekusi yang ramah pengembang (*developer-centric*), portabel, berbobot ringan, serta memiliki waktu inisiasi instan (*fast startup*).
  - Lingkungan *container* bersifat fana (*ephemeral*): jika sebuah *container* mengalami anomali atau kerusakan di lingkungan produksi, teknisi tidak memperbaikinya di tempat melainkan langsung menghancurkan wadah tersebut dan menggantinya dengan wadah baru yang bersih (*throw-away runtimes*).

#### B. Evolusi Arsitektur Perangkat Lunak dan Infrastruktur
Perkembangan metodologi rekayasa perangkat lunak bergerak secara bertahap seiring evolusi komputasi:
- **Era Waterfall:**
  - Karakteristik Aplikasi: Sistem monolitik raksasa (*monoliths*).
  - Lingkungan Infrastruktur: Server fisik tunggal (*bare metal physical servers*).
  - Pola Rilis: Siklus rilis panjang dengan jeda berbulan-bulan hingga tahunan.
- **Era Agile:**
  - Karakteristik Aplikasi: Arsitektur berorientasi layanan (*Service Oriented Architecture* / SOA).
  - Lingkungan Infrastruktur: Mesin virtual (*Virtual Machines* / VMs) dan komputasi awan tahap awal.
  - Pola Rilis: Siklus iterasi bertahap dalam hitungan pekan (*sprints*).
- **Era DevOps:**
  - Karakteristik Aplikasi: Layanan mikro terdistribusi (*microservices*).
  - Lingkungan Infrastruktur: Wadah kontainer kekal (*immutable containers*) yang dikelola melalui platform orkestrasi awan (*cloud-native*).
  - Pola Rilis: Pengiriman berkesinambungan (*continuous delivery*) dalam hitungan jam atau menit.

#### C. Tiga Dimensi DevOps
Implementasi *DevOps* yang seimbang mencakup tiga pilar dimensi:
- **1. Dimensi Budaya (*Culture*):**
  - Merupakan faktor penentu kesuksesan nomor satu (riset Atlassian). Tanpa rasa saling percaya, transparansi, dan tanggung jawab bersama, adopsi metodologi dan alat bantu tidak akan membuahkan hasil.
- **2. Dimensi Metode (*Method*):**
  - Menerapkan kerangka kerja terstruktur seperti alur kerja *small batches*, integrasi terus-menerus, dan umpan balik berkala.
- **3. Dimensi Alat (*Tools*):**
  - Rangkaian teknologi pendukung otomatisasi seperti *pipeline* CI/CD, repositori kode berbasis Git, alat pengujian otomatis, dan platform kontainerisasi. Perkakas berfungsi mempercepat jalannya metode dan budaya.

---

### 6. Leading Up to DevOps: The Waterfall Pitfalls

#### A. Alur Kerja Siklus Waterfall Tradisional
Model *Waterfall* memperlakukan rekayasa perangkat lunak serupa dengan proyek konstruksi teknik sipil:
- **1. Fase Pengumpulan Kebutuhan (*Requirements Gathering*):**
  - Tim analis menyusun dokumen spesifikasi kebutuhan sistem secara ekstensif selama berbulan-bulan hingga dokumen ditandatangani.
- **2. Fase Perancangan Sistem (*System Design*):**
  - Arsitek perangkat lunak menyusun dokumen desain teknis bertingkat (*high-level design*, *low-level design*, dan *system-level design*).
- **3. Fase Penulisan Kode (*Development/Coding*):**
  - Pengembang mengimplementasikan kode secara terisolasi tanpa integrasi dengan modul tim lain berdasarkan dokumen desain yang telah disahkan.
- **4. Fase Integrasi (*Integration*):**
  - Seluruh modul yang dibuat terpisah digabungkan untuk pertama kalinya. Pada fase ini, berbagai kegagalan antarmuka dan ketidakcocokan logika mulai bermunculan.
- **5. Fase Pengujian Mutu (*Testing/QA*):**
  - Tim penguji menjalankan pengujian menyeluruh terhadap sistem gabungan dan mencatat cacat sistem (*severity 1 and 2 defects*) untuk dikembalikan ke pengembang.
- **6. Fase Penerapan ke Operasional (*Deployment/Operations*):**
  - Kode yang telah lolos uji diserahkan kepada tim operasional untuk dipasang pada server produksi, sering kali berjarak 6 hingga 24 bulan sejak proyek pertama kali dimulai.

#### B. Kelemahan Kritis Metodologi Waterfall
- **Ketiadaan Ruang Perubahan (*No Provision for Change*):**
  - Setiap fase memiliki kriteria masuk (*entrance criteria*) dan keluar (*exit criteria*) yang kaku. Ketika satu fase selesai, pintu ditutup rapat dan proses beralih ke tahap berikutnya tanpa fleksibilitas untuk mengakomodasi perubahan pasar atau kebutuhan klien.
- **Ketiadaan Hasil Antara (*No Intermediate Delivery*):**
  - Tidak ada luaran perangkat lunak fungsional yang dapat dicoba oleh pengguna sebelum fase akhir tercapai. Risiko proyek menjadi sangat tinggi karena kegagalan nilai baru terdeteksi di ujung siklus.
- **Biaya Pemulihan Cacat Sangat Mahal:**
  - Jika terjadi cacat arsitektur mendasar yang baru disadari saat pengujian integrasi, tim harus "berenang melawan arus air terjun": mencari kembali arsitek awal yang mungkin telah ditugaskan ke proyek lain, merevisi dokumen desain, menulis ulang kode, dan mengulang pengujian dari awal.
- **Waktu Siklus Sangat Panjang (*Long Lead Times*):**
  - Jeda rilis yang memakan waktu tahunan menyebabkan perangkat lunak yang diluncurkan kerap sudah usang dan kehilangan relevansi pasar.

#### C. Terbentuknya Silo Fungsional Antara Dev dan Ops
- **Silo dan Keterasingan Tanggung Jawab:**
  - Tim perancang tidak memahami kesulitan pengembang; pengembang tidak memahami tantangan tim penguji; dan semua pihak terisolasi dari realitas pemeliharaan sistem.
- **Beban Tim Operasional di Ujung Alur:**
  - Tim operasional adalah pihak yang posisinya paling jauh dari kode sumber (*furthest away from code*), namun dituntut untuk menjaga stabilitas dan ketersediaan aplikasi di lingkungan produksi selama 24 jam penuh.
  - Akibatnya, tim operasional memandang rilis kode baru dari pengembang sebagai ancaman utama terhadap stabilitas sistem (*conflict of interest*).

---

### 7. XP, Agile, and the Emergence of Two-Speed IT

#### A. Extreme Programming (XP) dan Siklus Umpan Balik Cepat
- **Inisiasi oleh Kent Beck (1996):**
  - Kent Beck memperkenalkan *Extreme Programming* (XP) sebagai fondasi awal metodologi tangkas, dengan fokus pada siklus umpan balik yang semakin merapat (*tight feedback loops*):
    - Rencana rilis (*release plans*): Divalidasi dalam hitungan bulan.
    - Rencana iterasi (*iteration plans*): Divalidasi dalam hitungan pekan.
    - Rencana penerimaan (*acceptance plans*): Divalidasi dalam hitungan hari.
    - Pertemuan koordinasi (*stand-up meetings*): Dijalankan setiap hari.
    - Negosiasi pasangan pemrograman (*pair negotiations*): Dilakukan setiap jam.
    - Pengujian unit (*unit testing*): Dijalankan dalam hitungan menit.
    - Penulisan kode (*programming*): Divalidasi dalam hitungan detik.
- **Praktik Pemrograman Berpasangan (*Pair Programming*):**
  - Menempatkan dua pemrogram pada satu lingkungan penulisan kode yang sama.
  - Memberikan dua pasang mata untuk setiap baris kode guna meminimalkan kesalahan (*bugs*).
  - Menjadi sarana transfer pengetahuan lintas anggota tim (*cross-training*), seperti saat pengembang senior membimbing pengembang junior dalam memahami arsitektur dan pola penyelesaian masalah secara langsung.

#### B. Kelahiran Agile Manifesto
- **Deklarasi Snowbird (2001):**
  - Tujuh belas praktisi rekayasa perangkat lunak berkumpul di Snowbird, Utah, untuk merumuskan alternatif metode pengembangan ringan (*lightweight methods*), yang melahirkan *Agile Manifesto*.
- **Empat Nilai Pokok Agile:**
  - **1. Individu dan interaksi** lebih dihargai daripada proses dan alat bantu (*individuals and interactions over processes and tools*).
  - **2. Perangkat lunak yang berfungsi** lebih dihargai daripada dokumentasi yang komprehensif (*working software over comprehensive documentation*).
  - **3. Kolaborasi dengan pelanggan** lebih dihargai daripada negosiasi kontrak (*customer collaboration over contract negotiation*).
  - **4. Tanggap terhadap perubahan** lebih dihargai daripada sekadar mematuhi rencana (*responding to change over following a plan*).
- **Karakteristik Operasional:**
  - Pembagian beban kerja ke dalam siklus berulang pendek yang disebut *sprints* (biasanya berdurasi 2 pekan).
  - Perencanaan adaptif (*adaptive planning*), penghantaran bertahap di awal (*early delivery*), dan perbaikan berkelanjutan (*continuous improvement*).

#### C. Keterbatasan Agile Tanpa Ops: Fenomena Two-Speed IT dan Shadow IT
- **Friksi Antara Dev dan Ops di Bawah Agile:**
  - Metodologi *Agile* berhasil mempercepat kinerja tim pengembang (*Dev*), namun mengabaikan tim operasional (*Ops*).
  - Pengembang mampu memproduksi kode siap uji setiap dua pekan, namun penggelaran kode tersebut ke lingkungan produksi tetap tertahan oleh prosedur birokrasi operasional yang diukur berdasarkan stabilitas dan minimnya perubahan.
- **Kisah Nyata Hambatan Tiket Layanan:**
  - Dalam sebuah proyek, tim pengembang menyelesaikan kode pada akhir Februari dan meminta penyediaan tiga mesin virtual (*virtual machines* / VMs) kepada tim operasional.
  - Meskipun pembuatan VM secara teknis hanya memerlukan waktu 20 menit, tiket permohonan tertahan selama berminggu-minggu hanya untuk menemukan teknisi yang memiliki alokasi waktu luang 20 menit tersebut. Akibatnya, kode baru berhasil diterapkan pada bulan September.
- **Munculnya Two-Speed IT:**
  - Kecepatan Lambat (*Slow Speed*): Jalur internal resmi perusahaan melalui sistem antrean tiket operasional (*service ticket queue*) yang membutuhkan waktu tunggu berhari-hari hingga berminggu-minggu.
  - Kecepatan Cepat (*Fast Speed*): Pengembang mengabaikan antrean internal dan langsung menyewa infrastruktur komputasi awan publik menggunakan kartu kredit secara mandiri dalam hitungan menit.
- **Bahaya Shadow IT:**
  - Penggunaan layanan komputasi awan di luar kendali dan pengawasan departemen TI resmi (*Shadow IT*) menciptakan kerentanan keamanan, risiko tata kelola data, dan biaya liar yang tidak terpantau oleh manajemen.
  - Gerakan *DevOps* lahir sebagai solusi menyeluruh untuk menyelaraskan kedua kecepatan ini dengan menjadikan tim operasional sama tangkasnya dengan pengembang.

---

### 8. Historical Milestones and Influential Pioneers of DevOps

#### A. Garis Waktu Perkembangan Gerakan DevOps (2007 - 2016)
- **2007: Identifikasi Masalah oleh Patrick Debois**
  - Patrick Debois menyadari frustrasi akibat benturan cara kerja antara *Dev* dan *Ops* saat terlibat dalam proyek migrasi pusat data, memicu pencarian metode kerja sama yang lebih efektif.
- **2008: Pertemuan Birds of a Feather (BoF) di Konferensi Agile**
  - Andrew Clay Shafer menginisiasi sesi diskusi bebas (*Birds of a Feather*) mengenai *Agile Infrastructure* di Toronto.
  - Meskipun awalnya sesi tersebut sepi peminat, Patrick Debois mendatangi Shafer secara langsung untuk mendiskusikan gagasan memperluas prinsip *Agile* ke ranah operasional dan infrastruktur.
- **2009: Presentasi Terobosan Flickr di Velocity Conference**
  - John Allspaw dan Paul Hammond mendemonstrasikan bahwa kerja sama erat antara *Dev* dan *Ops* memungkinkan pelaksanaan sepuluh kali deployment dalam satu hari secara stabil.
- **Oktober 2009: Konferensi DevOpsDays Pertama di Ghent, Belgia**
  - Patrick Debois menyelenggarakan pertemuan independen pertama bagi para praktisi pengembang dan operasional.
  - Tagar media sosial `#DevOpsDays` dan istilah *DevOps* mulai digunakan secara global serta melahirkan rangkaian konferensi komunitas tahunan di berbagai negara.
- **2010: Publikasi Buku Continuous Delivery**
  - Jez Humble dan David Farley menerbitkan buku *Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation*.
  - Menetapkan fondasi teknis mengenai otomasi jalur rilis perangkat lunak secara cepat dan berisiko rendah.
- **2013: Publikasi Buku The Phoenix Project**
  - Gene Kim, Kevin Behr, dan George Spafford menulis novel manajemen TI *The Phoenix Project*, yang mengadaptasi prinsip-prinsip *Lean manufacturing* dari buku legendaris *The Goal* karya Eliyahu M. Goldratt ke dalam konteks penyelamatan divisi teknologi informasi korporat.
- **2015: Pendirian Lembaga Riset DORA**
  - Dr. Nicole Forsgren bersama Gene Kim dan Jez Humble mendirikan *DevOps Research and Assessment* (DORA).
  - Melakukan penelitian empiris skala besar yang membuktikan secara ilmiah hubungan antara kemampuan pengiriman perangkat lunak dengan performa finansial dan keunggulan kompetitif organisasi.
- **2016: Publikasi Buku The DevOps Handbook**
  - Ditulis oleh Gene Kim, Jez Humble, Patrick Debois, dan John Willis sebagai panduan implementasi praktis langkah demi langkah untuk menerapkan prinsip-prinsip *DevOps* di lingkungan korporasi.

#### B. Tokoh-Tokoh Pelopor Gerakan DevOps
- **Patrick Debois:** Dijuluki sebagai bapak *DevOps* (*The Father of DevOps*), pemrakarsa istilah *DevOps*, dan pendiri konferensi *DevOpsDays*.
- **Andrew Clay Shafer:** Pelopor konsep *Agile Infrastructure* yang bersama Debois meletakkan batu pertama pergerakan.
- **John Allspaw:** Mantan VP of Technical Operations di Flickr dan CTO Etsy, membuktikan kelayakan implementasi rilis frekuensi tinggi melalui kolaborasi *Dev* dan *Ops*.
- **Jez Humble:** Penulis rujukan utama *Continuous Delivery* dan periset senior yang merumuskan arsitektur pipa rilis modern.
- **Gene Kim:** Peneliti, pendiri IT Revolution, serta penulis buku *The Phoenix Project* dan *The DevOps Handbook*.
- **John Willis:** Koordinator awal *DevOpsDays*, praktisi di Docker dan Chef, serta salah satu penulis *The DevOps Handbook*.
- **Bridget Kromhout:** Pengelola global konferensi *DevOpsDays* (2015 - 2020) dan ko-pembawa acara pada siniar (*podcast*) teknologi ternama *Arrested DevOps*.
- **Dr. Nicole Forsgren:** Peneliti utama dan pakar statistik yang memimpin riset DORA serta membuktikan dampak ekonomi nyata dari transformasi *DevOps*.

#### C. Karakteristik Komunitas: Dari Praktisi untuk Praktisi
- **Gerakan Akar Rumput (*Grassroots Movement*):**
  - Mengutip pernyataan Damon Edwards (ko-pembawa acara *DevOps Cafe* bersama John Willis), *DevOps* lahir dari praktisi untuk praktisi (*from practitioners, by practitioners*).
  - Gerakan ini tidak berawal dari standardisasi lembaga formal, spesifikasi vendor berbayar, atau produk komersial, melainkan gerakan terdesentralisasi yang terbuka bagi siapa saja yang ingin menghilangkan hambatan dalam rekayasa perangkat lunak.

---

### 9. Key Takeaways and Summary

#### A. Poin-Poin Strategis Modul 01
- **Teknologi adalah Pemungkin:**
  - Nilai inovasi ditentukan oleh model bisnis yang tepat dalam memanfaatkan teknologi, bukan semata kepemilikan alat canggih.
- **Budaya adalah Pondasi Nomor Satu:**
  - Dari tiga dimensi *DevOps* (budaya, metode, dan alat), budaya kerja kolaboratif, transparansi, dan rasa percaya antartim memegang peranan paling penting terhadap kesuksesan jangka panjang.
- **Agilitas Memerlukan Sinergi Tiga Pilar:**
  - Kolaborasi *DevOps*, modularitas *microservices*, dan sifat fana *containers* membentuk kombinasi ideal untuk merilis perubahan kecil secara cepat dengan risiko minimal.
- **Melampaui Jebakan Waterfall dan Two-Speed IT:**
  - Menghilangkan proses serah terima kerja yang kaku dan menghapus friksi silo antardepartemen guna mencegah pembengkakan biaya serta kemunculan *Shadow IT*.
- **Karakteristik Rilis Modern:**
  - Melakukan rilis dalam potongan kecil (*small batches*), menguji langsung ke pasar (*A/B testing*), mengisolasi dampak kesalahan (*limiting blast radius*), dan memprioritaskan pemulihan yang cepat (*mean time to recovery* / MTTR).