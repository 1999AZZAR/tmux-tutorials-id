# Modul 04: Sesi dan Persistensi

Session adalah fitur inti yang memungkinkan pemisahan antara terminal foreground dengan proses background.

## Pengelolaan Sesi dari Shell
Perintah eksternal untuk manajemen sesi:

- `tmux new -s <name>`: Inisialisasi sesi baru dengan identitas unik.
- `tmux ls`: Menampilkan daftar sesi aktif beserta jumlah window dan status attach.
- `tmux attach-session -t <name>`: Menghubungkan terminal aktif ke sesi yang sudah ada.
- `tmux detach-client`: Memutuskan koneksi terminal aktif dari sesi (alternatif: `Prefix + d`).
- `tmux kill-session -t <name>`: Terminasi sesi secara total (proses di dalamnya akan mati).
- `tmux rename-session -t <old> <new>`: Mengubah identitas sesi.

## Pengelolaan Sesi dari Dalam Tmux
- `Prefix + d`: Detach dari sesi saat ini.
- `Prefix + s`: Switcher sesi interaktif (mendukung preview window).
- `Prefix + $`: Mengubah nama sesi aktif.
- `Prefix + ( / )`: Pindah ke sesi sebelumnya/berikutnya dalam daftar server.

## Skenario Persistensi: Ssh dan Reboot
1. **SSH Disconnect**: Jika koneksi internet terputus saat SSH, sesi Tmux di server tidak akan mati. Cukup login kembali dan jalankan `tmux attach`.
2. **System Restart**: Secara default, sesi Tmux hilang saat server reboot. Gunakan plugin `tmux-resurrect` untuk menyimpan state ke disk.

## Praktik Terbaik
- Berikan nama sesi yang deskriptif (misal: `api-dev`, `db-prod`, `learning`).
- Jangan jalankan Tmux di dalam Tmux (nested session) secara tidak sengaja karena akan membingungkan Prefix Key.
