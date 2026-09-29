# Cloud Security and Monitoring

Dokumen ini menyajikan rangkuman komprehensif mengenai tata kelola keamanan dan observabilitas sistem di lingkungan komputasi awan. Pembahasan mencakup analisis ancaman siber kontemporer, model tanggung jawab bersama (*shared responsibility model*), kerangka kerja keamanan siber NIST, manajemen postur keamanan cloud (*Cloud Security Posture Management* / CSPM), arsitektur *Zero Trust* dan protokol federasi identitas (SAML dan OpenID Connect), tata kelola hak istimewa terkecil (*Principle of Least Privilege*), enkripsi tiga status data, praktik terbaik manajemen kunci kriptografi (KMS), hingga teknik pemantauan infrastruktur, basis data, *Application Performance Monitoring* (APM), pemantauan *Infrastructure as Code* (IaC), serta audit jejak panggilan API lintas penyedia cloud enterprise.

---

## 1. Fundamentals of Cloud Security and Threat Landscape

### A. Urgensi Keamanan pada Transformasi Cloud
- **Transisi Menuju Lingkungan Terhubung:**
  - Migrasi beban kerja enterprise ke komputasi awan membuka efisiensi operasional besar, namun memperluas bidang serangan siber (*attack surface*).
  - Penyedia cloud menjamin keandalan dan integritas fisik perangkat keras pusat data, namun tata kelola data, konfigurasi akses, dan integritas aplikasi tetap menjadi tanggung jawab penuh organisasi pengguna.
- **Tantangan Unik Keamanan Cloud:**
  - *Lack of Visibility*: Kesulitan melacak siapa yang mengakses data dan memantau layanan eksternal apa saja yang terhubung di luar batas jaringan internal organisasi.
  - *Multitenancy Risks*: Beberapa organisasi berbagi infrastruktur fisik yang sama; aktivitas berbahaya yang menargetkan penyewa lain berpotensi menimbulkan dampak tidak langsung jika isolasi virtualisasi tidak dikonfigurasi secara sempurna.
  - *Shadow IT*: Penggunaan layanan dan aplikasi cloud pihak ketiga oleh karyawan tanpa persetujuan atau pengawasan departemen TI resmi.
  - *Misconfigurations*: Kesalahan konfigurasi pengaturan privasi, membiarkan ember penyimpanan (*storage buckets*) terbuka untuk publik, atau penggunaan kata sandi administratif bawaan (*default credentials*).

### B. Spektrum Ancaman Siber di Lingkungan Cloud
- **1. Ancaman Orang Dalam (Insider Threats):**
  - Dilakukan oleh karyawan aktif, mantan staf, mitra bisnis, atau kontraktor yang memiliki riwayat hak akses resmi ke jaringan internal.
  - Sangat berbahaya karena aktivitas penyalahgunaan wewenang ini berada di balik benteng pertahanan eksternal sehingga tidak terdeteksi oleh sistem keamanan perimeter tradisional.
- **2. Serangan Penolakan Layanan Terdistribusi (DDoS Attacks):**
  - Upaya membanjiri kapasitas server, jaringan, atau aplikasi dengan lalu lintas palsu masif dari ribuan sistem terkoordinasi (botnet).
  - Sering mengeksploitasi kelemahan protokol manajemen jaringan seperti *Simple Network Management Protocol* (SNMP) untuk melumpuhkan ketersediaan layanan publik.
- **3. Pelanggaran dan Kebocoran Data (Data Breaches):**
  - Akses ilegal terhadap informasi rahasia bisnis, data keuangan nasabah, atau identitas pribadi konsumen.
  - Menimbulkan kerugian finansial masif, tuntutan hukum ganti rugi, serta rusaknya reputasi korporasi secara permanen.

### C. Model Tanggung Jawab Bersama (Shared Responsibility Model)
Keamanan komputasi awan bukan merupakan tanggung jawab tunggal penyedia cloud ataupun pelanggan, melainkan kolaborasi pembagian tugas yang bergantung pada model layanan yang digunakan:

$$
\text{Tanggung Jawab Keamanan Pelanggan}(\text{IaaS}) > \text{Tanggung Jawab Keamanan Pelanggan}(\text{PaaS}) > \text{Tanggung Jawab Keamanan Pelanggan}(\text{SaaS})
$$

- **Infrastruktur sebagai Layanan (IaaS):**
  - *Tanggung Jawab Penyedia*: Keamanan fasilitas fisik gedung data center, pasokan listrik, pendingin, perangkat keras server fisik, jaringan kabel optik, dan lapisan perangkat lunak *hypervisor*.
  - *Tanggung Jawab Pelanggan*: Instalasi dan penambalan keamanan sistem operasi (*OS patching*), konfigurasi firewall virtual (*security groups*), pengaturan jaringan virtual, *middleware*, runtime aplikasi, kode program, dan perlindungan data.
- **Platform sebagai Layanan (PaaS):**
  - *Tanggung Jawab Penyedia*: Keamanan infrastruktur fisik, virtualisasi, sistem operasi, pustaka runtime, dan mesin basis data terkelola.
  - *Tanggung Jawab Pelanggan*: Keamanan kode sumber aplikasi, konfigurasi logika bisnis, dan tata kelola data pengguna.
- **Perangkat Lunak sebagai Layanan (SaaS):**
  - *Tanggung Jawab Penyedia*: Mengelola hampir seluruh tumpukan teknologi mulai dari perangkat keras, sistem operasi, runtime, basis data, hingga pembaruan aplikasi perangkat lunak dan keamanannya.
  - *Tanggung Jawab Pelanggan*: Pengelolaan hak akses identitas pengguna (*credentials*), kebijakan kata sandi, dan integritas data yang dimasukkan ke dalam aplikasi.

### D. Kerangka Kerja NIST dan Cloud Security Posture Management (CSPM)
- **Lima Pilar Cybersecurity Framework (NIST):**
  - *1. Identify*: Mengidentifikasi aset data penting, inventaris sistem, dan profil risiko organisasi.
  - *2. Protect*: Menetapkan kebijakan perlindungan data, enkripsi, dan pembatasan hak akses.
  - *3. Detect*: Memantau anomali jaringan dan tanda-tanda intrusi siber secara berkesinambungan.
  - *4. Respond*: Menjalankan prosedur mitigasi dan respons insiden saat serangan terdeteksi.
  - *5. Recover*: Mengembalikan fungsi operasional sistem pascaserangan dan memulihkan data cadangan.
- **Manajemen Postur Keamanan Cloud (CSPM):**
  - Solusi otomatisasi yang dirancang untuk mendeteksi dan memperbaiki kesalahan konfigurasi (*misconfigurations*) pada seluruh layanan cloud.
  - Memeriksa kepatuhan terhadap regulasi industri (ISO 27001, SOC 2, HIPAA, GDPR), memantau kepatuhan kebijakan IAM, dan mengevaluasi risiko aset digital secara otomatis.

---

## 2. Identity and Access Management (IAM) and Access Policies

### A. Peran IAM sebagai Garis Pertahanan Pertama
- **Definisi IAM:**
  - *Identity and Access Management* (IAM) adalah kerangka kerja kebijakan dan teknologi yang memastikan bahwa individu atau sistem yang tepat memiliki hak akses yang sesuai ke sumber daya teknologi yang ditentukan, pada waktu yang tepat, dan untuk alasan yang sah.
  - Menjadi lini pertahanan terdepan untuk mencegah ancaman kebocoran data akibat pencurian kredensial akun.
- **Klasifikasi Persona Pengguna Cloud:**
  - *1. Administrative Users*:
    - Administrator platform cloud, teknisi operasional, dan manajer infrastruktur.
    - Memiliki wewenang membuat, memperbarui, dan menghapus instans layanan serta basis data produksi. Akun ini memerlukan pengawasan ketat karena penyusup dapat menghancurkan seluruh lingkungan sistem.
  - *2. Developer Users*:
    - Pengembang aplikasi, arsitek sistem, dan penerbit kode program.
    - Memerlukan akses ke lingkungan pengembangan, API, *command-line interface* (CLI), dan repositori build.
  - *3. Application Users*:
    - Konsumen akhir atau karyawan bisnis yang hanya berinteraksi dengan antarmuka aplikasi cloud untuk operasional harian.

### B. Prinsip Hak Istimewa Terkecil (Principle of Least Privilege / PoLP)
- **Konsep Inti PoLP:**
  - Setiap entitas (pengguna, proses, atau program) hanya diberikan hak akses minimum yang mutlak dibutuhkan untuk menyelesaikan tugas pekerjaannya, dan tidak lebih dari itu.
  - Jika sebuah akun mengalami peretasan, dampak kerusakan dapat diisolasi secara ketat dan tidak merembet ke sistem kritis lainnya.
- **Pemisahan Tingkat Akses (Console vs CLI/API):**
  - Pengguna operasional bisnis hanya diberikan akses konsol berbasis grafis (GUI) dengan izin baca (*read-only*).
  - Teknisi pengembang diberikan akses terprogram berbasis token API atau kunci SSH dengan ruang lingkup tindakan yang dibatasi secara spesifik.

### C. Komponen Arsitektur IAM dan Tata Kelola Kebijakan
- **Elemen Format Kebijakan Keamanan (Policy Format):**
  - *Title*: Penamaan deskriptif yang jelas mengenai tujuan kebijakan.
  - *Scope*: Menentukan sistem, akun, atau pengguna mana yang terikat oleh aturan tersebut.
  - *Objective*: Sasaran keamanan dan kepatuhan yang ingin dicapai.
  - *Policy Statement*: Rincian aturan, prosedur operasional, dan batasan teknis yang diberlakukan.
  - *Roles & Responsibilities*: Pembagian wewenang penegakan aturan.
  - *Compliance & Enforcement*: Sanksi dan mekanisme pemantauan pelanggaran.
  - *Review & Revision*: Jadwal pembaruan berkala kebijakan.
- **Access Groups dan Access Policies:**
  - *Access Groups*: Pengelompokan logis dari sekumpulan pengguna dan identitas layanan (*Service IDs*) yang memerlukan tingkat izin serupa.
  - Memberikan hak akses ke grup jauh lebih efisien dan terstruktur daripada mengelola izin pengguna secara individual:
    - *Subject*: Entitas yang meminta akses (pengguna atau grup akses).
    - *Target*: Sumber daya atau instans layanan yang dituju.
    - *Role*: Kumpulan tindakan yang diizinkan pada target (seperti Viewer, Operator, Editor, atau Administrator).
- **Standar Kebijakan Kata Sandi dan Otentikasi Multi-Faktor (MFA):**
  - Penerapan panjang kata sandi minimum, kombinasi karakter alfanumerik dan simbol, kedaluwarsa berkala, pelarangan penggunaan ulang kata sandi lama (*password history*), serta penguncian akun otomatis setelah beberapa kali kegagalan login.
  - Kewajiban MFA berbasis waktu (*Time-Based One-Time Passwords* / TOTP), sertifikat digital, atau kunci keamanan fisik FIDO2.

### D. Standar Federasi Identitas: SAML dan OpenID Connect
- **Security Assertion Markup Language (SAML 2.0):**
  - Standar berbasis XML untuk pertukaran data autentikasi dan otorisasi antara Penyedia Identitas (*Identity Provider* / IdP) dan Penyedia Layanan (*Service Provider* / SP).
  - Memungkinkan implementasi *Single Sign-On* (SSO) tingkat enterprise, di mana pengguna cukup masuk satu kali melalui direktori korporat untuk mengakses puluhan aplikasi cloud.
- **OpenID Connect (OIDC):**
  - Standar identitas modern yang dibangun di atas kerangka kerja otorisasi OAuth 2.0 menggunakan format *JSON Web Tokens* (JWT).
  - Dirancang untuk kemudahan integrasi pada aplikasi seluler, aplikasi satu halaman (*single-page applications*), dan antarmuka pemrograman aplikasi web modern.

---

## 3. Cloud Encryption and Key Management

### A. Peran Enkripsi sebagai Garis Pertahanan Terakhir
- **Definisi Kriptografi Cloud:**
  - Enkripsi adalah proses matematis mengubah data teks terbaca (*plaintext*) menjadi bentuk sandi acak yang tidak dapat dibaca (*ciphertext*) menggunakan algoritma kriptografi dan kunci rahasia:

$$
\text{Ciphertext} = \text{Encrypt}(\text{Plaintext}, K)
$$

$$
\text{Plaintext} = \text{Decrypt}(\text{Ciphertext}, K)
$$

  - Berfungsi sebagai garis pertahanan terakhir (*last line of defense*): jika penyerang berhasil menembus lapisan pertahanan jaringan dan mencuri data fisik, data tersebut tetap tidak bernilai karena tidak dapat didekripsi tanpa kunci yang sah.

### B. Perlindungan Enkripsi pada Tiga Status Data (Data in Three States)
Data memerlukan mekanisme perlindungan kriptografi pada tiga fase siklus hidupnya:

- **1. Data saat Diam (Data at Rest):**
  - Melindungi data yang tersimpan secara fisik di dalam media penyimpanan lokal, piringan disk blok (*block storage*), sistem berkas (*file storage*), basis data terdistribusi, atau wadah penyimpanan objek (*object storage*).
  - Diterapkan menggunakan algoritma enkripsi simetris berstandar militer seperti *Advanced Encryption Standard* (AES-256).
- **2. Data saat Transit (Data in Motion / Transit):**
  - Melindungi integritas dan kerahasiaan data yang sedang mengalir melintasi jaringan internet publik atau jalur privat antar pusat data.
  - Memanfaatkan protokol *Transport Layer Security* (TLS 1.3) dan *Secure Sockets Layer* (SSL) untuk mengautentikasi titik akhir dan mencegah penyadapan (*eavesdropping*) serta serangan man-in-the-middle.
- **3. Data saat Digunakan (Data in Use / Confidential Computing):**
  - Melindungi data sensitif ketika sedang dimuat ke dalam memori kerja (*RAM*) dan diproses oleh unit pemrosesan pusat (*CPU*).
  - Memanfaatkan teknologi komputasi rahasia (*confidential computing*) berbasis enklave perangkat keras terisolasi (*hardware-based trusted execution environments* / TEE), sehingga sistem operasi host maupun penyedia cloud fisik tidak dapat mengintip isi memori kerja.

### C. Enkripsi Sisi Server vs Enkripsi Sisi Klien
- **Enkripsi Sisi Server (Server-Side Encryption / SSE):**
  - Data dienkripsi secara otomatis oleh sistem penyimpanan cloud begitu data diterima, sebelum ditulis ke piringan disk fisik.
  - *Customer-Supplied Keys*: Pelanggan menyediakan kunci enkripsi mereka sendiri saat memanggil API.
  - *Customer-Managed Keys*: Kunci dikelola menggunakan layanan manajemen kunci cloud (*Key Management Service* / KMS).
- **Enkripsi Sisi Klien (Client-Side Encryption / CSE):**
  - Data dienkripsi secara lokal di lingkungan pengguna sebelum dikirimkan melintasi jaringan ke penyimpanan cloud.
  - Penyedia layanan cloud hanya menerima gumpalan data acak (*ciphertext*) tanpa pernah memiliki kunci dekripsinya, menjamin privasi absolut.

### D. Praktik Terbaik Tata Kelola Kunci Kriptografi (KMS)
- **Pemisahan Kunci dari Data:**
  - Kunci enkripsi wajib disimpan di fasilitas perangkat keras terpisah (*Hardware Security Modules* / HSM) dan dilarang disimpan bersamaan dengan data terenkripsi.
- **Pencadangan Luar Lokasi (Off-Site Backup):**
  - Kunci pemulihan master dicadangkan di lingkungan yang terisolasi secara geografis dan diaudit secara rutin.
- **Rotasi Kunci Berkala (Periodic Key Rotation):**
  - Memperbarui dan memutar kunci enkripsi secara otomatis setiap periode waktu tertentu (misalnya per 90 atau 365 hari) guna membatasi volume data yang terekspos jika suatu kunci bocor.
- **Autentikasi Multi-Faktor untuk Kunci Master:**
  - Setiap tindakan administratif tingkat tinggi terhadap kunci induk wajib memerlukan persetujuan otentikasi ganda dari beberapa penanggung jawab keamanan (*dual-custody principle*).

---

## 4. Cloud Monitoring, Observability, and Threat Detection

### A. Esensi dan Ruang Lingkup Observabilitas Cloud
- **Definisi Pemantauan Cloud (Cloud Monitoring):**
  - Pemantauan bukan sekadar memasang perangkat lunak otomatis, melainkan penerapan strategi, proses, dan metrik berkelanjutan untuk melacak ketersediaan, alokasi sumber daya, performa, kepatuhan, serta mendeteksi ancaman siber di seluruh tumpukan aplikasi.
- **Tiga Kategori Alat Pemantauan:**
  - *Infrastructure Monitoring*: Memantau utilisasi CPU, memori, bandwidth jaringan, dan status perangkat keras fisik maupun virtual mesin.
  - *Database Monitoring*: Melacak kueri lambat (*slow queries*), utilisasi kumpulan koneksi (*connection pools*), proses transaksi, dan integritas replikasi data.
  - *Application Performance Monitoring (APM)*: Mengukur latensi transaksi dari ujung ke ujung (*end-to-end user transactions*), tingkat kesalahan aplikasi, dan ketersediaan layanan untuk memenuhi Perjanjian Tingkat Layanan (*Service Level Agreements* / SLA).

### B. Empat Pilar Data Pemantauan Cloud
- **1. Metrik (Metrics):**
  - Data numerik terukur yang dikumpulkan pada interval waktu teratur untuk membentuk garis dasar performa (*baselines*) dan mengidentifikasi anomali pemakaian.
- **2. Log (Logs):**
  - Catatan peristiwa tekstual terperinci yang mencatat aktivitas sistem, kesalahan aplikasi, dan jejak akses pengguna untuk keperluan forensik.
- **3. Peristiwa (Events):**
  - Notifikasi kejadian waktu nyata di dalam infrastruktur yang dapat memicu alur penanganan insiden otomatis.
- **4. Peringatan Dini (Alarms and Alerts):**
  - Ambang batas proaktif (*proactive thresholds*) yang mengirimkan pemberitahuan instan kepada teknisi jaga saat kondisi abnormal terdeteksi.

### C. Pemantauan Berbasis Layanan (Service-Based Monitoring) dan Audit IaC
- **Load Balancer Monitoring:**
  - Mengawasi distribusi beban kerja antar server dan memantau status kesehatan instans (*health checks*).
- **CDN Monitoring:**
  - Memantau latensi penayangan konten statis, persentase keberhasilan tembolok (*cache hit ratio*), dan performa jaringan tepi (*edge points of presence*).
- **Auto-Scaling Group Monitoring:**
  - Memvalidasi efektivitas kebijakan penskalaan dinamis agar penambahan dan pengurangan instans berlangsung seimbang sesuai beban transaksi riil.
- **Infrastructure as Code (IaC) Monitoring:**
  - Memantau konfigurasi infrastruktur yang dibuat melalui kode skrip (Terraform, Ansible, CloudFormation).
  - Berfungsi penting mendeteksi pergeseran konfigurasi (*configuration drift*), yaitu perubahan manual yang dilakukan secara langsung di server tanpa melalui repositori kode IaC.

### D. Pelacakan Panggilan API untuk Audit Forensik
Setiap interaksi dengan konsol web, skrip otomatisasi, atau perkakas pengembang di cloud dieksekusi melalui panggilan API. Pelacakan panggilan API menjadi bukti hukum dan audit kepatuhan (*audit trail*) utama:

- **AWS CloudTrail:**
  - Mencatat, menyimpan, dan mengaudit seluruh panggilan API di akun AWS, mencakup identitas pemanggil (*IAM identity*), cap waktu (*timestamp*), alamat IP asal, dan parameter permintaan.
- **Google Cloud Audit Logging:**
  - Menangkap aktivitas administrasi sistem, akses data pengguna, dan modifikasi konfigurasi di seluruh ekosistem GCP.
- **Microsoft Azure Activity Logs:**
  - Merekam seluruh operasi tingkat bidang kontrol (*control plane*) pada sumber daya Azure, membantu mendeteksi tindakan tidak sah dan perubahan izin akses.
- **Salesforce Event Monitoring:**
  - Melacak akses data pelanggan, pengunduhan laporan massal, dan riwayat login untuk mencegah kebocoran informasi bisnis.

### E. Matriks Mitigasi Ancaman dan Solusi Cloud Terkelola
- **Mitigasi Serangan DDoS:**
  - *Layanan Cloud*: AWS Shield dan Google Cloud Armor.
  - *Mekanisme*: Penyerapan lonjakan lalu lintas palsu secara otomatis melalui jaringan *Anycast* global dan aturan firewall aplikasi web (*WAF*).
- **Pencegahan Pelanggaran Data:**
  - *Layanan Cloud*: Azure Key Vault dan AWS Key Management Service (KMS).
  - *Mekanisme*: Isolasi kunci kriptografi dalam modul perangkat keras HSM dan penegakan enkripsi data otomatis.
- **Pendeteksian Miskonfigurasi:**
  - *Layanan Cloud*: AWS Config dan Google Cloud Security Command Center.
  - *Mekanisme*: Audit konfigurasi berkelanjutan terhadap standar keamanan dan perbaikan deviasi secara terprogram.
- **Penanganan Ancaman Orang Dalam:**
  - *Layanan Cloud*: Azure Active Directory (Microsoft Entra ID) dan Cloud IAM Privileged Access Management.
  - *Mekanisme*: Akses tepat waktu (*Just-In-Time access*) dan verifikasi berbasis risiko kontekstual.

---

## 5. Key Takeaways and Summary

### A. Poin-Poin Kunci Pembelajaran Modul 05 Lesson 1
- **Keamanan adalah Tanggung Jawab Bersama:**
  - Keamanan komputasi awan bukan monopoli penyedia cloud; pelanggan memegang kendali penuh atas keamanan data, identitas akun, dan konfigurasi lingkungan mereka sendiri.
- **IAM sebagai Garis Depan Pertahanan:**
  - Penerapan prinsip hak istimewa terkecil (*PoLP*), autentikasi multi-faktor (*MFA*), dan integrasi protokol federasi (*SAML/OIDC*) memitigasi risiko pencurian identitas dan ancaman orang dalam.
- **Enkripsi Menyeluruh di Tiga Status:**
  - Melindungi kerahasiaan data pada saat diam (*at rest*), saat berpindah di jaringan (*in transit*), dan saat diproses di memori (*in use* / *confidential computing*) dengan tata kelola kunci kriptografi yang terisolasi.
- **Observabilitas Proaktif dan Audit Jejak:**
  - Pemantauan menyeluruh yang menggabungkan metrik, log, peringatan otomatis, pemantauan *Infrastructure as Code*, dan perekaman panggilan API menjamin deteksi anomali dini dan pemenuhan regulasi kepatuhan enterprise.