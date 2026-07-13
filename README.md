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

## 📌 Catatan

- Website ini murni **client-side** (tidak memerlukan server/backend), sehingga cocok untuk GitHub Pages.
- Data admin/konten yang diisi melalui panel admin akan tersimpan di **local storage browser** pengguna (bersifat lokal per perangkat), bukan di server pusat.
- Pastikan nama file utama tetap `index.html` agar GitHub Pages otomatis mengenalinya sebagai halaman utama.

---

## 📄 Lisensi

Website ini dibuat untuk keperluan Pemerintah Desa Bantik. Silakan sesuaikan penggunaan sesuai kebutuhan desa Anda.
