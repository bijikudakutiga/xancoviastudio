# Xancovia Studio: paket deploy

Website landing (video, musik, demo sistem) yang masuk ke dunia game studio.
Semua file sudah siap diunggah ke GitHub Pages. Tidak perlu build apa pun.

## Isi paket

```
index.html            halaman utama (game, dan memuat site.html sebagai pembuka)
site.html             landing page: hero, demo sistem, proses, kontak
.nojekyll             supaya GitHub Pages menyajikan file apa adanya
assets/
  video/hero.mp4      video latar hero (1280x720)
  video/sample.mp4    video sampel ruangan Video Maker (1280x720, 73 detik)
  audio/bgm.mp3       musik latar (Apex Protocol)
  audio/songs/        4 lagu untuk jukebox
  img/                semua gambar (80 file)
  og.jpg              gambar pratinjau saat link dibagikan
  favicon.png, apple-touch-icon.png
```

Total sekitar 40 MB. Semua file di bawah 25 MB, jadi bisa diunggah lewat browser.

## Cara upload ke GitHub (lewat browser)

1. Buka github.com, klik **New repository**. Beri nama, misalnya `xancovia-studio`, pilih **Public**, lalu **Create repository**.
2. Klik **uploading an existing file**.
3. Karena jumlah file banyak, unggah dua kali:
   - **Batch 1**: seret folder `assets/img` (isinya 80 file). Klik **Commit changes**.
   - **Batch 2**: seret sisanya (`index.html`, `site.html`, `.nojekyll`, `README.md`, dan folder `assets/video`, `assets/audio`, plus `assets/og.jpg`, `assets/favicon.png`, `assets/apple-touch-icon.png`). Klik **Commit changes**.
   - Jaga struktur foldernya tetap sama, karena kode memanggil file lewat path `assets/...`.
4. Buka **Settings**, lalu **Pages**. Pada **Build and deployment**, pilih **Source: Deploy from a branch**, **Branch: main**, folder **/ (root)**, lalu **Save**.
5. Tunggu 1 sampai 2 menit. Alamatnya muncul di halaman yang sama, bentuknya `https://USERNAME.github.io/xancovia-studio/`.

### Cara alternatif (git)

```bash
cd xancovia-studio
git init && git add . && git commit -m "Xancovia Studio"
git branch -M main
git remote add origin https://github.com/USERNAME/xancovia-studio.git
git push -u origin main
```

## Langkah wajib setelah alamat jadi: pratinjau link WhatsApp

Di bagian `<head>` file **index.html** dan **site.html**, ganti `YOUR-USERNAME` dan `YOUR-REPO` dengan alamat sebenarnya (ada di `og:image` dan `og:url`). Alamat gambar pratinjau harus lengkap (absolut), kalau tidak, WhatsApp dan Instagram tidak menampilkan gambarnya. Setelah itu commit lagi.

## Mengubah isi

- **Nomor WhatsApp**: cari `628881612817` di `index.html` dan `site.html`.
- **Pesan WhatsApp tiap produk**: di `site.html`, cari daftar `SYS` (kolom `msg`) dan bagian `WAM(`.
- **Video hero atau video sampel**: ganti file di `assets/video/` dengan nama yang sama.
- **Lagu jukebox**: ganti file di `assets/audio/songs/`. Judul yang tampil ada di `index.html`, pada baris `const SONGS=`.
- **Musik latar**: ganti `assets/audio/bgm.mp3`.
- **Teks hero** (headline, kata berganti, lencana): di `site.html`.

## Catatan

- **Musik tidak bisa otomatis**. Browser hanya mengizinkan suara setelah pengunjung menyentuh layar. Musik mulai pada sentuhan pertama, dan ada tombol suara di pojok kanan bawah.
- Jangan buka `index.html` langsung dengan klik dua kali (file://). Buka lewat GitHub Pages, atau server lokal: `python3 -m http.server`, lalu buka `http://localhost:8000`.
- Hak cipta: pastikan kamu punya izin untuk lagu dan video yang dipublikasikan. Lagu penuh di jukebox bisa diunduh siapa pun yang membuka alamat filenya.
- Domain sendiri: **Settings, Pages, Custom domain**, lalu atur DNS ke GitHub Pages.
