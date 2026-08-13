# Flap City — Flappy Bird Classic

## Deskripsi Sistem

Flap City adalah game arcade 2D berbasis browser yang terinspirasi dari mekanik Flappy Bird. Pemain mengendalikan seekor burung yang bergerak secara horizontal melewati celah di antara pipa-pipa. Burung akan terus jatuh karena gravitasi, sehingga pemain harus memberikan dorongan ke atas secara berkala menggunakan tombol keyboard, klik mouse, atau sentuhan pada layar.

Game ini dibuat sebagai satu file HTML mandiri bernama `index.html`. Seluruh struktur halaman, gaya visual, logika permainan, animasi, audio, dan penyimpanan skor berada di dalam file tersebut. Sistem tidak menggunakan library JavaScript pihak ketiga, gambar eksternal, atau file audio eksternal.

## Teknologi yang Digunakan

| Teknologi | Fungsi |
| --- | --- |
| HTML5 Canvas | Merender langit, awan, bukit, pipa, burung, tanah, HUD, dan panel antarmuka. |
| CSS3 | Mengatur tampilan cabinet arcade, responsivitas, safe area mobile, warna, border, dan tekstur latar. |
| Vanilla JavaScript | Mengelola game loop, fisika, input, collision detection, skor, state, dan animasi. |
| `requestAnimationFrame` | Menjalankan animasi game secara halus mengikuti refresh rate browser. |
| Web Audio API | Menghasilkan suara flap, skor, dan tabrakan secara prosedural. |
| `localStorage` | Menyimpan dan membaca high score pemain di browser. |

## Arsitektur Sistem

Game menggunakan satu canvas dengan logical coordinate system berukuran **432 × 768**. Canvas kemudian diperbesar atau diperkecil menggunakan CSS dan device pixel ratio sehingga tampilan tetap tajam pada desktop maupun mobile.

State permainan dikelola menggunakan tiga mode utama:

| State | Penjelasan |
| --- | --- |
| `ready` | Layar awal ditampilkan. Burung melakukan animasi melayang dan pemain dapat memulai permainan. |
| `playing` | Fisika, pipa, skor, animasi, audio, dan collision detection aktif. |
| `over` | Permainan berhenti setelah tabrakan. Skor saat ini dan best score ditampilkan. |

Komponen logika utama berada di dalam fungsi-fungsi JavaScript berikut. Objek `bird` menyimpan posisi, kecepatan vertikal, rotasi, dan fase animasi sayap. Array `pipes` menyimpan posisi, ukuran, celah, serta status skor setiap pipa. Fungsi `update()` memperbarui fisika dan posisi semua objek, sedangkan fungsi `draw()` merender seluruh frame ke canvas.

## Fisika Burung

Burung memiliki gravitasi yang terus meningkatkan kecepatan jatuh sampai batas maksimum. Setiap flap mengatur kecepatan vertikal menjadi nilai negatif sehingga burung bergerak ke atas. Posisi burung diperbarui berdasarkan delta time, sehingga permainan tetap stabil ketika frame rate berubah.

Rotasi burung dihitung dari kecepatan vertikal. Saat burung bergerak ke atas, hidung burung sedikit mengarah ke atas. Saat burung jatuh, burung menunduk. Nilai rotasi dibatasi agar gerakannya tetap natural dan mudah dibaca.

## Pipa dan Collision Detection

Pipa dibuat secara prosedural dengan posisi horizontal yang terus bergerak ke kiri. Tinggi celah dibuat dalam rentang tertentu agar tantangan tetap bervariasi tetapi masih adil. Setelah pipa keluar dari layar, pipa tersebut dihapus dan pipa baru dibuat di sisi kanan.

Collision detection menggunakan metode **AABB atau Axis-Aligned Bounding Box**. Area hitbox burung dibuat sedikit lebih kecil daripada gambar burung agar kontrol terasa adil. Tabrakan diperiksa terhadap pipa atas, pipa bawah, batas atas layar, dan tanah.

Setiap kali burung melewati satu pasang pipa, skor bertambah satu poin dan suara skor diputar. Ketika terjadi tabrakan, state berubah menjadi `over`, suara hit diputar, dan high score diperbarui.

## Kontrol Pemain

| Input | Aksi |
| --- | --- |
| Spacebar | Flap atau memulai ulang permainan. |
| Arrow Up | Flap atau memulai ulang permainan. |
| Klik mouse | Flap atau menekan tombol permainan. |
| Sentuhan layar | Flap atau menekan tombol permainan pada perangkat mobile. |

Audio diaktifkan secara lazy setelah input pertama dari pengguna. Pendekatan ini digunakan karena browser modern biasanya memblokir pemutaran audio otomatis sebelum adanya interaksi pengguna.

## Antarmuka Pengguna

Layar awal menampilkan judul game, maskot burung, instruksi kontrol, tombol **START GAME**, dan best score. Saat permainan berlangsung, skor ditampilkan di bagian atas canvas. Setelah game over, panel hasil menampilkan skor saat ini, best score, dan tombol **PLAY AGAIN**.

## Penyimpanan High Score

High score disimpan dengan key `flap-city-best` di `localStorage`. Data tetap tersedia ketika halaman direfresh selama pengguna tidak menghapus data situs atau menggunakan mode browser yang tidak menyimpan storage.

## Responsivitas Mobile

Layout menggunakan `100dvh` agar tinggi game mengikuti viewport dinamis pada browser mobile. Safe area inset digunakan untuk menghindari notch, status bar, dan home indicator. Ukuran cabinet juga dihitung berdasarkan tinggi viewport sehingga seluruh canvas tetap terlihat pada layar yang pendek.

Canvas menggunakan `touch-action: none` agar gesture sentuh tidak menyebabkan halaman bergeser saat pemain melakukan flap. Ukuran dan border cabinet diperkecil pada layar sempit untuk memberikan ruang bermain yang lebih luas.

## Mode Demo

Tambahkan query parameter `?demo` pada URL untuk menjalankan autopilot deterministik:

```text
index.html?demo
```

Mode ini digunakan untuk verifikasi visual. Autopilot akan memberikan flap secara otomatis berdasarkan posisi celah pipa sehingga gameplay dapat diamati tanpa input manual.

## Cara Menjalankan

Karena seluruh game berada dalam satu file, cara paling sederhana adalah membuka `index.html` menggunakan browser modern seperti Chrome, Edge, Firefox, atau Safari.

Untuk menjalankan melalui server lokal, gunakan salah satu contoh berikut dari folder yang berisi file tersebut:

```bash
python3 -m http.server 8000
```

Kemudian buka alamat berikut pada browser:

```text
http://localhost:8000/index.html
```

## Struktur File Utama

| File | Fungsi |
| --- | --- |
| `index.html` | Versi standalone yang dapat dibuka langsung tanpa proses build. |
| `client/index.html` | Salinan entrypoint yang digunakan oleh preview WebDev. |
| `PLAN.md` | Rencana teknis dan kriteria verifikasi game. |
| `STRUCTURE.md` | Penjelasan struktur internal dan kepemilikan data. |
| `ASSETS.md` | Catatan arah visual dan referensi aset. |
| `MEMORY.md` | Catatan implementasi dan hasil pengujian. |

## Verifikasi

Game telah diverifikasi pada ukuran desktop dan mobile. Pengujian mencakup layar awal, gameplay demo, input pointer, pergerakan pipa, skor, game over, best score, serta responsivitas pada ukuran 390 × 844 dan 1280 × 720. Pemeriksaan TypeScript proyek juga berhasil dijalankan menggunakan `pnpm check`.

## Lisensi dan Ketergantungan

Game ini tidak memiliki dependency runtime pihak ketiga. Seluruh visual dirender menggunakan Canvas 2D, dan seluruh efek suara dibuat menggunakan Web Audio API. Dengan demikian, file `index.html` dapat dipindahkan atau dibagikan secara mandiri selama browser target mendukung HTML5 Canvas, Web Audio API, `localStorage`, dan `requestAnimationFrame`.
