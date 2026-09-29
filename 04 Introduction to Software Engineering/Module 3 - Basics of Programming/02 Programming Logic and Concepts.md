# Programming Logic and Fundamental Concepts

Dokumen ini menyajikan panduan komprehensif mengenai logika dasar pemrograman dan konsep-konsep fundamental rekayasa perangkat lunak, mencakup logika percabangan (*branching*) dan perulangan (*looping*), evaluasi ekspresi Boolean, tipologi pengenal (*identifiers*) konstanta dan variabel, struktur penampung data (*arrays* dan *vectors*), arsitektur fungsi modular, hingga prinsip enkapsulasi objek dalam Pemrograman Berorientasi Objek (*Object-Oriented Programming / OOP*).

---

## 1. Branching and Looping Programming Logic

Sebuah program komputer pada dasarnya tersusun atas dua pilar utama: instruksi yang memberitahukan komputer tindakan apa yang harus diambil, serta data yang dimanipulasi selama program berjalan. Seluruh alur eksekusi instruksi tersebut dikendalikan melalui dua ragam logika pemrograman primer: percabangan (*branching*) dan perulangan (*looping*).

### A. Fondasi Logika Pemrograman: Ekspresi Boolean dan Variabel
- **Ekspresi Boolean (*Boolean Expressions*)**:
  - Pernyataan logika pemrograman yang hanya menghasilkan dua kemungkinan nilai kebenaran: Benar (*True*) atau Salah (*False*).
  - Komputer mengandalkan logika Boolean untuk mengambil keputusan operasional: komputer akan menjalankan satu set tindakan jika suatu kondisi bernilai *True*, dan menjalankan set tindakan yang berbeda jika bernilai *False*.
- **Variabel (*Variables*)**:
  - Lokasi penyimpanan data bernama yang memiliki nilai dinamis yang dapat berubah sepanjang program berjalan.
  - Nilai variabel diteruskan ke dalam fungsi atau subrutin sebagai parameter masukan untuk memandu pengambilan keputusan logika.

### B. Logika Percabangan (Branching Logic)
Logika percabangan adalah mekanisme di mana program komputer memilih dan mengeksekusi jalur instruksi yang berbeda berdasarkan terpenuhi atau tidaknya suatu kriteria kondisi selama eksekusi program:
- **Konsep Jalur Eksekusi (*Code Pathways*)**:
  - Setiap kemungkinan keputusan menciptakan cabang kode (*branch*) baru.
  - Cabang kode yang dieksekusi sepenuhnya bergantung pada evaluasi parameter masukan, baik yang dimasukkan langsung oleh pengguna maupun hasil luaran dari prosedur sebelumnya.
  - Pengembang dapat merangkai cabang keputusan tanpa batas untuk mengimplementasikan logika bisnis yang sangat kompleks.
- **Konstruksi Pernyataan Percabangan Utama**:
  - *Pernyataan `if`*: Struktur pengambilan keputusan paling mendasar yang mengevaluasi kondisi Boolean; menjalankan blok kode tertentu hanya jika kondisi terpenuhi (*True*).
  - *Pernyataan `if-then-else` / `if-else`*: Memperluas pernyataan `if` dengan menyediakan tindakan alternatif melalui blok `else` apabila kondisi bernilai *False*. Pada konstruksi ini, salah satu dari blok kode (blok *True* atau blok *False*) dipastikan selalu dieksekusi.
  - *Pernyataan `switch`*: Mekanisme kendali seleksi berbasis pemetaan nilai (*search and map*); mencocokkan nilai variabel atau ekspresi terhadap daftar label kasus (*cases*) untuk mengalihkan alur program tanpa memerlukan rantai `if-else` bertingkat yang panjang.
  - *Pernyataan `GoTo`*: Perintah transfer alur kendali satu arah (*unconditional one-way jump*) ke baris kode tertentu. Berbeda dari pemanggilan fungsi yang selalu mengembalikan alur kendali ke titik pemanggil, `GoTo` memindahkan eksekusi secara permanen sehingga penggunaannya dalam rekayasa perangkat lunak modern sangat dibatasi guna mencegah timbulnya kode yang rumit dan tidak terstruktur (*spaghetti code*).

### C. Logika Perulangan (Looping Logic)
Perulangan adalah rangkaian instruksi yang dieksekusi secara berulang-ulang sampai suatu kondisi batas (*terminating condition*) tercapai:
- **Mekanisme Siklus Perulangan**:
  - Program melakukan suatu proses tertentu (seperti mengambil atau memodifikasi data), lalu memeriksa variabel penghitung (*counter*) atau kondisi penghenti.
  - Jika kondisi penghenti belum terpenuhi, alur eksekusi kembali ke instruksi awal dalam blok untuk mengulang proses.
  - Jika kondisi penghenti telah tercapai, alur program keluar (*break/fall through*) dari blok perulangan dan melanjutkan eksekusi ke instruksi sekuensial berikutnya.
- **Tiga Pernyataan Perulangan Mendasar**:
  - *Perulangan `While`*: Perulangan dengan kendali di awal (*entry-controlled loop*). Kondisi Boolean dievaluasi sebelum blok kode dijalankan. Tubuh perulangan hanya dieksekusi apabila kondisi bernilai *True*; jika sejak awal bernilai *False*, blok kode tidak akan pernah dijalankan sama sekali.
  - *Perulangan `For`*: Perulangan berbasis penghitung (*counter-driven loop*). Nilai awal penghitung diinisialisasi satu kali di awal, kemudian kondisi batas diuji pada setiap siklus iterasi. Setiap kali iterasi selesai, penghitung diperbarui (*increment/decrement*) hingga evaluasi kondisi menghasilkan nilai *False*.
  - *Perulangan `Do-While`*: Perulangan dengan kendali di akhir (*exit-controlled loop*). Kondisi Boolean baru dievaluasi setelah tubuh perulangan selesai dieksekusi. Karakteristik khas konstruksi ini menjamin bahwa tubuh perulangan dipastikan dieksekusi minimal satu kali, terlepas dari apakah kondisi bernilai benar atau salah.

### D. Perbedaan Hakiki Percabangan vs Perulangan
- **Percabangan (*Branching*)**: Berfokus pada keputusan memilih tindakan mana yang harus diambil (*deciding what actions to take*).
- **Perulangan (*Looping*)**: Berfokus pada keputusan menentukan berapa kali suatu tindakan harus diulang (*deciding how many times to perform a certain action*).

---

## 2. Identifiers and Data Containers

Dalam menulis kode program, pengembang memerlukan cara terstandarisasi untuk merujuk komponen kode, menyimpan nilai data, serta mengelola koleksi data berskala besar secara efisien.

### A. Peran Pengenal (Identifiers) dalam Pemrograman
Pengenal (*identifier*) adalah label nama kustom yang didefinisikan oleh pengembang untuk merujuk komponen tertentu di dalam program, seperti nilai data tersimpan, metode, antarmuka (*interface*), maupun kelas (*class*). Apabila pengenal digunakan untuk menampung data, pengenal tersebut diklasifikasikan ke dalam dua kelompok: konstanta atau variabel.

### B. Konstanta Bernama (Named Constants)
Konstanta adalah item data yang nilainya bersifat tetap dan tidak dapat dimodifikasi sepanjang siklus eksekusi program:
- **Pemberian Nilai dan Contoh**:
  - Nilai konstanta ditetapkan tepat saat konstanta tersebut didefinisikan.
  - Contoh konstanta numerik: nilai matematis pi (`3.14159`), tarif pajak tetap (`tax_rate`), atau harga pokok penjualan (`cost_price`).
  - Contoh konstanta teks: nama pemain permanen dalam game atau pesan galat baku sistem.
- **Keuntungan Penggunaan Konstanta**:
  - *Keterbacaan Kode (Code Readability)*: Menghilangkan keberadaan angka ajaib (*magic numbers*) tanpa konteks dengan menggantinya menjadi label deskriptif (misalnya menggunakan `tax_rate` alih-alih angka `0.11`).
  - *Kemudahan Pemeliharaan (Maintainability)*: Jika nilai referensi berubah di masa mendatang, pengembang hanya perlu memperbarui nilai pada baris deklarasi konstanta satu kali, tanpa harus mencari dan mengganti setiap kemunculan angka tersebut di seluruh berkas proyek.

### C. Variabel (Variables)
Variabel adalah pengenal yang nilainya bersifat dinamis dan dapat berubah-ubah sewaktu-waktu selama program berjalan:
- **Karakteristik Penggunaan**:
  - Digunakan untuk menampung data masukan pengguna yang belum diketahui saat kode ditulis (misalnya usia pengguna, skor permainan, nama akun, atau nama berkas yang diunggah).
  - Mencegah praktik penulisan nilai statis langsung di dalam kode (*hard-coding*), yang merupakan anti-pola dalam rekayasa perangkat lunak.
- **Inisialisasi Nilai**:
  - Variabel dapat dideklarasikan dengan tipe data dan nilai awal (*initial value*) secara langsung, atau dideklarasikan terlebih dahulu untuk kemudian diberi nilai oleh instruksi program selanjutnya.

### D. Struktur Penampung Data Jamak: Larik (Arrays) vs Vektor (Vectors)
Ketika program perlu mengelola sekumpulan data berjumlah masif (misalnya ribuan data numerik), mendefinisikan variabel terpisah untuk setiap item data merupakan pendekatan yang tidak efisien dan tidak terkelola. Untuk mengatasi hal ini, pengembang menggunakan struktur penampung (*containers*).

- **Larik Statis (*Arrays*)**:
  - Wadah data paling dasar yang menampung sejumlah elemen bernilai tetap (*fixed size*) dengan tipe data yang seragam.
  - Elemen-elemen disimpan dalam lokasi memori sekuensial yang berurutan, dengan penomoran indeks yang dimulai dari nol (`0`).
  - *Sintaks Deklarasi*: Pengembang menentukan tipe data, nama larik, dan kapasitas ukuran maksimum dalam kurung siku (contoh: `int scores[100]`).
  - *Karakteristik*: Efisiensi akses elemen sangat tinggi dan hemat memori, namun ukurannya kaku dan tidak dapat diperbesar saat aplikasi berjalan.
- **Vektor Dinamis (*Vectors / Dynamic Arrays*)**:
  - Wadah data yang memiliki kapasitas ukuran dinamis (*dynamic size*).
  - Vektor secara otomatis menyesuaikan kapasitas alokasi memorinya sendiri saat elemen baru ditambahkan atau dihapus.
  - *Kompromi Teknis*: Sifat alokasi dinamis menyebabkan vektor mengonsumsi ruang memori (*overhead*) yang sedikit lebih besar dibandingkan larik statis, serta waktu akses elemen sedikit lebih lambat karena manajemen alokasi memori dinamis di latar belakang.
  - *Sintaks Deklarasi*: Menggunakan notasi wadah dan kurung sudut untuk tipe data tanpa perlu menentukan batas ukuran maksimum (contoh dalam C++: `vector<int> scores`).

---

## 3. Modular Programming: Functions and Procedures

Seiring bertambahnya kompleksitas perangkat lunak, paradigma pemrograman modular (*modular programming*) diterapkan untuk memecah sistem monolitik menjadi komponen-komponen mandiri yang terfokus.

### A. Hakikat dan Definisi Fungsi
- **Definisi Fungsi (*Function*)**:
  - Blok kode terstruktur, mandiri, dan dapat digunakan kembali (*reusable*) yang dirancang khusus untuk menjalankan satu aksi spesifik.
  - Memungkinkan pengembang menguraikan permasalahan bisnis yang besar dan rumit menjadi modul-modul kecil yang mudah dipahami, diuji, dan dikelola.
- **Variasi Terminologi Lintas Bahasa**:
  - Berbagai bahasa pemrograman menggunakan istilah yang bervariasi untuk konsep ini, seperti prosedur (*procedures*), subrutin (*subroutines*), metode (*methods*), atau modul (*modules*), namun istilah *functions* merupakan sebutan paling universal dalam ekosistem modern.

### B. Model Operasional Fungsi (Input-Process-Output)
Fungsi beroperasi dengan mekanisme pertukaran data yang terdefinisi:
- **Masukan (*Input / Arguments*)**: Fungsi menerima data masukan berupa parameter yang dikirimkan oleh pemanggil.
- **Pemrosesan (*Processing*)**: Rangkaian pernyataan di dalam tubuh fungsi mengeksekusi logika algoritma terhadap data masukan.
- **Keluaran (*Output / Return Value*)**: Fungsi mengembalikan hasil pemrosesan kepada pemanggil program.

### C. Klasifikasi Fungsi
- **Fungsi Pustaka Standar (*Standard Library Functions*)**:
  - Fungsi bawaan (*built-in*) yang telah disediakan oleh bahasa pemrograman.
  - Menyediakan utilitas umum yang siap digunakan tanpa perlu dibuat dari awal, seperti fungsi pencetakan keluaran layar (`print()`, `printf()`), fungsi manipulasi teks, atau operasi matematika kompleks (`Math.sqrt()`).
- **Fungsi Buatan Pengguna (*User-Defined Functions*)**:
  - Fungsi yang dirancang dan ditulis sendiri oleh pengembang untuk menyelesaikan kebutuhan spesifik aplikasi.
  - Sekali fungsi didefinisikan, fungsi tersebut dapat dipanggil berulang kali dari berbagai bagian program (*write once, use repeatedly*).

### D. Tahapan Siklus Penggunaan Fungsi
- **1. Pendeklarasian Fungsi (*Declaration / Prototype*)**:
  - Diwajibkan pada bahasa terkompilasi tertentu seperti C dan C++. Berfungsi menginformasikan nama fungsi, tipe nilai kembali, dan tipe data parameter kepada kompilator sebelum fungsi tersebut dipanggil.
- **2. Pendefinisian Fungsi (*Definition*)**:
  - Menuliskan implementasi fisik fungsi yang mencakup kata kunci fungsi (*function keyword*), nama unik fungsi, daftar parameter formal, dan blok pernyataan tubuh fungsi.
  - Penanda blok tubuh fungsi berbeda antar bahasa: kurung kurawal `{}` (C, C++, Java, JavaScript), indentasi spasi ketat (Python), atau kata kunci `begin` dan `end` (Pascal).
- **3. Pemanggilan Fungsi (*Invocation / Call*)**:
  - Menginstruksikan program untuk mengeksekusi blok kode fungsi dengan meneruskan argumen parameter yang diperlukan.

---

## 4. Object-Oriented Programming: Concepts and Abstractions

Pemrograman Berorientasi Objek (*Object-Oriented Programming / OOP*) adalah paradigma pemrograman yang mengorganisasikan perancangan perangkat lunak di sekitar objek dan data, bukan di sekitar fungsi dan logika prosedural semata.

### A. Perbedaan Mendasar OOP vs Pemrograman Prosedural
- **Pemrograman Prosedural (*Procedure-Oriented Programming*)**:
  - Menitikberatkan fokus pada urutan eksekusi fungsi dan prosedur.
  - Prosedur beroperasi pada struktur data yang terpisah secara eksternal; data berpindah bebas dari satu fungsi ke fungsi lainnya sehingga rentan terhadap modifikasi yang tidak diinginkan.
- **Pemrograman Berorientasi Objek (*OOP*)**:
  - Menitikberatkan fokus pada objek mandiri.
  - Membungkus data (*properties/attributes*) dan kode prosedur (*methods/behaviors*) ke dalam satu kesatuan unit terpadu (*encapsulation*).
  - Objek beroperasi langsung pada struktur datanya sendiri, melindungi integritas status internal dari intervensi luar.

### B. Anatomi Objek: Keadaan (States) dan Perilaku (Behaviors)
Objek dalam perangkat lunak dimodelkan berdasarkan dua pertanyaan fundamental:
- **1. "Keadaan apa yang dapat dimiliki oleh objek?" (*States / Properties*)**:
  - Merepresentasikan data, atribut, atau karakteristik status yang melekat pada objek pada suatu waktu.
  - Disimpan dalam bentuk variabel atau medan internal (*fields*).
- **2. "Perilaku apa yang dapat dilakukan oleh objek?" (*Behaviors / Methods*)**:
  - Merepresentasikan aksi, fungsionalitas, atau komputasi yang dapat dijalankan oleh objek untuk merespons permintaan atau memperbarui keadaan internalnya.
  - Diekspos keluar dalam bentuk fungsi atau prosedur internal (*methods*).

### C. Pemodelan Objek Dunia Nyata ke Perangkat Lunak
- **Analogi Objek Fisik Nyata**:
  - *Mobil*:
    - Keadaan (*States*): Kecepatan saat ini, posisi transmisi gigi, sisa bahan bakar, status mesin menyala atau mati.
    - Perilaku (*Behaviors*): Menekan pedal gas (*accelerate*), menginjak rem (*brake*), memindahkan gigi (*shift gear*), menyalakan lampu.
  - *Mesin Cuci*:
    - Keadaan (*States*): Pilihan program cuci, suhu air, status timer putaran, pintu terkunci atau terbuka.
    - Perilaku (*Behaviors*): Mengisi air (*fill water*), memutar tabung (*spin*), membuang air kotor (*drain*).
- **Manifestasi Objek Perangkat Lunak Konkret**:
  - Konsep objek tidak terbatas pada benda fisik, melainkan mencakup seluruh entitas logis dalam sistem komputasi:
    - *Layanan Sistem Operasi (Windows Service)*: Memiliki properti status berjalan (*running/stopped*) dan metode mulai (*start*), jeda (*pause*), atau henti (*stop*).
    - *Akun Pengguna (User Account)*: Memiliki properti nama pengguna, surel, tingkat hak akses, dan metode ubah sandi (*change password*) atau autentikasi (*login*).
    - *Tabel Basis Data (Database Table)*: Memiliki properti nama tabel, jumlah baris, skema kolom, dan metode tambah data (*insert row*) atau hapus data (*drop table*).
    - *Direktori Sistem (System Folder)*: Memiliki properti jalur berkas, kapasitas ukuran direktori, tanggal modifikasi, dan metode buat berkas (*create file*) atau hapus direktori (*delete folder*).