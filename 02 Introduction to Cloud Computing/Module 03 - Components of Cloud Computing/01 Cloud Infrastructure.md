# Cloud Infrastructure and Compute Resources

Catatan komprehensif ini membahas fondasi arsitektur infrastruktur komputasi awan (*Cloud Infrastructure*), teknologi virtualisasi (*Virtual Machines* dan *Hypervisors*), spektrum opsi komputasi (*Shared VMs*, *Transient/Spot VMs*, *Reserved Instances*, *Dedicated Hosts*, *Bare Metal Servers*, *Containers*, dan *Serverless*), perancangan jaringan aman (*Software-Defined Networking*, VPC, Subnet, ACL, dan *Security Groups*), hingga kerangka kerja pengambilan keputusan arsitektur berdasarkan pandangan pakar industri.

---

## 1. Overview of Cloud Infrastructure Architecture

### A. Hierarki Geografis dan Fasilitas Fisik
- Lapisan infrastruktur merupakan fondasi fisik paling mendasar yang menopang seluruh model layanan komputasi awan:
  - Lingkungan teknologi informasi penyedia cloud terdistribusi secara global melalui hierarki wilayah geografis dan fasilitas data center:
    - Wilayah Komputasi (*Cloud Region*): Area geografis tertentu di dunia tempat infrastruktur cloud dikelompokkan (misalnya *US East* atau *NA South*). Setiap region terisolasi secara fisik dan operasional dari region lainnya, sehingga bencana alam (seperti gempa bumi atau banjir) di satu wilayah tidak akan melumpuhkan operasional cloud di wilayah lain.
    - Zona Ketersediaan (*Availability Zone* / AZ): Setiap region memiliki beberapa zona ketersediaan terpisah (misalnya `DAL-09` atau `us-east-1a`). Satu AZ umumnya merepresentasikan satu atau lebih data center fisik mandiri yang memiliki pasokan listrik redundan, sistem pendingin independen, dan konektivitas jaringan terisolasi.
    - Karakteristik Desain Fault Tolerance: Pemisahan antar zona ketersediaan dirancang untuk meminimalkan latensi antar zona melalui koneksi serat optik berkecepatan tinggi, sekaligus menghilangkan titik kegagalan tunggal (*single point of failure*).
  - Pusat Data Cloud (*Cloud Data Center*):
    - Bangunan atau fasilitas pergudangan khusus berskala raksasa yang menampung ribuan rak server (*racks*) dan wadah komputasi terstandardisasi (*pods*).
    - Memuat perangkat keras pemrosesan (server fisik), media penyimpanan massal, serta peralatan interkoneksi jaringan berkecepatan tinggi.

### B. Sumber Daya Inti Infrastruktur Cloud
- Tiga pilar utama sumber daya yang disediakan di dalam pusat data cloud:
  - Sumber Daya Komputasi (*Compute Resources*):
    - Mesin-mesin server yang menjalankan perangkat lunak virtualisasi untuk menghasilkan server virtual (*Virtual Machines* / VMs), server fisik tanpa virtualisasi (*Bare Metal Servers*), serta lapisan abstraksi komputasi tanpa server (*Serverless*).
  - Sumber Daya Penyimpanan Data (*Storage Resources*):
    - Fasilitas penyimpanan terdistribusi untuk menampung berkas aplikasi, basis data, citra sistem operasi, *snapshots*, dan cadangan data (*backups*). Server fisik maupun virtual dilengkapi media penyimpanan lokal bawaan secara default, yang kemudian dapat dihubungkan ke penyimpanan jaringan berskala masif.
  - Sumber Daya Jaringan Berbasis Perangkat Lunak (*Software-Defined Networking* / SDN):
    - Selain perangkat keras fisik tradisional (seperti sakelar dan perute), cloud mengandalkan SDN untuk memvirtualisasikan fungsi jaringan dan menyediakannya melalui antarmuka program (*API*).
    - Memungkinkan pembuatan antarmuka jaringan virtual (*Virtual Network Interfaces* / vNICs), alokasi alamat IP dinamis, pembentukan subnet, dan penegakan aturan keamanan secara terprogram dalam hitungan detik.
    - Mendukung integrasi jaringan distribusi konten (*Content Delivery Networks* / CDNs) untuk mendistribusikan berkas statis ke titik-titik kehadiran (*Points of Presence* / PoP) terdekat dengan pengguna global guna mereduksi latensi.

---

## 2. Virtualization and Hypervisors

### A. Konsep dan Prinsip Kerja Virtualisasi
- Virtualisasi merupakan proses teknologi yang menciptakan versi berbasis perangkat lunak (*software-based*) atau virtual dari sumber daya fisik komputasi, mencakup prosesor, memori, media penyimpanan, antarmuka jaringan, maupun server utuh.
- Komponen kunci yang memungkinkan terwujudnya virtualisasi adalah *hypervisor*:
  - *Hypervisor* (atau *Virtual Machine Monitor* / VMM) adalah lapisan perangkat lunak yang berjalan di atas perangkat keras fisik (*host*) untuk menarik sumber daya komputasi fisik dan mendistribusikannya secara terisolasi ke berbagai lingkungan virtual.
  - Setiap lingkungan virtual yang terbentuk disebut Mesin Virtual (*Virtual Machine* / VM).

### B. Klasifikasi Hypervisor: Type 1 vs Type 2
- Dua klasifikasi utama arsitektur hypervisor:
  - *Type 1 Hypervisor (Bare-Metal Hypervisor)*:
    - Dipasang dan berjalan langsung (*directly on top*) pada perangkat keras fisik server tanpa melalui perantara sistem operasi induk.
    - Karakteristik: Memberikan tingkat keamanan tertinggi, efisiensi eksekusi maksimal, dan latensi komputasi paling rendah karena tidak memiliki lapisan perantara tambahan.
    - Menjadi standar de facto yang paling banyak digunakan di pusat data komersial enterprise dan cloud publik.
    - Contoh Produk: VMware ESXi, Microsoft Hyper-V, dan Kernel-based Virtual Machine (KVM) pada sistem operasi Linux.
  - *Type 2 Hypervisor (Hosted Hypervisor)*:
    - Berjalan sebagai aplikasi perangkat lunak di atas sistem operasi induk (*Host OS*) yang sudah terpasang pada perangkat keras fisik.
    - Karakteristik: Memiliki lapisan *Host OS* yang berada di antara perangkat keras fisik dan hypervisor, sehingga menimbulkan latensi komputasi yang lebih tinggi (*overhead*).
    - Umumnya digunakan untuk kebutuhan virtualisasi pengguna akhir (*end-user virtualization*) pada komputer desktop atau laptop pengembang, bukan untuk beban kerja produksi pusat data skala besar.
    - Contoh Produk: Oracle VM VirtualBox dan VMware Workstation.

### C. Karakteristik Mesin Virtual dan Keuntungan Virtualisasi
- Karakteristik teknis Mesin Virtual (*Virtual Machines* / VMs):
  - VM beroperasi layaknya komputer fisik mandiri, memiliki sistem operasi tamu (*Guest OS*), pustaka dependensi (*binaries & libraries*), dan ruang penyimpanan sendiri.
  - Antar VM yang berada di bawah hypervisor yang sama saling terisolasi secara independen, sehingga satu server fisik dapat menjalankan berbagai OS yang berbeda secara simultan (misalnya satu VM menjalankan Linux, VM lain menjalankan Windows Server).
  - Portabilitas Tinggi: Instans VM dapat disalin, dicadangkan, dan dipindahkan (*migrated*) dari satu server fisik ke server fisik lain secara instan tanpa memutus kesinambungan layanan.
- Tiga keuntungan utama adopsi virtualisasi:
  - Penghematan Biaya dan Konsolidasi Infrastruktur (*Cost Savings & Consolidation*):
    - Menjalankan banyak lingkungan virtual pada satu mesin fisik secara drastis mengurangi jejak perangkat keras (*hardware footprint*), menurunkan konsumsi listrik, menghemat pendingin data center, dan memangkas biaya pemeliharaan berkala.
  - Kelincahan dan Kecepatan Provisi (*Agility & Speed*):
    - Menyediakan lingkungan pengujian dan pengembangan (*dev/test*) baru dalam hitungan menit melalui konsol perangkat lunak, menggantikan proses pengadaan server fisik tradisional yang memakan waktu berminggu-minggu.
  - Mengurangi Waktu Henti Sistem (*Lower Downtime*):
    - Jika suatu server fisik (*host*) mengalami kerusakan mendadak, hypervisor orkestrasi dapat memindahkan VM yang sedang berjalan ke server fisik cadangan lain secara cepat (*live migration / failover*).

---

## 3. Types of Virtual Machines and Provisioning Models

### A. Shared atau Public Cloud VMs (Multi-Tenant)
- Karakteristik mesin virtual multi-tenant:
  - Perangkat keras server fisik yang mendasarinya dibagi pakai (*shared*) bersama beban kerja dari pengguna atau penyewa (*tenants*) lain.
  - Di-*provisioning* secara cepat dengan konfigurasi ukuran standar yang telah ditentukan penyedia (*predefined sizes*), mencakup:
    - *Compute-Intensive*: Rasio vCPU tinggi untuk pemrosesan logika matematika berat.
    - *Memory-Intensive*: Kapasitas RAM ekstra besar untuk basis data in-memory dan caching.
    - *High Performance I/O*: Throughput pembacaan dan penulisan disk super cepat untuk sistem transaksional.
  - Sebagian penyedia juga menyediakan opsi konfigurasi kustom (*custom configurations*), di mana pengguna bebas menentukan perbandingan jumlah core vCPU, RAM, dan disk lokal.
  - Model Penagihan: Berbasis hitungan per jam atau per detik (*pay-per-use*), atau berbasis kontrak bulanan tetap (*monthly billing*) untuk efisiensi biaya beban kerja berdurasi panjang.

### B. Transient atau Spot VMs
- Karakteristik mesin virtual transien:
  - Memanfaatkan sisa kapasitas komputasi yang sedang tidak terpakai (*idle / unused capacity*) di dalam pusat data cloud penyedia.
  - Ditawarkan dengan potongan harga yang sangat besar (diskon mencapai 70% hingga 90% dibandingkan tarif VM reguler).
  - Kompromi Risiko Penghentian (*Preemption Risk*): Penyedia cloud berhak mengambil kembali (*reclaim / de-provision*) sumber daya VM ini sewaktu-waktu dengan pemberitahuan singkat saat permintaan instans reguler melonjak.
  - Kasus Penggunaan Ideal: Beban kerja yang toleran terhadap interupsi, lingkungan pengujian sementara, pemrosesan tumpukan (*batch processing*), simulasi komputasi kinerja tinggi (HPC), dan analisis mahadata (*Big Data*) nir-keadaan (*stateless*).

### C. Reserved Virtual Server Instances
- Karakteristik instans virtual terpesan:
  - Pengguna memesan dan menjamin ketersediaan kapasitas komputasi tertentu untuk jangka waktu tetap di masa mendatang, umumnya dengan komitmen kontrak 1 tahun atau 3 tahun.
  - Memberikan potongan harga signifikan dibandingkan tarif bayar per jam (*hourly on-demand*).
  - Jaminan Kapasitas: Kapasitas komputasi di pusat data pilihan dijamin selalu tersedia sepanjang masa sewa kontrak.
  - Sangat ideal untuk aplikasi bisnis inti dengan kebutuhan beban kerja dasar (*baseline workload*) yang konstan dan dapat diprediksi secara tahunan.

### D. Dedicated Hosts (Single-Tenant)
- Karakteristik tuan rumah terdedikasi:
  - Menawarkan isolasi penyewa tunggal (*single-tenant isolation*), di mana satu server fisik penuh didedikasikan secara eksklusif untuk menjalankan VM-VM milik satu pelanggan saja.
  - Pengguna dapat menentukan pusat data spesifik dan unit rak (*POD*) tempat server fisik tersebut ditempatkan.
  - Memberikan visibilitas dan kendali penuh atas penempatan beban kerja di tingkat soket prosesor fisik (*socket-level control*).
  - Kasus Penggunaan Utama: Memenuhi regulasi industri ketat yang melarang berbagi perangkat keras fisik dengan pihak luar, audit keamanan tingkat tinggi, serta kepatuhan lisensi perangkat lunak pihak ketiga yang berbasis jumlah soket/core prosesor fisik.

---

## 4. Bare Metal Servers

### A. Definisi dan Model Pengelolaan
- *Bare Metal Server* adalah server fisik berarsitektur penyewa tunggal (*single-tenant dedicated physical server*) yang disediakan secara eksklusif bagi satu pelanggan tanpa ada lapisan perangkat lunak pihak ketiga di bawahnya.
- Penyedia cloud memasang server fisik nyata langsung ke dalam rak (*rack*) di data center untuk pelanggan bersangkutan.
- Pembagian Tanggung Jawab Operasional:
  - Penyedia cloud bertanggung jawab mengelola kesehatan fisik perangkat keras, modul memori, catu daya, dan konektivitas rak jaringan hingga ke tingkat pelaporan sistem operasi. Jika perangkat keras rusak, vendor akan mengganti suku cadang dan melakukan boot ulang server.
  - Pelanggan memegang kendali administratif mutlak (*root/admin access*) atas konfigurasi perangkat keras, partisi disk, pemilihan sistem operasi, hingga perangkat lunak aplikasi di atasnya.

### B. Kustomisasi dan Akselerasi Hardware
- Fleksibilitas konfigurasi:
  - Tersedia dalam bentuk paket racikan standar (*pre-configured builds*) maupun pesanan kustom menyeluruh (*custom-configured*) sesuai spesifikasi prosesor, RAM, arsitektur hard drive/NVMe, dan kartu antarmuka jaringan.
  - Pelanggan bebas memasang sistem operasi eksklusif atau menginstal hypervisor pilihan sendiri (misalnya membangun klaster virtualisasi privat berbasis Xen atau Proxmox mandiri).
  - Dukungan Unit Pemroses Grafis (*GPU Acceleration*): Server bare metal dapat dilengkapi prosesor grafis canggih (seperti NVIDIA Tensor Core GPUs) untuk mempercepat beban kerja kecerdasan buatan (*AI*), pembelajaran mendalam (*Deep Learning*), analitik data ilmiah, dan perenderan grafis 3D presisi tinggi.

### C. Perbandingan Komprehensif: Bare Metal vs Virtual Servers
- Keunggulan Kinerja dan Eliminasi "Hypervisor Tax":
  - Server bare metal berjalan tanpa lapisan hypervisor, sehingga seluruh daya siklus prosesor dan bus data I/O dialokasikan 100% untuk aplikasi pengguna tanpa potongan beban sistem (*zero virtualization overhead*).
  - Menghilangkan fenomena tetangga bising (*noisy neighbor effect*), yaitu penurunan kinerja I/O disk atau CPU akibat aktivitas ekstrem penyewa lain pada server fisik bersama.
- Kompromi Waktu Penyediaan (*Provisioning Time*):
  - Virtual Server dapat di-*provisioning* dalam hitungan detik atau menit.
  - Bare Metal Server memerlukan waktu provisi fisik: berkisar 20 hingga 40 menit untuk paket standar, dan 3 hingga 4 jam untuk paket kustom spesifik.
- Model Biaya:
  - Virtual Server menggunakan model pembayaran per jam/detik yang elastis dan terjangkau untuk skala kecil.
  - Bare Metal Server memiliki biaya sewa bulanan tetap (*flat monthly pricing*) dengan tarif lebih tinggi karena sifatnya yang terdedikasi penuh.
- Kasus Penggunaan Ideal Bare Metal:
  - Beban kerja intensif CPU dan I/O tinggi: Sistem ERP skala raksasa (SAP HANA), CRM transaksional terpusat, basis data skala besar, serta simulasi rekayasa aerodinamika (seperti kalkulasi terowongan angin jet supersonik berulang kali).

---

## 5. Secure Networking in Cloud Environments

### A. Konstruksi Jaringan Logis Berbasis Perangkat Lunak
- Pembangunan jaringan di cloud mengadopsi prinsip yang serupa dengan jaringan pusat data lokal (*on-premises*), namun seluruh fungsi perangkat keras fisik direpresentasikan sebagai entitas logis virtual:
  - Kartu Antarmuka Jaringan Fisik (*NIC*) diwujudkan dalam bentuk *Virtual Network Interface Controllers* (vNICs).
  - Peralatan jaringan fisik seperti sakelar, perute, dan penyeimbang beban dikirimkan sebagai layanan perangkat lunak (*Networking as a Service*).
  - Pembentukan batas perimeter jaringan diawali dengan mendefinisikan blok rentang alamat IP menggunakan notasi *Classless Inter-Domain Routing* (CIDR).
  - *Virtual Private Cloud* (VPC): Ruang jaringan terisolasi secara privat dan logis di dalam cloud publik bersama, memadukan keamanan arsitektur privat dengan skalabilitas publik.
  - *Subnet*: Pemisahan segmen jaringan di dalam VPC menjadi blok-blok IP yang lebih kecil untuk memfasilitasi arsitektur bertingkat (*multi-tier architecture*).

### B. Arsitektur Aplikasi Tiga Tingkat (Three-Tier Architecture) dan Keamanan
- Penataan aplikasi enterprise menggunakan subnet terpisah:
  - Tingkat Web (*Web Tier*): Menampung instans antarmuka web (*VSIs*) yang bertugas menerima koneksi langsung dari jaringan internet publik.
  - Tingkat Aplikasi (*Application Tier*): Menampung instans logika pemrosesan bisnis yang hanya dapat diakses oleh lapisan web, terisolasi dari internet luar.
  - Tingkat Basis Data (*Database Tier*): Menampung instans penyimpanan basis data internal yang hanya dapat diakses oleh lapisan aplikasi, memiliki tingkat isolasi keamanan paling ketat.
- Perlindungan Keamanan Jaringan Berlapis (*Defense-in-Depth*):
  - *Access Control Lists (ACLs / NACLs)*:
    - Bekerja sebagai *firewall* di tingkat perimeter subnet (*subnet-level firewall*).
    - Memeriksa dan memfilter paket data yang masuk (*inbound*) dan keluar (*outbound*) dari seluruh batas subnet secara nir-keadaan (*stateless*).
  - *Security Groups (SGs)*:
    - Bekerja sebagai *firewall* virtual di tingkat instans server individual (*instance-level firewall*).
    - Memfilter lalu lintas jaringan yang masuk dan keluar secara berkeadaan (*stateful*), di mana izin lalu lintas masuk secara otomatis mengizinkan lalu lintas balasan keluar.

### C. Gerbang Internet, VPN, Direct Link, dan Load Balancer
- Mekanisme interkoneksi dan distribusi lalu lintas data:
  - *Public Gateway*: Komponen jaringan yang menyediakan akses keluar internet bagi instans-instans di subnet privat tanpa mengekspos alamat IP privat mereka ke publik.
  - *Virtual Private Network (VPN)*: Saluran terowongan terenkripsi (*encrypted tunnel*) melalui internet publik yang menghubungkan jaringan pusat data lokal kantor secara aman ke VPC di cloud.
  - Koneksi Berkecepatan Tinggi Terdedikasi (*Direct Link / Direct Connect*):
    - Jalur koneksi fisik khusus dari jaringan *on-premises* ke infrastruktur cloud milik penyedia (seperti *IBM Cloud Direct Link*).
    - Mengabaikan internet publik sepenuhnya guna menjamin keamanan maksimal, stabilitas koneksi prima, dan latensi transmisi yang sangat rendah bagi lingkungan *Hybrid Cloud*.
  - *Load Balancer*: Perangkat lunak perutean yang membagi lalu lintas permintaan pengguna secara merata ke berbagai server instans guna mencegah kelebihan beban kerja (*overload*) dan memastikan aplikasi selalu responsif.

---

## 6. Containerization Technology and Cloud-Native Architecture

### A. Konsep Dasar dan Sejarah Kontainer
- Kontainer (*Containers*) adalah unit perangkat lunak bereksekusi mandiri yang mengemas kode program aplikasi beserta seluruh pustaka pendukung dan dependensinya dalam satu format terstandarisasi, sehingga aplikasi dapat dijalankan secara konsisten di lingkungan mana pun (desktop pengembang, server fisik lokal, maupun multi-cloud).
- Kontainer berukuran sangat ringan (*lightweight*), cepat dieksekusi, dan portabel karena tidak memuat salinan sistem operasi tamu (*Guest OS*) di setiap instansnya, melainkan memanfaatkan fitur dan kernel bersama dari sistem operasi induk (*Host OS*).
- Akar teknologi kontainer berawal dari tahun 2008 saat kernel Linux memperkenalkan fitur *Control Groups* (`cgroups`) dan *Namespaces*, yang memungkinkan isolasi proses, pembatasan alokasi CPU, partisi memori, dan ruang nama jaringan secara mandiri. Inovasi ini membuka jalan bagi kemunculan Docker, Cloud Foundry, Rocket (rkt), dan standar *Open Container Initiative* (OCI).

### B. Alur Tiga Langkah Kontainerisasi (The Three-Step Process)
- Siklus hidup pembuatan dan penggelaran kontainer modern:
  - Langkah 1: Berkas Manifes (*Manifest File*):
    - Menulis dokumen instruksi deklaratif yang mendeskripsikan kebutuhan aplikasi. Pada ekosistem Docker disebut `Dockerfile`, sedangkan pada ekosistem lain berupa berkas manifes YAML/JSON.
  - Langkah 2: Citra Kontainer (*Container Image*):
    - Mengompilasi berkas manifes menjadi artefak biner statis yang dapat dibagikan (*immutable image*), seperti *Docker Image* atau *Application Container Image* (ACI), lalu menyimpannya ke repositori registri citra (*Container Registry*).
  - Langkah 3: Instans Kontainer Berjalan (*Container Instance*):
    - Mesin pengelola runtime (*Container Runtime Engine* seperti Docker Engine, containerd, atau CRI-O) menarik citra dari registri dan menjalankannya sebagai kontainer aktif di memori.

### C. Komparasi Efisiensi: Kontainer vs Mesin Virtual
- Perbandingan arsitektur komputasi:
  - Lapisan Sistem Operasi: Mesin virtual membutuhkan sistem operasi tamu (*Guest OS*) lengkap berukuran ratusan megabita hingga gigabita di setiap VM. Kontainer hanya memuat dependensi aplikasi murni di atas kernel host bersama.
  - Perbandingan Ukuran Aplikasi Node.js:
    - VM Linux terkecil untuk aplikasi Node.js umumnya berukuran lebih dari $400\text{ MB}$ karena memuat OS lengkap.
    - Citra kontainer untuk aplikasi Node.js dan runtime-nya dapat dikemas dalam ukuran di bawah $15\text{ MB}$.
- Formula rasio konsumsi sumber daya dan efisiensi densitas:

$$
\text{Resource Overhead}_{\text{Container}} \ll \text{Resource Overhead}_{\text{Virtual Machine}}
$$

$$
\text{Startup Time}_{\text{Container}} \approx \mathcal{O}(\text{milliseconds}) \quad \text{vs} \quad \text{Startup Time}_{\text{VM}} \approx \mathcal{O}(\text{seconds to minutes})
$$

- Mengatasi Masalah *"It Works on My Machine"*:
  - Mengeliminasi ketidakcocokan versi pustaka antara komputer laptop pengembang (misalnya macOS) dengan server produksi (Linux), memfasilitasi implementasi metodologi *Agile DevOps* dan *CI/CD*.

### D. Keunggulan Modularitas Layanan Mikro (Microservices)
- Desain arsitektur berbasis kontainer memungkinkan pembagian sistem menjadi modul-modul independen yang terkopel longgar:
  - Jika aplikasi Node.js membutuhkan integrasi layanan kecerdasan buatan (*AI Cognitive API*) yang dibangun menggunakan Python:
    - Pada model VM tradisional, pengembang cenderung memaksakan kedua aplikasi berjalan dalam satu VM yang sama agar menghemat sumber daya, sehingga menyulitkan penskalaan independen.
    - Pada model kontainer, modul Node.js dan modul Python berjalan dalam kontainer terpisah yang sangat ringan.
    - Penskalaan Independen: Jika lalu lintas pengguna Node.js melonjak drastis, tim cukup menggandakan jumlah kontainer Node.js tanpa perlu menggandakan kontainer Python.
  - Pemanfaatan Sumber Daya Dinamis: Jika suatu kontainer sedang tidak aktif menggunakan CPU atau memori, sumber daya yang menganggur tersebut secara otomatis dapat dimanfaatkan oleh kontainer lain di dalam klaster perangkat keras yang sama.

---

## 7. Expert Viewpoints: Decision Framework for Cloud Compute Options

### A. Kompromi Arsitektur dan Pandangan Praktisi
- Pandangan para pakar rekayasa cloud mengenai pemilihan sumber daya komputasi di lingkungan produksi:
  - Pilihan Utama Default: Pengembang umumnya memprioritaskan kontainer (*Containers*) sebagai opsi pertama untuk arsitektur modern berorientasi cloud (*cloud-native*) karena skalabilitasnya yang cepat, efisiensi biaya, dan portabilitasnya yang tinggi (Docker berjalan identik di penyedia cloud mana pun / *cloud-agnostic*).
  - Pilihan Komputasi Tanpa Server (*Serverless Functions*):
    - Sangat ideal untuk beban kerja yang bersifat sporadis atau digerakkan oleh kejadian (*event-driven*).
    - Penyedia cloud hanya mengenakan biaya per milidetik durasi eksekusi aktif, dan tim pengembang dibebaskan sepenuhnya dari tugas pemeliharaan sistem operasi maupun patching keamanan.
  - Pertimbangan Memilih Mesin Virtual (*Virtual Machines*):
    - Dipilih apabila organisasi tidak dapat mentoleransi risiko keamanan kontainer yang berbagi kernel OS host yang sama dengan penyewa lain (*tenant isolation*).
    - Memerlukan sistem operasi khusus yang berbeda dari host (misalnya menjalankan sistem operasi lawas atau Windows Server di atas infrastruktur Linux).
  - Pertimbangan Memilih Server Fisik (*Bare Metal Servers*):
    - Dipilih apabila beban kerja membutuhkan performa komputasi murni tanpa toleransi terhadap potongan kinerja hypervisor (*hypervisor tax*) atau gangguan fluktuasi kinerja dari penyewa lain (*noisy neighbor effect*).
    - Memerlukan akses ke instruksi tingkat kernel prosesor atau kartu grafis khusus yang tidak dapat dialokasikan melalui lapisan virtualisasi/kontainer.
    - Beban kerja berbasis analitik *real-time*, mesin permainan daring (*online gaming engines*), perbankan bertransaksi sangat tinggi, atau simulasi aerodinamika ilmiah berskala ekstrim.

---

## 8. Rangkuman Pelajaran (Cloud Infrastructure Summary)

### A. Sintesis Komponen Kunci Infrastruktur Komputasi Awan
- Infrastruktur cloud terdiri dari pusat data fisik, media penyimpanan, komponen jaringan tervirtualisasi, dan tumpukan sumber daya komputasi terdistribusi.
- Virtualisasi membagi sumber daya fisik menjadi unit virtual melalui peran penting *hypervisor*, baik *Type 1 (Bare-Metal)* yang berkinerja tinggi maupun *Type 2 (Hosted)*.
- Mesin Virtual (VM) hadir dalam berbagai model penerapan: *Shared/Public VMs*, *Transient/Spot VMs*, *Reserved VMs*, dan *Dedicated Hosts*.
- Server fisik (*Bare Metal*) menyediakan kinerja murni tertinggi tanpa perantara hypervisor untuk beban kerja dengan komputasi intensif dan kepatuhan regulasi ketat.
- Jaringan cloud disajikan sebagai layanan (*Networking as a Service*) menggunakan *Virtual Private Cloud* (VPC), subnet bertingkat, serta penyaringan keamanan ganda melalui *Network ACLs* dan *Security Groups*.
- Kontainerisasi merevolusi penyebaran aplikasi *cloud-native* dengan mengemas aplikasi dan pustakanya tanpa *Guest OS*, menghasilkan unit perangkat lunak yang sangat ringan, hemat memori, dan portabel lintas platform.
