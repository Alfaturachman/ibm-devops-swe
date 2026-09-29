# Tools and Technologies in Software Development

Dokumen ini menyajikan panduan mendalam mengenai ekosistem peralatan pengembangan perangkat lunak modern, mencakup sistem kendali versi (*version control*), pustaka (*libraries*), kerangka kerja (*frameworks*) beserta prinsip pembalikan kendali (*inversion of control*), otomatisasi *CI/CD*, alat bantu *build*, manajemen paket lintas platform dan bahasa pemrograman, taksonomi tumpukan perangkat lunak (*software stacks* seperti LAMP, MEAN, MEVN, MERN, Django, ASP.NET), hingga wawasan praktisi industri mengenai standar rekayasa perangkat lunak kontemporer.

---

## 1. Introducing Application Development Tools

Mewujudkan aplikasi dari tahap pencetusan ide hingga siap dioperasikan di lingkungan produksi merupakan proses panjang yang mengandalkan integrasi perkakas kerja terstandarisasi. Meja kerja pengembang (*developer's workbench*) bertumpu pada tiga instrumen utama: sistem kendali versi, pustaka kode, dan kerangka kerja perangkat lunak.

### A. Sistem Kendali Versi (Version Control Systems / VCS)
Dalam proyek rekayasa perangkat lunak modern di mana banyak pengembang bekerja pada basis kode yang sama secara simultan, pencatatan urutan perubahan kode sumber menjadi hal yang mutlak:
- **Fungsi Utama VCS**:
  - Melacak setiap riwayat modifikasi kode secara terperinci (siapa yang mengubah, kapan perubahan dilakukan, dan apa alasan perubahan tersebut).
  - Menyediakan mekanisme resolusi konflik (*conflict resolution*) secara sistematis ketika dua pengembang memodifikasi bagian kode yang sama.
- **Nilai Penting bagi Pengembang Tunggal (*Sole Contributor*)**:
  - Menyediakan riwayat evolusi kode yang terdokumentasi rapi.
  - Memberikan jaring pengaman untuk mengembalikan (*revert*) kondisi kode ke versi stabil sebelumnya apabila terjadi kesalahan fatal atau regresi fitur.
- **Repositori Kode (*Code Repositories*)**:
  - Fungsionalitas kendali versi terikat erat dengan sistem penyimpanan kode.
  - Git merupakan sistem kendali versi terdistribusi standar industri yang paling populer, sedangkan GitHub menyediakan platform berbasis awan untuk penyimpanan repositori, kolaborasi tim, dan pelacakan isu.
- **Percabangan (*Branching*) dan Penggabungan (*Merging*)**:
  - Fitur percabangan (*feature branches*) memungkinkan pengembang mengisolasi pengerjaan modul baru tanpa mengganggu stabilitas kode pada cabang utama (*main branch*).
  - Setelah kode teruji, cabang fitur digabungkan kembali (*merge*) ke cabang utama melalui mekanisme peninjauan kode (*pull request*).

### B. Pustaka Kode (Code Libraries)
Pustaka kode adalah sekumpulan kode program standar, modul, dan subrutin teruji yang dapat disematkan ke dalam aplikasi guna memecahkan masalah spesifik atau menambahkan fitur tertentu:
- **Karakteristik Kendali (*Developer in Control*)**:
  - Pengembang memegang kendali penuh atas alur jalannya program (*program flow*).
  - Pengembang secara aktif memanggil metode atau fungsi pustaka saat diperlukan, dan setelah subrutin selesai dieksekusi, kendali dikembalikan sepenuhnya ke alur program utama.
- **Manfaat Pemanfaatan Pustaka**:
  - Penggunaan kembali kode (*code reuse*) menghemat waktu dan tenaga secara signifikan, menghindarkan pengembang dari keharusan membuat modul umum dari nol (misalnya modul tampilan karusel visual atau validasi data).
- **Contoh Pustaka Populer**:
  - *jQuery*: Pustaka JavaScript legendaris yang menyederhanakan manipulasi hierarki DOM (*Document Object Model*), penanganan peristiwa (*event handling*), dan pemanggilan AJAX.
  - *EmailValidator*: Pustaka utilitas terfokus untuk memeriksa keabsahan struktur dan sintaks format alamat surel.
  - *Apache Commons Proper*: Repositori komponen Java sumber terbuka yang dapat digunakan kembali untuk menangani manipulasi berkas, konfigurasi matematika, dan pemrosesan string.

### C. Kerangka Kerja Perangkat Lunak (Software Frameworks)
Kerangka kerja menyediakan kerangka arsitektur terstandarisasi (*scaffold* atau *skeleton*) yang menjadi landasan utama bagi pengembang dalam membangun dan menyebarkan aplikasi:
- **Karakteristik Struktural**:
  - Kerangka kerja harus dipilih dan ditetapkan sejak fase perencanaan awal proyek. Kerangka kerja mendikte arsitektur keseluruhan aplikasi sehingga mustahil menyisipkan kerangka kerja baru ke dalam proyek yang sudah berjalan tanpa perombakan total.
- **Pembalikan Kendali (*Inversion of Control / IoC*)**:
  - Berbeda secara mendasar dari pustaka, pada kerangka kerja terjadi pembalikan kendali: kerangka kerja yang mendikte alur program dan memanggil kode yang ditulis pengembang (*the framework calls on your code*).
  - Mengikuti prinsip arsitektur *"Don't call us, we'll call you"*: pengembang mengisi titik-titik ekstensi (*extension points*) yang disediakan, sementara kerangka kerja menentukan kapan dan bagaimana fungsi tersebut dieksekusi.
- **Sifat Berpendirian Kuat (*Opinionated Frameworks*)**:
  - Sebagian besar kerangka kerja memiliki konvensi ketat (*opinionated*) mengenai tata cara penulisan kode, penamaan berkas, struktur direktori proyek, hingga mekanisme interaksi data.
  - Meskipun mengurangi fleksibilitas bebas pengembang, pendekatan ini mengeliminasi beban pengambilan keputusan mikro yang melelahkan (*configuration fatigue*), menjamin standarisasi struktur kode di seluruh tim, dan mengoptimalkan efisiensi rekayasa.
- **Contoh Kerangka Kerja Utama**:
  - *Angular*: Kerangka kerja berbasis TypeScript/JavaScript dari Google untuk membangun aplikasi web dinamis berskala besar.
  - *Vue.js*: Kerangka kerja JavaScript adaptif yang berfokus pada kemudahan pengembangan antarmuka pengguna.
  - *Django*: Kerangka kerja tingkat tinggi berbasis Python yang menerapkan pola arsitektur MVT (*Model-View-Template*) untuk pengembangan aplikasi web yang cepat, aman, dan terstruktur.

---

## 2. Build Tools, CI/CD, and Package Management

Setelah kode program ditulis, serangkaian alat bantu otomatisasi diperlukan untuk mengompilasi, menguji, mengemas, dan mendistribusikan perangkat lunak ke lingkungan produksi secara konsisten.

### A. Praktik Integrasi dan Pengiriman Berkelanjutan (CI/CD)
CI/CD merupakan pilar fundamental dalam budaya DevOps yang memungkinkan tim rekayasa merilis pembaruan perangkat lunak secara cepat, terukur, dan aman:
- **Integrasi Berkelanjutan (*Continuous Integration / CI*)**:
  - Praktik penggabungan perubahan kode dari seluruh pengembang ke dalam repositori utama secara sering, minimal sekali sehari atau bahkan beberapa kali dalam sehari.
  - Diimplementasikan melalui peladen otomatisasi bangun (*build-automation server*) yang secara otomatis mengambil kode terbaru, mengompilasi proyek, dan menjalankan seluruh skenario pengujian otomatis.
  - Memastikan seluruh modul yang dibuat oleh berbagai pengembang terbukti bekerja selaras (*mutually compatible*) serta mendeteksi regresi atau kerusakan kode sedini mungkin.
- **Pengiriman dan Penerapan Berkelanjutan (*Continuous Delivery and Deployment / CD*)**:
  - *Continuous Delivery (CD)*: Tahapan otomatisasi lanjutan di mana kode yang telah lolos uji pada fase CI secara otomatis dibangun menjadi artefak rilis dan disebarkan ke lingkungan pengujian (*testing/staging environment*), siap untuk dirilis ke lingkungan produksi kapan saja dengan persetujuan manual.
  - *Continuous Deployment (CD)*: Otomatisasi penuh tanpa intervensi manual; setiap perubahan kode yang berhasil melewati seluruh tahapan pengujian dan verifikasi akan langsung diterapkan ke lingkungan produksi (*live production*) yang diakses pengguna akhir.

### B. Alat Bantu Bangun dan Otomatisasi (Build Tools and Automation)
Alat bantu bangun mentransformasikan berkas kode sumber mentah (*source code*) menjadi berkas biner atau artefak eksekusi yang siap dijalankan dan diinstal:
- **Tanggung Jawab Alat Bangun**:
  - Mengelola bendera kompilasi (*compile flags*) dan urutan ketergantungan modul.
  - Mengotomatisasi siklus kerja harian pengembang yang berulang: mengunduh dependensi pihak ketiga, mengompilasi kode sumber menjadi bahasa mesin/biner, mengemas berkas artefak, menjalankan rangkaian pengujian (*unit/integration tests*), hingga melakukan penyebaran ke peladen.
- **Dua Kategori Alat Bangun**:
  - *Utilitas Otomatisasi Bangun (Build-Automation Utilities)*: Perangkat lunak yang mengeksekusi proses kompilasi, transpiler, pembungkusan (*bundling*), dan penautan (*linking*) kode sumber menjadi artefak biner. Contohnya:
    - *Webpack*: Pembungkus modul (*module bundler*) untuk ekosistem JavaScript modern.
    - *Babel*: Kompiler/transpiler yang mengubah kode JavaScript versi mutakhir (ES6+) menjadi versi kompatibel ke belakang agar dapat berjalan di seluruh peramban web lama.
    - *WebAssembly (Wasm)*: Format instruksi biner tingkat rendah yang dirancang untuk dieksekusi dengan kecepatan mendekati perangkat keras (*near-native speed*) di dalam peramban web modern.
  - *Peladen Otomatisasi Bangun (Build-Automation Servers)*: Infrastruktur terpusat yang mengoordinasikan eksekusi utilitas bangun secara terjadwal atau terpicu oleh peristiwa repositori (*webhook triggers*), seperti Jenkins atau GitHub Actions.

### C. Manajemen Paket (Packages and Package Managers)
Untuk mendistribusikan perangkat lunak atau menggunakan pustaka pihak ketiga secara efisien, pengembang mengandalkan format paket dan manajer paket:
- **Konsep Paket (*Packages*)**:
  - Berkas arsip terkompresi yang membundel seluruh berkas program, skrip instalasi, dan berkas metadata.
  - Metadata memuat informasi esensial mencakup deskripsi paket, nomor versi, pengenal pembuat, serta daftar dependensi prasyarat yang wajib terpasang sebelumnya.
- **Fungsi Manajer Paket (*Package Managers*)**:
  - Mengotomatisasi penemuan (*discovery*), pengunduhan, dan pemasangan paket dari repositori publik atau privat.
  - Memverifikasi integritas dan keaslian paket menggunakan kode pengecekan (*checksum verification*) dan sertifikat digital.
  - Menyelesaikan pohon dependensi bertingkat (*recursive dependency resolution*) agar seluruh pustaka yang dibutuhkan tersedia tanpa konflik versi.
  - Mempermudah pembaruan (*upgrade*) serta penghapusan (*uninstall*) paket dari sistem secara bersih.
- **Manajer Paket Tingkat Sistem Operasi**:
  - *Linux*: Debian Package Management System (*DPKG* / berkas `.deb`) dan Red Hat Package Manager (*RPM* / berkas `.rpm`).
  - *Windows*: Chocolatey.
  - *macOS*: Homebrew dan MacPorts.
  - *Android*: Android Package Manager (mengelola berkas `.apk`).
- **Manajer Paket Tingkat Bahasa Pemrograman**:
  - *JavaScript / Node.js*: npm (*Node Package Manager*).
  - *Java*: Gradle dan Apache Maven.
  - *Ruby*: RubyGems.
  - *Python*: Pip dan Conda.

---

## 3. Introduction to Software Stacks

Aplikasi modern jarang dibangun hanya dengan satu teknologi tunggal; aplikasi merupakan hasil integrasi harmonis dari berbagai lapisan perangkat lunak dan infrastruktur yang bekerja sama.

### A. Terminologi dan Konsep Dasar
- **Tumpukan Perangkat Lunak (*Software Stack*)**:
  - Kombinasi berjenjang dari berbagai teknologi perangkat lunak dan bahasa pemrograman yang disusun secara hierarkis untuk mendukung eksekusi aplikasi (misalnya aplikasi web atau aplikasi seluler).
  - Lapisan teratas dalam hierarki melayani tugas langsung dan antarmuka pengguna, sedangkan lapisan terbawah berinteraksi langsung dengan perangkat keras komputer.
- **Perbedaan Istilah: Software Stack vs Technology Stack**:
  - *Software Stack*: Berfokus murni pada lapisan perangkat lunak aplikasi (antarmuka, pustaka, kerangka kerja aplikasi, peladen web, dan basis data).
  - *Technology Stack*: Istilah dengan cakupan lebih luas yang memadukan tumpukan perangkat lunak dengan infrastruktur perangkat keras dan virtualisasi pendukung, seperti mesin virtual (*virtual machines*), kontainer (*Docker/Kubernetes*), penyimpanan awan (*cloud storage*), dan penyeimbang beban (*load balancers*).
- **Prinsip Modularitas**: Tidak ada aturan kaku mengenai jumlah lapisan dalam tumpukan; pengembang hanya menggunakan lapisan-lapisan yang relevan dengan kebutuhan solusi yang dibangun.

### B. Tiga Lapisan Arsitektur Fundamental
Implementasi tumpukan perangkat lunak paling sederhana terdiri dari tiga lapisan utama (*three-tier architecture*):
- **1. Lapisan Presentasi (*Presentation Layer*)**:
  - Sisi antarmuka pengguna (*front-end*) yang memvisualisasikan data dan menangkap input interaksi pengguna.
- **2. Lapisan Logika Bisnis (*Business Logic Layer*)**:
  - Sisi peladen (*back-end*) yang memproses kalkulasi, menegakkan aturan operasional bisnis, dan memvalidasi alur data.
- **3. Lapisan Data (*Data Layer*)**:
  - Sistem persistensi yang menyimpan, mengelola, dan mengamankan data transaksi (melalui basis data relasional atau NoSQL).
- **Lapisan Lanjutan pada Sistem Kompleks**: Menambahkan lapisan virtualisasi, penjadwalan dan orkestrasi (*scheduling and orchestration*), lingkungan waktu proses (*runtime*), konektivitas basis data, jaringan terdistribusi, serta lapisan keamanan enkripsi.

### C. Taksonomi Tumpukan Perangkat Lunak Populer
- **Tumpukan Python Django**:
  - Mengombinasikan bahasa pemrograman Python dengan kerangka kerja Django.
  - Sepenuhnya berbasis sumber terbuka, sangat andal untuk membangun aplikasi web berskala besar yang menuntut laju perubahan fitur secara cepat (*fast-changing web applications*).
- **Tumpukan Ruby on Rails**:
  - Mengombinasikan bahasa pemrograman Ruby dengan kerangka kerja Rails di sisi peladen.
  - Sangat tangguh dalam menangani pertukaran data berformat JSON atau XML, serta terintegrasi mulus dengan HTML, CSS, dan JavaScript di sisi antarmuka.
- **Tumpukan ASP.NET**:
  - Ekosistem korporat berbasis teknologi Microsoft: kerangka kerja ASP.NET MVC, peladen web IIS (*Internet Information Services*), basis data Microsoft SQL Server, dan layanan komputasi awan Microsoft Azure.
- **Tumpukan LAMP**:
  - Salah satu tumpukan generasi awal (*early incarnation*) yang menjadi standar emas pembangunan situs web dan aplikasi awan.
  - Komposisi: Sistem operasi *Linux*, peladen web *Apache HTTP*, basis data relasional *MySQL*, dan bahasa skrip *PHP* (dapat pula menggunakan Perl atau Python).
  - Bersifat sumber terbuka dan memiliki keterikatan longgar (*loosely coupled*), sehingga komponennya mudah diganti (misalnya mengganti MySQL dengan PostgreSQL sehingga berubah menjadi tumpukan *LAPP*).
- **Keluarga Tumpukan Berbasis JavaScript Penuh (Full-Stack JavaScript)**:
  - Menggunakan JavaScript sebagai bahasa tunggal di seluruh lapisan dari antarmuka hingga peladen:
    - *Tumpukan MEAN*: Mengombinasikan basis data dokumen *MongoDB*, kerangka kerja peladen *Express.js*, kerangka kerja antarmuka *Angular*, dan lingkungan waktu proses *Node.js*. Bersifat independen terhadap sistem operasi (*platform-agnostic*), gratis, dan sumber terbuka.
    - *Tumpukan MERN*: Mengganti Angular dengan pustaka antarmuka *React.js*, menghadirkan fleksibilitas tinggi dan arsitektur berbasis komponen modular.
    - *Tumpukan MEVN*: Mengganti Angular dengan kerangka kerja *Vue.js*, menawarkan bobot yang lebih ringan, implementasi cepat, dan performa tinggi.

### D. Analisis Komparatif: Keunggulan dan Tantangan (MEAN vs MEVN vs LAMP)
Setiap tumpukan memiliki karakteristik performa dan kompromi arsitektural yang berbeda:
- **Tumpukan MEAN**:
  - *Keunggulan*: Seluruh lapisan menggunakan bahasa tunggal (JavaScript) sehingga pengembang tidak perlu mempelajari banyak sintaks bahasa; hemat biaya karena sepenuhnya sumber terbuka; pengembangan berlangsung sangat cepat berkat ketersediaan jutaan pustaka modular siap pakai di repositori npm.
  - *Tantangan*: Kurang optimal untuk aplikasi skala masif tertentu; logika bisnis yang terkonsentrasi pada peladen Express.js dapat membatasi penggunaan kembali layanan tertentu (seperti operasi pemrosesan tumpak / *batching operations*); MongoDB sangat unggul untuk data tidak terstruktur (*unstructured data*), namun tidak menyediakan kapabilitas integritas relasional sekuat basis data SQL tradisional.
- **Tumpukan MEVN**:
  - *Keunggulan*: Menikmati seluruh manfaat tumpukan JavaScript terpadu seperti MEAN; Vue.js memiliki bobot yang lebih ringan dan kurva pembelajaran yang lebih ramah sehingga mampu memberikan performa antarmuka yang sangat responsif.
  - *Tantangan*: Ekosistem pustaka dan komponen siap pakai Vue.js masih lebih sedikit dibandingkan ekosistem Angular yang telah matang.
- **Tumpukan LAMP**:
  - *Keunggulan*: Merupakan salah satu tumpukan paling matang di dunia teknologi; ketersediaan dokumentasi, panduan pemecahan masalah, dan dukungan komunitas sangat melimpah; basis data MySQL memberikan jaminan integritas relasional yang teruji untuk transaksi data terstruktur.
  - *Tantangan*: Keterikatan erat dengan sistem operasi Linux membuatnya kurang fleksibel dibandingkan tumpukan MEAN/MEVN yang bebas platform; MySQL kurang cocok menangani lonjakan data tanpa struktur; terjadi hambatan peralihan konteks (*context switching*) bagi pengembang karena sisi peladen dijalankan dengan PHP/Python sementara sisi antarmuka menggunakan JavaScript dan HTML.

---

## 4. Insiders' Viewpoint: Tools and Technologies

Praktisi dan insinyur perangkat lunak industri membagikan pengalaman nyata mengenai instrumen kerja yang menjadi standar emas dalam proyek rekayasa modern.

### A. Penggunaan Rutin Git dan GitHub dalam Kolaborasi Industri
- **Peralatan Harian Tanpa Henti**: Tim rekayasa mengandalkan Git dan GitHub setiap hari untuk pelacakan kode sumber, kolaborasi lintas anggota, penelusuran kutu program (*bug tracking*), serta manajemen tugas dan fitur.
- **Standar Baku Perangkat Lunak Terbuka dan Tertutup**: Mayoritas proyek perangkat lunak di dunia saat ini telah terstandarisasi menggunakan Git.
- **Kekuatan Fitur Kolaboratif**: Nilai sejati Git paling terasa saat bekerja dalam tim multi-pengembang melalui pemanfaatan percabangan fitur (*feature branches*) dan permintaan penarikan (*pull requests*).
- **Manfaat bagi Pengembang Tunggal**: Tetap sangat direkomendasikan bagi pengembang solo karena menyediakan rekam jejak versi yang aman dan membuka akses ke komunitas pengembang global di GitHub.

### B. Ekosistem Perkakas Antarmuka (Front-End Tools)
- **Fondasi Tiga Pilar**: Pembangunan antarmuka berpusat pada HTML, CSS, dan JavaScript.
- **Pemilihan Editor dan IDE**:
  - Menggunakan editor terfokus antarmuka seperti *Brackets*, atau editor serbaguna standar industri seperti *Visual Studio Code (VS Code)*.
- **Otomatisasi Linting dan Pemformatan Kode**:
  - Pemasangan ekstensi IDE untuk pemformatan kode otomatis (*Prettier*) dan analisis kode statis (*ESLint*).
  - Menangkap potensi galat, inkonsistensi penulisan, dan kesalahan ruang lingkup (*scoping*) sedini mungkin sebelum kode dijalankan.

### C. Lanskap Pustaka dan Kerangka Kerja Antarmuka
- **React.js**:
  - Sangat populer di kalangan praktisi industri karena menerapkan arsitektur berorientasi komponen (*component-driven architecture*).
  - Menyediakan konsep status internal (*state*) dan properti (*props*) yang membuat pengelolaan aliran data aplikasi menjadi terstruktur dan mudah diprediksi.
  - Menggunakan ekstensi sintaks *JSX (JavaScript XML)* yang memungkinkan penulisan struktur antarmuka langsung di dalam logika JavaScript, menghasilkan pesan peringatan dan galat yang jauh lebih deskriptif.
  - Mengeliminasi inkonsistensi rendering antar peramban (*cross-browser issues*) dan memiliki kurva pembelajaran yang relatif ramah bagi tim baru.
- **Angular**:
  - Kerangka kerja komprehensif dari Google yang dirancang khusus untuk memfasilitasi arsitektur aplikasi satu halaman (*Single Page Applications / SPA*) berskala korporat.
- **Pustaka Pendukung dan Warisan Sejarah**:
  - *jQuery*: Diciptakan oleh John Resig pada tahun 2006, merupakan pustaka JavaScript paling berpengaruh dalam sejarah web yang masih kerap digunakan berdampingan dengan React dan Angular.
  - *Backbone.js*: Pustaka ringan yang memberikan struktur model-tampilan pada aplikasi berbasis JavaScript.

### D. Lanskap dan Optimasi Sisi Peladen (Back-End Technologies)
- **Node.js**:
  - Platform sisi peladen sumber terbuka yang dibangun di atas mesin JavaScript *Google Chrome V8*.
  - Menggunakan arsitektur asinkron berbasis utas tunggal (*asynchronous single-threaded architecture*) yang digerakkan oleh gelung peristiwa (*event loop*).
  - Mampu menangani lonjakan koneksi konkuren dalam jumlah masif dengan penggunaan memori yang sangat efisien.
- **Express.js**:
  - Kerangka kerja minimalis dan tangguh untuk Node.js yang memungkinkan penskalaan aplikasi secara kilat.
  - Memungkinkan tim menggunakan satu bahasa terpadu (JavaScript) untuk lapisan antarmuka sekaligus peladen.
  - Dilengkapi dukungan fitur tembolok (*caching*) terintegrasi, mencegah eksekusi ulang fungsi-fungsi berat secara berulang sehingga mempercepat waktu pemuatan halaman web.
- **Kerangka Kerja Peladen Alternatif**:
  - *Flask*: Kerangka kerja mikro berbasis Python yang sangat disukai komunitas pengembang Python (*Pythonistas*) karena kesederhanaan dan fleksibilitasnya.
  - *Spring Framework*: Kerangka kerja enterprise berbasis Java yang telah teruji keandalannya selama bertahun-tahun dalam menangani arsitektur sistem berskala masif.
- **Pustaka Esensial Harian**:
  - *Axios*: Pustaka klien HTTP berbasis janji (*promise-based*) untuk melakukan permintaan data ke antarmuka layanan web (*web services*), mengonfigurasi header permintaan secara otomatis, serta menyediakan fungsi penanganan tanggapan yang bersih.
  - Driver Basis Data npm: Pustaka terstandarisasi untuk menghubungkan peladen dengan basis data relasional (SQL) maupun basis data non-relasional (NoSQL).

### E. Transformasi Kualitas Kode dengan Standar Modern JavaScript (ES6+)
Praktisi sangat menyarankan pengembang untuk mendalami fitur-fitur modern *ECMAScript 6 (ES6+)*:
- **Fungsi Panah (*Arrow Functions*)**: Menyediakan sintaks deklarasi fungsi yang lebih ringkas dan mengikat konteks leksikal `this` secara otomatis.
- **Operator Sebaran (*Spread / Rest Operator `...`*)**: Mempermudah manipulasi dan penggabungan struktur data larik (*array*) maupun objek secara elegan.
- **Dampak Kualitas Perangkat Lunak**: Menjadikan kode program lebih bersih, ringkas, mudah dipahami (*readable*), dan meminimalkan potensi kesalahan pemrograman yang tidak disengaja.