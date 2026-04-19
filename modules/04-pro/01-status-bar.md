# Modul 05: Kustomisasi Status Bar dan Visual

Status bar Tmux sangat fleksibel dan dapat dikonfigurasi untuk menampilkan informasi sistem secara real-time.

## Struktur Status Bar
Status bar terbagi menjadi tiga komponen utama:
1. `status-left`: Bagian kiri (biasanya untuk nama sesi).
2. `window-status`: Bagian tengah (daftar window aktif dan tidak aktif).
3. `status-right`: Bagian kanan (biasanya untuk jam, info CPU, baterai).

## Konfigurasi Global
Letakkan konfigurasi ini di `~/.tmux.conf`:
```tmux
# Posisi status bar (top atau bottom)
set -g status-position top

# Frekuensi update status bar (dalam detik)
set -g status-interval 5

# Penjajaran daftar window (left, centre, right)
set -g status-justify left
```

## Styling dan Warna
Tmux mendukung TrueColor dan Hex code:
```tmux
# Warna dasar status bar
set -g status-style "bg=#1e1e2e,fg=#cdd6f4"

# Warna window yang sedang aktif
set -g window-status-current-style "fg=#fab387,bold"

# Format tampilan window
set -g window-status-format " #I:#W "
set -g window-status-current-format " #[bg=#fab387,fg=#1e1e2e] #I:#W "
```

## Komponen Dinamis (Interpolasi)
Anda dapat menyisipkan variabel internal atau output shell script:
- `#S`: Nama Sesi.
- `#I`: Indeks Window.
- `#W`: Nama Window.
- `#H`: Hostname.
- `#(perintah)`: Output dari perintah shell.

Contoh `status-right` yang menampilkan penggunaan RAM dan jam:
```tmux
set -g status-right-length 100
set -g status-right "#[fg=#94e2d5] RAM: #(free -m | awk '/Mem:/ { print $3 }')MB | #[fg=#cdd6f4]%H:%M "
```

## Conditional Formatting
Menampilkan indikator khusus berdasarkan kondisi tertentu:
- `#{?client_prefix,#[bg=red] COMMAND ,#[bg=blue] NORMAL }`: Mengubah warna indikator saat Prefix ditekan.
- `#{?window_zoomed_flag, 🔍 ,}`: Menampilkan ikon kaca pembesar jika window sedang di-zoom.
