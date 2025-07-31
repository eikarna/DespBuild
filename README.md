# Despair Browser

## Visi

Despair Browser adalah sebuah peramban web yang difork dari Brave Browser, dengan fokus utama pada minimalisme, kecepatan, dan privasi yang kuat. Proyek ini bertujuan untuk "mendebloat" Brave dengan menghapus fitur-fitur non-esensial seperti Sync, AI, VPN, dan Wallet, sambil tetap mempertahankan dan memperkuat inti dari Brave: adblocker-nya yang canggih berbasis Rust.

## Arsitektur & Rencana Teknis

Proyek ini akan menggunakan dan memodifikasi ekosistem open source Brave.

### Repositori yang Akan Di-fork:

1.  **UI & Build System:** `brave/brave-browser`
2.  **Modifikasi Inti Chromium:** `brave/brave-core`
3.  **Mesin Adblocker:** `brave/adblock-rust`
4.  **Basis Chromium:** `chromium/src` (sebagai submodule, mengikuti struktur build Brave)

### Rencana Pengembangan

1.  **Setup Lingkungan Build:**
    *   Mengkloning fork dari `brave/brave-browser`.
    *   Mengatur skrip build agar menunjuk ke fork `brave-core` dan `adblock-rust` milik kita.
    *   Berhasil mengompilasi versi "vanilla" dari Brave terlebih dahulu untuk memastikan build system berjalan dengan benar.

2.  **Debloating (Penghapusan Fitur):**
    *   Secara sistematis mengidentifikasi dan menghapus kode yang berkaitan dengan fitur-fitur berikut:
        *   [ ] Brave Sync
        *   [ ] Brave Leo (Fitur AI)
        *   [ ] Brave VPN
        *   [ ] Brave Wallet (Dompet Kripto)
        *   [ ] Brave Rewards (Sistem Iklan & Reward)
        *   [ ] Fitur lain yang tidak esensial (akan diidentifikasi selama pengembangan).
    *   Proses ini akan melibatkan modifikasi pada `brave-browser` (untuk UI) dan `brave-core` (untuk fungsionalitas inti).

3.  **Penguatan Adblocker:**
    *   Menganalisis konfigurasi `adblock-rust` di dalam `brave-core`.
    *   Mengatur filter list default untuk menyertakan daftar yang lebih komprehensif dan agresif untuk memblokir iklan dan pelacak.

4.  **Branding:**
    *   Mengganti nama, logo, ikon, dan teks di seluruh aplikasi dari "Brave" menjadi "Despair Browser".

5.  **CI/CD dengan GitHub Actions:**
    *   Membuat workflow di repositori `DespairBrowser/brave-browser` (fork kita).
    *   Workflow ini akan mengotomatisasi proses:
        1.  Checkout kode sumber.
        2.  Sinkronisasi dengan submodule (termasuk Chromium).
        3.  Instalasi semua dependensi build.
        4.  Kompilasi browser.
        5.  (Opsional) Menjalankan tes.
        6.  Memaketkan hasil build untuk didistribusikan.
