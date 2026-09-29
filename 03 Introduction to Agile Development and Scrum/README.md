# Introduction to Agile Development and Scrum

Dokumen ini memuat dokumentasi komprehensif, catatan studi mendalam, sintesis metodologis, dan panduan praktis untuk kursus **Introduction to Agile Development and Scrum** (Course 03 dari *IBM DevOps and Software Engineering Professional Certificate* di Coursera). Kursus ini mengupas tuntas filosofi ketangkasan (*Agile philosophy*), kerangka kerja Scrum (*Scrum framework*), pembagian peran dan tanggung jawab tim, teknik perencanaan tangkas (*Agile planning*), perumusan cerita pengguna (*User Stories*) dan kriteria penerimaan Gherkin, estimasi bobot cerita (*story points*), eksekusi harian pada papan Kanban (*Daily Execution*), pemantauan diagram pembakaran (*Burndown Chart*), upacara penutupan sprint (*Sprint Review* dan *Sprint Retrospective*), pengukuran kinerja berbasis metrik DORA (*actionable metrics*), pencegahan anti-pola (*anti-patterns*), hingga pelaksanaan proyek akhir terintegrasi (*Final Project*).

---

## 1. Course Curriculum Structure

Kurikulum kursus ini terbagi ke dalam empat modul pembelajaran terstruktur yang memandu peserta dari pemahaman filosofis dasar hingga simulasi rekayasa proyek secara nyata:

1. **Module 1 - Introduction to Agile and Scrum**
2. **Module 2 - Agile Planning**
3. **Module 3 - Daily Execution**
4. **Module 4 - Final Project**

---

## 2. Executive Summaries per Module

### A. Module 1: Introduction to Agile and Scrum
Modul ini membangun fondasi pola pikir ketangkasan, membedah kegagalan model sekuensial tradisional (Waterfall), serta memperkenalkan arsitektur kerangka kerja Scrum dan pembentukan tim berkinerja tinggi:
- **01 Introduction to Agile Philosophy.md**: Analisis krisis perangkat lunak akibat model Waterfall yang lambat dan kaku, pengenalan Manifesto Agile (4 Nilai Inti dan 12 Prinsip Panduan), pergeseran dari proses prediktif ke proses adaptif berbasis siklus umpan balik cepat (*fast feedback loops*), serta penanaman budaya keamanan psikologis (*psychological safety*) dan keberanian bereksperimen (*fail fast, learn fast*).
- **02 Introduction to Scrum Methodology.md**: Prinsip dasar pengendalian proses empiris (*empirical process control*: transparansi, inspeksi, adaptasi), tiga pilar peran Scrum (*Product Owner* sebagai visioner produk, *Scrum Master* sebagai pelayan-pemimpin dan fasilitator, serta *Developers* sebagai pelaksana teknis lintas fungsi), tiga artefak resmi (*Product Backlog*, *Sprint Backlog*, dan *Potentially Shippable Increment*), serta empat upacara terikat waktu (*Sprint Planning*, *Daily Scrum*, *Sprint Review*, dan *Sprint Retrospective*).
- **03 Organizing for Success.md**: Karakteristik organisasi tim berkinerja tinggi yang mandiri (*self-organizing*) dan lintas disiplin (*cross-functional*), pembatasan ukuran tim kecil ($7 \pm 2$ orang) guna menekan jalur komunikasi eksponensial, keunggulan keterampilan berbentuk T (*T-shaped skills*) dibanding spesialis sempit (*I-shaped skills*), penghapusan sekat departemen (*silos*), serta pembangunan ruang kolaborasi fisik maupun virtual (*virtual team rooms*).
- **README.md (Modul 1)**: Silabus modul, ringkasan konsep inti, dan pemetaan materi Modul 1.

---

### B. Module 2: Agile Planning
Modul ini membahas tata kelola perencanaan bertahap, perumusan kebutuhan bisnis dari kacamata pengguna, serta teknik estimasi konsensus yang objektif:
- **01 Planning to be Agile.md**: Paradigma perencanaan adaptif dan berulang (*iterative planning*), konsep bawang perencanaan (*the planning onion*) dari level strategi hingga tugas harian, penerapan *Rolling Wave Planning*, pembatasan waktu (*timeboxing*) untuk menjaga fokus dan mencegah penundaan, serta manajemen ketidakpastian proyek.
- **02 User Stories.md**: Esensi cerita pengguna melalui konsep Tiga C (*Card, Conversation, Confirmation*), templat narasi Connextra (`As a... I need... So that...`), kriteria kualitas cerita berbasis prinsip INVEST (*Independent, Negotiable, Valuable, Estimable, Small, Testable*), standarisasi kriteria penerimaan (*Acceptance Criteria*) berbasis sintaks formal Gherkin (`Given... When... Then...`), serta dekomposisi hierarki kebutuhan dari *Themes*, *Epics*, *User Stories*, hingga *Technical Tasks*.
- **03 Planning Process.md**: Perbedaan mendasar antara estimasi ukuran relatif (*relative sizing*) dengan estimasi durasi jam kerja (*absolute hours*), standarisasi *Story Points* menggunakan deret modifikasi Fibonacci (1, 2, 3, 5, 8, 13, 20...), teknik konsensus tim *Planning Poker* dan pemilahan afinitas (*T-Shirt Sizing*), penyempurnaan simpanan produk secara berkala (*Backlog Refinement / Grooming*), serta pengukuran kapasitas (*capacity*) dan kecepatan historis tim (*velocity*).
- **README.md (Modul 2)**: Silabus modul, ringkasan konsep inti, dan pemetaan materi Modul 2.

---

### C. Module 3: Daily Execution
Modul ini mengulas manajemen alur kerja harian, upacara penutupan iterasi, tata kelola metrik kinerja, dan evaluasi kesehatan tim rekayasa:
- **01 Executing the Plan.md**: Manajemen aliran nilai menggunakan papan visual (*Kanban board*), pemetaan alur kolom (*Icebox*, *Product Backlog*, *Sprint Backlog*, *In Progress*, *Review/QA*, *Done*), penerapan sistem tarik (*pull system*) dan pembatasan pekerjaan dalam proses (*Work in Process / WIP Limits*), serta panduan disiplin pertemuan harian *Daily Stand-up* (durasi 15 menit, tiga pertanyaan fokus, penanganan *impediments*, dan larangan pemecahan masalah teknis berlarut-larut di dalam sesi).
- **02 Completing the Sprint.md**: Pemantauan sisa beban kerja menggunakan diagram pembakaran (*Burndown Chart*), anatomi sumbu waktu dan poin, interpretasi garis ideal (*ideal path*) serta penyesuaian akhir pekan (*flat line*), pelaksanaan Tinjauan Sprint (*Sprint Review*) berbasis demonstrasi perangkat lunak nyata (*working software*) bersama pemangku kepentingan, protokol penanganan cerita yang ditolak (*rejected stories*), serta Retrospeksi Sprint (*Sprint Retrospective*) sebagai sarana evaluasi proses kerja internal tim tanpa kehadiran *Product Owner* guna menjamin keamanan psikologis.
- **03 Measuring Success.md**: Filosofi pengukuran kinerja objektif, bahaya metrik semu (*vanity metrics*) dibanding keunggulan metrik yang dapat ditindaklanjuti (*actionable metrics*), empat metrik kinerja utama DORA (*Mean Lead Time*, *Release Frequency*, *Change Failure Rate*, dan *Mean Time to Recovery / MTTR*), tata laksana penutupan sprint pada Kanban (penutupan *milestone*, pengembalian *untouched stories* ke *Product Backlog*, dan pemecahan cerita / *story splitting* pada *unfinished stories* untuk menjaga akurasi *velocity*), serta identifikasi enam anti-pola Scrum dan daftar periksa kesehatan tim (*Scrum Health Check*).
- **README.md (Modul 3)**: Silabus modul, ringkasan konsep inti, dan pemetaan materi Modul 3.

---

### D. Module 4: Final Project
Modul ini menyajikan sintesis menyeluruh dalam bentuk proyek terapan berbasis skenario nyata:
- **Final Project - Agile Planning and Scrum Execution.md**: Skenario rekayasa katalog produk bagian belakang (*back-end product catalog*) untuk platform *e-commerce*, simulasi multi-peran (*Product Owner*, *Scrum Master*, *Developer*), pemetaan 10 kebutuhan pemangku kepentingan ke papan visual Kanban (*GitHub Projects* atau *ZenHub*), pembuatan templat isu `.github/ISSUE_TEMPLATE/user-story.md` berspesifikasi Gherkin, pelabelan utang teknis (`technical debt`) dan fitur (`enhancement`), konfigurasi *Sprint Milestone* 2 minggu, estimasi poin, orkestrasi alur kerja Kanban hingga kolom *Done*, evaluasi analitik *Burndown Chart*, dokumentasi artefak sprint, serta penerapan tata kelola Scrum profesional (*Definition of Ready* dan *Definition of Done*).
- **README.md (Modul 4)**: Silabus modul, ringkasan instruksi, dan panduan penyelesaian proyek akhir.

---

## 3. Core Competencies and Skills Acquired

Setelah mempelajari seluruh materi dan menyelesaikan proyek akhir dalam kursus ini, pembaca memperoleh seperangkat kompetensi profesional yang relevan dengan standar industri perangkat lunak modern:
- **Pola Pikir Ketangkasan (*Agile Mindset*)**: Mampu menginternalisasi 4 nilai inti dan 12 prinsip Agile dalam dinamika tim rekayasa perangkat lunak nyata.
- **Penguasaan Kerangka Kerja Scrum (*Scrum Mastery*)**: Memahami secara mendalam peran, tanggung jawab, artefak, dan batasan waktu upacara Scrum tanpa mencampuradukkan wewenang antar peran.
- **Rekayasa Kebutuhan Berpusat pada Pengguna (*User-Centric Requirements Engineering*)**: Terampil menyusun cerita pengguna yang memenuhi kriteria INVEST serta merumuskan kriteria penerimaan yang teruji menggunakan sintaks formal Gherkin (*Given-When-Then*).
- **Estimasi Konsensus dan Perencanaan Kapasitas**: Mampu memandu sesi *Planning Poker*, menetapkan *Story Points* secara relatif berbasis deret Fibonacci, dan memproyeksikan kapasitas sprint berdasarkan tren kecepatan (*velocity*).
- **Manajemen Alur Kerja Visual (*Visual Workflow Management*)**: Mahir mengoperasikan papan Kanban, menetapkan batas *Work in Process (WIP)* yang sehat, dan mengidentifikasi hambatan (*bottlenecks*) secara seketika.
- **Evaluasi dan Metrik Kinerja Modern**: Terbiasa memanfaatkan diagram *Burndown Chart* dan metrik DORA untuk mendorong perbaikan proses secara empiris, menghindari metrik semu (*vanity metrics*), serta menjaga kesehatan tim melalui *Scrum Health Check*.
- **Penerapan Alat Kolaborasi Nyata**: Berpengalaman mengonfigurasi dan mengelola alur kerja proyek langsung menggunakan ekosistem *GitHub Projects*, repositori kode, templat isu, serta ekstensi *ZenHub*.
