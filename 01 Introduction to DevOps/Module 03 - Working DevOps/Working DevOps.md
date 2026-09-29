# Working DevOps

Dokumen ini menyajikan rangkuman komprehensif mengenai transformasi cara kerja dalam DevOps, mengupas pergeseran dari Taylorisme dan analogi teknik sipil menuju kepemilikan produk terintegrasi, perilaku kolaboratif Dev dan Ops, otomatisasi infrastruktur berbasis kode (*Infrastructure as Code*), serta implementasi terperinci dari *Continuous Integration* dan *Continuous Delivery* (CI/CD).

---

### 1. Taylorism and Working in Silos

#### A. Konsep Taylorisme dan Manajemen Komando
- **Asal-Usul Manajemen Ilmiah:**
  - Diprakarsai oleh insinyur industri Amerika Serikat, Frederick Winslow Taylor, melalui buku *Principles of Scientific Management* (1911).
  - Taylor merancang metode manajemen lini perakitan pabrik manufaktur massal pada era Revolusi Industri, yang melahirkan model manajemen komando dan kendali (*command-and-control*).
- **Pemisahan Pemikiran dari Eksekusi:**
  - Taylorisme membagi organisasi ke dalam silo-silo fungsional yang terisolasi.
  - Pengambilan keputusan dipisahkan secara kaku dari pekerjaan fisik (*decision-making separated from work*): manajer bertugas memikirkan dan merencanakan pekerjaan, sedangkan buruh pabrik hanya mengeksekusi instruksi secara mekanis tanpa ruang inisiatif.
- **Dampak Negatif pada Teknologi Informasi:**
  - Struktur TI tradisional meniru hierarki Taylorisme: Manajer Proyek berada di puncak komando, memberi instruksi kepada arsitek; arsitek merancang cetak biru dan menyerahkannya ke pengembang (*developers*); pengembang menyerahkan kode ke penguji (*testers*); penguji menyerahkan ke tim operasional (*operations*); dan tim operasional menyerahkan ke tim keamanan (*security*).
  - Setiap titik serah terima antarruang kerja (*handoffs across silos*) menjadi sumber utama kesalahpahaman, distorsi konteks, penundaan, dan kemacetan alur kerja (*bottlenecks*).

#### B. Rekayasa Perangkat Lunak: Kriya Kustom vs Lini Perakitan
- **Komponen Standar vs Pekerjaan Kriya (*Craftwork*):**
  - Pada lini perakitan otomotif, mobil dibangun dari ribuan suku cadang standar yang telah diproduksi massal ratusan ribu unit, sehingga investasi perakitan kaku (*tooling*) sangat menguntungkan.
  - Dalam rekayasa perangkat lunak, komponen yang dibangun umumnya belum pernah ada sebelumnya. Jika sudah tersedia, industri akan langsung membeli pustaka jadi (*off-the-shelf*).
  - Menulis kode perangkat lunak adalah pekerjaan berbasis pengetahuan (*knowledge work*) dan bersifat kriya kustom (*bespoke / craftwork*). Membangun lini perakitan pabrik yang kaku hanya untuk menghasilkan satu produk unik adalah kesalahan mendasar.
- **Filosofi Manajemen Modern:**
  - Mengutip pandangan Steve Jobs: *"Tidak masuk akal mempekerjakan orang-orang pintar lalu mendikte apa yang harus mereka kerjakan; kita merekrut orang pintar agar mereka memberi tahu kita apa yang harus dilakukan."*
  - Manajemen harus meninggalkan pendekatan komando, memercayai kompetensi tim, mengomunikasikan sasaran hasil, lalu menyingkirkan hambatan birokrasi agar tim dapat berinovasi secara optimal.

---

### 2. Software Engineering vs. Civil Engineering

#### A. Analogi Proyek Teknik Sipil
- **Alur Kerja Pembangunan Gedung:**
  - Dalam proyek teknik sipil (seperti pembangunan gedung perkantoran), pemilik proyek mempekerjakan arsitek untuk membuat cetak biru (*blueprint*).
  - Cetak biru diserahkan ke kontraktor konstruksi yang membangun gedung selama berbulan-bulan sesuai spesifikasi kaku.
  - Setelah serah terima, arsitek beralih ke proyek lain. Gedung yang telah berdiri diserahkan kepada tim pemeliharaan fasilitas (*facility maintenance*).
  - Struktur fisik gedung dan tanah tempat berpijak bersifat statis dan permanen: tidak ada penambahan lantai baru secara mendadak setelah konstruksi rampung.

#### B. Mengapa Model Proyek Sipil Gagal dalam Perangkat Lunak
- **Sifat Organik Perangkat Lunak:**
  - Berbeda dengan gedung fisik, tumpukan teknologi perangkat lunak (*software stack*) di bawah aplikasi bersifat dinamis dan terus berubah (*organic*).
  - Sistem operasi secara rutin menerima tambalan keamanan (*security patches*) dan dependensi pustaka diperbarui untuk menutup celah kerentanan baru, meskipun kode inti aplikasi tidak dimodifikasi.
- **Kerapuhan Model "Lempar Kode Melewati Tembok" (*Throwing over the Wall*):**
  - Arsitek melempar desain ke pengembang lalu pergi ke proyek lain; pengembang melempar kode ke tim penguji; tim penguji melempar hasil ke tim operasional.
  - Setelah proyek selesai, tim dibubarkan dan dialihkan ke proyek baru, hanya menyisakan segelintir personel operasional untuk pemeliharaan rutin.
  - Ketiadaan rasa kepemilikan (*lack of ownership*) menyebabkan hilangnya pemahaman mendalam terhadap basis kode, memicu frustrasi dan tingginya biaya pemeliharaan saat terjadi anomali sistem.

#### C. Paradigma Produk vs Paradigma Proyek
- **Transisi Menuju Kepemilikan Produk (*Product Ownership*):**
  - DevOps menuntut penghentian perlakuan rekayasa perangkat lunak sebagai proyek sementara (*project model*).
  - Pengembangan perangkat lunak harus diposisikan sebagai siklus pengembangan produk (*product development*) yang memiliki rentang hidup panjang.
- **Tim Stabil dan Langgeng (*Stable, Long-Lasting Teams*):**
  - Membentuk tim stabil lintas fungsi dengan kepemilikan ujung ke ujung (*end-to-end ownership*). Tim yang merancang dan menulis kode adalah tim yang sama yang bertanggung jawab mengoperasikan dan memeliharanya di lingkungan produksi (*you build it, you run it*).

---

### 3. Required DevOps Behaviors and Culture Alignment

#### A. Benturan Budaya: Tradisional Ops vs DevOps
Pendekatan korporasi konvensional memandang setiap perubahan sebagai ancaman kompleks, mahal, dan berisiko tinggi. DevOps membalikkan paradigma tersebut dengan memecah pekerjaan besar menjadi serangkaian perubahan kecil yang dapat dikelola secara aman.

Perbedaan fundamental antara operasional tradisional dan DevOps mencakup:
- **Metode Konfigurasi Sistem:**
  - Tradisional Ops: Melakukan modifikasi konfigurasi infrastruktur kritis secara manual, sehingga memerlukan badan peninjau perubahan (*Change Review Board* / CRB) yang lambat.
  - DevOps: Mengotomatiskan seluruh alur penerapan kode dan konfigurasi ke seluruh tingkatan lingkungan secara konsisten.
- **Hubungan Aplikasi dan Jaringan:**
  - Tradisional Ops: Arsitektur aplikasi dibatasi dan ditentukan oleh desain fisik jaringan.
  - DevOps: Desain jaringan disesuaikan secara fleksibel mengikuti kebutuhan arsitektur aplikasi melalui jaringan berbasis perangkat lunak (*software-defined networking*).
- **Siklus Hidup Server:**
  - Tradisional Ops: Infrastruktur unik (*snowflake servers*) dibangun sekali secara manual lalu dirawat selamanya.
  - DevOps: Infrastruktur fana (*ephemeral infrastructure*) dibangkitkan otomatis saat dibutuhkan dan langsung dihancurkan saat selesai digunakan.
- **Pengelolaan Risiko Rilis:**
  - Tradisional Ops: Membatasi perubahan hanya pada jendela waktu tertentu (*change windows*), biasanya di tengah malam pada akhir pekan.
  - DevOps: Mengelola risiko melalui aktivasi bertahap (*progressive activation*), memungkinkan penerapan perubahan kapan saja di siang hari tanpa gangguan layanan.
- **Pola Pembangunan Sistem:**
  - Tradisional Ops: Berorientasi pada pembangunan sekali (*build once*) yang kerap tidak terdokumentasi dengan baik sehingga sulit direproduksi.
  - DevOps: Proses dirancang untuk keluaran berkecepatan tinggi dengan proses pembangunan berulang yang identik (*repeatable builds*) melalui *Infrastructure as Code* (IaC).

#### B. Tembok Kebingungan (*The Wall of Confusion*)
- **Perbedaan Metrik Penilaian Kinerja:**
  - Pengembang diukur berdasarkan volume inovasi: seberapa cepat mereka merilis fitur dan kapabilitas baru bagi pengguna.
  - Tim operasional diukur berdasarkan stabilitas: menjaga sistem tetap menyala, meminimalkan gangguan, dan mengamankan data.
  - Andrew Clay Shafer menyebut kebuntuan ini sebagai Tembok Kebingungan (*wall of confusion*). Kedua tujuan saling bertolak belakang: inovasi menuntut perubahan, sedangkan stabilitas menolak perubahan.
- **Prasangka Buruk Antarsilo:**
  - Tim operasional menganggap pengembang kerap melemparkan masalah ke seberang tembok (*throwing dead cats over the wall*) dengan kode yang minim pengujian dan tanpa rencana pembatalan (*back-out plan*).
  - Pengembang menganggap tim operasional bekerja lambat, kaku, dan hanya menyalin instruksi dari buku panduan manual (*runbooks*).
  - Jika situs web berjalan lancar, pengembang mendapat pujian; jika situs web tumbang, tim operasional yang disalahkan. Kondisi ini menciptakan lingkungan kerja tanpa pemenang (*no-win scenario*).

#### C. Transformasi Perilaku yang Wajib Diterapkan
- **1. Dari Silo Menuju Kepemilikan Bersama (*Shared Ownership*):**
  - Seluruh anggota tim berada di perahu yang sama; tidak ada konsep "kebocoran hanya terjadi di sisi perahumu". Seluruh tim memiliki tujuan bersama yang berorientasi pada kepuasan pelanggan.
- **2. Dari Takut Berubah Menuju Merangkul Perubahan (*Embracing Change*):**
  - Mengelola risiko dengan memperkecil ukuran perubahan, bukan dengan menghentikan atau menunda perubahan.
- **3. Dari Server Unik Menuju Infrastruktur Fana Berbasis Kode:**
  - Menghilangkan *snowflake servers* dan beralih ke penyediaan infrastruktur yang dapat direproduksi secara identik setiap saat.
- **4. Dari Antrean Tiket Menuju Layanan Mandiri Otomatis (*Automated Self-Service*):**
  - Menghapus antrean birokrasi manual; pengembang dapat menyediakan lingkungan komputasi awan yang terstandarisasi secara mandiri dalam hitungan menit.
- **5. Dari Eskalasi Reaktif Menuju Umpan Balik Berbasis Data:**
  - Mengganti rantai eskalasi panggilan darurat manual dengan sistem pemantauan telemetri otomatis yang menyajikan data performa secara waktu nyata.

---

### 4. Infrastructure as Code and Immutable Delivery

#### A. Definisi dan Konsep Dasar IaC
- **Format Tekstual yang Dapat Dieksekusi:**
  - *Infrastructure as Code* (IaC) adalah praktik mendefinisikan dan mengelola konfigurasi infrastruktur dalam bentuk berkas teks terstruktur yang dapat dieksekusi secara otomatis oleh komputer (*executable code*), bukan sekadar dokumen panduan manual.
  - Alat manajemen konfigurasi populer mencakup Ansible, Puppet, dan Chef, serta teknologi deklaratif seperti Terraform, Docker, Vagrant, dan Kubernetes.
- **Integrasi dengan Sistem Kendali Versi (*Version Control*):**
  - Seluruh berkas definisi infrastruktur disimpan di repositori Git. Hal ini memungkinkan pelacakan riwayat perubahan, peninjauan kode (*code review*), pengujian otomatis, serta audit kepatuhan konfigurasi.

#### B. Mengatasi Pergeseran Konfigurasi (*Server Drift*)
- **Bahaya Modifikasi Manual:**
  - Perubahan manual langsung pada server menyebabkan konfigurasi server menyimpang dari kondisi aslinya (*server drift*).
  - Akumulasi perubahan tersembunyi antarteknisi memicu kegagalan sistem yang sulit diisolasi dan menyebabkan server-server yang seharusnya identik berperilaku berbeda.
- **Prinsip Ternak vs Hewan Peliharaan (*Cattle, Not Pets*):**
  - **Pets (Hewan Peliharaan):** Diberi nama khusus, dirawat dengan perhatian ekstra, dan diobati secara telaten saat jatuh sakit.
  - **Cattle (Hewan Ternak):** Diberi penanda identifikasi standar; jika satu ekor sakit, ia segera digantikan dengan yang sehat demi melindungi kawanan.
  - Teknisi tidak boleh memperlakukan server seperti hewan peliharaan dengan menghabiskan waktu berjam-jam melakukan perbaikan manual di lingkungan produksi. Server yang bermasalah harus segera dihancurkan dan diganti dengan instans identik baru yang sehat.

#### C. Infrastruktur Fana dan Rilis Paralel
- **Infrastruktur Transien (*Ephemeral Infrastructure*):**
  - Lingkungan kerja (seperti lingkungan pengujian) hanya diaktifkan saat diperlukan dan langsung dihapus saat pengujian rampung, menghemat biaya komputasi secara signifikan.
- **Penerapan Lingkungan Paralel (*Blue-Green Deployment*):**
  - Tim membangun infrastruktur baru yang identik berdampingan dengan infrastruktur produksi aktif.
  - Setelah versi baru divalidasi dan berjalan normal, pengalihan lalu lintas jaringan dipindahkan ke lingkungan baru, dan lingkungan lama dinonaktifkan tanpa menimbulkan *downtime*.

#### D. Pengiriman Kekal (*Immutable Delivery*) Melalui Docker
- **Dockerfile sebagai Cetak Biru:**
  - Berkas `Dockerfile` mendefinisikan tumpukan dependensi, sistem operasi dasar, dan konfigurasi runtime aplikasi. Setiap kontainer yang dibangun dari *image* tersebut dijamin identik 100%.
- **Paritas Pengembangan dan Produksi (*Dev-Prod Parity*):**
  - Kontainer yang dijalankan di laptop pengembang memiliki perilaku yang sama persis dengan kontainer yang berjalan di klaster Kubernetes produksi.
- **Larangan Menambal Kontainer Aktif:**
  - Dilarang keras melakukan *patching* atau modifikasi konfigurasi langsung di dalam kontainer yang sedang berjalan.
  - Setiap perubahan wajib dilakukan dengan memperbarui berkas `Dockerfile`, membangun ulang *image*, dan menerapkan ulang kontainer baru (*immutable containers*).
- **Pembaruan Bergulir (*Rolling Updates*) dan Pembatalan Instan (*Instant Rollback*):**
  - Jika kontainer versi baru mengalami kendala performa, sistem dapat mematikan kontainer tersebut dan menyalakan kembali kontainer versi sebelumnya dalam hitungan detik.

---

### 5. Continuous Integration (CI)

#### A. Definisi dan Esensi Continuous Integration
- **Dua Praktik yang Berbeda:**
  - Istilah CI/CD kerap diucapkan seolah-olah merupakan satu kesatuan tunggal. Sejatinya, *Continuous Integration* dan *Continuous Delivery* adalah dua praktik terpisah yang saling melengkapi.
- **Definisi CI:**
  - Praktik pengembangan perangkat lunak di mana setiap pengembang secara berkala mengintegrasikan perubahan kodenya ke cabang utama (*main/master branch*) dalam repositori bersama.
  - Setiap integrasi secara otomatis diverifikasi oleh proses pembangunan (*automated build*) dan serangkaian pengujian (*automated tests*) guna memastikan integritas sistem tetap terjaga.
  - Menghasilkan basis kode yang selalu berada dalam kondisi siap diterapkan (*potentially deployable code*).

#### B. Jebakan Cabang Panjang Tradisional vs Cabang Fitur Singkat
- **Kelemahan Tradisional:**
  - Pada masa lalu, pembuatan cabang (*branching*) di sistem kendali versi lama membutuhkan duplikasi berkas penuh dan berbiaya mahal, sehingga tim mempertahankan cabang pengembangan berumur panjang (*long-lived development branches*).
  - Cabang yang terpisah selama berminggu-minggu mengalami divergensi ekstrem dari cabang utama. Saat proses penggabungan (*merge*) dilakukan, tim menghadapi konflik penggabungan masif (*merge hell*) yang membutuhkan waktu berhari-hari untuk diperbaiki.
- **Alur Kerja CI Modern:**
  - Git menyediakan pencabangan yang sangat ringan. Pengembang bekerja pada cabang fitur berumur pendek (*short-lived feature branches*) yang segera digabungkan ke cabang utama setelah fitur selesai dan lolos uji.
  - Aturan emas frekuensi integrasi:

$$\text{Frekuensi Integrasi} \ge 1 \text{ kali per hari per pengembang}$$

  - Semakin sering kode diintegrasikan dalam ukuran kecil (*small batches*), semakin kecil risiko terjadinya konflik penggabungan.

#### C. Praktik Terbaik Implementasi CI
- **1. Disiplin Pull Request dan Peninjauan Kode:**
  - Setiap perubahan diajukan melalui *Pull Request* (PR) yang menjadi sarana komunikasi tim dan peninjauan mutu kode (*code review*) oleh minimal satu rekan kerja.
- **2. Otomatisasi Pembangunan Mandiri (*Self-Testing Build*):**
  - Perkakas CI (seperti Jenkins, GitHub Actions, Travis CI, atau CircleCI) memantau repositori secara otomatis, mendeteksi setiap PR, lalu memicu proses pembangunan dan pengujian unit tanpa intervensi manual.
- **3. Larangan Menggabungkan Kode Gagal:**
  - Dilarang keras menggabungkan PR yang memiliki pengujian berstatus merah (gagal).
- **4. Cabang Utama Wajib Selalu Siap Diterapkan:**
  - Cabang utama (*master/main*) harus selalu berada dalam kondisi stabil dan siap dirilis setiap saat. Kode yang belum diuji secara otomatis wajib dianggap sebagai kode yang belum berfungsi (*untested code is broken code*).

---

### 6. Continuous Delivery (CD)

#### A. Definisi dan Landasan Filosofis
- **Definisi Martin Fowler:**
  - *Continuous Delivery* adalah disiplin rekayasa perangkat lunak di mana tim membangun perangkat lunak sedemikian rupa sehingga kode dapat dirilis ke lingkungan produksi kapan saja secara aman dan cepat.
- **Hubungan CI dan CD:**
  - *Continuous Delivery* mutlak membutuhkan *Continuous Integration*. Tanpa pengujian dan pembangunan otomatis pada setiap integrasi kode, organisasi tidak akan memiliki kepastian apakah kode tersebut aman untuk dirilis ke produksi.
- **Pengiriman ke Lingkungan Serupa Produksi (*Production-Like Environment*):**
  - CD memvalidasi setiap perubahan pada lingkungan bertingkat (pengembangan, pengujian, pemanggungan/*staging*) yang arsitektur dan konfigurasinya identik dengan lingkungan produksi riil.
- **Perbedaan Continuous Delivery vs Continuous Deployment:**
  - **Continuous Delivery:** Perubahan kode secara otomatis diuji, dibangun, dan diterapkan hingga lingkungan pra-produksi. Peluncuran ke produksi siap dilakukan kapan saja melalui satu persetujuan bisnis manual (*manual trigger / push-button*).
  - **Continuous Deployment:** Setiap perubahan yang berhasil melewati gerbang pengujian otomatis langsung diterapkan secara otomatis ke lingkungan produksi tanpa intervensi manusia sama sekali.

#### B. Anatomi Pipa CI/CD (*CI/CD Pipeline*)
Pipa rilis otomatis menghubungkan berbagai perkakas di mana luaran dari satu tahapan menjadi masukan bagi tahapan berikutnya:
- **1. Repositori Kode Sumber (*Code Repository*):**
  - Mengelola seluruh kode aplikasi dan konfigurasi (contoh: GitHub, GitLab).
- **2. Server Pembangun (*Build Server*):**
  - Menyediakan lingkungan komputasi untuk mengompilasi dan mengemas kode sumber.
- **3. Server Integrasi dan Orkestrasi (*Integration Server / Orchestrator*):**
  - Mengotomatiskan rangkaian eksekusi uji unit, uji integrasi, pemindaian keamanan statis, dan verifikasi kualitas (contoh: GitHub Actions, Tekton, Jenkins).
- **4. Repositori Artefak (*Artifact Repository*):**
  - Menyimpan biner hasil kompilasi yang telah teruji (contoh: paket JAR/WAR, paket pustaka Python/Ruby, atau kontainer *Docker images*).
- **5. Perkakas Otomatisasi Penerapan (*Deployment Tool*):**
  - Mengonfigurasi dan menyebarkan artefak ke lingkungan target secara otomatis.

Pemetaan alur siklus hidup pengembangan perangkat lunak (SDLC) terbagi menjadi:
- **Siklus Continuous Integration:** Mencakup fase *Plan*, *Code*, *Build*, dan *Test*.
- **Siklus Continuous Delivery:** Mencakup fase *Release*, *Deploy*, dan *Operate*.

#### C. Lima Prinsip Utama Continuous Delivery
- **1. Kualitas Terpasang Sejak Awal (*Built-in Quality*):**
  - Pipa otomatis melakukan serangkaian pengujian ketat sejak awal alur kerja untuk mencegah cacat merembet ke tahap hilir.
- **2. Bekerja dalam Kelompok Kecil (*Working in Small Batches*):**
  - Memecah rilis menjadi komponen-komponen kecil guna mempermudah isolasi galat dan meminimalkan dampak risiko kegagalan.
- **3. Otomatisasi Pekerjaan Repetitif:**
  - Komputer sangat andal dalam melakukan tugas berulang secara konsisten tanpa lelah, sedangkan manusia unggul dalam pemecahan masalah kompleks. Tugas mekanis wajib diserahkan kepada komputer.
- **4. Pengejaran Perbaikan Berkelanjutan Tanpa Henti:**
  - Secara proaktif menganalisis metrik operasional yang dapat ditindaklanjuti (*actionable metrics*) guna menyempurnakan alur kerja tim secara berkala.
- **5. Tanggung Jawab Bersama (*Shared Responsibility*):**
  - Menjaga stabilitas *pipeline* adalah tanggung jawab seluruh tim. Jika sebuah proses pembangunan gagal (*broken build*), seluruh aktivitas dihentikan sementara untuk bersama-sama memulihkan kestabilan sistem.

#### D. Manajemen Risiko Modern dan Teknik Penerapan
DevOps mengelola risiko bukan dengan menghindari atau menunda perubahan, melainkan dengan meningkatkan frekuensi perubahan dalam skala kecil untuk membangun memori otot tim (*muscle memory*).

Teknik manajemen rilis modern meliputi:
- **Pemisahan Penerapan dari Aktivasi (*Decoupling Deployment from Activation*):**
  - **Feature Flags (Feature Toggles):** Kode fitur baru dapat diterapkan ke lingkungan produksi dalam keadaan nonaktif. Pengelola sistem dapat menyalakan atau mematikan fitur tersebut seketika tanpa perlu melakukan *redeploy*.
- **Pengujian Kenari (*Canary Testing*):**
  - Menerapkan fitur baru ke sebagian kecil infrastruktur produksi dan mengarahkan sebagian kecil lalu lintas pengguna untuk memantau kestabilan performa:

$$\text{Aktivasi Progresif Trafik}: \quad 10\% \longrightarrow 25\% \longrightarrow 50\% \longrightarrow 100\%$$

  - Jika telemetri menunjukkan peningkatan galat, lalu lintas segera dikembalikan ke versi stabil sebelumnya.
- **Penerapan Biru-Hijau (*Blue-Green Deployment*):**
  - Menyediakan dua lingkungan produksi identik (*Blue* dan *Green*). Satu lingkungan melayani lalu lintas aktif sementara lingkungan lain diperbarui dengan kode baru. Pengalihan dilakukan di tingkat *router/load balancer* untuk menjamin ketiadaan waktu henti layanan (*zero-downtime deployment*).

---

### 7. Key Takeaways and Summary

#### A. Poin-Poin Strategis Modul 03
- **Tinggalkan Taylorisme dan Silo:**
  - Rekayasa perangkat lunak adalah pekerjaan pengetahuan kriya (*knowledge craftwork*). Hilangkan pemisahan komando dan birokrasi serah terima antarsilo.
- **Adopsi Pola Pikir Produk:**
  - Perlakukan perangkat lunak sebagai produk berumur panjang dengan tim stabil yang memiliki kepemilikan ujung ke ujung (*end-to-end ownership*).
- **Runtuhkan Tembok Kebingungan:**
  - Satukan metrik keberhasilan *Dev* (inovasi) dan *Ops* (stabilitas) di bawah satu tujuan bersama demi menghantarkan nilai nyata kepada pengguna.
- **Kelola Infrastruktur Berbasis Kode (*IaC*):**
  - Terapkan prinsip *cattle, not pets*. Gunakan infrastruktur fana yang dapat direproduksi dan terapkan kontainer kekal (*immutable delivery*) tanpa penambalan manual di produksi.
- **Disiplin CI/CD untuk Kecepatan dan Keamanan:**
  - *Continuous Integration* menjamin integrasi harian dengan pengujian otomatis mandiri.
  - *Continuous Delivery* memastikan cabang utama selalu berada dalam kondisi siap rilis ke lingkungan produksi kapan saja dengan risiko minimal melalui teknik *feature flags*, *canary testing*, dan *blue-green deployment*.
