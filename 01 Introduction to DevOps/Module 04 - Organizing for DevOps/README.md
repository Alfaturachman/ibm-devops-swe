# Module 04: Organizing for DevOps

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 04: Organizing for DevOps pada kursus Introduction to DevOps, mencakup kriteria pembentukan tim berkinerja tinggi, pengaruh Hukum Conway terhadap arsitektur sistem, restrukturisasi tim berbasis domain bisnis, bahaya anti-pola pembentukan divisi "Tim DevOps", serta penanaman rasa tanggung jawab kolektif melalui prinsip kepemilikan ujung ke ujung.

---

### Ringkasan Konsep Inti

- **Karakteristik Tim DevOps Berperforma Tinggi:**
  - **Berukuran Kecil (*Small Teams*):** Terdiri dari 5 hingga 7 personel, maksimal 10 orang (aturan *two-pizza team*), guna mencegah ledakan eksponensial jalur komunikasi antarpribadi yang memicu kemacetan koordinasi.
  - **Berdedikasi Penuh (*Dedicated*):** Tidak membagi fokus ke banyak proyek sekaligus untuk menghindari kerugian produktivitas akibat pergantian konteks (*context switching*).
  - **Lintas Fungsi (*Cross-Functional*):** Menggabungkan seluruh disiplin yang dibutuhkan (pengembang, penguji, teknisi operasional, analis bisnis) dalam satu tim tanpa terhambat antrean tiket birokratis.
  - **Swakelola (*Self-Organizing*):** Memiliki wewenang mandiri dalam mengelola alur kerja dan berkomitmen menyelesaikan paket tugas per iterasi *sprint*.
- **Hukum Conway (Conway's Law):**
  - Dirumuskan oleh Melvin Conway (1968): struktur arsitektur sistem yang dihasilkan oleh suatu organisasi merupakan cerminan langsung dari struktur komunikasi internal organisasi tersebut.
  - Pembagian organisasi berdasarkan lapisan teknologi horisontal (tim UI, tim backend, tim DBA) pasti menghasilkan arsitektur monolitik tiga lapis (*three-tier architecture*) yang lambat dan kaku.
- **Restrukturisasi Berbasis Domain Bisnis (*Business Domains*):**
  - Menerapkan *Reverse Conway Maneuver*: merestrukturisasi tim mengelilingi domain kapabilitas bisnis vertikal (seperti Tim Akun, Tim Personalisasi, dan Tim Pergudangan).
  - Setiap tim beroperasi seperti perusahaan rintisan mini (*mini start-up*): otonom, lintas fungsi, memiliki basis data mandiri, serta memegang tanggung jawab siklus hidup layanan secara utuh (*commit, build, deploy, maintain, operate*).

---

### Anti-Pola dan Pembongkaran Silo

- **Anti-Pola "Tim DevOps" Terpisah:**
  - *DevOps* bukanlah jabatan individual (*job title*) dan bukan departemen terpisah.
  - Elemen "Dev" merepresentasikan pengembangan kode; peran yang hanya mengelola infrastruktur tanpa menyentuh kode aplikasi hanyalah operasional biasa (*Ops*).
  - Membentuk "Tim DevOps" di antara tim pengembang dan tim operasional merupakan kesalahan fatal (anti-pola) yang diidentifikasi oleh Jez Humble, karena tindakan ini justru menciptakan silo baru dan menambah dua lapis Tembok Kebingungan.
  - Sama halnya dengan filosofi *Agile* di mana perusahaan tidak membuat "tim Agile" khusus, seluruh organisasi harus bertransformasi bersama menjadi entitas *DevOps*.
- **Tiga Pilar Budaya Kolaboratif:**
  - **Keterbukaan (*Openness*):** Kesiapan untuk saling bertukar pengetahuan dan menerima masukan lintas keahlian.
  - **Transparansi (*Transparency*):** Keterbukaan seluruh metrik kinerja, status rilis, dan kendala operasional bagi seluruh anggota tim.
  - **Rasa Percaya (*Trust*):** Manajemen memercayai tim di garis depan untuk mengambil keputusan teknis terbaik secara mandiri.

---

### Akuntabilitas dan Kepemilikan Ujung ke Ujung

- **Dampak Negatif Pemisahan Tindakan dari Konsekuensi:**
  - Jez Humble menegaskan bahwa perilaku buruk muncul saat manusia dipisahkan dari konsekuensi langsung atas tindakannya (*abstracting people away from consequences leads to apathy*).
  - **Studi Kasus Tim QA Terpisah:** Membentuk divisi QA terpisah untuk mengatasi masalah mutu justru menurunkan kualitas perangkat lunak secara drastis, karena pengembang merasa tidak lagi bertanggung jawab atas pengujian kode mereka sendiri dan melemparkan kode bermasalah ke tim QA.
- **Menumbuhkan Empati dan Tanggung Jawab Operasional:**
  - Mengembalikan tanggung jawab penulisan pengujian otomatis sepenuhnya kepada para pengembang.
  - Melakukan rotasi berkala pengembang ke lingkungan operasional untuk memahami realitas pemeliharaan sistem.
  - Menerapkan jadwal siaga darurat (*on-call rotation / pager duty*) bagi para pengembang. Pengalaman menangani insiden sistem pada dini hari di akhir pekan secara instan mendorong pengembang untuk menulis kode yang lebih tangguh dan mudah dipantau.
- **Prinsip Kepemilikan Amazon:**
  - Menghidupi prinsip kepemilikan penuh dari Werner Vogels (CTO Amazon): *"You build it, you run it!"*
  - Mencapai kesadaran bersama di tingkat organisasi yang dipadukan dengan kendali lokal terdistribusi (*shared consciousness with distributed, local control*).
