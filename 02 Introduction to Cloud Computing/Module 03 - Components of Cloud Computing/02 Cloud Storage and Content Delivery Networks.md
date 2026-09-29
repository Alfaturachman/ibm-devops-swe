# Cloud Storage and Content Delivery Networks

Catatan komprehensif ini menyajikan pembahasan mendalam mengenai arsitektur penyimpanan data di lingkungan komputasi awan (*Cloud Storage*) dan jaringan distribusi konten (*Content Delivery Networks* / CDNs). Topik bahasan mencakup taksonomi empat model penyimpanan awan (*Direct Attached*, *File Storage*, *Block Storage*, dan *Object Storage*), konsep performa *Input/Output Operations Per Second* (IOPS), persistensi data, tingkatan kelas objek (*storage tiers*), integrasi *S3-compatible REST API*, optimasi latensi global melalui CDN, hingga pandangan praktisi industri mengenai strategi pemilihan media simpan yang optimal.

---

## 1. Basics of Cloud Storage

### A. Definisi dan Model Operasional Penyimpanan Awan
- Penyimpanan awan (*Cloud Storage*) adalah infrastruktur komputasi untuk menyimpan, mengelola, dan memelihara berkas data digital di pusat data terdistribusi milik penyedia layanan:
  - Penyedia cloud bertanggung jawab penuh atas pengadaan perangkat keras fisik, keamanan fasilitas, pemeliharaan redundansi, penggantian disk yang rusak, dan ketersediaan data (*high availability*).
  - Konsumen dapat memperbesar atau memperkecil kapasitas secara elastis sesuai kebutuhan riil tanpa investasi modal di muka, dengan skema pembayaran berbasis konsumsi kapasitas per gigabita per bulan (*pay-per-gigabyte per month*).
  - Hubungan fundamental antara kinerja dan biaya penyimpanan:

$$
\text{Storage Cost per GB} \propto \text{Read/Write Speed (Throughput \& IOPS)} \propto \frac{1}{\text{Latency}}
$$

### B. Empat Klasifikasi Utama Penyimpanan Awan
- Ringkasan karakteristik empat varian media simpan di cloud:
  - *Direct Attached Storage (Local Storage)*:
    - Media penyimpanan fisik yang terpasang langsung di dalam sasis server fisik (*chassis*) atau di rak yang sama dengan simpul komputasi (*compute node*).
    - Menawarkan kecepatan sangat tinggi, namun bersifat sementara (*ephemeral*), terikat pada satu mesin, dan tidak memiliki ketahanan lintas rak.
  - *File Storage (Network Attached Storage / NFS)*:
    - Penyimpanan berbasis sistem berkas hierarki yang diakses melalui jaringan Ethernet standar.
    - Mendukung pemasangan (*mounting*) bersamaan oleh banyak mesin server (*multi-client concurrent access*).
  - *Block Storage (Storage Area Network / SAN)*:
    - Penyimpanan volume berbasis blok mentah berkecepatan tinggi yang dihubungkan melalui jaringan serat optik (*fibre channel*).
    - Diperlakukan seperti disk internal oleh server dan umumnya hanya dapat dipasang ke satu simpul komputasi pada satu waktu (*single-client mount*).
  - *Object Storage*:
    - Penyimpanan data tak terstruktur yang diakses langsung menggunakan antarmuka pemrograman aplikasi berbasis web (*RESTful API*).
    - Memiliki kapasitas elastis tanpa batas (*effectively infinite*), biaya per gigabita paling murah, namun memiliki latensi akses paling lambat.

### C. Konsep Persistensi, Efemeralitas, dan Snapshot
- Status siklus hidup volume penyimpanan:
  - Penyimpanan Persisten (*Persistent Storage*):
    - Volume penyimpanan dipisahkan secara siklus hidup dari simpul komputasi (*compute node*).
    - Jika mesin virtual dimatikan, dihapus, atau dihentikan (*terminated*), volume penyimpanan beserta seluruh data di dalamnya tetap utuh dan dapat dipasangkan kembali ke mesin virtual lain. Biaya sewa penyimpanan tetap berjalan selama volume belum dihapus secara eksplisit.
  - Penyimpanan Sementara (*Ephemeral Storage*):
    - Volume penyimpanan terikat langsung pada siklus hidup mesin virtual.
    - Saat mesin virtual dimatikan atau dihentikan, volume penyimpanan secara otomatis ikut terhapus permanen dan seluruh data di dalamnya hilang.
- Mekanisme Pencadangan Berbasis *Snapshot*:
  - *Snapshot* adalah salinan citra instan dari volume penyimpanan pada satu titik waktu tertentu (*point-in-time image*).
  - Proses pembuatan *snapshot* berlangsung sangat cepat tanpa memerlukan waktu henti sistem (*zero downtime*), karena sistem penyimpanan cloud hanya mencatat metadata penanda waktu dan delta blok data yang mengalami perubahan (*incremental changes*).
  - Sangat efektif untuk mengembalikan kondisi seluruh volume disk ke keadaan semula jika terjadi kesalahan fatal, namun tidak dirancang untuk memulihkan berkas individual secara parsial.

---

## 2. File Storage

### A. Arsitektur dan Mekanisme Konektivitas
- *File Storage* menyediakan antarmuka penyimpanan berbasis berkas dan direktori hierarkis (pohon folder) yang serupa dengan sistem berkas pada komputer konvensional:
  - Media penyimpanan fisik ditempatkan pada peralatan penyimpanan jarak jauh terdedikasi (*remote storage appliances*) yang dikelola sepenuhnya oleh penyedia cloud.
  - Peralatan ini memiliki redundansi tingkat tinggi dan dilengkapi fitur enkripsi data baik saat transit di jaringan (*encryption in transit*) maupun saat tersimpan di disk (*encryption at rest*).
  - Dihubungkan ke simpul komputasi melalui jaringan Ethernet menggunakan protokol sistem berkas jaringan (*Network File System* / NFS atau *Server Message Block* / SMB).
  - Karakteristik Jaringan Ethernet: Meskipun penyedia cloud merancang jaringan berkapasitas besar, kecepatan transfer data pada jaringan Ethernet dapat berfluktuasi tergantung kepadatan lalu lintas jaringan bersama.

### B. Kemampuan Multi-Mounting dan Kasus Penggunaan
- Keunggulan utama *File Storage* adalah kemampuannya untuk dipasang (*mounted*) secara simultan ke banyak simpul komputasi sekaligus (dapat mencapai 30 hingga 80 server atau lebih):
  - Setiap server melihat volume yang terpasang layaknya kandar (*drive*) lokal bersama.
  - Mendukung operasi pembacaan dan penulisan secara bersamaan (*simultaneous reads and writes*) tanpa risiko kerusakan integritas data.
- Skenario penggunaan ideal untuk *File Storage*:
  - Berbagi Berkas Antar Divisi (*Departmental File Shares*): Ruang kolaborasi dokumen bersama bagi banyak pengguna dan aplikasi.
  - Zona Pendaratan Data (*Landing Zone*): Repositori tempat berkas masuk disimpan untuk kemudian diproses secara paralel oleh beberapa aplikasi pekerja (*worker nodes*).
  - Menghosting Konten Situs Web (*Web Content Repository*): Menyimpan aset gambar, templat, dan berkas statis yang diakses secara serentak oleh beberapa server web di balik *load balancer*.
  - Beban Kerja Campuran Terstruktur dan Tak Terstruktur: Server aplikasi yang mengelola dokumen teks sekaligus media biner.

### C. Pengukuran dan Perhitungan IOPS pada File Storage
- *Input/Output Operations Per Second* (IOPS) merepresentasikan jumlah operasi pembacaan dan penulisan yang mampu diproses oleh disk penyimpanan dalam waktu satu detik:
  - Nilai IOPS ditentukan oleh kemampuan perangkat keras disk penyimpanan yang mendasarinya (misalnya SSD vs HDD), bukan oleh kecepatan bandwidth jaringan penghubungnya.
  - Formula perkiraan kebutuhan IOPS:

$$
\text{IOPS}_{\text{Required}} = \frac{\text{Total I/O Operations}}{\text{Duration in Seconds}} = \frac{N_{\text{nodes}} \times \text{Requests per minute per node}}{60}
$$

  - Contoh Kalkulasi:
    - Sebuah folder berbagi *File Storage* dipasang pada 30 simpul komputasi.
    - Seluruh simpul tersebut secara kumulatif mengeksekusi 60 permintaan baca/tulis per menit:

$$
\text{IOPS}_{\text{Average}} = \frac{60 \text{ operations}}{60 \text{ seconds}} = 1 \text{ IOPS}
$$

  - Pertimbangan Alokasi: IOPS yang terlalu rendah akan memicu antrean proses dan menjadi hambatan performa (*bottleneck*), sedangkan alokasi IOPS yang terlalu berlebihan akan mengakibatkan pemborosan anggaran TI karena tarif sewa berbanding lurus dengan kuota IOPS yang diprovisi.

---

## 3. Block Storage

### A. Arsitektur Blok dan Jaringan Serat Optik
- *Block Storage* bekerja dengan cara memecah data digital menjadi potongan-potongan blok mentah berukuran tetap (*raw chunks of data*), di mana setiap blok diberi alamat pengenal unik (*unique address*) tanpa menyertakan metadata berkas tingkat tinggi:
  - Sistem operasi yang terpasang pada simpul komputasi memiliki kendali penuh atas cara pengelolaan struktur data pada blok-blok tersebut, termasuk penentuan sistem berkas (*file system formatting* seperti ext4, XFS, atau NTFS).
  - Dihubungkan ke simpul komputasi melalui jaringan serat optik khusus (*Storage Area Network* / SAN berbasis Fibre Channel atau iSCSI berkecepatan tinggi).
  - Jaringan serat optik mentransmisikan sinyal dengan kecepatan cahaya, menjamin latensi transmisi ultra rendah (*ultra-low latency*) dan konsistensi kecepatan baca/tulis yang stabil tanpa terpengaruh kemacetan lalu lintas internet umum.

### B. Karakteristik Operasional dan Isolasi Simpul Tunggal
- Karakteristik pembeda utama *Block Storage*:
  - Isolasi Simpul Tunggal (*Single-Node Mount*): Berbeda dengan *File Storage*, sebuah volume *Block Storage* pada umumnya hanya dapat dipasangkan ke tepat satu simpul komputasi pada satu waktu.
  - Redundansi Terintegrasi: Penyedia layanan cloud menerapkan replikasi data otomatis di tingkat volume fisik, sehingga apabila salah satu disk fisik pada rak mengalami kegagalan, data tetap aman dan operasional aplikasi tidak terganggu.
  - Kustomisasi IOPS Dinamis: Pengguna dapat menentukan profil IOPS saat provisi awal dan menyesuaikan nilai IOPS tersebut secara dinamis (*elastic IOPS scaling*) seiring pertumbuhan aktivitas beban kerja aplikasi.

### C. Kasus Penggunaan Ideal Block Storage
- Skenario yang mutlak membutuhkan keunggulan *Block Storage*:
  - Kandar Booting Sistem Operasi (*Boot Volumes*): Menjadi media instalasi sistem operasi untuk mesin virtual (seperti lingkungan klaster VMware ESXi atau KVM), di mana kinerja booting dan integritas sistem sangat diutamakan.
  - Basis Data Transaksional dan Relasional (RDBMS): Sistem perbankan, platform eCommerce, serta mesin basis data (seperti Oracle Database, Microsoft SQL Server, PostgreSQL, MySQL) yang membutuhkan latensi mikrodetik dan ribuan IOPS untuk menjaga konsistensi transaksi ACID.
  - Server Surat Elektronik (*Mail Servers*): Aplikasi perpesanan enterprise yang menjalankan jutaan operasi baca/tulis kecil secara terus-menerus.

---

## 4. Perbandingan Tradisional: File Storage vs Block Storage

### A. Matriks Analisis Arsitektur dan Kinerja
- Perbandingan mendalam berdasarkan penjelasan Amy Blea (IBM Cloud Offering Team):
  - Mekanisme Akses dan Protokol:
    - *File Storage*: Menggunakan protokol tingkat jaringan (NFS/SMB) di atas Ethernet. Menampilkan struktur folder hierarkis terpadu.
    - *Block Storage*: Menggunakan protokol tingkat blok mentah melalui jaringan serat optik (SAN). Menampilkan kandar mentah (*raw drive*).
  - Kemampuan Koneksi Bersama (*Concurrency*):
    - *File Storage*: Mendukung konkurensi tinggi, dapat dipasang ke banyak server (30-80+ simpul) secara bersamaan.
    - *Block Storage*: Khusus dipasang ke satu server tunggal pada satu waktu (*exclusive attachment*).
  - Karakteristik Kinerja dan Latensi:
    - *File Storage*: Kecepatan transfer dapat bervariasi bergantung pada beban jaringan bersama; latensi tingkat menengah.
    - *Block Storage*: Latensi ultra rendah yang sangat konsisten dengan throughput tinggi; performa IOPS terjamin.
  - Struktur Biaya:
    - *File Storage*: Lebih ekonomis karena infrastruktur Ethernet lebih murah untuk dibangun dan dirawat.
    - *Block Storage*: Memiliki titik harga lebih tinggi karena biaya perangkat keras jaringan serat optik yang canggih.

### B. Panduan Pengambilan Keputusan (Decision Rules)
- Gunakan *Block Storage* apabila:
  - Membutuhkan kandar booting OS mesin virtual (*boot disks*).
  - Menjalankan basis data transaksional yang menuntut ribuan IOPS stabil dan latensi ultra rendah.
  - Aplikasi memerlukan kontrol langsung terhadap partisi dan sistem berkas disk.
- Gunakan *File Storage* apabila:
  - Membutuhkan repositori berkas bersama yang diakses oleh banyak pengguna atau simpul komputasi secara bersamaan.
  - Menghosting situs web dengan aset media statis yang dibagikan ke beberapa server web.
  - Mengutamakan efisiensi biaya untuk beban kerja yang tidak membutuhkan kecepatan latensi setinggi serat optik.

---

## 5. Object Storage Overview

### A. Definisi, Konsep Desain, dan Eliminasi Simpul Komputasi
- *Object Storage* adalah paradigma penyimpanan data di mana setiap data disimpan sebagai entitas mandiri yang disebut "Objek" (*Object*), bukan dalam bentuk blok disk mentah ataupun hierarki folder pohon:
  - Eliminasi Ketergantungan Komputasi: *Object Storage* tidak dipasangkan (*attached/mounted*) ke mesin server atau simpul komputasi tertentu. Pengguna dan aplikasi berinteraksi langsung dengan layanan penyimpanan melalui antarmuka web berbasis API (*RESTful HTTP Requests*).
  - Skalabilitas Tanpa Batas (*Effectively Infinite Capacity*): Tidak memerlukan pemesanan kuota ukuran di muka. Pengguna dapat terus mengunggah data dari ukuran bita hingga petabita dan kapasitas akan meluas secara otomatis tanpa batas kepenuhan.
  - Model Pembiayaan Hemat: Biaya penyimpanan per gigabita berkisar beberapa sen dolar AS per bulan, menjadikannya opsi penyimpanan awan paling murah dibandingkan *File* maupun *Block Storage*.

### B. Arsitektur Wadah Datar (Buckets) dan Metadata
- Struktur pengorganisasian data pada *Object Storage*:
  - Struktur Penyimpanan Datar (*Flat Storage Architecture*):
    - Seluruh objek disimpan di dalam wadah terisolasi yang disebut *Bucket*.
    - Berbeda dengan folder direktori pada sistem berkas konvensional, *Bucket* memiliki arsitektur yang sepenuhnya datar: tidak diizinkan membuat wadah di dalam wadah (*buckets cannot be nested inside buckets*).
  - Komposisi Objek:
    - Data Biner: Berkas isi data sebenarnya (teks, gambar, video, arsip zip).
    - Metadata Kustom dan Sistem: Informasi deskriptif komprehensif mengenai data tersebut (seperti *Object ID*, tanggal pembuatan, ukuran, tipe konten MIME, hak akses keamanan, dan tag klasifikasi bisnis).
    - Kunci Pengenal Unik (*Unique Key / Object ID*): Alamat unik berbasis URL yang digunakan oleh aplikasi untuk menemukan dan mengunduh objek dari bucket.
  - Pembatasan Fungsional:
    - *Object Storage* bersifat statis: tidak dapat digunakan untuk mengeksekusi sistem operasi atau menjalankan basis data transaksional aktif.
    - Sifat *Immutable*: Pembaruan pada data objek (meskipun hanya mengubah satu karakter) mengharuskan penulisan dan pengunggahan ulang seluruh objek secara utuh.

### C. Ketahanan Data dan Tingkat Ketersediaan Geografis
- Opsi ketahanan (*resilience*) yang disediakan oleh penyedia cloud:
  - Ketahanan Titik Tunggal (*Single Data Center Resilience*): Objek disimpan dengan redundansi disk di dalam satu fasilitas pusat data. Opsi paling ekonomis, cocok jika data terikat aturan domisili geografis khusus.
  - Ketahanan Lintas Zona (*Cross-Zone / Regional Resilience*): Salinan objek direplikasi secara otomatis ke beberapa *Availability Zones* di dalam satu region komputasi awan.
  - Ketahanan Lintas Wilayah (*Cross-Region Resilience*): Salinan objek didistribusikan ke pusat-pusat data di berbagai belahan negara atau benua yang berbeda, memberikan jaminan ketersediaan data tertinggi terhadap ancaman bencana alam global.

---

## 6. Object Storage Tiers and APIs

### A. Klasifikasi Tingkatan Penyimpanan (Storage Tiers / Classes)
- Penyedia cloud membagi *Object Storage* ke dalam beberapa kelas berdasarkan frekuensi akses data guna mengoptimalkan biaya:
  - Tingkat Standar (*Standard Tier*):
    - Dirancang untuk objek data yang sering diakses (*hot data*).
    - Biaya penyimpanan per gigabita paling tinggi di antara kelas objek, namun tidak dikenakan biaya tambahan saat data diambil atau diunduh (*zero retrieval fees*).
  - Tingkat Brankas (*Vault / Archive Tier*):
    - Dirancang untuk data yang jarang diakses (*warm data*), misalnya berkas laporan yang hanya dibuka 1 hingga 2 kali per bulan.
    - Menawarkan tarif penyimpanan bulanan per gigabita yang lebih murah.
  - Tingkat Brankas Dingin (*Cold Vault / Deep Archive Tier*):
    - Dirancang untuk data arsip kepatuhan hukum yang sangat jarang diakses (*cold data*), misalnya dokumen pajak yang hanya diperiksa 1 kali per tahun.
    - Tarif penyimpanan super murah (hanya sepersekian sen per gigabita per bulan).
    - Kompromi Waktu Pengambilan (*Retrieval Latency*): Data disimpan dalam kondisi luring (*offline*), sehingga proses pemulihan data dari status beku ke status aktif dapat membutuhkan waktu beberapa jam.

### B. Kebijakan Siklus Hidup Otomatis (Lifecycle Management Rules)
- Pengguna dapat mengonfigurasi aturan kebijakan otomatis (*automatic archiving rules*) berbasis metadata:
  - Sebuah objek yang berada di *Standard Tier* secara otomatis dialihkan ke *Vault Tier* setelah 30 hari tidak diakses.
  - Objek tersebut dialihkan kembali ke *Cold Vault Tier* setelah 90 hari, dan dihapus permanen setelah 7 tahun sesuai regulasi retensi perusahaan:

$$
\text{Standard Tier (Hot)} \xrightarrow{t > 30\text{ days}} \text{Vault Tier (Warm)} \xrightarrow{t > 90\text{ days}} \text{Cold Vault (Cold)} \xrightarrow{t > 2555\text{ days}} \text{Purge/Delete}
$$

### C. Antarmuka Pemrograman Aplikasi (S3-Compatible APIs)
- Mekanisme integrasi sistem dengan *Object Storage*:
  - Standar Industri De Facto: Mayoritas penyedia cloud mengadopsi standar *S3-compatible API* (yang awalnya dipelopori oleh Amazon S3).
  - Berbasis Layanan Web RESTful HTTP:
    - Metode `PUT`: Mengunggah objek baru atau membuat bucket.
    - Metode `GET`: Mengunduh berkas objek atau membaca metadata.
    - Metode `DELETE`: Menghapus objek dari wadah penyimpanan.
  - Mencegah Keterikatan Vendor (*Vendor Agnostic*): Pengembang dapat menulis basis kode program tunggal yang mampu berinteraksi dengan berbagai layanan *Object Storage* dari vendor berbeda (seperti IBM Cloud Object Storage, AWS S3, Google Cloud Storage, atau MinIO privat).
  - Modernisasi Pemulihan Bencana (*Disaster Recovery*): Menggantikan teknologi pita magnetik fisik (*tape backup*) tradisional yang memakan waktu dan rentan aus, mempercepat waktu pemulihan data perusahaan secara signifikan.

---

## 7. Content Delivery Networks (CDNs)

### A. Definisi dan Analisis Masalah Latensi Global
- *Content Delivery Network* (CDN) adalah jaringan server terdistribusi secara geografis yang bertugas mempercepat pengiriman konten web dengan menyajikan salinan data statis sementara (*cached copies*) dari lokasi yang paling dekat dengan pengguna akhir.
- Studi Kasus Ryan Sumner (Chief Network Architect, IBM Cloud):
  - Sebuah server aplikasi web ditempatkan di satu pusat data tunggal di kota Dallas, Amerika Serikat.
  - Terdapat pengguna global yang tersebar di berbagai belahan dunia mengakses situs web tersebut:
    - Pengguna di Sydney (Australia): Menempuh jarak pulang-pergi sekitar $17.200\text{ mil}$ ($8.600\text{ mil}$ pergi, $8.600\text{ mil}$ pulang), menghasilkan waktu bolak-balik (*round-trip latency*) sekitar $170\text{ milidetik}$.
    - Pengguna di London (Inggris): Menghasilkan latensi bolak-balik sekitar $100\text{ milidetik}$.
    - Pengguna di New York City: Menghasilkan latensi bolak-balik sekitar $40\text{ milidetik}$.
    - Pengguna di Los Angeles: Menghasilkan latensi bolak-balik sekitar $30\text{ milidetik}$.
- Prinsip Kecepatan CDN: Semakin jauh jarak fisik antara server asal (*origin server*) dan pengguna, semakin lambat performa pemuatan situs web. CDN mengatasi kendala ini dengan menempatkan titik kehadiran (*Points of Presence* / PoP atau *Edge Servers*) di berbagai kota besar di seluruh dunia.

### B. Cara Kerja Penyaluran Konten dan Titik Kehadiran (PoP)
- Alur kerja pendistribusian konten melalui CDN:
  - Permintaan Pertama: Ketika seorang pengguna di Sydney mengakses gambar pada situs web untuk pertama kalinya, jaringan CDN menarik berkas gambar tersebut dari server asal di Dallas dan menyimpannya di server *edge* terdekat di Sydney.
  - Permintaan Berikutnya: Seluruh pengguna lain di wilayah Australia dan Asia Pasifik akan langsung disajikan salinan gambar dari server *edge* lokal di Sydney dalam hitungan milidetik, tanpa perlu lagi melakukan perjalanan jaringan ribuan mil ke Dallas.

### C. Keuntungan Langsung dan Tidak Langsung Penggunaan CDN
- Keuntungan Langsung (*Direct Benefit*):
  - Peningkatan Kecepatan Akses (*Website Acceleration*): Memangkas waktu pemuatan halaman web dari ratusan milidetik menjadi hitungan detik pecahan terkecil.
- Tiga Keuntungan Tidak Langsung (*Indirect Benefits*):
  - Penurunan Beban Server Asal (*Offloading Origin Server Capacity*): Karena sebagian besar konten statis dilayani langsung oleh server CDN, trafik yang mencapai server asal di Dallas berkurang drastis, sehingga menghemat biaya kapasitas komputasi server.
  - Peningkatan Ketersediaan dan Waktu Aktif (*Increased Uptime*): Beban kerja yang ringan menjaga kestabilan server asal, mencegah sistem mengalami *crash* saat terjadi lonjakan trafik pengunjung mendadak.
  - Keamanan Melalui Pengaburan (*Security through Obscurity & DDoS Mitigation*): Pengguna akhir tidak pernah berkomunikasi langsung dengan alamat IP server asal, melainkan hanya berinteraksi dengan server proksi CDN. Hal ini melindungi infrastruktur internal dari serangan penolakan layanan terdistribusi (*Distributed Denial of Service* / DDoS).

---

## 8. Expert Viewpoints: Cloud Storage Selection Framework

### A. Kerangka Kerja Pengambilan Keputusan Praktisi
- Tiga parameter utama evaluasi pemilihan penyimpanan menurut para profesional cloud:
  - Biaya Menyeluruh (*Total Cost*): Meliputi biaya penyimpanan kapasitas per gigabita, frekuensi panggilan API, serta biaya penarikan data (*data egress / retrieval fees*).
  - Kecepatan dan Kinerja (*Performance & IOPS*): Kebutuhan throughput pembacaan dan penulisan, kecepatan bus data, serta batas toleransi latensi aplikasi.
  - Durasi dan Ketersediaan (*Availability & Lifecycle*): Kebijakan retensi data, immutabilitas data (pencegahan modifikasi berkas), enkripsi (*at rest & in flight*), dan otomatisasi penghapusan data lama.

### B. Matriks Sintesis Pemilihan Media Simpan Awan
- Ringkasan panduan memilih media simpan:
  - *Direct Attached Storage*:
    - Karakteristik: Paling cepat, terpasang lokal, sifatnya efemeral.
    - Rekomendasi Penggunaan: Kandar sistem operasi sementara (*swap space* / *scratch disks*).
  - *Block Storage*:
    - Karakteristik: Sangat cepat, latensi ultra rendah berbasis serat optik, IOPS tinggi, satu simpul per volume.
    - Rekomendasi Penggunaan: Kandar boot VM produksi, basis data transaksional (SQL/NoSQL berkinerja tinggi).
  - *File Storage*:
    - Karakteristik: Kecepatan menengah berbasis Ethernet, hierarki direktori familiar, dapat dipasang bersamaan ke banyak server (*multi-client*).
    - Rekomendasi Penggunaan: Kandar berbagi departemen, media hosting web bersama, *landing zone* pemrosesan data.
  - *Object Storage*:
    - Karakteristik: Kapasitas elastis tanpa batas, biaya termurah, akses via REST API, lambat untuk modifikasi parsial.
    - Rekomendasi Penggunaan: Arsip data statis, video streaming, citra VM, log audit, pencadangan dan pemulihan bencana (*Disaster Recovery*).
  - *Content Delivery Network (CDN)*:
    - Karakteristik: Jaringan server cache terdistribusi global yang terintegrasi dengan penyimpanan objek dan server web.
    - Rekomendasi Penggunaan: Akselerasi konten web multimedia, proteksi DDoS, optimalisasi pengalaman pengguna global.

---

## 9. Rangkuman Pelajaran (Storage and CDN Summary)

### A. Poin-Poin Kunci Pembelajaran
- Penyimpanan awan terbagi menjadi empat model utama: *Direct Attached*, *File Storage*, *Block Storage*, dan *Object Storage*, yang masing-masing memiliki kompromi unik antara kecepatan baca/tulis, arsitektur koneksi, kapasitas, dan biaya.
- *File Storage* menggunakan protokol NFS di atas jaringan Ethernet, ideal untuk kebutuhan berbagi berkas yang dapat diakses secara simultan oleh banyak mesin server.
- *Block Storage* menggunakan jaringan serat optik SAN berkinerja tinggi dengan latensi terendah, dirancang khusus untuk beban kerja transaksional intensif IOPS seperti basis data.
- *Object Storage* mengabstraksi perangkat keras secara total melalui API web HTTP, menyediakan ruang simpan elastis tanpa batas untuk data tak terstruktur dengan efisiensi biaya tertinggi.
- CDN melengkapi ekosistem penyimpanan cloud dengan mendistribusikan salinan konten statis ke server-server tepi terdekat dengan pengguna, memangkas latensi geografis, meringankan beban server asal, dan memperkuat pertahanan keamanan infrastruktur.