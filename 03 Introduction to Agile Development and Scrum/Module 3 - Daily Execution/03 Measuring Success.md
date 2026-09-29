# Measuring Success and Agile Team Health

Pengukuran kinerja dan evaluasi kesehatan tim merupakan elemen fundamental dalam rekayasa perangkat lunak tangkas (*agile software engineering*). Tim berkinerja tinggi tidak mengandalkan intuisi atau perasaan semata, melainkan memanfaatkan data dan metrik yang dapat ditindaklanjuti (*actionable metrics*) untuk mendorong perbaikan berkelanjutan (*continuous improvement*). Dokumen ini merangkum prinsip pengukuran efektivitas proyek, tata kelola penutupan sprint pada papan visual (*Kanban board*), mekanisme penanganan cerita yang belum tuntas (*unfinished stories*) guna menjaga akurasi kecepatan (*velocity*), serta identifikasi anti-pola (*anti-patterns*) dan daftar periksa kesehatan tim Scrum (*Scrum health check*).

## 1. Using Measurements Effectively

Aforisme klasik dalam manajemen rekayasa menyatakan bahwa sebuah tim tidak dapat meningkatkan apa yang tidak dapat diukur (*you cannot improve what you cannot measure*). Pengukuran yang tepat memberikan visibilitas objektif terhadap proses pengembangan, memungkinkan identifikasi hambatan (*bottlenecks*), dan memvalidasi apakah perubahan proses membawa dampak positif.

### A. Vanity Metrics vs Actionable Metrics

Pemilihan metrik harus dilakukan secara selektif agar tidak menjebak tim dalam ilusi produktivitas semu.

#### a. Vanity Metrics (Metrik Semu)
*Vanity metrics* adalah angka atau data statistik yang tampak mengesankan di permukaan, namun tidak memberikan wawasan nyata mengenai perilaku pengguna, kualitas produk, atau efisiensi alur kerja:
- Contoh tipikal adalah jumlah klik (*hits/page views*) pada sebuah situs web, seperti perayaan keberhasilan karena mencapai 10.000 kunjungan.
- Data tersebut tidak menjelaskan konteks substantif: apakah 10.000 klik tersebut berasal dari 10.000 pengguna unik, atau satu orang yang me-refresh halaman secara berulang karena sistem lambat.
- Metrik ini tidak memberikan panduan mengenai tindakan apa yang harus dilakukan selanjutnya untuk meningkatkan nilai bisnis atau teknis.

#### b. Actionable Metrics (Metrik yang Dapat Ditindaklanjuti)
*Actionable metrics* adalah indikator terukur yang mengikat langsung data dengan keputusan atau tindakan spesifik yang dapat diambil oleh tim:
- Mengidentifikasi hubungan sebab-akibat yang jelas antara intervensi teknis/fitur dengan respons pengguna atau kinerja sistem.
- Penerapan pengujian terbelah (*A/B split-testing*) merupakan contoh nyata: membagi lalu lintas pengguna secara merata (50% melihat antarmuka lama dan 50% melihat antarmuka baru), kemudian mengukur fitur mana yang menghasilkan konversi atau interaksi yang diharapkan. Jika hipotesis terbukti, pengembangan dilanjutkan; jika tidak, fitur dihentikan atau disesuaikan.

### B. Menetapkan Baseline dan Target Perbaikan

Pengukuran perubahan membutuhkan titik referensi awal yang valid:
- **Pengambilan Garis Dasar (*Baseline*)**: Mengukur kinerja alur kerja saat ini sebagaimana adanya. Contoh: proses rilis ke lingkungan produksi saat ini memerlukan koordinasi 6 tim berbeda dan memakan waktu operasional selama 10 jam.
- **Penetapan Sasaran Terukur (*Goal Setting*)**: Merumuskan target perbaikan yang realistis dan spesifik, misalnya memangkas waktu rilis dari 10 jam menjadi 2 jam.
- **Iterasi Berkelanjutan**: Perbaikan performa tidak tercapai secara instan dalam satu malam, melainkan diuji dan dievaluasi secara bertahap sepanjang rangkaian sprint.
- **Deteksi Dini Cacat (*Shift-Left Testing*)**: Membandingkan rasio cacat (*bugs*) yang ditemukan pada fase pengujian (*testing*) dengan lingkungan produksi (*production*). Menemukan lebih banyak *bugs* pada fase pengujian akan menghemat biaya perbaikan darurat (*break-fix*) secara dramatis.

### C. Empat Metrik Kinerja Utama (Top 4 Actionable Metrics / DORA)

Dalam praktik DevOps dan Agile modern, terdapat empat metrik inti (dikenal secara luas sebagai metrik DORA) yang digunakan untuk menilai efisiensi dan stabilitas pengiriman perangkat lunak:
- **Waktu Tunggu Rata-Rata (*Mean Lead Time*)**: Durasi waktu yang dibutuhkan dari sejak suatu ide atau kebutuhan bisnis dicetuskan hingga fitur tersebut selesai diimplementasikan, diuji, dan berhasil berjalan di lingkungan produksi (*time to market*).
- **Frekuensi Rilis (*Release Frequency*)**: Seberapa sering tim mampu menerapkan pembaruan perangkat lunak secara aman ke lingkungan produksi. Kecepatan ini disesuaikan dengan kebutuhan bisnis nyata (misalnya harian, mingguan, atau dwi-mingguan).
- **Tingkat Kegagalan Perubahan (*Change Failure Rate*)**: Persentase perilisan (*deployments*) ke lingkungan produksi yang mengalami kegagalan, degradasi layanan, atau menimbulkan insiden yang memerlukan perbaikan segera (*hotfix*) atau pemulihan mundur (*rollback*).
- **Waktu Rata-Rata Pemulihan (*Mean Time to Recovery / MTTR*)**: Kecepatan rata-rata yang dibutuhkan tim untuk memulihkan layanan hingga kembali beroperasi normal saat terjadi insiden atau *downtime*. Paradigma modern beralih dari fokus mencegah kegagalan (*Mean Time Between Failures*) menjadi percepatan pemulihan, karena kegagalan sistem tidak terhindarkan; indikator keunggulan sejati adalah seberapa cepat sistem pulih tanpa disadari oleh pengguna akhir.

---

## 2. Getting Ready for the Next Sprint

Setelah seluruh upacara sprint (*Sprint Review* dan *Sprint Retrospective*) selesai, tim harus melakukan serangkaian aktivitas administratif penutupan siklus pada papan visual (*Kanban board*) sebelum memulai siklus berikutnya.

### A. Penutupan Status Story dan Sprint Milestone

Pengelolaan status kerja harus mencerminkan kondisi riil di lapangan:
- **Memindahkan Kartu Selesai**: Seluruh *user stories* yang berada pada kolom *Done* harus dipindahkan ke kolom *Closed*.
- **Menutup Milestone Sprint**: *Milestone* sprint yang bersangkutan harus ditutup secara eksplisit pada sistem pelacak (seperti GitHub atau ZenHub). Penutupan *milestone* secara tepat waktu memastikan bahwa grafik kecepatan (*velocity charts*) mengunci perhitungan poin secara akurat untuk sprint tersebut.
- **Membuat Milestone Baru**: Menyiapkan *milestone* untuk sprint yang akan datang, baik disiapkan langsung pada penutupan sprint atau pada awal sesi *Sprint Planning* berikutnya.

### B. Penanganan Cerita yang Belum Disentuh (Untouched Stories)

*Untouched stories* adalah kartu pekerjaan yang telah dialokasikan ke dalam *Sprint Backlog*, namun hingga akhir sprint tidak sempat dikerjakan oleh anggota tim mana pun:
- **Hindari Pemindahan Otomatis**: Anggota tim sering tergoda untuk langsung memindahkan cerita yang belum disentuh ke sprint berikutnya. Praktik ini salah karena mengabaikan dinamika bisnis.
- **Evaluasi Ulang Prioritas**: Di tengah jalannya sprint, kondisi bisnis atau kebutuhan pemangku kepentingan mungkin telah berubah, sehingga cerita lama belum tentu menjadi prioritas utama untuk sprint berikutnya.
- **Prosedur yang Benar**: Kembalikan cerita tersebut ke urutan paling atas dari *Product Backlog* (*top of Product Backlog*), dan hapus penugasan *milestone* sprint lama (*unassign from sprint milestone*) agar tidak menjadi *dangling story*. *Product Owner* bersama tim akan mengevaluasi kembali posisinya pada sesi perencanaan berikutnya.

### C. Penanganan Cerita Belum Tuntas dan Pembagian Cerita (Unfinished Stories & Story Splitting)

*Unfinished stories* adalah pekerjaan yang sudah mulai dikerjakan oleh developer (misalnya telah selesai 50%), namun belum memenuhi kriteria selesai (*Definition of Done*) saat waktu sprint habis:
- **Bahaya Pemindahan Langsung**: Memindahkan cerita yang setengah jadi secara utuh ke sprint berikutnya akan merusak akurasi metrik kecepatan (*velocity*). Tim tidak mendapatkan pengakuan atas usaha nyata yang telah dihabiskan pada sprint berjalan, dan sprint berikutnya akan tampak memiliki kapasitas yang melambung semu.
- **Pemberian Kredit Kecepatan Secara Adil**: Pengembang dan tim berhak mendapatkan kredit poin atas porsi pekerjaan yang telah berhasil diselesaikan dalam rentang waktu sprint tersebut.
- **Prosedur Pembagian Cerita (*Story Splitting*)**:
  - Tinjau ulang estimasi awal pekerjaan. Jika estimasi awal adalah 8 poin dan tim telah menyelesaikan separuhnya, sesuaikan ukuran cerita lama menjadi 4 poin.
  - Tutup (*close*) cerita yang telah diperbarui tersebut di dalam sprint saat ini dengan menyematkan label khusus, seperti `unfinished` atau `not completed`. Tindakan ini memastikan sprint mendapatkan kredit sebesar 4 poin pada grafik *velocity*.
  - Buat sebuah *user story* baru di dalam *Product Backlog* yang mencakup sisa pekerjaan yang belum selesai (misalnya sebesar 4 poin sisa, atau bobot baru jika analisis teknis menunjukkan kompleksitas yang lebih besar dari dugaan awal).
  - Tentukan pada *Sprint Planning* berikutnya apakah cerita lanjutan tersebut akan dimasukkan ke dalam sprint berikutnya atau ditunda berdasarkan prioritas *Product Owner*.

---

## 3. Agile Anti-Patterns and Scrum Health Check

Keberhasilan penerapan kerangka kerja Scrum sangat ditentukan oleh kepatuhan terhadap prinsip kolaborasi dan otonomi. Penyimpangan dari prinsip ini melahirkan anti-pola (*anti-patterns*) yang menjamin kegagalan tim.

### A. Enam Anti-Pola Utama dalam Praktik Scrum

Berikut adalah kebiasaan buruk yang harus diidentifikasi dan dihindari:

#### a. No Real Product Owner (Ketiadaan Product Owner Tunggal yang Jelas)
Kondisi di mana tim tidak memiliki figur PO yang pasti, atau sebaliknya memiliki banyak PO (*multiple product owners*):
- Ketiadaan PO menyebabkan ketiadaan visi produk yang terarah dan ketidakjelasan prioritas.
- Kehadiran lebih dari satu PO sering memicu konflik keputusan karena masing-masing pihak memiliki agenda dan instruksi yang saling bertentangan mengenai fitur apa yang harus dibangun.
- Solusi: Harus ada satu individu berdedikasi yang memegang peran sebagai visioner produk tunggal.

#### b. Teams are Too Large (Ukuran Tim Terlalu Besar)
Membentuk tim dengan anggota berkisar antara 20 hingga 30 orang:
- Jalur komunikasi meningkat secara eksponensial, mengakibatkan koordinasi harian menjadi sangat lambat dan tidak efektif.
- Ukuran ideal tim pengembang adalah berskala kecil, yaitu di bawah 10 orang (pedoman standar industri adalah $7 \pm 2$ atau $5 \pm 2$ orang).

#### c. Teams are Not Dedicated (Anggota Tim Tidak Berdedikasi Penuh)
Anggota tim dialokasikan untuk menangani beberapa proyek secara bersamaan (*context switching*):
- Terjadi insiden umum saat *Daily Stand-up*, di mana anggota tim melaporkan bahwa mereka ditarik oleh manajer fungsional untuk mengerjakan proyek lain.
- Pembagian fokus ini adalah resep menuju kegagalan (*recipe for disaster*) karena merusak komitmen sprint dan menurunkan produktivitas tim secara drastis.

#### d. Teams are Too Geographically Dispersed (Penyebaran Geografis Berlebihan)
Anggota tim tersebar di banyak zona waktu global tanpa tumpang tindih waktu kerja yang memadai:
- Menghambat komunikasi langsung dan memperlambat penyelesaian kendala harian.
- Jika tim harus bekerja lintas batas negara, terapkan aturan penempatan minimal dua orang di dalam satu zona waktu atau lokasi yang sama agar tercipta ruang kolaborasi langsung. Kondisi terbaik tetap dicapai saat seluruh anggota tim berada dalam satu zona waktu yang sama.

#### e. Teams are Siloed (Tim Tersekat Secara Fungsional)
Struktur tim yang terpisah berdasarkan keahlian fungsional (misalnya tim pengembang terpisah dari tim penguji atau tim operasi):
- Anggota tim terpaksa membuka tiket permohonan (*tickets*) ke departemen lain untuk menyelesaikan satu unit pekerjaan.
- Tim Scrum harus bersifat lintas fungsi (*cross-functional*), di mana semua keterampilan yang dibutuhkan untuk menghantarkan *Done increment* berada di dalam satu tim yang sama.

#### f. Teams are Not Self-Managing (Tim Tidak Mengelola Diri Sendiri)
Anggota tim diperlakukan sebagai pelaksana pasif yang menunggu perintah atau pembagian tugas dari atasan (*top-down task assignment*):
- Bertentangan dengan prinsip ketangkasan. Dalam tim yang sehat, anggota tim mengambil sendiri (*pulling*) cerita kerja dari *Sprint Backlog* berdasarkan prioritas tertinggi dan menetapkannya secara mandiri kepada diri mereka.

### B. Daftar Periksa Kesehatan Tim Scrum (Scrum Health Check Checklist)

Untuk memastikan tim beroperasi pada tingkat kematangan yang optimal, Scrum Master dan tim dapat menggunakan daftar periksa berikut:
- **Akuntabilitas Bersama (*Mutual Accountability*)**: Seluruh elemen tim (Scrum Master, Product Owner, dan Developers) memahami perannya masing-masing, memiliki rasa kepemilikan mendalam terhadap produk, dan saling bahu-membahu ketika menghadapi kegagalan tanpa mencari kambing hitam.
- **Sprint Berdurasi Ringkas (*Small Sprints*)**: Menjalankan siklus sprint berdurasi 1 hingga 2 minggu (maksimal 4 minggu). Sprint yang terlalu panjang (1-2 bulan) membuat tim kehilangan kelincahan dalam merespons perubahan pasar.
- **Product Backlog Terurut Rapi (*Ordered Product Backlog*)**: *Backlog* produk senantiasa terprioritisasi dengan baik, serta memuat detail dan kriteria penerimaan yang jelas bagi siapa pun yang membacanya.
- **Sprint Backlog Visual (*Visualized Sprint Backlog*)**: Sisa pekerjaan sprint divisualisasikan secara transparan menggunakan papan Kanban, memungkinkan seluruh tim melihat alur kerja sekilas pandang.
- **Daily Scrum Menghasilkan Penyesuaian Rencana (*Replanning*)**: Pertemuan harian bukan sekadar laporan status pasif, melainkan sarana evaluasi aktif untuk menyusun ulang rencana, menggeser beban kerja, atau memberikan bantuan rekan (*pairing*) jika terdapat target yang meleset.
- **Hantaran Berpotensi Rilis Setiap Sprint (*Done Increment*)**: Di setiap akhir sprint, tim selalu menghasilkan peningkatan perangkat lunak yang berfungsi secara nyata, dapat didemonstrasikan, dan memenuhi standar kualitas.
- **Umpan Balik Pemangku Kepentingan Aktif (*Active Stakeholder Feedback*)**: Pemangku kepentingan hadir secara rutin dan memberikan respons kritis (baik pujian maupun kritik) saat sesi *Sprint Review*. Sikap bungkam dari pemangku kepentingan adalah indikasi bahaya bagi kesehatan tim.
- **Pembaruan Berkelanjutan pada Backlog (*Continuous Backlog Update*)**: Masukan dan ide baru dari *Sprint Review* segera diterjemahkan menjadi cerita baru di *Product Backlog*.
- **Penyelarasan pada Sprint Retrospective**: Tim secara terbuka menyepakati apa yang berjalan baik, apa yang harus dihentikan, dan langkah konkret apa yang akan diterapkan pada sprint berikutnya guna mencapai perbaikan bertahap (*incremental improvement*).

---

## 4. Summary and Key Takeaways

Pengelolaan sprint yang matang menjembatani rencana kerja harian dengan keberhasilan pengiriman nilai produk jangka panjang:
- Keberhasilan tim diukur melalui metrik yang dapat ditindaklanjuti (*actionable metrics*), khususnya empat metrik DORA: *Mean Lead Time*, *Release Frequency*, *Change Failure Rate*, dan *Mean Time to Recovery (MTTR)*.
- Metrik semu (*vanity metrics*) seperti jumlah klik halaman harus dihindari karena tidak memberikan korelasi tindakan nyata.
- Pada penutupan sprint, *milestone* harus ditutup untuk mengunci *velocity*, dan *untouched stories* harus dikembalikan ke *Product Backlog* untuk dievaluasi ulang prioritasnya.
- Pekerjaan yang belum tuntas (*unfinished stories*) harus dipecah (*story splitting*) agar usaha developer diakui secara proporsional pada sprint berjalan, sementara sisa pekerjaan dibuatkan cerita baru demi menjaga objektivitas kapasitas sprint berikutnya.
- Menghindari enam anti-pola Scrum (ketiadaan PO tunggal, tim terlalu besar, tidak berdedikasi, terlalu tersebar, tersekat, dan tidak mandiri) serta menjalankan *Scrum Health Check* menjamin terciptanya tim rekayasa yang tangguh, kolaboratif, dan berkinerja tinggi.
