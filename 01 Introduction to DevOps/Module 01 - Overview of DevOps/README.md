# Module 01: Overview of DevOps

Dokumen ini berisi dokumentasi dan rangkuman komprehensif untuk Modul 01: Overview of DevOps pada kursus Introduction to DevOps, mencakup latar belakang historis, urgensi bisnis menghadapi disrupsi, definisi esensial, pilar-pilar agilitas, serta transisi dari Waterfall menuju DevOps.

---

### Ringkasan Konsep Inti

- **Urgensi Disrupsi dan Peran Model Bisnis:**
  - Sejak tahun 2000, sebanyak 52% perusahaan dalam daftar Fortune 500 telah lenyap akibat ketidakmampuan beradaptasi dengan disrupsi pasar.
  - Teknologi berperan sebagai instrumen pemungkin (*enabler*), bukan penggerak mandiri (*driver*). Keberhasilan inovasi pendobrak pasar (seperti Uber dan Netflix) ditentukan oleh model bisnis inovatif dalam memanfaatkan teknologi yang umumnya sudah tersedia luas.
  - Perusahaan petahana yang lambat beradaptasi (seperti Blockbuster) mengalami kebangkrutan, sementara organisasi yang mampu melakukan *pivot* strategis (seperti Garmin beralih ke perangkat pelacak kebugaran) berhasil bertahan dan berkembang.
- **Definisi dan Filosofi Fundamental DevOps:**
  - *DevOps* bukan nama jabatan (*job title*), bukan perkakas perangkat lunak (*tool*), dan bukan tim silo baru.
  - *DevOps* adalah praktik kolaborasi menyeluruh antara teknisi pengembang (*development*) dan tim operasional (*operations*) di sepanjang siklus hidup pengembangan perangkat lunak (*software development lifecycle* / SDLC), berlandaskan prinsip *Lean* dan *Agile* untuk menghantarkan perangkat lunak secara cepat dan berkesinambungan.
  - Mengubah paradigma dari sekadar menjalankan *DevOps* secara mekanis menjadi menghidupi budaya kolaboratif (*we do not "do" DevOps, we "become" DevOps*).
- **Tiga Dimensi DevOps:**
  - **Budaya (*Culture*):** Faktor nomor satu penentu keberhasilan (riset Atlassian dan DORA). Membangun transparansi, rasa saling percaya, dan tanggung jawab bersama.
  - **Metode (*Methods*):** Praktik kerja bertahap (*small batches*), integrasi berkala, dan umpan balik cepat.
  - **Alat (*Tools*):** Otomatisasi pipa rilis, platform pengujian, dan orkestrasi kontainer.
- **Tiga Pilar Agilitas (The Perfect Storm):**
  - **DevOps:** Transformasi budaya kolaboratif, pipa rilis otomatis (*automated pipelines*), serta infrastruktur kekal berbasis kode (*Infrastructure as Code* / IaC).
  - **Microservices:** Arsitektur modular yang terikat secara longgar (*loosely coupled*), tahan kegagalan, dan berkomunikasi melalui antarmuka REST API terstandarisasi.
  - **Containers:** Lingkungan eksekusi portabel berbobot ringan dengan waktu inisiasi instan dan bersifat fana (*ephemeral runtimes*).

---

### Metodologi dan Evolusi Industri

- **Kelemahan Kritis Siklus Waterfall:**
  - Pendekatan sekuensial kaku (*requirements*, desain, penulisan kode, integrasi, pengujian, operasional) menciptakan sekat silo fungsional.
  - Ketiadaan ruang perubahan di tengah jalan (*no provision for change*) dan ketiadaan hasil antara (*no intermediate delivery*).
  - Tim operasional yang posisinya paling jauh dari kode sumber (*furthest away from code*) dibebani tanggung jawab memelihara stabilitas aplikasi di produksi, memicu Tembok Kebingungan (*wall of confusion*).
- **Lahirnya Agile dan Fenomena Two-Speed IT:**
  - *Extreme Programming* (XP, Kent Beck, 1996) memperkenalkan siklus umpan balik ketat (*tight feedback loops*) dan pemrograman berpasangan (*pair programming*).
  - *Agile Manifesto* (2001) memprioritaskan individu, kolaborasi, dan tanggap terhadap perubahan di atas rencana kaku.
  - Kelemahan adopsi Agile tanpa operasional: pengembang bekerja cepat dalam siklus *sprint*, namun terhambat antrean tiket manual tim operasional (*slow speed*). Hal ini memicu *Shadow IT* di mana tim pengembang menyewa infrastruktur komputasi awan mandiri di luar pengawasan TI resmi (*fast speed*).
- **Tonggak Sejarah dan Tokoh Pelopor:**
  - **2007 - 2008:** Patrick Debois dan Andrew Clay Shafer menginisiasi diskusi *Agile Infrastructure*.
  - **2009:** John Allspaw dan Paul Hammond mempresentasikan "10+ Deploys per Day at Flickr" di Velocity Conference; Patrick Debois mendirikan konferensi *DevOpsDays* pertama di Ghent, Belgia.
  - **2010 - 2016:** Publikasi buku mani *Continuous Delivery* (Jez Humble & David Farley), *The Phoenix Project* (Gene Kim dkk.), pendirian lembaga riset DORA oleh Dr. Nicole Forsgren, serta buku panduan *The DevOps Handbook*.

---

### Studi Kasus dan Pembelajaran Industri

- **Flickr (2008 - 2009):** Membuktikan kelayakan 10 kali rilis produksi per hari (67 rilis dari 496 perubahan dalam sepekan) melalui pemecahan modul aplikasi dan kerja sama erat Dev-Ops.
- **Etsy (2011):** Menjalankan 517 kali rilis produksi dalam sebulan (rata-rata satu kali setiap 25 menit) pada lalu lintas lebih dari 1 miliar tayangan halaman dengan fondasi transparansi dan disiplin tim.
- **Adopsi Korporasi Skala Enterprise (DevOps Enterprise Summit 2016):**
  - **Ticketmaster:** Memangkas waktu rata-rata pemulihan insiden (*mean time to recovery* / MTTR) sebesar 98%.
  - **Target:** Mempercepat rilis tumpukan penuh (*full-stack deployment*) dari 3 bulan menjadi hitungan menit.
  - **Nordstrom:** Mempersingkat durasi tunggu siklus pengiriman (*lead time*) sebesar 20%.
  - **USAA:** Menekan siklus rilis layanan asuransi dari 28 hari menjadi 7 hari.
