# LUNIX 1.4 · Web statis untuk GitHub Pages

Paket web sudah selesai dibangun, diminifikasi dan diobfuscate. Tidak memerlukan Node.js, PHP, API, database server, Cloud Functions, atau proses backend pada hosting. GitHub Pages hanya menyajikan berkas statis. Paket ini adalah tampilan web/desktop di browser, bukan installer Windows.

## Mengunggah build yang sudah jadi

1. Ekstrak `LUNIX-1.4.3-web-build.zip`.
2. Salin **isi** ZIP ke root repository atau branch publikasi Anda: `index.html`, folder `assets`, `boot.css`, `sw.js`, `.nojekyll`, dan dokumen pendamping. `index.html` harus berada langsung pada folder publikasi. Jangan mengunggah ZIP sebagai satu berkas dan mengharapkannya menjadi situs.
3. Jika memakai GitHub Desktop, salin berkas tersebut ke folder repository lokal, commit, lalu push. Ikutkan `.nojekyll` agar berkas statis dipublikasikan tanpa proses Jekyll.
4. Di repository GitHub buka **Settings → Pages**. Pada **Source**, pilih **Deploy from a branch**. Pilih branch berisi build dan folder **/(root)**, lalu simpan.
5. Buka alamat HTTPS yang ditampilkan GitHub setelah publikasi selesai. Build memakai jalur relatif, sehingga mendukung alamat repository GitHub Pages maupun root/custom domain tanpa mengganti konfigurasi nama repository.

Gunakan ZIP web-build untuk publikasi hasil jadi. ZIP source ditujukan untuk pengembangan dan tidak diperlukan pada repository publikasi build. Paket build tidak berisi kode JSX asli, source map, keystore atau password SuperAdmin/HR.

## Menyiapkan presentasi

- Gunakan Chrome/Edge modern. Pada desktop tersedia tombol layar penuh di navbar; animasi aktif secara bawaan tanpa tombol jeda. Preferensi pengurangan gerakan sistem tetap dihormati.
- Aplikasi menyimpan IndexedDB pada browser/origin yang digunakan. Akun dan data tidak disinkronkan antar-PC, HP, browser atau origin. APK memiliki penyimpanan sendiri.
- Instalasi baru menyiapkan lingkungan DEMO dengan 12 pegawai, 24 payroll dua bulan, kalender dan empat susunan kerja. Gunakan akses akun yang diberikan pemilik aplikasi.
- Buka situs saat online dan biarkan seluruh pemuatan pertama selesai. Service worker kemudian menyiapkan cache aset. Setelah cache terpasang, aplikasi mendukung pemuatan ulang dan penggunaan offline pada browser yang sama. Pemakaian offline bergantung pada cache/penyimpanan yang tetap tersedia; mode privat bukan pilihan untuk menyimpan pekerjaan permanen.
- HTTPS atau localhost diperlukan untuk kamera, lokasi dan fitur penyimpanan browser yang aman. Izin kamera/GPS tetap diberikan melalui browser. Bukti absensi sintetis di data demo diberi penanda tersendiri.
- Saat versi baru tersedia, aplikasi menampilkan pemberitahuan pembaruan. Simpan perubahan formulir, lalu pilih Muat ulang. Proses ini tidak mereset IndexedDB. Pencadangan data tersedia pada akun SuperAdmin.
- Untuk menjalankan di PC tanpa GitHub, gunakan `npm run preview` dari source yang telah dibangun, atau host berkas build melalui server statis localhost. Jangan membuka `index.html` langsung sebagai `file://`.

## Perlindungan build

JavaScript produksi diminifikasi lalu diobfuscate secara lokal dengan target browser-no-eval. CSS diminifikasi, source map dimatikan, dan Content Security Policy tetap tidak mengizinkan unsafe-eval. Tidak ada pengiriman source ke layanan obfuscation eksternal atau penguncian domain yang menghalangi localhost/GitHub Pages.

Obfuscation menyulitkan pembacaan source hasil build; kode yang berjalan di browser tetap dapat dianalisis. Ini bukan pengganti otorisasi server atau sarana menyembunyikan rahasia. Aplikasi ini tetap offline-first pada perangkat bersama; backend dan sinkronisasi multi-perangkat belum diimplementasikan. Pembatasan peran lokal bukan otorisasi server terhadap pemilik perangkat yang memodifikasi runtime.

## Referensi

- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- https://vite.dev/guide/build#relative-base
- https://github.com/javascript-obfuscator/javascript-obfuscator

Pada ruang demo, akun publik `lunix_demo` terisi otomatis pada login. Gunakan akun lain untuk masuk sebagai pemilik atau peran berbeda. Database operasional tidak memakai isian akun publik. Pembaruan tidak otomatis mereset data; simpan file cadangan sebelum mengganti versi.
