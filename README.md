# 🥟 Dimsum Delight Web Server

**Dimsum Delight Web Server** merupakan aplikasi pemesanan dan pengelolaan produk dimsum berbasis web yang dikembangkan menggunakan **Node.js, Express.js, MariaDB, HTML, CSS, dan JavaScript** serta dijalankan pada **server Debian 13**.

Project ini tidak hanya berfokus pada pembuatan aplikasi pemesanan, tetapi juga menerapkan konsep **Web Server, deployment aplikasi, service management, database management, REST API, activity logging, resource monitoring, dan antisipasi penggunaan resource server berlebih**.

Pada sisi server, aplikasi dijalankan sebagai service menggunakan **systemd**, sehingga aplikasi dapat dikelola seperti service server pada umumnya. Project juga menyediakan **Server Monitoring** untuk memantau penggunaan CPU, RAM, uptime, serta status server melalui dashboard penjual.


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

Dimsum Delight merupakan aplikasi web yang dibuat untuk membantu proses pengelolaan bisnis dimsum secara terintegrasi.

Sistem memiliki dua sisi utama:

### 👤 Customer

Customer dapat:

* Melihat daftar produk.
* Melihat harga produk.
* Melihat stok.
* Melakukan pemesanan.
* Mengisi informasi pelanggan.
* Mengirim pesanan ke sistem.

### 🏪 Seller / Administrator

Seller memiliki dashboard untuk:

* Melihat kondisi bisnis.
* Mengelola produk.
* Mengelola pesanan.
* Memantau aktivitas sistem.
* Melihat kondisi server.
* Memantau penggunaan resource server.

Dengan demikian, aplikasi tidak hanya digunakan sebagai website pemesanan, tetapi juga menjadi media penerapan **administrasi Web Server dan dasar DevOps**.

---

# 🎯 Tujuan Project

Project ini dibuat untuk menerapkan konsep yang dipelajari pada bidang **Teknik Jaringan Komputer dan Telekomunikasi (TJKT)**, khususnya dalam pengelolaan Web Server.

Tujuan utama project:

1. Membuat aplikasi web yang dapat berjalan pada server Linux.
2. Menghubungkan aplikasi dengan database MariaDB.
3. Melakukan deployment aplikasi Node.js.
4. Mengelola aplikasi menggunakan systemd.
5. Menyediakan REST API untuk komunikasi antara frontend dan backend.
6. Menerapkan monitoring resource server.
7. Menyediakan indikator kondisi CPU dan RAM.
8. Mencatat aktivitas sistem menggunakan activity log.
9. Menyediakan informasi server untuk membantu troubleshooting.
10. Memberikan antisipasi ketika resource server mengalami penggunaan tinggi.

---

# 🧰 Tech Stack

| Teknologi                   | Fungsi                                               |
| --------------------------- | ---------------------------------------------------- |
| **Debian 13**               | Operating System server                              |
| **Node.js**                 | Runtime untuk menjalankan backend                    |
| **Express.js**              | Framework backend dan HTTP server                    |
| **MariaDB**                 | Database aplikasi                                    |
| **MySQL2**                  | Driver koneksi Node.js ke MariaDB                    |
| **HTML**                    | Struktur halaman web                                 |
| **CSS**                     | Tampilan dan layout dashboard                        |
| **JavaScript**              | Interaksi frontend dan komunikasi API                |
| **REST API**                | Komunikasi frontend dengan backend                   |
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
Debian Server
   ↓
Node.js
   ↓
Express.js
   ↓
MariaDB
```

Debian juga digunakan untuk menjalankan:

* Node.js
* MariaDB
* systemd service
* Activity Logging
* Server Monitoring

---

## 2. Node.js

Node.js digunakan sebagai runtime untuk menjalankan backend aplikasi.

Node.js menjalankan file utama:

```text
server.js
```

Versi Node.js yang digunakan pada server:

```text
Node.js v22.23.2
```

Node.js menangani:

* HTTP request
* API
* komunikasi database
* business logic
* server monitoring
* activity logging

---

## 3. Express.js

Express.js digunakan sebagai framework backend.

Contoh alur request:

```text
Browser
   ↓
HTTP Request
   ↓
Express.js
   ↓
Route
   ↓
Logic
   ↓
MariaDB
   ↓
JSON Response
   ↓
Browser
```

Express juga digunakan untuk menyediakan endpoint seperti:

```text
/api/menu
/api/products
/api/server/health
/api/business/monitoring
```

---

## 4. MariaDB

MariaDB digunakan sebagai database utama.

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

Dengan struktur tersebut, satu pesanan dapat memiliki beberapa produk.

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

Connection pool digunakan agar aplikasi dapat mengelola koneksi database secara lebih efisien.

---

# 🖥️ Arsitektur Sistem

Secara keseluruhan, arsitektur Dimsum Delight:

```text
                 CLIENT
                   │
                   ▼
             Web Browser
                   │
                   │ HTTP
                   ▼
        ┌─────────────────────┐
        │    Debian 13 Server │
        │                     │
        │    Node.js          │
        │       │             │
        │   Express.js        │
        │       │             │
        │       ├──── REST API
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

---

# ⚙️ Cara Kerja Sistem

## 1. Customer membuka website

Browser mengakses:

```text
http://IP-SERVER:3000
```

Request diterima oleh Node.js dan Express.js.

---

## 2. Express memproses request

Express menentukan endpoint yang diminta.

Contoh:

```text
GET /api/menu
```

Kemudian backend mengambil data produk dari MariaDB.

---

## 3. Database mengirimkan data

MariaDB mengembalikan data produk.

Node.js kemudian mengubah data menjadi response JSON.

Contoh:

```json
{
  "success": true,
  "products": []
}
```

---

## 4. Frontend menampilkan data

JavaScript frontend mengambil API menggunakan:

```javascript
fetch('/api/menu')
```

Data kemudian ditampilkan pada halaman website.

---

# 🛒 Fitur Project

## Customer

* Daftar produk.
* Harga produk.
* Stok produk.
* Pemesanan.
* Informasi pelanggan.
* Pengiriman data pesanan.

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

---

# 📊 Business Monitoring

Business Monitoring digunakan untuk melihat kondisi operasional bisnis.

Informasi yang dapat ditampilkan:

* Total transaksi.
* Total pendapatan.
* Jumlah produk.
* Stok produk.
* Status pesanan.
* Produk yang terjual.

Data diperoleh dari database MariaDB melalui API.

Alurnya:

```text
MariaDB
   ↓
Query
   ↓
Express API
   ↓
JavaScript
   ↓
Business Monitoring
```

---

# 📦 Product Management

Fitur Product Management digunakan untuk mengelola produk.

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

---

# 📋 Order Management

Order Management digunakan untuk mengelola pesanan customer.

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

Hal ini membuat proses pengelolaan pesanan menjadi lebih terstruktur.

---

# 🖥️ Server Monitoring

Salah satu bagian utama project adalah **Server Monitoring**.

Fitur ini dibuat sebagai bentuk antisipasi apabila resource server mengalami penggunaan yang tinggi.

Monitoring mencakup:

* CPU Usage.
* CPU Core.
* RAM Usage.
* Uptime.
* Status server.
* Status resource.
* Threshold CPU.
* Threshold RAM.

---

# 📈 Cara Kerja Monitoring

Server menyediakan endpoint:

```text
/api/server/health
```

Frontend meminta data tersebut secara berkala.

Alurnya:

```text
Server
   ↓
Node.js OS Monitoring
   ↓
CPU / RAM / Uptime
   ↓
Health API
   ↓
JavaScript Frontend
   ↓
Server Monitoring Dashboard
```

Contoh response:

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

---

# 🚨 Resource Threshold

Monitoring menggunakan threshold untuk membedakan kondisi resource.

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

Dengan cara tersebut, nilai threshold tidak perlu ditulis berulang kali pada backend.

---

# 🧠 Monitoring Status Logic

Status resource diproses melalui:

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

---

# 🔔 Konsep Alert

Project ini menggunakan konsep **local server alert**, bukan Telegram.

Tujuannya adalah memberikan informasi ketika terjadi kondisi yang perlu diperhatikan.

Contoh:

```text
CPU Usage
92%

🔴 CRITICAL

Resource usage is critically high.
```

Dengan konsep tersebut administrator dapat mengetahui adanya lonjakan penggunaan resource dari dashboard.

> Alert pada project ini difokuskan sebagai mekanisme antisipasi dan monitoring internal server, tanpa integrasi layanan pesan eksternal seperti Telegram.

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
* Membantu proses pemeriksaan ketika terjadi masalah.

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

Backend menyediakan API untuk menghubungkan frontend dengan server.

Contoh endpoint:

| Endpoint                   | Fungsi                          |
| -------------------------- | ------------------------------- |
| `/api/menu`                | Mengambil data menu             |
| `/api/products`            | Mengelola/mengambil data produk |
| `/api/business/monitoring` | Data monitoring bisnis          |
| `/api/server/health`       | Data kondisi server             |

API server health merupakan salah satu bagian penting pada monitoring.

Endpoint:

```text
GET /api/server/health
```

Digunakan untuk mendapatkan:

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

---

# ⚙️ Deployment dan Service Management

Aplikasi tidak hanya dijalankan menggunakan:

```bash
node server.js
```

Tetapi juga dikonfigurasi sebagai **systemd service**.

Nama service:

```text
dimsum.service
```

Alur deployment:

```text
Source Code
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
```

---

# 🔄 systemd

systemd digunakan agar aplikasi dapat dikelola sebagai service server.

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

Dengan systemd, aplikasi dapat berjalan lebih terstruktur dibandingkan menjalankan Node.js secara manual setiap kali server dinyalakan.

---

# 🔐 Konsep Keamanan dan Stabilitas

Beberapa penerapan yang digunakan:

* Database tidak diakses langsung oleh frontend.
* Frontend berkomunikasi melalui API.
* Database berada pada server.
* Aplikasi dijalankan sebagai service.
* Activity log digunakan untuk pemeriksaan aktivitas.
* CPU dan RAM dipantau.
* Threshold digunakan untuk mendeteksi kondisi resource tinggi.
* Konfigurasi monitoring dipisahkan dari konfigurasi database.

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

> Screenshot digunakan sebagai dokumentasi tampilan aplikasi yang dijalankan pada Web Server Debian.

---

# 🚀 Cara Menjalankan

## 1. Clone Repository

```bash
git clone <URL-REPOSITORY>
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

Health API dapat diuji menggunakan:

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

### Cek API

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
                  
Monitoring:
CPU ────────────┐
RAM ────────────┤
Uptime ─────────┤
Service ────────┤
                ▼
          Health API
                │
                ▼
       Server Monitoring
                │
                ▼
       NORMAL / WARNING /
          CRITICAL
```

---

# 🧩 Konsep DevOps yang Diterapkan

Walaupun project ini tidak menggunakan tools monitoring berat seperti Prometheus atau Grafana, beberapa konsep dasar DevOps tetap diterapkan.

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

### Deployment

```text
Debian 13
systemd
```

### Monitoring

```text
CPU
RAM
Uptime
Service Status
Health API
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

Project ini memiliki keterkaitan dengan pembelajaran TJKT karena mencakup beberapa aspek administrasi server, seperti:

* Linux server administration.
* Konfigurasi Web Server.
* Deployment aplikasi.
* Pengelolaan service Linux.
* Konfigurasi database server.
* Penggunaan jaringan lokal.
* Monitoring resource server.
* Troubleshooting service.
* Pengelolaan log.
* Pengujian konektivitas dan API.

Dengan demikian, project tidak hanya menunjukkan kemampuan membuat aplikasi web, tetapi juga bagaimana aplikasi tersebut **dijalankan, dikelola, dipantau, dan diantisipasi ketika berjalan pada sebuah server**.

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

Dimsum Delight Web Server merupakan project yang menggabungkan **aplikasi web, database, Web Server, dan monitoring server** dalam satu sistem.

Aplikasi dibangun menggunakan Node.js dan Express.js, kemudian terhubung dengan MariaDB sebagai database. Aplikasi dijalankan pada Debian 13 dan dikelola menggunakan systemd sehingga dapat berjalan sebagai service server.

Selain fungsi utama seperti pengelolaan produk dan pesanan, project juga menerapkan **Business Monitoring, Activity Logging, Server Health API, CPU Monitoring, RAM Monitoring, uptime monitoring, dan resource threshold**.

Penerapan monitoring tersebut bertujuan sebagai **langkah antisipasi**, sehingga administrator dapat mengetahui kondisi server dan mengenali penggunaan resource yang tinggi sebelum berkembang menjadi masalah yang lebih serius.

Project ini menunjukkan bahwa sebuah aplikasi Web Server tidak hanya perlu dibuat agar dapat berjalan, tetapi juga perlu **dikelola, dipantau, dan dipelihara** agar tetap dapat digunakan dengan baik.

---

# 🌐 Portofolio Lengkap

Dokumentasi lengkap mengenai project, proses pengembangan, implementasi Web Server, monitoring server, serta hasil project dapat dilihat pada:

**Edusoft Portfolio**

```text
<TEMPEL-LINK-PORTFOLIO-DI-SINI>
```

---

## 👩‍💻 Project Information

**Project:** Dimsum Delight Web Server
**Bidang:** Web Server & Server Monitoring
**Jurusan:** TJKT
**Server OS:** Debian 13
**Backend:** Node.js + Express.js
**Database:** MariaDB
**Service Management:** systemd
**Monitoring:** CPU, RAM, Uptime & Server Health
**Logging:** Activity Log

---

Dengan struktur seperti ini, README-mu sudah jauh lebih menunjukkan bahwa **Dimsum Delight adalah project Web Server/TJKT yang punya sisi deployment, administrasi, monitoring, logging, dan antisipasi resource**, bukan sekadar website penjualan.
