# Case Study: Modernizing a Food Delivery Service with Cloud Architecture

Dokumen ini menyajikan studi kasus komprehensif mengenai strategi modernisasi arsitektur sistem pengiriman makanan daring "DineEase". Pembahasan mengulas dekomposisi sistem monolitik warisan menjadi arsitektur komputasi awan berbasis layanan mikro (*microservices*), identifikasi kelemahan performa dan hambatan operasional basis data relasional mandiri, pemetaan solusi arsitektur target pada ekosistem IBM Cloud, serta penentuan sembilan komponen cloud enterprise kunci yang mencakup ketersediaan multi-zona, peladen fisik terdedikasi (*Bare Metal*), orkestrasi kontainer, gerbang API, basis data NoSQL dokumen (IBM Cloudant), basis data relasional terkelola (IBM Db2), jaringan penyalur konten (CDN), penyeimbang beban (*Load Balancer*), dan observabilitas terpadu (*Cloud Monitoring*).

---

## 1. Business Context and Monolith Architecture

### A. Gambaran Bisnis DineEase
- **Model Operasional Platform:**
  - DineEase adalah platform layanan pemesanan dan pengantaran makanan daring yang melayani dua kelompok persona utama:
    - *Konsumen Akhir (Consumers)*: Menggunakan aplikasi seluler untuk menjelajahi menu restoran, melakukan pemesanan makanan, membayar transaksi, dan melacak kurir pengantaran secara waktu nyata.
    - *Pengguna Administratif dan Restoran (Back-Office Users)*: Menggunakan aplikasi web untuk mengelola katalog menu, memantau pesanan masuk, mengelola laporan akuntansi, dan memverifikasi pencairan dana kemitraan.
- **Alur Transaksi Inti:**
  - Konsumen memilih restoran dan menambahkan hidangan ke keranjang belanja.
  - Modul pemesanan memproses rincian transaksi dan modul pembayaran menagih dana dari metode pembayaran konsumen.
  - Rincian pesanan diteruskan secara instan ke dapur restoran untuk dimasak.
  - Sistem mengoordinasikan mitra kurir pengantar (*delivery partners*) agar tiba tepat saat makanan selesai dikemas, menjamin makanan sampai dalam kondisi hangat tanpa waktu tunggu yang berlebihan.

### B. Komponen Fungsional Aplikasi Monolitik
Sebelum proses modernisasi, seluruh logika bisnis DineEase disatukan ke dalam satu basis kode aplikasi monolitik yang mencakup lima modul fungsional:

- **1. Modul Menu (Menu Service):**
  - Mengelola data katalog menu restoran, deskripsi hidangan, gambar makanan, harga satuan, dan pengelompokan kategori (seperti hidangan pembuka, hidangan utama, dan hidangan penutup).
- **2. Modul Penetapan Harga (Dynamic Pricing Service):**
  - Menerapkan kalkulasi harga dinamis berdasarkan lokasi geografis konsumen, riwayat loyalitas pesanan, hari libur nasional, akhir pekan, kondisi cuaca, atau momen acara perayaan tertentu.
  - Menyediakan titik pembaruan terpusat sehingga perubahan tarif oleh mitra restoran langsung tersinkronisasi ke seluruh antarmuka secara waktu nyata.
- **3. Modul Pemesanan (Ordering Service):**
  - Gerbang penerimaan dan pemrosesan transaksi pesanan yang memastikan kelancaran alur pemesanan dari sisi konsumen hingga konfirmasi pihak dapur restoran.
- **4. Modul Pembayaran (Payment Service):**
  - Memproses pembayaran digital secara terenkripsi, memvalidasi otentikasi perbankan, menjalankan deteksi potensi penipuan (*fraud checks*), serta mengintegrasikan sistem dengan mesin kasir fisik (*Point of Sales* / POS).
- **5. Modul Pengantaran (Dispatch and Tracking Service):**
  - Mengatur penugasan kurir terdekat, menyinkronkan waktu kesiapan makanan dengan waktu kedatangan kurir, serta menyajikan estimasi waktu tiba (*Estimated Time of Arrival* / ETA) melalui pelacakan peta interaktif.

### C. Basis Data Relasional Mandiri dan Keterbatasannya
- **Model Relasional Tradisional (E.F. Codd, 1970):**
  - Seluruh data transaksi, pengguna, menu, ulasan, dan catatan akuntansi disimpan dalam basis data relasional yang dikelola sendiri (*self-managed RDBMS*) di server lokal.
  - Memanfaatkan tabel yang terhubung melalui relasi kunci primer (*primary key*) dan kunci asing (*foreign key*) dengan jaminan integritas data ACID (*Atomicity, Consistency, Isolation, Durability*).
- **Tantangan Operasional Monolitik:**
  - *Keterbatasan Penskalaan Parsial (Selective Scalability Failure)*:
    - Modul Pemesanan tidak dapat diskalakan secara terisolasi saat terjadi lonjakan pesanan musiman pada momen perayaan besar, memaksa penskalaan seluruh monolitik yang sangat boros sumber daya.
  - *Latensi Tinggi pada Modul Dispatch*:
    - Kurir membutuhkan pembaruan status berlatensi ultra-rendah, namun latensi jaringan terhambat oleh keterikatan modul pada pusat data tunggal yang jauh dari jangkauan regional.
  - *Kemacetan Beban Komputasi Pembayaran*:
    - Pemeriksaan deteksi penipuan (*fraud detection algorithms*) membutuhkan daya komputasi CPU dan GPU intensif secara instan, namun terhambat karena berbagi sumber daya dengan modul penjelajahan menu biasa.
  - *Penurunan Performa Operasi Baca (Read Bottleneck on Reviews)*:
    - Sebelum memesan, konsumen selalu membaca ulasan dan peringkat bintang restoran. Operasi penggabungan relasional (*JOIN queries*) antara tabel Restoran, Ulasan, dan Peringkat menjadi sangat lambat seiring membengkaknya volume baris data.
  - *Beban Pemeliharaan Administratif Basis Data*:
    - Pengelolaan mandiri mencakup pencadangan manual, instalasi penambalan keamanan (*patching*), serta penanganan replikasi toleransi kegagalan (*HADR*) yang memakan lebih dari 60% waktu tim rekayasa perangkat lunak.

---

## 2. Target Architecture: DineEase 2.0 on IBM Cloud

### A. Prinsip Arsitektur Berbasis Layanan Mikro (Microservices Architecture)
- **Karakteristik Arsitektur Sasaran:**
  - Memecah blok monolitik menjadi layanan-layanan independen yang terkopel longgar (*loosely coupled*).
  - Setiap layanan mikro memiliki siklus hidup pengembangan dan penerapan mandiri (*independent CI/CD pipeline*).
  - Mengadopsi prinsip persistensi poliglota (*polyglot persistence*), di mana setiap layanan bebas menggunakan jenis basis data yang paling optimal untuk karakteristik beban kerjanya (basis data relasional untuk transaksi keuangan dan basis data dokumen NoSQL untuk ulasan konsumen).
  - Komunikasi antarlayanan berlangsung secara aman melalui panggilan REST APIs, protokol perpesanan asinkron (*message brokers*), dan penstriman peristiwa (*event streaming*).

---

## 3. Recommended Cloud Architecture and Service Mapping

### A. Ketersediaan Tinggi dan Latensi Rendah (Low Latency and High Availability)
- **Analisis Kebutuhan Arsitektur:**
  - Layanan *Dispatch* dan pembaruan kurir membutuhkan waktu respons instan dengan jaminan Perjanjian Tingkat Layanan ketersediaan tinggi:

$$
\text{Ketersediaan Sistem (Target SLA)} \ge 99,99\% \quad (\text{Maksimal Toleransi Gangguan} < 52,6 \text{ menit/tahun})
$$

  - Sistem wajib memiliki redundansi pada lokasi fisik terpisah di dalam satu kawasan geografis guna mencegah kelumpuhan akibat bencana di satu pusat data fisik.
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Cloud Multizone Regions (MZR):**
    - Menyebarkan layanan mikro ke dalam arsitektur wilayah multi-zona (MZR).
    - Terdiri dari tiga zona ketersediaan (*Availability Zones*) fisik yang terisolasi secara mandiri dalam satu wilayah metropolitan, masing-masing dilengkapi sistem pendingin, pasokan listrik, dan koneksi jaringan independen dengan latensi antar-zona kurang dari dua milidetik (< 2 ms).

### B. Beban Kerja Terdedikasi Berkinerja Ekstrem (Dedicated Compute for Payments)
- **Analisis Kebutuhan Arsitektur:**
  - Pemrosesan pembayaran dan algoritma deteksi penipuan (*fraud detection*) membutuhkan komputasi berkecepatan tinggi, keamanan isolasi fisik mutlak, tanpa berbagi sumber daya CPU atau RAM dengan penyewa lain (*no multi-tenant noisy neighbors*), serta dukungan akselerasi grafis GPU.
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Cloud Bare Metal Servers (dengan Akselerator GPU):**
    - Menyediakan peladen fisik tunggal terdedikasi (*single-tenant physical servers*) tanpa lapisan overhead virtualisasi (*hypervisor*).
    - Memberikan akses perangkat keras langsung ke prosesor multi-core berkecepatan tinggi dan kartu grafis GPU Nvidia untuk memproses model inferensi deteksi penipuan secara instan dan memenuhi standar kepatuhan PCI-DSS.

### C. Layanan Mikro Berbasis API yang Elastis (Containerized Microservices)
- **Analisis Kebutuhan Arsitektur:**
  - Layanan Pencarian (*Search*), Katalog Menu (*Menu*), dan Penetapan Harga (*Pricing*) perlu dibangun dengan tumpukan teknologi poliglota yang ringan, portabel, mampu memulihkan diri secara otomatis saat gagal (*self-healing*), serta melakukan penskalaan dinamis saat menerima lonjakan panggilan HTTP REST API.
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Cloud Kubernetes Service (IKS) / Red Hat OpenShift on IBM Cloud:**
    - Menyediakan platform orkestrasi kontainer terkelola (*managed container orchestration*) yang memfasilitasi pengemasan layanan mikro ke dalam kontainer Docker.
    - Mengatur penskalaan horizontal otomatis (*Horizontal Pod Autoscaling*) dan pemulihan instans kontainer yang rusak tanpa intervensi manual.
    - *Alternatif Serverless*: **IBM Cloud Code Engine** untuk layanan mikro yang memerlukan penskalaan elastis langsung hingga ke nol (*scale-to-zero*) saat lalu lintas sepi.

### D. Lapisan Gerbang Komunikasi dan Perutean (API Gateway)
- **Analisis Kebutuhan Arsitektur:**
  - Diperlukan satu titik masuk terpusat (*single entry point*) yang menjembatani komunikasi antara aplikasi seluler konsumen, aplikasi web back-office, dan sistem mitra eksternal dengan puluhan layanan mikro internal.
  - Berfungsi mengarahkan permintaan (*request routing*) berdasarkan peta rute URL, melakukan pembatasan kuota panggilan (*rate limiting*), serta mengelola otentikasi token keamanan.
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM API Connect / IBM Cloud API Gateway:**
    - Mengabstraksi arsitektur internal layanan mikro dari konsumsi publik, menerapkan kebijakan keamanan terpusat (OAuth 2.0 / JWT), dan membagi beban kueri secara cerdas ke titik akhir layanan mikro yang sesuai.

### E. Optimalisasi Performa Baca Ulasan (Document-Based Database)
- **Analisis Kebutuhan Arsitektur:**
  - Pembacaan data ulasan dan rating restoran membutuhkan format fleksibel yang mampu menampung data semi-terstruktur berformat JSON tanpa operasi relasional *JOIN* yang lambat.
  - Membutuhkan arsitektur *offline-first* agar ulasan tetap dapat diakses di ponsel konsumen saat koneksi internet tidak stabil.
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Cloudant:**
    - Basis data dokumen NoSQL terkelola penuh yang dibangun di atas mesin Apache CouchDB.
    - Menyimpan dokumen dalam format JSON hierarkis mandiri, memungkinkan pembacaan indeks ulasan dan rating dalam hitungan milidetik.
    - Memiliki kapabilitas sinkronisasi data bawaan (*built-in bidirectional sync*) yang mendukung pustaka PouchDB pada aplikasi seluler konsumen untuk pengalaman *offline-first*.

### F. Basis Data Transaksional Terkelola Penuh (Managed Relational Database)
- **Analisis Kebutuhan Arsitektur:**
  - Modul Pemesanan dan Akuntansi membutuhkan basis data relasional terkelola penuh (*Database-as-a-Service* / DBaaS) yang menjamin kepatuhan transaksi ACID, pemulihan bencana otomatis (*High-Availability Disaster Recovery* / HADR), pemrosesan kueri analitik transaksional online (*OLTP*) berkecepatan tinggi, dan penskalaan kapasitas disk tanpa gangguan.
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Db2 on Cloud (atau IBM Cloud Databases for PostgreSQL):**
    - Layanan basis data relasional enterprise terkelola yang menyediakan fitur ketersediaan tinggi HADR multi-zona dengan failover otomatis tanpa kehilangan data.
    - Menghilangkan 100% beban administratif rutin (pencadangan otomatis, enkripsi data *at rest*, dan instalasi patch keamanan).

### G. Penyaluran Media Cepat dan Caching Global (Content Delivery Network)
- **Analisis Kebutuhan Arsitektur:**
  - DineEase memiliki ratusan ribu foto makanan beresolusi tinggi, logo mitra restoran, dan aset grafis statis yang memperberat kerja peladen aplikasi jika disajikan langsung dari server web utama.
  - Diperlukan solusi untuk menyalurkan aset dari simpul geografis terdekat ke pengguna, melakukan kompresi berkas otomatis, dan menyajikan tembolok (*caching*).
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Cloud Content Delivery Network (CDN):**
    - Mendistribusikan aset statis ke ratusan titik kehadiran (*Points of Presence* / PoPs) di seluruh dunia (didukung kemitraan jaringan Akamai).
    - Memangkas jarak tempuh data (*latency reduction*), mengurangi beban transfer data ke server asal (*origin offload*), dan mengadaptasi resolusi gambar sesuai tipe layar perangkat konsumen.

### H. Peningkatan Ketersediaan dan Penyeimbangan Beban (Load Balancing)
- **Analisis Kebutuhan Arsitektur:**
  - Mendistribusikan lalu lintas lalu lintas masuk secara merata ke puluhan replika instans layanan mikro yang berjalan di zona-zona berbeda.
  - Melakukan uji kesehatan (*health checks*) berkala dan secara transparan mengalihkan lalu lintas dari instans yang gagal ke instans yang sehat.
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Cloud Load Balancer / IBM Cloud Internet Services (CIS) Global Load Balancer:**
    - Menyediakan penyeimbangan beban lalu lintas aplikasi pada Lapisan 4 (TCP/UDP) dan Lapisan 7 (HTTP/HTTPS) dengan kemampuan failover lintas zona ketersediaan secara mulus (*zero downtime*).

### I. Observabilitas dan Pemantauan Kesehatan Operasional (Cloud Monitoring)
- **Analisis Kebutuhan Arsitektur:**
  - Ekosistem layanan mikro terdistribusi memerlukan visibilitas operasional terpusat untuk memantau metrik performa CPU, memori, latensi jaringan, penelusuran kesalahan transaksi, serta pembuatan dasbor visual dan peringatan dini otomatis (*proactive alerts*).
- **Rekomendasi Layanan IBM Cloud:**
  - **IBM Cloud Monitoring (didukung oleh Sysdig) dan IBM Cloud Log Analysis:**
    - Memberikan visibilitas mendalam ke dalam klaster Kubernetes, kontainer kontainer aktif, dan panggilan API.
    - Memfasilitasi pembuatan dasbor kustom pemantauan KPI bisnis (seperti jumlah pesanan per detik dan tingkat kegagalan pembayaran) serta pemicu peringatan otomatis via surel atau Slack saat ambang batas bahaya terlampaui.

---

## 4. Architectural Synthesis and Key Takeaways

### A. Rangkuman Pemetaan Solusi Arsitektur DineEase 2.0
- **Infrastruktur Multi-Zona:** IBM Cloud Multizone Regions menjamin SLA ketersediaan 99,99% dan latensi rendah untuk layanan pengantaran (*Dispatch*).
- **Komputasi Khusus Terisolasi:** IBM Cloud Bare Metal dengan GPU menjamin pemrosesan transaksi pembayaran dan verifikasi anti-fraud dengan keamanan fisik penuh.
- **Kontainer dan Gerbang Terpusat:** IBM Cloud Kubernetes Service dan IBM API Connect menyajikan fleksibilitas layanan mikro poliglota yang terukur dan terkelola secara aman.
- **Strategi Basis Data Terpadu:** Penggabungan IBM Cloudant (NoSQL Dokumen untuk ulasan konsumen cepat) dan IBM Db2 on Cloud (RDBMS terkelola untuk konsistensi transaksi pesanan) mengoptimalkan performa baca dan integritas data secara bersamaan.
- **Penyaluran Konten dan Penyeimbangan Beban:** Integrasi IBM Cloud CDN dan IBM Cloud Load Balancer meminimalkan latensi aset multimedia dan menjamin toleransi kesalahan instans.
- **Observabilitas Menyeluruh:** IBM Cloud Monitoring memastikan stabilitas operasional melalui pemantauan telemetri waktu nyata dan penanganan anomali dini.

### B. Evaluasi Manfaat Bisnis dan Efisiensi Operasional
- **Eliminasi Titik Kegagalan Tunggal (*Single Point of Failure*):** Arsitektur terdistribusi multi-zona mengisolasi kegagalan modul sehingga gangguan pada satu layanan mikro (misalnya penjelajahan menu) tidak melumpuhkan pemrosesan pesanan yang sedang berjalan.
- **Optimasi Efisiensi Biaya (*TCO Optimization*):** Pendekatan nirserver (*scale-to-zero*) dan penskalaan horizontal otomatis mengeliminasi pemborosan kapasitas komputasi pada jam-jam sepi transaksi.
- **Peningkatan Pengalaman Pelanggan (*Customer Experience*):** Kombinasi CDN global dan latensi rendah antarzona (< 2 ms) memastikan antarmuka seluler konsumen tetap responsif bahkan saat jam sibuk promosi makanan.
- **Fokus Rekayasa pada Nilai Tambah Bisnis:** Pengalihan beban pemeliharaan basis data ke model terkelola (*DBaaS*) membebaskan tim rekayasa perangkat lunak untuk berkonsentrasi pada pengembangan fitur baru daripada pemeliharaan infrastruktur rutin.
