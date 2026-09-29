# Agile Planning and Scrum Execution in Software Development

Dokumen ini memuat dokumentasi komprehensif implementasi metodologi tangkas (*Agile and Scrum*) dalam pengelolaan siklus hidup perangkat lunak. Pembahasan mencakup simulasi peran kolaboratif (*Product Owner*, *Scrum Master*, dan *Developer*), transformasi kebutuhan bisnis menjadi cerita pengguna (*user stories*), standarisasi kriteria penerimaan Gherkin, manajemen simpanan produk (*Product Backlog*), perencanaan sprint (*Sprint Planning*), orkestrasi papan visual (*Kanban board*), serta analisis performa tim melalui diagram *Burndown Chart*.

---

## 1. Project Overview and Stakeholder Requirements

Pada skenario proyek rekayasa ini, tim pengembang ditugaskan untuk membangun layanan katalog produk bagian belakang (*back-end product catalog*) untuk sebuah platform perdagangan elektronik (*e-commerce*).

### A. Peran Kolaborasi Scrum (Simulated Scrum Roles)
Praktik ini mengintegrasikan kolaborasi lintas peran kunci dalam ekosistem Scrum:
- **Product Owner**: Bertanggung jawab mendefinisikan kebutuhan pemangku kepentingan menjadi cerita pengguna (*user stories*), memprioritaskan urutan kerja pada *Product Backlog*, serta menyetujui kriteria penerimaan (*acceptance criteria*).
- **Scrum Master**: Memfasilitasi pembuatan tonggak pencapaian sprint (*Sprint Milestone*), memastikan cerita yang dipilih memenuhi kriteria kesiapan (*Definition of Ready*), dan mengawal disiplin alur kerja visual.
- **Developer**: Melakukan estimasi bobot cerita (*story point estimation*), menarik pekerjaan ke dalam *Sprint Backlog*, menetapkan tugas ke diri sendiri, serta menggeser kartu kerja melintasi kolom papan Kanban hingga mencapai status selesai (*Definition of Done*).

### B. Spesifikasi Kebutuhan Pemangku Kepentingan (Stakeholder Requirements)
Pemangku kepentingan telah merumuskan 10 kebutuhan fungsional dan teknis yang harus dikonversi menjadi isu cerita pengguna pada papan visual:
1. Kemampuan untuk membuat produk baru di dalam katalog (*create a product in the catalog*).
2. Kemampuan untuk mengambil atau melihat data produk dari katalog (*retrieve a product from the catalog*).
3. Kemampuan untuk memperbarui data produk di dalam katalog (*update a product in the catalog*).
4. Kemampuan untuk menghapus produk dari katalog (*delete a product from the catalog*).
5. Kemampuan untuk memberikan tanda suka pada suatu produk (*Like a product in the catalog*).
6. Kemampuan untuk memberikan tanda tidak suka pada suatu produk (*Dislike a product in the catalog*).
7. Kemampuan untuk menampilkan seluruh daftar produk di katalog (*list all products in the catalog*).
8. Kemampuan untuk mencari dan memfilter sebagian produk di katalog (*query a subset of products in the catalog*).
9. Kebutuhan infrastruktur agar sistem di-host di lingkungan komputasi awan (*hosted in the cloud*).
10. Kebutuhan otomatisasi pipa penyebaran kode baru ke lingkungan komputasi awan (*automated deployment to the cloud*).

---

## 2. Agile Workflow and Implementation Methodology

Pelaksanaan manajemen proyek tangkas dijalankan melalui sembilan tahapan metodologis berurutan:

### A. Inisialisasi Repositori dan Papan Visual Kanban
- Membangun repositori baru di GitHub dengan nama proyek standar: `agile-final-project`.
- Mengatur visibilitas repositori ke publik (*Public*) guna memastikan keterbukaan artefak dan memfasilitasi peninjauan kolaboratif.
- Mengonfigurasi papan proyek (*Project Board*) dengan nama **Final Project** menggunakan antarmuka GitHub Projects atau ZenHub.

### B. Standarisasi Templat Isu Cerita Pengguna (Issue Template)
Membangun standarisasi penulisan cerita pengguna di dalam repositori:
- Membuat struktur direktori dan berkas templat: `.github/ISSUE_TEMPLATE/user-story.md`.
- Templat wajib memuat dua komponen inti rekayasa kebutuhan:
  - Struktur narasi nilai bisnis Connextra: `As a... I need... So that...`
  - Kriteria penerimaan (*Acceptance Criteria*) berbasis BDD menggunakan sintaks formal Gherkin: `Given... When... Then...`

Format standar isi berkas `user-story.md`:
````markdown
---
name: User Story
about: Agile User Story Template
title: ''
labels: ''
assignees: ''
---

### Story Description
**As a** [role/user]  
**I need** [function/capability]  
**So that** [business benefit/value]  

### Acceptance Criteria
```gherkin
Given [initial context or precondition]
When [an event or action occurs]
Then [an expected outcome or observable result]
```
````

### C. Pendaftaran Kebutuhan dan Pemilahan Awal Backlog (Backlog Triage)
- Mendaftarkan 10 kebutuhan pemangku kepentingan sebagai isu (*issues*) baru di GitHub menggunakan templat cerita pengguna.
- Memilah isu nomor 7 (*list all products*) dan isu nomor 8 (*query a subset of products*) ke kolom **Icebox** (area penampungan ide fitur masa depan yang belum diprioritaskan).
- Memindahkan delapan isu sisanya (isu nomor 1 hingga 6, serta isu nomor 9 dan 10) ke kolom **Product Backlog**.

### D. Penghalusan Backlog dan Kriteria Penerimaan Gherkin (Backlog Refinement)
- Menyusun urutan kartu pada kolom *Product Backlog* berdasarkan prioritas nilai bisnis (isu 1 berada paling atas, diikuti isu 2, dan seterusnya).
- Memperinci lima cerita teratas (*top 5 stories*) dengan menambahkan kriteria penerimaan terukur menggunakan sintaks Gherkin (*Given-When-Then*).

Contoh spesifikasi kriteria penerimaan Gherkin pada cerita pembuatan produk (Kebutuhan 1):
```gherkin
Scenario: Successfully creating a new product
  Given the administrator is logged into the catalog management system
  When the administrator enters valid product details and clicks "Submit"
  Then the new product should be saved in the database
  And a confirmation message "Product created successfully" should be displayed
```

### E. Taksonomi Pelabelan Komponen dan Utang Teknis (Labeling and Technical Debt)
- Membuat label kustom bernama `technical debt` dengan warna visual yang kontras.
- Menyematkan label `technical debt` khusus untuk isu nomor 9 (*hosted in the cloud*) dan isu nomor 10 (*automated deployment to the cloud*) guna menandai kebutuhan fondasi infrastruktur dan otomatisasi pipa rilis.
- Menyematkan label `enhancement` pada seluruh cerita fungsional bisnis lainnya di dalam *Product Backlog*.

### F. Konfigurasi Tonggak Pencapaian Iterasi (Sprint Milestone)
- Membuat tonggak pencapaian iterasi (*Milestone*) baru bernama **Sprint**.
- Menetapkan batasan waktu (*timebox*) pelaksanaan sprint selama 2 minggu sesuai durasi standar siklus Scrum industri.

### G. Perencanaan Sprint dan Estimasi Kapasitas Tim (Sprint Planning and Estimation)
- Memilih empat cerita teratas dari kolom *Product Backlog* yang telah siap dikerjakan (*Definition of Ready*).
- Menghubungkan keempat cerita tersebut ke tonggak pencapaian **Sprint**.
- Menetapkan nilai estimasi poin cerita (*Story Point Estimates*) berdasarkan tingkat kesulitan dan ketidakpastian teknis (misalnya 1, 2, 3, atau 5 poin).
- Memindahkan keempat cerita yang telah disepakati dari *Product Backlog* ke kolom **Sprint Backlog**.

### H. Orkestrasi Alur Kerja dan Eksekusi Sprint (Sprint Simulation)
Mensimulasikan alur kerja harian tim rekayasa melintasi papan visual Kanban:
- **Pekerjaan Pertama**: Mengambil cerita teratas dari *Sprint Backlog*, menetapkan penugasan (*assignee*) ke diri sendiri, lalu menggeser ke kolom **In Progress**. Setelah implementasi selesai, geser ke kolom **Review/QA**.
- **Pekerjaan Kedua**: Mengambil cerita berikutnya dari *Sprint Backlog*, menetapkan ke diri sendiri, lalu menggeser ke **In Progress**.
- **Transisi Pertama**: Menggeser cerita pertama dari kolom **Review/QA** ke kolom **Done**. Menggeser cerita kedua dari **In Progress** ke **Review/QA**. Mengambil cerita ketiga dari *Sprint Backlog*, menetapkan ke diri sendiri, lalu menggeser ke **In Progress**.
- **Penutupan Sprint**: Menggeser cerita kedua dari **Review/QA** ke kolom **Done**. Membiarkan cerita ketiga tetap berada pada kolom **In Progress** (sebagai representasi realistis dari pekerjaan yang sedang aktif dikerjakan saat batas waktu sprint berakhir).
- Pada akhir iterasi, status kerja terdiri dari dua cerita berstatus *Done*, satu cerita berstatus *In Progress*, dan satu cerita tersisa di *Sprint Backlog*.

### I. Evaluasi Kemajuan Melalui Diagram Burndown (Burndown Chart Analysis)
- Membuka laporan diagram *Burndown Chart* pada antarmuka proyek.
- Mengamati penurunan garis sisa usaha seiring penyelesaian kartu kerja yang berpindah ke status *Done*.
- Mengevaluasi apakah deviasi garis aktual terhadap garis ideal disebabkan oleh estimasi awal yang kurang akurat atau hambatan eksternal (*impediments*).

---

## 3. Sprint Artifacts and Execution Documentation

Bagian ini menyajikan dokumentasi artefak rekayasa yang dihasilkan sepanjang siklus eksekusi Scrum:

### A. Arsitektur Kolom dan Alur Kerja Papan Visual (Kanban Board Architecture)
Papan visual proyek dikonfigurasi dengan alur multi-kolom yang mencerminkan status siklus hidup pengembangan:
- **Icebox**: Menampung kebutuhan fitur tambahan di masa mendatang yang belum dijadwalkan untuk implementasi segera (Kebutuhan 7 dan Kebutuhan 8).
- **Product Backlog**: Daftar simpanan produk utama yang telah diprioritaskan oleh *Product Owner* dan siap dihaluskan dalam sesi *refinement*.
- **Sprint Backlog**: Kumpulan cerita pengguna yang telah disepakati untuk dikerjakan dalam iterasi dua minggu aktif.
- **In Progress**: Kartu kerja yang sedang aktif dikerjakan oleh pengembang, dibatasi oleh batas pekerjaan aktif (*WIP limits*) untuk mencegah *multitasking* berlebihan.
- **Review/QA**: Tahap peninjauan kode (*peer review*), pengujian mutu, dan verifikasi kriteria penerimaan sebelum penggabungan ke basis kode utama.
- **Done**: Artefak kerja yang telah lolos seluruh kriteria *Definition of Done* dan siap dideploy ke lingkungan produksi.

### B. Dokumentasi Cerita Pengguna dan Kriteria Penerimaan Gherkin (User Stories Specification)
Seluruh kebutuhan pemangku kepentingan diklasifikasikan ke dalam taksonomi kerja:
- **Fitur Fungsional Katalog (`enhancement`)**:
  - *Story 1*: Pembuatan produk baru di katalog (*Create Product*).
  - *Story 2*: Pengambilan data detail produk (*Retrieve Product*).
  - *Story 3*: Pembaruan informasi produk (*Update Product*).
  - *Story 4*: Penghapusan produk dari katalog (*Delete Product*).
  - *Story 5*: Penambahan tanda suka pada produk (*Like Product*).
  - *Story 6*: Penambahan tanda tidak suka pada produk (*Dislike Product*).
- **Fondasi Infrastruktur dan Otomasi (`technical debt`)**:
  - *Story 9*: Hosting sistem di lingkungan komputasi awan (*Cloud Hosting*).
  - *Story 10*: Otomatisasi pipa pengiriman dan penyebaran berkelanjutan (*CI/CD Deployment*).
- **Spesifikasi Kriteria Penerimaan Gherkin**:
  - Setiap cerita pengguna dilengkapi dengan skenario konkret mencakup *Given* (kondisi awal), *When* (tindakan pengguna/sistem), dan *Then* (hasil yang diharapkan) untuk menjamin objektivitas pengujian.

### C. Metrik Kinerja dan Analisis Diagram Burndown (Burndown Analytics)
- **Alokasi Poin Cerita (*Story Points Allocation*)**:
  - Penetapan poin komparatif memungkinkan tim mengukur beban kerja secara relatif tanpa terikat estimasi jam mutlak.
- **Dinamika Garis Kemajuan (*Ideal vs Actual Burndown*)**:
  - Garis tren ideal (*Ideal Trend*) menurun secara linear dari total poin estimasi menuju nol pada hari terakhir sprint.
  - Garis sisa kerja aktual (*Actual Effort Remaining*) memperlihatkan grafik bertangga (*stair-step pattern*) yang turun setiap kali cerita menyelesaikan tahapan QA dan berpindah ke kolom *Done*.
- **Kecepatan Tim (*Sprint Velocity*)**:
  - Akumulasi poin dari cerita yang berstatus *Done* dijadikan tolok ukur kecepatan historis (*velocity*) untuk memprediksi kapasitas tim pada sesi *Sprint Planning* berikutnya.

---

## 4. Scrum Governance and Professional Quality Standards

Penerapan tata kelola Scrum profesional menjamin kualitas kode, kejelasan komunikasi, dan integritas rekayasa perangkat lunak:

### A. Standar Kualitas Kesiapan dan Penyelesaian (Definition of Ready and Definition of Done)
- **Definition of Ready (DoR)**:
  - Cerita pengguna telah ditulis dengan format Connextra (`As a... I need... So that...`) yang mendefinisikan persona dan nilai bisnis secara gamblang.
  - Kriteria penerimaan telah dispesifikasikan dengan format Gherkin yang dapat diuji.
  - Estimasi bobot poin cerita telah disepakati oleh tim pengembang.
  - Ketergantungan teknis (*dependencies*) antartugas telah teridentifikasi dan diselesaikan.
- **Definition of Done (DoD)**:
  - Kode sumber telah selesai ditulis dan mematuhi konvensi penulisan kode (*coding style guides*).
  - Seluruh pengujian unit dan pengujian integrasi otomatis berjalan sukses tanpa galat (*zero test failures*).
  - Melewati proses peninjauan kode (*peer code review*) dan disetujui oleh anggota tim pengembang lain.
  - Kode telah digabungkan (*merged*) ke cabang utama dan berhasil dideploy ke lingkungan pengujian tanpa menimbulkan utang teknis baru.

### B. Manajemen Utang Teknis dalam Lingkungan Tangkas (Technical Debt Management)
- **Prioritas Berimbang**: Memperlakukan tugas utang teknis (seperti otomatisasi CI/CD dan stabilitas lingkungan cloud) dengan urgensi yang setara dengan fitur fungsional bisnis.
- **Pencegahan Erosi Arsitektur**: Mengalokasikan kapasitas sprint secara konsisten untuk pemeliharaan fondasi sistem guna mencegah akumulasi masalah struktural yang dapat memperlambat kecepatan rilis jangka panjang.

### C. Disiplin Transparansi dan Retrospeksi Berkelanjutan (Engineering Transparency and Retrospective)
- **Transparansi Visual**: Menjaga papan visual Kanban selalu mutakhir secara waktu nyata sehingga seluruh pemangku kepentingan memiliki visibilitas penuh terhadap status pekerjaan.
- **Budaya Retrospektif (*Continuous Improvement*)**: Menjadikan sesi evaluasi retrospektif sebagai ruang pembelajaran tim untuk mengevaluasi apa yang berjalan baik, apa yang perlu ditingkatkan, serta merumuskan rencana perbaikan proses (*action items*) pada sprint berikutnya.
