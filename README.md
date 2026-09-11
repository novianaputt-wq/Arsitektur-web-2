````markdown
# 🥟 Dimsum Delight Web Server

**Dimsum Delight Web Server** merupakan aplikasi pemesanan dan pengelolaan produk dimsum berbasis web yang dikembangkan menggunakan **Node.js, Express.js, MariaDB, HTML, CSS, dan JavaScript** serta dijalankan pada **server Debian 13**.

Project ini tidak hanya berfokus pada pembuatan aplikasi, tetapi juga menerapkan konsep **jaringan client-server, Web Server, deployment, administrasi server Linux, service management, database server, komunikasi melalui jaringan lokal, activity logging, resource monitoring, dan antisipasi penggunaan resource server berlebih**.

Pada implementasinya, Debian 13 digunakan sebagai server yang menyediakan layanan aplikasi kepada client melalui jaringan. Aplikasi dijalankan menggunakan **systemd** sehingga dapat dikelola sebagai service. Selain itu, tersedia fitur **Server Monitoring** untuk memantau CPU, RAM, uptime, dan status server sebagai bagian dari administrasi serta pemeliharaan server.


# 📌 Daftar Isi

* [Tentang Project](#-tentang-project)
* [Tujuan Project](#-tujuan-project)
* [Tech Stack](#-tech-stack)
* [Tools yang Digunakan](#-tools-yang-digunakan)
* [Arsitektur Sistem](#-arsitektur-sistem)
* [Cara Kerja Sistem](#-cara-kerja-sistem)
* [Fitur Project](#-fitur-project)
* [Server Monitoring](#-server-monitoring)
* [Resource Threshold](#-resource-threshold)
* [Activity Logging](#-activity-logging)
* [Database](#-database)
* [REST API](#-rest-api)
* [Deployment dan Service Management](#-deployment-dan-service-management)
* [Struktur Project](#-struktur-project)
* [Screenshot](#-screenshot)
* [Cara Menjalankan](#-cara-menjalankan)
* [Demo](#-demo)
* [Troubleshooting](#-troubleshooting)
* [Kesimpulan](#-kesimpulan)
* [Portofolio](#-portofolio)

---

# 🎯 Tentang Project

Dimsum Delight merupakan aplikasi web yang digunakan sebagai media penerapan **arsitektur jaringan client-server**.

Aplikasi ditempatkan pada server Debian 13 dan dapat diakses oleh client menggunakan **alamat IP server melalui jaringan lokal**. Server bertugas menyediakan layanan aplikasi, memproses request dari client, mengelola database, serta melakukan monitoring terhadap kondisi sistem.

Sistem memiliki dua sisi utama:

### 👤 Customer

Customer dapat:

* Mengakses website melalui jaringan.
* Melihat daftar produk.
* Melihat harga produk.
* Melihat stok.
* Melakukan pemesanan.
* Mengisi informasi pelanggan.
* Mengirim pesanan ke server.

### 🏪 Seller / Administrator

Seller memiliki dashboard untuk:

* Melihat kondisi bisnis.
* Mengelola produk.
* Mengelola pesanan.
* Memantau aktivitas sistem.
* Melihat kondisi server.
* Memantau penggunaan resource server.
* Membantu pengecekan ketika terjadi masalah pada layanan.

Dengan demikian, project ini tidak hanya menunjukkan pembuatan aplikasi, tetapi juga penerapan **client-server, administrasi Web Server, pengelolaan server Linux, monitoring, dan troubleshooting** yang berkaitan dengan bidang TJKT.

---

# 🎯 Tujuan Project

Project ini dibuat untuk menerapkan konsep yang dipelajari pada bidang **Teknik Jaringan Komputer dan Telekomunikasi (TJKT)**, khususnya dalam pengelolaan **server dan layanan jaringan**.

Tujuan utama project:

1. Membuat aplikasi yang dapat berjalan pada server Linux.
2. Menempatkan aplikasi pada server Debian 13.
3. Mengatur aplikasi agar dapat diakses melalui jaringan lokal.
4. Menghubungkan client dengan server menggunakan alamat IP dan port.
5. Menghubungkan aplikasi dengan database MariaDB.
6. Melakukan deployment aplikasi Node.js.
7. Mengelola aplikasi menggunakan systemd.
8. Menerapkan monitoring resource server.
9. Menyediakan indikator kondisi CPU dan RAM.
10. Mencatat aktivitas sistem menggunakan activity log.
11. Menyediakan informasi kondisi server untuk membantu troubleshooting.
12. Memberikan antisipasi ketika resource server mengalami penggunaan tinggi.

---

# 🧰 Tech Stack

| Teknologi                   | Fungsi                                               |
| --------------------------- | ---------------------------------------------------- |
| **Debian 13**               | Operating System server                              |
| **Node.js**                 | Runtime untuk menjalankan aplikasi pada server       |
| **Express.js**              | Framework backend dan HTTP server                    |
| **MariaDB**                 | Database server aplikasi                             |
| **MySQL2**                  | Driver koneksi Node.js ke MariaDB                    |
| **HTML**                    | Struktur halaman web                                 |
| **CSS**                     | Tampilan dan layout dashboard                        |
| **JavaScript**              | Interaksi frontend dan komunikasi client-server      |
| **REST API**                | Komunikasi data antara client dan server             |
| **systemd**                 | Menjalankan dan mengelola aplikasi sebagai service   |
| **Linux OS Monitoring API** | Mengambil informasi CPU, RAM, uptime, dan sistem     |
| **VirtualBox**              | Menjalankan environment server Debian secara virtual |

---

# 🛠️ Tools yang Digunakan

## 1. Debian 13

Debian digunakan sebagai **server utama** tempat aplikasi Dimsum Delight dijalankan.

Server bertanggung jawab terhadap:

```text
Client
   ↓
Jaringan Lokal
   ↓
Debian Server
   ↓
Node.js
   ↓
Express.js
   ↓
MariaDB
````

Debian juga digunakan untuk menjalankan:

* Node.js
* MariaDB
* systemd service
* Activity Logging
* Server Monitoring

Dalam project ini, Debian berperan sebagai pusat layanan yang menerima request dari client melalui jaringan.

---

## 2. Node.js

Node.js digunakan sebagai runtime untuk menjalankan aplikasi pada server.

Node.js menjalankan file utama:

```text
server.js
```

Versi Node.js yang digunakan pada server:

```text
Node.js v22.23.2
```

Node.js menangani:

* Request dari client.
* Komunikasi antara client dan server.
* Pengolahan data aplikasi.
* Komunikasi database.
* Server monitoring.
* Activity logging.

Node.js menjadi bagian utama dari layanan aplikasi yang berjalan pada server Debian.

---

## 3. Express.js

Express.js digunakan sebagai framework backend sekaligus HTTP server.

Alur komunikasi:

```text
Browser
   ↓
HTTP Request
   ↓
Express.js
   ↓
Proses Request
   ↓
MariaDB
   ↓
HTTP Response
   ↓
Browser
```

Express digunakan untuk menangani request dari client dan memberikan response melalui jaringan.

Dengan konsep tersebut, client tidak mengakses database secara langsung. Seluruh proses data dilakukan melalui server.

---

## 4. MariaDB

MariaDB digunakan sebagai database server utama.

Database:

```text
dimsum_delight
```

Database menyimpan data seperti:

* Produk
* Pesanan
* Detail pesanan
* Informasi transaksi

Contoh hubungan data:

```text
products
   │
   │ product_id
   ↓
order_items
   │
   │ order_id
   ↓
orders
```

MariaDB berada pada sisi server dan digunakan oleh aplikasi server untuk mengelola data.

---

## 5. MySQL2

Library `mysql2` digunakan sebagai penghubung antara Node.js dengan MariaDB.

Konfigurasinya berada pada:

```text
config/db.js
```

Alur komunikasinya:

```text
Node.js
   ↓
mysql2
   ↓
MariaDB
   ↓
dimsum_delight
```

Connection pool digunakan agar server dapat mengelola koneksi database dengan lebih efisien.

---

# 🖥️ Arsitektur Sistem

Secara keseluruhan, arsitektur Dimsum Delight menggunakan konsep **client-server**:

```text
                 CLIENT
                   │
                   ▼
             Web Browser
                   │
                   │ HTTP
                   ▼
             Jaringan Lokal
                   │
                   ▼
        ┌─────────────────────┐
        │    Debian 13 Server │
        │                     │
        │    Node.js          │
        │       │             │
        │   Express.js        │
        │       │             │
        │       ├──── Komunikasi Client
        │       │
        │       ├──── Monitoring
        │       │
        │       └──── Logging
        │                     │
        │       systemd      │
        │         │           │
        └─────────┼───────────┘
                  │
                  ▼
             MariaDB
                  │
                  ▼
          dimsum_delight
```

Client mengakses server melalui jaringan menggunakan alamat IP server dan port aplikasi.

Server kemudian menerima request, memproses data, berkomunikasi dengan database, dan mengirimkan response kembali kepada client.

---

# ⚙️ Cara Kerja Sistem

## 1. Customer membuka website

Browser client mengakses:

```text
http://IP-SERVER:3000
```

Request dikirim melalui jaringan menuju server Debian 13.

Server menerima request pada port aplikasi yang digunakan.

---

## 2. Express memproses request

Express.js memproses request yang diterima dari client.

Alurnya:

```text
Client
   ↓
HTTP Request
   ↓
Debian Server
   ↓
Express.js
   ↓
Proses Request
```

Server kemudian menentukan proses atau data yang diperlukan oleh client.

---

## 3. Database mengirimkan data

Jika request membutuhkan data, server melakukan komunikasi dengan MariaDB.

Alurnya:

```text
Express.js
   ↓
MySQL2
   ↓
MariaDB
   ↓
Database
   ↓
Data
```

Data kemudian diproses oleh server sebelum dikirimkan kembali kepada client.

---

## 4. Frontend menampilkan data

Setelah server memberikan response, JavaScript pada browser memproses data tersebut.

Alurnya:

```text
Server
   ↓
HTTP Response
   ↓
Jaringan
   ↓
Browser Client
   ↓
JavaScript
   ↓
Tampilan Website
```

Dengan demikian, komunikasi antara client dan server berlangsung melalui jaringan.

---

# 🛒 Fitur Project

## Customer

* Mengakses website melalui jaringan.
* Daftar produk.
* Harga produk.
* Stok produk.
* Pemesanan.
* Informasi pelanggan.
* Pengiriman data pesanan ke server.

## Seller Dashboard

Dashboard seller terdiri dari:

```text
Dashboard
Business Monitoring
Product Management
Order Management
Activity Logs
Server Monitoring
Settings
```

Dashboard juga digunakan sebagai media untuk melihat kondisi aplikasi dan server.

---

# 📊 Business Monitoring

Business Monitoring digunakan untuk melihat kondisi operasional bisnis berdasarkan data yang diproses oleh server.

Informasi yang dapat ditampilkan:

* Total transaksi.
* Total pendapatan.
* Jumlah produk.
* Stok produk.
* Status pesanan.
* Produk yang terjual.

Alurnya:

```text
Client
   ↓
Server
   ↓
MariaDB
   ↓
Data
   ↓
Server
   ↓
Client Dashboard
```

Data diproses pada sisi server sebelum ditampilkan kepada client.

---

# 📦 Product Management

Fitur Product Management digunakan untuk mengelola data produk pada server.

Informasi produk meliputi:

* ID produk.
* Nama produk.
* Deskripsi.
* Harga.
* Gambar.
* Stok.
* Waktu pembuatan.

Data produk disimpan pada tabel:

```text
products
```

Pengelolaan dilakukan melalui aplikasi yang berjalan pada server, sedangkan browser berfungsi sebagai client.

---

# 📋 Order Management

Order Management digunakan untuk mengelola pesanan customer yang dikirim melalui jaringan ke server.

Status pesanan:

```text
Menunggu
    ↓
Diproses
    ↓
Selesai
```

Sistem juga menyimpan timestamp yang berkaitan dengan proses pesanan.

Contohnya:

```text
created_at
processed_at
completed_at
```

Alur sederhananya:

```text
Customer
   ↓
Jaringan
   ↓
Server
   ↓
Database
   ↓
Seller Dashboard
```

Hal tersebut menunjukkan proses pertukaran data antara client, server, dan database.

---

# 🖥️ Server Monitoring

Salah satu bagian utama project adalah **Server Monitoring**.

Fitur ini digunakan untuk melihat kondisi server Debian secara langsung melalui dashboard.

Data monitoring diambil menggunakan Node.js `os` module dan diproses oleh server sebelum ditampilkan pada dashboard.

Monitoring mencakup:

* CPU Usage.
* CPU Core.
* RAM Usage.
* Uptime.
* Status server.
* Status resource.
* Threshold CPU.
* Threshold RAM.

Fitur ini digunakan sebagai bagian dari **administrasi server dan antisipasi gangguan akibat penggunaan resource yang terlalu tinggi**.

---

# 📈 Cara Kerja Monitoring

Server mengambil informasi kondisi sistem kemudian mengirimkan hasil monitoring kepada client.

Alurnya:

```text
Debian Server
   ↓
Node.js OS Monitoring
   ↓
CPU / RAM / Uptime
   ↓
Server Processing
   ↓
Client Browser
   ↓
Server Monitoring Dashboard
```

Contoh informasi yang ditampilkan:

```json
{
  "success": true,
  "server": {
    "hostname": "debian13",
    "cpuCores": 1,
    "cpuUsage": "0.2%",
    "memoryUsage": "16.4%",
    "uptime": "3 jam 15 menit",
    "status": "ONLINE"
  }
}
```

Data tersebut membantu administrator melihat kondisi server tanpa harus selalu melakukan pengecekan melalui terminal.

---

# 🚨 Resource Threshold

Monitoring menggunakan threshold untuk membedakan kondisi resource server.

### CPU

```text
< 80%
   ↓
🟢 NORMAL

80% - 89%
   ↓
🟠 WARNING

≥ 90%
   ↓
🔴 CRITICAL
```

### Memory

```text
< 80%
   ↓
🟢 NORMAL

80% - 89%
   ↓
🟠 WARNING

≥ 90%
   ↓
🔴 CRITICAL
```

Konfigurasi threshold disimpan secara terpisah pada:

```text
config/monitoring.js
```

Contohnya:

```javascript
cpu: {
    warning: 80,
    critical: 90
}
```

Dengan cara tersebut, penggunaan resource server dapat dikategorikan sehingga administrator lebih mudah mengetahui kondisi server.

---

# 🧠 Monitoring Status Logic

Status resource server diproses melalui:

```text
config/monitoringStatus.js
```

Logic:

```text
CPU/RAM Value
      │
      ▼
Compare Threshold
      │
      ├── < Warning
      │       ↓
      │    NORMAL
      │
      ├── >= Warning
      │       ↓
      │    WARNING
      │
      └── >= Critical
              ↓
           CRITICAL
```

Response monitoring juga memberikan informasi status:

```json
{
  "level": "normal",
  "label": "NORMAL",
  "message": "Resource usage is within normal limits."
}
```

Status tersebut membantu administrator melakukan pengecekan kondisi server berdasarkan penggunaan resource.

---

# 🔔 Konsep Alert

Project ini menggunakan konsep **local server alert**.

Tujuannya adalah memberikan informasi ketika penggunaan resource server berada pada kondisi yang perlu diperhatikan.

Contoh:

```text
CPU Usage
92%

🔴 CRITICAL

Resource usage is critically high.
```

Dengan konsep tersebut administrator dapat mengetahui adanya lonjakan penggunaan resource melalui dashboard.

> Alert pada project ini difokuskan sebagai mekanisme antisipasi dan monitoring internal server tanpa menggunakan layanan pesan eksternal.

---

# 📝 Activity Logging

Project menyediakan Activity Logs untuk mencatat aktivitas sistem.

File log:

```text
logs/activity.log
```

Alurnya:

```text
Aktivitas Sistem
       ↓
writeLog()
       ↓
activity.log
       ↓
Activity Logs Dashboard
```

Logging berguna untuk:

* Monitoring aktivitas.
* Troubleshooting.
* Mengetahui aktivitas sistem.
* Membantu pemeriksaan ketika terjadi masalah pada layanan.
* Membantu administrator melakukan pengecekan aktivitas server.

---

# 🗄️ Database

Database utama:

```text
dimsum_delight
```

Tabel utama:

```text
products
orders
order_items
```

Database berada pada sisi server dan digunakan untuk menyimpan data aplikasi.

### Products

Menyimpan informasi produk.

```text
id
name
description
price
image
stock
created_at
```

### Orders

Menyimpan informasi pesanan.

```text
id
customer_name
customer_phone
notes
total_price
status
created_at
processed_at
completed_at
```

### Order Items

Menyimpan detail produk yang terdapat pada setiap pesanan.

```text
id
order_id
product_id
quantity
subtotal
```

---

# 🔌 REST API

Backend menyediakan mekanisme komunikasi data antara **client dan server**.

API digunakan agar client dapat meminta atau mengirim data melalui layanan yang berjalan pada server tanpa mengakses database secara langsung.

Alur komunikasi:

```text
Client
   ↓
HTTP Request
   ↓
Debian Server
   ↓
Node.js / Express.js
   ↓
MariaDB
   ↓
Node.js / Express.js
   ↓
HTTP Response
   ↓
Client
```

Pada project ini, komunikasi server juga digunakan untuk memberikan informasi mengenai kondisi server kepada dashboard.

Informasi yang dapat digunakan untuk monitoring meliputi:

```text
Hostname
Platform
Kernel Release
Architecture
CPU Core
CPU Usage
RAM Usage
CPU Status
Memory Status
Uptime
Server Status
Threshold
```

Dengan konsep tersebut, client dapat memperoleh data dari server melalui layanan aplikasi tanpa berhubungan langsung dengan database.

---

# ⚙️ Deployment dan Service Management

Aplikasi ditempatkan pada server Debian dan dikonfigurasi sebagai **systemd service**.

Nama service:

```text
dimsum.service
```

Alur deployment:

```text
Source Code
    ↓
Debian Server
    ↓
Node.js
    ↓
server.js
    ↓
systemd
    ↓
dimsum.service
    ↓
Application Running
    ↓
Client Access
```

Deployment dilakukan agar aplikasi dapat berjalan sebagai layanan pada server dan dapat diakses oleh client melalui jaringan.

---

# 🔄 systemd

systemd digunakan agar aplikasi dapat dikelola sebagai service pada server Linux.

### Menjalankan aplikasi

```bash
systemctl start dimsum
```

### Mengecek status

```bash
systemctl status dimsum
```

### Restart aplikasi

```bash
systemctl restart dimsum
```

### Menghentikan aplikasi

```bash
systemctl stop dimsum
```

### Mengaktifkan saat boot

```bash
systemctl enable dimsum
```

Dengan systemd, aplikasi dapat dikelola secara lebih terstruktur sebagai layanan pada server Linux.

---

# 🔐 Konsep Keamanan dan Stabilitas

Beberapa penerapan yang digunakan:

* Database tidak diakses langsung oleh client.
* Client berkomunikasi dengan server melalui layanan aplikasi.
* Database berada pada sisi server.
* Aplikasi dijalankan sebagai service.
* Activity log digunakan untuk pemeriksaan aktivitas.
* CPU dan RAM dipantau.
* Threshold digunakan untuk mendeteksi kondisi resource tinggi.
* Konfigurasi monitoring dipisahkan dari konfigurasi database.
* Aplikasi dapat diakses melalui alamat IP dan port server.

Struktur konfigurasi:

```text
config/
├── db.js
├── monitoring.js
└── monitoringStatus.js
```

Dengan pemisahan tersebut, konfigurasi database dan monitoring tidak tercampur.

---

# 📁 Struktur Project

```text
Project2/
│
├── config/
│   ├── db.js
│   ├── monitoring.js
│   └── monitoringStatus.js
│
├── logs/
│   └── activity.log
│
├── public/
│   ├── css/
│   ├── js/
│   │   └── seller.js
│   ├── images/
│   ├── index.html
│   └── seller.html
│
├── server.js
├── package.json
├── package-lock.json
└── README.md
```

---

## 📸 Screenshot

### 🏠 Dashboard

![Dashboard](./Screenshot/Screenshot%202026-08-28%20115431.png)

### 📊 Business Monitoring

![Business Monitoring](./Screenshot/Screenshot%202026-08-28%20115448.png)

### 📦 Product Management

![Product Management](./Screenshot/Screenshot%202026-08-28%20115505.png)

### 🛒 Order Management

![Order Management](./Screenshot/Screenshot%202026-08-28%20115522.png)

### 📋 Activity Logs

![Activity Logs](./Screenshot/Screenshot%202026-08-28%20115542.png)

### 🖥️ Server Monitoring

![Server Monitoring](./Screenshot/Screenshot%202026-08-28%20115559.png)

### ⚙️ Settings

![Settings](./Screenshot/Screenshot%202026-08-28%20115613.png)

> Screenshot digunakan sebagai dokumentasi tampilan aplikasi yang dijalankan pada Web Server Debian dan diakses melalui jaringan.

---

# 🚀 Cara Menjalankan

## 1. Clone Repository

```bash
git clone <https://github.com/novianaputt-wq/Arsitektur-web-2>
cd Project2
```

## 2. Install Dependency

```bash
npm install
```

## 3. Konfigurasi Database

Buat database:

```sql
CREATE DATABASE dimsum_delight;
```

Kemudian sesuaikan:

```text
config/db.js
```

dengan konfigurasi MariaDB pada server.

> Jangan memasukkan password database asli ke repository publik.

## 4. Jalankan Server

```bash
node server.js
```

Server akan berjalan pada:

```text
http://localhost:3000
```

Untuk akses melalui jaringan:

```text
http://IP-SERVER:3000
```

## 5. Jalankan Menggunakan systemd

```bash
systemctl start dimsum
```

Cek:

```bash
systemctl status dimsum
```

## 6. Akses Website

```text
http://IP-SERVER:3000
```

Seller Dashboard:

```text
http://IP-SERVER:3000/seller
```

---

# 🧪 Pengujian Server

Pengujian dilakukan untuk memastikan layanan pada server berjalan dengan baik.

Health service dapat diuji menggunakan:

```bash
curl -s http://localhost:3000/api/server/health
```

Contoh hasil:

```json
{
  "success": true,
  "server": {
    "hostname": "debian13",
    "platform": "linux",
    "architecture": "x64",
    "cpuCores": 1,
    "cpuUsage": "0.2%",
    "memoryUsage": "16.4%",
    "uptime": "3 jam 15 menit",
    "status": "ONLINE"
  }
}
```

Status service dapat diperiksa dengan:

```bash
systemctl status dimsum --no-pager
```

Pengecekan port:

```bash
ss -tulpn | grep 3000
```

Pengujian tersebut digunakan untuk memastikan service berjalan dan port aplikasi tersedia pada server.

---

# 🌐 Demo

Project dijalankan pada server Debian melalui jaringan lokal.

### Customer

```text
http://192.168.10.50:3000
```

### Seller Dashboard

```text
http://192.168.10.50:3000/seller
```

### Server Health API

```text
http://192.168.10.50:3000/api/server/health
```

> Karena menggunakan IP jaringan lokal, demo hanya dapat diakses dari perangkat yang berada pada jaringan yang dapat terhubung ke server.

---

# 🔧 Troubleshooting

Beberapa pengecekan dasar ketika aplikasi mengalami masalah:

### Cek service

```bash
systemctl status dimsum
```

### Restart aplikasi

```bash
systemctl restart dimsum
```

### Cek layanan dari server

```bash
curl -s http://localhost:3000/api/server/health
```

### Cek port

```bash
ss -tulpn | grep 3000
```

### Cek log service

```bash
journalctl -u dimsum -n 50 --no-pager
```

### Cek koneksi database

Periksa pesan aplikasi:

```text
Database MariaDB terhubung!
```

Jika terjadi masalah database, periksa status MariaDB:

```bash
systemctl status mariadb
```

Pengecekan tersebut membantu menentukan apakah masalah berasal dari **service aplikasi, port, database, atau layanan server**.

---

# 📌 Alur Keseluruhan Project

Secara sederhana, keseluruhan sistem bekerja seperti berikut:

```text
                 USER
                   │
                   ▼
             Web Browser
                   │
                   ▼
             Jaringan Lokal
                   │
                   ▼
          ┌────────────────┐
          │   Debian 13    │
          │     Server     │
          └───────┬────────┘
                  │
                  ▼
             systemd
                  │
                  ▼
             Node.js
                  │
                  ▼
             Express.js
          ┌───────┼─────────┐
          │       │         │
          ▼       ▼         ▼
       Product  Order    Monitoring
          │       │         │
          └───────┼─────────┘
                  ▼
               MariaDB
                  │
                  ▼
          dimsum_delight

Network:
Client ────────────┐
                   │
IP Server ─────────┤
Port 3000 ─────────┤
                   ▼
              Web Server
                   │
                   ▼
             Client Access

Monitoring:
CPU ────────────┐
RAM ────────────┤
Uptime ─────────┤
Service ────────┤
                ▼
          Server Monitoring
                │
                ▼
       NORMAL / WARNING /
          CRITICAL
```

---

# 🧩 Konsep DevOps yang Diterapkan

Walaupun project ini tidak menggunakan tools monitoring berat seperti Prometheus atau Grafana, beberapa konsep pengelolaan server dan layanan tetap diterapkan.

### Development

```text
Node.js
Express.js
HTML
CSS
JavaScript
```

### Database

```text
MariaDB
MySQL2
```

### Server & Network

```text
Debian 13
Client-Server
Jaringan Lokal
IP Server
Port 3000
```

### Deployment

```text
Debian 13
systemd
dimsum.service
```

### Monitoring

```text
CPU
RAM
Uptime
Service Status
Server Health
Threshold
```

### Logging

```text
activity.log
systemd journal
```

Sehingga konsep sederhananya:

```text
Develop
   ↓
Deploy
   ↓
Connect
   ↓
Run
   ↓
Monitor
   ↓
Detect
   ↓
Anticipate
   ↓
Troubleshoot
```

---

# 🎓 Relevansi dengan TJKT

Project ini memiliki keterkaitan dengan pembelajaran TJKT karena mencakup beberapa aspek jaringan dan administrasi sistem, seperti:

* Penerapan konsep client-server.
* Penggunaan jaringan lokal.
* Penggunaan alamat IP server.
* Penggunaan port layanan.
* Linux server administration.
* Konfigurasi Web Server.
* Deployment aplikasi pada server.
* Pengelolaan service Linux.
* Konfigurasi database server.
* Komunikasi data antara client dan server.
* Monitoring resource server.
* Troubleshooting service.
* Pengelolaan log.
* Pengujian konektivitas layanan.

Dengan demikian, project tidak hanya menunjukkan kemampuan membuat aplikasi, tetapi juga bagaimana sebuah **server menyediakan layanan kepada client melalui jaringan, dikelola, dipantau, dan dilakukan troubleshooting** ketika terjadi masalah.

---

# 📊 Status Project

| Komponen                 | Status    |
| ------------------------ | --------- |
| Web Application          | ✅ Selesai |
| Customer Page            | ✅ Selesai |
| Seller Dashboard         | ✅ Selesai |
| Product Management       | ✅ Selesai |
| Order Management         | ✅ Selesai |
| Business Monitoring      | ✅ Selesai |
| MariaDB Integration      | ✅ Selesai |
| REST API                 | ✅ Selesai |
| systemd Service          | ✅ Selesai |
| Activity Logging         | ✅ Selesai |
| CPU Monitoring           | ✅ Selesai |
| RAM Monitoring           | ✅ Selesai |
| Server Health API        | ✅ Selesai |
| Resource Threshold       | ✅ Selesai |
| Server Status Monitoring | ✅ Selesai |

---

# 📝 Kesimpulan

Dimsum Delight Web Server merupakan project yang menggabungkan **jaringan client-server, Web Server, server Linux, database, deployment, service management, dan monitoring server** dalam satu sistem.

Aplikasi dijalankan pada Debian 13 sebagai server dan dapat diakses oleh client melalui **alamat IP dan port pada jaringan lokal**. Node.js dan Express.js digunakan untuk menyediakan layanan aplikasi, sedangkan MariaDB digunakan sebagai database pada sisi server.

Pengelolaan aplikasi dilakukan menggunakan systemd sehingga aplikasi dapat dijalankan dan dikontrol sebagai service pada server Linux.

Selain fungsi utama seperti pengelolaan produk dan pesanan, project juga menerapkan **komunikasi client-server, Activity Logging, Server Monitoring, CPU Monitoring, RAM Monitoring, uptime monitoring, resource threshold, dan troubleshooting service**.

Penerapan monitoring tersebut bertujuan sebagai **langkah antisipasi**, sehingga administrator dapat mengetahui kondisi server dan mengenali penggunaan resource yang tinggi sebelum berkembang menjadi masalah yang lebih serius.

Project ini menunjukkan bahwa sebuah sistem jaringan tidak hanya membutuhkan layanan yang dapat berjalan, tetapi juga membutuhkan **server yang dapat dikonfigurasi, dikelola, dipantau, dan dilakukan troubleshooting** agar layanan tetap dapat digunakan oleh client dengan baik.

---

# 🌐 Portofolio Lengkap

Dokumentasi lengkap mengenai project, proses pengembangan, implementasi jaringan client-server, Web Server, administrasi server, monitoring server, serta hasil project dapat dilihat pada:

**Edusoft Portfolio**

[Noviana Putri Yuliani](https://portfolio.edusoftcenter.com/contributors/noviana-putri-yuliani)

---

## 👩‍💻 Project Information

**Project:** Dimsum Delight Web Server
**Bidang:** Network & System / Web Server
**Jurusan:** TJKT
**Server OS:** Debian 13
**Arsitektur:** Client-Server
**Jaringan:** Jaringan Lokal
**Backend:** Node.js + Express.js
**Database:** MariaDB
**Service Management:** systemd
**Monitoring:** CPU, RAM, Uptime & Server Health
**Logging:** Activity Log

---

```
```
