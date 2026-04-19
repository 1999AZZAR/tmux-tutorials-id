# Modul 03: Copy Mode dan Navigasi Buffer

Copy mode memungkinkan user untuk melakukan scrollback pada output terminal yang sudah lewat, melakukan pencarian teks, dan menyalin data ke buffer.

## Aktivasi dan Dasar Vi-Mode
Untuk menggunakan navigasi gaya Vim, tambahkan konfigurasi berikut pada `~/.tmux.conf`:
```tmux
set-window-option -g mode-keys vi
```

Masuk ke Copy Mode: `Prefix + [`

### Navigasi (Gaya Vim)
- `h`, `j`, `k`, `l`: Pindah kursor ke kiri, bawah, atas, kanan.
- `w`, `b`: Pindah per kata (forward/backward).
- `g`: Lompat ke baris paling atas buffer.
- `G`: Lompat ke baris paling bawah buffer.
- `Ctrl + u`: Scroll ke atas (setengah layar).
- `Ctrl + d`: Scroll ke bawah (setengah layar).

### Pencarian
- `/`: Mencari teks ke arah bawah (forward search).
- `?`: Mencari teks ke arah atas (backward search).
- `n`: Hasil pencarian berikutnya.
- `N`: Hasil pencarian sebelumnya.

## Prosedur Copy-Paste
1. Masuk ke Copy Mode: `Prefix + [`
2. Mulai seleksi: `Space` (default) atau `v` (jika sudah di-bind).
3. Salin seleksi ke buffer: `Enter` (default) atau `y` (jika sudah di-bind).
4. Paste dari buffer: `Prefix + ]`

## Integrasi Clipboard Sistem (Linux/macOS)
Tmux secara default menyimpan data pada buffer internal. Untuk menyalin langsung ke clipboard sistem (agar bisa dipaste ke aplikasi lain):

### macOS
```tmux
bind-key -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "pbcopy"
```

### Linux (X11)
```tmux
bind-key -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "xclip -in -selection clipboard"
```

## Buffer List
Tmux menyimpan riwayat salinan dalam stack buffer:
- `Prefix + #`: Menampilkan daftar buffer yang tersimpan.
- `Prefix + =`: Memilih buffer dari daftar secara interaktif untuk di-paste.
