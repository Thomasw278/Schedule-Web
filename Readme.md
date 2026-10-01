# 🍏 Mac-Style Daily Task Manager

Sebuah aplikasi web manajemen jadwal harian (*Daily Planner*) yang dirancang dengan antarmuka futuristik bergaya macOS (Glassmorphism). Aplikasi ini dibangun secara *serverless* menggunakan HTML, Tailwind CSS, dan JavaScript di sisi *frontend*, serta terintegrasi penuh dengan **Google Apps Script** dan **Google Sheets** sebagai *backend* dan *database*.

## ✨ Fitur Utama

### 🎨 1. UI/UX Futuristik (macOS Glassmorphism)
*   **Desain Transparan:** Menggunakan efek kaca tembus pandang (*backdrop-blur*) yang elegan dengan animasi gradien warna latar belakang yang hidup.
*   **Dark Mode Toggle:** Mendukung transisi mulus antara mode terang (Light Mode) dan mode gelap (Dark Mode) khas ekosistem Apple.
*   **Window Controls:** Dekorasi tombol merah, kuning, dan hijau di sudut kiri atas untuk memperkuat kesan aplikasi *native* desktop.
*   **Smooth Animations:** Animasi transisi yang halus saat menambah, menghapus, atau menyelesaikan tugas, serta efek khusus ("Glowing Neon") pada tugas yang sudah selesai.

### ⚡ 2. Manajemen Tugas (CRUD) Real-time
*   **Optimistic UI:** Penambahan, pengeditan, penyelesaian, dan penghapusan jadwal langsung direfleksikan di layar tanpa waktu tunggu (*loading*), memberikan pengalaman pengguna yang sangat cepat.
*   **Cloud Sync Indicator:** Indikator visual di sudut layar yang menunjukkan status sinkronisasi ke Google Sheets secara *real-time* ("Menyinkronkan..." -> "Tersimpan").
*   **Custom Time Picker:** Dropdown pemilihan waktu yang dioptimalkan dengan interval 5 menit untuk UX yang lebih rapi dibandingkan input waktu bawaan browser.

### 🤖 3. Automasi Cerdas (Smart Features)
*   **Auto-Sorting:** Aplikasi secara cerdas mengurutkan daftar jadwal Anda. Tugas yang waktunya paling dekat dengan jam saat ini akan diprioritaskan dan diletakkan di urutan teratas.
*   **Up Next Widget:** Fitur yang memindai jadwal Anda dan menampilkan 1 tugas prioritas terdekat di *sidebar*, sehingga Anda tahu persis apa yang harus dilakukan selanjutnya tanpa harus mencari.
*   **Live Clock & Date:** Jam dan tanggal digital yang berjalan sinkron secara *real-time*.
*   **Dynamic Pie Chart:** Visualisasi statistik harian berupa *Donut Chart* yang menunjukkan persentase jadwal yang sudah diselesaikan hari ini.

### 📧 4. Backend Serverless (Google Ecosystem)
*   **Google Sheets Database:** Menyimpan data dengan aman dan gratis tanpa perlu mengonfigurasi XAMPP, MariaDB, atau server tradisional.
*   **Email Notification Trigger:** Skrip yang berjalan otomatis di belakang layar setiap 5 menit untuk mengecek jadwal. Jika sudah waktunya, sistem akan mengirimkan email pengingat langsung ke kotak masuk Gmail Anda.
*   **Auto-Reset Harian:** Skrip pemicu waktu (*time-driven trigger*) yang akan menghapus semua jadwal di tengah malam, memberikan Anda "kanvas kosong" setiap paginya.

---

## 🛠️ Teknologi yang Digunakan

*   **Frontend:** HTML5, JavaScript (ES6+), [Tailwind CSS](https://tailwindcss.com/) (via CDN), [Font Awesome](https://fontawesome.com/) (Ikon), Google Fonts (Outfit).
*   **Backend & Database:** Google Apps Script (GAS), Google Sheets.
*   **Notifikasi:** Gmail API (terintegrasi dalam GAS).

---

## 🚀 Panduan Instalasi & Penggunaan

### Tahap 1: Persiapan Database (Google Sheets)
1. Buat Spreadsheet baru di [Google Sheets](https://sheets.google.com/).
2. Buat *header* pada baris pertama persis seperti ini:
   * `A1`: ID
   * `B1`: Task Name
   * `C1`: Start Time
   * `D1`: End Time
   * `E1`: Status
   * `F1`: Email Sent
3. Salin **ID Spreadsheet** Anda dari URL (contoh: `https://docs.google.com/spreadsheets/d/[SALIN_ID_INI]/edit`).

### Tahap 2: Pengaturan Backend (Google Apps Script)
1. Pada Google Sheets Anda, klik menu **Ekstensi > Apps Script**.
2. Salin dan tempel kode backend (`code.gs`) ke dalam editor.
3. Ubah variabel konfigurasi di baris atas kode dengan ID Spreadsheet dan alamat Email Anda.
4. Klik ikon Roda Gigi (Setelan Project) > Centang "Tampilkan file manifes 'appsscript.json'". Buka file tersebut dan pastikan `"timeZone": "Asia/Jakarta"` (atau sesuaikan dengan zona waktu Anda).
5. Klik tombol biru **Terapkan (Deploy) > Deployment Baru**. Pilih **Aplikasi Web**, atur akses ke **"Siapa saja"**, lalu *Deploy*. Salin **URL Aplikasi Web** yang diberikan.

### Tahap 3: Pengaturan Automasi (Triggers)
1. Di layar Apps Script, klik menu jam ⏰ (Pemicu) di sebelah kiri.
2. Tambahkan pemicu baru untuk `checkAndSendEmails`:
   * Sumber acara: Berdasarkan waktu
   * Jenis pemicu: Timer menit
   * Interval: Setiap 5 menit
3. Tambahkan pemicu baru untuk `dailyReset`:
   * Sumber acara: Berdasarkan waktu
   * Jenis pemicu: Timer hari
   * Waktu: Tengah malam hingga 01.00

### Tahap 4: Menjalankan Frontend
1. Buka file `index.html` menggunakan *text editor* (seperti VS Code).
2. Cari variabel `API_URL` dan ganti nilainya dengan URL Web App yang Anda dapatkan pada Tahap 2.
3. Buka `index.html` di browser favorit Anda, dan aplikasi siap digunakan!

---

## 💡 Ide Pengembangan Selanjutnya
Aplikasi ini sangat terbuka untuk dikembangkan lebih jauh. Beberapa ide fitur:
*   Integrasi notifikasi via **Telegram Bot API** atau WhatsApp.
*   Fitur *Pomodoro Timer* bawaan di dalam aplikasi.
*   Halaman riwayat (History) untuk melihat jadwal di hari-hari sebelumnya (menghapus auto-reset).
*   Monggo yang mau bikin update / perubahan bisa fork / langsung ubah disini

---
*Dibuat untuk produktivitas yang lebih baik.* 🚀