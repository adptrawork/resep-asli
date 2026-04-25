# TODO - Catatan Pengembangan

## ✅ Selesai

### Phase 1: Layout Dasar
- [x] Struktur grid 2 kolom × 3 baris
- [x] Header dengan logo dan info rumah sakit
- [x] Info pasien (No. RM, SEP, Kartu, Telpon, Unit, Nama, TTL, BB, Penjamin, Diagnosa, Alergi)
- [x] Info dokter (No. Resep, Dokter, SIP, Ruangan/Poli, Tanggal, Jam, Iter)
- [x] Daftar Resep dengan format R/
- [x] Telaah Resep (1-10)
- [x] Telaah Obat (1-6)
- [x] Persetujuan Perubahan
- [x] Waktu Tunggu
- [x] Edukasi Obat (1-7)
- [x] Tabel Paraf (Pasien/Keluarga + Petugas Farmasi)
- [x] Tabel Proses (Hitung, Timbang, Kemas, Penyerahan)

### Phase 2: Styling
- [x] Hapus border layout utama (.page, .header, .cell)
- [x] Simplifikasi border tabel (0.5px solid #000)
- [x] Font Poppins untuk tampilan profesional
- [x] Spacing yang konsisten antar elemen

### Phase 3: Data Contoh
- [x] Contoh 1: Infeksi Saluran Pernapasan (Anak) - Racikan puyer + Sirup
- [x] Contoh 2: Hipertensi & Kolesterol (Dewasa) - 3 obat tunggal
- [x] Contoh 3: Penyakit Kulit - Racikan salep campuran
- [x] Contoh 4: Nyeri Lambung & Vitamin - Kaplet + Racikan kapsul

### Phase 4: Print Optimization
- [x] Ukuran kertas 1/4 F4 (165mm × 107.5mm landscape)
- [x] Hybrid approach: Fluid structure + Scale fine-tuning
- [x] Fluid structure dengan persentase (38%, 5%, 12%, 15%, 20%, 8%)
- [x] Scale fine-tuning 0.88 (minimal scale untuk teks tajam)
- [x] Optimasi spacing (padding 0-2px, line-height 1.2-1.25)
- [x] Optimasi font size (5.5-7pt)

### Phase 5: Signature & Alignment
- [x] Perbesar kolom paraf Pasien (65%) dan Farmasi (35%)
- [x] Tinggi signature 48px untuk ruang TTD cukup
- [x] Sejajarkan process-table dengan signature-table
- [x] Samakan padding antar cell untuk alignment konsisten

## 🔮 Future Enhancements

### Potensial Fitur
- [ ] Form input untuk data pasien/dokter dinamis
- [ ] Database untuk menyimpan riwayat resep
- [ ] Export/Import data resep (JSON/CSV)
- [ ] Barcode/QR code untuk tracking resep
- [ ] Multi-bahasa (Indonesia/English)
- [ ] Dark mode untuk tampilan layar
- [ ] Preview cetak real-time
- [ ] Template resep yang bisa dipilih

### Pengembangan Frontend
- [ ] Framework modern (Vue/React) untuk interaktivitas
- [ ] State management untuk form
- [ ] Validation form
- [ ] Auto-save draft
- [ ] Print queue management

### Backend (Jika Diperlukan)
- [ ] REST API untuk CRUD resep
- [ ] Authentication & Authorization
- [ ] Audit log
- [ ] Integration dengan sistem rumah sakit (SIMRS)
- [ ] Email/SMS notifikasi

## 📝 Catatan Penting

### Print Scale Adjustment
Jika hasil cetak tidak pas di printer berbeda, ubah nilai di `style.css`:
```css
@media print {
    .page {
        transform: scale(0.88); /* 0.90, 0.88, 0.85 */
    }
}
```

### Konvensi Penulisan Resep
- **Tunggal**: Jml sejajar nama obat
- **Racikan**: Jml sejajar metode racik (m.f. pulv., m.f. cap., dll)
- **Signatura**: Selalu di baris terbawah, format italic

### Alignment Rules
- Cell padding: 4px 5px (konsisten)
- Signature height: 48px
- Process height: 48px (sejajar signature)
- Checklist Y/T: 10% width (cukup untuk centang)

## 🐛 Known Issues

- Logo placeholder mungkin muncul jika URL logo gagal dimuat
- Browser tertentu mungkin perlu pengaturan print manual (background graphics)

## 📚 Referensi

- Ukuran kertas F4: 215mm × 330mm
- Ukuran 1/4 F4: 165mm × 107.5mm
- A5 landscape: 210mm × 148mm
