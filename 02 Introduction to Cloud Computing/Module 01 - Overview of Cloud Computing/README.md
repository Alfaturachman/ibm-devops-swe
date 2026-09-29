# Module 01: Overview of Cloud Computing

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 01: Overview of Cloud Computing pada kursus Introduction to Cloud Computing, mencakup definisi resmi NIST, lima karakteristik esensial komputasi awan, justifikasi bisnis dan pergeseran finansial CapEx menuju OpEx, sejarah evolusi virtualisasi, profil penyedia cloud terkemuka, serta peran komputasi awan sebagai akselerator teknologi mutakhir (IoT, AI, dan Blockchain).

---

### Ringkasan Konsep Inti

- **Definisi Resmi NIST (SP 800-145):**
  - Komputasi awan adalah model yang memungkinkan akses jaringan di mana saja, nyaman, dan sesuai kebutuhan (*on-demand*) ke kumpulan bersama sumber daya komputasi yang dapat dikonfigurasi (seperti jaringan, server, penyimpanan, aplikasi, dan layanan) yang dapat disediakan dan dirilis secara cepat dengan upaya manajemen minimal atau interaksi penyedia layanan yang sedikit.
- **Lima Karakteristik Esensial Komputasi Awan (NIST):**
  - **1. On-Demand Self-Service:** Konsumen dapat memesan dan mengonfigurasi kapasitas komputasi (waktu server, penyimpanan disk) secara sepihak dan otomatis tanpa interaksi manusia dengan staf penyedia.
  - **2. Broad Network Access:** Sumber daya komputasi dapat diakses melalui jaringan internet menggunakan mekanisme standar yang mendukung beragam perangkat (ponsel cerdas, tablet, laptop, dan stasiun kerja).
  - **3. Resource Pooling:** Sumber daya komputasi fisik penyedia digabungkan (*pooled*) untuk melayani banyak konsumen menggunakan model multi-penyewa (*multi-tenant*), dengan sumber daya fisik dan virtual yang berbeda dialokasikan secara dinamis sesuai permintaan konsumen.
  - **4. Rapid Elasticity:** Kemampuan komputasi dapat disediakan dan dilepaskan secara elastis, dalam beberapa kasus secara otomatis, untuk melakukan penskalaan cepat (*scale-out / scale-in*) sesuai lonjakan beban kerja.
  - **5. Measured Service:** Penggunaan sumber daya dikontrol, dioptimalkan, dan dilaporkan secara transparan melalui sistem pengukuran berbasis pemakaian (*pay-as-you-go* atau *metered billing*).
- **Rasional dan Justifikasi Bisnis:**
  - Menghilangkan beban belanja modal awal (*CapEx*) pengadaan server fisik dan menggantinya dengan biaya operasional berkala yang terprediksi (*OpEx*).
  - Mempersingkat waktu peluncuran produk ke pasar (*time-to-market*) dari hitungan bulan menjadi hitungan jam atau menit.
  - Mengatasi tantangan ledakan volume data global dan menjamin ketersediaan tinggi (*high availability*) serta toleransi kegagalan tanpa membangun data center sekunder mandiri.

---

### Metodologi dan Arsitektur Teknis

- **Sejarah dan Evolusi Komputasi Awan:**
  - **Era Mainframe (1950-an):** Pengenalan komputasi terpusat dengan mekanisme pembagian waktu (*time-sharing*) menggunakan terminal bodoh (*dumb terminals*).
  - **Kelahiran Virtual Machine (1970-an):** IBM memperkenalkan CP-40/CP-67 dan VM/370 yang memungkinkan pembagian perangkat keras mainframe fisik menjadi beberapa mesin virtual independen.
  - **Peran Kunci Hypervisor:** Lapisan perangkat lunak perantara (*Virtual Machine Monitor* / VMM) yang mengabstraksi perangkat keras fisik, mengalokasikan CPU/RAM secara dinamis, dan mengisolasi sistem operasi tamu (*guest OS*).
  - **Lahirnya Komputasi Utilitas Modern (Akhir 1990-an s.d. 2000-an):** Perusahaan seperti Salesforce (SaaS via peramban web pada 1999) dan Amazon Web Services (AWS EC2 & S3 pada 2006) memopulerkan penyewaan infrastruktur virtual berbasis jaringan internet publik.
- **Profil Penyedia Layanan Cloud Terkemuka:**
  - **Amazon Web Services (AWS):** Pelopor pasar komputasi awan publik dengan portofolio layanan terlengkap dan pangsa pasar global terbesar.
  - **Microsoft Azure:** Penyedia cloud enterprise terkemuka dengan integrasi mulus ke ekosistem Windows Server, Active Directory, dan perkakas bisnis korporasi.
  - **Google Cloud Platform (GCP):** Dikenal atas keunggulan infrastruktur analitik data masif (*big data*), kecerdasan buatan, dan orkestrasi kontainer Kubernetes.
  - **IBM Cloud:** Berfokus pada kebutuhan enterprise, arsitektur *hybrid cloud*, kepatuhan data ketat (perbankan dan industri yang teratur), serta integrasi Red Hat OpenShift.
  - **Alibaba Cloud:** Penyedia komputasi awan terbesar di kawasan Asia-Pasifik dengan kekuatan pada platform e-commerce dan komputasi skala masif.

---

### Studi Kasus dan Pembelajaran Industri

- **Studi Kasus Adopsi Enterprise:**
  - **American Airlines:** Memanfaatkan cloud publik untuk memodernisasi aplikasi seluler pelanggan, menyajikan swalayan tiket instan, dan meningkatkan ketahanan sistem saat terjadi badai besar.
  - **UBank:** Memindahkan infrastruktur perbankan ke IBM Cloud untuk meluncurkan fitur perbankan digital baru dalam hitungan hari tanpa terhambat birokrasi server fisik lama.
  - **Bitly:** Memproses miliaran klik tautan per bulan dengan melakukan penskalaan otomatis instan tanpa mengkhawatirkan kapasitas batas server lokal.
  - **ActivTrades:** Memanfaatkan infrastruktur cloud berlatensi ultra-rendah untuk mengeksekusi jutaan transaksi perdagangan finansial global secara aman dan stabil.
- **Akselerasi Teknologi Mutakhir (Emerging Technologies):**
  - **Internet of Things (IoT) pada Konservasi Satwa di Afrika Selatan:** Pemasangan sensor nirkabel IoT pada zebra dan antelop di Cagar Alam Welgevonden yang terhubung ke IBM Cloud; anomali pergerakan hewan memicu deteksi dini penyusupan pemburu liar (*poachers*) untuk melindungi badak langka.
  - **Artificial Intelligence (AI) pada Turnamen Tenis US Open:** IBM Watson memproses ribuan jam siaran video secara otomatis menggunakan visi komputer dan analisis audio untuk merangkum klip sorotan terbaik (*AI Highlights*) dalam hitungan menit pascapertandingan serta melayani lonjakan trafik web hingga +5.000%.
  - **Blockchain pada Keterlacakan Pangan Salinas Valley:** Platform IBM Food Trust melacak asal-usul selada dari ladang panen hingga rak swalayan dalam hitungan detik, mencegah pemborosan jutaan ton bahan pangan saat terjadi penarikan produk (*food recall*).
  - **Pemeliharaan Prediktif KONE:** Memproses data telemetri lift dan eskalator bagi lebih dari satu miliar mobilitas manusia per hari menggunakan arsitektur nirserver (*IBM Cloud Functions*) untuk mengganti suku cadang sebelum kerusakan fisik terjadi.
