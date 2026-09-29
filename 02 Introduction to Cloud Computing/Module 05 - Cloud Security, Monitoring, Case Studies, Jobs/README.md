# Module 05: Cloud Security, Monitoring, Case Studies, Jobs

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 05: Cloud Security, Monitoring, Case Studies, Jobs pada kursus Introduction to Cloud Computing, mencakup analisis lanskap ancaman siber cloud, model tanggung jawab bersama pada keamanan, prinsip hak istimewa terkecil (PoLP) dan federasi identitas IAM, enkripsi tiga status data dan manajemen kunci KMS, observabilitas sistem dan pelacakan panggilan API audit, lima studi kasus transformasi enterprise terkemuka, serta analisis pasar tenaga kerja dan profil karir spesialisasi cloud.

---

### Ringkasan Konsep Inti

- **Lanskap Ancaman dan Tanggung Jawab Bersama:**
  - Meskipun penyedia cloud menjamin keamanan fasilitas fisik pusat data, pengelolaan keamanan data, konfigurasi akses, dan integritas aplikasi tetap menjadi tanggung jawab penuh organisasi pengguna (*shared responsibility*).
  - Spektrum ancaman siber utama mencakup ancaman orang dalam (*insider threats*), serangan penolakan layanan terdistribusi (*DDoS attacks*), kebocoran data rahasia (*data breaches*), serta kesalahan konfigurasi sistem (*misconfigurations*).
- **Identity and Access Management (IAM) sebagai Garis Pertahanan Pertama:**
  - Penerapan prinsip hak istimewa terkecil (*Principle of Least Privilege* / PoLP): setiap pengguna hanya diberikan izin minimum yang mutlak diperlukan untuk menyelesaikan tugasnya.
  - Memisahkan akses konsol web grafis (*read-only*) dari akses terprogram pengembang (*CLI/API token*), menegakkan kebijakan kata sandi ketat, dan mewajibkan otentikasi multi-faktor (MFA).
- **Kriptografi dan Enkripsi Tiga Status Data:**
  - Enkripsi bertindak sebagai garis pertahanan terakhir (*last line of defense*). Data wajib dilindungi pada tiga kondisi siklus hidupnya:
    - *Data at Rest*: Disimpan di disk atau database, diamankan dengan algoritma AES-256.
    - *Data in Transit*: Bergerak di jaringan, dilindungi oleh protokol TLS 1.3 / SSL.
    - *Data in Use*: Diproses di memori RAM, dilindungi oleh teknologi komputasi rahasia (*Confidential Computing* / TEE).
- **Observabilitas Menyeluruh (Cloud Monitoring):**
  - Pemantauan bukan sekadar memasang alat otomatis, melainkan proses berkelanjutan untuk mengukur metrik, mengumpulkan log sistem, mendeteksi anomali kejadian, dan mengonfigurasi peringatan dini (*alarms*).

---

### Metodologi dan Arsitektur Teknis

- **Kerangka Kerja Keamanan Siber NIST dan CSPM:**
  - **Lima Pilar NIST:** *Identify* (identifikasi aset), *Protect* (perlindungan data & IAM), *Detect* (deteksi intrusi), *Respond* (tindakan mitigasi insiden), dan *Recover* (pemulihan operasional).
  - **Cloud Security Posture Management (CSPM):** Otomatisasi pengawasan untuk mendeteksi deviasi kepatuhan dan memperbaiki kesalahan konfigurasi sistem secara proaktif.
- **Standar Federasi Identitas Enterprise:**
  - **SAML 2.0:** Protokol berbasis XML untuk pertukaran autentikasi antara Identity Provider (IdP) dan Service Provider (SP), mendukung Single Sign-On (SSO) perusahaan.
  - **OpenID Connect (OIDC):** Protokol identitas modern berbasis kerangka kerja OAuth 2.0 menggunakan format JSON Web Tokens (JWT) untuk aplikasi web dan seluler.
- **Tiga Dimensi Pemantauan dan Audit Panggilan API:**
  - **Infrastructure Monitoring:** Mengawasi CPU, memori, bandwidth, dan kesehatan perangkat keras virtual/fisik.
  - **Database Monitoring:** Melacak kueri lambat, utilisasi koneksi pool, dan ketersediaan DBMS.
  - **Application Performance Monitoring (APM):** Mengukur latensi transaksi pengguna ujung ke ujung guna memenuhi SLA.
  - **Pelacakan Panggilan API untuk Audit Forensik:** Merekam seluruh aktivitas kontrol sistem melalui layanan cloud terkelola seperti AWS CloudTrail, Google Cloud Audit Logging, dan Azure Activity Logs.

---

### Studi Kasus dan Pembelajaran Industri

- **Transformasi Nyata Lima Enterprise Terkemuka:**
  - **The Weather Company:** Memetakan atmosfer bumi dan menghasilkan 250 miliar prakiraan cuaca per hari (throughput 150.000 RPS) pada resolusi $1 \text{ km}^2$. Migrasi ke IBM Cloud Kubernetes Service memangkas alur pipa DevOps sebesar 80% dan memungkinkan penskalaan elastis 5x lipat saat badai ekstrem.
  - **American Airlines:** Membangun platform swalayan digital berbasis microservices untuk memberikan transparansi opsi penerbangan alternatif saat terjadi penundaan cuaca buruk (*IROPS*).
  - **Cementos Pacasmayo:** Mengimplementasikan SAP S/4HANA di IBM Cloud untuk bertransformasi dari entitas berbasis produk menjadi penyedia layanan, menghasilkan visibilitas laporan keuangan dan pengadaan secara *real-time*.
  - **Welch's Food:** Menerapkan strategi hybrid cloud koperatif dengan memindahkan sistem non-kritis ke cloud publik agar tim TI internal dapat fokus pada nilai-nilai inti para petani.
  - **LiquidPower Specialty Products Inc. (LSPI):** Memilih solusi cloud penuh (*greenfield cloud adoption*) untuk menjalankan ERP SAP mandiri di bawah naungan Berkshire Hathaway tanpa beban membangun data center fisik baru.
- **Peluang Karir dan Pasar Tenaga Kerja Cloud:**
  - Proyeksi pasar layanan komputasi awan global mencapai **$1.554,94 Miliar pada 2030** dengan pertumbuhan tahunan majemuk (**CAGR 14,1%**).
  - Indeks Gartner TalentNeuron mencatat skor kesulitan perekrutan sebesar **78**, membuktikan bahwa permintaan tenaga ahli jauh melampaui pasokan kandidat yang tersedia (*demand outpaces supply*).
  - Profil enam spesialisasi karir utama: *Cloud Developer*, *Cloud Integration Specialist*, *Cloud Data Engineer*, *Cloud Security Engineer*, *Cloud DevOps Engineer*, dan *Cloud Solutions Architect*.
  - Peran sertifikasi industri resmi sebagai akselerator karir yang membuka visibilitas di mata perekrut tanpa keharusan memiliki latar belakang ilmu komputer formal.
