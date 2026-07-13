# 🏘️ Website Resmi Desa Bantik

Website resmi Pemerintah Desa Bantik, Kecamatan Tombulu, Kabupaten Minahasa, Sulawesi Utara. Portal ini berisi profil desa, berita, wisata, UMKM, layanan surat online, peta desa, dan transparansi anggaran.

🔗 **Live Demo:** `https://<username-github-anda>.github.io/<nama-repo>/`

---

## ✨ Fitur

- 🏠 Beranda dengan hero slideshow & statistik desa
- 📰 Berita & pengumuman desa
- 🗺️ Peta lokasi desa interaktif
- 🏞️ Galeri wisata & UMKM
- 📄 Layanan pengajuan surat online + lacak status
- 📊 Transparansi anggaran desa
- 🌙 Mode gelap/terang (dark mode)
- 📱 Tampilan responsif (mobile-friendly)
- 🔐 Panel admin untuk pengelolaan konten

---

## 🚀 Cara Hosting di GitHub Pages

Website ini adalah **single-file HTML** (`index.html`) sehingga sangat mudah di-hosting gratis menggunakan **GitHub Pages**. Ikuti langkah berikut:

### 1. Buat Repository Baru
1. Login ke akun GitHub Anda.
2. Klik tombol **New repository**.
3. Beri nama repository, misalnya `desa-bantik` (boleh nama lain).
4. Pilih **Public**, lalu klik **Create repository**.

### 2. Upload File
Upload 3 file berikut ke root repository (bukan di dalam folder):
- `index.html`
- `README.md`
- `.nojekyll`

Cara upload:
- Klik **Add file → Upload files** di halaman repository.
- Seret (drag & drop) ketiga file di atas, lalu klik **Commit changes**.

> 💡 Alternatif via terminal/Git:
> ```bash
> git init
> git add .
> git commit -m "Initial commit - Website Desa Bantik"
> git branch -M main
> git remote add origin https://github.com/<username-anda>/<nama-repo>.git
> git push -u origin main
> ```

### 3. Aktifkan GitHub Pages
1. Buka repository → klik tab **Settings**.
2. Di sidebar kiri, klik **Pages**.
3. Pada bagian **Build and deployment → Source**, pilih **Deploy from a branch**.
4. Pada bagian **Branch**, pilih `main` dan folder `/ (root)`, lalu klik **Save**.
5. Tunggu 1–2 menit, GitHub akan menampilkan link website Anda, biasanya berbentuk:
   ```
   https://<username-github-anda>.github.io/<nama-repo>/
   ```

### 4. Selesai! 🎉
Website Desa Bantik Anda sudah online dan dapat diakses oleh siapa saja.

---

## 📁 Struktur File

```
├── index.html      # Seluruh website (HTML, CSS, dan JavaScript dalam satu file)
├── .nojekyll       # Menonaktifkan proses Jekyll agar GitHub Pages
│                     tidak memfilter/mengubah file yang diawali underscore (_)
└── README.md       # Dokumentasi ini
```

> ⚠️ **Penting:** File `index.html` **tidak diubah sama sekali** dari file asli yang Anda unggah, sehingga seluruh tampilan dan fungsi tetap sesuai aslinya.

---

## ❓ Kenapa Ada File `.nojekyll`?

Secara default, GitHub Pages memproses situs menggunakan **Jekyll** (static site generator bawaan GitHub). Proses ini terkadang:
- Mengabaikan file/folder yang diawali garis bawah (`_`)
- Menyebabkan proses build tambahan yang tidak perlu untuk file HTML statis

Dengan menambahkan file kosong bernama `.nojekyll` di root repository, GitHub Pages akan **melewati proses Jekyll** dan langsung menyajikan file `index.html` apa adanya — memastikan tidak ada file yang hilang atau berubah, dan proses deploy lebih cepat.

---

## 🛠️ Teknologi yang Digunakan

- HTML5, CSS3 (Tailwind CSS via CDN), JavaScript (vanilla)
- [Iconify](https://iconify.design/) untuk ikon
- [Chart.js](https://www.chartjs.org/) untuk grafik statistik
- Google Fonts (Poppins)

---

## 🔥 WAJIB: Aktifkan Sinkronisasi Cloud (Firebase) — 5 Menit

**Ini bagian PALING PENTING.** Tanpa langkah ini, data seperti **Surat Masuk**, **Pengaduan**, **Musik Latar**, **Berita**, dll yang diisi lewat panel Admin **hanya akan tersimpan di HP/browser Admin itu sendiri** — tidak akan muncul di HP warga lain, dan pengajuan surat dari warga tidak akan terlihat di HP Admin. Ini penyebab masalah "surat masuk kosong di admin" yang sebelumnya terjadi.

Solusinya: website ini sudah saya siapkan agar bisa tersambung ke **Firebase Firestore** (database cloud gratis dari Google) supaya semua data tersinkron real-time ke semua perangkat.

### Langkah Setup:

1. Buka **[https://console.firebase.google.com](https://console.firebase.google.com)** → login pakai akun Google → **Add project** → beri nama bebas (mis. `desa-bantik`) → boleh matikan Google Analytics → **Create project**.
2. Di dashboard project, klik ikon **`</>`** (Web) → beri nama app bebas → **Register app**.
3. Firebase akan menampilkan kode `firebaseConfig` seperti ini:
   ```js
   const firebaseConfig = {
     apiKey: "AIzaSy...",
     authDomain: "desa-bantik-xxxx.firebaseapp.com",
     projectId: "desa-bantik-xxxx",
     storageBucket: "desa-bantik-xxxx.appspot.com",
     messagingSenderId: "123456789",
     appId: "1:123456789:web:abcdef"
   };
   ```
4. **Copy nilai-nilai tersebut**, lalu buka file `index.html` (bisa edit langsung di GitHub dengan klik ikon pensil ✏️), cari bagian:
   ```js
   var FIREBASE_CONFIG = {
     apiKey: "GANTI_DENGAN_API_KEY",
     ...
   };
   ```
   Ganti semua nilai `"GANTI_DENGAN_..."` dengan nilai asli dari Firebase Console kamu. Simpan (**Commit changes**).
5. Kembali ke Firebase Console → menu kiri **Build → Firestore Database** → **Create database** → pilih lokasi server (misalnya `asia-southeast2 (Jakarta)`) → mode **Production** → **Enable**.
6. Buka tab **Rules** di Firestore, hapus isinya, ganti dengan ini, lalu klik **Publish**:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /site_data/{doc} {
         allow read, write: if true;
       }
     }
   }
   ```
   > Rule ini sengaja dibuat terbuka supaya warga bisa mengajukan surat/pengaduan tanpa perlu login. Cukup aman untuk website informasi desa skala kecil seperti ini.
7. Selesai! Buka lagi website-nya (boleh dari HP manapun) — sekarang semua data (surat masuk, musik, berita, dll) akan **otomatis tersinkron ke semua orang secara real-time**, termasuk ke panel Admin di HP manapun Admin login.

> 💡 Kalau langkah ini **belum dilakukan**, website tetap bisa jalan normal seperti biasa (tidak error), hanya saja datanya tetap tersimpan lokal per-HP seperti sebelumnya.

---

## 📌 Catatan

- Pastikan nama file utama tetap `index.html` agar GitHub Pages otomatis mengenalinya sebagai halaman utama.
- Firebase Firestore versi gratis (Spark Plan) sudah lebih dari cukup untuk website desa — gratis selamanya untuk trafik skala kecil-menengah (puluhan ribu pembacaan/penulisan data per hari).
- Untuk musik latar, disarankan **memasukkan tautan/link file MP3** (bukan unggah file langsung) agar ukurannya kecil dan cepat tersinkron ke semua pengunjung.
- Kalau butuh reset seluruh data cloud, hapus semua dokumen di collection `site_data` lewat Firebase Console → Firestore Database.

---

## 📄 Lisensi

Website ini dibuat untuk keperluan Pemerintah Desa Bantik. Silakan sesuaikan penggunaan sesuai kebutuhan desa Anda.
