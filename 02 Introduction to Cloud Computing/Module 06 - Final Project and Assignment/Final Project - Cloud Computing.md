# Final Project Tutorial: Deploying "Guess the Capital" on IBM Cloud Code Engine

Dokumen ini merupakan panduan tutorial instruksional praktikum mandiri untuk menyelesaikan proyek akhir komputasi awan. Tutorial ini membimbing Anda langkah demi langkah dalam memodernisasi dan menerapkan aplikasi web "Guess the Capital" ke lingkungan cloud, mulai dari verifikasi prasyarat lingkungan, pengujian lokal, pembuatan Dockerfile berbasis peladen web Nginx, pembangunan dan pengujian kontainer lokal, pengunggahan citra ke IBM Cloud Container Registry (ICR), hingga penerapan aplikasi nirserver (*serverless*) di IBM Cloud Code Engine dengan URL akses publik.

---

## 1. Prerequisites and Lab Setup

### A. Verifikasi Alat Baris Perintah (CLI Tools)
Sebelum mengeksekusi instruksi proyek, pastikan perkakas baris perintah utama telah terpasang dan berfungsi dengan baik di dalam terminal Cloud IDE Anda:

- **Instruksi 1: Memeriksa Instalasi Docker CLI**
  - Buka terminal baru melalui menu **Terminal > New Terminal**, lalu jalankan perintah:

```bash
docker --version
```

  - *Hasil yang Diharapkan*: Terminal menampilkan nomor versi Docker aktif (contoh: `Docker version 20.10.x` atau versi yang lebih baru).

- **Instruksi 2: Memeriksa Instalasi IBM Cloud CLI**
  - Jalankan perintah berikut untuk memastikan plugin dan perkakas baris perintah IBM Cloud telah terpasang:

```bash
ibmcloud version
```

  - *Hasil yang Diharapkan*: Terminal menampilkan versi IBM Cloud CLI yang terpasang (contoh: `ibmcloud version 2.x.x`).

### B. Inisialisasi Proyek dan Terminal IBM Code Engine
Platform IBM Cloud Code Engine menyediakan antarmuka baris perintah yang telah dikonfigurasi secara otomatis dengan variabel lingkungan dan kredensial akses:

- **Instruksi 1: Mengakses Menu Code Engine**
  - Pada panel menu Cloud IDE, klik ikon menu Cloud dan pilih menu **Code Engine**.
- **Instruksi 2: Membuat Proyek Code Engine**
  - Klik tombol **Create Project** pada panel pengaturan Code Engine. Tunggu beberapa saat hingga proses provisi lingkungan selesai dan indikator status berubah menjadi **Active**.
- **Instruksi 3: Membuka Code Engine CLI**
  - Klik tombol **Code Engine CLI**. Langkah ini akan membuka sesi terminal baru yang telah dikonfigurasi dengan kredensial klaster, proyek aktif, dan file `Kubeconfig` yang siap digunakan.

---

## 2. Task 1: Setting Up the Starter Code and Local Verification

### A. Kloning Repositori Kode Sumber Aplikasi
Aplikasi kuis "Guess the Capital" tersedia sebagai repositori kode awal (*starter code*) di GitHub.

- **Instruksi 1: Berpindah ke Direktori Kerja Utama**
  - Pastikan terminal Anda berada di direktori proyek:

```bash
cd /home/project
```

- **Instruksi 2: Mengunduh Kode Sumber Melalui Git Clone**
  - Jalankan perintah berikut untuk menyalin repositori ke lingkungan lokal Anda:

```bash
[ ! -d 'fyidw-guess-the-capital' ] && git clone https://github.com/ibm-developer-skills-network/fyidw-guess-the-capital.git
```

- **Instruksi 3: Memeriksa Struktur Berkas Proyek**
  - Masuk ke direktori repositori dan periksa seluruh daftar berkas yang tersedia:

```bash
cd fyidw-guess-the-capital
ls -la
```

  - *Daftar Komponen Aplikasi*:
    - `index.html`: Kerangka utama halaman arahan aplikasi web.
    - `style.css`: Berkas stylesheet CSS untuk mengatur tata letak, warna, dan tipografi responsif.
    - `script.js`: Logika interaktif JavaScript untuk memuat kuis, memproses pilihan jawaban pengguna, dan menghitung skor.
    - `data.json`: Berkas data terstruktur berformat JSON yang memuat daftar nama negara beserta empat opsi pilihan ibu kota.
    - `favicon.ico`: Ikon grafis tab peramban aplikasi.

### B. Menjalankan Peladen Lokal Berbasis Python
Sebelum membungkus aplikasi ke dalam kontainer, verifikasi bahwa berkas web statis berfungsi normal menggunakan modul peladen HTTP bawaan Python.

- **Instruksi 1: Menjalankan Peladen Web Lokal**
  - Eksekusi peladen web pada port `8000`:

```bash
python3 -m http.server 8000
```

  - *Hasil yang Diharapkan*: Terminal menampilkan log `Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...`.

- **Instruksi 2: Menguji Tampilan Aplikasi di Peramban**
  - Buka fitur pratinjau web Cloud IDE (*Launch Application*), masukkan nomor port `8000`, dan buka halaman aplikasi.
  - Verifikasi bahwa judul permainan "Guess the Capital" tampil, tombol pilihan negara dapat diklik, dan skor bertambah saat jawaban benar dipilih.
- **Instruksi 3: Menghentikan Peladen Python**
  - Kembali ke terminal dan tekan tombol kombinasi `CTRL + C` untuk menghentikan proses peladen web lokal.

---

## 3. Task 2: Containerizing the Web Application with Docker

### A. Pembuatan Berkas Konfigurasi Dockerfile
Untuk memodernisasi aplikasi web statis menjadi aplikasi siap cloud (*cloud-ready*), kita mengemas seluruh aset web ke dalam citra kontainer menggunakan peladen web Nginx yang ringan dan berkinerja tinggi.

- **Instruksi 1: Membuat Berkas Dockerfile**
  - Buat berkas baru bernama `Dockerfile` di dalam folder `/home/project/fyidw-guess-the-capital/`.
- **Instruksi 2: Menulis Konfigurasi Dockerfile**
  - Masukkan konfigurasi berikut ke dalam berkas `Dockerfile`:

```dockerfile
# Gunakan citra resmi Nginx dari Docker Hub sebagai fondasi peladen web
FROM nginx

# Salin ikon favicon ke direktori publik Nginx
COPY favicon.ico /usr/share/nginx/html/favicon.ico

# Salin dokumen HTML utama sebagai halaman beranda
COPY index.html /usr/share/nginx/html/index.html

# Salin skrip JavaScript untuk fungsionalitas logika interaktif
COPY script.js /usr/share/nginx/html/script.js

# Salin lembar gaya CSS untuk tampilan visual
COPY style.css /usr/share/nginx/html/style.css

# Salin berkas basis data konten JSON ke direktori web
COPY data.json /usr/share/nginx/html/data.json
```

- **Rincian Instruksi Dockerfile:**
  - `FROM nginx`: Mengunduh citra resmi peladen Nginx yang sudah dilengkapi dependensi jaringan dan konfigurasi web server standar.
  - `COPY <file> /usr/share/nginx/html/`: Menyalin berkas lokal ke direktori root dokumen publik default yang disajikan oleh Nginx pada port 80.

### B. Membangun Citra Kontainer Lokal (Docker Build)
- **Instruksi 1: Mengeksekusi Pembangunan Citra Docker**
  - Jalankan perintah berikut untuk mengompilasi berkas `Dockerfile` menjadi citra kontainer dengan tag `guess-the-capital`:

```bash
docker build -t guess-the-capital .
```

  - *Penjelasan Opsi Perintah*:
    - `-t guess-the-capital`: Memberikan penamaan (*tag*) lokal pada citra yang dihasilkan.
    - `.`: Menentukan konteks pembangunan (*build context*) pada direktori kerja saat ini.

- **Instruksi 2: Memeriksa Citra yang Telah Terbentuk**
  - Pastikan citra telah tersimpan di repositori Docker lokal:

```bash
docker images
```

  - *Hasil yang Diharapkan*: Tabel terminal menampilkan baris dengan repositori `guess-the-capital`, tag `latest`, beserta ukuran citra sekitar 140 MB hingga 190 MB.

### C. Menjalankan dan Menguji Kontainer Docker di Lingkungan Lokal
- **Instruksi 1: Menjalankan Kontainer pada Mode Terlepas (Detached)**
  - Eksekusi kontainer dengan memetakan port host `8080` ke port internal kontainer `80`:

```bash
docker run -it -d -p 8080:80 guess-the-capital
```

  - *Penjelasan Parameter*:
    - `-i`: Mengaktifkan mode interaktif (*interactive*).
    - `-t`: Mengalokasikan pseudo-terminal (TTY).
    - `-d`: Menjalankan kontainer di latar belakang (*detached mode*).
    - `-p 8080:80`: Menghubungkan port `8080` pada mesin pengembang ke port `80` tempat Nginx berjalan di dalam kontainer.
  - *Hasil yang Diharapkan*: Terminal mencetak string panjang pengenal unik kontainer (*Container ID*).

- **Instruksi 2: Memverifikasi Akses Kontainer di Peramban**
  - Buka fitur peluncur aplikasi Cloud IDE (*Launch Application*), masukkan port `8080`, dan akses halamannya.
  - Jika aplikasi kuis muncul dan dapat dimainkan, berarti kontainer Docker berbasis Nginx Anda telah berhasil dibuat dan berfungsi secara sempurna.

---

## 4. Task 3: Pushing Container Image to IBM Container Registry

### A. Menandai Citra Kontainer untuk IBM Container Registry (ICR)
Agar platform cloud dapat mengambil dan menjalankan citra kontainer Anda, citra harus diberi label alamat registri jarak jauh (*remote registry*) dan diunggah ke IBM Cloud Container Registry.

- **Instruksi 1: Membangun Citra dengan Tag Registri ICR**
  - Gunakan variabel lingkungan `${SN_ICR_NAMESPACE}` yang telah disediakan oleh sesi lab:

```bash
cd /home/project/fyidw-guess-the-capital
docker build . -t us.icr.io/${SN_ICR_NAMESPACE}/guess-the-capital
```

  - *Penjelasan Struktur Alamat Tag*:
    - `us.icr.io`: Domain peladen IBM Cloud Container Registry wilayah Amerika Serikat.
    - `${SN_ICR_NAMESPACE}`: Ruang nama unik (*namespace*) akun pengguna di registri.
    - `guess-the-capital`: Nama repositori citra aplikasi.

### B. Mengunggah Citra Kontainer ke Registri Jarak Jauh (Docker Push)
- **Instruksi 1: Melakukan Pendorongan Citra ke ICR**
  - Unggah citra yang telah ditandai ke repositori privat IBM Cloud:

```bash
docker push us.icr.io/${SN_ICR_NAMESPACE}/guess-the-capital
```

  - *Hasil yang Diharapkan*: Terminal menampilkan proses pengunggahan lapisan-lapisan citra (*layers*) dengan status `Pushed` atau `Layer already exists`, diakhiri dengan digest kriptografis penanda integritas citra.

---

## 5. Task 4: Deploying and Verifying Application on IBM Code Engine

### A. Membuat dan Menerapkan Aplikasi Nirserver (Code Engine Application)
IBM Cloud Code Engine akan mengunduh citra dari registri ICR, membuat beban kerja kontainer, dan mengonfigurasi rute lalu lintas web publik secara otomatis.

- **Instruksi 1: Menerapkan Aplikasi via Perintah `ibmcloud ce`**
  - Jalankan perintah pembuatan aplikasi berikut di terminal Code Engine CLI:

```bash
ibmcloud ce application create --name guess-the-capital --image us.icr.io/${SN_ICR_NAMESPACE}/guess-the-capital --registry-secret icr-secret --port 80
```

  - *Penjelasan Parameter Perintah*:
    - `--name guess-the-capital`: Nama instans aplikasi yang dibuat di dalam proyek Code Engine.
    - `--image us.icr.io/${SN_ICR_NAMESPACE}/guess-the-capital`: Lokasi lengkap citra kontainer di registri ICR.
    - `--registry-secret icr-secret`: Kredensial rahasia yang telah dikonfigurasi sebelumnya untuk mengotorisasi Code Engine mengunduh citra dari registri privat.
    - `--port 80`: Port target tempat kontainer menerima lalu lintas HTTP (port Nginx).

- **Instruksi 2: Mengambil URL Akses Publik**
  - Perhatikan baris keluaran terminal saat proses pembuatan aplikasi selesai. Cari parameter URL publik yang memiliki format:

```text
https://guess-the-capital.<random-id>.<region>.codeengine.appdomain.cloud
```

### B. Memverifikasi Status dan Kesehatan Beban Kerja Aplikasi
- **Instruksi 1: Memeriksa Informasi Status Aplikasi**
  - Jalankan perintah berikut untuk mengaudit kesehatan dan konfigurasi operasional instans:

```bash
ibmcloud ce application get --name guess-the-capital
```

  - *Hasil yang Diharapkan*:
    - Parameter `Ready` bernilai `true`.
    - Parameter `Status` bernilai `Ready`.
    - Daftar kondisi menunjukkan alokasi rute (*routes*), konfigurasi klaster, dan revisi perangkat lunak berstatus sukses (*Successful*).

### C. Pengujian Akhir Antarmuka Pengguna Melalui URL Publik
- **Instruksi 1: Membuka URL Aplikasi di Browser**
  - Buka peramban web baru dan navigasikan ke alamat URL publik yang Anda peroleh dari keluaran Code Engine.
- **Instruksi 2: Validasi Fungsionalitas End-to-End**
  - Mainkan kuis dengan menjawab pertanyaan ibu kota negara.
  - Periksa apakah seluruh aset grafis, stylesheet CSS, logika JavaScript, dan berkas JSON termuat secara sempurna melalui protokol HTTPS aman.

---

## 6. Summary and Troubleshooting Guide

### A. Rangkuman Siklus Deployment Cloud-Native
- **1. Kode Sumber Lokal (Local Development):** Mengembangkan dan menguji kode HTML/CSS/JavaScript menggunakan server pengujian sederhana.
- **2. Pengemasan Kontainer (Docker Packaging):** Mengabstraksi aplikasi dan web server Nginx ke dalam satu citra mandiri yang portabel.
- **3. Distribusi Registri (Registry Distribution):** Mengunggah citra ke IBM Container Registry sebagai sumber distribusi tunggal yang aman.
- **4. Eksekusi Nirserver (Serverless Execution):** Menyebarkan beban kerja ke IBM Cloud Code Engine yang secara otomatis mengelola penskalaan naik saat trafik tinggi dan menyusut ke nol (*scale-to-zero*) saat tidak ada pengguna aktif.

### B. Panduan Penyelesaian Kendala (Troubleshooting Tips)
- **Kendala 1: Kesalahan Autentikasi Saat Docker Push**
  - *Penyebab*: Sesi autentikasi Docker ke server `us.icr.io` belum aktif atau namespace tidak sesuai.
  - *Solusi*: Periksa kembali apakah variabel `${SN_ICR_NAMESPACE}` telah terisi dengan menjalankan `echo ${SN_ICR_NAMESPACE}`.
- **Kendala 2: Aplikasi Code Engine Gagal Menarik Citra (ImagePullBackOff)**
  - *Penyebab*: Parameter `--registry-secret icr-secret` terlewat atau nama namespace salah ketik.
  - *Solusi*: Jalankan `ibmcloud ce application delete --name guess-the-capital` lalu ulangi perintah pembuatan aplikasi dengan menyertakan flag `--registry-secret icr-secret`.
- **Kendala 3: Halaman Web Menampilkan 403 Forbidden atau Halaman Kosong**
  - *Penyebab*: Berkas statis tidak tersalin dengan benar ke jalur `/usr/share/nginx/html/` di dalam berkas Dockerfile.
  - *Solusi*: Pastikan nama berkas pada baris instruksi `COPY` di dalam `Dockerfile` memiliki huruf besar/kecil yang sama persis dengan berkas fisik di repositori.