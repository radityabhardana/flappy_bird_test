Flappy City

Sebuah game Flappy Bird klasik yang dibuat sepenuhnya dari nol menggunakan HTML5 Canvas dan JavaScript vanilla. Tidak ada library eksternal, tidak ada framework, cukup satu file HTML yang bisa langsung dijalankan di browser manapun.

---

Demo live bisa diakses di sini:
[link vercel akan ditambahkan]

Screenshot atau preview game akan ditambahkan di sini.

---

Tentang Proyek Ini

Game ini terinspirasi dari Flappy Bird asli, tapi dengan sentuhan visual yang lebih fresh. Temanya adalah "Sunlit Handheld Arcade" — nuansa arcade jadul tahun 80-an tapi dengan spacing dan kontras yang lebih modern. Langit berwarna aqua pucat, burungnya kuning keemasan, pipanya hijau, dan semuanya dibalut outline navy tebal yang bikin kesan seperti game di layar handheld.

Semua aset digambar secara prosedural langsung di canvas — tidak ada file gambar, tidak ada font eksternal, tidak ada file audio terpisah. Efek suara dibuat menggunakan Web Audio API dengan oscilator sederhana.

---

Cara Main

Tekan spasi, klik layar, atau tap (di HP) untuk membuat burung melompat. Hindari pipa yang datang dari kanan. Setiap pipa yang berhasil dilewati menambah satu poin. Skor tertinggi tersimpan otomatis di browser.

Untuk desktop, bisa pakai tombol Space atau Arrow Up. Di HP, cukup tap di mana saja.

---

Fitur

Seluruh game berjalan dalam satu file index.html tanpa dependensi eksternal. Fisika burung menggunakan delta-time agar tetap konsisten di berbagai kecepatan frame. Ada parallax layering — awan bergerak lebih lambat dari pipa, dan tanah bergerak paling cepat. Skor tersimpan di localStorage. Efek suara ada tiga jenis: saat flap, saat lewat pipa, dan saat mati. Game juga bisa dijalankan dalam mode demo otomatis dengan menambahkan ?demo di URL, berguna untuk verifikasi visual.

Tampilan responsif untuk desktop maupun mobile menggunakan viewport height sebagai acuan ukuran canvas.

---

Teknologi

Proyek ini menggunakan HTML5 Canvas 2D untuk rendering, requestAnimationFrame untuk game loop, Web Audio API untuk efek suara, dan localStorage untuk menyimpan skor. Tidak ada library JavaScript tambahan.

Untuk keperluan hosting dan development server, proyek menggunakan Vite — tapi itu hanya sebagai host. Game aslinya berdiri sendiri dan tidak membutuhkan build step sama sekali.

---

Menjalankan Secara Lokal

Pastikan sudah ada Node.js dan pnpm. Lalu jalankan:

    pnpm install
    pnpm dev

Atau cukup buka file index.html langsung di browser — tidak perlu server sama sekali.

---

Struktur

File utama game ada di index.html di root folder. Di dalamnya terdapat semua logic game, rendering, input handling, dan audio dalam satu dokumen. Folder client, server, dan shared adalah bagian dari scaffold yang dipakai sebagai host preview saja.

---

Lisensi

MIT — bebas dipakai, dimodifikasi, dan didistribusikan.