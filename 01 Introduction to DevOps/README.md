# Introduction to DevOps

Dokumen ini merupakan ringkasan eksekutif dan panduan master dokumentasi untuk kursus Introduction to DevOps, bagian pertama dari program sertifikasi profesional IBM DevOps and Software Engineering. Kursus ini membedah transformasi budaya, pola pikir, metodologi kerja, struktur pengorganisasian tim, sistem metrik terukur, hingga studi kasus nyata dalam membangun praktik rekayasa perangkat lunak modern yang tangkas, stabil, dan berkesinambungan.

---

### Bagian 1: Struktur Modul Kursus

1. **Module 01 - Overview of DevOps**
2. **Module 02 - Thinking DevOps**
3. **Module 03 - Working DevOps**
4. **Module 04 - Organizing for DevOps**
5. **Module 05 - Measuring DevOps**
6. **Module 06 - Case Studies and Final Exam**

---

### Bagian 2: Rangkuman Eksekutif per Modul

#### Modul 1: Overview of DevOps
- Mengupas urgensi bisnis di era disrupsi di mana lebih dari separuh perusahaan Fortune 500 telah tersingkir sejak tahun 2000 akibat ketidakmampuan beradaptasi dengan model bisnis baru.
- Menegaskan bahwa teknologi berperan sebagai instrumen pemungkin (*enabler*) inovasi, bukan penggerak mandiri (*driver*).
- Mendefinisikan DevOps bukan sebagai alat atau jabatan fungsional, melainkan praktik kolaborasi menyeluruh antara teknisi *Development* dan *Operations* di sepanjang siklus hidup rekayasa perangkat lunak (SDLC) berlandaskan prinsip *Lean* dan *Agile*.
- Menjabarkan tiga dimensi DevOps (Budaya, Metode, dan Alat), dengan penekanan bahwa budaya merupakan faktor penentu kesuksesan nomor satu.
- Menganalisis kelemahan kritis metodologi Waterfall tradisional, keterbatasan adopsi Agile yang memicu fenomena *Two-Speed IT* dan *Shadow IT*, serta sejarah perkembangan gerakan DevOps dari Velocity Conference 2009 hingga publikasi ilmiah DORA.

#### Modul 2: Thinking DevOps
- Mentransformasi cara berpikir organisasi melalui adopsi prinsip *social coding* dan *inner source* guna mendorong keterbukaan kode internal serta mengeliminasi duplikasi pekerjaan (*reinventing the wheel*).
- Menjelaskan efektivitas *pair programming* (peran *Driver* dan *Navigator*) dalam mendeteksi galat lebih awal serta mempercepat transfer keahlian tim.
- Memaparkan pedoman repositori Git (*Git Feature Branch Workflow*) dan larangan menggabungkan *pull request* buatan sendiri demi menjamin peninjauan rekan kerja (*code review*).
- Mendemonstrasikan keunggulan alur satu bagian (*single-piece flow*) dalam kelompok kerja kecil (*small batches*) dibandingkan *batch* besar melalui percepatan siklus deteksi kesalahan dari 15 menit menjadi 24 detik.
- Mengulas hakikat sejati *Minimum Viable Product* (MVP) sebagai alat pembelajaran untuk mengarahkan keputusan *pivot* atau *persevere*, metodologi TDD dari dalam ke luar (*inside-out*), BDD dari luar ke dalam (*outside-in*) berbasis bahasa Gherkin, serta arsitektur layanan mikro nir-status (*stateless microservices*).
- Menjabarkan pola-pola ketahanan arsitektur menghadapi kegagalan yang tak terhindarkan (*designing for failure*): *retry with exponential backoff*, *circuit breaker*, *bulkhead*, serta validasi empiris via *chaos engineering*.

#### Modul 3: Working DevOps
- Membedah kritik terhadap Taylorisme (manajemen komando lini perakitan pabrik) dan kekeliruan menganalogikan rekayasa perangkat lunak dengan proyek teknik sipil.
- Mengubah paradigma dari proyek sementara (*project model*) menjadi kepemilikan produk jangka panjang (*product model*) yang dikelola oleh tim stabil dan langgeng dengan kepemilikan ujung ke ujung (*you build it, you run it*).
- Meruntuhkan Tembok Kebingungan (*wall of confusion*) dengan menyelaraskan metrik keberhasilan pengembang (inovasi) dan operasional (stabilitas).
- Menjelaskan praktik *Infrastructure as Code* (IaC) untuk mengeliminasi pergeseran konfigurasi (*server drift*) dan memperlakukan infrastruktur sebagai ternak yang fana, bukan hewan peliharaan (*cattle, not pets*).
- Menguraikan disiplin pengiriman kekal (*immutable delivery*) melalui kontainer Docker dengan larangan keras menambal kontainer yang sedang berjalan.
- Mengupas tuntas pemetaan siklus hidup *Continuous Integration* (CI) dan *Continuous Delivery* (CD), lima prinsip inti CD, serta teknik manajemen risiko modern melalui *feature flags*, *canary testing*, dan *blue-green deployment* tanpa waktu henti layanan (*zero downtime*).

#### Modul 4: Organizing for DevOps
- Menetapkan kriteria pembentukan tim berperforma tinggi: berukuran kecil (5 hingga 7 personel, aturan *two-pizza team*), berdedikasi penuh tanpa pergantian konteks (*context switching*), lintas fungsi (*cross-functional*), dan swakelola (*self-organizing*).
- Menjelaskan dampak Hukum Conway (*Conway's Law*): struktur arsitektur sistem merupakan cerminan dari struktur komunikasi organisasi.
- Menguraikan restrukturisasi organisasi berbasis domain bisnis vertikal (*business domains* / *Reverse Conway Maneuver*) di mana setiap tim beroperasi seperti perusahaan rintisan mini (*mini start-up*) yang otonom.
- Mengidentifikasi pembentukan divisi "Tim DevOps" terpisah sebagai anti-pola (*antipattern*) yang ironis karena hanya menambah lapisan silo dan birokrasi baru.
- Mengkaji kaidah Jez Humble bahwa pemisahan tindakan dari konsekuensi melahirkan sikap apatis (dibuktikan melalui studi kasus pembentukan tim QA terpisah yang justru menurunkan kualitas kode).
- Menanamkan rasa tanggung jawab dan empati operasional melalui keterlibatan pengembang dalam rotasi jadwal siaga darurat (*on-call rotation / pager duty*).

#### Modul 5: Measuring DevOps
- Membedah bahaya salah insentif melalui kajian Steven Kerr: *"On the folly of rewarding for A, while hoping for B"* (menegaskan kaidah *you get what you measure*).
- Menyoroti kegagalan pengukuran berbasis jumlah baris kode (KLOC) dan pemeringkatan relatif (*stack ranking*), serta memperkenalkan metrik perilaku sosial untuk mendorong penggunaan ulang kode (*code reuse*).
- Menjelaskan pergeseran paradigma ketersediaan sistem: dari upaya usang mencegah kegagalan (*Mean Time to Failure* / MTTF) menjadi kesiapan pemulihan kilat (*Mean Time to Recovery* / MTTR) memanfaatkan kontainer dan layanan mikro.
- Mengeliminasi ketergantungan pada metrik semu (*vanity metrics* seperti jumlah *hits* situs web) dan beralih ke metrik yang dapat ditindaklanjuti (*actionable metrics*).
- Menguraikan Empat Metrik Kunci DORA (*Deployment Frequency*, *Lead Time for Changes*, *Change Failure Rate*, dan *Mean Time to Recovery*) serta kerangka evaluasi budaya tanpa menyalahkan (*blameless culture*) dari Dr. Nicole Forsgren.
- Membandingkan DevOps dengan *Site Reliability Engineering* (SRE): membedah konsep *toil reduction*, mekanisme stabilitas *error budgets*, serta sinergi di mana SRE bertindak sebagai penyedia platform (*platform provider*) dan DevOps sebagai konsumen platform (*platform consumer*).

#### Modul 6: Case Studies and Final Exam
- Menganalisis skenario studi kasus terapan:
  - **Skenario 1 (Thinking DevOps):** Mengatasi hambatan antrean tiket infrastruktur melalui pembentukan tim lintas fungsi dan penyediaan TI mandiri (*self-service IT*).
  - **Skenario 2 (Organizing for DevOps):** Mengatasi kelambatan koordinasi dan konflik integrasi akhir bulan melalui restrukturisasi domain bisnis dan penerapan *Continuous Integration* harian.
  - **Skenario 3 (Social Coding):** Membangun budaya berbagi kode melalui repositori publik internal dan sistem penghargaan yang mengapresiasi kontribusi lintas tim.
- Menyajikan evaluasi komprehensif 20 soal ujian akhir (*Final Exam*) yang menguji penguasaan materi holistik di seluruh modul pembelajaran, dilengkapi pembahasan logis dan objektif untuk setiap konsep kunci.

---

### Bagian 3: Key Takeaways

- **Budaya Kolaborasi di Atas Segalanya:**
  - Perkakas dan otomatisasi modern tidak akan membuahkan hasil tanpa transformasi budaya kerja yang dilandasi oleh keterbukaan (*openness*), transparansi (*transparency*), rasa saling percaya (*trust*), dan lingkungan tanpa menyalahkan (*blameless culture*).
- **Rekayasa Perangkat Lunak Adalah Kriya Pengetahuan:**
  - Tinggalkan model manajemen komando manufaktur massal (Taylorisme) dan model proyek sipil yang kaku. Bangun tim stabil lintas fungsi dengan kepemilikan ujung ke ujung (*you build it, you run it*).
- **Kelincahan Melalui Ukuran Kecil (Small Batches):**
  - Mereduksi risiko kegagalan bukan dengan menunda atau menghentikan perubahan, melainkan dengan memecah pekerjaan ke dalam rilis kecil berkala yang diintegrasikan secara harian melalui pipa otomatis CI/CD.
- **Rancang Sistem Menghadapi Kegagalan:**
  - Karena kegagalan dalam sistem terdistribusi tidak dapat dihindari, fokus rekayasa dialihkan pada kecepatan pemulihan (MTTR) melalui pemanfaatan arsitektur layanan mikro nir-status, kontainer kekal (*immutable containers*), serta pola ketahanan *circuit breaker* dan *bulkhead*.
- **Ukur Hal-Hal yang Menggerakkan Nilai Nyata:**
  - Abaikan metrik semu yang menyesatkan. Selaraskan sistem insentif dengan perilaku kolaboratif dan pantau performa pengiriman perangkat lunak menggunakan Empat Metrik Kunci DORA secara terukur.
