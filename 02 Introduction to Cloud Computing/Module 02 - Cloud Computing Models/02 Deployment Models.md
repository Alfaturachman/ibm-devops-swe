# Deployment Models in Cloud Computing

Catatan komprehensif ini menyajikan analisis mendalam mengenai empat model penerapan komputasi awan (*Cloud Deployment Models*), yaitu *Public Cloud*, *Private Cloud*, *Hybrid Cloud*, dan *Community Cloud*. Materi mengulas penentuan lokasi infrastruktur, batas kepemilikan dan tata kelola, arsitektur *Virtual Private Cloud* (VPC), konsep *cloud bursting*, varian *multi-cloud*, pandangan pakar industri mengenai strategi migrasi dan prinsip pemilihan tumpukan teknologi (*stay high on the stack*), hingga evolusi *software-defined community cloud* berbasis standar NIST SP 800-145.

---

## 1. Public Cloud

### A. Definisi dan Filosofi Operasional
- *Public Cloud* merupakan model penerapan komputasi awan di mana seluruh sumber daya infrastruktur (server, komputasi, penyimpanan, jaringan, dan keamanan) dimiliki, dikelola, dan dioperasikan oleh penyedia layanan pihak ketiga (*cloud service provider*) dan disajikan kepada konsumen melalui jaringan internet publik.
- Karakteristik operasional utama *Public Cloud*:
  - Pengguna mengakses dan mengatur sumber daya secara mandiri (*self-service*) menggunakan konsol web berbasis peramban atau *Application Programming Interface* (API).
  - Konsumen tidak memiliki server fisik yang menjalankan aplikasi mereka maupun media penyimpanan fisik tempat data mereka disimpan.
  - Mengadopsi analogi layanan utilitas publik (*utility computing*), serupa dengan penggunaan air bersih, listrik, atau gas rumah tangga:
    - Konsumen tidak perlu mendirikan pembangkit listrik sendiri untuk menyalakan lampu.
    - Konsumen cukup terhubung dengan jaringan penyedia, menggunakan kapasitas sesuai kebutuhan, dan membayar tagihan berdasarkan konsumsi riil pada periode tertentu.

### B. Karakteristik Arsitektur dan Skala Ekonomi
- Karakteristik arsitektur teknis yang mendasari *Public Cloud*:
  - Arsitektur Multi-Penyewa Terdistribusi (*Virtualized Multi-Tenant Architecture*):
    - Berbagai organisasi dan pengguna (*tenants*) saling berbagi sekumpulan sumber daya komputasi fisik (*shared physical infrastructure pool*) yang berada di luar *firewall* internal masing-masing perusahaan.
    - Sumber daya tidak didedikasikan secara fisik untuk satu penyewa tunggal, melainkan diisolasi secara logis melalui perangkat lunak virtualisasi.
  - Skala Ekonomi Masif (*Massive Economies of Scale*):
    - Pembelian perangkat keras dalam jumlah raksasa oleh penyedia cloud menekan biaya modal awal secara drastis, sehingga penyedia mampu menawarkan tarif komputasi yang jauh lebih kompetitif dibandingkan pengadaan server internal perusahaan.
  - Formula perhitungan penghematan biaya kepemilikan menyeluruh (*Total Cost of Ownership* / TCO):

$$
\text{TCO}_{\text{Public Cloud}} = \text{OpEx}_{\text{Pay-As-You-Go}} \ll (\text{CapEx}_{\text{Hardware}} + \text{CapEx}_{\text{Facilities}} + \text{OpEx}_{\text{Maintenance}} + \text{OpEx}_{\text{Staff}})
$$

  - Ketersediaan Sangat Tinggi (*High Availability* dan *Fault Tolerance*):
    - Jumlah server fisik dan redundansi jalur jaringan yang tersebar di berbagai pusat data memastikan bahwa jika salah satu komponen fisik mengalami kerusakan, beban kerja akan dialihkan secara transparan ke komponen lain tanpa menghentikan ketersediaan layanan aplikasi.
- Penyedia terkemuka di pasar global:
  - Amazon Web Services (AWS)
  - Microsoft Azure
  - IBM Cloud
  - Google Cloud Platform (GCP)
  - Alibaba Cloud

### C. Keuntungan, Tantangan, dan Kasus Penggunaan
- Keuntungan utama:
  - Skalabilitas elastis instan: Aplikasi dapat merespons lonjakan trafik pengguna secara otomatis tanpa perlu menambah perangkat keras fisik secara manual.
  - Menghilangkan beban pemeliharaan fasilitas pusat data, sistem pendingin, dan keamanan fisik gedung.
- Kekhawatiran dan risiko strategis:
  - Ketiadaan Kendali Penuh terhadap Lingkungan Komputasi Fisik: Pengguna tunduk pada kebijakan operasional dan performa infrastruktur milik vendor.
  - Keamanan Siber: Risiko kebocoran data (*data breaches*), kehilangan data, pembajakan akun (*account hijacking*), dan kerentanan pada lapisan perangkat lunak bersama.
  - Kepatuhan Kedaulatan Data (*Data Sovereignty Compliance*): Tantangan regulasi ketika data disimpan dan dialirkan melintasi yurisdiksi batas negara yang berbeda (misalnya kepatuhan terhadap GDPR di Eropa).
- Kasus penggunaan (*Use Cases*) *Public Cloud*:
  - Aplikasi dengan Beban Kerja Berfluktuasi: Bisnis yang mengalami lonjakan musiman, seperti toko daring saat promosi akhir tahun.
  - Lingkungan Uji Coba dan Pengembangan Cepat: Membangun prototipe aplikasi dan memvalidasi ide bisnis baru untuk mempercepat waktu peluncuran ke pasar (*time-to-market*).
  - Infrastruktur Sekunder Pemulihan Bencana (*Disaster Recovery*): Memanfaatkan cloud publik sebagai cadangan sistem utama tanpa perlu menyewa data center kedua.
  - Penyimpanan dan Distribusi Data Skala Besar: Mencadangkan arsip data perusahaan dan mendistribusikan konten multimedia secara global menggunakan CDN.
  - *Outsourcing* Sistem Non-Kritis: Menyerahkan pengelolaan aplikasi standar (seperti platform kolaborasi atau blog perusahaan) kepada penyedia cloud publik.

---

## 2. Private Cloud

### A. Definisi Standar NIST dan Model Penerapan
- Berdasarkan dokumen *National Institute of Standards and Technology* (NIST SP 800-145):
  - *Private Cloud* didefinisikan sebagai infrastruktur komputasi awan yang di-*provisioning* secara eksklusif untuk digunakan oleh satu organisasi tunggal yang terdiri dari berbagai unit bisnis atau konsumen internal.
  - Infrastruktur *Private Cloud* dapat dimiliki, dikelola, dan dioperasikan oleh organisasi itu sendiri, pihak ketiga, atau kombinasi keduanya, serta dapat berlokasi di dalam lingkungan kantor (*on-premises*) maupun di luar lokasi (*off-premises*).
- Dua model penerapan arsitektur *Private Cloud*:
  - *On-Premises Private Cloud*:
    - Infrastruktur server dan jaringan ditempatkan di dalam pusat data internal milik organisasi sendiri.
    - Seluruh proses pemeliharaan, keamanan fisik, pembaruan perangkat keras, dan pengawasan operasional dilakukan secara mandiri oleh tim TI internal perusahaan.
  - *Off-Premises Private Cloud* / *Virtual Private Cloud* (VPC):
    - Infrastruktur berjalan di atas pusat data milik penyedia cloud publik (seperti AWS atau IBM Cloud), namun dipartisi dan diisolasi secara logis serta kriptografis ketat.
    - Memberikan lingkungan komputasi privat mandiri yang aman di dalam cloud publik bersama, memadukan fleksibilitas dan efisiensi biaya publik dengan privasi kontrol *private cloud*.

### B. Manfaat Strategis dan Operasional Private Cloud
- Pemanfaatan Nilai Cloud di Bawah Kendali Internal:
  - Organisasi mendapatkan kemudahan alokasi mandiri (*self-service*), otomatisasi orkestrasi, dan virtualisasi sumber daya dengan kepastian bahwa tata kelola tetap berada di bawah pengawasan departemen TI internal.
- Optimalisasi Investasi Aset yang Ada (*Asset Utilization*):
  - Memanfaatkan kembali infrastruktur server dan perangkat penyimpanan lama (*legacy hardware*) yang sudah dibeli perusahaan dengan melapisinya menggunakan perangkat lunak orkestrasi cloud privat.
- Skalabilitas Dinamis dan Fenomena *Cloud Bursting*:
  - Kapasitas komputasi dasar dijalankan di atas *private cloud*.
  - Ketika terjadi lonjakan beban kerja yang melebihi kapasitas server internal, beban kerja tersebut dapat meluap (*burst*) secara otomatis ke instans *public cloud* untuk sementara waktu, lalu menyusut kembali ke *private cloud* setelah beban kembali normal:

$$
\text{Workload Capacity}(t) = 
\begin{cases} 
\text{Private Cloud Resources}, & \text{jika } \text{Traffic}(t) \le \text{Threshold}_{\text{Internal}} \\ 
\text{Private Cloud} + \text{Public Cloud Burst}, & \text{jika } \text{Traffic}(t) > \text{Threshold}_{\text{Internal}} 
\end{cases}
$$

- Keamanan Kustom dan Kepatuhan Ketat:
  - Kebijakan autentikasi, enkripsi perangkat keras, dan isolasi jaringan dapat disesuaikan secara presisi untuk memenuhi standar regulasi industri yang sangat ketat (seperti sektor perbankan, militer, dan kesehatan).

### C. Kasus Penggunaan (Use Cases) Private Cloud
- Modernisasi dan Penyatuan Aplikasi Warisan (*Legacy Applications*):
  - Mengonversi aplikasi lama yang berjalan di server fisik terisolasi ke dalam mesin virtual atau kontainer cloud privat, sehingga meningkatkan utilisasi perangkat keras.
- Pengolahan Data Sangat Rahasia dan Regulasi Ketat:
  - Menyimpan rekam medis pasien, data intelijen negara, atau riwayat transaksi keuangan nasabah yang secara hukum dilarang ditempatkan di cloud publik bersama.
- Integrasi Layanan Hibrida dari Dalam Data Center:
  - Membuka gerbang antarmuka aman dari data center internal agar dapat memanfaatkan kecerdasan layanan analitik eksternal tanpa memindahkan data mentah ke luar lingkungan privat.
- Portabilitas Aplikasi Tingkat Lanjut:
  - Membangun dan menguji aplikasi di lingkungan privat dengan kepastian bahwa aplikasi tersebut dapat dipindahkan ke lingkungan komputasi lain tanpa mengorbankan kepatuhan dan integritas keamanan.

---

## 3. Hybrid Cloud

### A. Definisi, Konsep Terpadu, dan Tiga Pilar Utama
- *Hybrid Cloud* merupakan lingkungan komputasi terpadu yang menghubungkan dan mengorkestrasi infrastruktur *private cloud* (termasuk pusat data *on-premises*) milik organisasi dengan satu atau lebih layanan *public cloud* pihak ketiga menjadi satu arsitektur yang tunggal, fleksibel, dan kohesif.
- Tiga pilar fondasi (*Core Tenants*) arsitektur *Hybrid Cloud*:
  - Interoperabilitas (*Interoperability*):
    - Kemampuan sistem pada lingkungan *private cloud* dan *public cloud* untuk saling berkomunikasi secara mulus, memahami format API yang sama, sinkronisasi skema data, konfigurasi jaringan, serta mekanisme autentikasi dan otorisasi terpadu.
  - Skalabilitas (*Scalability*):
    - Kemampuan memperluas kapasitas beban kerja privat ke cloud publik secara elastis saat menghadapi lonjakan kebutuhan komputasi (*cloud bursting*).
  - Portabilitas (*Portability*):
    - Kemampuan memindahkan beban kerja, layanan kontainer, dan berkas data secara bebas antar lingkungan privat dan publik tanpa keterikatan pada satu penyedia perangkat keras atau vendor tertentu (*avoiding vendor lock-in*).

### B. Spektrum Varian Hybrid Cloud
- Tiga variasi arsitektur dalam ekosistem hybrid:
  - *Hybrid Mono-Cloud*:
    - Mengintegrasikan pusat data *private cloud* internal organisasi dengan tepat satu penyedia *public cloud* spesifik (misalnya integrasi internal data center dengan IBM Cloud saja).
  - *Hybrid Multi-Cloud*:
    - Arsitektur berbasis standar terbuka (*open standards*) yang mengintegrasikan lingkungan privat internal dengan beberapa penyedia *public cloud* sekaligus (misalnya kombinasi server on-premises dengan AWS, Azure, dan Google Cloud).
    - Memberikan kebebasan strategis bagi organisasi untuk memilih layanan terbaik dari masing-masing penyedia (*best-of-breed services*).
  - *Composite Multi-Cloud*:
    - Varian paling granular di mana komponen-komponen berbeda dari satu aplikasi tunggal didistribusikan secara terpisah lintas berbagai penyedia cloud (misalnya antarmuka web di AWS, pemrosesan logika bisnis di Azure, dan basis data inti tetap di *private cloud* on-premises).

### C. Seri Tiga Bagian Arsitektur Hybrid Cloud oleh Sai Vennam (IBM)
- Panduan arsitektur komputasi awan hibrida modern yang dirumuskan oleh Sai Vennam (Advokat Pengembang IBM):
  - Bagian 1: Konektivitas (*Connect*):
    - Fokus pada interoperabilitas jaringan dan integrasi aman antar lingkungan yang heterogen.
    - Memanfaatkan teknologi sumber terbuka (*open source*) seperti kontainer berbasis Linux, orkestrasi Kubernetes, jala layanan (*service mesh*) Istio, alat manajemen lintas klaster (*multi-cluster management*), dan antrean pesan (*message brokers* seperti IBM MQ atau Apache Kafka) untuk menyatukan aliran data antar sistem on-premise dan cloud publik.
  - Bagian 2: Modernisasi (*Modernize*):
    - Berfokus pada strategi dekomposisi aplikasi monolitik warisan (*legacy monolithic applications*) menjadi arsitektur layanan mikro (*microservices*).
    - Memecah modul sistem yang kaku menjadi unit-unit independen yang dapat disebarkan ke cloud publik agar mampu memanfaatkan fitur penskalaan otomatis secara maksimal.
  - Bagian 3: Keamanan Terpadu (*Secure*):
    - Menjawab tantangan keamanan siber dan pengetatan regulasi privasi data global.
    - Memastikan organisasi dapat tetap mempertahankan aset data paling bernilai di lingkungan *on-premises* yang terlindungi ketat, sambil tetap aman menghubungkan antarmuka layanan tersebut ke ekosistem cloud publik modern.

### D. Keuntungan, Tantangan, dan Kasus Penggunaan Hybrid Cloud
- Keuntungan strategis:
  - Mengoptimalkan alokasi anggaran TI dengan menempatkan beban kerja pada lingkungan yang paling hemat biaya (*cost-efficient placement*).
  - Meningkatkan ketahanan bisnis (*resilience*) dengan menghilangkan ketergantungan pada kegagalan infrastruktur tunggal.
- Tantangan implementasi:
  - Kompleksitas tinggi dalam orkestrasi perutean jaringan, latensi komunikasi antar pusat data geografis, kompatibilitas kebijakan keamanan, serta sinkronisasi data yang konsisten.
- Kasus penggunaan (*Use Cases*) umum:
  - Integrasi SaaS (*SaaS Integration*): Menghubungkan aplikasi SaaS modern (seperti Salesforce) dengan sistem ERP perbankan yang berjalan di mainframe *on-premises*.
  - Integrasi Data dan Kecerdasan Buatan (Data and AI Integration): Menggabungkan data transaksional internal yang sensitif dengan model pembelajaran mesin canggih (*Machine Learning / AI*) yang tersedia di cloud publik.
  - Modernisasi Aplikasi Warisan Secara Bertahap (*Enhancing Legacy Apps*): Meningkatkan tampilan antarmuka web pengguna di cloud publik tanpa harus membongkar basis kode inti di server lama.
  - Migrasi Mesin Virtual VMware (*VMware Migration*): Memindahkan mesin virtual on-premise secara *lift-and-shift* ke cloud publik tanpa konversi format untuk mengurangi jejak fisik data center.

---

## 4. Expert Viewpoints: Service and Deployment Models

### A. Evaluasi Kematangan Perjalanan Cloud (Cloud Journey)
- Pertimbangan utama para pakar industri dalam menentukan model layanan dan model penerapan komputasi awan yang tepat bagi organisasi:
  - Skenario Desakan Waktu dan Akhir Masa Sewa (*Imminent Lease Expiration*):
    - Jika kontrak sewa pusat data fisik akan segera berakhir dalam hitungan minggu atau bulan, tim teknis tidak memiliki waktu yang cukup untuk menulis ulang arsitektur aplikasi menjadi *cloud-native*.
    - Solusi terbaik: Memilih model IaaS dengan metode pemindahan langsung (*Lift-and-Shift*), yaitu menyalin mesin virtual dari data center lokal langsung ke mesin virtual cloud publik tanpa mengubah konfigurasi internalnya.
  - Skenario Modernisasi Platform Berkelanjutan (*Re-platforming*):
    - Jika organisasi memiliki waktu adaptasi yang memadai, aplikasi dapat dipindahkan ke lingkungan PaaS atau platform berbasis kontainer (seperti Kubernetes atau OpenShift).
    - Penyedia cloud mengelola pembaruan sistem operasi dan tambalan keamanan, sementara tim pengembang hanya perlu menyesuaikan dependensi aplikasi.
  - Skenario Pembangunan Produk Baru dari Awal (*Greenfield Application*):
    - Untuk produk perangkat lunak baru yang baru dirintis, para pakar menyarankan langsung mengadopsi pendekatan *Functions as a Service* (FaaS) atau komputasi tanpa server (*Serverless*).
    - Memungkinkan peluncuran produk secara instan tanpa perlu memikirkan provisi server maupun pemeliharaan sistem operasi.

### B. Prinsip Emas: "Stay as High on the Stack as You Can"
- Filosofi arsitektur yang dianjurkan oleh praktisi cloud profesional:
  - Organisasi disarankan untuk selalu beroperasi pada tingkatan abstraksi tertinggi dari tumpukan teknologi yang masih mampu memenuhi kebutuhan bisnis organisasi:
    - Prioritas Pertama (SaaS): Pilihlah solusi SaaS jika aplikasi bisnis standar (seperti email, CRM, atau manajemen proyek) sudah tersedia di pasar, karena SaaS memberikan nilai bisnis instan dengan biaya investasi infrastruktur nol di luar biaya langganan.
    - Prioritas Kedua (PaaS): Jika bisnis memerlukan aplikasi khusus yang dibangun sendiri namun tidak memerlukan kustomisasi tingkat sistem operasi, pilihlah PaaS agar tim pengembang dapat fokus sepenuhnya pada rekayasa fitur perangkat lunak.
    - Prioritas Terakhir (IaaS): Turunlah ke model IaaS hanya apabila organisasi mutlak membutuhkan kendali penuh atas konfigurasi perangkat keras virtual, pengaturan kernel sistem operasi, atau topologi jaringan khusus yang tidak didukung oleh platform PaaS.
- Hubungan timbal balik antara fleksibilitas kendali dan beban operasional:

$$
\text{Total Overhead} = f(\text{Control Level}) \quad \implies \quad \text{Overhead}(\text{IaaS}) \gg \text{Overhead}(\text{SaaS})
$$

---

## 5. Community Cloud

### A. Definisi NIST SP 800-145 dan Rasional Penerapan
- Berdasarkan standar NIST SP 800-145:
  - *Community Cloud* didefinisikan sebagai infrastruktur komputasi awan yang di-*provisioning* secara eksklusif untuk digunakan bersama oleh suatu komunitas konsumen tertentu yang berasal dari organisasi-organisasi dengan kesamaan kepentingan, seperti kesamaan misi strategis, persyaratan keamanan, kebijakan tata kelola, dan pertimbangan kepatuhan hukum.
  - Infrastruktur ini dapat dimiliki, dikelola, dan dioperasikan oleh satu atau lebih organisasi di dalam komunitas tersebut, pihak ketiga, atau kombinasi keduanya, serta dapat berlokasi secara *on-premises* maupun *off-premises*.
- Faktor pendorong pembentukan *Community Cloud*:
  - Penegakan Kerangka Keamanan Bersama: Seluruh anggota komunitas tunduk dan diikat oleh matriks kontrol keamanan siber yang seragam.
  - Kualifikasi Atribut Personel Dukungan (*Personhood & Citizenship*): Menjamin bahwa seluruh staf teknis yang memelihara sistem memiliki kewarganegaraan, izin keamanan (*security clearance*), dan lokasi fisik kerja yang memenuhi ketentuan hukum komunitas (misalnya lembaga intelijen atau pertahanan negara).
  - Jaminan Lokalisasi dan Kedaulatan Data (*Data Localization*): Menjamin data tidak pernah meninggalkan batas teritorial negara atau wilayah hukum tertentu.
  - Batas Parameter Keamanan Khusus (*Defined Security Perimeter*): Membangun benteng pertahanan digital yang melingkupi seluruh infrastruktur komunitas dari ancaman eksternal.

### B. Komparasi: Community Cloud Tradisional vs Software-Defined
- Perbedaan arsitektur antara implementasi tradisional berbasis isolasi fisik dengan pendekatan modern berbasis perangkat lunak (*Software-Defined Community Cloud* seperti Google Cloud Platform Assured Workloads):
  - Dimensi Eksklusivitas Infrastruktur (*Infrastructure Exclusivity*):
    - *Definisi NIST SP 800-145*: Infrastruktur cloud di-*provisioning* untuk penggunaan eksklusif oleh komunitas konsumen tertentu dengan kesamaan kepentingan.
    - *Implementasi Tradisional*: Mengharuskan pemisahan pusat data fisik dan fasilitas perangkat keras khusus secara total dari cloud publik komersial.
    - *Implementasi Software-Defined*: Setiap proyek (*project*) bertindak sebagai *private cloud* terisolasi yang dibangun di atas unit kapasitas primitif (*infrastructure primitives*) yang terisolasi secara kriptografis dan logis.
  - Dimensi Kontrol Keamanan Bersama (*Common Security Controls*):
    - *Definisi NIST SP 800-145*: Standar keamanan yang seragam diaplikasikan ke seluruh entitas pengguna di dalam komunitas.
    - *Implementasi Tradisional*: Kebijakan keamanan diterapkan secara kaku pada perangkat keras fisik tunggal yang digunakan bersama oleh anggota komunitas.
    - *Implementasi Software-Defined*: Aturan kebijakan *Assured Workloads* dikonfigurasi secara deklaratif melalui perangkat lunak dan ditegakkan melalui perjanjian tingkat layanan (*terms of service*).
  - Dimensi Atribut dan Kewarganegaraan Staf Dukungan (*Personhood & Citizenship*):
    - *Definisi NIST SP 800-145*: Infrastruktur dapat dioperasikan oleh organisasi komunitas, pihak ketiga, atau gabungan keduanya.
    - *Implementasi Tradisional*: Personel dukungan teknis wajib ditempatkan secara fisik di fasilitas gedung khusus yang terpisah.
    - *Implementasi Software-Defined*: Layanan manajemen akses (*Access Management Service*) menyaring dan membatasi tiket dukungan teknis hanya kepada staf yang memenuhi atribut kewarganegaraan, sertifikasi izin, dan lokasi kerja yang disyaratkan secara otomatis.
  - Dimensi Lokalisasi Data (*Data Localization*):
    - *Definisi NIST SP 800-145*: Infrastruktur dapat berada di dalam maupun di luar lokasi fisik (*on or off premises*).
    - *Implementasi Tradisional*: Menggunakan perangkat penyimpanan fisik khusus yang secara mekanis didedikasikan bagi komunitas.
    - *Implementasi Software-Defined*: Penempatan dan penguncian lokasi data di wilayah yurisdiksi tertentu ditegakkan secara otomatis melalui kebijakan berbasis perangkat lunak (*software policies*).
  - Dimensi Batas Parameter Keamanan (*Defined Security Perimeter*):
    - *Definisi NIST SP 800-145*: Penetapan batas keamanan yang melindungi lingkungan komunitas.
    - *Implementasi Tradisional*: Seluruh komunitas berada di dalam satu enklaf (*enclave*) jaringan fisik yang sama.
    - *Implementasi Software-Defined*: Setiap proyek mandiri merupakan enklaf logisnya sendiri (*per-project enclave*), mencegah pergerakan lateral ancaman antar proyek anggota komunitas.

### C. Konsep Software-Defined Government Cloud dan Keuntungannya
- Arsitektur Berbasis Primitif Infrastruktur (Studi Kasus Google Cloud Platform):
  - Dalam platform GCP, sebuah *Project* merupakan pengelompokan logis dari unit-unit primitif infrastruktur (*infrastructure primitives*), yaitu unit kapasitas atomik seperti mesin virtual (*Compute Engine*), cakram persisten (*Persistent Disk*), dan wadah penyimpanan (*Cloud Storage Buckets*).
  - Komponen tingkat rendah seperti *hypervisor* dan blok data pada sistem berkas terdistribusi diisolasi secara ketat menggunakan enkripsi kriptografis dan abstraksi perangkat lunak.
  - Saat sebuah proyek dilapisi oleh batasan *Assured Workloads*, enklaf proyek privat tersebut secara otomatis bertransformasi menjadi *Software-Defined Community Cloud* (atau *Government Cloud* modern).
- Keuntungan utama pendekatan berbasis perangkat lunak:
  - Adopsi Inovasi dan Layanan Baru Cepat: Pengguna *Community Cloud* dapat langsung menikmati pembaruan prosesor, GPU AI terbaru, dan fitur cloud mutakhir tanpa menunggu pembangunan fasilitas data center fisik baru yang memakan waktu bertahun-tahun.
  - Skala dan Ketersediaan Lebih Tinggi: Memanfaatkan keandalan jaringan tulang punggung (*backbone network*) global penyedia cloud skala besar.
  - Penegakan dan Audit Kepatuhan Otomatis: Batas kepatuhan diatur secara terprogram dan dapat diaudit secara *real-time* menggunakan dasbor kepatuhan otomatis.

---

## 6. Rangkuman Pelajaran Modul 2 (Deployment Models)

### A. Sintesis Karakteristik Empat Model Deployment
- *Public Cloud*:
  - Infrastruktur multi-tenant dimiliki dan dioperasikan sepenuhnya oleh penyedia cloud publik pihak ketiga.
  - Menawarkan efisiensi biaya tertinggi, skalabilitas masif, dan pemeliharaan tanpa beban bagi pengguna.
- *Private Cloud*:
  - Infrastruktur di-*provisioning* secara eksklusif untuk satu organisasi tunggal.
  - Dapat diimplementasikan secara internal (*on-premises*) maupun eksternal melalui partisi logis (*Virtual Private Cloud* / VPC).
  - Menawarkan kendali keamanan maksimal, pemanfaatan aset lama, serta mekanisme *cloud bursting*.
- *Hybrid Cloud*:
  - Mengintegrasikan lingkungan privat (*on-premises*) dengan satu atau lebih cloud publik menjadi satu ekosistem terpadu.
  - Berlandaskan pada prinsip interoperabilitas, skalabilitas dinamis, dan portabilitas aplikasi lintas vendor.
- *Community Cloud*:
  - Infrastruktur yang dibangun khusus untuk melayani sekelompok organisasi dengan kesamaan misi, standar kepatuhan regulasi, dan profil risiko keamanan.
  - Telah bertransformasi dari isolasi fasilitas fisik kaku menjadi *software-defined assured clouds* yang fleksibel dan berkinerja tinggi.

### B. Kesimpulan Strategis Pengambilan Keputusan
- Tidak ada satu model penerapan komputasi awan yang unggul mutlak untuk seluruh jenis beban kerja.
- Keputusan arsitektur modern berorientasi pada pendekatan hibrida (*hybrid multi-cloud*), di mana organisasi menempatkan data rahasia dan regulasi ketat di *private cloud* atau *community cloud*, memanfaatkan *public cloud* untuk beban kerja dinamis dan inovasi cepat, serta menerapkan prinsip *"stay as high on the stack as you can"* guna memaksimalkan efisiensi dan nilai bisnis.
