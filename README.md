# Arsitektur-web-2 | Design Project2
## Arsitektur Sistem
```text
                    ┌──────────────────────────┐
                    │       Web Browser        │
                    │ (Chrome / Edge / Firefox)│
                    └─────────────┬────────────┘
                                  │ HTTP
                                  │
                     ┌────────────▼────────────┐
                     │      Web Server         │
                     │ Apache / Express Server │
                     └────────────┬────────────┘
                                  │
               ┌──────────────────┼──────────────────┐
               │                  │                  │
               ▼                  ▼                  ▼
        Halaman Pembeli      Halaman Owner      API / Logic
        (Frontend)           (Dashboard)        (Backend)
               │                  │                  │
               └──────────────────┼──────────────────┘
                                  │
                                  ▼
                        Database (MySQL/MariaDB)
                                  │
              ┌───────────────────┼───────────────────┐
              ▼                   ▼                   ▼
          Data Menu          Data Pesanan        Data User
```

---

# Struktur Folder

```text
kedai-dimsum/
│
├── public/
│   ├── css/
│   │      style.css
│   │      owner.css
│   │
│   ├── js/
│   │      main.js
│   │      owner.js
│   │
│   ├── images/
│          dimsum-ayam.png
│          dimsum-udang.png
│          dimsum-jamur.png
│
├── pages/
│      menu.php
│      detail.php
│      keranjang.php
│      checkout.php
│      pesanan.php
│
├── owner/
│      dashboard.php
│      produk.php
│      pesanan.php
│      laporan.php
│
├── includes/
│      header.php
│      navbar.php
│      footer.php
│
├── config/
│      database.php
│
├── index.php
└── README.md
````
# Konsep Sistem

## 1. Pembeli

Halaman ini digunakan pelanggan.

### Menu

* Home
* Menu Dimsum
* Tentang
* Checkout / hubungi

### Alur

```
Masuk Website

↓

Melihat Menu

↓

Klik Detail

↓

Tambah Keranjang

↓

Checkout

↓

Pesanan Masuk
```

---

## 2. Owner

Halaman khusus admin.

### Menu

* Dashboard
* Kelola Produk
* Kelola Pesanan
* Laporan Penjualan

### Alur

```
Login Owner

↓

Dashboard

↓

Lihat Pesanan

↓

Konfirmasi Pesanan

↓

Pesanan Selesai

↓

Masuk Laporan
```

---

# Konsep Database

## Tabel User

```
id
nama
email
password
role
```

role

```
buyer
owner
```

---

## Tabel Produk

```
id_produk
nama
harga
gambar
deskripsi
```
# Cara Kerja Sistem

## Pembeli

```
Buka Website

↓

Pilih Dimsum

↓

Klik Detail

↓

Tambah Keranjang

↓

Checkout

↓

Data Masuk Database
```

---

## Owner

```
Login

↓

Dashboard

↓

Pesanan Baru

↓

Data Database Terupdate

↓

Pembeli melihat status terbaru
```

---

# Fitur Pembeli (3 fitur)

1. Lihat Menu Dimsum
2. Detail Produk
3. Pesan

---

# Fitur Owner (5 fitur)

1. Dashboard
2. Tambah/Edit/Hapus Produk
3. Kelola Pesanan
4. Update Status Pesanan
5. Laporan Penjualan

---

# Alur Keseluruhan

```text
                 PEMBELI
                     │
                     ▼
             Pilih Menu Dimsum
                     │
                     ▼
             Tambah Keranjang
                     │
                     ▼
                Checkout
                     │
                     ▼
          Data Masuk Database
                     │
────────────────────────────────────
                     │
                     ▼
                  OWNER
                     │
                     ▼
             Dashboard Pesanan
                     │
                     ▼
          Konfirmasi Pesanan
                     │
                     ▼
         Update Status Pesanan
                     │
                     ▼
     Pembeli melihat status terbaru
```
