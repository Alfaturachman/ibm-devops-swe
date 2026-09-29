# The Agile Planning Process

Dokumen ini memuat rangkuman komprehensif mengenai siklus perencanaan dalam kerangka kerja *Scrum*, mencakup metodologi penyempurnaan simpanan produk (*Backlog Refinement*), prosedur triase isu baru, pelabelan visual utang teknis (*technical debt*), perancangan dan eksekusi pertemuan perencanaan iterasi (*Sprint Planning*), formulasi sasaran iterasi (*Sprint Goal*), serta hakikat metrik kecepatan tim (*Team Velocity*).

---

## 1. Penyempurnaan Backlog (Backlog Refinement)

### A. Definisi dan Tujuan Backlog Refinement
*Backlog Refinement* (sebelumnya dikenal sebagai *Backlog Grooming*) adalah aktivitas berkesinambungan untuk meninjau, menyusun ulang urutan prioritas, dan merinci item-item pada *Product Backlog*:
- **Aktivitas Pokok Refinement:**
  - Menata urutan prioritas cerita pengguna sehingga kebutuhan bisnis paling bernilai berada di peringkat paling atas.
  - Mendekomposisi cerita berukuran besar (*Epics* atau cerita makro) menjadi potongan-potongan kecil yang dapat diselesaikan dalam kurun waktu satu *sprint*.
  - Melengkapi cerita pengguna teratas dengan rincian teknis, asumsi arsitektur, dan kriteria penerimaan yang jelas agar berada dalam kondisi siap dieksekusi (*sprint-ready*).
- **Efisiensi Waktu Perencanaan:**
  - Sesi *Backlog Refinement* bertujuan menyelesaikan perdebatan konseptual dan rincian dokumen sebelum sesi *Sprint Planning* dimulai, sehingga rapat *Sprint Planning* dapat berlangsung singkat dan terfokus tanpa aktivitas pengetikan dokumen yang berkepanjangan.

### B. Partisipan Pertemuan Refinement
Untuk menjaga efisiensi kerja tim pengembang, sesi penyempurnaan *backlog* tidak memerlukan kehadiran seluruh anggota tim secara masif:
- **Product Owner (Wajib Hadir):**
  - Pemilik visi produk yang bertanggung jawab menyusun, menjelaskan, dan menentukan urutan kepentingan cerita berdasarkan pertimbangan bisnis.
- **Scrum Master (Wajib Hadir):**
  - Fasilitator yang mendampingi *Product Owner* dalam menjaga kepatuhan proses *Agile* dan struktur cerita.
- **Perwakilan Tim Pengembang (Opsional / Terbatas):**
  - Cukup dihadiri oleh satu atau dua perwakilan teknis senior, seperti pimpinan pengembang (*development lead*) atau arsitek perangkat lunak. Kehadiran mereka difokuskan untuk menilai kelayakan teknis (*feasibility*) dan mengungkap dependensi arsitektur yang tidak disadari oleh PO. Mengikutsertakan seluruh tim pengembang dipandang sebagai pemborosan waktu rekayasa.

### C. Prosedur Triase Kotak Masuk (New Issue Triage)
Dalam ekosistem dinamis, pelanggan dan pemangku kepentingan akan terus mengajukan permintaan fitur baru yang masuk ke saluran *New Issues* pada papan kerja:
- **Prinsip Pengosongan Kotak Masuk (*Zero Inbox*):**
  - Saluran *New Issues* berfungsi sebagai kotak masuk (*inbox*). Setiap kali sesi *Backlog Refinement* dimulai, aturan utamanya adalah melakukan triase hingga saluran *New Issues* benar-benar kosong (*empty*).
- **Tiga Jalur Keputusan Triase:**
  1. *Dipindahkan ke Product Backlog:* Untuk kebutuhan relevan yang memiliki nilai bisnis mendesak dan direncanakan dieksekusi dalam satu hingga tiga *sprint* mendatang.
  2. *Dipindahkan ke Icebox:* Untuk ide-ide yang baik namun ditujukan bagi masa depan jangka panjang, sehingga tidak mengotori alur kerja aktif tim.
  3. *Ditolak Langsung (Reject out of Hand):* Untuk permintaan yang tidak selaras dengan arah strategis produk (*outside product wheelhouse*).
- **Studi Kasus Triase:**
  - Permintaan *"Kemampuan Menghapus Penghitung"* dialihkan ke *Icebox* karena fitur banyak penghitung (*multiple counters*) belum dibangun.
  - Permintaan *"Penerapan Layanan ke Cloud"* segera dipindahkan ke *Product Backlog* dengan prioritas tinggi agar fondasi infrastruktur siap sebelum penambahan fitur tingkat lanjut.

### D. Pembentukan Cerita yang Siap Dieksekusi (Sprint-Ready)
Sebuah cerita pengguna dinyatakan *sprint-ready* apabila memenuhi standar operasional:
- Telah memuat estimasi bobot kasar (*Rough Order of Magnitude / ROM*).
- Memiliki asumsi teknis yang disepakati (misalnya: fungsionalitas penambahan nilai hitungan dirancang sebagai transaksi tunggal yang atomik).
- Dilengkapi kriteria penerimaan objektif berbasis sintaksis *Gherkin*:
  ```gherkin
  Given nilai penghitung saat ini telah berada pada angka 2
  When pengguna melakukan panggilan untuk mengambil nilai penghitung
  Then sistem harus mengembalikan angka 2 sebagai nilai akhir
  ```

### E. Pemanfaatan Label Visual dan Pengelolaan Utang Teknis
Pelabelan warna pada *GitHub* dan *ZenHub* meningkatkan daya tangkap visual terhadap komposisi beban kerja di papan *Kanban*:
- **Label Standar GitHub:**
  - `bug` (Merah): Menandakan kecacatan fungsional atau bahaya yang mendesak untuk diperbaiki.
  - `enhancement` (Cyan/Biru Muda): Penambahan fitur atau peningkatan fungsional yang bernilai langsung bagi pelanggan.
  - `help wanted` (Hijau): Permintaan bantuan lintas keahlian.
- **Label Kustom Penting: Technical Debt (Kuning):**
  - *Technical Debt* (Utang Teknis) mencakup pembaruan dependensi, refaktor arsitektur kode, optimasi kueri basis data, atau peningkatan keamanan yang tidak menghasilkan fitur kasat mata bagi pemangku kepentingan, namun krusial bagi keberlanjutan sistem.
  - Diberikan warna kuning (*caution*) sebagai pengingat visual agar tim senantiasa menjaga keseimbangan: penumpukan label kuning yang berlebihan pada papan kerja menandakan sistem berada dalam kondisi rentan dan membutuhkan stabilisasi segera.

---

## 2. Perencanaan Sprint (Sprint Planning)

### A. Tujuan dan Partisipan Sprint Planning
*Sprint Planning* adalah pertemuan formal di awal iterasi untuk menentukan komitmen pekerjaan yang akan dieksekusi selama 2 pekan ke depan:
- **Partisipan Wajib (Tiga Peran Inti):**
  - *Product Owner*, *Scrum Master*, dan SELURUH anggota tim pengembang (*cross-functional team*: pengembang, penguji mutu, analis bisnis, dan praktisi operasional/DevOps).
  - Pihak luar atau pemangku kepentingan eksternal dilarang hadir agar tim dapat berdiskusi dan mengambil komitmen secara independen.
- **Luaran Pertemuan (*Output*):**
  - Terbentuknya *Sprint Backlog* yang berisi kumpulan cerita pengguna terencana beserta strategi pencapaiannya.

### B. Peran Krusial Sasaran Sprint (Sprint Goal)
Setiap *sprint* wajib memiliki satu sasaran terpadu (*Sprint Goal*) yang diartikulasikan dengan tegas oleh *Product Owner*:
- **Fungsi Sasaran Sprint:**
  - Memberikan konteks makna bagi tim mengenai nilai bisnis yang sedang diperjuangkan bersama.
  - Berfungsi sebagai kompas pengambil keputusan di tengah masa eksekusi. Saat pengembang bimbang mengenai detail implementasi, mereka merujuk kembali pada *Sprint Goal* guna mencegah rekayasa berlebihan (*over-engineering*) atau penyimpangan fokus (*getting off on a tangent*).

### C. Mekanisme Eksekusi Sprint Planning
Aktivitas perencanaan dipimpin secara otonom oleh tim pengembang:
1. **Penarikan Cerita (*Pulling Stories*):**
   - Tim pengembang mengambil cerita dari urutan teratas *Product Backlog* yang telah dipersiapkan sebelumnya pada sesi *refinement*.
2. **Validasi dan Kesepakatan Story Points:**
   - Tim pengembang memvalidasi kembali bobot cerita. Apabila diperlukan, teknik *Planning Poker* digunakan untuk menyamakan persepsi tingkat kerumitan sebelum angka poin dikunci. Tim pengembang adalah satu-satunya pihak yang berhak menentukan besaran poin karena mereka yang memikul tanggung jawab penyelesaian.
3. **Klarifikasi Pemahaman Teknis:**
   - Memastikan tidak ada tanda tanya teknis yang tertinggal; setiap anggota tim harus memahami alur kerja cerita jika sewaktu-waktu mereka yang bertugas mengeksekusinya.
4. **Batas Penghentian Penarikan Tugas:**
   - Penarikan cerita dari *Product Backlog* wajib dihentikan tepat saat akumulasi total *Story Points* menyamai angka kecepatan tim (*Team Velocity*).

### D. Hakikat dan Dinamika Kecepatan Tim (Team Velocity)
- **Definisi Formal:**
  - *Velocity* adalah kapasitas rata-rata jumlah *Story Points* yang dapat dituntaskan secara penuh oleh sebuah tim dalam satu siklus *sprint*.
- **Karakteristik Metrik:**
  - *Velocity* bersifat dinamis; nilainya akan bertumbuh dan stabil seiring meningkatnya kematangan kolaborasi serta ketepatan estimasi tim.
- **Larangan Mutlak: Membandingkan Velocity Antar Tim:**
  - Kecepatan adalah metrik personal internal tim (*velocity is a personal thing*).
  - Tim A mungkin menetapkan cerita tingkat *Medium* sebesar 2 poin, sedangkan Tim B menetapkan cerita setara sebagai 5 poin. Tim yang menggunakan angka deret lebih besar akan tampak memiliki *velocity* lebih tinggi di atas kertas, meskipun volume pekerjaan riil yang diselesaikan sama atau bahkan lebih rendah.
  - Membandingkan *velocity* antar tim merupakan tindakan manipulatif dan tidak valid secara statistik.

### E. Konfigurasi Milestone dan Sprint pada Perkakas
Dalam implementasi perkakas (*GitHub / ZenHub*), pembuatan iterasi diatur melalui fitur *Milestones* atau *Sprints*:
- **Judul Singkat dan Padat:**
  - Beri nama yang ringkas agar mudah terbaca pada menu tarik-turun (*dropdown list*), contoh: `Sprint 1: Single Counter`.
- **Deskripsi Sasaran:**
  - Kolom deskripsi wajib diisi dengan rumusan *Sprint Goal* sebagai pengingat utama sasaran kerja.
- **Durasi Waktu Tetap (*Timebox*):**
  - Durasi iterasi dikunci tepat 2 pekan kalender untuk menjaga ritme kerja yang stabil dan dapat diprediksi.

---

## 3. Rangkuman dan Poin Pembelajaran Kunci

1. **Backlog Refinement sebagai Mesin Penyelaras:** Menata prioritas, memecah cerita makro, dan menyiapkan cerita *sprint-ready* sebelum perencanaan formal dimulai.
2. **Disiplin Triase Kotak Masuk:** Mengosongkan saluran *New Issues* pada setiap sesi penyempurnaan dengan memilah item ke *Product Backlog*, *Icebox*, atau menolaknya secara tegas.
3. **Kewaspadaan terhadap Utang Teknis:** Mengidentifikasi pekerjaan perbaikan infrastruktur dan arsitektur melalui label visual khusus (*technical debt*) guna mencegah akumulasi kerapuhan sistem.
4. **Sentralitas Sasaran Sprint:** *Sprint Goal* memandu tim pengembang agar tetap terarah pada penghantaran nilai tanpa terjebak dalam jebakan *over-engineering*.
5. **Independensi Metrik Velocity:** *Velocity* berfungsi sebagai alat ukur kapasitas internal tim untuk perencanaan beban kerja, bukan sebagai alat evaluasi komparatif performa antar tim.
