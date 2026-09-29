# Module 06: Final Project and Assignment

Modul ini merupakan puncak penerapan praktis dari seluruh kompetensi *cloud computing* yang telah dipelajari pada modul-modul sebelumnya. Modul ini mengintegrasikan dua pilar penilaian utama: implementasi teknis penerapan aplikasi web kontainer ke *serverless platform* IBM Cloud Code Engine, serta perancangan solusi arsitektur strategis tingkat *enterprise* untuk memodernisasi platform pengiriman makanan monolitik menjadi ekosistem *hybrid multi-cloud* dan *microservices*.

### Ringkasan Konsep Inti

*   **Penerapan Berbasis Kontainer (*Containerized Deployment*):**
    *   Mengemas seluruh dependensi, pustaka, dan konfigurasi server web (*Nginx*) ke dalam format citra *Docker* (*Docker image*).
    *   Menjamin portabilitas aplikasi web statis interaktif agar dapat dieksekusi secara identik di lingkungan lokal maupun *cloud*.

*   **Platform Komputasi Tanpa Server (*Serverless Computing Platform*):**
    *   Mengadopsi IBM Cloud Code Engine sebagai platform *fully managed* berbasis *Kubernetes* dan *Knative*.
    *   Menghilangkan keharusan pengelolaan kluster komputasi, konfigurasi jaringan manual, serta manajemen infrastruktur dasar.
    *   Menyediakan penskalaan otomatis dari nol (*scale-to-zero*) saat tidak ada lalu lintas data hingga kapasitas puncak saat beban meningkat.

*   **Repositori Citra Kontainer Terkelola (*Managed Container Registry*):**
    *   Pemanfaatan IBM Cloud Container Registry (ICR) sebagai repositori terpusat dan aman untuk menyimpan, memindai, dan mendistribusikan citra kontainer produksi.
    *   Pengaturan hak akses berbasis *namespace* pribadi guna mengamankan artefak perangkat lunak organisasi.

*   **Modernisasi Arsitektur Monolitik ke *Microservices*:**
    *   Dekomposisi sistem terpusat (*tightly coupled*) menjadi layanan-layanan independen yang dapat dikembangkan, diterapkan, dan diskalakan secara terpisah.
    *   Pemilihan model basis data yang sesuai kebutuhan (*polyglot persistence*), pemisahan komputasi intensif kecerdasan buatan (*AI*), dan orkestrasi gerbang antarmuka pemrograman aplikasi (*API gateway*).

### Metodologi dan Arsitektur Teknis

*   **Alur Kerja Proyek Akhir Praktikum (*Hands-on Lab*):**
    *   *Pengujian Lokal:* Menjalankan dan memvalidasi aplikasi web "Guess the Capital" menggunakan server web lokal *Python HTTP* pada lingkungan *Theia Cloud IDE*.
    *   *Pengemasan Kontainer:* Menulis berkas *Dockerfile* berbasis citra resmi `nginx:alpine`, menyalin aset situs web statis ke direktori publik `/usr/share/nginx/html`, serta membangun citra kontainer menggunakan perintah `docker build`.
    *   *Publikasi ke Registry:* Melakukan autentikasi ke *IBM Cloud CLI*, membuat *namespace* unik pada IBM Container Registry (ICR), menandai (*tagging*) citra lokal, dan mengunggahnya (*docker push*) ke repositori privat *icr.io*.
    *   *Penerapan Serverless:* Mengonfigurasi dan meluncurkan aplikasi pada proyek IBM Cloud Code Engine dengan mengarahkan sumber citra ke ICR, menetapkan alokasi sumber daya komputasi, serta mengekspos aplikasi melalui *endpoint URL* publik yang aman (*HTTPS*).

*   **Arsitektur Solusi Modernisasi *Enterprise* (DineEase 2.0):**
    *   *Fondasi Infrastruktur:* Penerapan arsitektur *Multi-Zone Region* (MZR) untuk memastikan ketersediaan tinggi (*high availability*) lintas zona data terisolasi.
    *   *Komputasi Khusus AI:* Penggunaan server fisik berkinerja tinggi (*Bare Metal Servers*) yang dilengkapi akselerator grafis (*GPU*) untuk melatih dan mengeksekusi model *machine learning* rekomendasi makanan.
    *   *Orkestrasi Kontainer:* Penerapan IBM Cloud Kubernetes Service (IKS) atau *Red Hat OpenShift on IBM Cloud* guna mengelola siklus hidup *microservices* pemesanan, pelacakan kurir, dan pembayaran secara otomatis.
    *   *Gerbang dan Keamanan API:* Pemanfaatan IBM API Connect untuk standardisasi antarmuka komunikasi antar-layanan, manajemen kuota pemanggilan (*rate limiting*), serta penegakan kebijakan autentikasi.
    *   *Pemisahan Persistensi Data:*
        *   IBM Cloudant (NoSQL) untuk menampung katalog menu dinamis dan status pelacakan geospasial kurir yang membutuhkan fleksibilitas skema tinggi.
        *   IBM Db2 on Cloud (RDBMS) untuk mencatat transaksi finansial, pembayaran, dan pencatatan akuntansi yang mensyaratkan integritas data *ACID*.
    *   *Akselerasi Pengiriman Konten:* Distribusi aset visual (foto hidangan, materi promosi) melalui IBM Cloud Content Delivery Network (CDN) berbasis *edge server* Akamai untuk meminimalkan latensi unduhan bagi pengguna akhir.
    *   *Keseimbangan Beban Jaringan:* Pemasangan IBM Cloud Load Balancer untuk mendistribusikan permintaan masuk secara merata ke seluruh instans *microservices* yang sehat.
    *   *Observabilitas Menyeluruh:* Pemantauan kesehatan metrik sistem dan pelacakan jejak kesalahan secara terpadu melalui IBM Cloud Monitoring dan *Log Analysis*.

### Studi Kasus dan Pembelajaran Industri

*   **Transisi Praktis Menuju Operasional *Cloud Native*:**
    *   Proyek akhir membuktikan bahwa transisi dari berkas kode sumber statis ke aplikasi produksi global dapat diselesaikan secara efisien menggunakan pendekatan *container-first* dan *serverless-first*.
    *   Pengembang dapat memusatkan perhatian sepenuhnya pada inovasi fungsional aplikasi tanpa terbebani oleh manajemen konfigurasi server dan sistem operasi.

*   **Penyelesaian Masalah Nyata Skala Besar (*DineEase Case Study*):**
    *   Mengilustrasikan bagaimana arsitektur terpadu mengatasi kelemahan arsitektur monolitik konvensional seperti *single point of failure*, kesulitan skalabilitas parsial saat jam sibuk makan siang, dan keterbatasan kinerja komputasi analitik.
    *   Menunjukkan pentingnya kesesuaian antara karakteristik beban kerja dengan model layanan *cloud* (IaaS, PaaS, FaaS, SaaS) dan tipe basis data yang dipilih untuk mencapai efisiensi biaya (*TCO*) serta keandalan operasional tingkat tinggi.
