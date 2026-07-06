# UMKM-Link

Katalog digital & sistem pemesanan sederhana untuk **Toko ATK Sumber Jaya** — dibuat untuk **Hackathon Vibe Coding Polihasnur 2026**.

**🔗 Live demo**: https://umkm-link-atk-sumberjaya.netlify.app/
**📦 Repo**: https://github.com/yyyyyyyhkll/umkm-link-atk-sumberjaya

---

## Latar Belakang

Sebelum ada UMKM-Link, Toko ATK Sumber Jaya cuma bisa dijangkau kalau pelanggan datang langsung atau telepon buat nanya stok, dan pemilik toko mencatat pesanan serta stok manual di buku. UMKM-Link menjawab itu lewat katalog digital yang bisa dibuka kapan saja, dashboard admin yang menggantikan buku catatan, dan tombol kontak WhatsApp yang tetap menjaga sisi personal transaksi — tanpa menghilangkan cara pelanggan lama biasa bertransaksi.

## Fitur

**Customer**
- Katalog produk dengan search, filter kategori, sort harga, dan filter stok tersedia
- Produk dengan varian (Warna, Ukuran, Gramasi, dll — bebas ditentukan admin), masing-masing punya stok sendiri dan bisa punya tambahan harga sendiri (mis. Kertas 80gsm lebih mahal dari 70gsm; varian warna biasanya tanpa tambahan harga)
- Detail produk + rekomendasi "Sering Dibeli Bersama"
- Keranjang belanja dengan validasi stok real-time (per varian kalau produknya punya varian)
- Checkout: data pelanggan, pilihan ambil sendiri/diantar (ongkir otomatis per kecamatan), 3 metode pembayaran (COD, Transfer Bank, QRIS)
- Invoice otomatis, bisa diunduh sebagai PDF
- Riwayat pesanan bisa dilihat siapa saja (termasuk yang belum login), tapi **"Pesan Lagi" dan "Batalkan Pesanan" khusus akun Customer** — guest yang klik langsung diarahkan ke modal login
- Batalkan pesanan sendiri dari Riwayat Pesanan — stok yang sempat terpotong otomatis dikembalikan, dan pesanan yang dibatalkan tidak dihitung di statistik pendapatan admin

**Admin**
- Dashboard: pesanan hari ini, pendapatan, produk terlaris (grafik sederhana) — otomatis mengecualikan pesanan yang sudah dibatalkan
- CRUD produk penuh (tambah, edit, hapus — termasuk produk bawaan), termasuk upload & kompresi foto produk dan pengaturan varian per produk
- Pengelolaan kategori otomatis (tinggal ketik nama baru)
- Export/Import data demo (produk, stok, riwayat pesanan) dalam bentuk file JSON — buat mindahin skenario demo antar browser/device tanpa perlu server

## Tech Stack

Single-file vanilla JavaScript (tanpa framework) + Tailwind CSS, `html2pdf.js` untuk invoice — semua di-vendor lokal (folder `vendor/`), bukan CDN, supaya tidak tergantung layanan pihak ketiga selama masa penilaian. Data disimpan di **LocalStorage browser** — tidak ada backend/server.

## Keputusan Desain yang Disengaja (Baca Ini Dulu)

Beberapa hal di bawah ini terlihat seperti kekurangan kalau dilihat sekilas, tapi ini keputusan sadar mengingat waktu pengerjaan dalam hitungan hari, bukan kelalaian:

- **Login admin cuma tombol, tanpa password.** Klik "Masuk sebagai Admin" langsung dapat akses penuh CRUD produk & statistik. Ini sesuai scope awal proyek (mock login, tanpa validasi sungguhan) — autentikasi asli butuh backend yang di luar cakupan waktu pengerjaan. Ini bukan lubang keamanan yang terlewat; ini simulasi peran untuk keperluan demo, dan sengaja ada banner di halaman utama yang mengundang juri mencobanya.
- **Data tersimpan per-browser (LocalStorage), tidak sinkron antar device.** Produk yang ditambah dari satu perangkat tidak otomatis muncul di perangkat lain. Fitur Export/Import di Admin Dashboard ada khusus untuk menjembatani ini tanpa backend — export dari device kamu, import di device yang dipakai demo.
- **"Pesan Lagi" dan "Batalkan Pesanan" sengaja dibatasi untuk akun Customer**, sementara siapa pun (termasuk yang belum login) tetap bisa melihat isi Riwayat Pesanan. Ini simulasi benefit akun sederhana — guest bisa lihat, tapi harus login dulu untuk aksi yang mengubah data.
- **Nomor WhatsApp, nomor rekening, dan QRIS di aplikasi ini bersifat dummy** untuk keperluan demo, bukan kontak/rekening sungguhan.

## Menjalankan Lokal

Tidak perlu instalasi apa pun — buka `index.html` langsung di browser, atau jalankan lewat live server apa saja (VS Code Live Server, `npx serve`, dll).

---

Dibuat oleh tim Trio Anomali Riztek untuk Hackathon Vibe Coding Polihasnur 2026.
