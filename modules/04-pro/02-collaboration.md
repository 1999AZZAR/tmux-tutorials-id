# Modul 06: Kolaborasi dan Pair Programming

Tmux dapat digunakan sebagai media kolaborasi jarak jauh yang ringan, memungkinkan beberapa pengguna melihat dan mengontrol terminal yang sama secara simultan.

## Mekanisme Multi-User via SSH
Prosedur dasar kolaborasi pada satu server yang sama:

1. **User A (Host)**: Inisialisasi sesi Tmux.
   `tmux new -s pair-prog`
2. **User B (Guest)**: Login ke server yang sama via SSH dengan akun yang sama (atau akun berbeda dengan izin grup yang tepat), lalu jalankan:
   `tmux attach -t pair-prog`

Kedua user sekarang melihat terminal yang sama. Apa yang diketik User A akan terlihat oleh User B.

## Penggunaan Akun Berbeda (Shared Socket)
Jika kolaborasi melibatkan user akun berbeda di Linux, gunakan socket yang dishare:

1. **Host**: Jalankan tmux dengan mendefinisikan path socket.
   `tmux -S /tmp/shared-socket`
2. **Izin**: Berikan akses tulis/baca pada socket tersebut.
   `chmod 777 /tmp/shared-socket`
3. **Guest**: Hubungkan ke socket tersebut.
   `tmux -S /tmp/shared-socket attach`

## Tmate: Solusi Instan
**Tmate** adalah fork dari Tmux yang dikhususkan untuk kolaborasi instan tanpa perlu mengatur SSH server atau firewall:

- Instalasi: `sudo apt install tmate`
- Jalankan: `tmate`
- Tmate akan memberikan URL SSH atau Web yang bisa diberikan kepada rekan kerja. Mereka cukup menjalankan perintah tersebut untuk bergabung dalam sesi Anda.

## Sinkronisasi Pane (Input Terpusat)
Fitur ini berguna jika Anda ingin menjalankan perintah yang sama di banyak pane secara bersamaan (misal: update 4 server sekaligus):
`Prefix + :` lalu ketik `setw synchronize-panes`

Untuk mematikan:
`Prefix + :` lalu ketik `setw synchronize-panes off`
