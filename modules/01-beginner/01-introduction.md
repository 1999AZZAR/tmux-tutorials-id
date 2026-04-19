# Modul 01: Pengenalan dan Arsitektur Tmux

## Definisi Teknis
Tmux adalah terminal multiplexer berbasis server-client yang memungkinkan persistensi proses pada lingkungan shell. Tmux beroperasi pada lapisan abstraksi di atas terminal emulator biasa, memungkinkan pemisahan sesi dari siklus hidup proses terminal itu sendiri.

## Arsitektur Hirarkis
Tmux menggunakan struktur data hirarkis untuk mengelola sumber daya:
1. **Server**: Entitas tunggal yang mengelola semua sesi. Tetap berjalan di background selama ada minimal satu sesi aktif.
2. **Session**: Lingkungan kerja terisolasi yang menampung satu atau lebih window. Sesi bersifat persisten.
3. **Window**: Analog dengan tab pada browser. Satu window dapat menampung beberapa pane.
4. **Pane**: Unit terkecil berupa terminal virtual mandiri hasil dari pembagian (split) window.

## Instalasi Sistem
Metode instalasi berdasarkan manajer paket distribusi:
- Debian/Ubuntu: `sudo apt-get install tmux`
- RHEL/CentOS: `sudo yum install tmux`
- Fedora: `sudo dnf install tmux`
- Arch Linux: `sudo pacman -S tmux`
- macOS: `brew install tmux`

## Inisialisasi
Menjalankan sesi default:
```bash
tmux
```

## Mekanisme Prefix Key
Tmux menggunakan urutan tombol pemicu sebelum menerima perintah internal. Secara default, pemicu ini adalah `Ctrl + b`. Tanpa menekan pemicu ini, perintah akan diteruskan langsung ke shell di dalam pane.
