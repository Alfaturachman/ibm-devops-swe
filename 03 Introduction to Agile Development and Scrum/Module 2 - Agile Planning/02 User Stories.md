# User Stories and Backlog Management

Dokumen ini memuat rangkuman komprehensif mengenai perancangan cerita pengguna (*user stories*), penerapan kriteria penerimaan fungsional berbasis sintaksis *Gherkin*, evaluasi kualitas cerita menggunakan kerangka *INVEST*, teknik estimasi relatif menggunakan *Story Points* dan deret *Fibonacci*, mitigasi anti-pola estimasi waktu kalender, serta strategi pembangunan dan penataan prioritas pada *Product Backlog*.

---

## 1. Anatomi dan Karakteristik User Story yang Efektif

### A. Definisi dan Filosofi User Story vs Persyaratan Tradisional
Dalam rekayasa perangkat lunak modern, *User Story* menggantikan dokumen spesifikasi kebutuhan (*requirements*) tradisional yang kaku:
- **Keterbatasan Spesifikasi Kebutuhan Tradisional:**
  - Persyaratan konvensional umumnya hanya menyatakan secara sepihak apa yang harus dilakukan oleh sistem (contoh: *"Sistem harus menyediakan fitur penghitung"*), tanpa memuat konteks siapa penggunanya dan tujuan bisnis di balik fitur tersebut.
- **Definisi User Story:**
  - *User Story* merepresentasikan potongan nilai bisnis (*business value*) terkecil yang dapat dipahami, dikembangkan, diuji, dan diserahkan oleh tim pengembang dalam satu inkremen produk yang selesai (*done increment*).
  - Menyajikan tiga elemen fundamental: Siapa yang membutuhkan (*Who*), Apa yang dibutuhkan (*What*), dan Mengapa hal tersebut bernilai (*Why*).

### B. Format Templat Standar User Story
Untuk memastikan kelengkapan struktur cerita dan keselarasan pemahaman, digunakan templat standar tiga baris:
```text
As a <role/persona>,
I need <functionality>,
So that <business value/benefit>.
```
- **As a [Role/Persona]:** Mendefinisikan peran spesifik pihak yang memperoleh manfaat langsung (misalnya: *Marketing Manager*, *System Administrator*, atau *End Customer*), bukan sebutan umum yang samar.
- **I need [Functionality]:** Menjelaskan kapabilitas atau tindakan nyata yang dibutuhkan oleh peran tersebut.
- **So that [Business Value/Benefit]:** Menegaskan dampak atau nilai bisnis nyata yang ingin dicapai. Elemen ini menjadi pertimbangan utama bagi *Product Owner* dalam menentukan urutan prioritas di *Product Backlog*.

### C. Tiga Komponen Pendukung Cerita yang Baik
1. **Deskripsi Cerita (*Story Description*):**
   - Penjelasan ringkas fungsionalitas menggunakan templat persona di atas.
2. **Asumsi dan Rincian Teknis (*Assumptions and Details*):**
   - Informasi kontekstual yang disepakati bersama saat penulisan cerita guna membantu tim pengembang menghindari salah arah.
   - *Contoh:* Menyatakan asumsi bahwa data email pelanggan telah tersimpan di basis data relasional, atau bahwa sistem harus mematuhi regulasi persetujuan promosi (*opt-in*).
3. **Kriteria Penerimaan (*Acceptance Criteria / Definition of Done*):**
   - Tolok ukur objektif yang menentukan apakah suatu cerita telah tuntas dikerjakan (*done*) dan siap diuji. Kriteria ini mencegah perselisihan interpretasi antara pengembang dan *Product Owner* saat *Sprint Review*.

### D. Penerapan Kriteria Penerimaan dengan Sintaksis Gherkin
Sintaksis *Gherkin* (dikembangkan oleh *Cucumber*) menyediakan struktur kalimat baku yang mudah dipahami oleh pemangku kepentingan bisnis maupun tim teknis:
- **Struktur Tiga Klausa Gherkin:**
  - `Given`: Kumpulan prakondisi awal sistem (*preconditions*).
  - `When`: Tindakan atau peristiwa pemicu yang sedang diuji (*action/event*).
  - `Then`: Hasil akhir atau perilaku sistem yang dapat diamati dan diukur secara pasti (*observable outcome*).
- **Studi Kasus Skenario Promosi Pemasaran:**
  - *Cerita Pengguna:*
    - *Sebagai Manajer Pemasaran, saya membutuhkan daftar nama dan email pelanggan, agar saya dapat mengirimkan pemberitahuan promosi.*
  - *Kriteria Penerimaan (Gherkin):*
    ```gherkin
    Given terdapat 100 data pelanggan di dalam basis data
    And 90 pelanggan telah menyetujui penerimaan promosi (opt-in)
    When saya meminta daftar email promosi pelanggan
    Then sistem harus menampilkan tepat 90 alamat email pelanggan
    ```
  - *Hasil:* Pengembang memahami kewajiban memfilter data berdasarkan status persetujuan, dan penguji memiliki skenario validasi yang jelas.

### E. Prinsip Kualitas Cerita: Akronim INVEST
Diformulasikan oleh Bill Wake, akronim **INVEST** menjadi panduan uji kelayakan sebuah cerita pengguna:
1. **Independent (Independen):**
   - Sedapat mungkin cerita tidak memiliki ketergantungan erat dengan cerita lain, sehingga posisinya dapat dipindah atau diprioritaskan ulang di *backlog* secara bebas.
2. **Negotiable (Dapat Dinegosiasikan):**
   - Cerita bukan kontrak hukum yang kaku; rincian cakupan fungsionalitas dapat dinegosiasikan antara *Product Owner* dan pengembang sesuai kapasitas waktu.
3. **Valuable (Bernilai Nyata):**
   - Harus menghantarkan manfaat nyata bagi pengguna akhir atau bisnis, bukan sekadar tugas teknis internal (*technical debt*) yang tidak berdampak pada produk.
4. **Estimable (Dapat Diestimasi):**
   - Memiliki kejelasan konteks yang memadai sehingga tim dapat memperkirakan bobot usaha yang diperlukan.
5. **Small (Berukuran Kecil):**
   - Harus berukuran cukup ringkas agar dapat diselesaikan secara tuntas dalam kurun waktu satu *sprint* (beberapa hari kerja).
6. **Testable (Dapat Diuji):**
   - Memiliki kriteria keberhasilan yang jelas dan dapat divalidasi melalui pengujian otomatis maupun manual.

### F. Konsep Epics dan Penanganan Gagasan Berskala Besar
- **Definisi Epic:**
  - Inisiatif atau gagasan bisnis berskala besar yang terlalu kompleks dan melebihi durasi satu siklus *sprint*.
- **Hierarki Kerja:**
  - Dalam hierarki perencanaan, *Epic* berada di atas *Story*. Sebuah *Epic* memayungi dan dipecah menjadi kumpulan cerita pengguna yang lebih kecil.
- **Waktu Penggunaan Epic:**
  - Saat kebutuhan awal baru masuk ke saluran *New Issues* dalam bentuk ide makro.
  - Saat sebuah cerita setelah dianalisis memiliki ukuran terlalu besar (misalnya bernilai 21 poin), cerita tersebut dikonversi menjadi *Epic* lalu didekomposisi agar muat ke dalam rencana *sprint*.

---

## 2. Estimasi Relatif dan Pemanfaatan Story Points

### A. Hakikat Story Points sebagai Ukuran Abstrak
*Story Points* adalah metrik abstrak yang digunakan oleh tim *Agile* untuk mengukur tingkat kesulitan dalam menerapkan suatu cerita pengguna:
- **Tiga Dimensi Pembentuk Estimasi:**
  1. **Usaha (*Effort*):** Volume pekerjaan fisik atau waktu pengerjaan yang diperlukan untuk menyelesaikan tugas.
  2. **Kompleksitas (*Complexity*):** Kerumitan logika arsitektur, algoritma, atau interaksi sistem yang terlibat.
  3. **Ketidakpastian dan Risiko (*Uncertainty / Risk*):** Tingkat ketidaktahuan tim terhadap teknologi baru atau dependensi eksternal yang belum pernah dieksplorasi sebelumnya.

### B. Kelemahan Manusia terhadap Estimasi Waktu Kalender
- **Keterbatasan Estimasi Absolut:**
  - Manusia secara psikologis terbukti sangat buruk dalam memperkirakan durasi waktu kalender (*wall-clock time*) secara absolut.
  - Terdapat ungkapan populer dalam rekayasa perangkat lunak: *"Satu-satunya hal yang memakan waktu tepat 30 menit adalah 30 menit; hal-hal lainnya selalu memakan waktu lebih lama."*
- **Pendekatan Estimasi Relatif:**
  - Membandingkan ukuran suatu objek terhadap objek pembanding lain jauh lebih mudah dan akurat daripada mengukur dimensi absolutnya.
  - *Analogi Ketinggian Gedung:* Jika seseorang diminta menebak tinggi gedung secara presisi dalam satuan meter, ia akan kesulitan. Namun, jika gedung acuan ditetapkan berukuran 5, ia dapat dengan mudah menyimpulkan bahwa gedung di sebelahnya berukuran 3 (lebih rendah), gedung lain berukuran 8 (lebih tinggi), dan gedung pencakar langit di kejauhan bernilai 13.

### C. Ukuran Kaus dan Deret Fibonacci yang Dimodifikasi
Untuk mengoperasionalkan estimasi relatif, tim memadukan konsep ukuran kaus (*T-shirt sizes*) dengan deret angka Fibonacci:
- **Pemetaan Skala Ukuran:**
  - *Small (S):* Diberi bobot 3 poin.
  - *Medium (M):* Diberi bobot 5 poin (dijadikan sebagai tolok ukur dasar / *baseline* tim).
  - *Large (L):* Diberi bobot 8 poin.
  - *Extra Large (XL):* Diberi bobot 13 poin.
- **Pentingnya Kesepakatan Garis Dasar (*Baseline Agreement*):**
  - Tim harus terlebih dahulu menyepakati contoh sebuah cerita nyata yang mewakili kategori *Medium* (5 poin). Seluruh cerita baru berikutnya dinilai secara komparatif terhadap cerita acuan tersebut: apakah lebih mudah, setara, atau lebih rumit.
- **Pelacakan Kecepatan Tim (*Velocity Tracking*):**
  - Angka-angka ini dapat dijumlahkan pada akhir *sprint* untuk mengukur kecepatan rata-rata tim (*team velocity*), sehingga kapasitas perencanaan *sprint* berikutnya menjadi lebih terukur.

### D. Batasan Ukuran Cerita dan Dekomposisi
- Cerita yang ideal harus dapat diselesaikan dalam rentang waktu beberapa hari kerja.
- Cerita yang mendapat estimasi 21 poin atau lebih dianggap terlalu besar untuk dieksekusi dalam satu *sprint* 2 pekan. Cerita tersebut wajib dipecah (*split*) menjadi beberapa cerita independen yang lebih kecil.

### E. Anti-Pola Fatal: Menyamakan Story Points dengan Waktu Kalender
Salah satu kesalahan paling destruktif dalam praktik *Scrum* adalah menyamakan *Story Points* secara linier dengan durasi hari kalender:
- **Anti-Pola Mantan Manajer Proyek:**
  - Menyatakan kepada tim bahwa 1 poin setara dengan 1 hari kerja, 3 poin setara dengan 3 hari, dan 5 poin setara dengan 5 hari adalah kekeliruan total.
- **Dampak Negatif:**
  - Menghilangkan sifat keabstrakan estimasi, mengembalikan tim ke perangkap jadwal kaku *Gantt Chart*, dan memicu kepanikan saat target hari meleset. Tingkat ketidakpastian (*uncertainty*) tidak dapat dikonversi secara langsung menjadi jam kerja statis.

---

## 3. Pembangunan dan Pengelolaan Product Backlog

### A. Definisi dan Struktur Hierarki Product Backlog
*Product Backlog* adalah daftar terurut (*ranked list*) yang memuat seluruh cerita pengguna yang belum diimplementasikan:
- **Gradasi Rincian Berdasarkan Posisi:**
  - *Bagian Atas Backlog (Top):* Memiliki prioritas bisnis tertinggi, dirinci secara sangat mendalam (*high detail*), telah dilengkapi kriteria penerimaan yang jelas, dan berada dalam kondisi siap dieksekusi (*sprint-ready*) untuk 1 atau 2 *sprint* ke depan.
  - *Bagian Bawah Backlog (Bottom):* Berisi inisiatif jangka panjang yang rinciannya masih bersifat makro dan fleksibel (*fuzzy*); pendalaman cerita dilakukan saat item tersebut bergerak mendekati bagian atas.

### B. Studi Kasus Komprehensif: Pembangunan Layanan Penghitung (Hit Counter Service)
Contoh nyata konversi empat kebutuhan pelanggan menjadi cerita pengguna terstruktur dan penataan prioritasnya pada *Product Backlog*:
1. **Kebutuhan 1: Layanan Dasar Penghitung:**
   - *Spesifikasi Cerita:*
     - *Sebagai pengguna, saya membutuhkan layanan penghitung, agar saya dapat melacak berapa kali suatu aksi telah dilakukan.*
   - *Evaluasi Prioritas:* Merupakan kapabilitas fundamental paling inti. Tanpa layanan dasar ini, fungsionalitas lain tidak dapat berjalan. Ditempatkan pada peringkat teratas *Product Backlog*.
2. **Kebutuhan 2: Dukungan Banyak Penghitung (Multiple Counters):**
   - *Spesifikasi Cerita:*
     - *Sebagai pengguna, saya membutuhkan kemampuan membuat banyak penghitung sekaligus, agar saya dapat melacak beberapa hitungan yang berbeda secara simultan.*
   - *Evaluasi Prioritas:* Meskipun bermanfaat, fitur ini dapat ditunda ke masa depan setelah layanan tunggal terbukti bekerja. Dipindahkan ke saluran *Icebox* atau dasar *backlog*.
3. **Kebutuhan 3: Persistensi Data Melintasi Restart Layanan:**
   - *Spesifikasi Cerita:*
     - *Sebagai penyedia layanan, saya membutuhkan sistem untuk menyimpan hitungan terakhir ke basis data, agar data pengguna tidak hilang saat server mengalami restart.*
   - *Evaluasi Prioritas:* Versi produk awal (*MVP*) dapat berjalan sementara di dalam memori (*in-memory*). Namun, persistensi basis data harus segera dibangun tepat setelah layanan dasar bekerja. Ditempatkan pada prioritas kedua.
4. **Kebutuhan 4: Kemampuan Reset Nilai Penghitung:**
   - *Spesifikasi Cerita:*
     - *Sebagai administrator sistem, saya membutuhkan wewenang mereset nilai penghitung kembali ke nol, agar saya dapat mengulang pencatatan hitungan dari awal.*
   - *Evaluasi Prioritas:* Dibatasi hanya untuk peran administrator sistem demi keamanan data. Ditempatkan pada prioritas ketiga setelah persistensi basis data selesai diintegrasikan.

### C. Alur Triase dan Prioritisasi pada Papan Kanban
- Seluruh kebutuhan awal masuk ke saluran *New Issues* sebagai kotak masuk.
- *Product Owner* mengevaluasi nilai bisnis dari klausul *"So that..."* pada setiap cerita.
- Cerita yang fundamental segera dimasukkan ke puncak *Product Backlog*, cerita jangka panjang dialihkan ke *Icebox*, dan cerita yang tidak relevan ditolak secara transparan.

---

## 4. Rangkuman dan Poin Pembelajaran Kunci

1. **Esensi User Story:** Menggeser paradigma dokumen spesifikasi statis menjadi artikulasi nilai bisnis yang menghubungkan peran pengguna (*Who*), fungsionalitas (*What*), dan manfaat (*Why*).
2. **Kepastian Kriteria Penerimaan:** Pemanfaatan sintaksis *Gherkin* (`Given`/`When`/`Then`) mengeliminasi ambiguitas definisi selesai (*Definition of Done*) antara pengembang dan pemangku kepentingan.
3. **Uji Kelayakan INVEST:** Menjamin cerita berukuran kecil, mandiri, dapat dinegosiasikan, dapat diuji, dan bernilai nyata bagi bisnis.
4. **Estimasi Berbasis Story Points:** Pemanfaatan skala komparatif relatif (Fibonacci 3, 5, 8, 13) yang menggabungkan usaha, kompleksitas, dan ketidakpastian; larangan mutlak menyamakan poin dengan durasi hari kalender.
5. **Dinamika Product Backlog:** Pengelolaan berjenjang di mana cerita teratas dipersiapkan secara mendalam dan siap dieksekusi (*sprint-ready*), sedangkan inisiatif masa depan disimpan rapi pada *Icebox*.
