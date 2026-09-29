# Software Development Methodologies, Processes, and Team Roles

Proses pembangunan perangkat lunak modern menuntut keterpaduan antara metodologi pengembangan yang terstruktur, disiplin penjaminan kualitas dan dokumentasi, tata kelola versi yang konsisten, serta kolaborasi harmonis antarperan di dalam tim rekayasa. Keberhasilan proyek tidak hanya bertumpu pada kemahiran penulisan kode program semata, melainkan pada bagaimana alur komunikasi dan pertukaran informasi dikelola sepanjang siklus hidup sistem. Dokumen ini menyajikan kajian mendalam mengenai perbandingan tiga metodologi utama pengembangan perangkat lunak (Waterfall, V-Shape, dan Agile), tata cara penomoran versi perangkat lunak, klasifikasi dan tingkatan pengujian mutu, struktur dokumentasi produk dan prosedur operasi standar (SOP), serta pemetaan tanggung jawab berbagai peran profesional di dalam ekosistem rekayasa perangkat lunak.

## 1. Software Development Methodologies

Metodologi pengembangan perangkat lunak dipilih untuk memberikan kerangka kerja komunikasi yang jelas bagi tim pengembang, serta menetapkan mekanisme dan waktu pertukaran informasi teknis.

### A. Model Sekuensial Linier: Waterfall
Metodologi tertua dalam siklus hidup pengembangan perangkat lunak yang menerapkan alur kerja satu arah:
- **Karakteristik Operasional**: Pengembangan bergerak secara bertahap seperti air terjun, di mana luaran dari suatu fase menjadi masukan langsung bagi fase berikutnya. Pengerjaan suatu fase baru dapat dimulai hanya setelah fase sebelumnya dinyatakan selesai secara formal.
- **Perencanaan di Muka (*Upfront Planning*)**: Seluruh spesifikasi kebutuhan bisnis, analisis sistem, dan desain arsitektur dirumuskan secara menyeluruh di awal proyek.
- **Keterlibatan Klien dan Pemangku Kepentingan**: Pengguna atau klien umumnya baru dapat melihat dan menguji produk ketika sistem telah memasuki fase pengujian akhir atau rilis produksi.
- **Siklus Rilis**: Rilis versi utama (*major releases*) membutuhkan interval waktu yang sangat panjang, sering kali memakan waktu berbulan-bulan hingga bertahun-tahun.
- **Kelebihan**: Struktur sangat sederhana, tahapan terdefinisi secara kaku, serta memudahkan estimasi anggaran biaya dan alokasi sumber daya di awal proyek.
- **Kekurangan**: Sangat tidak fleksibel terhadap perubahan. Kebutuhan yang terlewat atau perubahan dinamika pasar di tengah jalan sangat sulit diakomodasi tanpa merombak jadwal dan biaya secara dramatis.

### B. Model Verifikasi dan Validasi Simetris: V-Shape Model
Variasi lanjutan dari model Waterfall yang menekankan hubungan timbal balik antara tahap perancangan dengan tahap pengujian:
- **Struktur Simetri V**:
  - **Sisi Kiri (Fase Verifikasi)**: Alur penurunan tingkat abstraksi dari perencanaan (*planning*), desain sistem (*system design*), desain arsitektur (*architecture design*), hingga desain modul rinci (*module design*).
  - **Titik Dasar V (Fase Implementasi)**: Penulisan baris kode program (*coding*).
  - **Sisi Kanan (Fase Validasi)**: Alur pengujian naik yang berkorespondensi langsung dengan fase di sisi kiri, mencakup pengujian unit (*unit testing*), pengujian integrasi (*integration testing*), pengujian sistem (*system testing*), dan pengujian penerimaan (*acceptance testing*).
- **Kelebihan**: Rencana kasus uji (*test plans*) dirancang bersamaan saat spesifikasi kebutuhan dan arsitektur disusun di sisi kiri, sehingga menghemat waktu dan meningkatkan ketelitian saat fase eksekusi pengujian di sisi kanan.
- **Kekurangan**: Memiliki tingkat kekakuan yang serupa atau bahkan lebih tinggi dibanding Waterfall. Begitu sistem memasuki fase validasi, sangat sulit untuk kembali ke fase sebelumnya guna memodifikasi fungsionalitas.

### C. Model Iteratif dan Kolaboratif: Agile
Pendekatan modern yang menggantikan kekakuan proses linier dengan serangkaian iterasi pendek dan kolaboratif:
- **Karakteristik Operasional**: Mengadopsi siklus kerja berulang yang terikat waktu (*timeboxed sprints*) berdurasi antara 1 hingga 4 minggu.
- **Pengujian Terintegrasi**: Pengujian unit dan validasi kualitas dilakukan di setiap sprint untuk menekan akumulasi risiko cacat perangkat lunak.
- **Fase Umpan Balik Cepat**: Pada setiap akhir sprint, potongan kode yang berfungsi nyata (*working software increment*) dipamerkan dalam demonstrasi sprint (*sprint demo*) kepada pemangku kepentingan untuk memperoleh masukan seketika.
- **Pengembangan Produk Layak Minimal (*Minimum Viable Product / MVP*)**: Menggabungkan fitur-fitur esensial dalam beberapa iterasi awal untuk memvalidasi asumsi bisnis secara cepat di pasar.
- **Empat Nilai Inti Manifesto Agile**:
  - Individu dan interaksi lebih diutamakan daripada proses dan alat kerja.
  - Perangkat lunak yang berfungsi lebih diutamakan daripada dokumentasi yang komprehensif.
  - Kolaborasi dengan pelanggan lebih diutamakan daripada negosiasi kontrak.
  - Tanggap terhadap perubahan lebih diutamakan daripada kepatuhan pada rencana kaku.
- **Kelebihan**: Sangat adaptif terhadap perubahan kebutuhan bisnis, risiko kegagalan proyek ditekan seminimal mungkin, dan nilai produk dihantarkan secara berkala.
- **Kekurangan**: Perencanaan anggaran dan penjadwalan jangka panjang di muka menjadi lebih menantang karena ruang lingkup produk berkembang secara dinamis.

---

## 2. Software Versions: Semantic and Calendar Versioning

Penomoran versi perangkat lunak (*software versioning*) adalah mekanisme standar yang digunakan para rekayasawan untuk melacak evolusi program, pembaruan fitur, serta perbaikan galat keamanan secara transparan bagi pengguna dan pengembang lain.

### A. Struktur dan Format Penomoran Versi
Nomor versi umumnya disajikan dalam dua, tiga, atau empat kelompok angka yang dipisahkan oleh tanda titik:
- **Versi Rilis Awal**: Ditandai dengan nomor `1.0` untuk rilis publik stabil pertama tanpa tambalan bug.
- **Versi Pra-Rilis**: Perangkat lunak yang masih dalam tahap pengujian beta biasanya menggunakan angka di bawah 1, seperti `0.9` atau `0.9.5`.
- **Penomoran Berbasis Kalender (*Calendar Versioning*)**: Sebagian ekosistem (seperti Ubuntu Linux) menggunakan tahun dan bulan rilis resmi, misalnya versi `18.04.2` menandakan rilis pada tahun 2018 bulan April dengan pembaruan paket minor kedua.

### B. Penomoran Semantik Standar (Semantic Versioning / SemVer)
Sistem penomoran semantik membagi versi ke dalam komponen hierarkis yang merefleksikan sifat perubahan kode:
- **Angka Pertama (Major Version)**: Menandakan perubahan arsitektur berskala besar, perombakan fitur mendasar, atau perubahan antarmuka yang tidak kompatibel ke belakang (*breaking changes*).
- **Angka Kedua (Minor Version)**: Menandakan penambahan fitur atau fungsionalitas baru yang tetap menjaga kompatibilitas ke belakang (*backward-compatible*).
- **Angka Ketiga (Patch Version)**: Menandakan perbaikan cacat (*bug fixes*) atau penambalan celah keamanan internal tanpa mengubah antarmuka fungsional.
- **Angka Keempat (Build Number / Build Date)**: Pengidentifikasi kompilasi internal atau tanggal pembangunan paket perangkat lunak untuk keperluan pelacakan teknis.

---

## 3. Software Testing: Categories and Levels

Pengujian perangkat lunak adalah praktik penjaminan mutu terpadu di sepanjang siklus pengembangan untuk memverifikasi kesesuaian sistem terhadap kebutuhan dan menjamin ketiadaan galat fungsional maupun struktural.

### A. Anatomi Kasus Uji (Test Case Anatomy)
Kasus uji dirumuskan secara formal setelah spesifikasi kebutuhan selesai dianalisis, memuat:
- Langkah-langkah eksekusi yang runtut (*execution steps*).
- Kondisi prasyarat dan masukan data (*inputs and test data*).
- Luaran atau perilaku yang diharapkan (*expected outputs*).

### B. Tiga Kategori Utama Pengujian Perangkat Lunak
Pengujian dikelompokkan berdasarkan fokus pengujian yang dilakukan:
- **Pengujian Fungsional (*Functional Testing*)**:
  - Menerapkan pendekatan kotak hitam (*black-box testing*), yaitu memverifikasi perilaku sistem tanpa memeriksa struktur internal baris kode sumber.
  - Memvalidasi apakah sistem yang diuji (*System Under Test / SUT*) menghasilkan luaran yang benar berdasarkan masukan yang diberikan.
  - Memastikan sistem mampu menangani kondisi batas (*edge cases*) dan kesalahan pengguna dengan menampilkan pesan kesalahan yang tepat (*graceful error handling*).
- **Pengujian Non-Fungsional (*Non-Functional Testing*)**:
  - Memeriksa atribut kualitas operasional dan ketahanan sistem.
  - Menguji kinerja (*performance*), waktu respons di bawah beban padat (*stress/load testing*), skalabilitas penambahan pengguna (*scalability*), ketersediaan layanan (*availability*), pemulihan bencana (*disaster recovery*), kekebalan celah keamanan (*security*), serta konsistensi perilaku lintas sistem operasi.
- **Pengujian Regresi (*Regression Testing / Maintenance Testing*)**:
  - Memverifikasi bahwa modifikasi kode terkini (seperti perbaikan *bug* atau penambahan fitur baru) tidak merusak fungsi-fungsi lama yang sebelumnya telah berjalan stabil.
  - Kriteria penentuan prioritas kasus uji regresi mencakup modul dengan frekuensi cacat tinggi, fungsi yang paling sering diakses pengguna, komponen yang baru mengalami perubahan signifikan, serta kasus uji yang rumit atau rentan tidak konsisten (*flaky tests*).

### C. Empat Tingkatan Pengujian Standar (Testing Levels)
Empat tingkatan pengujian diterapkan pada tahapan berbeda dalam SDLC untuk mencegah tumpang tindih verifikasi:
- **Pengujian Unit (*Unit Testing*)**:
  - Menguji fungsionalitas komponen kode terkecil yang dapat diisolasi (fungsi, metode, atau kelas).
  - Dieksekusi langsung oleh pengembang selama fase penulisan kode untuk mengeliminasi kesalahan konstruksi logika sedini mungkin.
- **Pengujian Integrasi (*Integration Testing*)**:
  - Menguji interaksi dan pertukaran data saat dua atau lebih unit modul independen digabungkan.
  - Mengungkap kesalahan protokol komunikasi antar-antarmuka, ketidaksesuaian logika dependensi modul, interaksi dengan basis data, atau integrasi perangkat keras eksternal.
- **Pengujian Sistem (*System Testing*)**:
  - Menguji keseluruhan sistem yang telah terintegrasi penuh di dalam lingkungan pementasan (*staging environment*) yang menyerupai lingkungan produksi.
  - Memvalidasi kepatuhan produk utuh terhadap seluruh spesifikasi fungsional dan non-fungsional.
- **Pengujian Penerimaan (*Acceptance Testing / UAT*)**:
  - Pengujian formal terhadap proses bisnis dan kebutuhan nyata pengguna akhir.
  - Dilakukan langsung oleh pelanggan atau pemangku kepentingan untuk memutuskan apakah perangkat lunak layak diterima dan disebarkan ke lingkungan produksi.

---

## 4. Software Documentation and Standard Operating Procedures (SOP)

Dokumentasi adalah aset rekayasa fundamental yang mendeskripsikan hakikat produk, arsitektur teknis, dan tata cara penggunaannya di sepanjang fase SDLC.

### A. Format dan Klasifikasi Dokumentasi
Dokumentasi disajikan dalam tiga format utama: teks tertulis (*written*), panduan video (*video*), atau aset visual/grafis (*graphical diagrams*). Dokumen dibagi menjadi dua kategori besar:
- **Dokumentasi Produk (*Product Documentation*)**: Menjelaskan fungsionalitas, arsitektur, dan perilaku sistem perangkat lunak yang dibangun.
- **Dokumentasi Proses (*Process Documentation*)**: Menjelaskan metode, alur kerja, dan persyaratan kualitas yang harus diikuti tim dalam melaksanakan suatu proses rekayasa atau bisnis.

### B. Lima Jenis Dokumentasi Produk
Dokumentasi produk mencakup seluruh spektrum siklus hidup perangkat lunak:
- **Dokumentasi Kebutuhan (*Requirements Documentation*)**: Disusun pada fase perencanaan, memuat spesifikasi SRS, URS, dan kriteria penerimaan bagi arsitek, pengembang, dan tim QA.
- **Dokumentasi Desain (*Design Documentation*)**: Disusun oleh arsitek perangkat lunak dan teknisi senior, memuat desain konseptual, diagram arsitektur tingkat tinggi, dan spesifikasi teknis (SDD).
- **Dokumentasi Teknis (*Technical Documentation*)**: Komentar di dalam baris kode program (*inline comments*), dokumentasi API, kertas kerja teknis (*working papers*), serta catatan keputusan arsitektur tim pengembang.
- **Dokumentasi Jaminan Kualitas (*Quality Assurance Documentation*)**: Strategi pengujian, rencana uji (*test plans*), data uji, skenario uji, serta matriks ketertelusuran (*traceability matrices*) yang memetakan korelasi antara kasus uji dengan kebutuhan bisnis.
- **Dokumentasi Pengguna Akhir (*User Documentation*)**: Ditujukan untuk memandu pengguna non-teknis, mencakup buku panduan instalasi, manual operasional sistem, dokumen tanya-jawab (FAQ), dan tutorial alur kerja.

### C. Prosedur Operasi Standar (Standard Operating Procedures / SOP)
SOP adalah penjabaran terperinci dari dokumentasi proses yang mengatur tata cara penyelesaian tugas teknis spesifik di suatu organisasi:
- Menyajikan instruksi langkah demi langkah yang terperinci untuk tugas umum namun kompleks (misalnya alur pemeriksaan kode, pengujian otomatis, dan tata tertib penggabungan kode ke cabang utama / *main branch* pada repositori Git).
- Format penyajian SOP dapat berupa diagram alir (*flowchart*), bagan kerangka hierarkis (*hierarchical outline*), atau daftar instruksi sekuensial langkah demi langkah.
- Seluruh dokumentasi harus dirawat dan diperbarui secara berkala pada fase pemeliharaan (*maintenance phase*) setiap kali terjadi perubahan antarmuka atau logika sistem.

---

## 5. Roles in Software Engineering Projects

Struktur proyek rekayasa perangkat lunak melibatkan beragam peran profesional dengan batas tanggung jawab yang saling melengkapi.

### A. Penjabaran Peran Profesional
Setiap anggota tim mengawal aspek keberhasilan proyek yang berbeda:
- **Project Manager vs Scrum Master**:
  - *Project Manager* (metode Waterfall): Berfokus pada perencanaan makro, penyusunan jadwal, pengendalian anggaran biaya, dan alokasi sumber daya manusia.
  - *Scrum Master* (metode Agile): Berfokus pada keberhasilan individu dan tim, memfasilitasi komunikasi harian, melindungi tim dari gangguan eksternal, dan menyingkirkan hambatan (*impediments*).
- **Pemangku Kepentingan (*Stakeholders*)**: Klien, pengguna akhir, dan pengambil keputusan bisnis yang mendefinisikan kebutuhan sistem, memberikan klarifikasi arah produk, serta menguji penerimaan produk akhir.
- **Arsitek Sistem / Perangkat Lunak (*System / Software Architect*)**: Merancang struktur internal fundamental, menetapkan pola desain (*design patterns*), mengawal batas modul, dan memberikan panduan teknis lintas fase SDLC.
- **Perancang Pengalaman Pengguna (*UX Designer*)**: Menyeimbangkan antara kemudahan interaksi antarmuka pengguna yang intuitif dengan ketahanan fungsi teknis, serta merancang tata letak dan alur navigasi pengguna.
- **Pengembang Perangkat Lunak (*Software Developer*)**: Menerjemahkan rancangan desain arsitektur, kebutuhan fungsional SRS, dan spesifikasi antarmuka UX ke dalam baris kode program yang dapat dieksekusi.
- **Penguji / Rekayasawan Kualitas (*Tester / QA Engineer*)**: Merancang dan mengeksekusi skenario kasus uji, mendeteksi cacat fungsional maupun non-fungsional, serta memberikan laporan umpan balik kualitas secara berkala.
- **Rekayasawan Keandalan Situs / Operasi (*Site Reliability Engineer / SRE / Ops Engineer*)**: Menjembatani pengembangan dengan operasional infrastruktur, mengelola otomatisasi pipa penerapan (*CI/CD*), memantau insiden peladen, dan menjamin keandalan sistem produksi.
- **Manajer Produk / Pemilik Produk (*Product Manager / Product Owner*)**: Memegang visi tunggal produk, memahami kebutuhan mendalam dari pengguna dan pasar, serta memprioritaskan fitur kerja demi memaksimalkan nilai bisnis.
- **Penulis Teknis (*Technical Writer / Information Developer*)**: Menyusun materi dokumentasi teknis ke dalam bahasa yang mudah dipahami oleh pengguna non-teknis melalui panduan manual, buku petunjuk, dan laporan teknis.

---

## 6. Insiders' Viewpoint: Real-World Team Collaboration

Pengalaman praktisi industri menegaskan bahwa rekayasa perangkat lunak modern adalah kerja tim yang sangat kolaboratif dan terintegrasi secara lintas fungsi (*cross-functional*).

### A. Dinamika Kolaborasi Lintas Peran
Dalam tim rekayasa terpadu, sekat pemisah antardepartemen dihapuskan:
- **Kolaborasi Pengembang dan Manajer Produk**: Pengembang berkoordinasi intensif dengan Product Manager atau Scrum Master melalui pertemuan harian (*daily stand-ups*) dan pelacak tiket kerja (seperti Jira) untuk memastikan ritme kerja tetap pada jalurnya dan hambatan kerja dapat segera diselesaikan.
- **Kolaborasi Pengembang dan Desainer UX**: Hubungan kerja berjalan sejak tahap curah gagasan di papan tulis hingga penerjemahan purwarupa antarmuka presisi tinggi dari alat desain (seperti Figma) ke dalam kode tampilan.
- **Siklus Kemitraan Pengembang dan QA**: Setelah kode selesai ditulis dan ditinjau oleh pimpinan teknis (*tech lead*), kode diuji oleh QA Engineer. Jika ditemukan cacat, penguji menyusun dokumen pengujian terperinci agar pengembang dapat segera memperbaikinya sebelum dilakukan uji ulang.
- **Integrasi dengan SRE dan Pengujian Otomatis**: Pengembang bekerja bersama teknisi SRE untuk memastikan kode dapat berjalan stabil di lingkungan peladen awan serta terintegrasi mulus dalam pipa integrasi berkelanjutan.
- **Prinsip Kerja Rekayasa**: Seorang rekayasawan perangkat lunak tidak pernah bekerja terisolasi; keberhasilan hantaran sistem ditentukan oleh keterbukaan komunikasi dan keselarasan visi di antara seluruh anggota tim.

---

## 7. Summary and Key Takeaways

Pemahaman menyeluruh terhadap proses pembangunan perangkat lunak menjadi landasan profesionalisme rekayasa:
- Tiga metodologi pengembangan perangkat lunak menawarkan karakteristik unik: Waterfall bersifat linier dan kaku, V-Shape menekankan perancangan uji dini yang simetris, sedangkan Agile mengutamakan kolaborasi iteratif dan kemampuan adaptasi terhadap perubahan.
- Penomoran versi perangkat lunak (*SemVer*) memberikan kejelasan evolusi kode melalui tiga tingkatan utama: *Major* (perubahan mendasar/inkompatibel), *Minor* (penambahan fitur kompatibel), dan *Patch* (perbaikan bug).
- Pengujian perangkat lunak mencakup tiga kategori (fungsional, non-fungsional, regresi) yang dieksekusi melintasi empat tingkatan berjenjang (*Unit*, *Integration*, *System*, dan *Acceptance Testing*).
- Dokumentasi produk dan proses (termasuk SOP) adalah pilar penjamin keberlanjutan sistem yang harus diperbarui secara konsisten pada fase pemeliharaan.
- Keberhasilan proyek perangkat lunak merupakan hasil simfoni kolaboratif antarperan multidisiplin (PM/Scrum Master, Arsitek, UX, Pengembang, QA, SRE, PO, dan Penulis Teknis) yang bekerja bersama dalam satu tim yang erat.
