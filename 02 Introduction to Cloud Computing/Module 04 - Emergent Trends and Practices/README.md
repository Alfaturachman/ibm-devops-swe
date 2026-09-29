# Module 04: Emergent Trends and Practices

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 04: Emergent Trends and Practices pada kursus Introduction to Cloud Computing, mencakup analisis mendalam mengenai arsitektur hybrid multi-cloud, dekomposisi layanan mikro (microservices), paradigma komputasi nirserver (serverless / FaaS), arsitektur lima lapisan aplikasi cloud-native oleh Andrea Crawford, integrasi alur kerja DevOps di cloud, serta trilogi modernisasi aplikasi terpadu oleh Eric Minick.

---

### Ringkasan Konsep Inti

- **Hybrid Multi-Cloud sebagai Strategi Bebas Keterikatan:**
  - *Hybrid Multi-Cloud* menggabungkan keunggulan komputasi hibrida (menghubungkan data center lokal dengan cloud publik) dan strategi multicloud (memanfaatkan berbagai vendor cloud sekaligus seperti AWS, Azure, GCP, dan IBM Cloud).
  - Memberikan kebebasan strategis bagi organisasi untuk memilih layanan terbaik dari masing-masing penyedia (*best-of-breed*) serta menghindari bahaya keterikatan vendor tunggal (*vendor lock-in*).
- **Arsitektur Layanan Mikro (Microservices Architecture):**
  - Pendekatan rekayasa perangkat lunak di mana satu aplikasi dipecah menjadi kumpulan layanan berukuran kecil yang terkopel longgar (*loosely coupled*), berfokus pada fungsi tunggal (*single responsibility*), dan dapat disebarkan secara mandiri (*independently deployable*).
  - Mengeliminasi risiko kerapuhan aplikasi monolitik tradisional, memungkinkan penskalaan komponen secara spesifik (*selective scaling*), dan memfasilitasi penggunaan beragam tumpukan teknologi (*polyglot tech stack*).
- **Komputasi Nirserver (Serverless Computing / FaaS):**
  - Paradigma di mana seluruh pengelolaan infrastruktur fisik dan virtual diabstraksi sepenuhnya oleh penyedia cloud; pengembang hanya bertanggung jawab menulis logika kode aplikasi (*Functions as a Service* / FaaS).
  - Menerapkan model biaya konsumsi murni: pengembang hanya membayar durasi komputasi per milidetik saat fungsi dipanggil, tanpa ada biaya sewa saat sistem menganggur (*never pay for idle capacity*).

---

### Metodologi dan Arsitektur Teknis

- **Arsitektur Lima Lapisan Cloud-Native (Andrea Crawford):**
  - **1. Cloud Infrastructure:** Lapisan komputasi fisik dan tervirtualisasi (Private, Public, Enterprise).
  - **2. Scheduling and Orchestration:** Bidang kontrol (*control plane*) manajemen kontainer otomatis (seperti Kubernetes / K8s).
  - **3. Application and Data Services:** Layanan pendukung (*backing services*), integrasi data terdistribusi, dan antrean pesan.
  - **4. Application Runtimes:** Lingkungan eksekusi runtime aplikasi (konvensional dikenal sebagai *middleware*).
  - **5. Cloud Native Apps:** Kode aplikasi bisnis di puncak tumpukan (*the sweet spot*).
- **Komoditisasi Tumpukan Solusi (Lower Center of Gravity):**
  - Fungsi-fungsi teknis rumit (seperti penemuan layanan, penyeimbangan beban, dan perutean jaringan) diturunkan ke lapisan tumpukan bawah melalui jala layanan (*service mesh* seperti Istio) dan framework serverless (Knative), membebaskan pengembang untuk berinovasi murni pada kode bisnis.
- **Siklus Hidup DevOps dan Alur Kerja CI/CD:**
  - **Continuous Integration (CI):** Integrasi perubahan kode harian dengan otomatisasi pengujian dan pembuatan paket citra kekal (*immutable images*).
  - **Continuous Delivery (CD):** Kode selalu berada dalam status siap rilis ke produksi dengan pengawasan terpadu.
  - **Infrastructure as Code (IaC):** Provisi infrastruktur secara terprogram melalui skrip kode, menghasilkan lingkungan pengujian yang dapat diulang (*repeatable*) dan terlacak (*traceable*).
- **Trilogi Modernisasi Aplikasi Terpadu (Eric Minick):**
  - Keberhasilan modernisasi aplikasi (*AppMod*) menuntut keterpaduan tiga transformasi simultan:
    - *Transformasi Arsitektur*: Bergerak dari monolitik/SOA menuju layanan mikro (*microservices*).
    - *Transformasi Infrastruktur*: Bergerak dari server fisik/VM lambat menuju *Cloud & Containers*.
    - *Transformasi Cara Kerja*: Bergerak dari rencana kaku Waterfall menuju *DevOps & SRE*.

---

### Studi Kasus dan Pembelajaran Industri

- **Studi Kasus Hybrid Multi-Cloud:**
  - **Layanan Pemesanan Bunga (Cloud Scaling):** Mengatasi lonjakan pesanan ekstrem pada Hari Valentine dan Hari Ibu melalui penskalaan elastis ke cloud publik tanpa harus membeli server fisik mahal yang menganggur sepanjang tahun.
  - **Arsitektur Composite Cloud Lintas Benua:** Mempertahankan kerangka kerja poin hadiah (*rewards framework*) di server lokal Eropa, sementara antarmuka web dan API penagihan dipindahkan ke pusat data cloud Amerika Utara untuk mengatasi latensi saat liburan Thanksgiving.
  - **Modernisasi Maskapai Penerbangan:** Menghubungkan basis data pemeliharaan historis ke model analitik prediktif AI di cloud guna memangkas 30% waktu keterlambatan penerbangan akibat kerusakan mekanis tak terduga.
- **Studi Kasus Microservices "Dream Game":**
  - Menguraikan dekomposisi aplikasi streaming video ke dalam tiga layanan mikro independen: *Content Catalog* (metadata jutaan video), *Search Function* (pencarian instan), dan *Recommendations* (algoritma analitik preferensi pengguna).
  - Tim pengembang dapat memperbarui modul rekomendasi secara independen dalam hitungan hari tanpa menyebabkan waktu henti (*zero downtime*) bagi layanan pemutaran video lainnya.
- **Skenario Penerapan Serverless:**
  - Sangat ideal untuk pemrosesan teks dan media (pembuatan *thumbnail*, transkripsi video, konversi PDF), pencarian data paralel, penyerapan aliran data telemetri IoT (*data stream ingestion*), dan API seluler.
  - *Pertimbangan Teknis*: Memahami isu *cold start delay* saat inisialisasi awal fungsi serta batasan batas waktu eksekusi (*timeout*) untuk beban kerja proses jangka panjang (*long-running tasks*).
