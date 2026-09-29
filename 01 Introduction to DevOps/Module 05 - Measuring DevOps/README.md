# Module 05: Measuring DevOps

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 05: Measuring DevOps pada kursus Introduction to DevOps, mencakup perancangan sistem evaluasi dan insentif organisasi, mitigasi kesalahan pengukuran, eliminasi metrik semu (*vanity metrics*), penerapan empat metrik utama DORA, kerangka evaluasi budaya tim Dr. Nicole Forsgren, serta komparasi mendalam antara DevOps dan *Site Reliability Engineering* (SRE).

---

### Ringkasan Konsep Inti

- **Bahaya Salah Insentif (The Folly of Rewarding for A While Hoping for B):**
  - Mengutip riset Steven Kerr (1975): setiap individu dalam organisasi secara alami mencari informasi mengenai tindakan apa yang dihargai dan diberi imbalan, lalu mencurahkan tenaganya untuk mengejar hal tersebut hingga mengabaikan hal yang tidak diukur.
  - Kaidah mutlak manajemen: Anda mendapatkan apa yang Anda ukur (*you get what you measure*).
  - Mengukur jumlah baris kode (*Lines of Code* / KLOC) hanya menghasilkan kode yang bertele-tele dan tidak efisien.
  - Menerapkan kurva pemeringkatan relatif (*stack ranking*) merusak kerja sama dan memicu perilaku antisosial antarkaryawan.
- **Mengukur Perilaku Sosial (Social Metrics):**
  - Jika organisasi menginginkan budaya kolaboratif (*social coding*), sistem penilaian harus secara eksplisit mengukur aktivitas sosial dan penggunaan ulang kode:
    - *Who is leveraging the code you are building?* (Mendorong perancangan kode bernilai tinggi yang dapat dipakai ulang oleh tim lain).
    - *Whose code are you leveraging?* (Mendorong efisiensi dengan memanfaatkan komponen yang sudah ada alih-alih menciptakan kembali roda dari nol).
- **Pergeseran Paradigma Ketersediaan: Dari MTTF ke MTTR:**
  - Meninggalkan upaya usang mencegah server agar tidak pernah mati (*Mean Time to Failure* / MTTF).
  - Beralih ke filosofi kesiapan pemulihan seketika (*Mean Time to Recovery* / MTTR). Dalam arsitektur kontainer mikro, jika satu instans mati, instans baru langsung menyala dalam hitungan detik tanpa disadari oleh pelanggan (*high availability*).

---

### Kerangka Metrik Kinerja dan Budaya

- **Vanity Metrics vs Actionable Metrics:**
  - **Vanity Metrics:** Angka statistik mentah (seperti jumlah *hits* atau *pageviews* pada situs web) yang memberi kepuasan semu tetapi tidak memberikan petunjuk logis mengenai tindakan perbaikan apa yang harus diambil.
  - **Actionable Metrics:** Metrik yang secara eksplisit menunjukkan korelasi sebab-akibat (*cause and effect*), seperti peningkatan pendapatan sebesar 20% pada pengujian terpisah (*A/B testing*) yang langsung memandu keputusan peluncuran fitur ke seluruh pengguna.
- **Empat Metrik Kunci DORA (The Four Key DORA Metrics):**
  - Dirumuskan oleh Dr. Nicole Forsgren sebagai tolok ukur efektivitas penghantaran perangkat lunak:
    - **Mean Lead Time for Changes:** Durasi dari pencetusan kebutuhan hingga kode berhasil berjalan di produksi.
    - **Deployment Frequency:** Seberapa sering kode baru dirilis ke lingkungan produksi secara aman.
    - **Change Failure Rate (CFR):** Persentase rilis produksi yang menimbulkan kegagalan atau insiden.
    - **Mean Time to Recovery (MTTR):** Rata-rata durasi yang dibutuhkan untuk memulihkan layanan operasional kembali normal saat terjadi kegagalan sistem.
- **Evaluasi Budaya Tim Dr. Nicole Forsgren:**
  - Mengukur kesehatan budaya kerja menggunakan skala Likert 1 (Sangat Tidak Setuju) hingga 7 (Sangat Setuju) terhadap 6 pilar perilaku:
    - Informasi dicari secara aktif (*information is actively sought*).
    - Kegagalan adalah peluang belajar dan pembawa pesan tidak dihukum (*blameless culture*).
    - Tanggung jawab dipikul bersama (*shared responsibility*).
    - Kolaborasi lintas fungsi didorong dan diberi penghargaan.
    - Kegagalan memicu penyelidikan penyebab akar sistemik (*failure causes inquiry*).
    - Ide-ide baru disambut dengan tangan terbuka.

---

### Perbandingan Komparatif: DevOps vs SRE

- **Definisi SRE (Benjamin Treynor Sloss, Google):**
  - SRE adalah apa yang terjadi ketika seorang insinyur perangkat lunak ditugaskan untuk menangani hal-hal yang sebelumnya disebut operasional, dengan fokus utama memprogram otomatisasi guna mereduksi pekerjaan operasional repetitif (*toil reduction*).
- **Perbedaan Arsitektur Organisasi dan Pengendalian Stabilitas:**
  - **Struktur Tim:** SRE mempertahankan tim pengembang dan tim operasional (SRE) terpisah namun dengan kolam sumber daya bersama (*shared staffing pool*), sedangkan DevOps menyatukan Dev dan Ops ke dalam satu tim lintas fungsi.
  - **Pengendalian Stabilitas:** SRE menggunakan anggaran kesalahan (*Error Budgets* = 100% - SLO) untuk membatasi rilis baru jika kuota gangguan terlampaui; sedangkan DevOps mengandalkan otomatisasi pipa rilis CI/CD dan tanggung jawab penuh pengembang (*you build it, you run it*).
- **Sinergi Komplementer:**
  - Tim SRE bertindak sebagai penyedia platform terkelola (*platform provider*) yang memelihara keandalan infrastruktur cloud, sedangkan tim DevOps bertindak sebagai konsumen platform (*platform consumers*) yang memanfaatkan infrastruktur tersebut untuk merilis aplikasi bisnis secara mandiri.
