# Daily Plan Execution and Stand-Up Meetings

Dokumen ini memuat rangkuman komprehensif mengenai tata kelola eksekusi harian dalam *sprint*, alur kerja operasional penarikan tugas mandiri pada papan *Kanban*, penegakan batas beban kerja dalam proses (*WIP limits*), otomatisasi peninjauan kode melalui *Pull Requests*, serta protokol pelaksanaan rapat berdiri harian (*Daily Stand-Up*) yang berdisiplin dan berorientasi pada pemecahan hambatan (*impediments*).

---

## 1. Alur Kerja Eksekusi Harian pada Papan Kanban

### A. Prinsip Penarikan Tugas dari Sprint Backlog
Ketika siklus *sprint* 2 pekan resmi dimulai, fokus operasional tim pengembang beralih sepenuhnya ke sisi kanan papan kerja (*Kanban board*):
- **Isolasi Fokus Operasional:**
  - Anggota tim tidak perlu lagi memperhatikan saluran di sisi kiri (*New Issues, Icebox, Product Backlog*). Perhatian harian dipusatkan pada empat saluran eksekusi: *Sprint Backlog*, *In Progress*, *Review / QA*, dan *Done*.
- **Aturan Pemilihan Tugas:**
  - Setiap pengembang mengambil cerita dari urutan teratas pada *Sprint Backlog* yang sesuai dengan keahlian teknisnya.
  - Anggota tim tidak diperkenankan memilih tugas di posisi tengah secara acak atau memilih fitur favorit pribadi; pengerjaan wajib mematuhi hierarki kepentingan bisnis yang telah disepakati bersama *Product Owner*.

### B. Penugasan Diri (Self-Assignment) dan Visibilitas Transparan
- **Mekanisme Mandiri (*Self-Managing*):**
  - Tidak ada manajer atau pimpinan proyek yang membagikan tugas. Pengembang secara proaktif membuka kartu cerita teratas dan memilih opsi *Assign Yourself* pada antarmuka perkakas (*GitHub / ZenHub*).
- **Visibilitas Tim dan Manajemen:**
  - Begitu kartu cerita dipindahkan ke saluran *In Progress*, foto profil (*avatar*) pengembang yang bersangkutan akan tersemat secara otomatis pada kartu tersebut.
  - Memberikan transparansi seketika bagi seluruh organisasi: siapa pun dapat melihat tugas apa yang sedang berjalan dan siapa penanggung jawab teknisnya tanpa perlu mengadakan rapat konfirmasi terpisah.

### C. Aturan Emas: Batasan Satu Cerita per Orang (WIP Limit = 1)
Prinsip paling mendasar dalam eksekusi harian *Agile* adalah pembatasan ketat beban kerja dalam proses (*Work in Progress / WIP*):
- **Larangan Multitasking Antar Cerita:**
  - Setiap individu dilarang keras menarik atau mengerjakan lebih dari satu cerita pengguna secara simultan. Munculnya avatar yang sama pada beberapa kartu di kolom *In Progress* merupakan tanda terjadinya pelanggaran alur kerja.
- **Justifikasi Nilai Bisnis:**
  - Organisasi tidak dapat merilis 50% dari dua cerita yang setengah jadi ke tangan pelanggan pada akhir *sprint*.
  - Organisasi hanya dapat merilis dan memperoleh nilai dari 100% dari satu cerita yang tuntas secara fungsional. Mengerjakan satu fitur hingga tuntas sebelum beralih ke fitur berikutnya meminimalkan pemborosan (*waste*) peralihan konteks pikiran (*context switching*).
- **Pengecualian Rintangan (*Blocker Exception*):**
  - Pengembang hanya diizinkan menarik cerita baru jika pekerjaan yang sedang ditanganinya terhenti total akibat hambatan eksternal yang di luar kendalinya, sementara *Scrum Master* berupaya membersihkan hambatan tersebut.

### D. Transisi ke Review / QA dan Otomatisasi Pull Request
- **Penyelesaian Kode dan Pengujian Mandiri:**
  - Setelah pengembang menyelesaikan kode dan memastikan seluruh pengujian otomatis lolos, ia mengajukan permohonan penggabungan kode (*Pull Request / PR*).
- **Otomatisasi ZenHub dan GitHub:**
  - Sistem dapat dikonfigurasi agar pembuatan *Pull Request* yang ditautkan ke sebuah isu *GitHub* secara otomatis memindahkan kartu cerita dari *In Progress* ke saluran *Review / QA*.
- **Tinjauan Sejawat (*Peer Review*):**
  - Keberadaan kartu pada kolom *Review / QA* menjadi sinyal visual bagi rekan pengembang lain untuk menyisihkan waktu menelaah kode (*code review*) dan memvalidasi kriteria penerimaan sebelum kode digabungkan ke cabang utama.

### E. Penyelesaian Teknis pada Saluran Done
- **Penggabungan Cabang (*Merging*):**
  - Setelah *Pull Request* disetujui dan digabungkan (*merged*) ke cabang utama (*main/master*), kartu cerita dipindahkan ke saluran *Done*.
- **Makna Definisi Done bagi Pengembang:**
  - Masuknya cerita ke kolom *Done* menandakan bahwa pengembang telah menyelesaikan seluruh tanggung jawab teknisnya. Penerimaan resmi atas fungsionalitas tersebut akan dilakukan oleh *Product Owner* pada sesi *Sprint Review*.
- **Pengulangan Siklus:**
  - Pengembang kembali ke saluran *Sprint Backlog*, mengambil cerita prioritas tertinggi berikutnya yang tersedia, dan mengulangi siklus yang sama.

---

## 2. Rapat Berdiri Harian (The Daily Stand-Up)

### A. Hakikat, Tempat, Waktu, dan Batas Waktu 15 Menit
*Daily Stand-Up* (sering disebut juga *Daily Scrum*) adalah pertemuan sinkronisasi harian berdurasi pendek bagi tim pengembang:
- **Konsistensi Pelaksanaan:**
  - Pertemuan wajib diselenggarakan pada lokasi fisik (atau tautan daring) yang sama dan pada jam yang sama setiap hari kerja guna membentuk kebiasaan rutin yang terprediksi.
- **Filosofi Berdiri Fisik:**
  - Seluruh peserta diwajibkan berdiri membentuk lingkaran tanpa ada yang duduk. Posisi fisik berdiri secara psikologis mendorong setiap peserta berbicara ringkas, padat, dan langsung pada inti persoalan.
- **Ketegasan Batas Waktu (*Timebox 15 Menit*):**
  - Rapat dibatasi tepat maksimal 15 menit, berapa pun jumlah anggota dalam tim pengembang. Rapat yang berlarut-larut menandakan terjadinya pergeseran tujuan pertemuan.

### B. Dekonstruksi Miskonsepsi: Stand-Up Bukan Laporan Status Proyek
- **Pertemuan Antar Rekan Tim (*Team-to-Team Alignment*):**
  - *Daily Stand-Up* diadakan semata-mata untuk kepentingan internal tim pengembang: memahami kemajuan rekan kerja, mendeteksi potensi konflik kode, dan saling menawarkan bantuan teknis.
- **Bukan Pertanggungjawaban Hierarkis:**
  - Pertemuan ini BUKAN sesi interogasi laporan status kerja bagi manajer proyek, atasan divisi, maupun *Product Owner*. Apabila rapat berubah menjadi sesi pelaporan individual kepada atasan, maka esensi keterbukaan tim akan segera runtuh.

### C. Aturan Partisipasi dan Etika Tiga Peran
1. **Scrum Master (Wajib Hadir):**
   - Mengawal batas waktu 15 menit dan secara proaktif mencatat rintangan yang diungkapkan oleh anggota tim agar dapat segera diselesaikan seusai rapat.
2. **Development Team (Wajib Hadir Penuh):**
   - Seluruh anggota tim pengembang lintas fungsi wajib hadir dan menyampaikan pembaruan tugas secara bergiliran.
3. **Product Owner (Kehadiran Opsional):**
   - Kehadiran PO bersifat opsional untuk mengamati dinamika kerja tim.
   - **Etika Ketat bagi PO:** PO tidak diperkenankan berbicara kecuali dimintai klarifikasi fungsional oleh tim pengembang. PO dilarang memanfaatkan sesi ini untuk menuntut kepastian rilis atau membagi-bagikan tugas baru.

### D. Tiga Pertanyaan Standar Rapat Berdiri
Setiap anggota tim pengembang menjawab tiga pertanyaan secara berurutan dan ringkas:
1. **Apa yang telah saya selesaikan kemarin?**
   - Memberikan visibilitas kepada tim mengenai kemajuan cerita yang sedang ditangani.
2. **Apa yang akan saya kerjakan hari ini?**
   - Mengumumkan rencana kerja hari ini (misalnya: melanjutkan cerita berjalan atau mengambil cerita baru dari *Sprint Backlog*).
3. **Hambatan atau rintangan (*blockers / impediments*) apa yang merintangi kemajuan saya?**
   - Titik paling krusial dalam pertemuan. Apabila seorang pengembang terhalang oleh dependensi sistem, izin akses lingkungan, atau kegagalan server, hal tersebut wajib diumumkan secara transparan.

**Prosedur Tindak Lanjut Hambatan:**
- Mengeliminasi rintangan anggota tim merupakan prioritas kerja tertinggi bagi *Scrum Master* pada hari itu.
- Pengembang yang terhalang tidak boleh berdiam diri; jika penanganan rintangan membutuhkan waktu beberapa jam atau berhari-hari, pengembang segera mengambil tugas lain dari *Sprint Backlog* agar tetap produktif.

### E. Manajemen Topik Tertunda (Tabled Topics / The Parking Lot)
Penyebab utama rapat berdiri melampaui batas waktu 15 menit adalah munculnya perdebatan teknis mendalam saat seseorang menjawab pertanyaan:
- **Konsep Kotak Parkir (*The Parking Lot*):**
  - Setiap pembahasan teknis, usulan solusi arsitektur, atau percakapan yang membutuhkan waktu lebih dari satu menit wajib segera dipotong (*tabled*) dan dicatat ke dalam daftar topik tertunda (*Parking Lot*).
- **Penyelesaian Pasca-Rapat (*Post-Stand-Up Discussion*):**
  - Tepat pada menit ke-15, rapat berdiri resmi ditutup. Anggota tim yang tidak berkepentingan dipersilakan membubarkan diri untuk mulai bekerja.
  - Hanya individu yang terkait langsung dengan topik di *Parking Lot* yang tetap tinggal untuk mendiskusikan solusi teknis secara mendalam.

---

## 3. Rangkuman dan Poin Pembelajaran Kunci

1. **Kedisiplinan Aliran Kanban:** Eksekusi harian berfokus pada penarikan mandiri cerita teratas dari *Sprint Backlog* dengan mematuhi urutan prioritas bisnis.
2. **Prinsip WIP Limit = 1:** Mengerjakan satu cerita pengguna hingga tuntas 100% menghasilkan nilai nyata dan mencegah penumpukan pekerjaan setengah jadi.
3. **Transparansi Visual Menyeluruh:** Pemanfaatan avatar pada kolom *In Progress* serta penautan otomatis *Pull Request* ke kolom *Review / QA* menjaga kelancaran koordinasi tanpa birokrasi manual.
4. **Fokus Murni Daily Stand-Up:** Pertemuan 15 menit dengan posisi berdiri untuk sinkronisasi internal tim pengembang melalui tiga pertanyaan inti, bukan sesi laporan status kepada manajemen.
5. **Efisiensi Melalui Parking Lot:** Melindungi batas waktu 15 menit dengan menunda perdebatan teknis mendalam ke sesi khusus setelah rapat utama dibubarkan.
