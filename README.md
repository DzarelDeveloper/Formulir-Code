# Formulir Permintaan Kode dengan Integrasi Telegram Bot

Repositori ini berisi formulir web yang memungkinkan pengguna untuk mengirimkan permintaan kode yang akan diteruskan ke dua grup Telegram: satu privat (dengan email) dan satu publik (tanpa email). Berikut adalah panduan untuk mengatur dan menggunakan formulir ini.

## Fitur
- Formulir dua bahasa (Indonesia dan Inggris)
- Validasi input
- Integrasi dengan Telegram Bot
- Navigasi Form dan About
- Responsif untuk berbagai ukuran layar

## Prasyarat
1. Browser modern
2. Koneksi internet
3. Akun Telegram dan Bot yang sudah dibuat

## Cara Setup

### 1. Membuat Telegram Bot
1. Buka Telegram dan cari `@BotFather`
2. Ketik `/start` lalu `/newbot`
3. Ikuti instruksi untuk membuat bot dan dapatkan **BOT_TOKEN**
4. Catat token yang diberikan (contoh: `8197646932:AAHQj0lFZlsan-dxgre1mJt9rc5_CzZNhyg`)

### 2. Membuat Grup Telegram
1. Buat dua grup Telegram:
   - Grup Privat (untuk admin/owner)
   - Grup Publik (untuk anggota komunitas)
2. Tambahkan bot Anda ke kedua grup sebagai **admin**
3. Dapatkan ID grup:
  - Kalau kamu butuh ID ini untuk bot (misalnya pakai getUpdates atau sendMessage), pastikan bot sudah ditambahkan ke grup dan punya izin admin. Setelah dapat ID-nya, gunakan seperti ini di API:
    ```
   https://api.telegram.org/bot(BOT-TOKENMU)/getUpdates
    ```
   - Catat ID grup (contoh: `-1002450587276` untuk privat, `-1002281623446` untuk publik)

### 3. Mengatur Kode
1. Clone repositori ini:
```bash
git clone <url-repositori-anda>
cd <nama-folder>
```
2. Buka file `script.js` dan modifikasi bagian berikut:
```javascript
const formSection = document.getElementById('formSection');
const aboutSection = document.getElementById('about');
const formLink = document.getElementById('formLink');
const aboutLink = document.getElementById('aboutLink');
const indicator = document.querySelector('.indicator');
const requestForm = document.getElementById('requestForm');
const nameInput = document.getElementById('name');
const emailInput = document.getElementById('email');
const requestInput = document.getElementById('request');
const nameError = document.getElementById('nameError');
const emailError = document.getElementById('emailError');
const requestError = document.getElementById('requestError');
const content = document.getElementById('content');
const languageModal = document.getElementById('languageModal');

const BOT_TOKEN = 'YOUR_BOT_TOKEN_HERE'; // Ganti dengan token bot Anda
const CHAT_ID_1 = 'YOUR_PRIVATE_GROUP_ID'; // Ganti dengan ID grup privat Anda
const CHAT_ID_2 = 'YOUR_PUBLIC_GROUP_ID'; // Ganti dengan ID grup publik Anda
```
- Ganti `YOUR_BOT_TOKEN_HERE` dengan token bot Anda
- Ganti `YOUR_PRIVATE_GROUP_ID` dengan ID grup privat
- Ganti `YOUR_PUBLIC_GROUP_ID` dengan ID grup publik

### 4. Menjalankan Formulir
1. Buka `index.html` di browser
2. Pilih bahasa (Indonesia/Inggris)
3. Isi formulir dan submit
4. Cek kedua grup Telegram untuk melihat hasilnya:
   - Grup privat: menerima nama, email, deskripsi, dan link
   - Grup publik: menerima nama, deskripsi, dan link (tanpa email)

## Struktur File
- `index.html`: Struktur HTML utama
- `styles.css`: Styling untuk tampilan
- `script.js`: Logika JavaScript dan integrasi Telegram

## Cara Kerja
1. Formulir divalidasi saat disubmit
2. Jika valid, data dikirim ke:
   - Grup privat: pesan lengkap dengan email
   - Grup publik: pesan tanpa email
3. Pengguna menerima pesan konfirmasi di web

## Catatan
- Pastikan bot memiliki izin admin di kedua grup
- Proses pengiriman membutuhkan koneksi internet
- Waktu respon maksimal 24-48 jam (sesuai deskripsi About) - ( ini manual respon karna ini untuk menerima atau menolak permintaan seseorang )

## Kontribusi
Silakan fork dan buat pull request untuk perbaikan atau fitur baru.

## Lisensi
[MIT License](LICENSE)
