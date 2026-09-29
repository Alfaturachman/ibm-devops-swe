# Measuring DevOps

Dokumen ini menyajikan rangkuman komprehensif mengenai perancangan sistem pengukuran dan metrik dalam DevOps, bahaya salah insentif (*folly of rewarding for A while hoping for B*), perbandingan metrik semu (*vanity metrics*) vs metrik yang dapat ditindaklanjuti (*actionable metrics*), empat metrik utama DORA, kerangka evaluasi budaya tim Dr. Nicole Forsgren, serta komparasi mendalam antara DevOps dan *Site Reliability Engineering* (SRE).

---

### 1. The Folly of Rewarding for "A" While Hoping for "B"

#### A. Landasan Teori Perilaku Organisasi
- **Kajian Klasik Steven Kerr (1975):**
  - Mengutip riset Steven Kerr dalam *Academy of Management Journal* bertajuk *"On the folly of rewarding for A, while hoping for B"*.
  - Setiap manusia dan organisme dalam organisasi secara alami mencari informasi mengenai tindakan apa yang diberi penghargaan (*rewarded*), kemudian mencurahkan energinya untuk melakukan (atau berpura-pura melakukan) tindakan tersebut, bahkan hingga mengabaikan hal-hal yang tidak diukur.
- **Prinsip Utama Pengukuran:**
  - Organisasi tidak dapat memberi penghargaan pada perilaku A tetapi mengharapkan tim menghasilkan perilaku B.
  - Kaidah mutlak manajemen: Anda mendapatkan apa yang Anda ukur (*you get what you measure*).

#### B. Dampak Negatif Metrik yang Salah Arah
- **Pengukuran Jumlah Baris Kode (*Lines of Code* / KLOC):**
  - Mengukur produktivitas pengembang berdasarkan ribuan baris kode (*KLOC*) hanya akan menghasilkan perangkat lunak yang bertele-tele (*verbose code*), tidak efisien, dan sulit dipelihara. Pengembang termotivasi memperbanyak baris kode daripada menulis solusi yang ringkas dan elegan.
- **Pemeringkatan Relatif Antarkaryawan (*Stack Ranking*):**
  - Memeringkatkan pengembang dalam kurva kompetisi internal merusak kerja sama tim dan memicu perilaku antisosial (*antisocial behavior*).
  - Karyawan enggan membantu rekan kerja yang kesulitan karena khawatir rekan tersebut akan memperoleh peringkat evaluasi, kenaikan gaji, atau promosi yang lebih tinggi.

#### C. Mengukur Perilaku Sosial (Social Metrics)
Jika organisasi menginginkan kolaborasi dan keterbukaan (*social coding*), sistem evaluasi harus secara eksplisit mengukur aktivitas sosial dan berbagi pengetahuan:
- **1. Pemanfaatan Kode oleh Pihak Luar (*Who is leveraging your code?*):**
  - Mengukur seberapa banyak tim lain atau komunitas internal yang menggunakan modul atau komponen yang Anda bangun. Hal ini mendorong pengembang mendesain kode yang bernilai, modular, dan dapat dipakai ulang.
- **2. Pemanfaatan Kode Milik Pihak Lain (*Whose code are you leveraging?*):**
  - Mengukur seberapa sering pengembang memanfaatkan komponen yang sudah ada alih-alih menciptakan kembali roda dari nol (*reinventing the wheel*).

#### D. Penetapan Garis Dasar (Baseline) dan Sasaran Bertahap
- **Menetapkan Baseline Nyata:**
  - Evaluasi perbaikan berkelanjutan memerlukan titik awal (*baseline*) terukur. Misalnya, proses rilis saat ini membutuhkan 6 teknisi dan memakan waktu 10 jam.
- **Menetapkan Target Terukur:**
  - Tetapkan sasaran kuantitatif spesifik satu per satu, misalnya memangkas durasi rilis dari 10 jam menjadi 2 jam (peningkatan lima kali lipat).
  - Jika eksperimen alur kerja belum mencapai target, lakukan penyesuaian hingga angka tercapai sebelum beralih ke sasaran berikutnya.

#### E. Pergeseran Paradigma Ketersediaan: Dari MTTF ke MTTR
- **Pola Pikir Usang (*Mean Time to Failure* / MTTF):**
  - Berfokus pada upaya mustahil mencegah server agar tidak pernah mengalami gangguan (*failure prevention*).
- **Pola Pikir Modern DevOps (*Mean Time to Recovery* / MTTR):**
  - Mengantisipasi bahwa kegagalan infrastruktur pasti akan terjadi (*failure is inevitable*).
  - Fokus utama dialihkan pada kecepatan pemulihan sistem saat insiden terjadi (*failure recovery*).
  - Dalam arsitektur layanan mikro berbasis kontainer, jika satu instans mengalami gangguan, orkestrator segera menyalakan instans baru dalam hitungan detik sehingga pengguna akhir tidak merasakan adanya gangguan layanan (*high availability*).

---

### 2. Vanity Metrics vs. Actionable Metrics

#### A. Karakteristik Vanity Metrics (Metrik Semu)
- **Definisi dan Keterbatasan:**
  - *Vanity metrics* adalah angka-angka statistik yang memberikan rasa bangga dan kepuasan semu (*good for feeling awesome*), namun tidak memberikan panduan objektif untuk pengambilan keputusan bisnis (*bad for taking action*).
- **Contoh Kasus Jumlah Kunjungan (*Hits/Pageviews*):**
  - Mengumumkan bahwa situs web memperoleh 10.000 *hits* tidak memberikan wawasan operasional apa pun.
  - Metrik ini tidak menjelaskan apakah angka tersebut berasal dari 1 orang pengguna yang mengalami galat dan melakukan klik berulang secara cemas sebanyak 10.000 kali, atau 10.000 pengunjung unik yang langsung meninggalkan situs web tanpa bertransaksi.
  - Angka aktivitas mentah tanpa konteks tidak menunjukkan apakah aktivitas tersebut bernilai positif atau merugikan.

#### B. Karakteristik Actionable Metrics (Metrik yang Dapat Ditindaklanjuti)
- **Hubungan Sebab-Akibat yang Jelas (*Cause and Effect*):**
  - *Actionable metrics* secara eksplisit mengaitkan tindakan spesifik yang diambil dengan hasil terukur yang diperoleh.
- **Studi Kasus Pengujian Terpisah (*A/B Testing*):**
  - Menampilkan fitur baru pada 50% pengguna (Grup B) sementara 50% sisanya (Grup A) melihat versi lama.
  - Jika data menunjukkan pendapatan per pengguna pada Grup B meningkat sebesar 20%, tim memiliki dasar logis yang kuat untuk mengambil tindakan: merilis fitur ke 100% pengguna dan mengembangkan fitur serupa.

#### C. Rekomendasi Metrik Menurut Eric Ries (The Lean Startup)
Eric Ries merumuskan beberapa contoh metrik yang dapat ditindaklanjuti dalam pengembangan produk:
- Mempersingkat waktu peluncuran fitur baru ke pasar (*reduce time to market*).
- Meningkatkan ketersediaan produk secara menyeluruh (*increase product availability*).
- Mempersingkat durasi proses penerapan rilis perangkat lunak (*reduce deployment time*).
- Meningkatkan persentase cacat yang terdeteksi pada fase pengujian sebelum mencapai produksi.
- Meningkatkan efisiensi pemanfaatan infrastruktur komputasi untuk menekan harga pokok penjualan (*Cost of Goods Sold* / COGS).
- Mempercepat siklus penyampaian umpan balik pengguna dan telemetri kinerja kepada manajer produk.

#### D. Empat Metrik Utama DORA (The Four DORA Metrics)
Dr. Nicole Forsgren dalam paparannya *"Tools Won't Fix Your Broken DevOps"* merumuskan empat metrik utama yang menjadi standar global dalam mengukur efektivitas penghantaran perangkat lunak:
- **1. Mean Lead Time for Changes:**
  - Mengukur durasi yang dibutuhkan dari saat sebuah ide atau kebutuhan diajukan oleh pemangku kepentingan hingga kode tersebut berhasil berjalan di lingkungan produksi.
- **2. Release Frequency (Deployment Frequency):**
  - Seberapa sering organisasi berhasil merilis pembaruan perangkat lunak ke lingkungan produksi secara aman.
- **3. Change Failure Rate (CFR):**
  - Rasio persentase rilis produksi yang menimbulkan kegagalan, insiden, atau membutuhkan pemulihan darurat:

$$\text{CFR} = \frac{\text{Jumlah Rilis yang Mengakibatkan Insiden}}{\text{Total Rilis ke Produksi}} \times 100\%$$

  - Kecepatan rilis tidak ada artinya jika mengorbankan stabilitas sistem.
- **4. Mean Time to Recovery (MTTR):**
  - Rata-rata durasi waktu yang diperlukan untuk memulihkan layanan operasional kembali normal ketika terjadi kegagalan di lingkungan produksi:

$$\text{MTTR} = \frac{\sum \text{Durasi Pemulihan Insiden}}{\text{Total Insiden yang Terjadi}}$$

---

### 3. Measuring Team Culture (Evaluasi Budaya Tim)

#### A. Metodologi Pengukuran Budaya Dr. Nicole Forsgren
- **Pendekatan Skala Likert DORA:**
  - Evaluasi kesehatan budaya kerja tim diukur menggunakan skala 1 (Sangat Tidak Setuju) hingga 7 (Sangat Setuju) terhadap serangkaian pernyataan perilaku.
- **Enam Pernyataan Evaluasi Budaya:**
  - **1. Informasi Dicari Secara Aktif (*Information is actively sought*):**
    - Mengukur rasa ingin tahu intelektual tim untuk memahami alasan di balik setiap kejadian dan keterbukaan arus data.
  - **2. Kegagalan adalah Peluang Belajar dan Pembawa Pesan Tidak Dihukum (*Failures are learning opportunities and messengers are not punished*):**
    - Menghilangkan budaya "menembak pembawa pesan buruk" (*don't shoot the messenger*). Karyawan tidak akan transparan jika keterbukaan berisiko menimbulkan sanksi pribadi.
    - Menanamkan keyakinan bahwa tidak ada karyawan yang sengaja merusak produksi; jika kegagalan terjadi, sistemlah yang gagal melindungi personel tersebut (*the system failed the person*).
    - Membangun budaya tanpa menyalahkan (*blameless culture*).
  - **3. Tanggung Jawab Dipikul Bersama (*Responsibilities are shared*):**
    - Mengikis sekat fungsional. Tidak ada konsep "bocor hanya terjadi di sisi perahumu"; ketika terjadi insiden, seluruh tim bahu-membahu menuntaskan masalah.
  - **4. Kolaborasi Lintas Fungsi Didorong dan Diberi Penghargaan (*Cross-functional collaboration is encouraged and rewarded*):**
    - Menyelaraskan sistem evaluasi kinerja agar menghargai kontribusi kerja sama tim di atas pencapaian individu yang terisolasi.
  - **5. Kegagalan Memicu Penyelidikan Sistemik (*Failure causes inquiry*):**
    - Penyelidikan pascainsiden tidak berfokus pada "siapa yang bersalah" (*who done it*), melainkan menganalisis "di mana letak kelemahan sistem" (*where did the system fail*) melalui analisis akar penyebab (*root cause analysis*) demi perbaikan berkelanjutan.
  - **6. Ide-Ide Baru Disambut Terbuka (*New ideas are welcomed*):**
    - Memastikan setiap anggota tim merasa masukannya didengarkan secara tulus dan tidak sekadar menerima basa-basi manajemen.

---

### 4. DevOps vs. Site Reliability Engineering (SRE)

#### A. Definisi dan Filosofi Dasar SRE
- **Konsep SRE (Benjamin Treynor Sloss, Google):**
  - *"SRE adalah apa yang terjadi ketika seorang insinyur perangkat lunak ditugaskan untuk menangani hal-hal yang sebelumnya disebut operasional."*
- **Pola Pikir Rekayasa vs Administrator Sistem Tradisional:**
  - Administrator sistem konvensional cenderung menerima tugas-tugas konfigurasi manual secara berulang.
  - Seorang insinyur perangkat lunak mungkin melakukan tugas manual pada kesempatan pertama dan kedua; namun pada kali ketiga, mereka akan menulis kode otomatisasi untuk menyelesaikannya secara permanen.
- **Mereduksi Kelelahan Kerja Repetitif (*Toil Reduction*):**
  - *Toil* adalah pekerjaan operasional yang bersifat manual, repetitif, dapat diotomatiskan, serta tidak memberikan nilai jangka panjang bagi produk.
  - Praktisi SRE mengalokasikan maksimal 50% waktu kerja mereka untuk menangani operasional rutin, sementara 50% sisanya wajib dialokasikan untuk rekayasa otomatisasi menggunakan *Infrastructure as Code*.

#### B. Perbandingan Komparatif: DevOps vs SRE
- **1. Struktur Organisasi Tim:**
  - **DevOps:** Meruntuhkan pemisahan silo dengan menyatukan pengembang dan operasional ke dalam satu tim lintas fungsi yang solid.
  - **SRE:** Tetap mempertahankan pemisahan struktural antara tim pengembang dan tim operasional (SRE), namun menggunakan kolam sumber daya bersama (*shared staffing pool*): penambahan satu posisi SRE memotong satu kuota pengembang untuk menjaga keseimbangan kapasitas.
- **2. Mekanisme Pengendalian Stabilitas:**
  - **SRE (Error Budget):**
    - Stabilitas dikendalikan melalui anggaran kesalahan (*Error Budget*) yang diturunkan dari sasaran tingkat layanan (*Service Level Objective* / SLO).

$$\text{Error Budget} = 100\% - \text{SLO}$$

    - Jika target ketersediaan layanan adalah $99{,}9\%$, maka anggaran batas toleransi henti layanan (*downtime*) adalah $0{,}1\%$.
    - Selama batas *error budget* tidak terlampaui, pengembang bebas merilis pembaruan ke produksi. Namun ketika kegagalan melebihi kuota anggaran, proses rilis dibekukan dan pengembang dialihkan untuk membantu tim SRE memulihkan stabilitas sistem.
  - **DevOps (Automated Delivery & Full Ownership):**
    - Menjaga stabilitas melalui otomatisasi pengujian ketat pada pipa CI/CD dan menanamkan tanggung jawab penuh bagi pengembang terhadap kode mereka di produksi (*you build it, you run it*).
- **3. Kebijakan Rotasi Pengembang:**
  - Dalam SRE, pengembang mengalokasikan sekitar 5% waktu mereka untuk berotasi di tim operasional guna memahami beban kerja produksi secara langsung.

#### C. Titik Temu dan Sinergi Antara DevOps dan SRE
- **Kesamaan Nilai Pokok:**
  - Keduanya bertujuan menghantarkan perangkat lunak secara cepat dengan stabilitas tinggi.
  - Keduanya menjunjung tinggi transparansi operasional dan budaya tanpa menyalahkan (*blameless culture*).
- **Kolaborasi Komplementer dalam Praktik:**
  - SRE berperan sebagai penyedia platform (*platform provider*): merancang, mengotomatiskan, dan menjaga keandalan infrastruktur komputasi awan (*Platform as a Service* / PaaS).
  - Tim DevOps berperan sebagai konsumen platform (*platform consumers*): memanfaatkan platform terkelola tersebut untuk membangun, menguji, dan merilis aplikasi secara mandiri dan cepat.

---

### 5. Key Takeaways and Summary

#### A. Poin-Poin Strategis Modul 05
- **Selaraskan Penghargaan dengan Target:**
  - Hindari jebakan memberi imbalan pada metrik A sementara mengharapkan perilaku B (*you get what you measure*). Ukur kolaborasi sosial untuk menumbuhkan budaya berbagi kode.
- **Fokus pada Pemulihan Cepat (MTTR):**
  - Alihkan fokus dari sekadar mencegah gangguan (MTTF) menjadi kesiapan memulihkan sistem secara instan (MTTR) memanfaatkan kontainer dan arsitektur layanan mikro.
- **Tinggalkan Vanity Metrics:**
  - Gunakan metrik yang dapat ditindaklanjuti (*actionable metrics*) yang menunjukkan korelasi sebab-akibat nyata terhadap nilai pelanggan dan performa bisnis.
- **Kuasai Empat Metrik Kunci DORA:**
  - Pantau dan optimalkan secara teratur: *Lead Time for Changes*, *Release Frequency*, *Change Failure Rate*, dan *Mean Time to Recovery*.
- **Ukur Kesehatan Budaya Secara Terbuka:**
  - Evaluasi keterbukaan informasi, budaya tanpa menyalahkan (*blameless culture*), dan penerimaan ide baru menggunakan kerangka kerja evaluasi DORA.
- **Integrasikan DevOps dan SRE:**
  - SRE menyediakan fondasi platform infrastruktur otomatis dengan tata kelola *error budgets*, sementara tim DevOps mengonsumsi platform tersebut untuk menghantarkan nilai produk secara tangkas.
