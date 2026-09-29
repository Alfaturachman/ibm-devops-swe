# Introduction to Software Engineering

Dokumen ini memuat dokumentasi komprehensif, catatan studi mendalam, sintesis metodologis, dan panduan praktis untuk kursus **Introduction to Software Engineering** (Course 04 dari *IBM DevOps and Software Engineering Professional Certificate* di Coursera). Kursus ini mengupas tuntas prinsip dasar rekayasa perangkat lunak, siklus hidup pengembangan sistem (*Software Development Life Cycle* / SDLC), metodologi pengembangan perangkat lunak (Waterfall, V-Model, Spiral, Iterative, Agile), tumpukan teknologi dan perkakas pengembangan, logika dan organisasi pemrograman, arsitektur perangkat lunak dan pola desain (*design patterns*), topologi penyebaran (*deployment topologies*), lanskap karier dan peran profesional rekayasawan perangkat lunak, serta penyusunan rencana aksi karier rekayasa perangkat lunak (*career plan roadmap*).

---

## 1. Course Curriculum Structure

Kurikulum kursus ini terbagi ke dalam enam modul pembelajaran terstruktur yang memandu peserta dari fondasi teoritis hingga perancangan peta jalan karier profesional:

1. **Module 1 - The Software Development Lifecycle**
2. **Module 2 - Introduction to Software Development**
3. **Module 3 - Basics of Programming**
4. **Module 4 - Software Architecture, Design, and Patterns**
5. **Module 5 - Job Opportunities and Skillsets in Software Engineering**
6. **Module 6 - Final Project**

---

## 2. Executive Summaries per Module

### A. Module 1: The Software Development Lifecycle
Modul ini membangun fondasi rekayasa perangkat lunak formal, membedah tahapan SDLC secara menyeluruh, serta menelaah spektrum model proses pengembangan perangkat lunak:
- **01 Overview of Software Engineering.md**: Definisi rekayasa perangkat lunak menurut standar IEEE dan Roger Pressman, pembedaan esensial antara perangkat lunak yang direkayasa (*engineered*) dengan produk fisik yang dimanufaktur (*software doesn't wear out*), enam fase siklus SDLC (Analisis Kebutuhan, Desain Sistem, Implementasi/Coding, Pengujian, Penerapan, dan Pemeliharaan), serta kepatuhan pada Kode Etik dan Praktik Profesional IEEE-CS/ACM.
- **02 Software Building Process and Associated Roles.md**: Analisis komparatif enam model proses rekayasa (Waterfall sekuensial, Prototyping evolusioner, Iterative & Incremental, Spiral berbasis analisis risiko Boehm, V-Model berpasangan verifikasi-validasi, serta Agile/Scrum adaptif), pembagian peran dan tanggung jawab spesifik dalam tim rekayasa (*Product Manager, Project Manager, Systems Analyst, Software Architect, Programmer/Developer, dan Tester/QA*), serta kriteria pemilihan model berdasarkan ketidakpastian kebutuhan dan skala proyek.

---

### B. Module 2: Introduction to Software Development
Modul ini mengulas anatomi aplikasi web modern, pemisahan lapisan logika komputasi, serta ekosistem perkakas bantu pengembang:
- **01 Introduction to Development.md**: Tiga pilar arsitektur web modern (lapisan antarmuka pengguna Front-End, lapisan pemrosesan bisnis dan persistensi data Back-End, serta integrasi Full-Stack), siklus interaksi permintaan dan tanggapan HTTP/HTTPS, prinsip antarmuka pemrograman aplikasi berbasis RESTful API, format pertukaran data terstruktur (JSON dan XML), serta transisi arsitektur monolitik menuju sistem layanan mikro (*microservices*).
- **02 Tools in Software Development.md**: Taksonomi perkakas rekayasa perangkat lunak, sistem kendali versi terdistribusi (*Git dan GitHub*), lingkungan pengembangan terintegrasi (*IDE vs Text Editors*), perkakas otomatisasi kompilasi dan manajemen paket (*build automation tools*), kerangka kerja pengujian kode otomatis (TDD dan BDD), integrasi pipa rilis CI/CD, serta platform pemantauan performa dan observabilitas operasional (Prometheus dan Grafana).

---

### C. Module 3: Basics of Programming
Modul ini membahas fondasi komputasional, klasifikasi bahasa pemrograman, organisasi berkas kode, serta prinsip logika dan algoritma:
- **01 Programming Languages and Organization.md**: Klasifikasi bahasa pemrograman berdasarkan tingkat abstraksi perangkat keras (bahasa tingkat rendah vs bahasa tingkat tinggi), paradigma pemrograman utama (imperatif/prosedural, berorientasi objek, fungsional, dan deklaratif), mekanisme eksekusi kode (kompilasi murni, interpretasi dinamis, dan pendekatan hibrida *Just-In-Time / JIT*), struktur pengorganisasian repositori kode modular, serta tata kelola dependensi pustaka pihak ketiga.
- **02 Programming Logic and Concepts.md**: Logika alur kontrol komputasi (struktur kondisional percabangan dan perulangan), struktur data fundamental (variabel primitif, array/list, antrean *queue*, tumpukan *stack*, tabel hash *hash map*), algoritma pencarian dan pengurutan efisien, pengukuran efisiensi asimtotik waktu dan ruang memori menggunakan notasi Big-O, serta teknik penanganan eksepsi (*exception handling*) dan perancangan fungsi modular.

---

### D. Module 4: Software Architecture, Design, and Patterns
Modul ini membedah perbedaan mendasar antara arsitektur sistem tingkat tinggi dengan desain detail berorientasi objek, serta mengevaluasi pola topologi penyebaran:
- **01 Software Architecture and Design.md**: Batasan pemisah antara arsitektur perangkat lunak (*the blueprint*) dengan desain detail (*the implementation structure*), penerapan lima prinsip desain berorientasi objek SOLID (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion) dan prinsip DRY (*Don't Repeat Yourself*), katalog pola desain Gang of Four (GoF) yang mencakup pola kreasi (*Creational*), struktural (*Structural*), dan perilaku (*Behavioral*), serta integrasi prinsip keamanan sistem sejak tahap desain (*Security by Design*).
- **02 Software Architecture Patterns and Deployment Topologies.md**: Evaluasi komparatif lima pola arsitektur enterprise (Monolith berlapis, Tiered/N-Tier arsitektur klien-peladen, Event-Driven asinkron berbasis pialang pesan, Microservices poliglota terdistribusi, dan Serverless FaaS berbasis kejadian), empat topologi penerapan komputasi awan (On-Premises, IaaS Virtual Machines, Kontainerisasi Kubernetes, dan Serverless Engine), serta strategi rilis produksi minim risiko (*Rolling Updates, Blue-Green Deployment, dan Canary Releases*).

---

### E. Module 5: Job Opportunities and Skillsets in Software Engineering
Modul ini memetakan lanskap karier rekayasa perangkat lunak, profil kompetensi yang disyaratkan, serta dinamika industri teknologi:
- **01 About Software Engineers.md**: Definisi peran, rutinitas harian, dan tanggung jawab rekayasawan perangkat lunak profesional, pemetaan kompetensi teknis inti (*hard skills*: bahasa pemrograman, basis data, Git, dan CI/CD), penguasaan keterampilan interpersonal (*soft skills*: komunikasi, empati, manajemen waktu, dan kolaborasi tim), kode etik profesi, serta dikotomi jalur karier teknis (*Individual Contributor track*) versus jalur kepemimpinan (*Management track*).
- **02 Careers in Software Engineering.md**: Diferensiasi spesialisasi peran rekayasa di industri teknologi (Front-End Engineer, Back-End Engineer, Full-Stack Developer, Cloud/DevOps Engineer, Site Reliability Engineer / SRE, Data Engineer, dan Cybersecurity Engineer), tren pertumbuhan pasar kerja global dan regional, analisis faktor penentu kompensasi/remunerasi, serta panduan praktis membangun portofolio repositori proyek terbuka dan personal branding di GitHub dan LinkedIn.

---

### F. Module 6: Final Project
Modul ini mengintegrasikan seluruh wawasan teoritis ke dalam perumusan dokumen rencana karier dan audit portofolio profesional:
- **Final Project - Develop Software Engineering Career Plan.md**: Studi kasus dan dokumentasi perencanaan karier komprehensif untuk posisi *Associate Cloud Software Engineer (DevOps & Infrastructure Automation)* di Red Hat/IBM. Dokumen memuat sasaran pengembangan profesional, kerangka kerja analisis lowongan industri nyata, metodologi audit kesenjangan portofolio (*gap analysis*), serta peta jalan rencana aksi konkret berbasis tiga pilar utama: Pendidikan dan Pengalaman, Penguasaan Keterampilan Teknis, dan Sertifikasi Profesional Industri.

---

## 3. Core Competencies and Skills Acquired

Setelah mempelajari seluruh modul dan menyusun rencana karier pada kursus ini, pembaca menguasai kompetensi esensial berikut:
- **Penguasaan Metodologi SDLC**: Mampu memilih, menyesuaikan, dan mengevaluasi model proses pengembangan perangkat lunak (Waterfall, Iterative, Spiral, V-Model, atau Agile) yang paling tepat untuk karakteristik proyek tertentu.
- **Arsitektur dan Rekayasa Web Modern**: Memahami alur kerja tumpukan teknologi modern, komunikasi antarmuka REST API, serta strategi dekomposisi monolitik menuju arsitektur layanan mikro.
- **Fondasi Komputasional dan Pemrograman**: Terampil dalam logika kontrol alur, pemilihan struktur data yang tepat, dan analisis efisiensi komputasi berbasis notasi Big-O.
- **Penerapan Prinsip Desain dan Pola Arsitektur**: Menguasai implementasi prinsip SOLID, pola desain GoF, serta pemilihan pola arsitektur enterprise dan topologi komputasi awan yang andal dan aman.
- **Perencanaan Karier Berbasis Bukti (*Evidence-Based Career Planning*)**: Mampu melakukan audit kesenjangan keterampilan mandiri secara objektif terhadap tuntutan industri nyata, serta merumuskan strategi penutupan kesenjangan melalui proyek nyata dan sertifikasi kredibel.
