# E-Money Bookstore Backend API

<div align="center">
  <img width="300" height="301" alt="Institut Teknologi dan Bisnis Bina Sarana Global" src="https://github.com/user-attachments/assets/1e84f66a-135b-4cf2-b07a-b2a9098ce119" width="200"/>
</div>

<div align="center">
Institut Teknologi dan Bisnis Bina Sarana Global <br>
FAKULTAS TEKNOLOGI INFORMASI & KOMUNIKASI <br>
https://global.ac.id/
</div>

## Project UAS
- Nim : 1123150114
- Nama : Muhamad Yajid Rizky
- Mata Kuliah : Aplikasi Mobile
- Kelas : TI-SE 23 SH

## Deskripsi Project
Project ini adalah backend API untuk sistem E-Money Bookstore yang digunakan untuk mendukung autentikasi pengguna, verifikasi OTP, manajemen saldo, serta transaksi pembayaran secara aman. Aplikasi ini dibangun menggunakan Go dengan framework Gin, MySQL, Redis, Firebase Authentication, dan SMTP untuk pengiriman OTP via email.

## Demo Video
Lihat demo aplikasi dan alur fitur yang tersedia dalam video berikut.

**[Watch Full Demo on YouTube](https://youtu.be/3T_PeOEtE7w)**

Alternative link: **[Google Drive Demo]()**

## Fitur Utama
- Autentikasi pengguna dengan Firebase Authentication
- Login dan verifikasi email menggunakan JWT
- OTP via Firebase dan email
- Dukungan TOTP untuk otentikasi dua faktor
- Manajemen saldo akun
- Top up saldo
- Transfer / pembayaran dengan verifikasi OTP
- Riwayat transaksi akun
- Middleware autentikasi dan logging

## Teknologi yang Digunakan
- **[Go](https://go.dev/)** - Bahasa pemrograman backend
- **[Gin](https://gin-gonic.com/)** - Web framework
- **[GORM](https://gorm.io/)** - ORM untuk MySQL
- **[MySQL](https://www.mysql.com/)** - Database relasional
- **[Redis](https://redis.io/)** - Cache dan penyimpanan OTP sementara
- **[Firebase](https://firebase.google.com/)** - Authentication dan notifikasi
- **[JWT](https://jwt.io/)** - Token autentikasi
- **[gomail](https://github.com/go-gomail/gomail)** - SMTP email

## Persyaratan Sistem
Pastikan perangkat Anda sudah memiliki:
- Go (versi terbaru yang kompatibel dengan modul ini)
- MySQL Server
- Redis Server
- Firebase project dengan service account
- Git
- Postman (opsional untuk testing API)

## Cara Menjalankan Project

### 1. Clone Repository
```bash
git clone https://github.com/Frientia/be-bookstore-money.git
cd be-bookstore-money
```

### 2. Install Dependency
```bash
go mod tidy
```

### 3. Siapkan Environment
Buat file `.env` berdasarkan konfigurasi yang dibutuhkan, termasuk:
```env
PORT=8089
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=
DB_NAME=emoney_bookstore
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=
JWT_SECRET=your-super-secret-jwt-key-change-this
FIREBASE_CREDENTIALS_PATH=firebase_service_account.json
FIREBASE_API_KEY=your-firebase-api-key
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASSWORD=your-app-password
SMTP_FROM=your-email@gmail.com
SMTP_FROM_NAME=E-Money Bookstore
OTP_EXPIRY_MINUTES=5
```

### 4. Siapkan Firebase
- Buat project Firebase
- Aktifkan Authentication
- Download file service account JSON
- Simpan sebagai `firebase_service_account.json` di root project

### 5. Siapkan Database dan Redis
Pastikan MySQL dan Redis berjalan di lokal sebelum menjalankan server.

### 6. Jalankan Server
```bash
go run main.go
```

Server akan berjalan di:
```bash
http://localhost:8089
```

## Struktur Project
```bash
.
├── config/             # Konfigurasi aplikasi
├── database/           # Inisialisasi MySQL, Redis, Firebase
├── handlers/           # Handler HTTP untuk endpoint
├── middleware/         # JWT middleware dan logger
├── models/             # Struktur data model
├── routes/             # Routing API
├── services/           # Logika bisnis: JWT, OTP, email, Firebase
├── postman/            # Koleksi Postman
├── main.go             # Entry point aplikasi
├── go.mod              # Modul Go
└── .env                # Konfigurasi environment
```

## Dokumentasi API
Base URL:
```bash
http://localhost:8089/v1
```

### Authentication
- `POST /v1/auth/verify-token` - Verifikasi token Firebase dan login
- `POST /v1/auth/register` - Registrasi user dengan OTP
- `GET /v1/auth/me` - Ambil profil user (butuh token)
- `PUT /v1/auth/fcm-token` - Update token FCM
- `POST /v1/auth/verify-email-otp` - Verifikasi email OTP

### OTP
- `POST /v1/otp/send-firebase` - Kirim OTP via Firebase
- `POST /v1/otp/send-email` - Kirim OTP via email
- `POST /v1/otp/confirm` - Konfirmasi OTP
- `POST /v1/otp/totp/register` - Daftarkan TOTP
- `POST /v1/otp/totp/verify` - Verifikasi TOTP

### Account
- `GET /v1/account` - Ambil saldo akun
- `GET /v1/account/transactions` - Riwayat transaksi

### Payment
- `POST /v1/payment/topup` - Top up saldo
- `POST /v1/payment/transfer` - Transfer / pembayaran dengan OTP

## Contoh Penggunaan dengan Postman
Koleksi request API sudah tersedia di:
```bash
postman/emoney-2fa.postman_collection.json
```

## Lisensi
Project ini dilisensikan di bawah MIT License.

## Ucapan Terima Kasih
- [Flutter Community](https://flutter.dev/community)
- [Firebase](https://firebase.google.com/)
- [Gin Gonic](https://gin-gonic.com/)
- [GORM](https://gorm.io/)
- [Redis](https://redis.io/)

---
<div align="center">
  <p>© 2026 E-Money Bookstore Backend API. All rights reserved.</p>
</div>
