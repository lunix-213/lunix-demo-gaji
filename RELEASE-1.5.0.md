# LUNIX Workforce 1.5.0 — Release Notes (Web Demo)

- **Executive Dark Mode & Light Mode**: Toggle tema di navbar & layar login dengan persistensi `localStorage` dan tetap aman untuk cetak slip/kartu pegawai.
- **Lab Simulasi Gaji, Lembur (PP 35/2021) & PPh 21 (`Simulasi Gaji`)**: Kalkulator *What-If* interaktif dengan rumus lembur 1/173 (hari kerja 1,5×/2×, akhir pekan 2×/3×/4×), estimasi BPJS (1% / 2% / 1%), PPh 21 progresif PTKP (`TK/0`–`K/3`), donut SVG live, preset cepat, muat data pegawai demo, dan salin ringkasan.
- **Analitik Dashboard Eksekutif**: Panel Alokasi Payroll per Divisi (dengan delta komparasi Agustus vs September 2026), Radar Perhatian HR real-time dari IndexedDB, Siklus Penggajian 5 Tahap interaktif, dan kartu KPI yang dapat diklik.
- **Penggajian & Kliring Bank**: Kartu Ringkasan Batch Kliring Bank, ekspor CSV Batch Kliring Bank (anti-injeksi formula), serta preset cepat tambahan/potongan di editor rincian draf.
- **Tur Spotlight Interaktif, 10 Misi Eksplorasi & 8 Modul Tutorial**: Panduan sorotan langkah-demi-langkah bersama Levia, Pusat Tutorial & Misi 3-tab, tips kontekstual per halaman, Pusat Bantuan berkategori dengan tombol coba langsung, dan 4 skenario 1-klik di layar login.
- **Hardened Production Build**: 17/17 unit test lulus, JS diminifikasi & diobfuskasi (`target: browser-no-eval`, tanpa sourcemap), CSS diminifikasi, dan Service Worker offline diperbarui.
