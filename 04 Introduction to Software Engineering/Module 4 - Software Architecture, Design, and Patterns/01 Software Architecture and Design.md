# Software Architecture and Design Fundamentals

Dokumen ini menyajikan kajian mendalam mengenai fondasi arsitektur dan perancangan perangkat lunak, mencakup peran arsitektur sebagai cetak biru sistem, pertimbangan atribut non-fungsional dan lingkungan produksi, prinsip desain terstruktur (*cohesion* dan *coupling*), pemodelan sistem menggunakan *Unified Modeling Language (UML)*, analisis dan perancangan berorientasi objek (*OOAD*) beserta diagram kelas dan relasi pewarisan (*inheritance*), hingga wawasan praktisi industri mengenai strategi arsitektur berkelanjutan dan perencanaan jangka panjang.

---

## 1. Introduction to Software Architecture

Perancangan perangkat lunak dan penyusunan dokumentasinya berlangsung secara intensif pada fase desain dalam Siklus Hidup Pengembangan Perangkat Lunak (*Software Development Life Cycle / SDLC*). Arsitektur perangkat lunak pada hakikatnya adalah pengorganisasian mendasar dari sebuah sistem komputasi yang menjadi cetak biru (*blueprint*) bagi para pengembang dalam merekayasa komponen-komponen yang saling berinteraksi.

### A. Definisi dan Hakikat Arsitektur Perangkat Lunak
- **Struktur Fundamental**:
  - Arsitektur mencakup komponen-komponen utama sistem, hubungan timbal balik antar-komponen, prinsip perancangan yang dianut, serta lingkungan operasional tempat perangkat lunak dijalankan.
  - Berfungsi menangkap keputusan-keputusan desain paling awal yang berimplikasi luas dan sangat mahal biayanya jika harus diubah di kemudian hari setelah kode program ditulis.
- **Fokus pada Kualitas Non-Fungsional**:
  - Arsitektur berfokus menjawab kebutuhan non-fungsional sistem (*non-functional requirements* atau atribut kualitas), seperti:
    - *Kinerja (Performance)*: Waktu respons dan efisiensi konsumsi sumber daya komputasi.
    - *Skalabilitas (Scalability)*: Kemampuan menangani lonjakan beban kerja dan pertumbuhan volume pengguna.
    - *Keterpeliharaan (Maintainability)*: Kemudahan perbaikan kutu program, pembaruan modul, dan refaktorisasi.
    - *Interoperabilitas (Interoperability)*: Kemampuan bertukar data dan beroperasi selaras dengan sistem eksternal lain.
    - *Keamanan (Security)*: Ketahanan terhadap ancaman siber dan perlindungan privasi data.
    - *Keterkelolaan (Manageability)*: Kemudahan pemantauan kondisi sistem dan administrasi operasional.

### B. Nilai Strategis Desain Arsitektur yang Kokoh
- **Penyelarasan Pemangku Kepentingan (*Stakeholder Communication*)**: Menjembatani berbagai kepentingan yang berbeda antara klien bisnis, manajer proyek, tim teknis, dan tim operasi ke dalam satu pemahaman arsitektural yang konsisten.
- **Landasan Keputusan Implementasi**: Keputusan arsitektur awal menjadi batasan acuan (*constraints*) yang mengarahkan keputusan pengkodean tingkat rendah pada tahap pengembangan selanjutnya.
- **Ketangkasan terhadap Perubahan Kebutuhan (*Agility*)**: Arsitektur yang terstruktur secara modular memungkinkan sistem beradaptasi terhadap perubahan kebutuhan fungsional tanpa merusak integritas sistem secara keseluruhan.
- **Memperpanjang Masa Pakai Sistem (*Lifespan*)**: Arsitektur yang solid menjaga perangkat lunak tetap relevan dan beroperasi stabil selama bertahun-tahun, meskipun detail teknologi implementasi di dalamnya mengalami pergantian.

### C. Pengaruh Arsitektur terhadap Tumpukan Teknologi dan Lingkungan Produksi
- **Panduan Pemilihan Tumpukan Teknologi (*Technology Stack*)**:
  - Pilihan bahasa pemrograman, kerangka kerja, pustaka pendukung, dan basis data harus diselaraskan secara ketat dengan atribut non-fungsional yang ditargetkan oleh arsitektur.
  - Arsitek wajib memahami kelebihan dan kompromi dari setiap tumpukan untuk mengantisipasi hambatan skalabilitas di masa depan.
- **Penetapan Infrastruktur Lingkungan Produksi (*Production Environment*)**:
  - Keputusan arsitektur mendikte rancangan infrastruktur fisik maupun komputasi awan yang mendistribusikan aplikasi kepada pengguna akhir, mencakup pemilihan jenis peladen, konfigurasi penyeimbang beban (*load balancers*), topologi basis data, hingga mekanisme replikasi data.

### D. Artefak Utama dalam Fase Desain Arsitektur
Desain arsitektur dikomunikasikan kepada tim pengembang dan pemangku kepentingan melalui sejumlah artefak resmi:
- **Dokumen Desain Perangkat Lunak (*Software Design Document / SDD*)**:
  - Kumpulan spesifikasi teknis komprehensif yang menjabarkan bagaimana solusi harus diimplementasikan.
  - Memuat deskripsi fungsional lengkap, batasan sistem (*constraints*), asumsi, dependensi modul, metodologi pengembangan, serta tujuan teknis proyek.
- **Diagram Arsitektur (*Architectural Diagram*)**:
  - Representasi grafis tingkat tinggi yang memetakan batas-batas komponen, pola interaksi, isolasi subsistem, serta pola arsitektur (*architectural patterns*) yang diterapkan.
- **Diagram Pemodelan Terpadu (*UML Diagrams*)**:
  - Rangkaian diagram berbasis visual terstandarisasi yang mendokumentasikan struktur statis maupun perilaku dinamis sistem tanpa terikat pada bahasa pemrograman tertentu.

---

## 2. Software Design and Modeling

Desain perangkat lunak adalah proses formal di mana komponen struktural dan atribut perilaku sistem didefinisikan serta didokumentasikan sebelum fase penulisan kode dimulai. Pemodelan sistem secara visual membantu tim rekayasa memetakan arsitektur global ke dalam subsistem-subsistem yang lebih mudah dikelola.

### A. Prinsip Desain Terstruktur (Structured Design)
Desain terstruktur memecah permasalahan perangkat lunak yang rumit menjadi elemen-elemen solusi yang lebih kecil dan terorganisasi secara rapi, yaitu berupa modul dan sub-modul dalam tatanan hierarkis:
- **Kohesi (*Cohesion*)**:
  - Derajat keterikatan fungsional antar-elemen di dalam satu modul tunggal.
  - *Prinsip Utama*: Seluruh fungsi dan data yang memiliki keterkaitan erat wajib dikelompokkan bersama di dalam modul yang sama (*high cohesion*).
- **Kopling (*Coupling*)**:
  - Derajat interaksi, komunikasi, dan ketergantungan antar-modul yang berbeda.
  - *Prinsip Utama*: Sistem yang unggul menuntut keterikatan yang lemah atau longgar antar-modul (*loose coupling*). Modul-modul dirancang agar perubahan internal pada satu komponen memiliki dampak minimal terhadap komponen lain.
  - Prinsip *loose coupling* menjadi fondasi mutlak dalam arsitektur berorientasi layanan (*Service-Oriented Architecture / SOA*) dan arsitektur layanan mikro (*microservices*).
- **Studi Kasus Modul Penagihan (*Billing System*)**:
  - Modul utama penagihan (*Billing*) membawahi sejumlah sub-modul terfokus seperti verifikasi asuransi (*insurance verification*), pengajuan klaim (*submit claim*), dan kalkulasi total biaya (*output total*). Aliran data bergerak secara terstruktur melalui antarmuka modul yang terdefinisi.

### B. Karakteristik Model Perilaku (Behavioral Models)
Model perilaku berfokus mendeskripsikan apa yang dilakukan oleh sistem secara dinamis dalam merespons stimulus luar, tanpa mempermasalahkan detail teknis bagaimana sistem mengimplementasikan mekanisme tersebut di balik layar.

### C. Unified Modeling Language (UML)
*Unified Modeling Language (UML)* adalah bahasa pemodelan visual terstandarisasi yang digunakan di seluruh industri teknologi untuk memvisualisasikan, merancang, dan mendokumentasikan sistem perangkat lunak:
- **Sifat Bebas Bahasa (*Language-Agnostic*)**:
  - Simbol dan notasi UML bersifat universal dan dapat dipahami oleh seluruh pengembang terlepas dari apakah sistem akan diimplementasikan menggunakan Java, Python, C++, atau bahasa lainnya.
- **Dua Klasifikasi Utama Diagram UML**:
  - *Diagram Struktural (Structural Diagrams)*: Memetakan konfigurasi statis sistem, komponen kode, antarmuka, dan hubungan hierarki objek.
  - *Diagram Perilaku (Behavioral Diagrams)*: Memodelkan dinamika waktu proses, perubahan status sistem, alur kerja operasional, dan komunikasi antar-komponen.
- **Keuntungan Utama Penggunaan UML**:
  - *Efisiensi Biaya dan Waktu*: Perencanaan fitur secara visual sebelum pengkodean mencegah kesalahan logika arsitektural yang mahal.
  - *Akselerasi Orientasi Anggota Baru (Onboarding)*: Membantu pengembang baru memahami keterkaitan arsitektur sistem secara menyeluruh dengan cepat.
  - *Jembatan Komunikasi Bisnis dan Teknis*: Memudahkan penyampaian konsep sistem yang kompleks kepada audiens non-teknis.
  - *Navigasi Basis Kode (Codebase Navigation)*: Menjadi peta visual yang memandu pengembang saat menelusuri baris-baris kode sumber yang saling terhubung.

### D. Ragam Diagram Perilaku Populer
- **Diagram Transisi Status (*State Transition Diagram*)**:
  - Menjelaskan siklus hidup entitas melalui kumpulan status (*states*) dan kejadian pemicu (*events*) yang menyebabkan perubahan status tersebut.
  - *Contoh Alur Pasien di Klinik*: Memodelkan perjalanan seorang pasien mulai dari status "menunggu" (*waiting*), beralih ke status "pemeriksaan laboratorium" (*testing*) akibat kejadian panggilan antrean, hingga beralih ke status "berkonsultasi dengan dokter" (*with the doctor*).
- **Diagram Interaksi / Diagram Urutan (*Sequence Diagram*)**:
  - Memodelkan aspek dinamis sistem dengan memperlihatkan pertukaran pesan dan komunikasi antar-objek berdasarkan urutan waktu (*with respect to time*).
  - *Contoh Pembuatan Janji Daring*: Memvisualisasikan pertukaran pesan antara objek pasien, antarmuka portal daring, modul jadwal, dan basis data saat reservasi dibuat secara kronologis.

---

## 3. Object-Oriented Analysis and Design (OOAD)

Analisis dan Desain Berorientasi Objek (*Object-Oriented Analysis and Design / OOAD*) adalah metodologi rekayasa sistem yang memandang perangkat lunak sebagai jejaring objek-objek mandiri yang berkolaborasi menjalankan tugas.

### A. Konsep Inti: Objek dan Kelas
- **Objek (*Objects*)**:
  - Entitas mandiri di dalam sistem yang merangkum data internal dan perilaku tindakan yang dapat dijalankan.
- **Kelas (*Classes*)**:
  - Cetak biru (*blueprint*) atau templat generik tempat objek diciptakan.
  - Mendefinisikan atribut generik yang mencakup medan data (*properties*) dan fungsi tindakan (*methods*).
- **Proses Instansiasi (*Instantiation*)**:
  - Objek konkret (disebut juga instans / *instance*) diwujudkan di dalam memori program dari cetak biru kelas.
  - *Contoh Penerapan*: Kelas generik `Patient` memiliki variabel properti `LastName`. Properti ini merupakan penampung kosong hingga terjadi instansiasi objek konkret bernama `Naya Patel`. Setelah instansiasi selesai, objek `Naya Patel` dapat memanggil metode seperti `cancelAppointment()` untuk membatalkan jadwal konsultasi.
- **Mendukung Konkurensi Rekayasa**: Sistem yang dipecah ke dalam objek-objek mandiri memungkinkan banyak pengembang bekerja secara paralel pada komponen berbeda tanpa saling mengganggu.

### B. Diagram Kelas (Class Diagram)
Diagram kelas merupakan salah satu diagram struktural UML yang paling fundamental dalam pendekatan OOAD untuk memetakan anatomi arsitektur sistem:
- **Representasi Visual Kelas**:
  - Setiap kelas digambarkan dalam sebuah kotak terbagi tiga:
    - Bagian atas: Nama kelas (*Class Name*).
    - Bagian tengah: Daftar atribut atau data properti (*Properties / Fields*).
    - Bagian bawah: Daftar tindakan atau operasi fungsi (*Methods / Behaviors*).
- **Pemetaan Hubungan Antar-Kelas**:
  - Memperlihatkan bagaimana berbagai kelas di dalam sistem saling berinteraksi, berasosiasi, atau membentuk relasi struktural.

### C. Hubungan Hierarki dan Pewarisan (Inheritance)
- **Konsep Pewarisan**:
  - Sebuah subkelas (*subclass*) diturunkan dari kelas induk (*parent/super class*). Subkelas secara otomatis mewarisi seluruh data atribut dan metode fungsi yang dimiliki oleh kelas induknya (*inherits attributes*).
  - Subkelas dapat menambahkan atribut dan metode baru yang lebih spesifik sesuai perannya.
- **Hierarki Tenaga Medis (*Medical Personnel Hierarchy*)**:
  - Kelas induk utama: `MedicalPersonnel`.
  - Subkelas langsung: `Nurse`, `Doctor`, dan `Technician`. Ketiganya mewarisi seluruh kapabilitas dasar tenaga medis.
  - Subkelas turunan tingkat lanjut: `Specialist` yang merupakan turunan langsung dari kelas `Doctor`.
  - *Implikasi Fungsional*: Kelas dokter dapat menjalankan seluruh fungsi tenaga medis, dan dokter spesialis dapat menjalankan seluruh fungsi dokter umum ditambah kompetensi spesialisasi lanjutannya.

---

## 4. Insiders' Viewpoint: The Importance of Design and Software Architecture

Praktisi dan arsitek sistem industri menegaskan bahwa desain dan arsitektur bukanlah formalitas teoritis semata, melainkan fondasi kelangsungan hidup perangkat lunak di dunia nyata.

### A. Filosofi Orkestrasi dan Keselarasan Ekosistem
- **Analogi Orkestra Simfoni**:
  - Pengembang dapat menciptakan sebuah modul atau instrumen musik yang terdengar sangat merdu secara individual. Namun, jika instrumen tersebut tidak berpadu secara harmonis dengan seluruh instrumen lain di orkestra, hasil akhirnya adalah kekacauan nada (*cacophonous mess*).
  - Rekayasa perangkat lunak menuntut pemahaman terhadap ekosistem sistem secara makro (*the bigger picture*).
- **Menghilangkan Pemborosan Kode (*Preventing Churny Code*)**:
  - Menulis baris kode tanpa rancangan arsitektur awal sering kali berakhir pada penulisan ulang kode yang sia-sia ketika modul terbukti tidak dapat beroperasi dalam sistem nyata.
  - Perencanaan arsitektur di muka memberikan kepastian tinggi bahwa kode yang ditulis akan bertahan lama (*persist*), terintegrasi mulus, dan bermanfaat nyata.

### B. Tiga Pertanyaan Fundamental dalam Perancangan Sistem
Seorang perancang atau arsitek sistem wajib merumuskan jawaban tegas atas tiga pertanyaan dasar:
- **1. Komponen apa yang kita butuhkan? (*What things do we need?*)**:
  - Mengidentifikasi modul, dependensi, jenis basis data, dan pustaka eksternal yang mutlak diperlukan.
- **2. Di mana komponen tersebut akan ditempatkan? (*Where are they going to live?*)**:
  - Menentukan topologi penempatan: apakah co-hosted pada peladen yang sama, didistribusikan di berbagai kontainer awan, atau dialokasikan di pusat data terpisah.
- **3. Apa cakupan dan batas tanggung jawabnya? (*What is their scope and responsibility?*)**:
  - Memastikan batas-batas kewenangan (*boundaries*) setiap modul terdefinisi jelas sehingga tidak terjadi tumpang tindih logika.

### C. Aliran Data, Latensi Jaringan, dan Skalabilitas Global
- **Kesenjangan Skala Lokal vs Skala Global**:
  - Solusi yang bekerja sempurna di laptop pengembang (*hyper-local environment*) untuk satu pengguna kerap mengalami kegagalan fatal saat dihadapkan pada jutaan pengguna dari berbagai belahan dunia (*global availability*).
- **Konsekuensi Arsitektur Layanan Mikro (*Microservices*)**:
  - Ketika modul dipecah ke peladen atau wadah komputasi awan yang terpisah, setiap komunikasi antar-layanan menuntut lompatan jaringan (*network hops*).
  - Lompatan jaringan memakan latensi waktu. Jika strategi pemuatan data (*data loading*) dirancang serampangan, aplikasi akan mengalami batas waktu habis (*timeouts*) dan mengecewakan pengguna.
- **Manajemen Identitas dan Keamanan Lintas Layanan**:
  - Arsitektur harus menentukan secara presisi mekanisme pembuktian identitas pengguna (*account management*) serta hak otorisasi yang sah saat berpindah antar-layanan.
  - Menetapkan protokol terenkripsi bagaimana layanan backend saling berkomunikasi secara aman dan terverifikasi.

### D. Perencanaan Jangka Panjang Berkelanjutan (5 hingga 10 Tahun ke Depan)
- **Visi Berkelanjutan (*Sustainable Architecture*)**:
  - Merancang arsitektur berarti memproyeksikan arah pertumbuhan sistem 5 hingga 10 tahun ke depan.
  - Arsitektur tidak boleh dirancang sekadar untuk menyelesaikan kebutuhan peluncuran instan yang berumur pendek.
- **Analogi Pemeliharaan Bangunan Gedung**:
  - Ketika sebuah bangunan fisik dirawat, pengelola melakukan perbaikan berkala pada elemen-elemen kecil yang aus, bukan merobohkan dan membangun ulang seluruh gedung setiap beberapa tahun sekali.
  - Demikian pula dalam perangkat lunak: arsitektur yang dirancang secara kokoh dan berkelanjutan memungkinkan tim melakukan evolusi bertahap (*incremental evolution*) tanpa harus melakukan perombakan arsitektur menyeluruh (*costly re-architecture*) secara berulang.