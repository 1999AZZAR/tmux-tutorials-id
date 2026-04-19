# Modul 03: Utilitas dan Fitur Bawaan Tmux

Tmux menyertakan beberapa utilitas internal untuk pemantauan visual, manajemen interaktif, dan dokumentasi perintah tanpa perlu menginstal aplikasi tambahan.

## 1. Clock Mode (Visual)
Tmux memiliki fitur jam digital layar penuh yang berguna untuk memantau waktu saat bekerja dalam mode fokus.
- **Shortcut**: `Prefix + t`
- **Keluar**: Tekan tombol apapun.
- **Kustomisasi**:
  ```tmux
  set -g clock-mode-colour green
  set -g clock-mode-style 24
  ```

## 2. Interactive Chooser (Manajemen)
Fitur ini memberikan antarmuka visual untuk menavigasi struktur hirarkis Tmux.
- **Choose Tree**: `Prefix + s` (Sesi) atau `Prefix + w` (Window).
  - Memungkinkan pencarian (tekan `/`), navigasi dengan kursor, dan melihat preview konten pane sebelum berpindah.
- **Choose Client**: `Prefix + D`.
  - Digunakan untuk melihat daftar terminal yang terhubung ke server Tmux dan memutuskan koneksi (*detach*) terminal tertentu secara paksa.

## 3. Command Prompt (Interaktivitas)
Semua perintah Tmux dapat dijalankan langsung melalui command prompt internal tanpa keluar dari sesi.
- **Akses**: `Prefix + :`
- **Fungsi**: Mendukung auto-completion (tombol `Tab`) untuk perintah dan opsi. Contoh: Ketik `split-window -h` untuk membagi layar.

## 4. Customize Mode (Konfigurasi Visual)
Tersedia pada Tmux versi 3.1 ke atas, fitur ini menyediakan UI berbasis terminal untuk mengubah opsi konfigurasi secara real-time.
- **Akses**: Jalankan `tmux customize-mode` di terminal atau bind ke tombol tertentu.
- **Fungsi**: Memungkinkan penelusuran seluruh opsi server, sesi, dan window serta mengubah nilainya tanpa mengedit file `.tmux.conf` secara manual.

## 5. Dokumentasi Internal (List Keys)
Melihat daftar lengkap shortcut yang terdaftar di dalam sistem, termasuk binding default dan binding kustom Anda.
- **Shortcut**: `Prefix + ?`
- **Fungsi**: Berguna untuk memeriksa apakah terjadi konflik antara shortcut kustom dengan shortcut bawaan. Navigasi di dalamnya menggunakan mode scrollback (Gaya Vim atau Emacs).

## 6. Pane Indicators
Menampilkan nomor indeks pada setiap pane untuk memudahkan perpindahan fokus kursor.
- **Shortcut**: `Prefix + q`
- **Fungsi**: Angka akan muncul sebentar di setiap pane. Tekan angka yang sesuai untuk langsung berpindah fokus ke pane tersebut.
