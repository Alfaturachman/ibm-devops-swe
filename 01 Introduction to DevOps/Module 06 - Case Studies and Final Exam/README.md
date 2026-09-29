# Module 06: Case Studies and Final Exam

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 06: Case Studies and Final Exam pada kursus Introduction to DevOps, mencakup analisis skenario studi kasus riil (Thinking DevOps, Organizing for DevOps, dan Social Coding) serta sintesis materi evaluasi akhir (*Final Exam*) dari seluruh rangkaian pembelajaran kursus.

---

### Ringkasan Konsep Inti dan Skenario Kasus

- **Skenario 1: Thinking DevOps (Transformasi Alur Kerja dan Infrastruktur Mandiri):**
  - Menganalisis kendala pengembang yang terhambat oleh antrean tiket manual operasional dalam penyediaan mesin virtual.
  - Menegaskan pentingnya menempatkan personel ke dalam tim lintas fungsi (*cross-functional Dev and Ops team*) serta beralih ke model TI layanan mandiri (*self-service IT*) melalui otomatisasi pipa rilis CI/CD.
  - Membuktikan bahwa meminta perlakuan khusus pada antrean tiket atau membentuk tim perantara baru tidak menyelesaikan masalah mendasar silo organisasi.
- **Skenario 2: Organizing for DevOps (Domain Bisnis dan Integrasi Berkelanjutan):**
  - Menghadapi masalah pemborosan waktu akibat koordinasi rumit antartim teknologi horizontal saat terjadi perubahan skema basis data dan konflik penggabungan kode di akhir bulan.
  - Solusi strategis: mereorganisasi tim mengelilingi domain bisnis (*business domains*) agar mandiri, menerapkan otomatisasi penerapan (*automated deployment*) dengan migrasi basis data terintegrasi, serta mewajibkan *Continuous Integration* (CI) dengan penggabungan kode harian untuk mendeteksi konflik sedini mungkin.
- **Skenario 3: Social Coding (Inner Source dan Insentif Kolaboratif):**
  - Mengkaji dinamika kontribusi lintas tim internal antara tim produk dan tim akun.
  - Menggarisbawahi kontribusi nyata *social coding* melalui keterbukaan repositori kode (*public/inner source repos*), pengajuan *pull request*, serta kesediaan berbagi keahlian teknis.
  - Menekankan keharusan perusahaan untuk memberikan penghargaan (*reward*) bagi tim yang membuka kodenya untuk dipakai ulang oleh tim lain alih-alih menghargai isolasi kode privat.

---

### Sintesis Evaluasi Ujian Akhir (Final Exam)

- **Fondasi Filosofis dan Budaya:**
  - Teknologi adalah pemungkin inovasi (*enabler of innovation*), sedangkan model bisnis inovatif adalah pembeda keberhasilan utama.
  - Dari tiga dimensi DevOps (Budaya, Metode, dan Alat), budaya kerja kolaboratif (*Culture*) merupakan faktor terpenting yang menentukan kesuksesan jangka panjang.
  - Extreme Programming (XP) meletakkan fondasi siklus umpan balik rapat (*tight feedback loops*) yang kemudian diperluas oleh DevOps.
- **Karakteristik Arsitektur dan Otomatisasi Rekayasa:**
  - Layanan mikro berbasis *cloud-native* bersifat nir-status (*stateless*), memiliki basis data terpisah (*database per service*), dan dapat diskalakan secara horizontal (*horizontal scaling*).
  - Pola ketahanan *bulkhead* mengisolasi kegagalan layanan agar tidak merembet menjadi kegagalan sistemik.
  - *Infrastructure as Code* (IaC) mendefinisikan infrastruktur ke dalam format teks yang dapat dieksekusi mesin (*executable textual format*).
  - *Continuous Integration* (CI) berfokus pada pembangunan dan pengujian otomatis harian ke cabang utama; sedangkan *Continuous Delivery* (CD) memastikan kode selalu berada dalam kondisi siap rilis ke lingkungan produksi kapan saja.
- **Tata Kelola Tim dan Pengukuran:**
  - Struktur tim wajib diselaraskan dengan domain bisnis, misi jangka panjang, dan arsitektur target sistem (*Inverse Conway Maneuver*).
  - Menghindari pemisahan tindakan dari konsekuensi yang memicu sikap apatis (*apathy*).
  - Mengukur keberhasilan melalui metrik yang dapat ditindaklanjuti (*actionable metrics* seperti Empat Metrik Kunci DORA) dan menolak penggunaan metrik semu (*vanity metrics*).
  - Mengapresiasi riset ilmiah Dr. Nicole Forsgren dalam merumuskan kerangka kerja pengukuran budaya tim yang sehat dan tanpa menyalahkan (*blameless culture*).
