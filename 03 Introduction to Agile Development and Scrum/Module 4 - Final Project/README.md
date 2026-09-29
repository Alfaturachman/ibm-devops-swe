# Module 04: Final Project

Dokumen ini berisi silabus terstruktur, ringkasan instruksi skenario terapan, dan panduan navigasi catatan pembelajaran untuk **Module 4: Final Project** pada kursus *Introduction to Agile Development and Scrum* (bagian dari *IBM DevOps and Software Engineering Professional Certificate* di Coursera).

---

## 1. Daftar Catatan Pembelajaran

Modul ini berfokus pada eksekusi proyek akhir terintegrasi yang merangkum seluruh keterampilan metodologis dan teknis yang telah dipelajari sebelumnya:

1. **Final Project - Agile Planning and Scrum Execution.md**:
   - Skenario proyek rekayasa: pengembangan sistem katalog produk bagian belakang (*back-end product catalog*) untuk situs web *e-commerce*.
   - Simulasi multi-peran Scrum: menjalankan peran *Product Owner* (membuat dan memprioritaskan cerita), *Scrum Master* (memfasilitasi *Sprint Milestone* dan kesiapan cerita), serta *Developer* (mengestimasi bobot poin dan menggeser status kartu kerja).
   - Analisis 10 kebutuhan pemangku kepentingan: fungsionalitas CRUD produk, penandaan suka/tidak suka, kueri data, hosting *cloud*, serta otomatisasi penyebaran.
   - Sembilan tahap metodologi pengerjaan terstruktur:
     - Inisialisasi repositori publik `agile-final-project` dan papan proyek `Final Project` (GitHub Projects / ZenHub).
     - Pembuatan templat cerita pengguna `.github/ISSUE_TEMPLATE/user-story.md` berspesifikasi Gherkin (`Given-When-Then`).
     - Pembuatan 10 isu dan pemilahan awal (isu 7 & 8 ke *Icebox*, sisanya ke *Product Backlog*).
     - Penghalusan *Product Backlog* dan penulisan kriteria penerimaan Gherkin pada 5 cerita teratas.
     - Pelabelan taksonomi: label `technical debt` (khusus isu 9 & 10) dan `enhancement` (cerita fungsional).
     - Pembuatan tonggak pencapaian *Sprint Milestone* berdurasi 2 minggu.
     - Sesi perencanaan sprint: alokasi 4 cerita teratas, estimasi poin, dan pemindahan ke *Sprint Backlog*.
     - Simulasi eksekusi sprint: perpindahan status kartu kerja melintasi kolom *In Progress*, *Review/QA*, hingga kolom *Done*, dengan menyisakan satu pekerjaan aktif di kolom *In Progress* saat sprint berakhir.
     - Pemantauan dan pembacaan diagram pembakaran (*Burndown Chart*).
   - Dokumentasi artefak sprint yang mencakup arsitektur multi-kolom papan Kanban, rincian cerita pengguna berbasis Connextra dan Gherkin, serta analisis metrik kecepatan tim (*velocity*).
   - Standar tata kelola Scrum profesional yang mencakup *Definition of Ready (DoR)*, *Definition of Done (DoD)*, manajemen utang teknis (*technical debt*), dan disiplin transparansi rekayasa.

---

## 2. Hubungan Antar Materi dan Integrasi Praktis

Modul 4 berfungsi sebagai batu uji praktis (*capstone lab*) dari seluruh kurikulum kursus:
- **Penerapan Terintegrasi**: Seluruh konsep teoritis yang dipelajari pada Modul 1 (peran Scrum), Modul 2 (templat cerita Connextra, kriteria Gherkin, dan estimasi poin), serta Modul 3 (papan Kanban, alur *In Progress* hingga *Done*, penutupan sprint, dan *Burndown Chart*) diimplementasikan secara langsung di dalam repositori nyata pada platform GitHub.
- **Kesiapan Profesional**: Melalui simulasi mandiri ini, praktikan tidak hanya menguasai teori ketangkasan, tetapi juga memiliki portofolio artefak rekayasa nyata yang siap ditunjukkan kepada calon pemberi kerja atau tim rekayasa industri.
