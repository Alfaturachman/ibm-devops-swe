# IBM DevOps and Software Engineering Professional Certificate

Repositori ini memuat dokumentasi komprehensif, catatan studi terstruktur, studi kasus arsitektur, dan implementasi proyek praktis untuk program sertifikasi profesional **IBM DevOps and Software Engineering Professional Certificate** dari Coursera. Program ini dirancang oleh para insinyur dan arsitek IBM untuk membekali praktisi rekayasa perangkat lunak modern dengan penguasaan metodologi *Agile*, budaya dan kerangka kerja *DevOps*, komputasi awan (*Cloud Computing*), otomasi *CI/CD*, infrastruktur berbasis kode (*Infrastructure as Code*), kontainerisasi, arsitektur *microservices*, *Test-Driven Development* (TDD), pengujian keamanan terintegrasi (*DevSecOps*), hingga pemantauan sistem (*observability*).

---

## Comprehensive Curriculum Breakdown (15 Courses)

### Course 01: Introduction to DevOps [COMPLETED]
- Deskripsi: Fondasi filosofis, budaya, dan metodologi DevOps modern. Menjelajahi sejarah lahirnya DevOps, penghapusan sekat silo organisasi (*wall of confusion*), kerangka kerja CALMS (*Culture, Automation, Lean, Measurement, Sharing*), transformasi pola pikir (*Thinking DevOps*), alur kerja terintegrasi (*Working DevOps*), struktur tim lintas fungsi berdasarkan hukum Conway (*Organizing for DevOps*), empat metrik utama DORA (*Measuring DevOps*), serta bedah studi kasus industri nyata.
- [Course 01: Introduction to DevOps](./01%20Introduction%20to%20DevOps/README.md) menjadi fondasi dasar bagi seluruh spesialisasi ini. Materi terbagi menjadi enam modul pembelajaran mendalam:
  - [Module 01: Overview of DevOps](./01%20Introduction%20to%20DevOps/Module%2001%20-%20Overview%20of%20DevOps/):
    - Memahami sejarah evolusi pengembangan perangkat lunak dari metode Waterfall tradisional yang kaku menuju Agile dan DevOps.
    - Menghancurkan dinding kebingungan (*Wall of Confusion*) yang memisahkan tim pengembang (berorientasi perubahan fitur cepat) dan tim operasional (berorientasi stabilitas sistem).
    - Mempelajari kerangka kerja CALMS (*Culture, Automation, Lean, Measurement, Sharing*) sebagai pilar kesuksesan implementasi.
    - Mengidentifikasi anti-pola DevOps (*silo baru, tim DevOps terpisah*) dan membuktikan nilai bisnis percepatan waktu peluncuran ke pasar (*faster time-to-market*).
  - [Module 02: Thinking DevOps](./01%20Introduction%20to%20DevOps/Module%2002%20-%20Thinking%20DevOps/):
    - Menanamkan transformasi budaya dan pola pikir kolaboratif (*Growth Mindset*).
    - Membangun lingkungan kerja yang aman dari rasa takut gagal (*Fail-Safe Environment* dan *Psychological Safety*).
    - Menerapkan budaya pembelajaran berkelanjutan (*Continuous Learning*) dan perbaikan proses secara terus-menerus (*Continuous Improvement / Kaizen*).
    - Strategi rekrutmen talenta berbasis wawancara perilaku (*Behavioral Interviewing*) untuk menilai kesesuaian nilai budaya tim.
  - [Module 03: Working DevOps](./01%20Introduction%20to%20DevOps/Module%2003%20-%20Working%20DevOps/):
    - Alur kerja rekayasa modern yang mengintegrasikan prinsip *Continuous Integration* (CI), *Continuous Delivery* (CD), dan *Continuous Deployment*.
    - Penerapan prinsip pengujian lebih awal (*Shift-Left Testing*) untuk mendeteksi cacat kode pada tahap perancangan awal.
    - Penerapan keamanan sejak dini (*Shift-Left Security / DevSecOps*) guna memangkas biaya perbaikan kerentanan sistem.
    - Otomatisasi pengujian dan pengelolaan lingkungan menggunakan konsep Infrastruktur sebagai Kode (*Infrastructure as Code* / IaC).
  - [Module 04: Organizing for DevOps](./01%20Introduction%20to%20DevOps/Module%2004%20-%20Organizing%20for%20DevOps/):
    - Mendesain struktur organisasi berbasis tim lintas fungsi (*Cross-Functional Teams*) yang memiliki otonomi penuh dari hulu ke hilir.
    - Penerapan Hukum Conway (*Conway's Law*): Struktur arsitektur sistem perangkat lunak mencerminkan struktur komunikasi organisasi.
    - Model tim inovatif: Aturan Tim Dua Piza Amazon (*Amazon Two-Pizza Teams*) untuk menjaga kelincahan komunikasi, serta model Spotify (*Squads, Tribes, Chapters, Guilds*).
    - Siklus pengambilan keputusan cepat berbasis *OODA Loop* (*Observe, Orient, Decide, Act*).
  - [Module 05: Measuring DevOps](./01%20Introduction%20to%20DevOps/Module%2005%20-%20Measuring%20DevOps/):
    - Pengukuran efektivitas kinerja pengiriman perangkat lunak berbasis data empiris.
    - Penguasaan Empat Metrik Kunci DORA (*DevOps Research and Assessment*):
      - Frekuensi Penggelaran (*Deployment Frequency*): Seberapa sering kode dideploy ke lingkungan produksi.
      - Waktu Tunggu Perubahan (*Lead Time for Changes*): Durasi dari komit kode hingga berjalan di lingkungan produksi.
      - Tingkat Kegagalan Perubahan (*Change Failure Rate*): Persentase deployment yang menyebabkan insiden atau degradasi layanan.
      - Waktu Pemulihan Layanan (*Time to Restore Service / MTTR*): Waktu yang dibutuhkan untuk memulihkan sistem dari gangguan produksi.
    - Membedakan metrik yang dapat ditindaklanjuti (*Actionable Metrics*) dari sekadar metrik semu yang menyesatkan (*Vanity Metrics*).
    - Memantau metrik sosial dan kepuasan tim (*Social Metrics*) untuk mencegah kelelahan kerja (*burnout*).
  - [Module 06: Case Studies and Final Exam](./01%20Introduction%20to%20DevOps/Module%2006%20-%20Case%20Studies%20and%20Final%20Exam/):
    - Analisis studi kasus nyata pada transformasi enterprise berskala global.
    - Penyelesaian skenario praktis: Otomasi *pipeline* rilis, migrasi sistem monolitik menuju arsitektur *microservices*, penanganan insiden produksi darurat dengan *post-mortem* tanpa menyalahkan (*blameless post-mortem*), dan pemecahan ujian akhir komprehensif.

### Course 02: Introduction to Cloud Computing [COMPLETED]
- Deskripsi: Pengenalan arsitektur dan model operasional komputasi awan. Mempelajari model layanan (*IaaS, PaaS, SaaS*), model penerapan (*Public, Private, Hybrid, Community Cloud*), prinsip *software-defined cloud*, virtualisasi, komponen infrastruktur (komputasi, jaringan, *object storage*), kasus bisnis transisi CapEx ke OpEx, integrasi teknologi mutakhir (*AI, IoT, Blockchain*), tren *cloud native* (*Microservices, Serverless, DevOps on Cloud*), tata kelola keamanan (*IAM, Enkripsi, Observabilitas*), serta implementasi proyek akhir pada IBM Cloud Code Engine.
- [Course 02: Introduction to Cloud Computing](./02%20Introduction%20to%20Cloud%20Computing/README.md) menyajikan fondasi komprehensif mengenai prinsip-prinsip komputasi awan modern, model layanan, arsitektur infrastruktur fisik dan virtualisasi, tren *cloud native*, tata kelola keamanan, hingga penerapan praktis pada platform nirserver. Materi terbagi menjadi enam modul pembelajaran terstruktur:
  - [Module 01: Overview of Cloud Computing](./02%20Introduction%20to%20Cloud%20Computing/Module%2001%20-%20Overview%20of%20Cloud%20Computing/):
    - Memahami definisi resmi komputasi awan menurut NIST SP 800-145 dan evolusi historisnya dari era mainframe time-sharing (1950-an), penemuan mesin virtual (1970-an), hingga komputasi utilitas modern.
    - Menguasai lima karakteristik esensial komputasi awan: *On-Demand Self-Service*, *Broad Network Access*, *Resource Pooling*, *Rapid Elasticity*, dan *Measured Service*.
    - Menganalisis imperatif bisnis: pergeseran belanja modal awal (*CapEx*) menjadi biaya operasional berkala (*OpEx*), percepatan waktu rilis produk ke pasar (*time-to-market*), dan elastisitas beban kerja.
    - Mengkaji peran cloud sebagai akselerator teknologi mutakhir: integrasi IoT untuk konservasi satwa liar di Welgevonden Afrika Selatan, kecerdasan buatan (*AI*) Watson pada turnamen tenis US Open, serta ketertelusuran rantai pasok pangan berbasis blockchain (IBM Food Trust).
  - [Module 02: Cloud Computing Models](./02%20Introduction%20to%20Cloud%20Computing/Module%2002%20-%20Cloud%20Computing%20Models/):
    - Membedah piramida abstraksi model layanan: *Infrastructure as a Service* (IaaS), *Platform as a Service* (PaaS), dan *Software as a Service* (SaaS), serta analogi kepemilikan mobil oleh perancang IBM Cloud Tessa Rhodes.
    - Menguasai matriks pembagian tanggung jawab operasional (*shared responsibility model*) antara penyedia layanan cloud dan konsumen.
    - Menganalisis empat model penyebaran (*deployment models*): Public Cloud (multi-tenant berskala ekonomi masif), Private Cloud (isolasi on-premises dan Virtual Private Cloud / VPC), Hybrid Cloud (tiga pilar: interoperabilitas, skalabilitas, dan portabilitas), serta Community Cloud berbasis kebijakan (*software-defined assured workloads*).
    - Memahami arsitektur Hybrid Mono-Cloud, Hybrid Multi-Cloud, dan Composite Multi-Cloud, serta penerapan prinsip arsitektur: *"Stay as high on the stack as you can"*.
  - [Module 03: Components of Cloud Computing](./02%20Introduction%20to%20Cloud%20Computing/Module%2003%20-%20Components%20of%20Cloud%20Computing/):
    - Mengupas hierarki infrastruktur fisik: *Data Centers*, *Availability Zones*, *Regions*, dan *Point of Presence* (PoP) latensi rendah.
    - Membedah teknologi virtualisasi dan klasifikasi Hypervisor: Type 1 Bare Metal (KVM, ESXi) versus Type 2 Hosted (VirtualBox), serta perbandingan VM multi-tenant, instans Spot/Transient, Reserved Instances, Dedicated Hosts, dan Bare Metal Servers berkinerja ekstrem.
    - Menganalisis karakteristik tiga jenis media simpan awan: *File Storage* (hierarkis multi-mount NFS/SMB), *Block Storage* (volume mentah terisolasi simpul tunggal berlatensi ultra-rendah via SAN untuk DBMS transaksional), dan *Object Storage* (wadah datar berbasis metadata dengan persistensi tak terbatas dan API kompatibel S3).
    - Menerapkan strategi tingkatan penyimpanan (*Storage Tiers*), kebijakan siklus hidup otomatis, serta akselerasi pengiriman konten melalui *Content Delivery Network* (CDN).
  - [Module 04: Emergent Trends and Practices](./02%20Introduction%20to%20Cloud%20Computing/Module%2004%20-%20Emergent%20Trends%20and%20Practices/):
    - Menganalisis strategi Hybrid Multi-Cloud untuk mencegah keterikatan vendor (*vendor lock-in*) melalui orkestrasi beban kerja dinamis.
    - Membedah dekomposisi sistem monolitik menuju arsitektur layanan mikro (*microservices*): pengemasan kontainer mandiri, tumpukan teknologi poliglota, serta komunikasi asinkron berbasis REST API dan antrean pesan.
    - Menguasai paradigma komputasi nirserver (*Serverless Computing* / FaaS): eksekusi berbasis kejadian (*event-driven*), kontainer nir-status (*stateless*), penagihan murni berbasis konsumsi tanpa biaya saat menganggur (*never pay for idle*), serta mitigasi penundaan mula dingin (*cold start*).
    - Mengkaji prinsip aplikasi *cloud native* (*Twelve-Factor App*), integrasi alur kerja *DevOps on the Cloud* (CI/CD pipeline, citra kekal, Infrastructure as Code), serta trilogi modernisasi aplikasi (Arsitektur + Infrastruktur + Cara Kerja).
  - [Module 05: Cloud Security, Monitoring, Case Studies, Jobs](./02%20Introduction%20to%20Cloud%20Computing/Module%2005%20-%20Cloud%20Security%2C%20Monitoring%2C%20Case%20Studies%2C%20Jobs/):
    - Membedah lanskap ancaman siber cloud: *insider threats*, serangan DDoS, kebocoran data, serta model tanggung jawab bersama pada keamanan siber NIST (Identify, Protect, Detect, Respond, Recover).
    - Menguraikan tata kelola *Identity and Access Management* (IAM): prinsip hak akses terendah (*PoLP*), autentikasi multifaktor (MFA), dan federasi identitas enterprise (SAML 2.0, OpenID Connect).
    - Menguasai enkripsi data pada tiga fase (*at rest*, *in transit*, dan *in use* / *Confidential Computing*) serta manajemen kunci kriptografi (KMS).
    - Menjabarkan teknik observabilitas terpadu: pemantauan infrastruktur, pemantauan basis data, Application Performance Monitoring (APM), serta audit log panggilan API.
    - Menganalisis studi kasus enterprise nyata: The Weather Company, American Airlines, Cementos Pacasmayo, Welch's Food, dan LSPI, serta membedah lanskap karier spesialisasi cloud.
  - [Module 06: Final Project and Assignment](./02%20Introduction%20to%20Cloud%20Computing/Module%2006%20-%20Final%20Project%20and%20Assignment/):
    - Menyelesaikan proyek akhir praktikum mandiri (*Hands-on Lab*): pengemasan aplikasi web interaktif "Guess the Capital" ke dalam citra kontainer Docker berbasis Nginx, publikasi citra ke IBM Container Registry (ICR), dan deployment ke platform nirserver IBM Cloud Code Engine dengan akses HTTPS publik.
    - Menyusun rancangan solusi arsitektur enterprise DineEase 2.0: memodernisasi platform pengiriman makanan monolitik ke microservices cloud-native pada ekosistem IBM Cloud melalui sembilan pemetaan layanan (MZR, Bare Metal GPU, IKS/OpenShift, API Connect, Cloudant NoSQL, Db2 on Cloud, Cloud CDN, Load Balancer, dan IBM Cloud Monitoring).

### Course 03: Introduction to Agile Development and Scrum [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Prinsip-prinsip *Agile Manifesto* dan implementasi praktis kerangka kerja *Scrum*. Mempelajari peran dalam Scrum (*Product Owner, Scrum Master, Developers*), artefak Scrum (*Product Backlog, Sprint Backlog, Increment*), upacara/seremoni (*Sprint Planning, Daily Standup, Sprint Review, Sprint Retrospective*), penulisan *User Stories*, estimasi menggunakan *Story Points*, dan manajemen papan Kanban.
- Akses Modul: [03 Introduction to Agile Development and Scrum](./03%20Introduction%20to%20Agile%20Development%20and%20Scrum/)

### Course 04: Introduction to Software Engineering [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Dasar-dasar rekayasa perangkat lunak modern dan siklus hidup pengembangan sistem (*Software Development Life Cycle* / SDLC). Mencakup metodologi analisis kebutuhan, prinsip desain perangkat lunak berorientasi objek (OOPS), arsitektur modular, pola desain (*design patterns*), manajemen konfigurasi, dan jaminan kualitas (*Quality Assurance*).
- Akses Modul: [04 Introduction to Software Engineering](./04%20Introduction%20to%20Software%20Engineering/)

### Course 05: Getting Started with Git and GitHub [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Penguasaan sistem kendali versi terdistribusi (*Distributed Version Control System* / DVCS) menggunakan Git dan platform kolaborasi GitHub. Mempelajari operasi dasar (*clone, commit, push, pull*), strategi percabangan (*branching strategies* seperti Git Flow dan GitHub Flow), penyelesaian konflik (*merge conflict resolution*), *Pull Requests* (PR), tinjauan kode (*code review*), dan penandaan rilis (*releases & tags*).
- Akses Modul: [mcino-Introduction-to-Git-and-GitHub](./mcino-Introduction-to-Git-and-GitHub/)

### Course 06: Hands-on Introduction to Linux Commands and Shell Scripting [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Keterampilan praktis sistem operasi Linux sebagai fondasi utama infrastruktur DevOps. Mempelajari navigasi berkas, pengelolaan izin akses (*chmod, chown*), manajemen proses dan layanan (*systemd*), jaringan, penyaringan teks menggunakan *grep, sed, awk*, serta otomatisasi tugas operasional melalui penulisan skrip Bash (*Shell Scripting*).
- Akses Modul: [07 Hands-on Introduction to Linux Commands and Shell Scripting](./07%20Hands-on%20Introduction%20to%20Linux%20Commands%20and%20Shell%20Scripting/)

### Course 07: Python for Data Science, AI & Development [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Dasar-dasar pemrograman Python untuk otomatisasi dan pengembangan sistem. Mempelajari struktur data (list, dictionary, tuple, set), logika kontrol alur, pemrograman berorientasi objek, penanganan berkas dan pengecualian (*exception handling*), konsumsi REST API menggunakan pustaka *Requests*, dan manipulasi data dasar.

### Course 08: Developing AI Applications with Python and Flask [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Pembangunan aplikasi web dan antarmuka pemrograman aplikasi (API) ringan menggunakan kerangka kerja Python Flask. Mempelajari konsep perutean (*routing*), penanganan permintaan HTTP, templating antarmuka, pembuatan *endpoint* RESTful, pengemasan aplikasi, dan integrasi layanan kecerdasan buatan (*AI services*) berbasis cloud.
- Akses Modul: [08 Developing AI Applications with Python and Flask](./08%20Developing%20AI%20Applications%20with%20Python%20and%20Flask/)

### Course 09: Introduction to Containers w/ Docker, Kubernetes & OpenShift [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Teknologi kontainerisasi dan orkestrasi beban kerja modern. Mempelajari pembuatan citra kontainer (*Dockerfile*), manajemen siklus hidup kontainer menggunakan Docker CLI, arsitektur klaster Kubernetes (Pods, Deployments, Services, Ingress, ConfigMaps, Secrets), deklarasi YAML, serta penerapan klaster enterprise menggunakan Red Hat OpenShift.
- Akses Modul: [09 Introduction to Containers w Docker, Kubernetes & OpenShift](./09%20Introduction%20to%20Containers%20w%20Docker,%20Kubernetes%20&%20OpenShift/)

### Course 10: Application Development using Microservices and Serverless [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Perancangan arsitektur berorientasi layanan mikro (*Microservices Architecture*) dan komputasi tanpa server (*Serverless*). Mempelajari dekomposisi monolitik, komunikasi sinkron via REST dan gRPC, komunikasi asinkron berbasis pesan (*Event-Driven Architecture*), gerbang API (*API Gateway*), pola ketahanan (*circuit breaker*), dan fungsi *Serverless / FaaS* (seperti IBM Cloud Code Engine).
- Akses Modul: [10 Application Development using Microservices and Serverless](./10%20Application%20Development%20using%20Microservices%20and%20Serverless/)

### Course 11: Introduction to Test and Behavior Driven Development (TDD/BDD) [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Metodologi pengujian otomatis terdepan untuk menjamin kualitas kode perangkat lunak. Mempelajari siklus *Red-Green-Refactor* pada TDD, penulisan pengujian unit (*Unit Testing* dengan PyTest/Unittest), teknik peniruan (*mocking & stubbing*), pengujian berbasis perilaku (*Behavior-Driven Development* / BDD) menggunakan sintaks Gherkin dan kerangka kerja Behave.
- Akses Modul: [11 Introduction to Test and Behavior Driven Development](./11%20Introduction%20to%20Test%20and%20Behavior%20Driven%20Development/)

### Course 12: Continuous Integration and Continuous Delivery (CI/CD) [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Otomasi siklus rilis perangkat lunak dari integrasi kode hingga penggelaran produksi. Mempelajari perancangan *CI/CD pipeline* deklaratif menggunakan GitHub Actions, Jenkins, dan Tekton, otomatisasi pengujian, pemindaian kode statis, pembuatan artefak rilis, strategi deployment (*Blue-Green, Canary, Rolling updates*), dan implementasi prinsip *GitOps*.
- Akses Modul: [12 Continuous Integration and Continuous Delivery (CICD)](./12%20Continuous%20Integration%20and%20Continuous%20Delivery%20(CICD)/)

### Course 13: Application Security for Developers and DevOps Professionals [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Integrasi praktik keamanan sejak awal siklus pengembangan (*Shift-Left Security* / DevSecOps). Mempelajari 10 kerentanan keamanan web teratas menurut OWASP, analisis keamanan kode statis (SAST), pengujian keamanan dinamis (DAST), analisis komposisi perangkat lunak (*Software Composition Analysis* / SCA), manajemen rahasia dan kunci (*Secret Management* seperti HashiCorp Vault), serta penegakan kebijakan kepatuhan.
- Akses Modul: [13 Application Security for Developers and DevOps Professionals](./13%20Application%20Security%20for%20Developers%20and%20DevOps%20Professionals/)

### Course 14: Monitoring and Observability for Development and DevOps [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Pengawasan kesehatan sistem dan keandalan operasional (*Site Reliability Engineering* / SRE). Mempelajari tiga pilar observabilitas (*Metrics, Logs, Traces*), pengumpulan metrik menggunakan Prometheus, visualisasi dasbor performa menggunakan Grafana, agregasi log terpusat (ELK / EFK Stack), pelacakan terdistribusi (*Distributed Tracing* dengan OpenTelemetry dan Jaeger), serta manajemen peringatan dini (*Alerting*).
- Akses Modul: [14 Monitoring and Observability for Development and DevOps](./14%20Monitoring%20and%20Observability%20for%20Development%20and%20DevOps/)

### Course 15: DevOps Capstone Project [ON PROGRESS]
- Status: Dalam Antrean.
- Deskripsi: Proyek puncak komprehensif yang mengintegrasikan seluruh keahlian yang telah dipelajari sepanjang program spesialisasi. Pembelajar merancang, membangun, menguji, mengamankan, mengotomasi, dan menggelar aplikasi berbasis *microservices* ke klaster cloud menggunakan jalur *CI/CD* otomatis penuh yang dilengkapi pemantauan observabilitas *real-time*.
- Akses Modul: [15 DevOps Capstone Project](./15%20DevOps%20Capstone%20Project/)

