# Overview of Software Engineering and the SDLC

Rekayasa perangkat lunak (*software engineering*) merupakan penerapan prinsip-prinsip ilmiah, matematis, dan keteknikan dalam merancang, membangun, menguji, serta memelihara sistem perangkat lunak berkualitas tinggi secara sistematis. Berbeda dari pemrograman ad-hoc sederhana, disiplin ini lahir sebagai respons terhadap krisis perangkat lunak (*software crisis*) historis guna memenuhi kebutuhan komputasi skala besar yang terus berkembang. Dokumen ini menyajikan tinjauan mendalam mengenai evolusi rekayasa perangkat lunak, perbandingan peran insinyur (*software engineer*) versus pengembang (*software developer*), siklus hidup pengembangan perangkat lunak (*Software Development Life Cycle / SDLC*), enam pilar proses pembangun kualitas, tahapan perilisan produk, hingga metodologi rekayasa kebutuhan perangkat lunak (*requirements engineering*).

## 1. What Is Software Engineering?

Rekayasa perangkat lunak didefinisikan sebagai penerapan pendekatan sistematis, disiplin, dan terukur terhadap pengembangan, pengoperasian, dan pemeliharaan perangkat lunak. Bidang ini mengumpulkan dan menganalisis kebutuhan bisnis secara ketat untuk menghasilkan aplikasi yang andal, aman, dan efisien.

### A. Evolusi Historis dan Krisis Perangkat Lunak (The Software Crisis)
Perkembangan disiplin ini melalui beberapa fase transformasi kritis:
- **Awal Komputasi (Akhir 1950-an hingga 1960-an)**: Pembuatan perangkat lunak pada masa awal dilakukan tanpa metodologi formal (*ad hoc programming*). Perangkat lunak dipandang sebagai pelengkap perangkat keras semata, tanpa standarisasi proses pengujian atau dokumentasi arsitektur.
- **Krisis Perangkat Lunak (Pertengahan 1960-an hingga Pertengahan 1980-an)**:
  - Lonjakan adopsi komputer oleh industri memicu permintaan masif terhadap sistem komputasi yang kompleks.
  - Ketiadaan proses formal melahirkan fenomena *software crisis*: proyek perangkat lunak kerap kali melampaui anggaran biaya (*over budget*), terlambat dari tenggat waktu (*behind schedule*), serta menghasilkan kode program yang penuh kesalahan (*buggy*) dan sulit dikelola (*unmanageable*).
  - Banyak arsitektur perangkat lunak yang dirancang untuk skala kecil mengalami kegagalan total saat diterapkan pada skala besar (*failed to scale*).
  - Terjadi keusangan dini: teknologi baru berkembang sangat cepat sehingga perangkat lunak lama sering kali sudah tertinggal bahkan sebelum proses pengembangannya rampung, memaksa tim melakukan perombakan menyeluruh (*complete redesign*).
- **Modernisasi dan Rekayasa Berbantuan Komputer (Pertengahan 1980-an hingga Sekarang)**:
  - Krisis tersebut diatasi dengan mengadopsi metodologi baku, kerangka kerja terstandarisasi, serta penerapan alat rekayasa perangkat lunak berbantuan komputer (*Computer-Aided Software Engineering / CASE*).

### B. Enam Kategori Alat CASE (Computer-Aided Software Engineering)
Alat CASE membantu tim otomatisasi dan standarisasi proses rekayasa:
- **Analisis dan Pemodelan Bisnis (*Business Analysis and Modeling*)**: Perangkat lunak untuk memetakan proses bisnis, diagram alir data (*Data Flow Diagrams*), dan pemodelan arsitektur sistem.
- **Alat Pengembangan (*Development Tools*)**: Lingkungan pengembangan terpadu (*Integrated Development Environments / IDE*), editor kode, kompiler, dan lingkungan penelusuran kesalahan (*debugging environments*).
- **Alat Verifikasi dan Validasi (*Verification and Validation Tools*)**: Kerangka kerja pengujian kode otomatis, alat analisis statis (*static code analyzers*), dan pemeriksa kepatuhan sintaks (*linters*).
- **Manajemen Konfigurasi (*Configuration Management*)**: Sistem kendali versi (*version control systems* seperti Git) dan alat manajemen rilis (*release management*).
- **Metrik dan Pengukuran (*Metrics and Measurement*)**: Alat pelacak kompleksitas kode, cakupan pengujian (*code coverage*), serta indikator kinerja sistem.
- **Manajemen Proyek (*Project Management*)**: Sistem pelacak isu, papan visual Kanban, pelacak tonggak pencapaian, dan alokasi sumber daya.

### C. Perbandingan Peran: Software Engineer vs Software Developer
Meskipun kedua istilah ini sering digunakan secara bergantian di industri, terdapat perbedaan mendasar pada cakupan perspektif dan tanggung jawab:
- **Cakupan dan Pendekatan Berpikir**:
  - *Software Engineer*: Mengambil pendekatan holistik gambaran besar (*big-picture, systematic approach*). Fokus pada struktur arsitektur jangka panjang, integritas sistem menyeluruh, skalabilitas, dan keandalan lintas platform.
  - *Software Developer*: Mengambil pendekatan yang lebih terfokus pada implementasi fungsionalitas tertentu (*creative, component-specific approach*). Fokus pada penulisan kode fungsional untuk menyelesaikan modul atau fitur spesifik.
- **Spesialisasi dan Tanggung Jawab Operasional**:
  - *Software Engineer*: Bertanggung jawab merancang arsitektur data, menetapkan batasan antarmuka, mengawal kepatuhan keamanan, serta berkonsultasi intensif dengan berbagai pemangku kepentingan (klien, vendor pihak ketiga, pakar keamanan jaringan, dan tim operasi).
  - *Software Developer*: Menerima spesifikasi kebutuhan teknis dan menerjemahkannya ke dalam baris kode program, unit pengujian, dan logika algoritma.
- **Perspektif Etika dan Regulasi Profesional**:
  - Di beberapa yurisdiksi hukum (seperti di Kanada), sebutan insinyur (*engineer*) dilindungi secara hukum dan menuntut pendidikan etika profesi resmi serta standar lisensi ketat yang setara dengan insinyur sipil atau mekanik. Sementara itu, di sebagian besar deskripsi pekerjaan industri teknologi global, kedua istilah sering kali digunakan sebagai padanan posisi yang serupa.

---

## 2. Insiders' Viewpoint: Keragaman Peran dalam Rekayasa Perangkat Lunak

Rekayasa perangkat lunak adalah bidang yang sangat luas dan mencakup spektrum disiplin kerja yang saling terhubung. Praktisi industri memandang rekayasa perangkat lunak sebagai proses kreatif ujung-ke-ujung (*end-to-end creative engineering*) yang mengawal produk sejak pencetusan ide hingga pensiun sistem.

### A. Tipologi Spesialisasi Rekayasa Perangkat Lunak
Di dalam ekosistem industri modern, peran rekayasa terbagi ke dalam berbagai bidang fokus:
- **Rekayasa Bagian Depan (*Front-End Engineering*)**: Berfokus pada antarmuka pengguna (*User Interface / UI*), pengalaman interaksi pengguna (*User Experience / UX*), dan integrasi peramban web atau aplikasi klien.
- **Rekayasa Bagian Belakang (*Back-End Engineering*)**: Bertanggung jawab atas logika bisnis inti di sisi peladen (*server-side*), arsitektur basis data, pemrosesan transaksi, dan desain antarmuka pemrograman aplikasi (*API*).
- **Rekayasa Tumpukan Penuh (*Full-Stack Engineering*)**: Menguasai integrasi vertikal menyeluruh dari lapisan antarmuka pengguna hingga lapisan basis data dan infrastruktur peladen.
- **Rekayasa Keamanan (*Security Engineering*)**: Memastikan seluruh lapisan arsitektur kebal terhadap kerentanan, merancang enkripsi data, dan mengawal kepatuhan privasi.
- **Rekayasa Perangkat Bergerak (*Mobile Engineering*)**: Mengembangkan aplikasi teroptimasi untuk sistem operasi seluler (Android, iOS).
- **Rekayasa Pengujian dan Kualitas (*Test / QA Engineering*)**: Merancang pengujian otomatis, memvalidasi kinerja beban kerja, dan mengawal standar kualitas perangkat lunak.
- **DevOps dan Rekayasa Keandalan Situs (*DevOps and Site Reliability Engineering*)**: Menjembatani pengembangan dengan operasional peladen, mengelola pipa integrasi berkelanjutan (*CI/CD*), otomatisasi infrastruktur, dan orkestrasi kontainer.
- **Rekayasa Komputasi Awan (*Cloud Engineering*)**: Merancang arsitektur layanan berbasis awan (*cloud-native*), skalabilitas elastis, dan efisiensi biaya infrastruktur terdistribusi.
- **Rekayasa Data dan Pembelajaran Mesin (*Data and Machine Learning Engineering*)**: Membangun pipa aliran data skala besar (*data pipelines*), melatih model kecerdasan buatan, dan menerapkannya ke lingkungan produksi.

---

## 3. Introduction to the Software Development Life Cycle (SDLC)

Siklus hidup pengembangan perangkat lunak (*Software Development Life Cycle / SDLC*) adalah kerangka kerja proses sistematis yang digunakan oleh organisasi untuk memproduksi perangkat lunak berkualitas tinggi dalam jangka waktu dan anggaran yang terukur serta dapat diprediksi.

### A. Tujuan dan Manfaat Utama Penerapan SDLC
Penerapan SDLC memberikan fondasi disiplin rekayasa yang kokoh bagi organisasi:
- **Peta Jalan Terstandarisasi (*Structured Roadmap*)**: Menggantikan pendekatan pemrograman coba-coba (*ad hoc*) dengan panduan tahapan yang jelas, meningkatkan efisiensi, dan meminimalkan risiko kegagalan proyek.
- **Fase Kerja Diskrit (*Discrete Phases*)**: Setiap tahapan memiliki kriteria masukan (*inputs*), proses, dan luaran terdefinisi (*deliverables*), sehingga setiap anggota tim mengetahui tanggung jawab mereka secara transparan.
- **Komunikasi Terarah antar Pemangku Kepentingan**: Memberikan visibilitas kepada klien, manajemen bisnis, dan tim teknis mengenai posisi kemajuan proyek di setiap waktu.
- **Penyelesaian Masalah Lebih Awal (*Early Problem Solving*)**: Risiko arsitektur dan cacat desain dapat diidentifikasi serta diselesaikan pada fase perencanaan awal, menghindarkan biaya perbaikan yang jauh lebih mahal saat kode sudah ditulis.
- **Dukungan terhadap Iterasi**: Walaupun berakar dari model Waterfall linier pada era 1960-an, SDLC modern dapat diterapkan secara berulang (*iterative*) dan tangkas (*agile*) untuk mengadopsi perubahan kebutuhan pasar secara cepat.

---

## 4. The Six Phases of the SDLC

Secara umum, siklus hidup rekayasa perangkat lunak terdiri dari enam tahapan diskrit yang berurutan atau berulang secara iteratif:

### A. Tahap 1: Perencanaan dan Analisis (Planning)
Tahap inisiasi di mana permasalahan didefinisikan secara komprehensif:
- Mengidentifikasi profil pengguna akhir dan tujuan utama solusi perangkat lunak.
- Menganalisis masukan data (*inputs*), pemrosesan logika, dan luaran yang diharapkan (*outputs*).
- Mengevaluasi kepatuhan hukum, regulasi perlindungan data, dan standar industri.
- Mengestimasi biaya tenaga kerja, kebutuhan infrastruktur, jadwal pengerjaan, serta pembagian peran tim.
- Pembuatan purwarupa awal (*prototyping*) untuk membantu pemangku kepentingan memperjelas kebutuhan bisnis yang masih ambigu.
- Menghasilkan dokumen Spesifikasi Kebutuhan Perangkat Lunak (*Software Requirements Specification / SRS*).

### B. Tahap 2: Perancangan Sistem dan Arsitektur (Design)
Tahap penerjemahan kebutuhan bisnis menjadi struktur teknis yang siap diimplementasikan:
- Merancang arsitektur sistem menyeluruh, batas-batas modul, dan diagram interaksi antar komponen.
- Menetapkan skema basis data, pemodelan entitas (*Entity-Relationship Diagrams*), dan desain antarmuka pemrograman aplikasi (*API*).
- Menentukan antarmuka pengguna (*User Interface / UI*) dan alur navigasi pengguna (*User Experience / UX*).
- Menghasilkan Dokumen Desain Perangkat Lunak (*Software Design Document / SDD*) yang menjadi pedoman teknis bagi pengembang.

### C. Tahap 3: Pengembangan dan Implementasi Kode (Development)
Tahap penulisan baris kode program secara konkret oleh para pengembang:
- Pengembang membedah dokumen desain menjadi tugas-tugas pemrograman (*coding tasks*).
- Memilih dan mengonfigurasi tumpukan teknologi (*software stack*), kerangka kerja (*frameworks*), dan pustaka dependensi yang relevan.
- Menerapkan standar penulisan kode baku, konvensi penamaan, dan pemeriksaan otomatis menggunakan *linters*.

### D. Tahap 4: Pengujian Kualitas (Testing)
Tahap verifikasi dan validasi untuk memastikan perangkat lunak bebas dari cacat dan sesuai dengan spesifikasi SRS:
- Pelaporan, pelacakan, dan perbaikan *bugs* secara berkesinambungan.
- Pengujian dapat dilakukan secara manual, otomatis (*automated testing*), maupun hibrida.
- **Empat Tingkatan Pengujian Standar**:
  - *Unit Testing*: Menguji unit kode terkecil (fungsi, metode, atau kelas) secara terisolasi; umumnya ditulis langsung oleh pengembang.
  - *Integration Testing*: Menguji antarmuka dan interaksi gabungan antara dua atau lebih modul komponen yang saling terhubung.
  - *System Testing*: Menguji keseluruhan sistem yang telah terintegrasi penuh terhadap seluruh persyaratan spesifikasi fungsional dan non-fungsional.
  - *User Acceptance Testing (UAT)*: Pengujian tahap akhir oleh pengguna akhir atau klien untuk memverifikasi apakah perangkat lunak telah memenuhi ekspektasi bisnis nyata sebelum diluncurkan.

### E. Tahap 5: Penerapan ke Lingkungan Produksi (Deployment)
Tahap rilis perangkat lunak agar dapat diakses dan digunakan oleh pengguna sasaran:
- Rilis bertahap: kode terlebih dahulu disebarkan ke lingkungan pementasan (*staging/UAT*); setelah mendapatkan persetujuan klien, kode disebarkan ke lingkungan produksi (*production*).
- Distribusi ke toko aplikasi seluler (*App Stores*), peladen web publik, atau peladen internal jaringan korporat.

### F. Tahap 6: Pemeliharaan dan Evaluasi Berkelanjutan (Maintenance)
Tahap operasional jangka panjang setelah perangkat lunak aktif digunakan:
- Memantau stabilitas sistem dan memperbaiki cacat tersembunyi yang lolos dari fase pengujian.
- Menangani kendala interaksi antarmuka pengguna dan memantau performa di bawah beban nyata.
- Mengumpulkan kebutuhan baru atau perbaikan fitur (*enhancements*) dari pengguna akhir yang kemudian menjadi masukan bagi siklus SDLC berikutnya.

---

## 5. Building Quality Software

Membangun perangkat lunak berkualitas tinggi memerlukan disiplin proses rekayasa yang ketat, standar penulisan kode yang bersih, serta strategi perilisan produk yang terkelola dengan baik.

### A. Enam Proses Inti Rekayasa Perangkat Lunak
Kualitas perangkat lunak dibangun melalui enam proses berkesinambungan:
- **Pengumpulan Kebutuhan (*Requirements Gathering*)**: Mendefinisikan kebutuhan sistem, batasan operasional, dan skenario kasus penggunaan (*use cases*).
- **Perancangan Sistem (*System Design*)**: Mentransformasikan kebutuhan abstrak ke dalam representasi modular yang memuat aturan bisnis, arsitektur data, dan antarmuka komunikasi.
- **Penulisan Kode Berkualitas (*Coding for Quality*)**: Membangun kode yang mudah dipelihara (*maintainability*), mudah dibaca (*readability*), mudah diuji (*testability*), dan aman (*security*).
- **Pengujian Perangkat Lunak (*Software Testing*)**: Mengidentifikasi kesenjangan antara spesifikasi yang dijanjikan dengan perilaku sistem aktual.
- **Perilisan Produk (*Software Releases*)**: Mengemas dan mendistribusikan versi sistem yang stabil kepada audiens yang tepat.
- **Dokumentasi Lengkap (*Documenting*)**: Menyediakan panduan referensi menyeluruh bagi pengguna teknis maupun non-teknis.

### B. Tiga Tingkatan Perilisan Produk (Release Stages)
Perangkat lunak didistribusikan secara bertahap untuk meminimalkan risiko kegagalan massal:
- **Rilis Alfa (*Alpha Release*)**: Versi fungsional pertama yang dirilis secara terbatas kepada kelompok pemangku kepentingan internal atau tim pengembang inti. Rilis alfa masih mengandung cacat dan belum memiliki kelengkapan fitur penuh, serta masih memungkinkan terjadinya modifikasi desain mendasar.
- **Rilis Beta (*Beta Release / Limited Release*)**: Versi yang telah memenuhi seluruh kebutuhan fungsional dan didistribusikan kepada kelompok pengguna luar terpilih. Tujuannya adalah menguji perangkat lunak di bawah kondisi lingkungan operasional riil dan mendeteksi cacat tersembunyi.
- **Ketersediaan Umum (*General Availability / GA Release*)**: Versi stabil, teruji, dan matang yang resmi diluncurkan untuk seluruh pengguna publik di lingkungan produksi.

### C. Klasifikasi Dokumentasi Perangkat Lunak
Dokumentasi dibagi berdasarkan profil audiens sasarannya:
- **Dokumentasi Sistem (*System Documentation*)**: Ditujukan untuk pembaca teknis (rekayasawan, pengembang, dan arsitek perangkat lunak). Berisi berkas README, komentar dalam kode (*inline comments*), dokumen arsitektur dan desain (SRS/SDD), informasi verifikasi pengujian, dan panduan pemeliharaan sistem.
- **Dokumentasi Pengguna (*User Documentation*)**: Ditujukan untuk pengguna akhir non-teknis. Berisi panduan pengguna (*user guides*), manual operasional, video tutorial, serta fitur bantuan daring (*online help*).

---

## 6. Requirements Engineering: Foundations and Artifacts

Rekayasa kebutuhan (*requirements engineering*) adalah proses kritis untuk mendefinisikan masalah bisnis yang hendak diselesaikan dan merumuskan spesifikasi solusi secara formal. Kesalahan dalam tahap ini merupakan penyebab utama kegagalan proyek perangkat lunak.

### A. Enam Langkah Pengumpulan Kebutuhan (Requirement Gathering Steps)
Proses pengumpulan kebutuhan berjalan melalui tahapan sistematis:
- **Identifikasi Pemangku Kepentingan (*Identifying Stakeholders*)**: Melibatkan perwakilan dari seluruh kelompok yang terdampak oleh produk (pengambil keputusan, pengguna akhir, administrator sistem, rekayasawan, tim pemasaran, tim penjualan, dan tim dukungan pelanggan).
- **Penetapan Sasaran dan Tujuan (*Goals and Objectives*)**:
  - Sasaran (*Goals*): Hasil jangka panjang berskala luas yang ingin dicapai (misalnya peningkatan efisiensi operasional organisasi).
  - Tujuan (*Objectives*): Langkah-langkah tindakan spesifik, terukur, dan dapat ditindaklanjuti untuk mewujudkan sasaran tersebut.
- **Pemerolehan Kebutuhan (*Eliciting Requirements*)**: Menggali kebutuhan nyata melalui wawancara mendalam, survei, kuesioner, dan observasi kerja.
- **Dokumentasi Kebutuhan (*Documenting Requirements*)**: Mencatat kebutuhan secara jelas, terstruktur, dan mudah dipahami oleh pemangku kepentingan maupun tim teknis.
- **Analisis dan Konfirmasi (*Analyzing and Confirming Requirements*)**: Menguji konsistensi, kejelasan, kelengkapan, dan ketiadaan kontradiksi antarkebutuhan, dilanjutkan dengan penandatanganan persetujuan resmi (*stakeholder sign-off*).
- **Penentuan Prioritas (*Prioritizing Requirements*)**: Mengelompokkan kebutuhan ke dalam kategori urgensi terukur, seperti *must-have* (wajib ada untuk operasional minimal), *highly desired* (sangat diinginkan), dan *nice-to-have* (pelengkap estetika/kenyamanan).

### B. Tiga Jenis Dokumen Spesifikasi Kebutuhan
Industri membedakan dokumen kebutuhan berdasarkan lingkup dan tujuannya:

#### a. User Requirements Specification (URS)
Dokumen yang menangkap kebutuhan bisnis murni dari sudut pandang pengguna akhir:
- Ditulis dalam bahasa bisnis non-teknis, biasanya berbentuk cerita pengguna (*user stories*) atau kasus penggunaan (*use cases*).
- Menjawab tiga pertanyaan fundamental: siapa penggunanya (*who*), fungsi apa yang ingin dijalankan (*what*), dan mengapa fungsionalitas tersebut berharga (*why*).
- Menjadi tolok ukur utama dalam pengujian penerimaan pengguna (*User Acceptance Testing / UAT*).

#### b. Software Requirements Specification (SRS)
Dokumen paling umum dalam rekayasa perangkat lunak yang merinci fungsi operasional dan tolok ukur kinerja yang harus dipenuhi oleh sistem perangkat lunak:
- **Pernyataan Tujuan (*Purpose Statement*)**: Menjelaskan sasaran dokumen, target audiens, dan batas lingkup produk (*scope*).
- **Batasan, Asumsi, dan Ketergantungan (*Constraints, Assumptions, Dependencies*)**:
  - Batasan: Faktor pembatas desain seperti kepatuhan standar hukum atau limitasi perangkat keras.
  - Asumsi: Kondisi prasyarat yang dianggap benar, misalnya ketersediaan sistem operasi tertentu.
  - Ketergantungan: Keterikatan fungsi dengan perangkat lunak atau API pihak ketiga.
- **Empat Kategori Kebutuhan SRS**:
  - *Functional Requirements*: Fungsionalitas kalkulasi, manipulasi data, dan operasi logis yang harus dieksekusi sistem.
  - *External Interface Requirements*: Aturan interaksi antarmuka perangkat lunak dengan entitas luar (antarmuka pengguna, protokol perangkat keras, atau pustaka perangkat lunak lain).
  - *System Features*: Rincian fitur terintegrasi yang wajib ada agar sistem dapat berfungsi utuh.
  - *Non-Functional Requirements*: Standar kualitas performa sistem, tingkat kecepatan respons, ketersediaan layanan (*availability*), keandalan (*reliability*), keselamatan (*safety*), dan protokol keamanan (*security*).

#### c. System Requirements Specification (SysRS)
Dokumen spesifikasi tingkat tertinggi yang memiliki cakupan lebih luas dibanding SRS:
- Tidak hanya mencakup perangkat lunak, melainkan mendefinisikan persyaratan terpadu untuk keseluruhan sistem, termasuk konfigurasi perangkat keras fisik (*hardware*), topologi jaringan, arsitektur fasilitas, dan integrasi personel manusia.
- Memuat kepatuhan regulasi makro, kebijakan operasional perusahaan, kriteria penerimaan sistem menyeluruh, dan persyaratan kualifikasi staf operasional.

---

## 7. Summary and Key Takeaways

Fondasi rekayasa perangkat lunak berakar pada kedisiplinan proses dan komitmen terhadap kualitas terukur:
- Rekayasa perangkat lunak mentransformasikan pemrograman informal menjadi disiplin ilmiah terstandarisasi untuk mengatasi krisis perangkat lunak (*software crisis*).
- Peran insinyur perangkat lunak (*software engineer*) berfokus pada arsitektur sistem jangka panjang dan gambaran besar, sedangkan pengembang (*software developer*) berfokus pada penulisan kode fungsional spesifik.
- Siklus hidup pengembangan perangkat lunak (SDLC) memandu proyek melalui enam fase terstruktur: *Planning*, *Design*, *Development*, *Testing*, *Deployment*, dan *Maintenance*.
- Kualitas perangkat lunak dicapai melalui kepatuhan pada standar kode bersih, pengujian berlapis (*Unit*, *Integration*, *System*, *UAT*), tahapan rilis bertahap (*Alpha*, *Beta*, *GA*), dan dokumentasi menyeluruh.
- Rekayasa kebutuhan memastikan keselarasan antara ekspektasi bisnis dengan realisasi teknis melalui tiga dokumen formal: URS (sudut pandang pengguna), SRS (rincian perangkat lunak), dan SysRS (spesifikasi sistem menyeluruh).
