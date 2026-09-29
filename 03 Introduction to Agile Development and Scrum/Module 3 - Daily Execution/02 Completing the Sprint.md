# Completing the Sprint and Retrospectives

Dokumen ini memuat rangkuman komprehensif mengenai aktivitas penutupan siklus *sprint*, pemantauan laju penyelesaian tugas menggunakan diagram *Burndown Chart*, pelaksanaan sesi demonstrasi fungsional pada *Sprint Review*, strategi penanganan cerita yang ditolak demi menjaga keakuratan metrik kecepatan (*velocity*), serta tata cara memfasilitasi sesi refleksi tim pada *Sprint Retrospective*.

---

## 1. Pemantauan Kemajuan dengan Diagram Burndown (Burndown Charts)

### A. Definisi dan Fungsi Diagram Burndown
*Burndown Chart* adalah alat visual grafis yang digunakan dalam kerangka kerja *Scrum* untuk melacak sisa beban kerja (*story points*) terhadap sisa waktu dalam satu siklus iterasi:
- **Prinsip Dasar:**
  - Menampilkan perbandingan antara jumlah bobot poin yang telah diselesaikan dengan sisa bobot poin yang masih harus diselesaikan seiring berjalannya waktu.
  - Memungkinkan tim pengembang memproyeksikan secara cepat apakah mereka berada pada jalur yang tepat (*on track*) untuk mencapai sasaran iterasi (*Sprint Goal*).
- **Fleksibilitas Penggunaan:**
  - Meskipun umumnya diterapkan pada iterasi *sprint* 2 pekan, diagram *Burndown* dapat dimanfaatkan untuk memantau pencapaian tonggak capaian (*milestone*) apa pun, seperti persiapan demonstrasi konferensi atau peluncuran rilis utama.

### B. Anatomi Sumbu dan Garis Ideal (The Ideal Path)
Struktur grafik *Burndown* memuat komponen pengukuran baku:
- **Sumbu Vertikal (Y):** Menunjukkan akumulasi total *Story Points* yang direncanakan dalam *sprint* tersebut.
- **Sumbu Horizontal (X):** Menunjukkan rentang hari kerja kalender dalam siklus *sprint* (misalnya 10 hari kerja dalam durasi 2 pekan).
- **Area Bayangan Akhir Pekan (*Weekends*):**
  - Ditandai dengan batas vertikal khusus. Perhitungan ideal tidak memperhitungkan akhir pekan sebagai waktu kerja guna mencegah kelelahan tim (*burnout*).
- **Garis Ideal (Optimal Path):**
  - Garis diagonal menurun yang ditarik dari total poin di hari pertama menuju angka 0 di hari terakhir *sprint*, memproyeksikan laju pembakaran beban kerja yang konstan dan merata.

### C. Pembacaan Garis Progres Riil dan Mitigasi Deviasi
- **Garis Progres Aktual:**
  - Garis aktual (biasanya berwarna biru) diperbarui setiap kali sebuah cerita ditutup atau dipindahkan ke saluran *Done*.
- **Pendeteksian Keterlambatan:**
  - Jika garis aktual berada di atas garis ideal, hal ini menandakan bahwa sisa beban kerja yang belum selesai lebih tinggi dari proyeksi teoritis (tim mengalami ketertinggalan jadwal).
- **Tindakan Penyelarasan:**
  - Tim pengembang menggunakan visualisasi ini untuk segera merapatkan barisan, memecahkan hambatan bersama *Scrum Master*, atau memfokuskan tenaga bersama pada cerita prioritas tertinggi sebelum masa *sprint* berakhir.
- **Sasaran Pengguna Utama:**
  - Diagram *Burndown* dirancang terutama sebagai instrumen navigasi internal bagi tim pengembang itu sendiri, bukan semata-mata laporan kepatuhan bagi manajemen puncak.

---

## 2. Demonstrasi Hasil pada Tinjauan Sprint (The Sprint Review)

### A. Hakikat Pertemuan "Demo Time"
*Sprint Review* diselenggarakan pada akhir masa *sprint* setelah seluruh pekerjaan teknis selesai diintegrasikan:
- **Waktu Unjuk Kinerja Tim (*Showcase Time*):**
  - Merupakan sesi demonstrasi langsung (*live demo*) di mana tim pengembang memperlihatkan fungsionalitas baru yang berhasil dibangun dan diuji selama 2 pekan terakhir.
- **Validasi Terhadap Kriteria Penerimaan:**
  - *Product Owner* menguji secara langsung apakah fungsionalitas yang disajikan telah memenuhi definisi selesai (*Definition of Done*) dan kriteria penerimaan yang telah disepakati sebelumnya.
  - Cerita yang lolos verifikasi secara resmi dipindahkan dari kolom *Done* ke kolom *Closed*.

### B. Partisipan Pertemuan: Keterbukaan Penuh
Berbeda dengan pertemuan internal lainnya, *Sprint Review* terbuka bagi khalayak luas:
- **Daftar Undangan:**
  - *Product Owner*, *Scrum Master*, seluruh anggota tim pengembang, pemangku kepentingan (*stakeholders*), perwakilan pengguna akhir (*customers*), hingga pimpinan divisi.
  - Siapa pun yang berkepentingan terhadap arah perkembangan produk dipersilakan hadir untuk menyaksikan demonstrasi.

### C. Konversi Umpan Balik Menjadi Nilai Produk Baru
- **Katalis Inovasi Berkelanjutan:**
  - Keberhasilan terbesar model iteratif terletak pada umpan balik spontan pemangku kepentingan saat melihat perangkat lunak bekerja secara nyata.
  - Sering kali pemangku kepentingan baru menyadari kebutuhan fitur baru yang bernilai tinggi setelah melihat demonstrasi prototipe fungsional, sesuatu yang mustahil terpicu pada pembacaan dokumen spesifikasi kaku model *Waterfall*.
- **Tindak Lanjut Umpan Balik:**
  - Seluruh ide, masukan, dan saran penyesuaian yang muncul selama demonstrasi segera dicatat oleh *Product Owner* untuk dikonversi menjadi cerita-cerita pengguna baru di dalam *Product Backlog*.

### D. Protokol Penanganan Cerita yang Ditolak (Rejected Stories)
Ketika *Product Owner* menyatakan bahwa suatu cerita tidak dapat diterima (*rejected*) karena tidak sesuai dengan harapan bisnis:
- **Larangan Menggeser Cerita ke Sprint Berikutnya:**
  - Jangan memindahkan cerita yang ditolak begitu saja ke *sprint* berikutnya. Praktik tersebut merusak akurasi pelacakan metrik kecepatan (*velocity*).
- **Justifikasi Perhitungan Velocity:**
  - Pengembang telah mencurahkan waktu dan usaha nyata untuk mengimplementasikan cerita tersebut (misalnya berbobot 8 poin). Jika cerita dipindahkan tanpa ditutup, maka 8 poin usaha tersebut hilang dari catatan kapasitas historis tim pada *sprint* berjalan.
- **Solusi Baku Pengelolaan:**
  1. Berikan label penjelas pada cerita tersebut (misalnya label `unfinished` atau `inaccurate`).
  2. Tutup (*close*) cerita tersebut pada *sprint* berjalan agar kredit *Story Points* tetap tercatat dalam *velocity* tim.
  3. Buka cerita pengguna baru di dalam *Product Backlog* yang memuat kriteria penerimaan yang telah diperbaiki sesuai keinginan *Product Owner*, untuk diprioritaskan pada perencanaan *sprint* mendatang.

---

## 3. Refleksi dan Perbaikan Berkelanjutan (The Sprint Retrospective)

### A. Tujuan dan Pengukuran Kesehatan Proses
*Sprint Retrospective* diselenggarakan sebagai agenda penutup dari seluruh rangkaian *sprint*:
- **Pemeriksaan Kesehatan Tim (*Health Check*):**
  - Berfokus pada peninjauan proses kerja, efektivitas perkakas, dan dinamika interaksi antar manusia, bukan membahas fitur perangkat lunak.
- **Fondasi Peningkatan Berkesinambungan (*Kaizen*):**
  - Memberikan ruang evaluasi berkala agar tim dapat berevolusi menjadi tim berkinerja tinggi (*high-performing team*).

### B. Aturan Partisipasi: Alasan Product Owner Tidak Diundang
- **Partisipan Wajib:** *Scrum Master* dan seluruh anggota tim pengembang.
- **Alasan Pengecualian Product Owner:**
  - Tim pengembang membutuhkan lingkungan psikologis yang sepenuhnya aman untuk berbicara bebas tanpa rasa takut (*psychological safety*).
  - Pengembang harus dapat menyampaikan kendala secara terus terang, termasuk jika terdapat tekanan berlebihan atau ekspektasi yang tidak realistis dari pihak *Product Owner*, tanpa khawatir memicu penilaian personal negatif.
  - Pengecualian hanya berlaku jika tim telah memiliki tingkat kematangan emosional dan transparansi komunikasi yang sangat tinggi dengan PO.

### C. Tiga Pertanyaan Pokok Retrospeksi
Dalam sesi refleksi, seluruh peserta menjawab tiga pertanyaan kunci:
1. **Apa yang telah berjalan dengan baik? (*What did we do well?*):**
   - Mengidentifikasi praktik positif, pola kolaborasi efektif, atau teknik pengujian yang berhasil, untuk terus dipertahankan (*keep doing*).
2. **Apa yang tidak berjalan dengan baik? (*What did not go well?*):**
   - Mengungkapkan gesekan komunikasi, kegagalan infrastruktur, dependensi yang lambat, atau kebiasaan buruk yang harus dihentikan (*stop doing*).
3. **Perubahan konkret apa yang harus kita lakukan? (*What should we change?*):**
   - Merumuskan rencana tindakan perbaikan nyata untuk diterapkan pada siklus berikutnya.

### D. Akuntabilitas Tindak Lanjut oleh Scrum Master
- **Mencegah Jebakan Sesi Keluhan (*Gripe Session*):**
  - Retrospeksi tidak boleh dibiarkan menjadi ajang keluhan tanpa jalan keluar.
- **Fasilitasi Rencana Aksi (*Action Items*):**
  - *Scrum Master* mendokumentasikan poin-poin perbaikan dan memilih satu atau dua isu paling krusial untuk dipastikan penerapannya pada *sprint* berikutnya.
  - Perubahan nyata yang dirasakan oleh anggota tim menumbuhkan keyakinan bahwa suara mereka dihargai dan proses kerja terus bergerak ke arah yang lebih baik.

---

## 4. Rangkuman dan Poin Pembelajaran Kunci

1. **Visibilitas Progres Lewat Burndown:** Diagram *Burndown* menyajikan komparasi sisa beban kerja terhadap waktu guna memprediksi pencapaian *Sprint Goal* secara mandiri oleh tim pengembang.
2. **Nilai Strategis Sprint Review:** Sesi unjuk kerja fungsional (*live demo*) bersama seluruh pemangku kepentingan yang mengubah umpan balik langsung menjadi inisiatif cerita baru di *Product Backlog*.
3. **Integritas Metrik Kecepatan:** Cerita yang ditolak wajib diberi label dan ditutup pada *sprint* berjalan untuk menjaga catatan *velocity* tetap akurat, kemudian dilanjutkan melalui pembuatan cerita baru di *backlog*.
4. **Keamanan Psikologis Retrospeksi:** Sesi evaluasi proses internal yang membatasi kehadiran *Product Owner* demi menjamin kebebasan berpendapat dan transparansi evaluasi tim pengembang.
5. **Komitmen Aksi Perbaikan:** Keberhasilan *Sprint Retrospective* diukur dari terwujudnya perubahan nyata pada proses operasional di *sprint* berikutnya, bukan dari banyaknya keluhan yang dicatat.
