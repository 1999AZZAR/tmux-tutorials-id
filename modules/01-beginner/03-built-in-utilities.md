# Modul 03: Akses Cepat Utilitas Bawaan Tmux

Kekuatan utama Tmux adalah kecepatan. Anda tidak perlu mengetik perintah panjang untuk fitur pemantauan atau manajemen; semuanya hanya berjarak satu ketukan tombol setelah `Prefix` (Ctrl + b).

## 1. Clock Mode (Jam Digital Cepat)
Butuh melihat waktu saat bekerja dalam layar penuh? Tidak perlu keluar dari terminal.
- **Akses**: Tekan `Prefix` lalu `t`.
- Jam digital akan langsung memenuhi pane aktif.
- **Keluar**: Tekan tombol apa saja (seperti `q` atau `Esc`).

## 2. Interactive Chooser (Manajemen Visual)
Jangan menghafal nama sesi jika Anda bisa melihatnya secara visual.
- **Daftar Sesi (Pohon)**: Tekan `Prefix` lalu `s`.
- **Daftar Window**: Tekan `Prefix` lalu `w`.
  - Gunakan panah Atas/Bawah untuk memilih, tekan `Enter` untuk berpindah.
- **Manajemen Client**: Tekan `Prefix` lalu `D` (D besar) untuk memutus paksa terminal lain yang terhubung.

## 3. Command Prompt (Eksekusi Langsung)
Untuk menjalankan perintah Tmux tanpa harus keluar ke shell biasa.
- **Akses**: Tekan `Prefix` lalu `:`.
- Anda bisa mengetik perintah seperti `split-window` dengan dukungan *auto-completion* (tombol `Tab`).

## 4. Customize Mode (Konfigurasi Visual)
Tersedia pada Tmux 3.1+. Mengubah konfigurasi tanpa perlu menyentuh file teks.
- **Akses**: Ketik `tmux customize-mode` di command prompt atau shell.
- Telusuri dan ubah opsi server, sesi, dan window secara langsung.

## 5. Dokumentasi Shortcut Bawaan
Lupa tombol apa untuk melakukan apa? Tanya langsung ke Tmux.
- **Akses**: Tekan `Prefix` lalu `?`.
- Menampilkan daftar lengkap semua shortcut yang sedang aktif. Navigasi menggunakan panah, tekan `q` untuk keluar.

## 6. Pane Indicators (Navigasi Instan)
Pusing mencari pane aktif jika layar terbagi banyak?
- **Akses**: Tekan `Prefix` lalu `q`.
- Angka raksasa akan muncul sebentar di setiap pane. Ketik angka tersebut dengan cepat untuk langsung memindahkan kursor ke pane yang diinginkan.

