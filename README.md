# ⚽ League Management System API

API RESTful sederhana yang dibangun menggunakan **Laravel 11** untuk mengelola data liga sepak bola.
Sistem ini mencakup pengelolaan **tim**, **pemain**, **jadwal pertandingan**, serta **perhitungan klasemen otomatis**.

## 🚀 Fitur Utama

### 🔐 Autentikasi Aman

* Menggunakan **Laravel Sanctum**
* Endpoint: Register, Login, Logout, dan Get User

### 🏟️ Manajemen Tim

* CRUD data klub sepak bola
* Data tim meliputi:

  * Nama Tim
  * Homebase
  * Logo

### 👥 Manajemen Pemain

* Mendaftarkan pemain ke dalam tim
* Validasi posisi pemain:

  * `GK` (Goalkeeper)
  * `DF` (Defender)
  * `MF` (Midfielder)
  * `FW` (Forward)

### ⚽ Pertandingan (Matches)

* Membuat jadwal pertandingan
* Validasi agar tim tidak bisa bertanding melawan dirinya sendiri
* Update skor pertandingan

### 📊 Klasemen Otomatis (Auto Standings)

* Klasemen dihitung otomatis saat skor diperbarui
* Aturan poin:

  * Menang: **+3**
  * Seri: **+1**
  * Kalah: **0**
* Urutan klasemen berdasarkan:

  1. Poin tertinggi
  2. Selisih gol (*Goal Difference*)

## 🛠️ Teknologi yang Digunakan

* **Laravel 11** – Framework PHP
* **MySQL** – Database
* **Laravel Sanctum** – Autentikasi API Token

## 📦 Cara Instalasi

Ikuti langkah-langkah berikut untuk menjalankan project secara lokal.

### 1️⃣ Clone Repository

```bash
git clone https://github.com/username-kamu/nama-repo-kamu.git
cd nama-repo-kamu
```

### 2️⃣ Install Dependencies

Pastikan **Composer** sudah terinstall.

```bash
composer install
```

### 3️⃣ Konfigurasi Environment

Salin file `.env.example` menjadi `.env`:

```bash
cp .env.example .env
```

Sesuaikan konfigurasi database di file `.env`:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nama_database_kamu
DB_USERNAME=root
DB_PASSWORD=
```

### 4️⃣ Generate App Key

```bash
php artisan key:generate
```

### 5️⃣ Migrasi Database

```bash
php artisan migrate
```

### 6️⃣ Jalankan Server

```bash
php artisan serve
```

Aplikasi akan berjalan di:

```
http://127.0.0.1:8000
```

## 📚 Dokumentasi API Singkat

> ⚠️ Endpoint yang dilindungi membutuhkan **Bearer Token**
> Tambahkan pada Header request:

```
Authorization: Bearer {access_token}
```

### 🔐 Auth

| Method | Endpoint             | Deskripsi                    |
| ------ | -------------------- | ---------------------------- |
| POST   | `/api/auth/register` | Mendaftar akun operator baru |
| POST   | `/api/auth/login`    | Login dan mendapatkan token  |
| POST   | `/api/auth/logout`   | Logout (hapus token)         |
| GET    | `/api/auth/me`       | Cek user yang sedang login   |

---

### 🏟️ Teams & Players

| Method | Endpoint                 | Deskripsi                    |
| ------ | ------------------------ | ---------------------------- |
| GET    | `/api/teams`             | List semua tim               |
| POST   | `/api/teams`             | Tambah tim baru              |
| GET    | `/api/players?team_id=1` | List pemain (filter per tim) |
| POST   | `/api/players`           | Tambah pemain baru           |

---

### ⚽ Matches & Standings

| Method | Endpoint            | Deskripsi                         |
| ------ | ------------------- | --------------------------------- |
| POST   | `/api/matches`      | Buat jadwal pertandingan          |
| PUT    | `/api/matches/{id}` | Update skor & status pertandingan |
| GET    | `/api/standings`    | Lihat klasemen sementara          |


## 🧪 Pengujian (Testing)

Disarankan menggunakan **Postman**:

1. Login terlebih dahulu untuk mendapatkan `access_token`
2. Masukkan token ke:

   * Authorization → Bearer Token
3. Uji endpoint sesuai kebutuhan


## 📝 Lisensi

Project ini bersifat **open-source** dan dilisensikan di bawah:

**MIT License**

## ✨ Catatan

Project ini cocok untuk:
* Latihan REST API Laravel
* Fondasi sistem liga sepak bola skala kecil

Silakan **fork**, **clone**, dan **kembangkan lebih lanjut** sesuai kebutuhan
