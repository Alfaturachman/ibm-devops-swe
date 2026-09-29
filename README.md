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
  - [Module 06: Final Project](./01%20Introduction%20to%20DevOps/Module%2006%20-%20Final%20Project/):
    - Analisis studi kasus nyata pada transformasi enterprise berskala global: *Thinking DevOps* (peruntuhan antrean tiket dan adopsi IT swalayan), *Organizing for DevOps* (penyelarasan domain bisnis dan CI harian), serta *Social Coding* (budaya *Inner Source* dan insentif kolaboratif).
    - Sintesis cetak biru arsitektur enterprise: Desain layanan mikro *cloud-native* nir-status, pola ketahanan sistem (*Bulkhead* dan *Circuit Breaker*), otomatisasi rilis CI/CD dan IaC, evaluasi pasca-insiden tanpa menyalahkan (*blameless post-mortem*), serta tata kelola metrik DORA.

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
    - Menyelesaikan proyek akhir penerapan mandiri: pengemasan aplikasi web interaktif "Guess the Capital" ke dalam citra kontainer Docker berbasis Nginx, publikasi citra ke IBM Container Registry (ICR), dan deployment ke platform nirserver IBM Cloud Code Engine dengan akses HTTPS publik.
    - Menyusun rancangan solusi arsitektur enterprise DineEase 2.0: memodernisasi platform pengiriman makanan monolitik ke microservices cloud-native pada ekosistem IBM Cloud melalui sembilan pemetaan layanan (MZR, Bare Metal GPU, IKS/OpenShift, API Connect, Cloudant NoSQL, Db2 on Cloud, Cloud CDN, Load Balancer, dan IBM Cloud Monitoring).

### Course 03: Introduction to Agile Development and Scrum [COMPLETED]
- Deskripsi: Prinsip-prinsip filosofi ketangkasan (*Agile Manifesto*) dan implementasi praktis kerangka kerja *Scrum*. Mempelajari pembagian tiga peran Scrum (*Product Owner, Scrum Master, Developers*), perumusan cerita pengguna (*User Stories*) berbasis kriteria INVEST dan format Gherkin, teknik estimasi konsensus (*Story Points* dan *Planning Poker*), orkestrasi alur kerja harian pada papan Kanban visual, analisis diagram *Burndown Chart*, upacara penutupan sprint (*Sprint Review* dan *Sprint Retrospective*), metrik DORA, hingga eksekusi proyek akhir rekayasa tangkas.
- [Course 03: Introduction to Agile Development and Scrum](./03%20Introduction%20to%20Agile%20Development%20and%20Scrum/README.md) menyajikan panduan implementasi komprehensif mengenai tata kelola pengembangan tangkas. Materi terbagi menjadi empat modul pembelajaran terstruktur:
  - [Module 1: Introduction to Agile and Scrum](./03%20Introduction%20to%20Agile%20Development%20and%20Scrum/Module%201%20-%20Introduction%20to%20Agile%20and%20Scrum/):
    - Memahami krisis perangkat lunak akibat model Waterfall dan pergeseran menuju Manifesto Agile (4 Nilai Inti dan 12 Prinsip Panduan).
    - Mempelajari pilar pengendalian proses empiris Scrum (transparansi, inspeksi, adaptasi), tiga peran utama, tiga artefak resmi, dan empat upacara terikat waktu (*timeboxed events*).
    - Membangun tim berkinerja tinggi yang mandiri (*self-organizing*), lintas fungsi (*cross-functional*), dengan keterampilan berbentuk T (*T-shaped skills*).
  - [Module 2: Agile Planning](./03%20Introduction%20to%20Agile%20Development%20and%20Scrum/Module%202%20-%20Agile%20Planning/):
    - Menerapkan paradigma perencanaan adaptif (*the planning onion*) dan *Rolling Wave Planning*.
    - Menyusun cerita pengguna menggunakan konsep Tiga C (*Card, Conversation, Confirmation*), templat Connextra (`As a... I need... So that...`), kriteria INVEST, dan kriteria penerimaan formal Gherkin (`Given... When... Then...`).
    - Menguasai estimasi ukuran relatif berbasis konsensus (*Story Points* deret Fibonacci) melalui *Planning Poker* dan sesi *Backlog Refinement*.
  - [Module 3: Daily Execution](./03%20Introduction%20to%20Agile%20Development%20and%20Scrum/Module%203%20-%20Daily%20Execution/):
    - Mengelola alur kerja visual menggunakan papan Kanban dengan batas *Work in Process* (WIP Limits) untuk mencegah kemacetan kerja.
    - Menjalankan pertemuan harian *Daily Stand-up* (15 menit) yang berfokus pada kemajuan dan eliminasi hambatan (*impediments*).
    - Memantau tren sisa usaha pada diagram *Burndown Chart*, memfasilitasi *Sprint Review* berbasis demonstrasi perangkat lunak nyata, menjalankan *Sprint Retrospective* tanpa *Product Owner* untuk keamanan psikologis, serta mengukur keberhasilan menggunakan metrik DORA.
  - [Module 4: Final Project](./03%20Introduction%20to%20Agile%20Development%20and%20Scrum/Module%204%20-%20Final%20Project/):
    - Melaksanakan simulasi proyek rekayasa tangkas penuh untuk pengembangan katalog produk *e-commerce*.
    - Mengonversi 10 kebutuhan bisnis ke templat cerita pengguna Gherkin di repositori publik GitHub, mengelola alur papan Kanban melintasi status *In Progress* hingga *Done*, menganalisis kemajuan *Burndown Chart*, serta menerapkan tata kelola mutu *Definition of Ready (DoR)* dan *Definition of Done (DoD)*.

### Course 04: Introduction to Software Engineering [COMPLETED]
- Deskripsi: Dasar-dasar rekayasa perangkat lunak modern dan siklus hidup pengembangan sistem (*Software Development Life Cycle* / SDLC). Mempelajari spektrum model proses pengembangan (Waterfall, Prototyping, Iterative, Spiral, V-Model, Agile), arsitektur web modern (Front-End, Back-End, Full-Stack, REST API), ekosistem perkakas bantu pengembang, logika komputasi dan struktur data fundamental, prinsip desain SOLID dan pola desain Gang of Four (GoF), pola arsitektur enterprise dan topologi komputasi awan, diferensiasi peran karier rekayasa, serta perancangan peta jalan karier profesional.
- [Course 04: Introduction to Software Engineering](./04%20Introduction%20to%20Software%20Engineering/README.md) memberikan wawasan fundamental dan aplikatif mengenai disiplin rekayasa perangkat lunak modern. Materi terbagi menjadi enam modul pembelajaran mendalam:
  - [Module 1: The Software Development Lifecycle](./04%20Introduction%20to%20Software%20Engineering/Module%201%20-%20The%20Software%20Development%20Lifecycle/):
    - Memahami definisi rekayasa perangkat lunak (IEEE dan Pressman), karakteristik perangkat lunak yang direkayasa vs dimanufaktur, enam fase SDLC, serta kepatuhan kode etik IEEE-CS/ACM.
    - Analisis komparatif enam model proses rekayasa (Waterfall, Prototyping, Iterative, Spiral, V-Model, Agile) dan pembagian peran kunci (*Product Manager, Project Manager, Systems Analyst, Software Architect, Programmer, Tester/QA*).
  - [Module 2: Introduction to Software Development](./04%20Introduction%20to%20Software%20Engineering/Module%202%20-%20Introduction%20to%20Software%20Development/):
    - Menguasai tiga pilar arsitektur web modern (Front-End, Back-End, Full-Stack), siklus permintaan-tanggapan HTTP/HTTPS, arsitektur RESTful API, pertukaran data JSON/XML, dan dekomposisi monolitik ke microservices.
    - Membedah taksonomi perkakas pengembang: sistem kendali versi (Git/GitHub), IDE modern, otomatisasi build, kerangka kerja pengujian (TDD/BDD), dan platform observabilitas (Prometheus/Grafana).
  - [Module 3: Basics of Programming](./04%20Introduction%20to%20Software%20Engineering/Module%203%20-%20Basics%20of%20Programming/):
    - Mempelajari klasifikasi bahasa pemrograman berdasarkan abstraksi dan paradigma (imperatif, OOP, fungsional, deklaratif), mekanisme eksekusi (kompilasi, interpretasi, JIT), dan struktur modular basis kode.
    - Menguasai logika kontrol alur, struktur data fundamental (array, linked list, stack, queue, hash table), algoritma pencarian dan pengurutan, notasi kompleksitas Big-O, serta penanganan eksepsi.
  - [Module 4: Software Architecture, Design, and Patterns](./04%20Introduction%20to%20Software%20Engineering/Module%204%20-%20Software%20Architecture%2C%20Design%2C%20and%20Patterns/):
    - Membedah pemisahan arsitektur sistem (*the blueprint*) vs desain detail, penerapan prinsip SOLID dan DRY, serta katalog pola desain Gang of Four (Creational, Structural, Behavioral).
    - Menganalisis lima pola arsitektur enterprise (Monolith, N-Tier, Event-Driven, Microservices, Serverless), empat topologi cloud (On-Premises, IaaS VM, Kubernetes, Serverless FaaS), dan strategi rilis minim downtime (*Rolling, Blue-Green, Canary*).
  - [Module 5: Job Opportunities and Skillsets in Software Engineering](./04%20Introduction%20to%20Software%20Engineering/Module%205%20-%20Job%20Opportunities%20and%20Skillsets%20in%20Software%20Engineering/):
    - Menelaah profil harian rekayasawan perangkat lunak, pemetaan keterampilan teknis (*hard skills*) dan interpersonal (*soft skills*), etika profesi, serta jalur karier kontributor individual (*IC track*) vs kepemimpinan (*Management track*).
    - Memetakan diferensiasi peran rekayasa teknologi (Frontend, Backend, Full-Stack, Cloud/DevOps, SRE, Data, Security), tren pasar tenaga kerja, evaluasi remunerasi, serta strategi membangun portofolio proyek terbuka di GitHub dan LinkedIn.
  - [Module 6: Final Project](./04%20Introduction%20to%20Software%20Engineering/Module%206%20-%20Final%20Project/):
    - Menyusun dokumentasi studi kasus perencanaan karier komprehensif untuk posisi *Associate Cloud Software Engineer (DevOps & Infrastructure Automation)* di Red Hat/IBM.
    - Menjalankan analisis kualifikasi lowongan industri nyata, evaluasi kesiapan diri, audit kesenjangan portofolio (*gap analysis*), serta perumusan peta jalan rencana aksi konkret berbasis tiga pilar: Pendidikan dan Pengalaman, Keterampilan Teknis, dan Sertifikasi Profesional.

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
