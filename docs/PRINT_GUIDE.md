# Panduan Cetak - Resep Asli

## Ukuran Kertas

| Jenis        | Ukuran      | Dimensi         |
| ------------ | ----------- | --------------- |
| F4 (Folio)   | Full        | 215mm × 330mm   |
| 1/3 F4       | **Default** | 165mm × 107.5mm |
| A5 Landscape | Alternative | 210mm × 148mm   |

**Rekomendasi**: Gunakan 1/3 F4 untuk ukuran yang paling optimal.

## Hybrid Print Approach

Project ini menggunakan pendekatan hybrid untuk hasil cetak terbaik:

### 1. Fluid Structure (Persentase)

Semua lebar kolom menggunakan persentase untuk fleksibilitas:

```css
/* Info Table */
.lbl  → 38%  (Label: No. RM, Nama Pasien, dll)
.sep  → 5%   (Pemisah titik dua)
.val  → Auto (Nilai)

/* Resep Table */
.col-r      → 12%  (Nomor R/)
.col-nama   → Auto (Nama obat)
.col-aturan → 15%  (Aturan pakai)
.col-jml    → 20%  (Jumlah)

/* Checklist Table */
.c-no → 8%   (Nomor urut)
.c-y  → 8%   (Kotak Y)
.c-t  → 8%   (Kotak T)
```

### 2. Scale Fine-Tuning

Transform scale hanya digunakan untuk fine-tuning, bukan scaling penuh:

```css
@media print {
  .page {
    width: 210mm !important; /* Base A5 landscape */
    transform: scale(0.88); /* Fine-tuning minimal */
    transform-origin: top left;
  }
}
```

**Kenapa 0.88?**

- Struktur sudah fluid → scale minimal
- Teks tetap tajam (scale < 0.90)
- Layout proporsional terjaga

### 3. Spacing Optimisasi

Padding dan line-height dikurangi untuk menghemat ruang:

```css
/* Cell padding */
.cell          → 2px 3px
.info-table td  → 0px 1px
.checklist td  → 0px 1px
.resep-table td → 1px 2px

/* Line height */
info-table    → 1.25
checklist     → 1.2
```

## Pengaturan Browser

### Chrome / Edge

1. Buka `index.html`
2. Tekan `Ctrl+P`
3. More Settings:
   - ✅ Background graphics
   - ❌ Headers and footers
   - Margins: Default atau None
   - Paper size: Custom (165mm × 107.5mm)

### Firefox

1. Buka `index.html`
2. Tekan `Ctrl+P`
3. Page Setup:
   - ✅ Print backgrounds
   - Margins: None
   - Orientation: Landscape

### Safari

1. Buka `index.html`
2. Tekan `Cmd+P`
3. Show Details:
   - ✅ Print backgrounds
   - Paper Size: Manage Custom Sizes
   - Width: 6.50 in, Height: 4.23 in

## Menyesuaikan Scale

Jika hasil cetak tidak pas dengan printer berbeda:

```css
@media print {
  .page {
    transform: scale(0.88); /* Ubah nilai ini */
  }
}
```

| Scale | Kondisi              | Penggunaan                      |
| ----- | -------------------- | ------------------------------- |
| 0.90  | Layout terlalu kecil | Printer dengan area cetak besar |
| 0.88  | **Default**          | Printer standar                 |
| 0.85  | Layout terpotong     | Printer dengan margin besar     |

## Troubleshooting

### Masalah: Layout Terpotong

**Solutions:**

1. Kurangi nilai scale (0.88 → 0.85)
2. Pastikan margins di None
3. Cek ukuran kertas custom

### Masalah: Tidak Muat Satu Halaman

**Solutions:**

1. Kurangi jumlah contoh resep
2. Perkecil font size:
   ```css
   @media print {
     body {
       font-size: 6.5pt !important;
     }
   }
   ```
3. Kurangi padding:
   ```css
   @media print {
     .info-table td {
       padding: 0px 0.5px !important;
     }
   }
   ```

### Masalah: Border Tidak Terlihat

**Solutions:**

1. Enable "Print backgrounds"
2. Disable "Print headers and footers"
3. Cek `@media print` rules

### Masalah: Teks Tajam Berkurang

**Solutions:**

1. Tingkatkan scale (0.85 → 0.88 → 0.90)
2. Gunakan kertas kualitas tinggi
3. Pastikan resolusi printer optimal

## Kualitas Cetak

### Thermal Printer

- Gunakan kertas thermal berkualitas
- Pastikan head printer bersih
- Kontras optimal (jika ada pengaturan)

### Laser/Inkjet Printer

- Gunakan kertas minimal 80gsm
- Mode: Normal atau High Quality
- Pastikan tinta/toner cukup

## Tips

1. **Selalu preview dulu** dengan "Save as PDF"
2. **Test print** dengan satu lembar sebelum cetak banyak
3. **Simpan preset** di browser jika sering mencetak
4. **Backup CSS** sebelum mengubah scale
5. **Gunakan font size minimal 6pt** untuk keterbacaan

## Referensi Ukuran

| Unit    | Nilai     | Konversi        |
| ------- | --------- | --------------- |
| 1 inch  | -         | 25.4mm          |
| 1 mm    | -         | 0.039 inch      |
| 1 pt    | -         | 0.353mm (print) |
| 165mm   | 6.50 inch | 1/3 F4 width    |
| 107.5mm | 4.23 inch | 1/3 F4 height   |
