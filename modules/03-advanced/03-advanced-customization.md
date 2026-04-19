# Modul 07: Konfigurasi Lanjut dan Otomatisasi Internal

Pada tingkat ini, Tmux tidak hanya digunakan sebagai pembagi layar, tetapi sebagai lingkungan kerja cerdas yang bereaksi terhadap aktivitas pengguna.

## 1. Terminal Overrides (Visual Fidelity)
Memastikan dukungan warna 24-bit (TrueColor) dan fitur teks modern seperti italic atau undercurl (wavy underlines) untuk Neovim.

```tmux
# Set terminal default
set -g default-terminal "tmux-256color"

# Aktifkan TrueColor (RGB)
set -as terminal-overrides ",xterm-256color:RGB"

# Dukungan Undercurl (garis bawah bergelombang untuk error/LSP)
set -as terminal-overrides ',*:Smulx=\E[4::%p1%dm'
set -as terminal-overrides ',*:Setulc=\E[58::2::%p1%{65536}%/%d::%p1%{256}%/%{255}%&%d::%p1%{255}%&%d%;m'
```

## 2. Tmux Hooks (Otomatisasi Event)
Hooks memungkinkan eksekusi perintah secara otomatis saat terjadi event tertentu di dalam Tmux server.

```tmux
# Menyeimbangkan ukuran pane secara otomatis saat ada pane yang ditutup
set-hook -g window-pane-changed 'select-layout -E'

# Notifikasi saat sebuah sesi baru dibuat
set-hook -g session-created 'display-message "Sesi Baru: #S dimulai"'

# Menjalankan script tertentu saat window diubah ukurannya
set-hook -g window-resized 'run-shell "~/scripts/handle_resize.sh"'
```

## 3. Custom Interactive Menus
Tmux 3.0+ mendukung pembuatan menu interaktif pop-up yang dapat dikontrol menggunakan keyboard atau mouse.

```tmux
# Menu aksi cepat pada Prefix + m
bind m display-menu -T "#[fg=blue] Menu Aksi Cepat " -x C -y C \
    "Split Vertikal"   v "split-window -h -c '#{pane_current_path}'" \
    "Split Horizontal" h "split-window -v -c '#{pane_current_path}'" \
    "" \
    "Layout Tiled"     t "select-layout tiled" \
    "Layout Even-V"    V "select-layout even-vertical" \
    "" \
    "Tutup Pane"       x "kill-pane" \
    "Tutup Menu"       q ""
```

## 4. Floating Windows (Pop-ups)
Gunakan `display-popup` untuk membuka terminal temporer tanpa mengganggu layout utama (sangat berguna untuk kalkulator, git client, atau file manager).

```tmux
# Membuka terminal popup di tengah layar pada Prefix + g
bind g display-popup -d "#{pane_current_path}" -w 80% -h 80% -E "lazygit"
```

## 5. Sinkronisasi Clipboard (OSC 52)
Memungkinkan penyalinan teks ke clipboard sistem bahkan saat bekerja di server remote via SSH tanpa perlu setup xclip/pbcopy di sisi server.
```tmux
set -s set-clipboard on
```
