# Modul 04: Konfigurasi .tmux.conf

Kustomisasi Tmux dilakukan melalui file `~/.tmux.conf`.

## Implementasi Dasar
Buat file konfigurasi:
```bash
touch ~/.tmux.conf
```

## Contoh Konfigurasi
```tmux
# Mengubah prefix ke Ctrl+a
set -g prefix C-a
unbind C-b
bind C-a send-prefix

# Mengaktifkan dukungan mouse
set -g mouse on

# Shortcut reload konfigurasi
bind r source-file ~/.tmux.conf \; display "Config Reloaded"
```

## Penerapan
Muat ulang konfigurasi dari terminal:
`tmux source-file ~/.tmux.conf`
Atau gunakan `Prefix + r` jika sudah dikonfigurasi.
