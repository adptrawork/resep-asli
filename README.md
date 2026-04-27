# Resep Asli - RSUD H. ABDUL MANAP KOTA JAMBI

Formulir Resep Asli dengan Telaah Resep untuk keperluan pencetakan di kertas 1/3 F4 (165mm × 107.5mm landscape).

## 📋 Fitur

- **Layout 2 kolom grid**: Informasi pasien/dokter di atas, Daftar Resep kiri, Telaah Resep kanan
- **Format Resep Medis**:
  - Mendukung obat tunggal dan racikan
  - Posisi jumlah obat dinamis (sejajar nama untuk tunggal, sejajar metode untuk racikan)
  - Signatura (aturan pakai) selalu di baris terbawah dengan format italic
- **Telaah Resep Lengkap**:
  - 10 poin Telaah Resep (kejelasan, identitas, dosis, frekuensi, dll)
  - 6 poin Telaah Obat (identitas, jenis, kekuatan, bentuk sediaan, dll)
  - 7 poin Edukasi Obat
  - Persetujuan Perubahan & Waktu Tunggu
- **Tanda Tangan**:
  - Kolom Paraf Pasien/Keluarga (65% - lebih longgar untuk TTD)
  - Kolom Petugas Farmasi (35%)
  - Tabel Proses: Hitung, Timbang, Kemas, Penyerahan
- **Print Optimization**:
  - Hybrid approach: Fluid structure + Scale fine-tuning
  - Kertas 1/3 F4 (165mm × 107.5mm landscape)
  - Scale 0.88 untuk teks tajam maksimal

## 🚀 Penggunaan

### Cara Cetak

1. Buka file `index.html` di browser modern (Chrome, Firefox, Edge, Safari)
2. Klik tombol "CETAK RESEP ASLI" atau tekan `Ctrl+P` / `Cmd+P`
3. Pastikan ukuran kertas terdeteksi sebagai 1/3 F4 atau atur manual:
   - Width: 165mm (6.5 inches)
   - Height: 107.5mm (4.23 inches)
   - Orientation: Landscape
   - Margins: 0.2cm

### Deployment

Project ini di-deploy secara otomatis ke GitHub Pages melalui `.github/workflows/static.yml`:

1. Push ke branch `main`
2. GitHub Actions akan mendeploy ke GitHub Pages
3. Akses di: `https://<username>.github.io/resep-asli/`

## 🛠️ Pengembangan

### Struktur Proyek

```
resep-asli/
├── index.html          # Halaman utama - layout resep
├── style.css           # Styling dengan hybrid print approach
├── README.md           # Dokumentasi utama
├── TODO.md             # Catatan pengembangan
├── docs/               # Dokumentasi tambahan
│   ├── SETUP.md       # Panduan setup & deployment
│   ├── PRINT_GUIDE.md # Panduan cetak lengkap
│   └── STRUCTURE.md   # Struktur kode & arsitektur
├── .github/
│   └── workflows/
│       └── static.yml  # GitHub Pages deployment
├── .claude/            # Konfigurasi Claude Code
└── .vscode/            # Konfigurasi VSCode
```

### Dokumentasi

- 📖 [Panduan Setup & Deployment](docs/SETUP.md) - Cara menjalankan dan mendeploy
- 🖨️ [Panduan Cetak Lengkap](docs/PRINT_GUIDE.md) - Pengaturan printer & troubleshooting
- 🏗️ [Struktur Kode](docs/STRUCTURE.md) - Arsitektur & komponen

### Hybrid Print Approach

Layout menggunakan pendekatan kombinasi:

1. **Fluid Structure (Persentase)**
   - Info-table label: 38%, separator: 5%
   - Resep table: R/ 12%, Aturan 15%, Jml 20%
   - Checklist Y/T: 8% masing-masing

2. **Scale Fine-Tuning**
   - Base width: 210mm (A5 landscape)
   - Transform scale: 0.88
   - Scale minimal karena struktur sudah fluid

3. **Spacing Optimisasi**
   - Padding: 0-2px untuk tabel
   - Line-height: 1.2-1.25
   - Font size: 5.5-7pt

### Menyesuaikan Ukuran Kertas

Jika perlu menyesuaikan scale untuk printer berbeda, ubah di `style.css`:

```css
@media print {
  .page {
    transform: scale(0.88); /* Ubah nilai ini */
  }
}
```

- `0.90` - Jika layout terlalu kecil
- `0.88` - Default (rekomendasi)
- `0.85` - Jika layout terlalu besar/memotong

## 📝 Konvensi Penulisan Resep

### Format Tunggal

```
R/ 1 | Omeprazole 20 mg Kaplet | | Jml: 10
     |                          | |
     | S. 2 dd cap I (ac)       | |
```

### Format Racikan

```
R/ 1 | Amoxicillin 125 mg       | |
     | Parasetamol 100 mg       | |
     | m.f. pulv. dtd. No. XV   | | Jml: 15 (Racikan)
     |                          | |
     | S. 3 dd pulv I           | |
```

## 🔧 Konfigurasi Browser

Untuk hasil cetak terbaik, pastikan pengaturan browser:

- **Chrome/Edge**: Settings > Print > More settings
  - Background graphics: ON
  - Margins: Default atau None
- **Firefox**: Print > Page Setup
  - Print backgrounds: Checked
- **Safari**: Print > Show Details
  - Print backgrounds: Checked

## 📄 Lisensi

Project ini dikembangkan untuk RSUD H. ABDUL MANAP KOTA JAMBI.

## 🤝 Kontribusi

Untuk kontribusi atau laporan bug, silakan buat issue di GitHub repository.
