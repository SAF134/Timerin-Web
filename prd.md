# Dokumen Kebutuhan Produk: Timerin (Landing Page & Distribusi APK)

## Gambaran Umum Produk

**Visi Produk:** Menghadirkan landing page satu section yang estetik, ringan, dan aman untuk memperkenalkan serta mendistribusikan aplikasi SaaS _Timerin_—aplikasi floating timer overlay yang membantu pemain Mobile Legends: Bang Bang (MLBB) melacak cooldown battle spell musuh secara presisi dan legal (anti-ban).

**Target Pengguna:**

- Pemain kompetitif Mobile Legends (Rank Mythic ke atas, pemain turnamen grassroot, roamer/shotcaller) yang membutuhkan kalkulasi cooldown spell musuh secara real-time.
- Pemain kasual yang ingin meningkatkan _game sense_ dan efektivitas serangan _ganking_ saat spell utama musuh sedang cooldown.

**Tujuan Bisnis:**

- Meningkatkan konversi unduhan APK aplikasi Timerin melalui halaman arahan tunggal (_single section landing page_) yang ringkas, meyakinkan, dan berkecepatan tinggi.
- Membangun reputasi aplikasi sebagai utilitas overlay legal, aman tanpa modifikasi game, dan tanpa risiko banned.

**Metrik Keberhasilan:**

- Rasio Konversi Unduhan (Download Conversion Rate) > 25% dari total kunjungan unik.
- Waktu Muat Halaman (Page Load Time) di bawah 1.0 detik di jaringan mobile 4G.
- Skor Google Lighthouse: Performance > 95, Accessibility > 95, Best Practices > 95, SEO > 95.

---

## Persona Pengguna

### Persona 1: Reza "The Shotcaller" (Pemain Kompetitif / Roamer)

- **Demografi:** Usia 21 tahun, Mahasiswa, sangat fasih teknologi smartphone Android, pemain MLBB tier Mythical Glory/Immortal.
- **Tujuan:** Mengetahui detik pasti kapan battle spell lawan (Flicker, Purify, Retribution) kembali aktif untuk memimpin inisiasi _team fight_.
- **Kendala/Masalah:** Menghitung waktu cooldown spell (misal Flicker 120 detik) secara manual di kepala sangat membebani fokus saat team fight yang intens.
- **Perjalanan Pengguna:** Membuka web dari browser HP atau link discord, melihat screenshot tampilan overlay di dalam game, membaca jaminan anti-ban, menekan tombol UNDUH APK, lalu menginstal dan langsung menggunakannya.

### Persona 2: Fajar "The Solo Ranker" (Pemain Kasual / Jungler)

- **Demografi:** Usia 18 tahun, Siswa SMA, pengguna smartphone mid-range, sering bermain solo rank di waktu luang.
- **Tujuan:** Memenangkan kontes objektif Turtle dan Lord dengan mengetahui status battle spell Retribution lawan.
- **Kendala/Masalah:** Ragu mengunduh aplikasi pendukung game karena takut akun terkena penalti/banned atau ponsel menjadi lemot.
- **Perjalanan Pengguna:** Mengunjungi landing page Timerin, melihat preview antarmuka aplikasi melalui 4 screenshot interaktif, melihat ukuran file yang ringan, lalu mengunduh installer APK secara instan.

---

## Kebutuhan Fitur

| Fitur                                         | Deskripsi                                                                                             | User Story                                                                                         | Prioritas | Kriteria Penerimaan                                                                                                                      | Dependensi                         |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| **Header Floating Navigation**                | Navigasi model _frosted pill_ melayang di bagian atas layar sesuai `DESIGN.md`.                       | Sebagai pengguna, saya ingin navigasi yang ringkas agar tampilan tetap bersih dan fokus.           | Must      | Menggunakan radius pill (50px), backdrop-blur, border halus `#dee2de`, memuat logo Timerin dan status versi v1.0.                        | Tailwind CSS, Lucide/Inline Icons  |
| **Hero & Value Proposition (Single Section)** | Bagian utama yang menyampaikan nilai jual Timerin dalam satu layar pandang.                           | Sebagai pengunjung, saya ingin langsung memahami fungsi Timerin tanpa harus banyak scroll.         | Must      | Menampilkan headline tegas dengan font display serif (`Fraunces`), subheadline deskriptif, dan chip fitur unggulan.                      | Typography & Theme Token           |
| **Showcase 4 Gambar Aplikasi**                | Komponen interaktif untuk menampilkan 4 screenshot fitur Timerin.                                     | Sebagai calon pengguna, saya ingin melihat rupa antarmuka overlay aplikasi sebelum mengunduhnya.   | Must      | Menampilkan 4 screenshot aplikasi dengan tombol navigasi/thumbnail switcher yang halus, responsif di mobile & desktop.                   | File gambar di `assets/images/`    |
| **Direct APK Download CTA**                   | Tombol unduh berbingkai (_outlined CTA_) yang langsung mengunduh file APK lokal.                      | Sebagai pengguna, saya ingin langsung mengunduh file `.apk` dengan sekali klik.                    | Must      | Tombol berbingkai `#41a1cf`, transparan, border-radius 8px, mengarah ke `assets/downloads/Timerin_v1.0.1.apk` dengan atribut `download`. | File `.apk` di `assets/downloads/` |
| **Trust Badges (Anti-Ban & Keamanan)**        | Indikator kepercayaan bahwa Timerin 100% aman (overlay murni, tanpa root, tanpa modifikasi APK game). | Sebagai pemain MLBB, saya ingin memastikan akun game saya tidak akan terbanned.                    | Should    | Memuat 3 poin kepercayaan: _Overlay Murni (No-Injection)_, _Tanpa Akses Root_, _Ringan & Ramah Baterai_.                                 | SVG Icons & Typography             |
| **Vercel Security Headers**                   | Konfigurasi perlindungan keamanan web di tingkat server hosting Vercel.                               | Sebagai pemilik website, saya ingin landing page terlindungi dari clickjacking, XSS, dan sniffing. | Must      | File `vercel.json` menerapkan CSP, HSTS, X-Frame-Options DENY, X-Content-Type-Options nosniff, Referrer-Policy.                          | Platform Vercel                    |

---

## Alur Pengguna (User Flows)

### Alur 1: Mengunduh Installer APK Timerin

1. Pengguna membuka URL website Timerin.
2. Pengguna membaca headline, deskripsi, dan memeriksa badge keamanan anti-ban.
3. Pengguna mengklik tombol _"Download Timerin (v1.0 APK)"_.
4. Browser memicu dialog penyimpanan file `Timerin_v1.0.1.apk` secara instan.

- **Jalur alternatif:** Pengguna ingin melihat detail tampilan aplikasi terlebih dahulu sebelum mengklik tombol unduh.
- **Kondisi error:** Jika file APK belum terunggah/hilang di server, muncul peringatan unduhan belum tersedia secara elegan.

### Alur 2: Menjelajahi 4 Screenshot Fitur Aplikasi

1. Pengguna melihat preview screenshot utama di frame mockup smartphone/tablet.
2. Pengguna mengklik thumbnail atau tombol indikator 1, 2, 3, atau 4.
3. Tampilan preview berpindah secara halus menampilkan screenshot yang dipilih (misal: _Tampilan In-Game Overlay_, _Pilihan Spell Cooldown_, _Pengaturan Transparansi_, _Notifikasi Suara/Getar_).

---

## Kebutuhan Non-Fungsional

### Performa

- **Waktu Muat (Load Time):** Target waktu muat penuh < 1.0 detik.
- **Ukuran Aset:** Gambar dioptimalkan (format modern WebP/PNG terkompresi).
- **Pengguna Bersamaan:** Mampu menangani ribuan permintaan secara serverless via Vercel Edge Network.

### Keamanan

- **Proteksi HTTP Headers:** Diterapkan via `vercel.json` mencakup:
  - `Content-Security-Policy`: membatasi sumber script, style, dan font hanya dari domain resmi (`cdn.tailwindcss.com`, `fonts.googleapis.com`, `fonts.gstatic.com`).
  - `X-Frame-Options: DENY`: mencegah serangan clickjacking.
  - `X-Content-Type-Options: nosniff`: mencegah MIME-type sniffing.
  - `Strict-Transport-Security`: memaksa HTTPS dengan HSTS.
  - `Referrer-Policy: strict-origin-when-cross-origin`.
- **Integritas Unduhan:** File `.apk` dilayani secara statis melalui saluran HTTPS aman.

### Kompatibilitas

- **Perangkat:** Smartphone Android (layar portrait), Tablet, dan Desktop (layar landscape 1080p ke atas).
- **Browser:** Google Chrome Mobile & Desktop, Safari iOS, Mozilla Firefox, Samsung Internet.
- **Ukuran Layar:** Responsif sempurna mulai dari 360px hingga 1920px+.

### Aksesibilitas

- **Tingkat Kepatuhan:** WCAG 2.1 Level AA.
- **Persyaratan Khusus:** Kontras warna teks memenuhi standar (minimal rasio 4.5:1 untuk teks normal), navigasi keyboard untuk galeri screenshot, serta tag `alt` deskriptif pada semua gambar.

---

## Spesifikasi Teknis

### Frontend

- **Stack Teknologi:** HTML5 Semantik, Tailwind CSS (CDN dengan token desain kustom sesuai `DESIGN.md`), JavaScript murni (Vanilla JS) tanpa dependensi eksternal berat.
- **Sistem Desain (Dylanbrouwer Brutalist Type Foundry at Dusk):**
  - Canvas & Hero: `#161616` (Onyx) dengan radial vignette atmosferik.
  - Teks: `#ffffff` (Pure White), `#f1f1f1` (Fog), `#c9c7cc` (Silver Mist), `#a2a2a2` (Ash), `#7b7a7c` (Stone).
  - Aksen Tunggal: `#ff6436` (Ember Orange) untuk status live, dot aktif, dan tombol aksi unduh.
  - Tipografi: Monument Condensed Display `Bebas Neue` / `Anton` (substitut `ABC Gravity Variable`), Grotesk `Inter` (substitut `Die Grotesk B`), dan Technical Monospace `IBM Plex Mono`.
  - Komponen Utama: Monument Headline raksasa dengan gradien teks vertikal, Frame Smartphone adaptif (Landscape untuk in-game MLBB `ml1.jpg` & `ml2.jpg`, Portrait untuk menu `beranda.jpg` & `login.jpg`), serta sticky top navbar dengan brand icon `timerin.png`.

### Backend & Penyimpanan

- **Model:** Serverless Static Hosting.
- **Penyimpanan Berkas:** Direktori lokal `/assets/downloads/` untuk file instalasi APK dan `/assets/images/` untuk aset grafis.

### Infrastruktur

- **Hosting:** Vercel (Edge Network global).
- **Konfigurasi Keamanan:** `vercel.json` di root direktori.
- **CI/CD:** Git push otomatis terintegrasi dengan pipeline Vercel.

---

## Analitik & Pemantauan

- **Metrik Utama:** Total unduhan APK, jumlah impresi halaman, rasio klik screenshot.
- **Event:** `click_download_btn`, `switch_screenshot_slide`.
- **Dashboard:** Vercel Web Analytics & Speed Insights.
- **Notifikasi/Alert:** Notifikasi bawaan Vercel untuk kegagalan build atau anomali traffic.

---

## Perencanaan Rilis

### MVP (v1.0)

- Rilis single section landing page Timerin.
- Galeri 4 screenshot interaktif dengan switcher thumbnail/dots.
- Tombol direct download `assets/downloads/Timerin_v1.0.1.apk`.
- Implementasi sistem desain `DESIGN.md` dan `vercel.json` security headers.

### Rilis Mendatang

- **v1.1:** Tambahan modal FAQ interaktif mengenai cara instalasi APK di Android (mengizinkan instalasi sumber tidak dikenal).
- **v1.2:** Fitur multi-bahasa (Bahasa Indonesia & English) untuk audiens global MLBB (Filipina, Malaysia, dsb.).
- **v2.0:** Integrasi tombol unduh Google Play Store saat aplikasi resmi dirilis di toko aplikasi.

---

## Pertanyaan Terbuka & Asumsi

- **Asumsi 1:** Pengguna Android telah memahami cara menginstal file `.apk` secara manual atau website memberikan teks panduan singkat.
- **Asumsi 2:** Keempat gambar yang disiapkan pengguna memiliki rasio aspek seragam (misal portrait 9:16 untuk tampilan layar smartphone).
- **Asumsi 3:** Ukuran file APK berkisar antara 5 MB hingga 25 MB sehingga aman untuk di-host langsung di Vercel (batas limit file statis Vercel gratis adalah 100MB per file).

---

## Lampiran

### Analisis Kompetitor

- **Penghitung Waktu Manual / Stopwatch:** Membutuhkan perangkat kedua atau mengganggu layar game secara fisik. Timerin unggul karena mengapung (_TIMER OVERLAY_) transparan langsung di atas Mobile Legends.
- **Cheat / Script Injector:** Berisiko tinggi banned permanen dari Moonton. Timerin unggul mutlak karena **100% legal** dan beroperasi murni sebagai timer visual independen tanpa membaca memori game.

### Wawasan Percakapan AI

- **Wawasan Desain:** Sistem desain yang diminta mengadopsi nuansa editorial hangat (_literary warm canvas_) dengan batasan ketat: tidak menggunakan warna hitam pekat `#000000`, tidak ada tombol chromatic filled, melainkan outlined CTA dengan aksen `#41a1cf`.
- **Kasus Khusus (Edge Cases):** Pada layar mobile kecil (lebar < 380px), tata letak single section harus tetap muat dan nyaman tanpa mengharuskan pengguna melakukan scroll berulang kali untuk mencapai tombol unduh.

### Glosarium

- **Battle Spell:** Kemampuan tambahan hero di Mobile Legends dengan waktu tunggu tertentu (cth: Flicker 120s, Purify 90s, Retribution 35s).
- **TIMER OVERLAY:** Jendela mini mengambang di atas aplikasi lain yang difasilitasi oleh izin sistem Android (_Draw over other apps_).
- **CSP (Content Security Policy):** Kebijakan keamanan web untuk membatasi eksekusi sumber daya berbahaya.
