# Software Architecture Patterns and Deployment Topologies

Dokumen ini menyajikan panduan mendalam mengenai pendekatan arsitektur aplikasi modern dan topologi penerapan sistem, mencakup prinsip arsitektur berbasis komponen (*component-based*) dan layanan (*SOA*), karakteristik sistem terdistribusi, lima pola arsitektur utama (*2-tier*, *3-tier*, *peer-to-peer*, *event-driven*, dan *microservices*), klasifikasi lingkungan pra-produksi hingga produksi, infrastruktur fisik on-premises dan komputasi awan (*public*, *private*, *hybrid cloud*), komponen kunci peladen produksi (firewall, load balancer, reverse proxy, cluster basis data), hingga strategi penerapan mutakhir seperti *canary deployment* dan pemantauan *Service Level Objectives (SLOs)*.

---

## 1. Approaches to Application Architecture

Pengembangan sistem berskala menengah hingga enterprise menuntut dekomposisi struktur perangkat lunak ke dalam unit-unit fungsional yang mandiri, teruji, dan dapat beroperasi selaras di berbagai lingkungan komputasi.

### A. Arsitektur Berbasis Komponen (Component-Based Architecture)
Komponen adalah unit fungsionalitas individual yang terenkapsulasi dan berfungsi sebagai bagian pembangun aplikasi secara terpadu bersama komponen lainnya. Desain berbasis komponen menyediakan tingkat abstraksi yang lebih tinggi dibandingkan sekadar perancangan berorientasi objek (*OOP*).

- **Enam Karakteristik Pilar Komponen**:
  - *Dapat Digunakan Kembali (Reusable)*: Komponen dirancang secara modular agar dapat disematkan pada berbagai aplikasi berbeda tanpa perlu modifikasi kode internal.
  - *Dapat Diganti (Replaceable)*: Komponen dapat diganti dengan komponen lain yang setara tanpa merusak kestabilan sistem secara keseluruhan.
  - *Mandiri (Independent)*: Komponen dirancang untuk meminimalkan dependensi terhadap komponen lain.
  - *Dapat Diperluas (Extensible)*: Memiliki kemampuan untuk ditambahkan fungsionalitas baru tanpa harus mengubah komponen-komponen lain yang terhubung.
  - *Terenkapsulasi (Encapsulated)*: Membungkus data internal dan metode secara ketat, menyembunyikan detail implementasi spesifik, dan hanya membuka antarmuka akses resmi.
  - *Bebas Konteks Spesifik (Non-Context Specific)*: Mampu beroperasi di beragam lingkungan operasional; data yang menetapkan status internal komponen harus diteruskan sebagai parameter dari luar, bukan ditanam kaku di dalam komponen.
- **Contoh Penerapan Komponen**:
  - *Antarmuka Pemrograman Aplikasi (API)*: Modul penghubung sumber terbuka yang mengelola konektivitas antara aplikasi dengan basis data tertentu.
  - *Objek Akses Data (Data Access Object / DAO)*: Komponen antarmuka yang mengabstraksi mekanisme akses basis data, memungkinkan pengalihan jenis basis data tanpa disadari oleh logika aplikasi utama.
  - *Pengendali (Controller)*: Komponen yang mengatur alur data dan memanggil komponen lain yang relevan saat menerima pemicu suatu peristiwa (*event*).

### B. Arsitektur Berorientasi Layanan (Service-Oriented Architecture / SOA)
Layanan (*service*) memiliki kesamaan dengan komponen sebagai unit fungsionalitas, namun dirancang untuk disebarkan secara mandiri (*independently deployed*) dan digunakan kembali oleh berbagai sistem eksternal guna memecahkan kebutuhan bisnis spesifik.

- **Hierarki Konseptual Arsitektur Berlapis**:
  - Layanan (*Services*) tersusun atas kumpulan komponen (*Components*).
  - Komponen (*Components*) tersusun atas kumpulan objek (*Objects*).
- **Perbedaan Mendasar Komponen vs Layanan**:
  - Layanan umumnya hanya memiliki satu instans unik yang berjalan secara terus-menerus (*always-running unique instance*) di jaringan dan melayani banyak klien secara bersamaan.
  - Contoh layanan bisnis: layanan verifikasi skor kredit nasabah, layanan kalkulasi simulasi pinjaman bulanan, atau layanan pemrosesan aplikasi hipotek.
- **Prinsip Operasional SOA**:
  - Layanan-layanan dihubungkan secara longgar (*loosely coupled*) dan saling berkomunikasi melalui protokol komunikasi terstandarisasi melalui jaringan komputer.

### C. Karakteristik Sistem Terdistribusi (Distributed Systems)
Arsitektur SOA menjadi fondasi dalam membangun sistem terdistribusi, yaitu sistem yang terdiri dari sekumpulan layanan independen yang beroperasi pada mesin-mesin fisik atau virtual yang berbeda, namun berkoordinasi secara harmonis melalui pertukaran pesan jaringan (seperti protokol HTTP).

- **Transparansi Sistem Tunggal**: Bagi pengguna akhir, seluruh infrastruktur terdistribusi tampak bekerja sebagai satu kesatuan sistem tunggal yang utuh dan koheren.
- **Karakteristik Utama Sistem Terdistribusi**:
  - *Berbagi Sumber Daya (Resource Sharing)*: Membagi alokasi perangkat keras, perangkat lunak, dan repositori data lintas jaringan.
  - *Toleransi Kesalahan (Fault-Tolerant)*: Kegagalan pada satu simpul (*node*) atau satu layanan tidak menghentikan operasional sistem secara keseluruhan; sistem dapat diperbarui secara dinamis tanpa pemadaman layanan (*zero downtime*).
  - *Eksekusi Konkuren (Concurrency)*: Berbagai aktivitas komputasi berjalan secara simultan pada banyak mesin, mereduksi latensi dan meningkatkan laju pemrosesan data (*throughput*).
  - *Skalabilitas Horizontal (Scalability)*: Kapasitas komputasi dapat ditambah secara elastis seiring pertumbuhan volume pengguna.
  - *Heterogenitas (Heterogeneity)*: Komputer pembangun sistem terdistribusi tidak perlu seragam; sistem dapat memadukan beragam jenis perangkat keras, sistem operasi, dan bahasa pemrograman yang berbeda.
- **Definisi Simpul (*Node*)**: Perangkat fisik atau virtual apa pun dalam jaringan yang mampu mengenali, memproses, dan mentransmisikan data ke simpul lainnya.

---

## 2. Architectural Patterns in Software

Pola arsitektur (*architectural pattern*) adalah solusi teruji yang dapat digunakan berulang kali untuk memecahkan permasalahan arsitektural umum dalam rekayasa perangkat lunak. Pola arsitektur memetakan struktur internal dan hubungan antar-subsistem.

### A. Pola Dua Tingkat (2-Tier / Client-Server)
- **Karakteristik**:
  - Membagi sistem menjadi dua entitas utama: mesin klien dan mesin peladen yang terhubung melalui jaringan.
  - Peladen menjadi pusat hosting, penyedia layanan, dan pengelola sumber daya utama, sedangkan klien menyediakan antarmuka interaksi dan mengirimkan permintaan (*requests*).
- **Contoh Penerapan**:
  - Aplikasi perpesanan teks instan (klien memulai pengiriman pesan ke peladen, peladen meneruskan pesan tersebut ke klien penerima).
  - Aplikasi klien desktop yang terhubung langsung ke mesin peladen basis data.

### B. Pola Tiga Tingkat (3-Tier / N-Tier)
Pola paling populer dalam rekayasa aplikasi web modern yang membagi aplikasi ke dalam tiga tingkatan komputasi logis dan fisik:
- **Tiga Tingkatan Standar**:
  - *Tingkat Presentasi (Presentation Tier)*: Lapisan antarmuka pengguna di sisi klien (*front-end*) yang menangkap interaksi pengguna.
  - *Tingkat Aplikasi / Logika Bisnis (Application / Middle Tier)*: Lapisan pemrosesan logika operasional bisnis, validasi aturan transaksi, dan kalkulasi dinamis.
  - *Tingkat Data (Data Tier)*: Lapisan persistensi yang mengelola, menyimpan, dan mengamankan integritas data melalui sistem manajemen basis data.
- **Aturan Isolasi Tingkat**:
  - Suatu tingkatan hanya boleh berkomunikasi langsung dengan tingkatan yang berada tepat di atas atau di bawahnya.
  - Komponen-komponen terkait dikelompokkan dalam tingkat yang sama, sehingga perubahan internal pada satu tingkat tidak berdampak negatif terhadap tingkat lainnya.

### C. Pola Komputasi Terdesentralisasi (Peer-to-Peer / P2P)
- **Karakteristik Desentralisasi**:
  - Menghilangkan peran peladen terpusat. Setiap simpul (*peer*) di dalam jaringan berfungsi secara setara sebagai klien sekaligus peladen secara serentak.
  - Beban kerja dan alokasi sumber daya (kapasitas pemrosesan CPU, ruang penyimpanan disk, dan lebar pita jaringan) dibagi rata di antara seluruh partisipan jaringan.
  - Setiap rekanan menyediakan (*supply*) sekaligus mengonsumsi (*consume*) sumber daya secara langsung tanpa perantara sentral.
- **Contoh Penerapan**:
  - Jaringan berbagi berkas terdistribusi, platform komunikasi instan terdesentralisasi, dan sistem *blockchain* mata uang kripto seperti Bitcoin dan Ethereum.

### D. Pola Digerakkan Peristiwa (Event-Driven Architecture / EDA)
- **Karakteristik Arsitektur**:
  - Berfokus pada produksi, deteksi, dan konsumsi kejadian atau perubahan status yang disebut peristiwa (*events*).
  - Terdiri atas dua komponen utama:
    - *Produsen Peristiwa (Event Producers)*: Komponen yang mendeteksi pemicu (seperti klik tombol pengguna atau pembaruan status sistem) dan menerbitkan notifikasi peristiwa ke perute peristiwa (*event router*).
    - *Konsumen Peristiwa (Event Consumers)*: Komponen yang mendengarkan (*listen*) saluran notifikasi dan mengeksekusi logika pemrosesan saat peristiwa yang relevan diteruskan oleh router.
  - Seluruh komponen terikat secara sangat longgar (*highly decoupled*), menjadikannya pola ideal untuk sistem terdistribusi modern yang menuntut responsivitas tinggi.
- **Contoh Penerapan**:
  - Aplikasi transportasi daring (*ride-sharing* seperti Uber atau Lyft): Permintaan tumpangan dari penumpang diterbitkan sebagai sebuah peristiwa, dirutekan secara otomatis oleh perute sistem, dan diterima oleh aplikasi pengemudi terdekat sebagai konsumen peristiwa.

### E. Pola Layanan Mikro (Microservices Architecture)
- **Karakteristik Modularitas**:
  - Memecah fungsionalitas aplikasi menjadi sekumpulan layanan kecil yang berdiri sendiri, memiliki basis data mandiri, dan dapat disebarkan secara independen (*independently deployable*).
  - Layanan-layanan berkomunikasi melalui antarmuka pemrograman aplikasi (*API*).
  - *Gerbang API (API Gateway)*: Bertindak sebagai titik masuk tunggal yang merutekan setiap permintaan dari klien menuju layanan mikro spesifik yang relevan.
  - *Orkestrasi Layanan (Service Orchestration)*: Mengelola tata kelola alur kerja dan komunikasi timbal balik antar-layanan mikro.
- **Contoh Penerapan**:
  - Platform media sosial berskala global: Terdiri dari layanan terpisah untuk otentikasi akun, pengelolaan pertemanan, mesin rekomendasi iklan bertarget, dan sistem umpan konten (*feed delivery*).

### F. Sinergi dan Batasan Kombinasi Pola
- **Pola Tidak Bersifat Eksklusif Saling Lepas**:
  - Berbagai pola arsitektur dapat dikombinasikan dalam satu arsitektur solusi sistem. Misalnya, arsitektur 3-tier dapat diimplementasikan menggunakan arsitektur microservices pada lapisan tengahnya, atau jaringan peer-to-peer dapat mengadopsi mekanisme event-driven.
- **Batasan Kontradiksi Pola**:
  - Beberapa pola memiliki filosofi yang bertolak belakang sehingga tidak dapat digabungkan secara langsung. Sebagai contoh, sebuah sistem tidak dapat menjadi pola *peer-to-peer* murni sekaligus pola *2-tier* konvensional, karena pola P2P menyatukan peran klien dan peladen pada setiap simpul, sedangkan pola 2-tier memisahkan peran keduanya secara kaku.

---

## 3. Application Deployment Environments

Sebuah lingkungan aplikasi (*application environment*) adalah kombinasi lengkap antara sumber daya perangkat lunak dan infrastruktur perangkat keras yang dibutuhkan untuk menjalankan aplikasi di setiap tahapan siklus hidupnya.

### A. Komposisi Pembangun Lingkungan Aplikasi
Lingkungan aplikasi mencakup:
- Berkas kode sumber dan artefak biner eksekutabel dari seluruh modul aplikasi.
- Tumpukan perangkat lunak (*software stack*) pendukung: pustaka dependensi, aplikasi pihak ketiga, middleware, dan sistem operasi.
- Konfigurasi komponen jaringan dan infrastruktur komunikasi.
- Sumber daya komputasi fisik atau tervirtualisasi: prosesor (*CPU*), memori kerja (*RAM*), dan media penyimpanan data (*storage*).

### B. Lingkungan Pra-Produksi (Pre-Production Environments)
Platform persiapan bertahap sebelum kode dirilis ke lingkungan publik:
- **Lingkungan Pengembangan (*Development Environment*)**:
  - Tempat di mana pengembang menulis, memodifikasi, dan menelusuri galat pada baris kode secara aktif. Kerap kali berwujud stasiun kerja (*workstation*) atau laptop pribadi pengembang.
- **Lingkungan Pengujian Kualitas (*QA / Testing Environment*)**:
  - Lingkungan terisolasi yang dialokasikan khusus bagi tim penjamin kualitas (*Quality Assurance*) untuk menguji fungsionalitas modul, menjalankan pengujian otomatis, dan memvalidasi kebebasan sistem dari bug.
- **Lingkungan Pementasan (*Staging Environment*)**:
  - Lingkungan pengujian tahap akhir yang dikonfigurasi sebagai replika sempurna yang sedekat mungkin mencerminkan infrastruktur produksi nyata. Digunakan untuk gladi bersih rilis dan verifikasi performa beban tanpa melibatkan pengguna umum.

### C. Lingkungan Produksi (Production Environment)
- **Hakikat Lingkungan Produksi**:
  - Platform operasional utama (*live production*) yang digunakan langsung oleh seluruh pengguna akhir aplikasi.
- **Tuntutan Mutlak Kualitas Non-Fungsional**:
  - Wajib memperhitungkan beban volume trafik nyata (*load*) yang dapat mencapai ribuan hingga jutaan pengguna secara konkuren pada aplikasi enterprise.
  - Menuntut standar tertinggi pada aspek keamanan data, ketersediaan tinggi (*high availability*), ketahanan terhadap bencana (*disaster recovery*), dan skalabilitas komputasi.

### D. Model Penyebaran Infrastruktur: On-Premises vs Cloud
- **Penyebaran Fisik Sendiri (*On-Premises Deployment*)**:
  - Seluruh infrastruktur peladen, perangkat jaringan, dan media penyimpanan ditempatkan secara fisik di pusat data internal milik organisasi di balik dinding api (*firewall*) privat.
  - Memberikan kendali mutlak atas kedaulatan data dan keamanan sistem, namun menuntut biaya kapital dan operasional yang sangat besar untuk pengadaan perangkat keras, pendingin ruangan, pasokan daya, dan tim pemeliharaan berkala.
- **Model Komputasi Awan Publik (*Public Cloud*)**:
  - Memanfaatkan infrastruktur terdistribusi milik penyedia layanan awan global (seperti AWS, Microsoft Azure, Google Cloud Platform, dan IBM Cloud) yang diakses melalui internet publik.
  - Perangkat keras dibagi bersama pelanggan lain (*multi-tenant*), menawarkan efisiensi biaya luar biasa dan skalabilitas instan.
- **Model Komputasi Awan Privat (*Private Cloud*)**:
  - Infrastruktur awan yang dialokasikan secara eksklusif hanya untuk satu organisasi tunggal. Dapat dioperasikan secara mandiri di lokasi perusahaan atau dikelola oleh penyedia layanan pihak ketiga. Menyediakan tingkat kustomisasi dan privasi yang superior.
- **Model Komputasi Awan Hibrida (*Hybrid Cloud*)**:
  - Mengintegrasikan komputasi awan publik dan privat agar dapat beroperasi secara selaras. Mengoptimalkan keunggulan keduanya: data sangat rahasia disimpan di awan privat, sementara komputasi berbeban dinamis dijalankan di awan publik.

---

## 4. Production Deployment Components

Topologi infrastruktur produksi tingkat N (*N-tier deployment infrastructure*) mengintegrasikan berbagai lapisan perangkat keras dan perangkat lunak di balik perimeter keamanan terpusat.

### A. Alur Arsitektur Berjenjang di Lingkungan Produksi
- **Tingkat Presentasi Luar**: Aplikasi klien pengguna akhir berada di luar perimeter, berinteraksi melalui internet.
- **Dinding Api (*Firewall*)**: Bertindak sebagai pintu gerbang penyaring pertama yang memisahkan jaringan publik dengan jaringan internal korporat.
- **Tingkat Web (*Web Tier*)**: Menerima trafik HTTP/HTTPS yang lolos firewall. Dilengkapi penyeimbang beban web (*Web Load Balancer*) yang mendistribusikan beban ke kluster peladen web (*Web Servers*).
- **Tingkat Aplikasi (*Application Server Tier*)**: Menerima permintaan dinamis dari peladen web. Dilengkapi penyeimbang beban aplikasi atau peladen proksi (*App Load Balancer / Proxy*) yang mendistribusikan beban komputasi ke sejumlah peladen aplikasi (*App Servers*).
- **Tingkat Data (*Data Tier*)**: Lapisan terdalam yang menampung peladen basis data (*Database Server*), umumnya dilengkapi dengan simpul replika ketersediaan tinggi (*High Availability Replica*) untuk mengantisipasi kegagalan perangkat keras.

### B. Komponen Keamanan dan Manajemen Trafik
- **Dinding Api (*Firewall*)**:
  - Perangkat keamanan jaringan yang memantau dan memfilter seluruh lalu lintas keluar-masuk berdasarkan aturan keamanan ketat.
  - Menjadi benteng pelindung perimeter untuk memblokir intrusi peretas, virus, perangkat perusak (*malware*), dan akses tanpa izin ke jaringan privat.
- **Penyeimbang Beban (*Load Balancer*)**:
  - Perangkat atau perangkat lunak yang bertugas mendistribusikan lalu lintas jaringan secara merata ke sekumpulan peladen (*server farm*).
  - Mencegah kelebihan beban (*overload*) pada satu peladen tertentu, memaksimalkan ketersediaan (*availability*), mempercepat responsivitas, dan mengelola jutaan permintaan konkuren secara andal.
- **Peladen Proksi (*Proxy Server*)**:
  - Peladen perantara yang menjembatani komunikasi antar-tingkatan.
  - Berfungsi ganda untuk optimasi performa caching, penyembunyian alamat asal permintaan (*IP obscuring/anonymization*), penanganan enkripsi SSL/TLS, pemindaian malware, hingga penyaringan konten.

### C. Karakteristik Peladen Web, Aplikasi, dan Basis Data
- **Peladen Web (*Web Server*)**:
  - Berfokus mengirimkan konten web statis seperti berkas HTML, lembar gaya CSS, berkas JavaScript, gambar, dan video.
  - Bertugas utama merespons permintaan protokol HTTP/HTTPS yang datang dari peramban web pengguna.
- **Peladen Aplikasi (*Application Server*)**:
  - Menjalankan logika bisnis inti aplikasi di sisi peladen (*server-side code*).
  - Memproses transaksi data, memvalidasi aturan fungsional, dan mengeksekusi komputasi dinamis sebelum berinteraksi dengan tingkat basis data.
- **Peladen Basis Data dan DBMS**:
  - Menyimpan, mengatur, dan mengamankan repositori data terstruktur maupun tidak terstruktur.
  - Dikendalikan oleh Sistem Manajemen Basis Data (*Database Management System / DBMS*) yang menjembatani koneksi antara peladen aplikasi dengan berkas data fisik di media penyimpanan.

---

## 5. Insiders' Viewpoint: Deployment Architecture and Best Practices

Insinyur dan praktisi terkemuka industri berbagi wawasan strategis mengenai faktor-faktor penentu keberhasilan penerapan sistem perangkat lunak di dunia nyata.

### A. Dimensi Skala, Aliran Data, dan Tata Kelola
- **Proyeksi Kapasitas Sejak Dini**:
  - Arsitek wajib memperkirakan skala sistem sejak tahap desain awal: berapa volume pengguna yang akan dilayani, berapa banyak data yang akan diproduksi dan dialirkan, serta seberapa tinggi tingkat pemrosesan data seketika (*real-time data access*) yang dituntut.
- **Strategi Pencatatan dan Privasi Data (*Logging and Privacy*)**:
  - Merancang sistem pencatatan jejak (*logging*) yang komprehensif untuk kebutuhan pemantauan performa internal maupun kepatuhan audit eksternal.
  - Menegakkan tata kelola perlindungan data sensitif pengguna melalui teknik anonimisasi data (*data anonymization*).

### B. Sasaran Tingkat Layanan (Service Level Objectives / SLOs)
- **Mendefinisikan Kesehatan Sistem Secara Kuantitatif**:
  - Tim rekayasa harus menetapkan metrik terukur mengenai apa arti sistem yang sehat dan berkinerja baik sejak awal melalui Sasaran Tingkat Layanan (*Service Level Objectives / SLOs*) dan ketersediaan sistem (*availability targets*).
- **Pemantauan Berkelanjutan dan Rencana Mitigasi**:
  - Memasang sistem telemetri otomatis untuk memantau pemenuhan SLO secara *real-time*, serta menyiapkan prosedur mitigasi darurat yang teruji apabila performa sistem merosot di bawah ambang batas toleransi.

### C. Modularisasi Kode dan Kecepatan Penerapan
- **Menghindari Jebakan Monolitik Raksasa**:
  - Menjaga basis kode agar tetap termodularisasi secara ketat (misalnya melalui arsitektur *microservices*) guna mencegah penumpukan basis kode raksasa yang kaku dan membengkak (*bloated behemoth codebases*).
  - Modularitas tinggi memungkinkan tim rekayasa bekerja secara mandiri, menguji modul lebih cepat, dan merilis pembaruan ke lingkungan produksi dengan siklus iterasi yang singkat.

### D. Disiplin Pengujian dan Penerapan Kenari (Canary Deployment)
- **Fondasi Pengembangan Berbasis Pengujian (*Test-Driven Development / TDD*)**:
  - Pengujian otomatis merupakan bagian paling fundamental dari strategi penerapan perangkat lunak. Praktisi sangat menekankan adopsi TDD sebagai kebiasaan kerja harian bagi setiap insinyur perangkat lunak guna menjamin stabilitas kode.
- **Strategi Penerapan Kenari (*Canary Deployment*)**:
  - Diambil dari analogi burung kenari yang dibawa penambang ke dalam tambang batu bara sebagai pendeteksi dini gas beracun.
  - *Mekanisme Kerja*: Pembaruan kode baru tidak langsung disebarkan ke 100% pengguna, melainkan dialirkan secara bertahap ke sebagian kecil trafik pengguna (misalnya 2% hingga 5%) sembari memantau tingkat galat dan performa sistem.
  - Memungkinkan tim mendeteksi potensi kerusakan fatal secara dini tanpa membahayakan seluruh basis pengguna, didukung oleh kesiapan prosedur pemulihan atau pembatalan rilis kilat (*rapid rollback*).