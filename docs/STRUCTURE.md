# Struktur Kode - Resep Asli

## Overview

Project ini menggunakan HTML murni untuk struktur dan CSS untuk styling dengan pendekatan hybrid print optimization.

## File Structure

```
resep-asli/
├── index.html          # Halaman utama
├── style.css           # Styling & print optimization
├── README.md           # Dokumentasi utama
├── TODO.md             # Catatan pengembangan
├── docs/               # Dokumentasi tambahan
│   ├── SETUP.md       # Panduan setup & deployment
│   ├── PRINT_GUIDE.md # Panduan cetak lengkap
│   └── STRUCTURE.md   # Dokumentasi ini
├── .github/
│   └── workflows/
│       └── static.yml  # GitHub Pages deployment
├── .claude/            # Konfigurasi Claude Code
└── .vscode/            # Konfigurasi VSCode
```

## HTML Structure (`index.html`)

### Root Container

```html
<div class="page">
  <header class="header">...</header>
  <h4>RESEP ASLI</h4>
  <div class="main-grid">...</div>
  <p class="note-text">...</p>
  <div class="no-print">...</div>
</div>
```

### Grid Layout (2 kolom × 3 baris)

```
┌─────────────────────────┬─────────────────────────┐
│  cell-info-pasien      │  cell-info-dokter       │
│  (grid-row: 1)         │  (grid-row: 1)         │
├─────────────────────────┼─────────────────────────┤
│  cell-daftar           │  cell-telaah-detail     │
│  (grid-row: 2)         │  (grid-row: 2/4)       │
├─────────────────────────┤                        │
│  cell-proses           │                        │
│  (grid-row: 3)         │                        │
└─────────────────────────┴─────────────────────────┘
```

### Component Breakdown

#### Header

- Logo rumah sakit
- Nama rumah sakit
- Alamat & kontak

#### Info Pasien (cell-info-pasien)

Tabel dengan 3 kolom: label (38%), separator (5%), nilai (auto)

Fields:

- No. RM, No. SEP, No. Kartu
- No. Telpon, Unit Asal
- Nama Pasien, Tanggal Lahir
- Berat Badan, Penjamin
- Diagnosa, Riwayat Alergi

#### Info Dokter (cell-info-dokter)

Tabel dengan 3 kolom: label (38%), separator (5%), nilai (auto)

Fields:

- No. Resep, Dokter, SIP
- Ruangan/Poli, Tanggal, Jam, Iter

#### Daftar Resep (cell-daftar)

Tabel dengan 4 kolom:

- col-r (12%): Nomor R/
- col-nama (auto): Nama obat
- col-aturan (15%): Aturan pakai
- col-jml (20%): Jumlah

Format:

- Tunggal: 1 baris
- Racikan: 2+ baris dengan signatura terpisah

#### Telaah Detail (cell-telaah-detail)

Spans grid-row 2-4, berisi:

1. Telaah Resep (1-10) - 10 poin dengan kolom Y/T
2. Telaah Obat (1-6) - 6 poin dengan kolom Y/T
3. Persetujuan Perubahan - Form isian
4. Waktu Tunggu - Form isian
5. Edukasi Obat (1-7) - 7 poin dengan kolom Y
6. Signature Table - 2 kolom (Pasien 65%, Farmasi 35%)

#### Proses (cell-proses)

Tabel dengan 4 kolom (25% masing-masing):

- Hitung, Timbang, Kemas, Penyerahan

## CSS Structure (`style.css`)

### Organization

```css
/* 1. Page Setup */
@page { ... }

/* 2. Base Styles */
* { ... }
body { ... }
.page { ... }

/* 3. Header */
.header { ... }
.logo { ... }
.hospital-info { ... }

/* 4. Main Grid */
.main-grid { ... }
.cell { ... }

/* 5. Info Tables */
.info-table { ... }
.info-table .lbl { ... }
.info-table .sep { ... }

/* 6. Prescription Area */
.prescription-area { ... }
.resep-table { ... }

/* 7. Checklist Area */
.checklist-container { ... }
.checklist-table { ... }

/* 8. Signature & Process */
.signature-table { ... }
.process-table { ... }

/* 9. Print Styles */
@media print { ... }
```

### Key Classes

| Class              | Purpose         | Key Properties                  |
| ------------------ | --------------- | ------------------------------- |
| `.page`            | Container utama | width: 100%, transform: scale() |
| `.main-grid`       | Layout grid     | grid-template-columns: 1fr 1fr  |
| `.cell`            | Grid cell       | padding, overflow: hidden       |
| `.info-table`      | Tabel info      | table-layout: fixed             |
| `.resep-table`     | Tabel resep     | border-collapse: collapse       |
| `.checklist-table` | Tabel checklist | font-size: 6.5pt                |
| `.signature-table` | Tabel TTD       | height: 48px                    |
| `.process-table`   | Tabel proses    | width: 25% per kolom            |

### Print Optimization Layers

#### Layer 1: Base Styles (Screen)

- Font size: 7.5pt
- Padding: 5px 7px
- Line-height: 1.3

#### Layer 2: @media print

- Font size: 7pt
- Padding: 2px 3px (reduced)
- Line-height: 1.2-1.25 (reduced)
- Transform scale: 0.88
- Font size tables: 5.5-7pt

### Color Scheme

| Element    | Color   | Usage             |
| ---------- | ------- | ----------------- |
| Text       | #000    | Semua teks utama  |
| Border     | #000    | Semua border      |
| Background | #f0f0f0 | Checklist headers |
| Background | #e8e8e8 | Box titles        |

## Data Flow

### Static Data

Semua data saat ini adalah statis di HTML:

- Data pasien: Hardcoded di `index.html`
- Data dokter: Hardcoded di `index.html`
- Data resep: 4 contoh kasus hardcoded
- Data telaah: Kosong (diisi manual)

### Future Dynamic Data

Jika diimplementasikan sistem dinamis:

1. Backend API menyediakan data
2. Frontend fetch data via fetch() / axios
3. Render ke DOM template
4. Print dengan style yang sama

## Print Process

1. User klik "CETAK RESEP ASLI" atau Ctrl+P
2. Browser mengaktifkan `@media print` rules
3. CSS transform scale diterapkan
4. Layout dirender ke kertas 1/3 F4
5. Browser mengirim ke printer

## Browser Compatibility

| Browser     | Support | Notes                     |
| ----------- | ------- | ------------------------- |
| Chrome 90+  | ✅ Full | Rekomendasi               |
| Firefox 88+ | ✅ Full | Perlu "Print backgrounds" |
| Edge 90+    | ✅ Full | Rekomendasi               |
| Safari 14+  | ✅ Full | Perlu custom paper size   |

## Performance

- **Load time**: < 100ms (HTML + CSS only)
- **Render time**: < 50ms (static content)
- **Print time**: < 5s (typical printer)
- **Total size**: ~40KB (HTML + CSS)

## Accessibility

- Semantic HTML: header, section, table
- Readable font size: 7pt minimum
- Contrast ratio: WCAG AA compliant
- Keyboard navigation: Standard HTML form elements

## Security

- No JavaScript (reduced attack surface)
- No external dependencies (no supply chain risk)
- Static files only (no server-side processing)
- HTTPS recommended for production

## Maintenance

### Adding New Prescription

Edit `index.html` in `.prescription-area`:

```html
<tr>
  <td class="col-r">R/ X</td>
  <td class="col-nama">Nama Obat</td>
  <td class="col-aturan"></td>
  <td class="col-jml">Jml: XX</td>
</tr>
<tr class="row-signatura">
  <td></td>
  <td colspan="3"><i>S. aturan pakai</i></td>
</tr>
```

### Adjusting Layout

Edit `style.css`:

- Grid columns: `.main-grid`
- Column widths: `colgroup col` percentages
- Spacing: padding values in `.cell`, table td
- Scale: `transform: scale()` in `@media print`

### Changing Paper Size

Edit `style.css`:

```css
@page {
  size: <width> <height> landscape;
  margin: 0.2cm;
}
```

Common sizes:

- 1/3 F4: `165mm 107.5mm`
- A5: `210mm 148mm`
- Letter: `279.4mm 215.9mm`
