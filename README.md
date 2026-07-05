# UMKM-Link

Katalog digital & sistem pemesanan sederhana untuk **Toko ATK Sumber Jaya** — dibuat untuk **Hackathon Vibe Coding Polihasnur 2026**.

**🔗 Live demo**: https://app.netlify.com/projects/umkm-link-atk-sumberjaya/overview
**📦 Repo**: https://github.com/yyyyyyyhkll/umkm-link-atk-sumberjaya

---

## Latar Belakang

Sebelum ada UMKM-Link, Toko ATK Sumber Jaya cuma bisa dijangkau kalau pelanggan datang langsung atau telepon buat nanya stok, dan pemilik toko mencatat pesanan serta stok manual di buku. UMKM-Link menjawab itu lewat katalog digital yang bisa dibuka kapan saja, dashboard admin yang menggantikan buku catatan, dan tombol kontak WhatsApp yang tetap menjaga sisi personal transaksi — tanpa menghilangkan cara pelanggan lama biasa bertransaksi.

## Fitur

**Customer**
- Katalog produk dengan search, filter kategori, sort harga, dan filter stok tersedia
- Detail produk + rekomendasi "Sering Dibeli Bersama"
- Keranjang belanja dengan validasi stok real-time
- Checkout: data pelanggan, pilihan ambil sendiri/diantar (ongkir otomatis per kecamatan), 3 metode pembayaran (COD, Transfer Bank, QRIS)
- Invoice otomatis, bisa diunduh sebagai PDF
- Riwayat pesanan + "Pesan Lagi"

**Admin**
- Dashboard: pesanan hari ini, pendapatan, produk terlaris (grafik sederhana)
- CRUD produk penuh (tambah, edit, hapus — termasuk produk bawaan)
- Pengelolaan kategori otomatis (tinggal ketik nama baru)

## Tech Stack

Single-file vanilla JavaScript (tanpa framework) + Tailwind CSS, `html2pdf.js` untuk invoice — semua di-vendor lokal (folder `vendor/`), bukan CDN, supaya tidak tergantung layanan pihak ketiga selama masa penilaian. Data disimpan di **LocalStorage browser** — tidak ada backend/server.

## Keputusan Desain yang Disengaja (Baca Ini Dulu)

Beberapa hal di bawah ini terlihat seperti kekurangan kalau dilihat sekilas, tapi ini keputusan sadar mengingat waktu pengerjaan solo dalam hitungan hari, bukan kelalaian:

- **Login admin cuma tombol, tanpa password.** Klik "Masuk sebagai Admin" langsung dapat akses penuh CRUD produk & statistik. Ini sesuai scope awal proyek (mock login, tanpa validasi sungguhan) — autentikasi asli butuh backend yang di luar cakupan waktu pengerjaan. Ini bukan lubang keamanan yang terlewat; ini simulasi peran untuk keperluan demo.
- **Data tersimpan per-browser (LocalStorage), tidak sinkron antar device.** Produk yang ditambah dari satu perangkat tidak otomatis muncul di perangkat lain. Cocok untuk demo satu perangkat; sinkronisasi lintas device butuh backend/database yang sengaja tidak dikerjakan agar waktu terpakai untuk fitur inti yang stabil.
- **Nomor WhatsApp, nomor rekening, dan QRIS di aplikasi ini bersifat dummy** untuk keperluan demo, bukan kontak/rekening sungguhan.

## Menjalankan Lokal

Tidak perlu instalasi apa pun — buka `index.html` langsung di browser, atau jalankan lewat live server apa saja (VS Code Live Server, `npx serve`, dll).

---

Dibuat oleh tim Trio Anomali Riztek untuk Hackathon Vibe Coding Polihasnur 2026.
