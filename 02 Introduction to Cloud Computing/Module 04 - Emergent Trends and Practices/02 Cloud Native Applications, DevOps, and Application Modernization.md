# Cloud Native Applications, DevOps, and Application Modernization

Dokumen ini menyajikan rangkuman komprehensif mengenai evolusi rekayasa perangkat lunak modern di lingkungan komputasi awan, mencakup arsitektur aplikasi *cloud native*, metodologi dan siklus hidup *DevOps on the Cloud*, integrasi *pipeline* CI/CD, serta strategi modernisasi aplikasi (*application modernization*). Pembahasan mengulas tumpukan solusi lima lapis oleh Andrea Crawford, trilogi transformasi terpadu oleh Eric Minick, studi perbandingan alat DevOps lintas penyedia cloud utama (AWS, Azure, GCP, dan IBM Cloud), hingga pandangan pakar industri mengenai komputasi tepi (*edge computing*), kecerdasan buatan terkelola, dan keandalan sistem (*Site Reliability Engineering* / SRE).

---

## 1. Cloud Native Applications

### A. Definisi dan Karakteristik Fundamental
- **Konsep Dasar Cloud Native:**
  - Aplikasi *cloud native* adalah perangkat lunak yang dirancang, dibangun, dan dioperasikan sejak awal secara eksklusif untuk berjalan di lingkungan komputasi awan, atau aplikasi yang telah direfaktor secara mendalam agar mematuhi prinsip-prinsip arsitektur cloud.
  - Berbeda dengan aplikasi monolitik tradisional yang dibangun sebagai satu blok kode raksasa dengan keterikatan erat antara antarmuka, logika bisnis, dan basis data, aplikasi *cloud native* dibangun dari kumpulan layanan mikro (*microservices*) independen.
- **Tiga Pilar Pengembangan Cloud Native:**
  - *1. Pendekatan Arsitektur Microservices*:
    - Memecah fungsionalitas aplikasi menjadi unit-unit mikro dengan fungsi tunggal (contoh pada situs perjalanan: pemesanan tiket penerbangan, reservasi hotel, penyewaan mobil, dan promosi diskon dikelola oleh layanan mikro terpisah).
    - Masing-masing layanan mikro dapat diperbarui dan diskalakan secara independen tanpa menimbulkan gangguan bagi pengguna akhir (*zero downtime*).
  - *2. Kontainerisasi (Containers)*:
    - Seluruh kode program, pustaka pendukung, dan dependensi dikemas ke dalam kontainer ringan agar memiliki portabilitas maksimal dan dapat dieksekusi secara seragam di berbagai lingkungan infrastruktur.
  - *3. Metodologi Agile dan Otomatisasi*:
    - Menggunakan siklus rilis yang cepat, berulang, dan didorong oleh umpan balik pengguna secara berkelanjutan.

### B. Arsitektur Lima Lapisan Cloud Native (Andrea Crawford)
Arsitektur tumpukan solusi komputasi awan modern yang dirumuskan oleh Andrea Crawford (IBM Cloud) membagi tumpukan teknologi menjadi lima lapisan terintegrasi:

- **1. Lapisan Infrastruktur Cloud (Cloud Infrastructure):**
  - Fondasi fisik dan tervirtualisasi yang mencakup *private cloud*, *public cloud*, serta infrastruktur *enterprise on-premises*.
  - Menopang skenario penerapan hibrida (*hybrid*) dan multicloud.
- **2. Lapisan Penjadwalan dan Orkestrasi (Scheduling and Orchestration Layer):**
  - Bidang kontrol (*control planes*) yang mengatur penempatan, ketersediaan, dan penskalaan beban kerja kontainer secara otomatis (contoh: Kubernetes / K8s).
- **3. Lapisan Layanan Aplikasi dan Data (Application and Data Services Layer):**
  - Menyediakan layanan pendukung (*backing services*) seperti basis data terdistribusi, antrean pesan, dan integrasi data lintas cloud maupun *on-premise*.
- **4. Lapisan Waktu Eksekusi Aplikasi (Application Runtimes):**
  - Lingkungan runtime eksekusi yang secara konvensional dikenal sebagai lapisan *middleware*.
- **5. Lapisan Aplikasi Cloud Native (Cloud Native Apps):**
  - Terletak di puncak tumpukan (*the sweet spot*), tempat kode bisnis aplikasi dirancang dan dieksekusi dengan memanfaatkan seluruh kapabilitas lapisan di bawahnya.

### C. Komoditisasi Tumpukan Solusi dan Inovasi Bisnis
- **Pergeseran Gravitasi Layanan (Lower Center of Gravity):**
  - Seiring matangnya teknologi komputasi awan, fungsi-fungsi teknis yang rumit diturunkan (*refactored*) ke lapisan tumpukan yang lebih rendah sehingga menjadi komoditas siap pakai.
  - Kapabilitas seperti perutean lalu lintas jaringan (*routing*), penyeimbangan beban (*load balancing*), dan penemuan layanan (*service discovery*) kini ditangani secara otomatis oleh lapisan jaringan jala (*service mesh* seperti Istio) dan kerangka kerja *serverless* (seperti Knative).
- **Pembebasan Waktu Rekayasa untuk Nilai Tambah:**
  - Pengembang tidak perlu lagi membangun infrastruktur jaringan atau sistem penanganan kesalahan dari nol, melainkan fokus sepenuhnya pada logika bisnis aplikasi.
- **Standarisasi Pengawasan dan Auditabilitas:**
  - Aplikasi *cloud native* wajib dilengkapi instrumentasi standar, mencakup:
    - *Standardized Logging and Events*: Format pencatatan log dan penanganan kejadian yang seragam berbasis katalog standar enterprise.
    - *Distributed Tracing*: Pelacakan perjalanan kueri yang melintasi puluhan kontainer layanan mikro untuk mendeteksi titik kemacetan (*bottlenecks*) kinerja.
- **Prinsip Utama Adopsi:**
  - Setiap perangkat lunak yang dioperasikan di cloud wajib mengadopsi pola pikir *cloud native* guna mewujudkan ketahanan dan efisiensi rekayasa perangkat lunak dalam skala enterprise (*engineering at scale*).

---

## 2. DevOps on the Cloud

### A. Definisi dan Filosofi Budaya DevOps
- **Penyatuan Dua Kutub Tradisional:**
  - Tim Pengembang (*Development*): Memiliki mandat bisnis untuk bergerak cepat, menulis kode baru, dan sesering mungkin merilis fitur inovatif.
  - Tim Operasional (*Operations*): Memiliki mandat stabilitas, menjaga keandalan sistem, memantau infrastruktur, serta meminimalkan risiko gangguan operasional (*downtime*).
- **Definisi DevOps:**
  - *DevOps* adalah pendekatan kolaboratif yang menyatukan pemilik bisnis, pengembang perangkat lunak, tim jaminan kualitas (*Quality Assurance* / QA), dan tim operasional untuk menyampaikan solusi perangkat lunak secara berkelanjutan (*continuous delivery*).
  - Mengadaptasi prinsip-prinsip *Agile* dan pola pikir *Lean* ke seluruh rantai pasok perangkat lunak (*software supply chain*), sehingga memangkas pemborosan kerja (*overhead*), duplikasi tugas, dan perbaikan berulang (*rework*).

### B. Siklus Hidup dan Alur Kerja DevOps (CI/CD Pipeline)
Siklus pengiriman perangkat lunak modern diwujudkan melalui alur otomatis (*automated delivery pipeline*) yang menghubungkan tahapan konseptual ideasi, pengkodean, kompilasi, pengujian, deployment, hingga pemantauan operasional:

- **1. Integrasi Berkelanjutan (Continuous Integration / CI):**
  - Pengembang menggabungkan (*merge*) perubahan kode ke repositori cabang utama secara berkala setiap hari.
  - Setiap integrasi secara otomatis memicu pengujian unit (*automated testing*) dan proses pembuatan paket build.
  - Paket build dirilis sebagai citra kekal (*immutable images*): pembaruan sistem tidak dilakukan dengan menambal instans yang sedang berjalan, melainkan mengganti seluruh komponen lama dengan citra kontainer versi baru yang telah terverifikasi.
- **2. Pengiriman Berkelanjutan (Continuous Delivery / CD):**
  - Memastikan seluruh perubahan kode yang lolos pengujian otomatis selalu berada dalam status siap rilis ke lingkungan produksi kapan saja (*releasable state*).
  - Proses perpindahan ke tahap produksi dapat dipicu dengan persetujuan manual satu tombol.
- **3. Penerapan Berkelanjutan (Continuous Deployment / CDep):**
  - Tahap otomatisasi tertinggi di mana setiap perubahan kode yang berhasil melewati seluruh rangkaian pengujian otomatis langsung disebarkan ke lingkungan produksi tanpa intervensi manual manusia.
- **4. Pemantauan Berkelanjutan (Continuous Monitoring / CM):**
  - Menggunakan alat pengawasan untuk mengumpulkan telemetri, metrik kinerja, dan log sistem secara waktu nyata (menggunakan Prometheus, Grafana, dan ELK Stack).
  - Memberikan wawasan prediktif kepada tim pengembang mengenai performa sistem dan kepuasan pengguna sebelum terjadi kegagalan fatal.

$$
\text{Kecepatan Rilis (Velocity)} \propto \text{Tingkat Otomatisasi CI/CD}
$$

$$
\text{Keandalan Sistem (Reliability)} \propto \text{Observabilitas Telemetri CM}
$$

### C. Keuntungan Strategis DevOps di Lingkungan Cloud
- **Infrastruktur yang Dapat Diprogram (Infrastructure as Code / IaC):**
  - Praktik DevOps memungkinkan penyediaan server, konfigurasi *middleware*, dan pemasangan aplikasi dilakukan secara terprogram melalui kode skrip.
  - Menghasilkan alur instalasi infrastruktur yang terdokumentasi, dapat diulang secara identik (*repeatable*), terverifikasi, dan terlacak (*traceable*).
- **Pengujian pada Lingkungan Serupa Produksi Berbiaya Rendah:**
  - Tim pengembang dapat membuat replika lingkungan produksi sementara untuk keperluan pengujian regresi dengan biaya sangat murah, lalu menghancurkannya kembali setelah pengujian selesai.
- **Ketahanan dan Pemulihan Bencana Cepat (Rapid Disaster Recovery):**
  - Jika terjadi bencana alam atau kerusakan sistem, infrastruktur cloud dapat dibangun kembali dari nol secara instan menggunakan konfigurasi skrip IaC yang tersimpan di repositori Git.

### D. Studi Kasus Alat DevOps Lintas Penyedia Cloud Utama
Organisasi dapat mengimplementasikan praktik DevOps menggunakan layanan asli (*native services*) yang disediakan oleh platform cloud terkemuka:

- **DevOps pada Amazon Web Services (AWS):**
  - *Alur CI/CD*: AWS CodePipeline dan AWS CodeBuild.
  - *Deployment Aplikasi*: AWS Elastic Beanstalk.
  - *Komputasi Nirserver dan Kontainer*: AWS Lambda dan Amazon Elastic Kubernetes Service (EKS).
- **DevOps pada Microsoft Azure:**
  - *Kolaborasi dan Alur Kerja*: Azure DevOps dan Azure Pipelines.
  - *Orkestrasi Kontainer*: Azure Kubernetes Service (AKS).
  - *Komputasi Nirserver*: Azure Functions.
- **DevOps pada Google Cloud Platform (GCP):**
  - *Alur CI/CD*: Cloud Build dan Artifact Registry.
  - *Manajemen Kontainer*: Google Kubernetes Engine (GKE).
  - *Komputasi Nirserver*: Cloud Functions dan Cloud Run.
- **DevOps pada IBM Cloud:**
  - *Automated Deployment*: IBM Cloud Continuous Delivery (didukung oleh rantai alat Tekton *open source*).
  - *Orkestrasi Kontainer Enterprise*: IBM Kubernetes Service (IKS) dan Red Hat OpenShift on IBM Cloud.
  - *Komputasi Nirserver*: IBM Cloud Functions.

---

## 3. Application Modernization

### A. Rasional dan Urgensi Bisnis
- **Beban Sistem Warisan (Legacy Debt):**
  - Banyak korporasi besar menginvestasikan jutaan dolar pada aplikasi inti yang telah beroperasi selama puluhan tahun.
  - Aplikasi-aplikasi ini umumnya terisolasi (*siloed*) dalam mainframe atau server lokal fisik, serta sangat mahal dan berisiko tinggi untuk diperbarui.
- **Definisi Modernisasi Aplikasi (AppMod):**
  - Proses merombak, merefaktor, dan mengadaptasikan sistem warisan agar dapat memanfaatkan arsitektur cloud modern, layanan analitik mutakhir, dan metodologi kerja baru tanpa harus membuang nilai bisnis yang telah tertanam di dalam aplikasi lama.

### B. Trilogi Transformasi Terpadu (Eric Minick)
Eric Minick (IBM Cloud) mengemukakan bahwa banyak organisasi enterprise salah memahami modernisasi dengan menganggap transformasi arsitektur, transformasi infrastruktur, dan transformasi cara kerja sebagai tiga proyek terpisah yang dipimpin oleh divisi berbeda. Padahal, ketiganya saling terikat erat (*inextricably linked*):

- **1. Transformasi Arsitektur (Architecture Transformation):**
  - Bergerak dari arsitektur monolitik yang kaku (*monolithic*) atau arsitektur berorientasi layanan (*Service-Oriented Architecture* / SOA) berbasis XML yang berat, menuju arsitektur layanan mikro (*microservices*) berbasis protokol RESTful yang ringan dan independen.
- **2. Transformasi Infrastruktur (Infrastructure Transformation):**
  - Bergerak dari server fisik (*bare metal*) dan mesin virtual statis (*virtual machines*) menuju komputasi awan yang elastis (*elastic cloud*), kontainerisasi (Docker), dan orkestrasi klaster (Kubernetes/OpenShift).
- **3. Transformasi Cara Kerja (Ways of Working Transformation):**
  - Bergerak dari model rekayasa tradisional air terjun (*waterfall development*) yang membutuhkan perencanaan tahunan kaku, menuju metodologi *Agile*, alur *DevOps*, dan praktik rekayasa keandalan situs (*Site Reliability Engineering* / SRE).

$$
\text{Modernisasi Aplikasi} = \Delta \text{Arsitektur (Microservices)} + \Delta \text{Infrastruktur (Cloud)} + \Delta \text{Cara Kerja (DevOps/SRE)}
$$

### C. Bahaya Menjalankan Transformasi Secara Terisolasi
- **Microservices Tanpa Cloud:**
  - Jika tim arsitektur membangun lusinan layanan mikro baru, tetapi divisi infrastruktur masih mewajibkan pengadaan server fisik manual (yang memakan waktu berbulan-bulan), maka kecepatan peluncuran fitur ke pasar (*time-to-market*) tidak akan pernah tercapai.
- **Cloud Tanpa Microservices:**
  - Menyewa server cloud elastis untuk menjalankan aplikasi monolitik raksasa yang tidak terdistribusi hanya akan memicu pemborosan biaya, karena monolitik tidak dapat memanfaatkan fitur penskalaan dinamis berbasis kontainer.
- **Infrastruktur Terprogram Tanpa DevOps:**
  - Infrastruktur cloud yang fleksibel membutuhkan pengembang dan operator yang mampu memprogram infrastruktur bersama. Rencana kerja tahunan bergaya *waterfall* akan melumpuhkan agilitas yang ditawarkan oleh teknologi cloud.

---

## 4. Expert Viewpoints: Emergent Trends in Cloud Computing

### A. Enam Arah Perkembangan Utama Industri
Para profesional komputasi awan mengidentifikasi enam tren utama yang mendominasi arah perkembangan teknologi masa kini dan masa depan:

- **1. Dominasi Arsitektur Hybrid Multi-Cloud:**
  - Sebagian besar korporasi global mengalihkan strategi mereka dari ketergantungan pada vendor tunggal (*single cloud provider*) menuju lingkungan gabungan *public cloud* dan *private on-premises*.
- **2. Lonjakan Komputasi Tepi (Edge Computing):**
  - Dengan proyeksi puluhan miliar perangkat pintar (*smart devices*) yang akan terhubung ke internet, pemrosesan data tidak lagi dapat sepenuhnya dipusatkan di data center utama yang berjarak jauh.
  - Komputasi awan bergerak mendekati perangkat fisik (*to the edge*) untuk memproses data secara lokal dengan latensi nol sebelum mengirimkan ringkasan analitik ke server cloud.
- **3. Pemanfaatan AI dan Layanan Pembelajaran Mesin Terkelola:**
  - Munculnya layanan kecerdasan buatan tingkat tinggi yang siap pakai (*pre-trained AI services*), seperti pengenalan gambar (*computer vision*), transkripsi audio, dan sintesis bahasa alami.
  - Perusahaan tidak perlu lagi membangun klaster server inferensi AI internal sendiri; cukup mengunggah data ke API penyedia cloud dan menerima wawasan cerdas secara instan.
- **4. Komputasi Nirserver Total (Serverless by Default):**
  - Pengembang semakin beralih ke komputasi nirserver karena mengeliminasi pekerjaan administratif yang tidak memberikan diferensiasi nilai bisnis (*undifferentiated heavy lifting*), seperti konfigurasi alamat IP, manajemen partisi memori, atau instalasi tambalan kernel OS.
- **5. Integrasi Dialogis DevOps dan SRE:**
  - Terciptanya dialog dua arah berkesinambungan antara pengembang dan operator sistem, di mana pengembang bertanggung jawab memantau kesehatan kodenya hingga ke lingkungan produksi menggunakan prinsip SRE.
- **6. Penguatan Keamanan Siber Menyeluruh (Cybersecurity Advancement):**
  - Perlindungan batas parameter jaringan (*network perimeter*), isolasi komputasi kriptografis, serta enkripsi data saat transit dan saat istirahat (*at rest*) secara berkesinambungan.

---

## 5. Key Takeaways and Summary

### A. Poin-Poin Kunci Pembelajaran Modul 04 Lesson 2
- **Aplikasi Cloud Native Mewujudkan Skalabilitas Enterprise:**
  - Dibangun dengan arsitektur layanan mikro, dikemas dalam kontainer mandiri, dan diatur melalui bidang kontrol Kubernetes untuk menghadirkan ketersediaan tinggi dan inovasi cepat tanpa henti.
- **DevOps sebagai Penggerak Kecepatan dan Stabilitas:**
  - Integrasi CI/CD, pengujian otomatis, dan pengawasan telemetri waktu nyata menyatukan pengembang dan operasional dalam menghadirkan rilis perangkat lunak berkualitas tinggi dengan risiko kegagalan minimal.
- **Sinergi Tiga Pilar Modernisasi Aplikasi:**
  - Keberhasilan modernisasi sistem warisan enterprise hanya dapat dicapai apabila transformasi arsitektur (layanan mikro), infrastruktur (cloud), dan budaya kerja (DevOps) dijalankan secara terpadu dan selaras.
