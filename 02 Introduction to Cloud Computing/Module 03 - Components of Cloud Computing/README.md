# Module 03: Components of Cloud Computing

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 03: Components of Cloud Computing pada kursus Introduction to Cloud Computing, mencakup analisis mendalam mengenai arsitektur fisik pusat data, klasifikasi hypervisor dan mesin virtual, keunggulan server Bare Metal, karakteristik tiga pilar penyimpanan awan (File, Block, dan Object Storage), tingkatan penyimpanan dan kebijakan siklus hidup data, serta jaringan penyalur konten (Content Delivery Networks / CDNs).

---

### Ringkasan Konsep Inti

- **Hierarki Geografis dan Infrastruktur Fisik:**
  - **Pusat Data (Data Centers):** Gedung fisik yang menampung ribuan rak server, catu daya redundan (UPS dan generator diesel), kontrol pendingin presisi (HVAC), serta keamanan biometrik berlapis.
  - **Zona Ketersediaan (Availability Zones / AZs):** Satu atau lebih pusat data fisik terisolasi dalam satu kawasan yang dihubungkan melalui jaringan serat optik latensi ultra-rendah (< 2 ms).
  - **Wilayah Geografis (Regions):** Wilayah geografis mandiri (seperti US-East atau EU-Central) yang menampung minimal dua hingga tiga zona ketersediaan guna menjamin toleransi bencana (*fault tolerance*).
- **Virtualisasi dan Klasifikasi Hypervisor:**
  - **Type 1 Hypervisor (Bare-Metal):** Berjalan langsung di atas perangkat keras fisik tanpa sistem operasi perantara (contoh: VMware ESXi, KVM, Xen, Microsoft Hyper-V). Memberikan efisiensi performa dan isolasi tertinggi untuk lingkungan cloud enterprise.
  - **Type 2 Hypervisor (Hosted):** Berjalan sebagai aplikasi perangkat lunak di atas sistem operasi host (contoh: Oracle VirtualBox, VMware Workstation). Umumnya digunakan untuk pengujian lokal di komputer pengembang.
- **Tiga Pilar Penyimpanan Awan (Cloud Storage Triad):**
  - **File Storage:** Penyimpanan berbasis sistem berkas hierarki pohon direktori (NFS/SMB) yang mendukung pemasangan bersamaan oleh banyak mesin virtual (*multi-mount capability*).
  - **Block Storage:** Penyimpanan data mentah berkinerja tinggi yang dibagi menjadi blok-blok berukuran tetap dan dihubungkan secara eksklusif ke satu instans komputasi (*single-tenant attach*).
  - **Object Storage:** Penyimpanan berbasis wadah datar (*flat buckets*) yang mengemas data bersama metadata terperinci dan pengenal unik global (*GUID*), dapat diakses langsung melalui internet via API RESTful (kompatibel AWS S3) dengan skalabilitas tak terbatas.

---

### Metodologi dan Arsitektur Teknis

- **Pilihan Komputasi Mesin Virtual vs Bare Metal:**
  - **Shared / Public VMs:** Mesin virtual multi-tenant hemat biaya yang berbagi sumber daya perangkat keras fisik dengan pengguna lain.
  - **Transient / Spot VMs:** Pemanfaatan kapasitas menganggur penyedia cloud dengan potongan harga hingga 80%, namun dapat diambil alih kembali oleh sistem sewaktu-waktu.
  - **Reserved Instances:** Komitmen sewa jangka panjang (1 hingga 3 tahun) untuk beban kerja stabil yang memberikan penghematan biaya signifikan.
  - **Dedicated Hosts:** Peladen fisik tunggal yang didedikasikan untuk satu organisasi, menjamin isolasi penuh untuk kepatuhan regulasi dan lisensi perangkat lunak khusus.
  - **Bare Metal Servers:** Akses langsung ke seluruh perangkat keras server fisik tanpa hypervisor, menawarkan performa CPU/RAM 100% mentah dan dukungan kartu akselerator GPU untuk komputasi kinerja tinggi (HPC).
- **Matriks Analisis Kinerja File vs Block Storage:**
  - **Konektivitas:** File Storage menggunakan Ethernet TCP/IP; Block Storage menggunakan Storage Area Network (SAN) melalui Fibre Channel berlatensi ultra-rendah.
  - **Karakteristik Akses:** File Storage bersifat *read/write many* (RWX); Block Storage bersifat *read/write once* (RWO) untuk satu simpul komputasi.
  - **Pengukuran IOPS:** Kinerja IOPS pada File Storage dipengaruhi oleh ukuran berkas dan beban antrean kueri jaringan, sedangkan Block Storage memberikan jaminan alokasi IOPS tetap (*provisioned IOPS*).
- **Tingkatan Penyimpanan Objek dan Siklus Hidup Otomatis (Lifecycle Management):**
  - **Standard Tier:** Data yang sering diakses setiap hari (biaya simpan tinggi, biaya akses nol).
  - **Cool / Infrequent Access:** Data yang diakses kurang dari sebulan sekali.
  - **Cold Tier:** Data yang jarang diakses (diakses sekali dalam 90 hari).
  - **Archive / Glacier Tier:** Data kepatuhan hukum jangka panjang yang jarang diakses (waktu penarikan kembali beberapa jam, biaya simpan sangat murah).
  - **Lifecycle Rules:** Kebijakan deklaratif otomatis yang memindahkan objek data dari tingkatan panas (*Standard*) ke tingkatan dingin (*Cold/Archive*) setelah melampaui rentang hari tertentu, memangkas biaya penyimpanan hingga lebih dari 70%.

---

### Studi Kasus dan Pembelajaran Industri

- **Pemilihan Media Simpan Berdasarkan Kasus Penggunaan:**
  - **Block Storage:** Menjadi pilihan mutlak untuk instalasi sistem operasi boot disk, basis data transaksional terdistribusi (PostgreSQL, Oracle, SQL Server), dan sistem file performa tinggi.
  - **File Storage:** Sangat cocok untuk repositori berkas kolaboratif bersama, sistem manajemen konten (CMS WordPress / Drupal), dan direktori bersama klaster kontainer.
  - **Object Storage:** Fondasi utama untuk *data lake*, arsip cadangan jangka panjang (*backups*), penampung data telemetri IoT, serta distribusi berkas multimedia massal.
- **Content Delivery Networks (CDNs) dan Penanggulangan Latensi Global:**
  - **Masalah Latensi Jaringan:** Jarak transmisi data yang jauh melintasi benua dan banyaknya simpul perutean jaringan (*network hops*) memperlambat waktu pemuatan situs web.
  - **Mekanisme Titik Kehadiran (Points of Presence / PoPs):** Jaringan CDN menempatkan server tembolok (*edge cache*) di ratusan lokasi kota di seluruh dunia.
  - **Keuntungan Terukur CDN:**
    - Memangkas latensi dengan menyajikan konten statis (gambar, video, skrip) dari peladen terdekat ke pengguna.
    - Mengurangi beban kerja peladen utama (*origin offload*) hingga lebih dari 80%.
    - Memberikan perlindungan terintegrasi terhadap serangan siber DDoS pada lapisan aplikasi web.
