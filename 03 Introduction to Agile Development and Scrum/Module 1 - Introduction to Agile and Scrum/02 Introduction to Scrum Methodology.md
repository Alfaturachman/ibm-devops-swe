# Introduction to Scrum Methodology

Dokumen ini memuat rangkuman komprehensif mengenai metodologi *Scrum*, struktur kerangka kerja operasional, tiga peran utama (*Product Owner*, *Scrum Master*, *Scrum Team*), tiga artefak, lima peristiwa resmi (*Scrum Events*), manfaat bisnis yang dihasilkan, serta analisis komparatif antara kerangka kerja *Scrum* dan *Kanban*.

---

## 1. Fondasi dan Kerangka Kerja Scrum

### A. Perbedaan Mendasar Agile dan Scrum
Meskipun istilah *Agile* dan *Scrum* sering digunakan secara bergantian dalam industri, keduanya memiliki perbedaan definisi yang sangat mendasar:
- **Agile sebagai Filosofi (*Philosophy*):**
  - Bersifat konseptual, tidak preskriptif (*non-prescriptive*), dan memuat seperangkat nilai serta prinsip pemandu mengenai cara berpikir dalam merespons perubahan pasar.
- **Scrum sebagai Metodologi (*Methodology*):**
  - Bersifat praktis dan preskriptif (*prescriptive*). *Scrum* merupakan kerangka kerja manajemen khusus yang menyediakan aturan main (*rules*), peran terdefinisi (*roles*), artefak (*artifacts*), serta pertemuan berkala (*events*) untuk menerapkan filosofi *Agile* secara nyata dalam pengembangan produk bertahap (*incremental product development*).

### B. Prinsip "Mudah Dipahami, Sulit Dikuasai"
*Scrum* dikenal dengan karakteristik *"easy to understand, difficult to master"*:
- Aturan dasar *Scrum* sangat ringkas dan sederhana untuk dipelajari secara teoritis.
- Namun, implementasi praktisnya membutuhkan kedisiplinan dan perubahan budaya kerja yang mendalam, dianalogikan seperti seni tari balet: gerakannya terlihat sederhana, namun membutuhkan latihan bertahun-tahun untuk membentuk memori otot dan kekuatan fisik yang tepat.
- Oleh karena itu, bagi organisasi atau tim yang baru memulai adopsi *Scrum*, kehadiran seorang pembimbing atau *Scrum Master* yang berpengalaman sangat menentukan keberhasilan transisi.

### C. Anatomi dan Karakteristik Sprint
Inti operasional *Scrum* berputar pada siklus berulang yang disebut *Sprint*:
- **Definisi Sprint:**
  - Satu siklus iterasi tetap yang menjalankan keseluruhan daur hidup pengembangan perangkat lunak (*Software Delivery Lifecycle / SDLC*) mini: perancangan (*design*), penulisan kode (*code*), pengujian (*test*), hingga penerapan (*deploy*).
- **Durasi Waktu (*Timebox*):**
  - Umumnya berdurasi 2 pekan (14 hari kalender). Durasi 4 pekan dinilai terlalu panjang dalam ekosistem dinamis karena risiko pergeseran kebutuhan pelanggan menjadi terlalu besar, sedangkan durasi 1 pekan sering kali terlalu menekan tim teknis. Durasi 2 pekan memberikan keseimbangan ideal antara ukuran *batch* kecil dan stabilitas fokus.
- **Sasaran Sprint (*Sprint Goal*):**
  - Setiap *sprint* wajib memiliki satu tujuan spesifik yang dipahami bersama oleh seluruh anggota tim: apa nilai fungsional yang ingin dihadirkan kepada pelanggan pada akhir iterasi.
- **Hasil Akhir (*Potentially Shippable Product Increment*):**
  - Setiap *sprint* harus menghasilkan satu inkremen produk yang berfungsi dan berpotensi untuk langsung dirilis ke tangan pengguna akhir guna memvalidasi penerimaan pasar.

### D. Alur Proses Operasional Scrum
Proses pengembangan dalam *Scrum* berjalan melalui tahapan terstruktur:
1. **Product Backlog:** Daftar induk yang memuat seluruh ide, fitur, perbaikan, dan kebutuhan masa depan yang diinginkan untuk produk.
2. **Backlog Refinement (Grooming):** Aktivitas rutin di mana *Product Owner* bersama tim menyempurnakan rincian cerita pengguna (*user stories*), memperjelas kriteria penerimaan, dan memastikan cerita siap untuk dieksekusi (*sprint-ready*).
3. **Sprint Planning:** Rapat penentuan sasaran *sprint* di mana tim mengambil sejumlah cerita teratas dari *Product Backlog* untuk dimasukkan ke dalam *Sprint Backlog*.
4. **Sprint Backlog:** Daftar komitmen tugas spesifik yang akan diselesaikan oleh tim pengembang dalam kurun waktu 2 pekan ke depan.
5. **Eksekusi dan Daily Scrum:** Pengerjaan tugas harian yang disinkronkan melalui rapat berdiri (*daily stand-up*) 15 menit dengan menjawab 3 pertanyaan pokok:
   - Apa yang telah saya selesaikan kemarin?
   - Apa yang akan saya kerjakan hari ini?
   - Hambatan atau kendala apa yang merintangi kemajuan kerja saya?
6. **Penyerahan Inkremen:** Menghasilkan produk jadi yang dapat diuji dan divalidasi langsung oleh pemangku kepentingan.

---

## 2. Tiga Peran Kunci dalam Scrum (Scrum Roles)

Struktur organisasi dalam *Scrum* hanya mengakui tiga peran resmi tanpa penambahan hierarki manajemen internal:

### A. Product Owner (PO)
*Product Owner* memegang peran sentral sebagai penentu arah bisnis dan pemilik visi produk:
- **Representasi Pemangku Kepentingan (*Stakeholder Interests*):**
  - Menjadi jembatan komunikasi tunggal antara pihak penyandang dana (*investor/sponsor*) dengan tim teknis. Tim pengembang tidak perlu berurusan langsung dengan tuntutan pemangku kepentingan yang saling bertentangan; seluruh kebutuhan disaring melalui *Product Owner*.
- **Perumus Visi Produk (*Articulating Product Vision*):**
  - Mengartikulasikan sasaran strategis produk kepada seluruh tim sehingga setiap anggota memahami konteks bisnis dari fitur yang mereka bangun.
- **Penentu Kebutuhan dan Prioritas (*Final Arbiter of Requirements*):**
  - Memiliki wewenang mutlak untuk memutuskan urutan prioritas pada *Product Backlog* (*backlog reprioritization*).
- **Pengambil Keputusan Rilis (*Accept or Reject Increment*):**
  - Satu-satunya pihak yang berwenang untuk menerima atau menolak hasil kerja tim di akhir *sprint*, serta memutuskan apakah inisiatif produk harus dilanjutkan (*persevere*) atau dibelokkan (*pivot*).
- **Perbedaan PO vs Product Manager:**
  - *Product Manager* adalah sebutan jabatan pekerjaan fungsional (*job title*), sedangkan *Product Owner* adalah peran resmi dalam kerangka kerja *Scrum* (*Scrum role*). Seorang *Product Manager* dapat berperan sebagai *Product Owner*, namun keduanya tidak boleh disamakan.

### B. Scrum Master (SM)
*Scrum Master* bertindak sebagai pemimpin yang melayani (*servant leader*) dan pelatih proses bagi tim:
- **Pelatih Proses Agile (*Agile Coach and Mentor*):**
  - Memandu dan memastikan seluruh anggota tim memahami serta menerapkan prinsip, aturan, dan pertemuan *Scrum* secara disiplin.
- **Membangun Kemandirian Tim (*Fostering Self-Organization*):**
  - Menciptakan iklim kerja yang kondusif agar tim pengembang memiliki otonomi untuk mengorganisasi dan menentukan cara kerja mereka sendiri.
- **Perisai Pelindung Tim (*Shielding the Team*):**
  - Menghalau intervensi eksternal dari manajer departemen, klien, atau pemangku kepentingan lain yang mencoba menyusupkan pekerjaan ad-hoc di tengah berlangsungnya *sprint*.
- **Penyelesai Hambatan (*Removing Impediments*):**
  - Prioritas kerja tertinggi seorang *Scrum Master* setiap hari adalah membersihkan rintangan (*blockers*) yang dihadapi anggota tim saat *Daily Scrum* agar tim dapat kembali fokus berproduksi secara optimal.
- **Penjaga Batas Waktu (*Enforcing Timeboxes*):**
  - Memastikan seluruh pertemuan mematuhi batas durasi waktu (misalnya *Daily Scrum* tepat 15 menit dan *Sprint* tidak melampaui 2 pekan).
- **Pengumpul Data Empiris:**
  - Menganalisis metrik kemajuan tim seperti diagram *Burndown Chart* untuk memproyeksikan pencapaian target.
- **Mengapa Scrum Master Bukan Manajer Tim:**
  - *Scrum Master* tidak boleh memiliki otoritas administratif (seperti kendali atas penilaian kinerja, bonus, atau gaji). Anggota tim harus memandang *Scrum Master* sebagai rekan terpercaya tempat berkeluh kesah mengenai kendala teknis dan kekurangan kompetensi tanpa rasa takut akan sanksi profesional.

### C. Scrum Team (Development Team)
Tim pengembang adalah sekelompok profesional yang berdedikasi menciptakan inkremen fungsional:
- **Komposisi Lintas Fungsi (*Cross-Functional*):**
  - Beranggotakan seluruh disiplin keahlian yang dibutuhkan untuk menghasilkan perangkat lunak siap pakai: rekayasawan perangkat lunak (*developers*), spesialis pengujian (*testers/QA*), analis bisnis (*business analysts*), desainer antarmuka (*UI/UX*), hingga praktisi operasional (*DevOps*).
- **Kemandirian Penuh (*Self-Organizing and Self-Managing*):**
  - Tidak ada pembagian sub-hierarki internal. Anggota tim mengambil sendiri pekerjaan dari papan kerja visual (*pull system*); tidak ada pihak luar yang berhak menugaskan pekerjaan kepada individu secara sepihak.
- **Ukuran Tim Kompak:**
  - Jumlah anggota ideal adalah $7 \pm 2$ orang (berkisar antara 5 hingga 9 orang). Tim yang terlalu besar ($> 10$ orang) menciptakan gesekan komunikasi dan birokrasi koordinasi yang kontraproduktif.
- **Lokasi Bersama (*Co-located*):**
  - Kinerja puncak tercapai saat seluruh anggota tim bekerja di satu ruangan fisik yang sama. Apabila tim harus terdistribusi secara geografis, aturan praktisnya adalah menempatkan minimal dua anggota dalam satu lokasi atau zona waktu yang sama guna menghindari isolasi sosial dan profesional.
- **Dedikasi Penuh (*Dedicated Members*):**
  - Anggota tim harus fokus 100% pada satu proyek tunggal. Membagi alokasi waktu satu individu ke beberapa proyek sekaligus terbukti merusak produktivitas dan membuyarkan komitmen tim.
- **Otonomi Eksekusi:**
  - Tim menegosiasikan komitmen volume pekerjaan dengan *Product Owner* untuk satu *sprint* berjalan, lalu diberikan kebebasan penuh mengenai metode teknis (*how*) untuk merealisasikan sasaran tersebut.

---

## 3. Tiga Artefak dan Lima Peristiwa dalam Scrum

### A. Tiga Artefak Resmi Scrum (*Scrum Artifacts*)
Artefak *Scrum* merepresentasikan nilai pekerjaan atau produk yang memberikan transparansi penuh:
1. **Product Backlog:**
   - Inventaris dinamis berisi seluruh daftar kebutuhan, fungsionalitas, peningkatan performa, dan perbaikan galat yang direncanakan untuk produk jangka panjang.
2. **Sprint Backlog:**
   - Kumpulan item terpilih dari *Product Backlog* yang dipadukan dengan rencana kerja teknis untuk menghantarkan sasaran *sprint* dalam kurun waktu 2 pekan.
3. **Done Increment:**
   - Hasil akumulasi fitur yang berfungsi, teruji, dan telah memenuhi standar kesepakatan kualitas (*Definition of Done*) pada akhir masa *sprint*.

### B. Lima Peristiwa Resmi Scrum (*Scrum Events*)
Semua peristiwa dalam *Scrum* memiliki batas waktu (*timeboxed*) untuk menciptakan keteraturan dan mengeliminasi rapat-rapat yang tidak terstruktur:
1. **Sprint Planning:**
   - Rapat kolaboratif di awal *sprint* antara PO, SM, dan tim pengembang untuk menyepakati sasaran *sprint* dan menyusun *Sprint Backlog*.
2. **Daily Scrum (Daily Stand-Up):**
   - Pertemuan sinkronisasi berdurasi maksimal 15 menit setiap pagi untuk mengoordinasikan aktivitas kerja harian dan mengungkap kendala teknis.
3. **The Sprint:**
   - Periode kontainer operasional berdurasi tetap 2 pekan di mana ide-ide dikonversi menjadi inkremen produk nyata.
4. **Sprint Review (Demo Time):**
   - Pertemuan di akhir *sprint* untuk mendemonstrasikan fitur baru yang telah selesai kepada pemangku kepentingan dan menerima masukan langsung.
5. **Sprint Retrospective:**
   - Pertemuan refleksi internal tim pengembang bersama *Scrum Master* (dan PO) untuk meninjau efektivitas hubungan kerja, proses operasional, serta merumuskan rencana aksi perbaikan konkret untuk *sprint* berikutnya.

---

## 4. Manfaat Bisnis dan Perbandingan Komparatif: Scrum vs Kanban

### A. Manfaat Nyata Implementasi Scrum
Penerapan *Scrum* yang matang memberikan sejumlah keuntungan strategis bagi organisasi:
- **Produktivitas Tinggi (*Higher Productivity*):** Kejelasan tugas harian, transparansi papan kerja, dan penghapusan *blocker* secara konsisten mendorong penyelesaian pekerjaan lebih cepat.
- **Peningkatan Mutu Perangkat Lunak (*Better Quality*):** Penerapan pengujian berulang dan integrasi praktik rekayasa (*TDD, BDD, otomatisasi uji*) meminimalkan cacat sebelum rilis.
- **Pemangkasan Waktu ke Pasar (*Reduced Time to Market*):** Inkremen fungsional dihasilkan setiap 2 pekan, memungkinkan peluncuran fitur bernilai tinggi lebih awal ke konsumen.
- **Kepuasan Pemangku Kepentingan (*Stakeholder Satisfaction*):** Klien melihat kemajuan nyata secara periodik dan memiliki kendali adaptif atas prioritas fitur.
- **Dinamika dan Budaya Kerja Positif (*Happier Employees*):** Anggota tim merasa dihargai, memiliki otonomi, dan bekerja dalam lingkungan kerja yang transparan dan suportif.

### B. Perbandingan Komparatif: Scrum vs Kanban
Meskipun tim *Scrum* sering kali memanfaatkan papan kerja visual bertipe *Kanban*, terdapat perbedaan filosofis dan operasional mendasar di antara keduanya:
- **Ritme / Irama Kerja (*Cadence*):**
  - *Scrum:* Beroperasi dalam iterasi berdurasi tetap (*fixed-length sprints*), umumnya 2 pekan.
  - *Kanban:* Beroperasi dalam aliran kerja berkelanjutan (*continuous flow*) tanpa batas waktu iterasi kaku.
- **Metodologi Rilis (*Release Methodology*):**
  - *Scrum:* Rilis dilakukan pada akhir masa *sprint* setelah demonstrasi dan persetujuan PO.
  - *Kanban:* Menganut pengiriman berkesinambungan (*continuous delivery*); fitur dirilis ke produksi seketika saat item selesai (*Definition of Done* terpenuhi).
- **Struktur Peran (*Roles*):**
  - *Scrum:* Memiliki tiga peran kaku yang wajib diisi (*Product Owner*, *Scrum Master*, *Scrum Team*).
  - *Kanban:* Tidak menetapkan peran formal baku; tim mempertahankan struktur peran organisasi yang sudah ada.
- **Metrik Kunci Kinerja (*Key Metrics*):**
  - *Scrum:* Mengukur Kecepatan (*Velocity*), yaitu jumlah bobot pekerjaan (*story points*) yang dapat dituntaskan tim dalam rentang 2 pekan.
  - *Kanban:* Mengukur Waktu Siklus (*Cycle Time* dan *Lead Time*), yaitu durasi yang dibutuhkan oleh satu item tugas sejak pertama kali masuk sistem hingga selesai dikerjakan.
- **Filosofi Perubahan (*Change Philosophy*):**
  - *Scrum:* Komitmen *Sprint Backlog* dikunci selama 2 pekan. Perubahan kebutuhan di tengah *sprint* sangat dibatasi dan dialihkan ke perencanaan *sprint* berikutnya.
  - *Kanban:* Perubahan prioritas dapat terjadi kapan saja secara bebas, asalkan batasan beban kerja dalam proses (*WIP limits*) tetap dihormati.

---

## 5. Rangkuman dan Poin Pembelajaran Kunci

1. **Definisi Distingtif:** *Agile* adalah payung filosofis berpikir, sementara *Scrum* adalah kerangka kerja manajemen preskriptif untuk mewujudkan nilai *Agile*.
2. **Karakteristik Tiga Peran:** *Product Owner* bertanggung jawab atas visi dan prioritas bisnis, *Scrum Master* bertanggung jawab atas pemeliharaan proses dan penghapusan hambatan, sedangkan *Scrum Team* memegang kendali otonom atas perancangan dan konstruksi teknis.
3. **Integritas Tiga Artefak:** *Product Backlog* (ekspektasi masa depan), *Sprint Backlog* (fokus operasional 2 pekan), dan *Done Increment* (nilai nyata yang teruji dan siap rilis).
4. **Disiplin Lima Peristiwa:** Setiap peristiwa *Scrum* dibatasi waktu secara ketat (*timeboxed*) untuk mengefisiensikan koordinasi dan menciptakan lingkaran umpan balik berkesinambungan.
5. **Diferensiasi terhadap Kanban:** *Scrum* mengandalkan iterasi tetap berbasis waktu dan komitmen terkunci, sedangkan *Kanban* bertumpu pada aliran kerja berkelanjutan tanpa batas *sprint* dengan pembatasan ketat terhadap WIP.
