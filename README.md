# Keyboard Shop — Panduan Proyek

## KELOMPOK 5
ARYA FADHIL SAGITARISANDY 231011400263
LANDIE AZIS NUGROHO 231011400279
IRFAN NUR KHOLIK 231011400273

Dokumentasi ini menjelaskan langkah-langkah menyiapkan, menjalankan, dan melakukan deploy proyek statis "Keyboard Shop".

## Prasyarat
- Disarankan: Visual Studio Code (VS Code)
- Opsi lokal:
  - Ekstensi VS Code: Live Server
  - atau Python 3 (macOS sudah menyertakan `python3`)
  - atau Node.js dengan paket `serve`
- Browser modern (Chrome/Edge/Safari)

## Menjalankan Secara Lokal
Pilih salah satu metode di bawah ini.

### Metode A — VS Code + Live Server (paling mudah)
1. Buka folder proyek di VS Code.
2. Install ekstensi "Live Server" (Ritwick Dey).
3. Klik kanan [index.html](index.html) → "Open with Live Server".
4. Aplikasi akan terbuka di `http://127.0.0.1:5500/` (atau port serupa).

### Metode B — Python Simple HTTP Server
```bash
cd /Users/aryafadhil/Documents/keyboard-shop
python3 -m http.server 8000
```
Buka `http://localhost:8000/index.html` di browser.

### Metode C — Node.js (serve)
```bash
npm install -g serve
cd /Users/aryafadhil/Documents/keyboard-shop
serve .
```
Buka URL yang ditampilkan (umumnya `http://localhost:3000`).

## Struktur Proyek
- [index.html](index.html): Halaman utama.
- [keyboard-shop.html](keyboard-shop.html), [keyboard-accessories.html](keyboard-accessories.html), [keyboard-guides.html](keyboard-guides.html): Halaman konten lainnya.
- [css/](css): Stylesheets (Bootstrap, Materialize, modern.css, templatemo-style.css, dll.).
- [js/](js): Skrip umum (contoh: `jquery-3.3.1.min.js`, `materialize.min.js`).
- [img/keyboard/](img/keyboard): Aset gambar dan skrip vendor terkait tema.
- [webfonts/](webfonts): Font web yang digunakan tema.

Catatan: Proyek ini adalah situs statis; tidak memerlukan build atau backend.

## Pengembangan
### Menambah Halaman Baru
1. Duplikat salah satu file HTML yang ada, misalnya [keyboard-shop.html](keyboard-shop.html).
2. Ubah judul, konten, dan tautan navigasi.
3. Pastikan rujukan ke CSS/JS menggunakan path relatif yang benar (mis. `css/modern.css`, `js/jquery-3.3.1.min.js`).

### Mengubah Gaya (CSS)
- Edit file di [css/](css):
  - `modern.css` atau `templatemo-style.css` untuk kustomisasi tema.
  - `bootstrap.min.css` / `materialize.min.css` untuk komponen.
- Tambahkan rule baru seperlunya, hindari mengubah file vendor kecuali diperlukan.

### Menambah Aset (Gambar/Font/JS)
- Tempatkan gambar ke [img/keyboard/](img/keyboard) atau buat subfolder sesuai kebutuhan.
- Tambahkan font ke [webfonts/](webfonts) bila diperlukan.
- Tambahkan skrip kustom ke [js/](js) dan referensikan dari HTML.

## Deploy
### GitHub Pages (gratis)
1. Inisialisasi dan push repo ke GitHub:
```bash
git init
git add .
git commit -m "Initial Keyboard Shop site"
git branch -M main
git remote add origin <URL_REPO_GITHUB>
git push -u origin main
```
2. Di GitHub: Settings → Pages → Source: `Deploy from a branch` → Branch: `main` → Folder: `/root`.
3. Tunggu proses publikasi, situs akan tersedia di URL GitHub Pages Anda.

### Netlify / Vercel
- Buat proyek baru, pilih repository ini.
- Set root directory ke folder proyek (root). Karena situs statis, tidak perlu build command.
- Deploy dan dapatkan URL produksi.

## Tips & Troubleshooting
- **Path relatif:** Gunakan path relatif yang konsisten antar halaman (contoh `css/...`, `js/...`).
- **Cache browser:** Hard refresh (`Cmd+Shift+R`) bila perubahan CSS tidak terlihat.
- **Port bentrok:** Ubah port Live Server atau gunakan metode lain (Python/serve).
- **Konsol browser:** Cek error di DevTools untuk path aset yang salah.

## Kontribusi
- Buat branch fitur, lakukan perubahan terfokus.
- Ajukan Pull Request dengan deskripsi yang jelas.

---
Jika Anda membutuhkan setup tambahan (favicon, SEO meta tags, atau optimasi performa), beri tahu saya dan saya akan menambahkan panduannya.

## Panduan Pembuatan dari Nol (Tugas Kuliah)
Bagian ini menjelaskan proses membangun situs "Keyboard Shop" dari awal: perencanaan, struktur folder, komponen CSS, hingga publikasi.

### 1) Perencanaan Singkat
- **Tujuan**: Situs katalog keyboard, aksesoris, dan panduan.
- **Halaman**: `index.html` (beranda), `keyboard-shop.html` (produk), `keyboard-accessories.html` (aksesoris), `keyboard-guides.html` (artikel).
- **Gaya**: Tema modern, responsif, aksesibel (semantik HTML), memanfaatkan CSS framework ringan (opsional).
- **Konten**: Gambar produk, deskripsi singkat, harga, CTA.

### 2) Struktur Folder (Disarankan)
```
keyboard-shop/
├─ index.html
├─ keyboard-shop.html
├─ keyboard-accessories.html
├─ keyboard-guides.html
├─ css/
│  ├─ modern.css            # gaya kustom utama
│  ├─ templatemo-style.css  # tema tambahan (opsional)
│  ├─ bootstrap.min.css     # framework (opsional)
│  └─ materialize.min.css   # framework (opsional, jangan gabungkan keduanya)
├─ js/
│  ├─ jquery-3.3.1.min.js   # utilitas DOM (opsional)
│  └─ materialize.min.js    # komponen JS framework (opsional)
├─ img/
│  └─ keyboard/             # gambar dan aset terkait
└─ webfonts/                # font web (jika digunakan)
```
Catatan: Hindari memuat dua framework CSS sekaligus untuk mencegah konflik.

### 3) Kerangka HTML Dasar
Contoh skeleton untuk setiap halaman:
```html
<!doctype html>
<html lang="id">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Keyboard Shop</title>
    <link rel="stylesheet" href="css/modern.css">
    <!-- Pilih salah satu framework jika diperlukan -->
    <!-- <link rel="stylesheet" href="css/bootstrap.min.css"> -->
  </head>
  <body>
    <header class="navbar">
      <a class="brand" href="index.html">Keyboard Shop</a>
      <nav class="nav">
        <a href="keyboard-shop.html">Produk</a>
        <a href="keyboard-accessories.html">Aksesoris</a>
        <a href="keyboard-guides.html">Panduan</a>
      </nav>
    </header>

    <main>
      <!-- Konten halaman spesifik -->
      <section class="hero">
        <h1>Bangun setup keyboard impianmu</h1>
        <p>Temukan switch, keycaps, case, dan lebih banyak lagi.</p>
        <a class="btn btn-primary" href="keyboard-shop.html">Belanja Sekarang</a>
      </section>
    </main>

    <footer class="footer">© 2025 Keyboard Shop</footer>
    <!-- <script src="js/jquery-3.3.1.min.js"></script> -->
  </body>
</html>
```

### 4) Desain Sistem CSS (Komponen & Utilitas)
Gunakan `css/modern.css` sebagai tempat utama komponen dan token gaya.

#### 4.1 Tokens (Variabel CSS)
```css
:root {
  /* Warna */
  --color-primary: #2e7adf;
  --color-primary-700: #1f5fb8;
  --color-bg: #ffffff;
  --color-text: #1b1f23;
  --color-muted: #6b7280;

  /* Tipografi */
  --font-sans: system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, sans-serif;
  --fs-1: clamp(1.8rem, 3vw, 2.4rem);
  --fs-2: 1.6rem;
  --fs-3: 1.4rem;

  /* Spasi (scale 4px) */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-6: 24px;
  --space-8: 32px;

  /* Radius & bayangan */
  --radius-1: 8px;
  --shadow-1: 0 4px 12px rgba(0,0,0,0.08);
}

html { font-size: 62.5%; }
body { font-family: var(--font-sans); color: var(--color-text); background: var(--color-bg); }
```

#### 4.2 Utilitas (margin/padding/layout)
```css
.container { max-width: 1200px; margin: 0 auto; padding: 0 var(--space-4); }
.grid { display: grid; gap: var(--space-6); }
.grid-3 { grid-template-columns: repeat(3, 1fr); }
.stack-4 > * + * { margin-top: var(--space-4); }
.sr-only { position: absolute; width: 1px; height: 1px; padding: 0; margin: -1px; overflow: hidden; clip: rect(0,0,0,0); border: 0; }
```

#### 4.3 Komponen Navigasi
```css
.navbar { display:flex; align-items:center; justify-content:space-between; padding: var(--space-4) var(--space-6); box-shadow: var(--shadow-1); }
.brand { font-weight: 700; font-size: var(--fs-2); text-decoration:none; color: var(--color-text); }
.nav a { margin-left: var(--space-4); text-decoration:none; color: var(--color-muted); }
.nav a:hover { color: var(--color-text); }
```

#### 4.4 Komponen Hero
```css
.hero { padding: var(--space-8) 0; text-align: center; }
.hero h1 { font-size: var(--fs-1); margin-bottom: var(--space-4); }
.hero p { font-size: var(--fs-3); color: var(--color-muted); margin-bottom: var(--space-6); }
```

#### 4.5 Tombol
```css
.btn { display:inline-block; padding: 12px 20px; border-radius: var(--radius-1); text-decoration:none; font-weight:600; }
.btn-primary { background: var(--color-primary); color: #fff; }
.btn-primary:hover { background: var(--color-primary-700); }
```

#### 4.6 Kartu Produk
```css
.card { border: 1px solid #e5e7eb; border-radius: var(--radius-1); box-shadow: var(--shadow-1); overflow: hidden; background: #fff; }
.card img { width: 100%; height: auto; display:block; }
.card-body { padding: var(--space-4); }
.card-title { font-size: var(--fs-2); margin-bottom: var(--space-2); }
.card-price { color: var(--color-primary); font-weight:700; }
```

#### 4.7 Formulir (Pencarian/Newsletter)
```css
.form-control { width:100%; padding: 10px 12px; border:1px solid #d1d5db; border-radius: var(--radius-1); }
.form-group { margin-bottom: var(--space-4); }
```

### 5) Menyusun Halaman Produk
Di [keyboard-shop.html](keyboard-shop.html), tampilkan grid produk:
```html
<section class="container stack-4">
  <h2>Produk Unggulan</h2>
  <div class="grid grid-3">
    <article class="card">
      <img src="img/keyboard/sample1.jpg" alt="Keyboard mekanik 65%">
      <div class="card-body">
        <h3 class="card-title">KeyChron K6</h3>
        <p class="card-price">Rp 1.200.000</p>
        <a class="btn btn-primary" href="#">Tambah ke Keranjang</a>
      </div>
    </article>
    <!-- duplikasi untuk item lainnya -->
  </div>
  
  <form class="stack-4" aria-label="Pencarian produk">
    <div class="form-group">
      <label class="sr-only" for="q">Cari produk</label>
      <input id="q" class="form-control" type="search" placeholder="Cari switch, keycaps...">
    </div>
    <button class="btn btn-primary" type="submit">Cari</button>
  </form>
  
  <nav aria-label="Pagination">
    <a class="btn" href="#">← Sebelumnya</a>
    <a class="btn" href="#">Berikutnya →</a>
  </nav>
  
  <aside class="stack-4" aria-label="Filter">
    <h3>Filter</h3>
    <label><input type="checkbox"> Hot-swap</label>
    <label><input type="checkbox"> Wireless</label>
  </aside>
  
  <section aria-label="Ulasan Pelanggan">
    <h3>Ulasan</h3>
    <p>"Keyboard mantap untuk pemula." — Andi</p>
  </section>
  
  <section aria-label="FAQ">
    <h3>FAQ</h3>
    <details><summary>Apakah bisa custom keycaps?</summary><p>Bisa, kompatibel dengan profil umum.</p></details>
  </section>
</section>
```

### 6) Aksesibilitas & SEO
- Gunakan elemen semantik (`header`, `nav`, `main`, `section`, `footer`).
- Teks alternatif pada gambar (`alt`).
- Kontras warna memadai (cek gunakan devtools). 
- Metadata dasar: `title`, `meta description` (opsional).

### 7) Performa
- Kompres gambar (JPEG/WebP) dan ukur ulang sesuai kebutuhan.
- Muat CSS utama di `<head>`, tunda skrip berat (defer/async bila relevan).
- Hindari framework ganda; minimalkan file yang di-load.

### 8) Versi & Kolaborasi
```bash
git init
git add .
git commit -m "Setup awal struktur + komponen CSS"
git branch -M main
```
Gunakan branch fitur untuk perubahan besar, buat Pull Request untuk review.

### 9) Publikasi
- Ikuti bagian "Deploy" di atas (GitHub Pages/Netlify/Vercel).

### 10) Rubrik Penilaian (Contoh)
- **Struktur & Semantik (25%)**: Folder rapi, HTML semantik.
- **Komponen CSS (30%)**: Desain sistem/tokens, utilitas, komponen reusable.
- **Responsivitas & Aksesibilitas (20%)**: Layout responsif, alt text, kontrast.
- **Konten & Navigasi (15%)**: Navigasi jelas, konten terorganisir.
- **Deploy & Dokumentasi (10%)**: Situs terpublikasi, README lengkap.
