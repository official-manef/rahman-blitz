# MonEscrow

Presentasi web bergaya slide untuk konsep MonEscrow, dengan tagline **“Silence pays. Objection pauses.”** Repositori ini berisi halaman HTML dan aset visual; halaman tersebut bukan bukti bahwa layanan escrow atau backend telah diimplementasikan.

## Membuka presentasi

Buka `index.html` langsung di browser, atau sajikan direktorinya:

```bash
python3 -m http.server 8000
```

Tidak ada langkah build. Satu-satunya skrip npm adalah `npm run env:check`, yang memeriksa kesesuaian nama variabel lingkungan antara kode dan `.env.example`; halaman ini tidak membaca variabel lingkungan apa pun.

## Mengoperasikan

Tujuh slide, tiap slide punya beberapa langkah yang muncul satu per satu.

- `→`, `↓`, `Space`, `Enter`, `PageDown`: langkah berikutnya.
- `←`, `↑`, `Backspace`, `PageUp`: langkah sebelumnya.
- `N`: buka/tutup catatan pembicara. `R`: mulai dari awal. `F`: layar penuh.
- Klik atau tap di 10% tepi kiri/kanan panggung, atau geser di layar sentuh.

Penghitung dan judul dokumen mengikuti posisi, misalnya `3/7 · The challenge window · MonEscrow`. Timer di HUD berubah kuning pada 2:45 dan merah pada 3:00.

## Tata letak dan skala

Panggung selalu 16:9: `width: min(100vw, calc(100vh * 16 / 9))` dengan `aspect-ratio: 16 / 9`. Di dalamnya semua ukuran memakai `cqw` (persen dari lebar panggung), dan `h1`/`h2`/`.lede` memakai `clamp()` supaya tetap terbaca di layar kecil. Di ponsel 375px panggung menjadi 375x211 dengan huruf `h1` 42px. Halaman tidak pernah menggulir secara horizontal.

## Struktur repositori

- `index.html`: halaman presentasi.
- `logo-mark.svg`, `logo.svg`: aset logo.
- `three-phone-demo.png`: aset gambar.

## Batasan dan verifikasi

Repositori ini menunjukkan presentasi/prototipe visual, bukan implementasi layanan escrow. Tidak ada backend, alur transaksi nyata, atau hasil deployment yang dapat dipastikan dari berkas yang tersedia.

Verifikasi terakhir dijalankan di browser pada 1280px dan 375px: ketujuh slide terbuka lewat tombol panah, langkah per slide muncul berurutan, `N` membuka catatan, geser di layar sentuh berpindah slide, dan tidak ada gulir horizontal di 375px. Tidak ada skrip pengujian otomatis.
