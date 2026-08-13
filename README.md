# Flap City · Flappy Bird Retro Arcade

**Flap City** adalah game arcade retro ala Flappy Bird yang responsif, visual retro menarik, dan suara audio prosedural. Projek ini dibangun menggunakan HTML5 Canvas, React, TypeScript, dan Vite.

---

## 🚀 Fitur Utama

- **Grafik Prosedural Pixel-Art & Retro**: Semua elemen visual (burung, pipa, latar belakang, awan, dan kabinet) digambar secara langsung menggunakan HTML5 Canvas.
- **Audio Prosedural (Web Audio API)**: Efek suara loncatan, perolehan skor, dan benturan dihasilkan secara dinamis tanpa memerlukan aset audio eksternal.
- **Desain Kabinet Arcade**: Pengalaman bermain layaknya menggunakan mesin game arcade genggam (*Sunlit Handheld Arcade*).
- **Kontrol Multi-platform**:
  - **Keyboard**: Tombol `Spasi` atau `Panah Atas`.
  - **Layar Sentuh (Mobile)**: Ketuk layar untuk melompat.
  - **Mouse (Desktop)**: Klik pada area game.
- **Penyimpanan Rekor (High Score)**: Skor tertinggi disimpan secara otomatis di `localStorage` browser.
- **Mode Demo**: Mendukung mode otomatis (*autopilot*) melalui parameter URL `?demo=true`.

---

## 🛠️ Teknologi yang Digunakan

- **Frontend Framework**: [React 19](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)
- **Bundler & Dev Server**: [Vite](https://vitejs.dev/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Canvas Rendering & Audio**: HTML5 2D Canvas Context & Web Audio API
- **Package Manager**: `pnpm`

---

## 📁 Struktur Direktori

```text
flappy_bird/
├── client/
│   ├── src/                # Kode sumber aplikasi React
│   └── index.html          # HTML entry point utama game
├── attached_assets/        # Aset referensi game
├── vite.config.ts          # Konfigurasi Vite & dev server
├── package.json            # Daftar dependensi & script proyek
├── .gitignore              # Daftar file/folder yang diabaikan Git
└── README.md               # Dokumentasi proyek (Bahasa Indonesia)
```

---

## 💻 Cara Menjalankan Proyek

### 1. Prasyarat
Pastikan Anda telah menginstal Node.js (versi 18+) dan `pnpm` (atau `npm`/`yarn`).

### 2. Instalasi Dependensi
Jalankan perintah berikut pada terminal:
```bash
pnpm install
```

### 3. Menjalankan Dev Server
Untuk memulai server pengembangan lokal:
```bash
pnpm dev
```
Buka browser dan akses alamat `http://localhost:3000`.

### 4. Build Produksi
Untuk mengompilasi proyek menjadi bundle produksi:
```bash
pnpm build
```

---

## 📝 Lisensi

MIT License © 2026
