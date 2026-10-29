# Timerin — Website Landing Page

Website landing page untuk memperkenalkan dan mendistribusikan aplikasi SaaS **Timerin**—aplikasi floating timer overlay untuk membantu pemain Mobile Legends: Bang Bang (MLBB) menghitung cooldown battle spell lawan (Flicker, Purify, Retribution, dll.) secara akurat, ringan, dan 100% legal (anti-ban).

Dibangun menggunakan **HTML5 semantik + Tailwind CSS**, mengikuti aturan sistem desain pada [`DESIGN.md`](./DESIGN.md) (gaya _Brutalist Type Foundry at Dusk_ dengan tipografi monumental raksasa, tata letak simetris rata tengah, pemisahan showcase gawai portrait & landscape, aksen Ember Orange `#ff6436`, dan kanvas Onyx `#141417`), serta konfigurasi keamanan siap deploy di **Vercel** (`vercel.json`).

---

## 📁 Struktur Direktori Proyek

```text
Timerin-Web/
├── assets/
│   ├── downloads/
│   │   └── Timerin_v1.0.1.apk    # File instalasi aplikasi Android Timerin (~53 MB)
│   └── images/
│       ├── timerin.png           # Icon & logo resmi aplikasi Timerin
│       ├── login.jpg             # Screenshot 1: Tampilan login aplikasi Timerin (Portrait)
│       ├── beranda.jpg           # Screenshot 2: Tampilan menu & pengaturan Timerin (Portrait)
│       ├── ml1.jpg               # Screenshot 3: In-game overlay Mobile Legends (Landscape)
│       └── ml2.jpg               # Screenshot 4: Cooldown tracking saat teamfight (Landscape)
├── .gitignore                    # Mengabaikan file sampah OS dan cache
├── DESIGN.md                     # Panduan sistem desain resmi (Brutalist Type Foundry at Dusk)
├── prd-guide-id.md               # Panduan penyusunan PRD
├── prd.md                        # Dokumen Kebutuhan Produk (PRD) Timerin lengkap
├── vercel.json                   # Konfigurasi keamanan HTTP Headers di Vercel
├── index.html                    # Halaman landing page utama
└── README.md                     # Petunjuk pengoperasian & deploy
```

---

## 🌟 Struktur Tata Letak (Rata Tengah / Centered)

1. **Hero Section (Rata Tengah):**
   - Monument Headline: `SMART SPELL COOLDOWN OVERLAY`.
   - Sub-headline deskriptif, tombol utama UNDUH APK (53 MB), dan baris badge legalitas anti-ban.
2. **Bagian 01: Antarmuka Aplikasi (Mode Portrait):**
   - Menampilkan 2 frame smartphone vertikal berdampingan secara simetris:
     - `1. MASUK & AKUN` (`login.jpg`)
     - `2. BERANDA APLIKASI` (`beranda.jpg`)
3. **Bagian 02: Pertandingan Real-Time (Mode Landscape):**
   - Menampilkan frame gaming display horisontal lebar di bawahnya:
     - `3. IN-GAME OVERLAY` (`ml1.jpg`)
     - `4. TRACKING TEAMFIGHT` (`ml2.jpg`)
     - Dilengkapi tombol tab switcher dan panah navigasi interaktif.
4. **Bagian 03: Fitur Unggulan & Spesifikasi Teknis:**
   - Grid 4 kolom rata tengah mencakup jaminan anti-ban, efisiensi RAM (<30MB), tanpa root, dan akurasi durasi spell patch terbaru.
5. **Bagian 04: Banner Unduhan Akhir & Panduan Pasang:**
   - Tombol CTA penutup dan dialog petunjuk instalasi APK Android.

---

## 📦 Berkas Unduhan APK

File APK aplikasi Timerin berada di:

```text
assets/downloads/Timerin_v1.0.1.apk
```

Tombol _"UNDUH APK"_ di navigasi atas dan banner utama langsung memicu pengunduhan file ini secara instan dan aman dengan header `Content-Disposition: attachment`.

---

## 🔒 Konfigurasi Keamanan (Vercel Security Headers)

File `vercel.json` menerapkan perlindungan tingkat industri:

- **Content-Security-Policy (CSP):** Membatasi eksekusi hanya dari sumber resmi (Tailwind CDN dan Google Fonts).
- **X-Frame-Options: `DENY`:** Menangkal serangan clickjacking.
- **X-Content-Type-Options: `nosniff`:** Mencegah MIME sniffing.
- **Strict-Transport-Security (HSTS):** Memaksa koneksi terenkripsi HTTPS (`max-age=63072000`).
- **Permissions-Policy:** Membatasi akses kamera, mikrofon, dan geolokasi yang tidak diperlukan.
