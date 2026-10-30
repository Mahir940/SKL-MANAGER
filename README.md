# SKL Manager

Aplikasi manajemen tugas SKL (Syarat Kecakapan Lulusan): dashboard, daftar SKL, kalender, progress, pengingat, pengaturan. Data tersimpan di localStorage.

## Struktur
```
skl-manager/
├─ index.html        # kerangka halaman
├─ css/style.css     # tema light/dark, layout responsive
├─ js/icons.js       # ikon SVG
├─ js/app.js         # data, tampilan, logika, pengingat, export/import
├─ sw.js             # service worker (offline + notifikasi)
├─ manifest.json     # agar bisa di-install (PWA)
└─ icons/icon.svg
```

## Menjalankan
Buka `index.html` langsung di browser, atau jalankan server lokal agar service worker aktif:
`python3 -m http.server 8000` lalu buka http://localhost:8000

Untuk online, unggah seluruh folder ke hosting statis (GitHub Pages, Netlify, Vercel). Wajib HTTPS agar notifikasi dan install bekerja.

## Notifikasi
- Notifikasi browser muncul saat aplikasi dibuka (atau tab masih berjalan). Menggunakan service worker jika tersedia, sehingga juga jalan di Android Chrome.
- Notifikasi saat browser benar-benar tertutup belum ada: butuh server Web Push (FCM/VAPID). `sw.js` sudah punya handler `push`, jadi tinggal menambah server.
- Alternatif tanpa server: ikon kalender di tiap SKL membuka Google Calendar, atau Pengaturan > Data > Kalender (.ics) untuk mengimpor semua deadline sekaligus ke Google Calendar dengan pengingat H-7, H-3, H-1, dan hari H.
