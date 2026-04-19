# Modul 06: Scripting dan Otomatisasi

Otomatisasi layout dan sesi untuk alur kerja yang konsisten.

## Shell Scripting
Contoh script untuk inisialisasi lingkungan kerja:
```bash
#!/bin/bash
tmux new-session -d -s "dev"
tmux rename-window -t "dev:0" "editor"
tmux split-window -h
tmux send-keys -t "dev:0.1" "htop" C-m
tmux attach -t "dev"
```

## Tmuxinator
Tmuxinator menggunakan file YAML untuk mendefinisikan layout.
Contoh `config.yml`:
```yaml
name: project
root: ~/src/project
windows:
  - editor:
      layout: main-vertical
      panes:
        - vim
        - tail -f logs/dev.log
```

## Integrasi Neovim
Gunakan plugin `christoomey/vim-tmux-navigator` untuk sinkronisasi navigasi antara Tmux dan Neovim menggunakan `Ctrl + hjkl`.
