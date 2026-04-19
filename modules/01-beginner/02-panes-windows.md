# Modul 02: Manajemen Pane dan Window

## Operasi Pane
Pane memungkinkan visualisasi beberapa output terminal secara simultan dalam satu window. Perintah berikut dieksekusi setelah `Prefix (Ctrl + b)`:

### Pembagian Layar (Splitting)
- `%`: Membagi window secara vertikal (kanan-kiri).
- `"`: Membagi window secara horizontal (atas-bawah).

### Navigasi dan Kontrol
- `o`: Berpindah fokus antar pane secara siklis.
- `;`: Berpindah ke pane yang terakhir diakses.
- `q`: Menampilkan nomor indeks pane (tekan nomor untuk pindah fokus).
- `x`: Mengirim sinyal terminasi ke pane aktif.
- `z`: Toggle zoom pada pane aktif untuk tampilan penuh.
- `Space`: Mengubah layout pane secara otomatis (preset: even-horizontal, even-vertical, dll).

### Penataan (Resizing)
Menyesuaikan dimensi pane secara manual:
- `Prefix + Alt + Arrow Keys`: Mengubah ukuran dalam inkremen 5 sel.
- `Prefix + Ctrl + Arrow Keys`: Mengubah ukuran dalam inkremen 1 sel.

## Operasi Window
Window bertindak sebagai tab yang mengelompokkan pane berdasarkan konteks tugas.

### Manajemen Tab
- `c`: Membuat window baru di direktori kerja saat ini.
- `,`: Memberikan label nama pada window untuk identifikasi cepat.
- `&`: Terminasi window beserta seluruh pane di dalamnya.

### Navigasi Tab
- `n`: Window berikutnya.
- `p`: Window sebelumnya.
- `0-9`: Akses langsung berdasarkan nomor indeks window.
- `w`: Daftar window interaktif dengan preview konten.
- `f`: Mencari window berdasarkan teks dalam output terminal.

## Latihan Teknis
1. Buat 4 pane dengan layout 2x2.
2. Gunakan `Prefix + z` pada salah satu pane, lalu jalankan `top`.
3. Keluar dari mode zoom dan pindah ke window baru.
4. Namakan window tersebut "monitoring".
