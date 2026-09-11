# 🥟 Dimsum Delight Server Monitoring & Management

**Dimsum Delight Server Monitoring & Management** merupakan project yang menerapkan konsep **Network & Server Administration** dengan menggunakan **Debian 13 sebagai server utama** untuk menjalankan, mengelola, memantau, dan menyediakan layanan aplikasi melalui jaringan lokal.

Project ini memang memiliki aplikasi pemesanan dimsum sebagai layanan yang dijalankan di server, tetapi fokus utama project berada pada **pengelolaan server dan jaringan**, bukan hanya pada pembuatan aplikasi.

Dalam project ini diterapkan beberapa konsep yang berkaitan dengan ranah **TJKT**, seperti konfigurasi jaringan, penggunaan IP Address, komunikasi client-server, pengelolaan port, administrasi Linux, service management menggunakan `systemd`, monitoring resource server, activity logging, pengecekan konektivitas, troubleshooting, serta pengelolaan database pada sisi server.

Dengan pendekatan tersebut, aplikasi digunakan sebagai salah satu **service yang berjalan di dalam infrastruktur server**, sehingga pembahasan project lebih menekankan bagaimana sebuah server dapat menyediakan layanan, menerima koneksi dari client, menjalankan service, memantau resource, dan menjaga layanan tetap berjalan.

---
## 📑 Daftar Isi

- [Tentang Project](#-tentang-project)
- [Tujuan Project](#-tujuan-project)
- [Tech Stack](#-tech-stack)
- [Tools yang Digunakan](#-tools-yang-digunakan)
- [Arsitektur Sistem](#-arsitektur-sistem)
- [Cara Kerja Sistem](#-cara-kerja-sistem)
- [Fitur Project](#-fitur-project)
- [Server Monitoring & Management](#-server-monitoring--management)
- [Resource Threshold](#-resource-threshold)
- [Activity Logging](#-activity-logging)
- [Database](#-database)
- [Deployment dan Service Management](#-deployment-dan-service-management)
- [Konsep Keamanan dan Stabilitas](#-konsep-keamanan-dan-stabilitas)
- [Struktur Project](#-struktur-project)
- [Screenshot](#-screenshot)
- [Cara Menjalankan](#-cara-menjalankan)
- [Pengujian Server dan Jaringan](#-pengujian-server-dan-jaringan)
- [Demo](#-demo)
- [Troubleshooting](#-troubleshooting)
- [Alur Keseluruhan Project](#-alur-keseluruhan-project)
- [Konsep Network dan Server yang Diterapkan](#-konsep-network-dan-server-yang-diterapkan)
- [Relevansi dengan TJKT](#-relevansi-dengan-tjkt)
- [Status Project](#-status-project)
- [Kesimpulan](#-kesimpulan)
- [Portofolio Lengkap](#-portofolio-lengkap)
- [Project Information](#-project-information)

---

## 📌 Tentang Project

Dimsum Delight Server Monitoring & Management merupakan project yang dibangun untuk menerapkan pengelolaan layanan pada sebuah **server Linux berbasis Debian 13**.

Server berfungsi sebagai pusat dari sistem. Di dalam server terdapat service aplikasi, database, konfigurasi monitoring, activity logging, dan komponen lain yang dibutuhkan agar layanan dapat digunakan oleh client melalui jaringan.

Client menggunakan komputer Windows dengan IP `192.168.10.12`, sedangkan server Debian menggunakan IP `192.168.10.50`.

Komunikasi antara client dan server dilakukan melalui jaringan lokal menggunakan protokol HTTP pada port `3000`.

```text
Client Windows
IP: 192.168.10.12
        │
        │ Network
        │
        ▼
Debian 13 Server
IP: 192.168.10.50
Port: 3000
        │
        ├── Node.js
        ├── Express.js
        ├── systemd
        ├── Server Monitoring
        ├── Activity Logging
        └── MariaDB
```

Aplikasi pemesanan dimsum pada project ini diposisikan sebagai **layanan yang berjalan pada server**, sehingga keberhasilan sistem tidak hanya bergantung pada aplikasi, tetapi juga pada konfigurasi jaringan, service, resource server, database, dan konektivitas client-server.

---

## 🎯 Tujuan Project

Project ini dibuat dengan beberapa tujuan utama:

* Menerapkan administrasi server menggunakan Debian 13.
* Membangun lingkungan server untuk menjalankan sebuah layanan aplikasi.
* Menerapkan konsep client-server pada jaringan lokal.
* Mengatur IP Address server agar dapat diakses oleh client.
* Menggunakan port sebagai jalur akses layanan.
* Mengelola service menggunakan `systemd`.
* Menerapkan monitoring resource server.
* Memantau penggunaan CPU dan RAM.
* Memantau uptime server.
* Menerapkan threshold untuk mengetahui kondisi resource.
* Menerapkan activity logging untuk membantu troubleshooting.
* Melakukan pengujian konektivitas antara client dan server.
* Menggunakan MariaDB sebagai database server.
* Menerapkan pengelolaan service agar aplikasi dapat berjalan secara stabil.
* Memahami hubungan antara jaringan, server, service, database, dan aplikasi.

---
<a id="tech-stack"></a>
## 🛠️ Tech Stack

| Teknologi  | Peran dalam Project                                      |
| ---------- | -------------------------------------------------------- |
| Debian 13  | Sistem operasi dan server utama                          |
| Linux      | Lingkungan administrasi server                           |
| Node.js    | Runtime untuk menjalankan service aplikasi               |
| Express.js | Framework server-side untuk menyediakan layanan aplikasi |
| MariaDB    | Database server                                          |
| HTML       | Struktur tampilan client                                 |
| CSS        | Tampilan antarmuka                                       |
| JavaScript | Interaksi aplikasi dan informasi monitoring              |
| systemd    | Service management pada server                           |
| Git        | Version control                                          |
| GitHub     | Repository project                                       |

Penggunaan teknologi tersebut tidak hanya ditujukan untuk membuat aplikasi, tetapi membentuk satu lingkungan **server yang dapat menjalankan dan mengelola layanan melalui jaringan**.

---

## 🔧 Tools yang Digunakan

* **VirtualBox** — digunakan untuk menjalankan virtual machine Debian 13.
* **Debian 13** — digunakan sebagai sistem operasi server.
* **Windows** — digunakan sebagai client untuk mengakses server.
* **Visual Studio Code** — digunakan untuk pengembangan dan pengelolaan file project.
* **Linux Terminal** — digunakan untuk administrasi server dan troubleshooting.
* **MariaDB** — digunakan untuk pengelolaan database.
* **Git & GitHub** — digunakan untuk version control dan penyimpanan repository.
* **systemd** — digunakan untuk mengelola service aplikasi.
* **Command Linux** — digunakan untuk pengecekan jaringan, resource, service, dan log.

---

## 🖥️ Arsitektur Sistem

Project menggunakan konsep **client-server architecture**.

Debian 13 berfungsi sebagai server utama yang menyediakan layanan kepada client melalui jaringan lokal.

```text
                         JARINGAN LOKAL
                              │
                ┌─────────────┴─────────────┐
                │                           │
                ▼                           ▼
       ┌─────────────────┐         ┌─────────────────┐
       │  Windows Client │         │  Debian Server  │
       │ 192.168.10.12   │────────►│ 192.168.10.50   │
       └─────────────────┘  HTTP   │    Port 3000    │
                                   │                 │
                                   │    Node.js      │
                                   │    Express.js   │
                                   │                 │
                                   │    systemd      │
                                   │                 │
                                   │ Server Monitor  │
                                   │ Activity Log    │
                                   │                 │
                                   │    MariaDB      │
                                   └─────────────────┘
```

### Komponen Server

Server Debian menjalankan beberapa komponen:

1. **Node.js** sebagai runtime.
2. **Express.js** sebagai service aplikasi.
3. **MariaDB** sebagai database server.
4. **systemd** sebagai pengelola service.
5. **Server Monitoring** untuk memantau resource.
6. **Activity Logging** untuk pencatatan aktivitas.

### Komponen Client

Windows digunakan sebagai client yang melakukan koneksi ke server menggunakan alamat IP server:

```text
192.168.10.50
```

dan port:

```text
3000
```

Dengan demikian, aplikasi tidak hanya berjalan pada `localhost`, tetapi dapat diakses melalui jaringan dari perangkat client.

---

## ⚙️ Cara Kerja Sistem

Alur sistem dimulai dari server Debian yang telah dikonfigurasi agar dapat berkomunikasi pada jaringan lokal.

1. Debian 13 dijalankan sebagai server.
2. Network interface server menggunakan IP `192.168.10.50`.
3. Client Windows berada pada jaringan yang sama dengan IP `192.168.10.12`.
4. Service `dimsum.service` dijalankan menggunakan systemd.
5. Service menjalankan aplikasi Node.js.
6. Express.js menyediakan layanan melalui port `3000`.
7. Client melakukan koneksi menuju `192.168.10.50:3000`.
8. Service berkomunikasi dengan database MariaDB.
9. Server monitoring mengambil informasi resource server.
10. Aktivitas tertentu dicatat melalui activity logging.
11. Kondisi CPU dan RAM dibandingkan dengan threshold yang telah ditentukan.
12. Jika terjadi masalah, administrator dapat melakukan pengecekan menggunakan command Linux, service status, log, dan pengujian konektivitas.

Secara sederhana:

```text
Client
  │
  │ Request melalui jaringan
  ▼
IP Server
192.168.10.50
  │
  │ Port 3000
  ▼
Node.js / Express.js
  │
  ├──────────────► MariaDB
  │
  ├──────────────► Server Monitoring
  │
  └──────────────► Activity Logging
```

---

## 🚀 Fitur Project

Project memiliki beberapa fitur yang mendukung pengelolaan layanan server:

* Dashboard
* Business Monitoring
* Product Management
* Order Management
* Server Monitoring
* Activity Logging
* Settings
* Database Management
* Service Management
* Network Connectivity Testing

Fitur aplikasi tetap digunakan sebagai layanan yang berjalan pada server, sedangkan sisi **monitoring, service management, jaringan, dan administrasi server** menjadi bagian penting dalam project.

---

## 🖥️ Server Monitoring & Management

Server Monitoring digunakan untuk mengetahui kondisi server secara berkala.

Informasi yang ditampilkan antara lain:

* Status server
* CPU usage
* RAM usage
* Uptime
* Hostname
* Platform
* Kernel/release
* Architecture
* CPU cores

Contoh informasi server:

```text
Hostname     : debian13
Platform     : linux
Architecture : x64
CPU Core     : 1
Status       : ONLINE
```

Monitoring ini berguna untuk melihat apakah server masih berada dalam kondisi normal atau mulai mengalami peningkatan penggunaan resource.

### CPU Monitoring

CPU monitoring digunakan untuk melihat tingkat penggunaan processor server.

Informasi tersebut dapat digunakan sebagai indikator apabila server mulai mengalami beban yang tinggi.

### RAM Monitoring

RAM monitoring digunakan untuk mengetahui penggunaan memory server.

Penggunaan RAM yang terlalu tinggi dapat menjadi salah satu indikator bahwa server perlu diperiksa lebih lanjut.

### Uptime Monitoring

Uptime digunakan untuk mengetahui berapa lama server telah berjalan sejak terakhir kali boot.

Informasi ini dapat membantu administrator mengetahui kestabilan waktu operasi server.

### Server Status

Status server memberikan informasi sederhana mengenai kondisi layanan.

```text
ONLINE
```

menunjukkan bahwa service masih dapat berjalan dan server dapat memberikan layanan.

---

## 📊 Resource Threshold

Untuk membantu membaca kondisi resource, CPU dan RAM menggunakan threshold.

| Penggunaan | Status   |
| ---------- | -------- |
| < 80%      | Normal   |
| 80% – 89%  | Warning  |
| ≥ 90%      | Critical |

Contoh:

```text
CPU Usage : 35%
Status    : NORMAL
```

Jika penggunaan meningkat:

```text
CPU Usage : 85%
Status    : WARNING
```

Jika penggunaan sangat tinggi:

```text
RAM Usage : 91%
Status    : CRITICAL
```

Threshold berfungsi sebagai indikator awal agar administrator dapat mengetahui kapan resource server perlu diperiksa.

---

## 📋 Activity Logging

Activity Logging digunakan untuk mencatat aktivitas sistem.

File log berada pada:

```text
logs/activity.log
```

Logging dapat digunakan untuk membantu:

* troubleshooting
* pemeriksaan aktivitas
* mengetahui kejadian pada sistem
* melihat aktivitas service
* melakukan analisis ketika terjadi masalah

Pencatatan aktivitas menjadi bagian penting dalam pengelolaan server karena administrator tidak hanya membutuhkan informasi kondisi server saat ini, tetapi juga membutuhkan riwayat aktivitas untuk melakukan pengecekan.

---

## 🗄️ Database

Database menggunakan **MariaDB** yang dijalankan pada sisi server.

Database:

```text
dimsum_delight
```

Tabel utama:

```text
products
orders
order_items
```

### Products

Digunakan untuk menyimpan data produk dan stok.

### Orders

Digunakan untuk menyimpan data pesanan.

Status pesanan:

```text
Menunggu
    ↓
Diproses
    ↓
Selesai
```

### Order Items

Digunakan untuk menyimpan detail produk dalam setiap pesanan.

Dalam konteks server, MariaDB berperan sebagai **database service** yang berjalan pada server dan digunakan oleh service aplikasi.

---

## 🚀 Deployment dan Service Management

Aplikasi dijalankan pada server Debian 13 dan dikelola sebagai service menggunakan **systemd**.

Lokasi project:

```text
/var/www/html/Project2
```

Nama service:

```text
dimsum.service
```

### Melihat Status Service

```bash
sudo systemctl status dimsum
```

### Menjalankan Service

```bash
sudo systemctl start dimsum
```

### Menghentikan Service

```bash
sudo systemctl stop dimsum
```

### Restart Service

```bash
sudo systemctl restart dimsum
```

### Enable Service

Agar service otomatis dijalankan ketika server melakukan boot:

```bash
sudo systemctl enable dimsum
```

Penggunaan systemd membuat service lebih mudah dikontrol tanpa harus menjalankan aplikasi secara manual setiap kali server dinyalakan.

---

## 🔐 Konsep Keamanan dan Stabilitas

Dalam project ini diterapkan beberapa pendekatan untuk menjaga kestabilan layanan:

* Service dikelola menggunakan systemd.
* Server menggunakan IP address yang jelas pada jaringan lokal.
* Akses layanan menggunakan port tertentu.
* CPU dan RAM dipantau.
* Resource memiliki threshold.
* Aktivitas dicatat melalui logging.
* Koneksi client-server diuji.
* Status service dapat diperiksa melalui systemd.
* Log service dapat diperiksa menggunakan `journalctl`.
* Resource server dapat diperiksa menggunakan command Linux.

Project menggunakan pendekatan monitoring yang sederhana dan ringan sehingga tidak membutuhkan platform monitoring tambahan yang kompleks.

---

## 📁 Struktur Project

```text
Project2/
├── config/
│   ├── monitoring.js
│   └── monitoringStatus.js
│
├── logs/
│   └── activity.log
│
├── public/
│   ├── css/
│   ├── js/
│   └── ...
│
├── server.js
├── package.json
└── ...
```

Folder `config` digunakan untuk konfigurasi monitoring.

Folder `logs` digunakan untuk menyimpan activity log.

Folder `public` berisi komponen client-side aplikasi.

File `server.js` digunakan sebagai entry point service Node.js.

---

## 📸 Screenshot

### 📊 Business Monitoring

![Business Monitoring](Screenshot/Screenshot%202026-08-28%20115448.png)

### 📋 Activity Log

![Activity Log](Screenshot/Screenshot%202026-08-28%20115542.png)

### 🖥️ Server Monitoring

![Server Monitoring](Screenshot/Screenshot%202026-08-28%20115559.png)

### ⚙️ Settings

![Settings](Screenshot/Screenshot%202026-08-28%20115613.png)

### 📸 Screenshot Lainnya

![Screenshot](Screenshot/Screenshot%202026-08-28%20115431.png)

![Screenshot](Screenshot/Screenshot%202026-08-28%20115505.png)

![Screenshot](Screenshot/Screenshot%202026-08-28%20115522.png)

---

## ▶️ Cara Menjalankan

Clone repository:

```bash
git clone https://github.com/novianaputt-wq/Arsitektur-web-2
```

Masuk ke folder project:

```bash
cd Arsitektur-web-2
```

Install dependency:

```bash
npm install
```

Jalankan aplikasi:

```bash
node server.js
```

Jika service systemd telah dikonfigurasi:

```bash
sudo systemctl start dimsum
```

Cek service:

```bash
sudo systemctl status dimsum
```

Aplikasi dapat diakses menggunakan:

```text
http://192.168.10.50:3000
```

Dashboard seller:

```text
http://192.168.10.50:3000/seller
```

---

## 🧪 Pengujian Server dan Jaringan

Pengujian dilakukan untuk memastikan server, service, dan koneksi jaringan dapat berjalan dengan baik.

### 1. Mengecek IP Address Server

```bash
ip addr
```

Server menggunakan:

```text
192.168.10.50
```

### 2. Mengecek Koneksi Client ke Server

Pada Windows:

```cmd
ping 192.168.10.50
```

Jika mendapatkan `Reply`, berarti koneksi dasar antara client dan server berhasil.

### 3. Mengecek Service

```bash
sudo systemctl status dimsum
```

### 4. Mengecek Layanan dari Server

```bash
curl http://localhost:3000
```

### 5. Mengakses dari Client

Client dapat mengakses:

```text
http://192.168.10.50:3000
```

### 6. Mengecek Resource Server

CPU dan proses:

```bash
top
```

Memory:

```bash
free -h
```

### 7. Mengecek Log Service

```bash
sudo journalctl -u dimsum
```

Log terbaru:

```bash
sudo journalctl -u dimsum -n 50
```

Pengujian ini membantu memastikan bahwa masalah dapat ditelusuri dari beberapa sisi, mulai dari **network connectivity, IP address, service, resource server, hingga log**.

---

## 🎥 Demo

Video demo project:

https://youtu.be/1la2yBKBuv0?si=eFNjFNOOjlzazwV9

Demo memperlihatkan penerapan server dan jaringan, mulai dari server Debian, akses menggunakan IP, service aplikasi, dashboard monitoring, hingga pengelolaan server.

---

## 🛠️ Troubleshooting

Troubleshooting dilakukan dengan melihat masalah dari sisi jaringan, service, resource, dan log.

### Service Tidak Berjalan

Cek:

```bash
sudo systemctl status dimsum
```

Restart:

```bash
sudo systemctl restart dimsum
```

### Client Tidak Bisa Terhubung

Cek IP server:

```bash
ip addr
```

Kemudian dari Windows:

```cmd
ping 192.168.10.50
```

Jika ping gagal, pengecekan dapat difokuskan pada konfigurasi jaringan dan konektivitas antara client dengan server.

### Aplikasi Tidak Dapat Diakses

Cek apakah service berjalan:

```bash
sudo systemctl status dimsum
```

Kemudian cek dari server:

```bash
curl http://localhost:3000
```

Jika localhost berhasil tetapi client tidak dapat mengakses, pemeriksaan dapat diarahkan pada koneksi jaringan, IP, dan port.

### Resource Server Tinggi

Cek proses:

```bash
top
```

Cek memory:

```bash
free -h
```

Kemudian lihat informasi monitoring untuk mengetahui CPU dan RAM yang sedang digunakan.

### Mengecek Log

```bash
sudo journalctl -u dimsum
```

Log aplikasi:

```text
logs/activity.log
```

Dengan pendekatan ini, troubleshooting tidak hanya dilakukan dari sisi aplikasi, tetapi juga dari sisi **server, service, resource, dan jaringan**.

---

## 🔄 Alur Keseluruhan Project

```text
                    CLIENT
              Windows 192.168.10.12
                       │
                       │
                  Network Lokal
                       │
                       ▼
              ┌─────────────────┐
              │  Debian 13      │
              │  Server         │
              │                 │
              │ 192.168.10.50   │
              └────────┬────────┘
                       │
              ┌────────┴────────┐
              │                 │
              ▼                 ▼
       systemd Service      Network Service
              │
              ▼
       Node.js / Express
              │
       ┌──────┴──────┐
       │             │
       ▼             ▼
    MariaDB     Monitoring
                    │
              ┌─────┼─────┐
              │     │     │
             CPU   RAM  Uptime
              │
              ▼
       Activity Logging
```

---

## 🌐 Konsep Network dan Server yang Diterapkan

Project ini menerapkan beberapa konsep utama dalam **Network & Server Administration**.

### 1. Client-Server

Windows berperan sebagai client yang meminta layanan dari Debian sebagai server.

### 2. IP Address

Server memiliki alamat:

```text
192.168.10.50
```

Client:

```text
192.168.10.12
```

IP digunakan sebagai identitas endpoint pada jaringan lokal.

### 3. Port

Layanan aplikasi menggunakan:

```text
Port 3000
```

Sehingga client dapat mengakses service melalui:

```text
192.168.10.50:3000
```

### 4. Network Connectivity

Koneksi client-server diuji menggunakan:

```bash
ping
```

Pengujian ini digunakan untuk mengetahui apakah komunikasi dasar antar perangkat dapat berjalan.

### 5. Service Management

Service aplikasi dikelola menggunakan:

```bash
systemctl
```

Hal ini merupakan bagian dari administrasi service pada Linux.

### 6. Server Monitoring

Server dipantau berdasarkan:

* CPU
* RAM
* Uptime
* Status server
* Informasi sistem

### 7. Resource Management

CPU dan RAM memiliki threshold sehingga kondisi resource dapat dikategorikan menjadi:

```text
NORMAL
WARNING
CRITICAL
```

### 8. Logging

Activity log digunakan sebagai sumber informasi ketika administrator perlu melakukan pengecekan aktivitas dan troubleshooting.

### 9. Database Server

MariaDB berjalan pada server dan digunakan oleh service aplikasi untuk menyimpan data.

### 10. Troubleshooting

Troubleshooting dilakukan dari beberapa layer:

```text
Network
   ↓
IP Address
   ↓
Port
   ↓
Service
   ↓
Application
   ↓
Database
   ↓
Resource Server
   ↓
Log
```

Dengan alur tersebut, proses troubleshooting menjadi lebih terstruktur karena administrator dapat menentukan bagian mana yang mengalami masalah.

---

## 🎓 Relevansi dengan TJKT

Project ini memiliki keterkaitan langsung dengan bidang **Teknik Jaringan Komputer dan Telekomunikasi (TJKT)** karena menerapkan konsep yang berhubungan dengan pengelolaan infrastruktur jaringan dan server.

Beberapa penerapan yang dilakukan antara lain:

* Administrasi Linux Server
* Konfigurasi IP Address
* Client-Server
* Jaringan lokal
* Port dan service
* Service management
* Monitoring server
* Resource management
* Logging
* Troubleshooting
* Database server
* Command Line Linux
* Pengelolaan service pada server

Aplikasi web pada project ini hanya menjadi salah satu layanan yang ditempatkan di dalam server.

Fokus project lebih luas, yaitu bagaimana **server dibangun sebagai pusat layanan, bagaimana client terhubung melalui jaringan, bagaimana service dijalankan, bagaimana resource dipantau, serta bagaimana administrator melakukan troubleshooting ketika terjadi masalah**.

---

## 📌 Status Project

| Komponen                     | Status     |
| ---------------------------- | ---------- |
| Debian 13 Server             | ✅ Berjalan |
| Network Configuration        | ✅ Berjalan |
| IP Address Server            | ✅ Berjalan |
| Client-Server Connectivity   | ✅ Berjalan |
| Node.js                      | ✅ Berjalan |
| Express.js                   | ✅ Berjalan |
| MariaDB                      | ✅ Berjalan |
| systemd Service              | ✅ Berjalan |
| Server Monitoring            | ✅ Berjalan |
| CPU Monitoring               | ✅ Berjalan |
| RAM Monitoring               | ✅ Berjalan |
| Uptime Monitoring            | ✅ Berjalan |
| Resource Threshold           | ✅ Berjalan |
| Activity Logging             | ✅ Berjalan |
| Network Connectivity Testing | ✅ Berjalan |
| Business Monitoring          | ✅ Berjalan |
| Product Management           | ✅ Berjalan |
| Order Management             | ✅ Berjalan |

---

## 📝 Kesimpulan

Dimsum Delight Server Monitoring & Management merupakan project yang menerapkan konsep **Network & Server Administration** dengan Debian 13 sebagai server utama.

Project tidak hanya membangun sebuah aplikasi, tetapi juga menunjukkan bagaimana sebuah layanan dapat ditempatkan dan dikelola dalam lingkungan server.

Server Debian digunakan untuk menjalankan service aplikasi, database, monitoring, logging, dan berbagai kebutuhan administrasi server. Client Windows kemudian melakukan komunikasi dengan server melalui jaringan lokal menggunakan IP `192.168.10.50` dan port `3000`.

Dari sisi network, project menerapkan konsep **IP Address, client-server, konektivitas jaringan, port, dan pengujian komunikasi**.

Dari sisi server, project menerapkan **administrasi Linux, systemd service management, CPU monitoring, RAM monitoring, uptime monitoring, resource threshold, activity logging, database server, serta troubleshooting**.

Dengan demikian, aplikasi Dimsum Delight pada project ini bukan menjadi satu-satunya fokus. Aplikasi digunakan sebagai layanan yang berjalan di dalam sebuah **infrastruktur server**, sedangkan pengelolaan server dan jaringan menjadi bagian utama dari implementasi project.

---

## 🔗 Portofolio Lengkap

Portfolio:

[Noviana Putri Yuliani](https://portfolio.edusoftcenter.com/contributors/noviana-putri-yuliani)

Repository GitHub:

https://github.com/novianaputt-wq/Arsitektur-web-2

Video Demo:

https://youtu.be/1la2yBKBuv0?si=eFNjFNOOjlzazwV9

---

## 📋 Project Information

**Project:** Dimsum Delight Server Monitoring & Management

**Category:** Network & Server Administration

**Operating System:** Debian 13

**Server IP:** `192.168.10.50`

**Client IP:** `192.168.10.12`

**Application Port:** `3000`

**Runtime:** Node.js `v22.23.2`

**Database:** MariaDB

**Database Name:** `dimsum_delight`

**Service:** `dimsum.service`

**Project Path:**

```text
/var/www/html/Project2
```

**Network Model:** Client-Server

**Environment:** VirtualBox

**Repository:**

https://github.com/novianaputt-wq/Arsitektur-web-2

**Demo:**

https://youtu.be/1la2yBKBuv0?si=eFNjFNOOjlzazwV9
