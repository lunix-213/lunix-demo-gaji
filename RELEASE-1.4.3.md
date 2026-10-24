# LUNIX 1.4.3 · Ruang demo yang lebih mudah digunakan

## Perubahan

- Maskot terbaru dipakai konsisten pada panggung login, banner Beranda, navbar, Pusat Bantuan, pendamping dan ringkasan penggajian. Enam aset WebP dari pemilik tetap lokal dan tidak diubah.
- Pemilih tanggal/bulan kustom: ketuk field untuk membuka kalender atau grid 12 bulan. Tahun dapat dipilih dari daftar; tanggal memakai kalender Senin–Minggu. Tersedia navigasi bulan/tahun, Hari ini/Bulan ini, penanda pilihan, batas min/max dan Kosongkan untuk field opsional. Semua filter bulan dan field tanggal/bulan di Form memakai komponen yang sama, termasuk tanggal mulai kerja, kebijakan gaji, jadwal, koreksi absensi, lembur dan pembayaran. Nilai tersimpan tetap ISO YYYY-MM atau YYYY-MM-DD.
- Penggajian: ringkasan total periode dengan maskot, kartu status Dibayar/Final/Draf yang bisa menjadi filter, pencarian nama/NIP, pilihan Tabel/Kartu, avatar/NIP, tombol tindakan yang lebih jelas. Mode kartu menjadi pilihan awal pada layar kecil. Total periode tidak berubah saat pencarian, filter atau pagination. Cetak payroll tetap mencakup seluruh payroll Final/Dibayar pada bulan yang dipilih.
- Pencarian serta pagination 10/25/50 untuk tabel data. Direktori pegawai, jabatan, susunan kerja, pola shift, penugasan lembur pegawai dan audit juga diberi pagination. Pencarian berjalan pada seluruh hasil yang diizinkan untuk akun, sebelum dipotong per halaman. Kalender, pilihan dropdown, komponen form dan ringkasan singkat Dashboard tetap mengikuti bentuk masing-masing.
- Animasi aktif secara bawaan; tombol jeda/aktifkan animasi di login dan navbar dihapus. Preferensi jeda lama tidak lagi digunakan. Pengaturan pengurangan gerakan perangkat tetap dihormati. Tombol layar penuh desktop dipertahankan.

## Akun demonstrasi

Username publik `lunix_demo`, password publik `Demo123!`, peran SuperAdmin. Akun ini ditambahkan khusus mode demo. Form login mengisinya otomatis jika akses tersebut sudah tersedia, sehingga pengunjung tinggal menekan Masuk. Tombol Gunakan akun lain mengosongkan kedua field; pengguna tetap dapat mengetik kredensial lain. Ini nilai input bawaan yang dapat diedit, bukan placeholder kosong.

Akun `lunix_demo` tidak dapat diubah, dinonaktifkan, diturunkan perannya, direset passwordnya atau dihapus melalui API repository maupun layar Pengguna. Selama mode demo, password semua SuperAdmin dikunci, termasuk melalui reset password pada layar Pengguna. Pengubahan peran SuperAdmin ke peran lain juga ditolak selama mode demo agar penguncian password tidak dilewati. HR/pegawai tetap dapat mengganti password dan diminta mengganti password awal akun baru sebagaimana mestinya. Akun SuperAdmin baru di ruang demo tidak diarahkan ke layar perubahan password yang dikunci.

Akun publik dapat mengembalikan fixture melalui Reset ke data demo. Pemulihan backup dan perpindahan ke data kosong/operasional menggunakan akun SuperAdmin pemilik agar akses demonstrasi tidak hilang. Ini tidak mengubah kemampuan pemilik melakukan reset/pemulihan sebagaimana versi sebelumnya.

Akun SuperAdmin pemilik dan HR yang sudah ada **tidak dihapus atau diganti**. Saat pembaruan pada database demo lama, akun baru diberi akses ke kunci data yang sama dengan memakai material provisioning bawaan yang masih cocok. Password akun yang sudah diganti, pegawai, catatan dan payroll tidak ditimpa. Jika semua akun bawaan sudah memakai pembungkus kunci baru, pengguna perlu masuk dahulu memakai akun yang sudah ada; setelah autentikasi berhasil akun demo ditambahkan tanpa reset. Database operasional tidak diberi akun publik atau kredensial login bawaan.

Kredensial demonstrasi memang publik. Aplikasi tetap memakai penyimpanan lokal dan batas otorisasi per peran yang sama; ini bukan autentikasi server untuk banyak perangkat. Obfuscation tidak menjadikan kredensial demo rahasia.

## Distribusi

- APK: package `id.lunix.workforce`, versionName 1.4.3, versionCode 7, sertifikat rilis yang sama. Pasang sebagai pembaruan tanpa uninstall untuk mempertahankan data.
- Web: ZIP hasil statis/serverless di root, tetap mendukung subpath GitHub Pages dan offline setelah cache pertama. Gunakan tombol Muat ulang ketika pembaruan web siap; simpan pekerjaan sebelum mengaktifkannya.
- Source: kode yang dapat dibaca, aset dan README. Build web dan logika web di APK diminifikasi/diobfuscate tanpa source map. Kunci penandatanganan dan password akun pemilik tidak disertakan.
- Tidak ada perubahan skema IndexedDB, aturan perhitungan gaji, plugin atau izin native. Native shell APK 1.4.2 digunakan kembali, aset web diperbarui, manifest versi dinaikkan, kemudian zipalign dan signing. Bukan kompilasi Gradle native penuh.

## Pemeriksaan

`npm test` mencakup penguncian akun, migrasi data demo dan batas mode operasional. `npm run test:release` menguji login bawaan, pemilih tanggal/bulan, pagination/pencarian, tampilan gaji, perlindungan akun, responsivitas dan offline melalui server statis subpath. Script e2e/workforce/upgrade memeriksa alur bisnis, tanggal melalui UI dan data lama; helper showAll memilih 50 baris agar pemeriksaan bisnis tidak dibatasi halaman pertama. Pagination itu sendiri diperiksa terpisah dalam release143-check.
