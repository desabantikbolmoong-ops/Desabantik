# 🏘️ Website Resmi Desa Bantik

Website resmi Pemerintah Desa Bantik, Kecamatan Tombulu, Kabupaten Minahasa, Sulawesi Utara — dibangun sebagai *single-page application* (SPA) dalam satu file HTML, siap deploy langsung ke **GitHub Pages** tanpa proses build.

🔗 **Live Demo:** `https://<username-github-anda>.github.io/<nama-repo>/`

---

## ✨ Fitur Utama

- **Profil Desa** — Sambutan Kepala Desa, Profil, Visi & Misi, Perangkat Desa, Peta Desa
- **Potensi Desa** — Wisata, UMKM, Statistik Penduduk (dengan grafik interaktif)
- **Transparansi** — Agenda Kegiatan, APBDes, Unduh Dokumen
- **Layanan Publik** — Layanan Surat Online, Pengaduan Masyarakat, Jadwal Posyandu
- **Berita & Galeri** Desa
- **FAQ & Kontak**
- **Panel Admin/Login** — pengelolaan konten & fitur menu langsung dari browser
- **Dark Mode** (mode terang/gelap)
- **Desain Responsif** — nyaman diakses dari HP, tablet, maupun desktop

## 🛠️ Teknologi

| Komponen        | Library / Sumber                         |
|-----------------|-------------------------------------------|
| Styling         | [Tailwind CSS](https://tailwindcss.com) (via CDN) |
| Font            | [Google Fonts – Poppins](https://fonts.google.com) |
| Ikon            | [Iconify Icon](https://iconify.design) |
| Grafik/Chart    | [Chart.js](https://www.chartjs.org) |
| Gambar Contoh   | [Picsum Photos](https://picsum.photos) |
| Penyimpanan Data| `localStorage` browser (untuk data yang diubah lewat panel admin) |

Semua library dimuat melalui CDN, sehingga **tidak ada proses build/install** — file `index.html` bisa langsung dibuka atau di-hosting apa adanya.

## 📁 Struktur Repository

```
.
├── index.html     # Halaman utama (seluruh aplikasi SPA)
├── .nojekyll      # Menonaktifkan pemrosesan Jekyll di GitHub Pages
└── README.md      # Dokumentasi ini
```

> **Catatan:** File `.nojekyll` wajib ada agar GitHub Pages tidak memproses folder/file yang diawali tanda titik (`_` atau `.`) melalui Jekyll, serta mencegah masalah pada aset yang dimuat secara dinamis.

## 🚀 Cara Deploy ke GitHub Pages

1. **Buat repository baru** di GitHub (public), misalnya `website-desa-bantik`.
2. **Upload 3 file ini** (`index.html`, `.nojekyll`, `README.md`) ke root repository — bisa lewat "Add file → Upload files" di GitHub, atau via Git:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Website Desa Bantik"
   git branch -M main
   git remote add origin https://github.com/<username-anda>/<nama-repo>.git
   git push -u origin main
   ```
3. Buka menu **Settings → Pages** pada repository.
4. Pada bagian **Build and deployment**, pilih:
   - Source: **Deploy from a branch**
   - Branch: **main** dan folder **/ (root)**
5. Klik **Save**. Tunggu 1–2 menit, situs akan aktif di:
   ```
   https://<username-anda>.github.io/<nama-repo>/
   ```

## ⚠️ Catatan Penting

- Data yang diubah melalui **Panel Admin** (konten, berita, pengaturan fitur, dll.) disimpan di `localStorage` **browser pengunjung masing-masing** — bukan di server/database terpusat. Artinya perubahan admin di satu perangkat/browser tidak otomatis muncul di perangkat lain.
- Situs ini membutuhkan **koneksi internet** karena beberapa aset (font, ikon, grafik, gambar contoh) dimuat dari CDN eksternal.
- Tidak ada perubahan apa pun yang dilakukan terhadap isi/kode `index.html` asli — file diunggah persis seperti sumber aslinya.

## 📄 Lisensi

Hak cipta konten dan desain dipegang oleh Pemerintah Desa Bantik. Silakan sesuaikan bagian ini bila ingin menambahkan lisensi open-source (MIT, dll.) atau ketentuan penggunaan lainnya.

---

Dibuat dengan ❤️ untuk kemajuan digital Desa Bantik.
