# Modul 04: Konfigurasi .tmux.conf dan Keybindings Dasar

Kustomisasi Tmux berpusat pada file `~/.tmux.conf`. File ini dieksekusi setiap kali server Tmux dimulai.

## 1. Remap Prefix Key
Prefix default `Ctrl + b` sering dianggap tidak ergonomis. Banyak pengguna mengubahnya ke `Ctrl + a`.

```tmux
# Mengubah prefix ke Ctrl + a
set -g prefix C-a
unbind C-b
bind C-a send-prefix
```

## 2. Pengaturan Opsi Dasar (Set Options)
Gunakan perintah `set` (untuk server/sesi) dan `setw` (untuk window) untuk mengubah perilaku default:

```tmux
# Aktifkan dukungan Mouse (klik pane, resize, scroll)
set -g mouse on

# Memulai indeks window dan pane dari 1 (default 0)
set -g base-index 1
setw -g pane-base-index 1

# Menambah limit history scrollback (default 2000)
set -g history-limit 10000

# Menghilangkan delay saat menekan tombol Esc (penting untuk pengguna Vim)
set -s escape-time 0
```

## 3. Kustomisasi Keybindings
Anda dapat membuat shortcut sendiri untuk mempercepat alur kerja:

```tmux
# Split pane menggunakan simbol yang lebih intuitif
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %

# Berpindah pane menggunakan Alt + Arrow tanpa Prefix
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Reload konfigurasi dengan cepat
bind r source-file ~/.tmux.conf \; display "Konfigurasi Berhasil Dimuat!"
```

## Penerapan Perubahan
Setiap kali `~/.tmux.conf` diubah, jalankan perintah berikut di terminal agar efeknya terasa:
`tmux source-file ~/.tmux.conf`
Atau gunakan shortcut `Prefix + r` jika sudah dikonfigurasi.
