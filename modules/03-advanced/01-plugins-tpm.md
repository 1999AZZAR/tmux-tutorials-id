# Modul 05: Plugin dan Ekosistem (TPM)

Tmux Plugin Manager (TPM) digunakan untuk mengelola ekstensi pihak ketiga.

## Instalasi TPM
```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

## Konfigurasi Plugin
Tambahkan ke dalam `~/.tmux.conf`:
```tmux
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'

run '~/.tmux/plugins/tpm/tpm'
```

## Manajemen Plugin
- `Prefix + I`: Menginstal plugin baru.
- `Prefix + U`: Memperbarui plugin.
- `Prefix + alt + u`: Menghapus plugin yang tidak terdaftar.

## Plugin Direkomendasikan
- tmux-resurrect: Menyimpan dan memulihkan sesi setelah restart.
- tmux-yank: Integrasi clipboard sistem.
