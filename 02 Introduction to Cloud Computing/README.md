# Introduction to Cloud Computing

Dokumen ini merupakan ringkasan eksekutif dan panduan master dokumentasi untuk kursus Introduction to Cloud Computing, bagian kedua dari program sertifikasi profesional IBM DevOps and Software Engineering Professional Certificate. Kursus ini menyajikan fondasi komprehensif mengenai prinsip-prinsip komputasi awan, model layanan (IaaS, PaaS, SaaS), model penyebaran (Public, Private, Hybrid, Community Cloud), arsitektur infrastruktur fisik dan virtualisasi, penyimpanan awan dan CDN, tren mutakhir cloud-native (Microservices, Serverless, DevOps on Cloud, Application Modernization), tata kelola keamanan (IAM, Enkripsi, Monitoring), hingga implementasi proyek akhir pada IBM Cloud Code Engine.

---

### Bagian 1: Struktur Modul Kursus

1. **Module 01 - Overview of Cloud Computing**
2. **Module 02 - Cloud Computing Models**
3. **Module 03 - Components of Cloud Computing**
4. **Module 04 - Emergent Trends and Practices**
5. **Module 05 - Cloud Security, Monitoring, Case Studies, Jobs**
6. **Module 06 - Final Project and Assignment**

---

### Bagian 2: Rangkuman Eksekutif per Modul

#### Modul 1: Overview of Cloud Computing
- Menguraikan definisi resmi komputasi awan menurut NIST SP 800-145 dan evolusinya dari era mainframe time-sharing (1950-an), penemuan mesin virtual (1970-an), hingga model komputasi utilitas modern.
- Menjabarkan lima karakteristik esensial komputasi awan: *On-Demand Self-Service*, *Broad Network Access*, *Resource Pooling*, *Rapid Elasticity*, dan *Measured Service*.
- Menganalisis urgensi adopsi cloud sebagai imperatif bisnis: pergeseran belanja modal awal (*CapEx*) menjadi biaya operasional berkala (*OpEx*), percepatan waktu rilis produk ke pasar (*time-to-market*), dan elastisitas menghadapi ledakan volume data global.
- Membedah studi kasus adopsi enterprise pada American Airlines, UBank, Bitly, dan ActivTrades.
- Menjelaskan bagaimana cloud menjadi akselerator teknologi mutakhir (*emerging technologies*): Internet of Things (IoT) untuk konservasi satwa liar di Welgevonden Afrika Selatan, kecerdasan buatan (AI) Watson pada turnamen US Open, integrasi blockchain IBM Food Trust pada keterlacakan pasokan pangan Salinas Valley, serta pemeliharaan prediktif KONE.

#### Modul 2: Cloud Computing Models
- Membedah tiga pilar model layanan (*Service Models*) melalui piramida abstraksi: *Infrastructure as a Service* (IaaS), *Platform as a Service* (PaaS), dan *Software as a Service* (SaaS), dilengkapi analogi kepemilikan mobil oleh perancang IBM Cloud Tessa Rhodes.
- Mengkaji pembagian tanggung jawab operasional (*shared responsibility model*) antara penyedia cloud dan konsumen untuk masing-masing model layanan.
- Mengulas empat model penyebaran (*Deployment Models*): Public Cloud (skala ekonomi multi-tenant masif), Private Cloud (isolasi on-premises dan Virtual Private Cloud / VPC), Hybrid Cloud (tiga pilar: interoperabilitas, skalabilitas, dan portabilitas), serta evolusi Community Cloud dari fasilitas fisik kaku menjadi *software-defined assured workloads*.
- Menguraikan variasi hibrida (Hybrid Mono-Cloud, Hybrid Multi-Cloud, dan Composite Multi-Cloud) serta prinsip emas arsitektur oleh praktisi industri: *"Stay as high on the stack as you can"*.

#### Modul 3: Components of Cloud Computing
- Mengupas tuntas hierarki fisik infrastruktur cloud: pusat data (*Data Centers*), zona ketersediaan terisolasi (*Availability Zones*), kawasan geografis (*Regions*), dan jaringan tulang punggung latensi rendah (*Points of Presence* / PoPs).
- Membedah teknologi virtualisasi dan klasifikasi Hypervisor: Type 1 Bare Metal (KVM, VMware ESXi) versus Type 2 Hosted (VirtualBox), serta perbandingan mendalam antara Virtual Machines multi-tenant, instans Spot/Transient, Reserved Instances, Dedicated Hosts, dan Bare Metal Servers berkinerja ekstrem.
- Menganalisis arsitektur dan karakteristik tiga jenis media simpan awan: *File Storage* (sistem berkas hierarkis multi-mount NFS/SMB dengan formula perhitungan IOPS), *Block Storage* (volume mentah terisolasi simpul tunggal berlatensi ultra-rendah via Fibre Channel SAN untuk OS dan DBMS transaksional), serta *Object Storage* (wadah datar berbasis metadata dengan persistensi tak terbatas dan API kompatibel S3).
- Menguraikan strategi tingkatan penyimpanan (*Storage Tiers*: Standard, Cool, Cold, Archive), kebijakan siklus hidup otomatis, serta peran krusial *Content Delivery Networks* (CDNs) dalam memangkas latensi penyaluran multimedia global.

#### Modul 4: Emergent Trends and Practices
- Menganalisis sinergi arsitektur *Hybrid Multi-Cloud* untuk mencegah keterikatan vendor (*vendor lock-in*) melalui studi kasus penskalaan dinamis layanan pengiriman bunga dan dekomposisi aplikasi *composite cloud* lintas benua.
- Membedah dekomposisi sistem monolitik menuju arsitektur layanan mikro (*microservices*): pengemasan kontainer mandiri, tumpukan teknologi poliglota, komunikasi asinkron via REST API dan event streaming, serta studi kasus platform streaming "Dream Game".
- Mengulas paradigma komputasi nirserver (*Serverless Computing* / FaaS): eksekusi berbasis kejadian (*event-driven*), kontainer nir-status (*stateless*), formula penagihan murni berbasis konsumsi tanpa biaya saat menganggur (*never pay for idle*), tantangan *cold start*, serta batasan proses jangka panjang.
- Menjabarkan arsitektur lima lapisan aplikasi *cloud-native* oleh Andrea Crawford dan konsep komoditisasi tumpukan solusi (Istio dan Knative).
- Mengkaji integrasi alur kerja *DevOps on the Cloud* (CI/CD pipeline, citra kekal, Infrastructure as Code, dan padanan alat di AWS, Azure, GCP, dan IBM Cloud) serta trilogi modernisasi aplikasi terpadu oleh Eric Minick (Arsitektur + Infrastruktur + Cara Kerja).

#### Modul 5: Cloud Security, Monitoring, Case Studies, Jobs
- Membedah lanskap ancaman siber cloud: *insider threats*, serangan DDoS via SNMP, *data breaches*, dan miskonfigurasi sistem.
- Menjelaskan model tanggung jawab bersama pada keamanan, lima pilar kerangka kerja keamanan siber NIST (Identify, Protect, Detect, Respond, Recover), serta peran otomatisasi *Cloud Security Posture Management* (CSPM).
- Menguraikan tata kelola *Identity and Access Management* (IAM) sebagai garis pertahanan pertama: prinsip hak istimewa terkecil (*PoLP*), kebijakan MFA, serta protokol federasi identitas enterprise (SAML 2.0 dan OpenID Connect).
- Mengupas enkripsi sebagai garis pertahanan terakhir: perlindungan kriptografi pada tiga status data (*at rest*, *in transit*, dan *in use* / *Confidential Computing*), serta praktik terbaik manajemen kunci (KMS).
- Menjabarkan teknik observabilitas cloud: Infrastructure Monitoring, Database Monitoring, Application Performance Monitoring (APM), audit pergeseran konfigurasi IaC (*configuration drift*), dan pelacakan panggilan API (AWS CloudTrail, Azure Activity Logs, GCP Audit Logging).
- Menganalisis studi kasus enterprise nyata: The Weather Company (250 miliar prakiraan/hari di IBM Kubernetes), American Airlines (swalayan digital IROPS), Cementos Pacasmayo (SAP S/4HANA on Cloud), Welch's Food (Hybrid Cloud koperatif), dan LSPI (migrasi penuh ke cloud).
- Memaparkan peluang karir, riset proyeksi pasar global ($1.554,94 Miliar pada 2030, CAGR 14,1%), indeks kesulitan rekrutmen Gartner (skor 78), profil enam peran spesialisasi cloud, dan strategi sertifikasi resmi.

#### Modul 6: Final Project and Assignment
- Menyajikan panduan tutorial praktikum mandiri (*Hands-on Lab Tutorial*): modernisasi aplikasi web "Guess the Capital" dari pengujian lokal, pembuatan Dockerfile berbasis peladen Nginx, pembangunan citra kontainer, pengunggahan citra ke IBM Cloud Container Registry (ICR), hingga deployment aplikasi nirserver di platform IBM Cloud Code Engine dengan URL akses publik.
- Menguraikan analisis studi kasus arsitektur enterprise DineEase: dekomposisi aplikasi pemesanan makanan monolitik menjadi arsitektur cloud-native pada ekosistem IBM Cloud yang mencakup sembilan pemetaan solusi: Multizone Regions (MZR untuk ketersediaan 99,99%), Bare Metal GPU (pemrosesan pembayaran anti-fraud terisolasi), IBM Cloud Kubernetes Service (orkestrasi kontainer poliglota), API Connect (gerbang perutean terpusat), IBM Cloudant (NoSQL dokumen JSON ulasan offline-first), IBM Db2 on Cloud (RDBMS transaksional HADR), Cloud CDN (distribusi foto makanan cepat), Cloud Load Balancer (penyeimbang beban multi-zona), dan IBM Cloud Monitoring (observabilitas waktu nyata berbasis Sysdig).

---

### Bagian 3: Key Takeaways

- **Komputasi Awan adalah Transformasi Model Bisnis:**
  - Cloud bukan sekadar memindahkan server fisik ke data center milik pihak ketiga, melainkan perubahan mendasar dari belanja modal kaku (*CapEx*) menjadi biaya operasional yang fleksibel (*OpEx*), memungkinkan inovasi cepat tanpa risiko finansial infrastruktur awal.
- **Pilihlah Tingkatan Abstraksi Tertinggi yang Memenuhi Kebutuhan:**
  - Selalu terapkan prinsip *"stay as high on the stack as you can"*. Prioritaskan solusi SaaS jika aplikasi standar telah tersedia, manfaatkan PaaS/Serverless untuk pengembangan aplikasi bisnis, dan turunlah ke IaaS/Bare Metal hanya saat kontrol perangkat keras dan isolasi khusus mutlak disyaratkan.
- **Modernisasi Aplikasi adalah Trilogi Terpadu:**
  - Keberhasilan transformasi cloud enterprise menuntut keselarasan simultan antara pembaruan arsitektur (menuju microservices), adopsi infrastruktur (kontainer dan cloud elastis), serta transformasi cara kerja (metodologi Agile, budaya DevOps, dan keandalan SRE).
- **Keamanan Berlapis Melalui IAM, Enkripsi, dan Observabilitas:**
  - Terapkan arsitektur *Zero Trust* dengan membatasi hak akses pengguna secara ketat (*PoLP*), amankan data di seluruh status siklus hidupnya (*at rest*, *in transit*, *in use*), dan pantau seluruh pertukaran data serta panggilan API untuk audit kepatuhan tanpa celah.
- **Elastisitas dan Portabilitas Melalui Standar Terbuka:**
  - Mengadopsi teknologi berbasis kontainer (Docker dan Kubernetes) pada lingkungan *hybrid multi-cloud* memberikan jaminan portabilitas aplikasi, penskalaan dinamis saat bencana, dan perlindungan strategis dari keterikatan pada satu vendor penyedia cloud.
