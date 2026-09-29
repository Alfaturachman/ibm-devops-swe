# Module 03: Working DevOps

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 03: Working DevOps pada kursus Introduction to DevOps, mencakup kritik terhadap manajemen komando Taylorisme, pergeseran dari analogi teknik sipil menuju kepemilikan produk terintegrasi, peruntuhan tembok kebingungan antara Dev dan Ops, otomatisasi infrastruktur berbasis kode (*Infrastructure as Code*), serta implementasi mendalam *Continuous Integration* dan *Continuous Delivery* (CI/CD).

---

### Ringkasan Konsep Inti

- **Kritik terhadap Taylorisme dan Manajemen Komando:**
  - Taylorisme (Frederick Winslow Taylor, 1911) dirancang untuk efisiensi lini perakitan pabrik massal dengan memisahkan fungsi perencanaan manajer dari eksekusi fisik buruh secara kaku.
  - Rekayasa perangkat lunak adalah pekerjaan pengetahuan berbasis kriya (*knowledge craftwork*) yang bersifat kustom (*bespoke*). Komponen baru belum pernah ada sebelumnya, sehingga memperlakukan perangkat lunak seperti lini perakitan mobil adalah kekeliruan fatal.
  - Mengadopsi prinsip Steve Jobs: mempercayakan inisiatif kepada para profesional cerdas dan menyingkirkan hambatan birokrasi serah terima antarsilo.
- **Kekeliruan Analogi Proyek Teknik Sipil:**
  - Pembangunan gedung fisik memperlakukan desain sebagai cetak biru statis: arsitek mendesain lalu pindah proyek, kontraktor membangun gedung, dan tim pemeliharaan mengelola gedung yang permanen.
  - Perangkat lunak bersifat dinamis dan organik (*organic*): lapisan sistem operasi dan dependensi pustaka di bawah aplikasi terus diperbarui karena kerentanan keamanan, serta kebutuhan pengguna terus berubah.
  - Model proyek sementara (*project model*) merusak kepemilikan. DevOps menggantinya dengan model pengembangan produk (*product development*) yang dikelola oleh tim stabil dan langgeng dengan kepemilikan ujung ke ujung (*you build it, you run it*).
- **Peruntuhan Tembok Kebingungan (The Wall of Confusion):**
  - Mengikis benturan metrik tradisional di mana pengembang diukur berdasarkan inovasi fitur baru sedangkan tim operasional diukur berdasarkan stabilitas sistem tanpa perubahan.
  - Mengubah stereotip saling menyalahkan: tim operasional tidak lagi memandang rilis pengembang sebagai ancaman (*throwing dead cats over the wall*), dan pengembang tidak lagi menganggap tim operasional lambat dan kaku.

---

### Metodologi dan Praktik Rekayasa

- **Infrastructure as Code (IaC) dan Pengiriman Kekal:**
  - Mendefinisikan konfigurasi infrastruktur ke dalam berkas teks deklaratif yang dapat dieksekusi oleh mesin (*executable code*) dan dikelola menggunakan sistem kendali versi Git (Ansible, Puppet, Chef, Terraform).
  - Mengeliminasi pergeseran konfigurasi (*server drift*) yang dipicu oleh penambalan manual acak antarteknisi.
  - Menghidupi prinsip *cattle, not pets*: server atau kontainer yang rusak tidak diperbaiki secara manual di produksi, melainkan langsung dihancurkan dan diganti dengan instans identik baru.
  - Paritas pengembangan dan produksi (*Dev-Prod parity*) melalui kontainer Docker: memastikan aplikasi di laptop pengembang berperilaku identik 100% dengan klaster produksi. Dilarang keras menambal kontainer yang sedang berjalan; modifikasi wajib dilakukan pada *image* dasar.
- **Continuous Integration (CI):**
  - Praktik integrasi kode harian ke cabang utama (*master/main branch*) dalam ukuran kecil (*small batches*) untuk mencegah konflik penggabungan masif (*merge hell*).
  - Setiap pengajuan kode (*Pull Request*) wajib melalui proses pembangunan dan pengujian otomatis mandiri (*self-testing build*).
  - Cabang utama wajib selalu berada dalam status siap rilis (*always deployable*); kode yang belum diuji secara otomatis harus diasumsikan sebagai kode rusak.
- **Continuous Delivery (CD):**
  - Disiplin memastikan perangkat lunak dapat dirilis ke lingkungan produksi kapan saja secara aman dengan memvalidasi setiap perubahan pada lingkungan yang menyerupai produksi (*production-like environment*).
  - Lima prinsip CD: kualitas terpasang sejak awal (*built-in quality*), bekerja dalam kelompok kecil, otomatisasi tugas repetitif, perbaikan berkelanjutan tanpa henti, dan tanggung jawab kolektif jika proses build mengalami kegagalan (*broken build*).

---

### Strategi Manajemen Risiko dan Penerapan Modern

- **Membangun Memori Otot Tim (*Muscle Memory*):**
  - Mengurangi risiko bukan dengan menghindari perubahan, melainkan dengan meningkatkan frekuensi penerapan ke berbagai tingkatan lingkungan uji secara otomatis.
- **Pemisahan Penerapan dari Aktivasi (*Decoupling Deployment from Activation*):**
  - **Feature Flags:** Menggelar kode baru ke lingkungan produksi dalam status nonaktif, lalu mengaktifkan atau menonaktifkan fitur secara seketika tanpa perlu melakukan *redeploy*.
  - **Canary Testing:** Mengarahkan sebagian kecil lalu lintas pengguna riil (misalnya 10%) ke versi baru untuk memvalidasi stabilitas telemetri sebelum memperluasnya ke 100% pengguna.
  - **Blue-Green Deployment:** Menyediakan dua lingkungan produksi identik berdampingan untuk melakukan pengalihan lalu lintas instan di tingkat router, menjamin ketiadaan waktu henti layanan (*zero-downtime deployment*).
