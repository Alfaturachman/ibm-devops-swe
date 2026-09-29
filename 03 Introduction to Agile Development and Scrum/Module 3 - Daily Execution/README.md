# Module 03: Daily Execution

Dokumen ini berisi silabus terstruktur, ringkasan konsep teoritis, dan panduan navigasi catatan pembelajaran untuk **Module 3: Daily Execution** pada kursus *Introduction to Agile Development and Scrum* (bagian dari *IBM DevOps and Software Engineering Professional Certificate* di Coursera).

---

## 1. Daftar Catatan Pembelajaran

Modul ini terdiri dari tiga catatan studi mendalam yang mengulas tata kelola alur kerja harian, upacara penutupan sprint, pemantauan diagram kemajuan, evaluasi metrik kinerja DORA, serta pencegahan anti-pola Scrum:

1. **01 Executing the Plan.md**:
   - Visualisasi aliran nilai (*value stream*) menggunakan papan Kanban digital.
   - Definisi dan fungsi kolom kerja standar: *Icebox* (ide masa depan), *Product Backlog* (keinginan produk terurut), *Sprint Backlog* (komitmen sprint), *In Progress* (sedang dikerjakan), *Review/QA* (verifikasi kualitas), dan *Done* (memenuhi *Definition of Done*).
   - Prinsip sistem tarik (*pull system*) dan penerapan batas pekerjaan dalam proses (*Work in Process / WIP Limits*) untuk menjaga fokus dan mencegah timbunan inventaris kerja.
   - Tata kelola pertemuan harian *Daily Stand-up*: batasan waktu ketat 15 menit, tiga pertanyaan fokus harian, identifikasi dini hambatan (*impediments*), dan larangan pembahasan teknis mendalam di dalam sesi.

2. **02 Completing the Sprint.md**:
   - Pelacakan beban kerja menggunakan diagram pembakaran (*Burndown Chart*): interpretasi sumbu hari kerja versus sisa poin, pembacaan garis ideal (*ideal path*), penyesuaian akhir pekan (*flat line*), serta analisis deviasi keterlambatan atau percepatan tim.
   - Penyelenggaraan Tinjauan Sprint (*Sprint Review*): demonstrasi perangkat lunak yang berfungsi nyata (*working software*) kepada pemangku kepentingan (*stakeholders*), penerimaan umpan balik langsung, dan tata cara penanganan cerita yang ditolak (*rejected stories*).
   - Upacara Retrospeksi Sprint (*Sprint Retrospective*): evaluasi proses kerja internal dan relasi tim, justifikasi tidak diundangnya *Product Owner* demi menjamin keselamatan psikologis tim pengembang, tiga pertanyaan reflektif pokok, serta komitmen perbaikan berkelanjutan (*actionable Kaizen*).

3. **03 Measuring Success.md**:
   - Filosofi pengukuran kinerja modern: "Anda tidak dapat memperbaiki apa yang tidak dapat Anda ukur".
   - Perbandingan antara metrik semu (*vanity metrics* seperti jumlah klik situs yang tidak memandu aksi) versus metrik yang dapat ditindaklanjuti (*actionable metrics* seperti hasil *A/B testing*).
   - Empat metrik kinerja utama DORA: *Mean Lead Time* (kecepatan ide ke produksi), *Release Frequency* (frekuensi perilisan aman), *Change Failure Rate* (persentase rilis bermasalah), dan *Mean Time to Recovery / MTTR* (kecepatan pemulihan insiden).
   - Tata laksana penutupan sprint pada Kanban: penutupan *Sprint Milestone* untuk mengunci data *velocity*, pengembalian cerita belum disentuh (*untouched stories*) ke *Product Backlog*, serta mekanisme pemecahan cerita (*story splitting*) pada cerita belum tuntas (*unfinished stories*) agar usaha pengembang tetap diakui secara proporsional.
   - Identifikasi enam anti-pola Scrum (ketiadaan PO tunggal, tim terlalu besar, tidak berdedikasi, terlalu tersebar geografis, tersekat departemen, dan tidak mandiri) serta panduan daftar periksa kesehatan tim (*Scrum Health Check Checklist*).

---

## 2. Hubungan Antar Materi dan Peta Konseptual

Rangkaian materi pada Modul 3 mengintegrasikan eksekusi harian dengan pembelajaran berkelanjutan:
- **Dari Alur Harian Menuju Evaluasi Siklus**: Pengoperasian papan Kanban dan pertemuan harian (*Executing the Plan*) menyediakan data riil mengenai bagaimana pekerjaan bergerak. Pada akhir iterasi, kemajuan tersebut dikonfirmasi melalui diagram Burndown, diulas bersama pemangku kepentingan dalam *Sprint Review*, dan dievaluasi proses kerjanya dalam *Sprint Retrospective* (*Completing the Sprint*).
- **Dari Refleksi Menuju Pengukuran Objektif**: Refleksi kualitatif pada retrospeksi diperkuat oleh metrik kuantitatif pada dokumen ketiga (*Measuring Success*). Melalui penutupan *milestone* yang tepat, pemecahan cerita yang adil, pemantauan metrik DORA, dan audit kesehatan berkala, tim rekayasa mampu bertransformasi menjadi tim berkinerja tinggi yang adaptif dan bebas dari anti-pola.
