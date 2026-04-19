# Modul 08: Integrasi Sistem dan Alur Kerja Modern

Modul ini membahas cara mengintegrasikan Tmux ke dalam ekosistem sistem operasi dan alat bantu pencarian fuzzy untuk mencapai produktivitas maksimal.

## 1. Otomatisasi Tmux dengan Systemd (Linux)
Agar server Tmux selalu berjalan sejak komputer diaktifkan (boot), kita dapat menggunakan unit service systemd user.

### Membuat Service File
Buat file di `~/.config/systemd/user/tmux.service`:
```ini
[Unit]
Description=Tmux Terminal Multiplexer (User Service)

[Service]
Type=forking
ExecStart=/usr/bin/tmux new-session -s main -d
ExecStop=/usr/bin/tmux kill-server
Restart=on-failure

[Install]
WantedBy=default.target
```

### Aktivasi
```bash
systemctl --user daemon-reload
systemctl --user enable --now tmux.service
```

## 2. Manajemen Sesi dengan FZF (Fuzzy Finder)
Alih-alih mengetik `tmux attach -t nama-sesi`, kita bisa menggunakan `fzf` untuk mencari dan berpindah sesi secara instan.

### Script Tmux-Sessionizer
Buat script shell sederhana untuk mencari direktori proyek dan membukanya sebagai sesi Tmux:
```bash
#!/bin/bash
# Cari folder di ~/projects, lalu pilih menggunakan fzf
selected=$(find ~/projects -mindepth 1 -maxdepth 1 -type d | fzf)

if [[ -z $selected ]]; then
    exit 0
fi

selected_name=$(basename "$selected" | tr . _)

# Jika tidak sedang di dalam Tmux, buat sesi baru dan attach
if [[ -z $TMUX ]]; then
    tmux new-session -s $selected_name -c $selected
else
    # Jika sudah di dalam Tmux, buat sesi (jika belum ada) lalu switch
    if ! tmux has-session -t=$selected_name 2> /dev/null; then
        tmux new-session -ds $selected_name -c $selected
    fi
    tmux switch-client -t $selected_name
fi
```

## 3. Integrasi Keybinding FZF ke Tmux
Tambahkan baris berikut di `~/.tmux.conf` agar pencarian sesi dapat dipicu langsung:
```tmux
# Prefix + f untuk mencari sesi/proyek
bind f run-shell "tmux neww ~/path/to/tmux-sessionizer"
```

## 4. Tips Workflow Profesional
- **Persistent Sessions**: Gunakan `tmux-continuum` bersama systemd agar sesi Anda pulih otomatis bahkan setelah listrik padam.
- **Project Isolation**: Setiap proyek besar harus memiliki sesinya sendiri. Jangan mencampur banyak proyek dalam satu sesi dengan banyak window, karena akan sulit dikelola.
- **Jump to Project**: Dengan `tmux-sessionizer`, Anda bisa berpindah antar konteks kerja (misal: dari Frontend ke Backend) dalam waktu kurang dari 2 detik.
