# Setup Guide - Resep Asli

## Prerequisites

Tidak ada prasyarat khusus. Project ini menggunakan HTML dan CSS murni.

## Local Development

### Cara 1: Buka Langsung di Browser

1. Clone repository:
   ```bash
   git clone https://github.com/adptrawork/resep-asli.git
   cd resep-asli
   ```

2. Buka `index.html` langsung di browser:
   - Double-click file `index.html`
   - atau drag & drop ke browser

### Cara 2: Live Server (Rekomendasi)

Menggunakan VSCode dengan Live Server extension:

1. Install [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.liveserver) di VSCode
2. Buka `index.html`
3. Klik kanan → "Open with Live Server"
4. Browser akan otomatis membuka di `http://127.0.0.1:5500`

### Cara 3: Python Simple HTTP Server

```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

Buka browser di `http://localhost:8000`

### Cara 4: Node.js http-server

```bash
# Install global
npm install -g http-server

# Jalankan
http-server -p 8000
```

Buka browser di `http://localhost:8000`

## Deployment ke GitHub Pages

### Otomatis via GitHub Actions

Project sudah dikonfigurasi untuk auto-deploy:

1. Push ke branch `main`
2. GitHub Actions akan otomatis mendeploy
3. Tunggu beberapa menit
4. Akses di: `https://<username>.github.io/resep-asli/`

### Manual Deploy

Jika ingin deploy manual:

1. Install `gh` CLI
2. Login: `gh auth login`
3. Deploy:
   ```bash
   gh repo set-default <username>/resep-asli
   git checkout -b gh-pages
   git checkout main -- index.html style.css
   git commit -m "Deploy to GitHub Pages"
   git push origin gh-pages
   ```

## Konfigurasi Printer

### Windows

1. Buka `index.html` di browser
2. Tekan `Ctrl+P`
3. Pilih printer:
   - **Thermal Printer**: Pilih driver thermal
   - **Laser/Inkjet**: Pilih printer biasa
4. Pengaturan kertas:
   - Ukuran: Custom (165mm × 107.5mm)
   - atau pilih ukuran terdekat yang tersedia
5. Margins: Minimum atau None
6. Background graphics: Enable

### macOS

1. Buka `index.html` di browser
2. Tekan `Cmd+P`
3. Pada dialog print:
   - Paper Size: Manage Custom Sizes
   - Width: 6.50 inches (165mm)
   - Height: 4.23 inches (107.5mm)
4. Margins: None
5. Background graphics: Check "Print backgrounds"

### Linux

1. Buka `index.html` di browser
2. Tekan `Ctrl+P`
3. Pengaturan printer:
   - Page Setup → Paper Size → Custom
   - Width: 165mm, Height: 107.5mm
4. Margins: None
5. Print background: Enable

## Troubleshooting

### Layout Terpotong

Jika layout terpotong saat dicetak:

1. Cek ukuran kertas di pengaturan print
2. Kurangi nilai scale di `style.css`:
   ```css
   transform: scale(0.85); /* dari 0.88 */
   ```
3. Pastikan margins diatur ke minimum

### Tidak Muat Satu Halaman

Jika konten terlalu panjang:

1. Kurangi jumlah contoh resep di `index.html`
2. Perkecil font size di `@media print`:
   ```css
   body { font-size: 6.5pt !important; }
   ```
3. Kurangi padding di tabel

### Border Tidak Terlihat

Jika border tabel tidak terlihat saat dicetak:

1. Pastikan "Print backgrounds" di-enable
2. Cek printer settings untuk "Print headers and footers" (disable)
3. Verifikasi CSS `@media print` aktif

## Pengembangan

### Edit Style

Untuk mengedit styling:

1. Buka `style.css`
2. Edit properti yang diinginkan
3. Refresh browser (Ctrl+R / Cmd+R)

### Edit Konten

Untuk mengedit konten:

1. Buka `index.html`
2. Edit data pasien/dokter/resep sesuai kebutuhan
3. Refresh browser

### Preview Print Cepat

Untuk preview print tanpa mencetak:

1. Tekan `Ctrl+P` / `Cmd+P`
2. Pilih "Save as PDF" sebagai printer
3. Klik Save untuk preview di PDF viewer
