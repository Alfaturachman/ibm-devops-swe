# Module 02: Cloud Computing Models

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 02: Cloud Computing Models pada kursus Introduction to Cloud Computing, mencakup analisis mendalam mengenai tiga model layanan komputasi awan (IaaS, PaaS, SaaS), empat model penerapan (Public, Private, Hybrid, Community Cloud), arsitektur Virtual Private Cloud (VPC), konsep cloud bursting, spektrum variasi multicloud, serta kerangka kerja pengambilan keputusan strategis.

---

### Ringkasan Konsep Inti

- **Tiga Model Layanan Cloud (Cloud Service Models):**
  - **Infrastructure as a Service (IaaS):** Model penyediaan sumber daya komputasi mentah (pemrosesan, penyimpanan disk, dan jaringan) secara *on-demand*. Memberikan fleksibilitas dan kendali konfigurasi tertinggi, namun menuntut keahlian teknis pemeliharaan sistem operasi dan keamanan.
  - **Platform as a Service (PaaS):** Model penyediaan lingkungan platform siap pakai bagi pengembang perangkat lunak untuk membangun, menguji, dan menyebarkan aplikasi tanpa perlu memusingkan manajemen server fisik, sistem operasi, atau penyeimbang beban.
  - **Software as a Service (SaaS):** Model penyampaian perangkat lunak berbasis cloud di mana pengguna langsung mengakses aplikasi melalui peramban web atau aplikasi seluler dengan seluruh infrastruktur, platform, pembaruan, dan keamanan dikelola penuh oleh vendor.
- **Analogi Kendaraan Tessa Rhodes (Car Metaphor):**
  - **IaaS dianalogikan seperti Leasing Mobil:** Pengguna memilih spesifikasi mobil, mengemudi sendiri, membeli bensin, membayar tol, dan bertanggung jawab atas servis berkala.
  - **PaaS dianalogikan seperti Menyewa Mobil di Bandara:** Pengguna mengemudi dan mengisi bahan bakar saat liburan, namun tidak menanggung kepemilikan dan depresiasi jangka panjang mobil.
  - **SaaS dianalogikan seperti Naik Taksi / Transportasi Online:** Pengguna hanya duduk sebagai penumpang sampai ke tujuan; tarif perjalanan sudah mencakup bahan bakar, tol, jasa sopir, dan perawatan mobil.
- **Prinsip Emas Arsitektur Cloud:**
  - *"Stay as high on the stack as you can"*: Organisasi disarankan untuk selalu beroperasi pada tingkatan abstraksi tertinggi yang masih memenuhi kebutuhan bisnis guna meminimalkan beban pengelolaan operasional (*operational overhead*).

---

### Metodologi dan Arsitektur Teknis

- **Pembagian Tanggung Jawab Operasional (Shared Responsibility Model):**
  - **Pada IaaS:** Penyedia mengelola pusat data fisik, kelistrikan, server fisik, jaringan, dan *hypervisor*. Pengguna mengelola sistem operasi, *patching* keamanan, basis data, *middleware*, runtime, kode aplikasi, dan data.
  - **Pada PaaS:** Penyedia mengelola seluruh tumpukan IaaS ditambah sistem operasi, pustaka runtime, dan basis data terkelola. Pengguna hanya mengelola kode aplikasi dan data.
  - **Pada SaaS:** Penyedia mengelola seluruh tumpukan teknologi ujung ke ujung. Pengguna hanya bertanggung jawab atas kredensial akun dan data bisnis yang diinput.
- **Empat Model Penerapan Cloud (Cloud Deployment Models):**
  - **Public Cloud:** Sumber daya multi-penyewa (*multi-tenant*) dimiliki dan dioperasikan oleh pihak ketiga di luar firewall organisasi, menawarkan efisiensi biaya tertinggi dan skalabilitas elastis instan.
  - **Private Cloud:** Infrastruktur komputasi yang di-*provisioning* secara eksklusif untuk satu organisasi tunggal, dapat berada di dalam kantor (*on-premises*) maupun di luar kantor (*off-premises* / *Virtual Private Cloud*).
  - **Hybrid Cloud:** Penggabungan dan orkestrasi antara lingkungan *private cloud* (termasuk on-premises) dengan satu atau lebih *public cloud* berdasarkan tiga pilar utama: interoperabilitas, skalabilitas, dan portabilitas aplikasi.
  - **Community Cloud:** Infrastruktur yang dibangun secara eksklusif untuk melayani sekelompok organisasi dengan kesamaan misi, standar kepatuhan regulasi, dan profil risiko keamanan (telah berevolusi dari isolasi fisik kaku menjadi *Software-Defined Assured Workloads* berbasis enklaf logis per-proyek).
- **Fenomena dan Mekanisme Cloud Bursting:**
  - Beban kerja normal dijalankan di atas *private cloud*. Saat terjadi lonjakan trafik melebihi ambang batas kapasitas server internal, beban kerja tersebut secara otomatis meluap (*burst*) ke instans *public cloud* sementara waktu, lalu menyusut kembali setelah beban normal.

---

### Studi Kasus dan Pembelajaran Industri

- **Skenario Evaluasi Kematangan Perjalanan Cloud (Cloud Journey):**
  - **Desakan Waktu Akhir Masa Sewa Data Center:** Mengadopsi IaaS dengan metode pemindahan langsung (*Lift-and-Shift*) untuk menyalin mesin virtual tanpa merombak kode.
  - **Modernisasi Berkelanjutan (Re-platforming):** Memindahkan aplikasi ke lingkungan PaaS atau platform kontainer (OpenShift/Kubernetes) untuk membebaskan tim dari pemeliharaan OS.
  - **Pembangunan Produk Baru dari Awal (Greenfield):** Mengadopsi arsitektur nirserver (*Serverless / FaaS*) untuk meluncurkan produk secara instan tanpa biaya server menganggur.
- **Spektrum Variasi Arsitektur Hibrida:**
  - **Hybrid Mono-Cloud:** Mengintegrasikan pusat data lokal dengan tepat satu penyedia cloud publik (misalnya integrasi on-premises dengan IBM Cloud saja).
  - **Hybrid Multi-Cloud:** Mengintegrasikan lingkungan lokal dengan beberapa penyedia cloud publik sekaligus (AWS, Azure, GCP) berbasis standar terbuka (*open standards*) guna memilih layanan terbaik (*best-of-breed*).
  - **Composite Multi-Cloud:** Memecah komponen aplikasi tunggal secara terdistribusi lintas penyedia cloud (misalnya UI di AWS, logika analitik di Azure, dan basis data inti tetap di *private cloud* lokal).
