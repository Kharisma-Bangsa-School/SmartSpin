# PutarPintar (Smart Spin)

Video analyzer praktikum gaya sentripetal berbasis AI tracker — upload video eksperimen gerak melingkar, dan aplikasi ini akan melacak objek yang berputar serta menghitung periode rotasinya secara otomatis.

**Berjalan 100% di browser.** Video tidak pernah diunggah ke server mana pun — semua pemrosesan terjadi secara lokal di perangkat Anda.

## Fitur utama

- **🔄 Smart Tracking (mode utama, direkomendasikan)** — melacak posisi objek di setiap frame video secara langsung (bukan berasumsi lintasannya lingkaran sempurna), lalu menyesuaikan (fit) bentuk lingkaran dari lintasan yang benar-benar teramati setelahnya. Tahan terhadap:
  - Tangan/kamera yang goyang (pusat putaran tidak sempurna diam)
  - Klik awal pengguna yang kurang presisi saat menandai pusat/objek
  - Kecepatan putaran yang berubah-ubah (mempercepat atau memperlambat selama video)
- **🎯 Point Crossing (mode alternatif)** — deteksi klasik berbasis "objek melintasi satu titik acuan", cocok sebagai cadangan atau untuk kasus tertentu
- **Analisis per-putaran** — periode dihitung untuk setiap putaran individual (bukan cuma dirata-rata dari awal sampai akhir), sehingga perubahan kecepatan dapat terlihat jelas lewat grafik, bukan tersembunyi di balik satu angka rata-rata
- **Indikator kualitas otomatis** — skor R² (kesesuaian model) dan "path quality" (seberapa mendekati lingkaran sempurna lintasan yang terlacak), supaya pengguna tahu seberapa bisa diandalkan hasilnya
- **Kalkulator bawaan** — masukkan radius (r) dan massa benda (m), langsung dapat kecepatan linear (v) dan gaya sentripetal (Fs) tanpa hitung manual
- **Ekspor cepat** — tombol "Copy row for worksheet" menyalin hasil (n, t, T, v, Fs) siap tempel ke tabel data

## Cara pakai

1. Buka aplikasi (lihat opsi di bawah)
2. Upload video eksperimen gerak melingkar
3. Pilih mode **Smart tracking** (default), lalu seret dari titik pusat putaran ke posisi objek yang berputar
4. Klik **Run Auto-detect** — aplikasi akan memutar videonya sekali dan melacak objeknya secara otomatis
5. Lihat hasil: periode rata-rata (T), grafik rotasi kumulatif, dan grafik periode-per-putaran
6. (Opsional) Isi radius dan massa benda di bagian kalkulator untuk mendapatkan v dan Fs otomatis
7. Salin hasilnya dengan tombol **Copy row for worksheet**, atau koreksi manual lewat log jika ada yang meleset

## Cara mengakses

### Opsi 1 — Offline (buka langsung)
Unduh `index.html`, lalu buka file tersebut langsung di browser mana pun (Chrome, Edge, atau Safari direkomendasikan). Tidak perlu instalasi atau server.

### Opsi 2 — Online lewat GitHub Pages
Jika repo ini sudah di-upload ke GitHub milik Anda sendiri:

1. Masuk ke halaman repo di GitHub, klik **Settings → Pages**
2. Di bagian **Source**, pilih branch `main` dan folder `/ (root)`, lalu **Save**
3. Tunggu beberapa menit — situs akan aktif di `https://<username-anda>.github.io/<nama-repo>/`
4. Bagikan link tersebut ke siswa; mereka tinggal buka lewat browser HP/laptop tanpa perlu download apa pun

## Batasan yang perlu diketahui

- **Kecepatan putar sangat ekstrem** (setara >300–400 RPM) pada video 30fps biasa bisa melebihi kemampuan mode Smart Tracking untuk mengikuti pergerakan antar-frame. Untuk kasus ini:
  - Coba mode **Point Crossing** sebagai alternatif, atau
  - Rekam ulang dengan mode **slow-motion** (120/240fps) jika kamera mendukung — ini akan sangat membantu di kedua mode
- Browser perlu mendukung `requestVideoFrameCallback` untuk hasil paling akurat (Chrome, Edge, dan Safari terbaru sudah mendukung; Firefox punya fallback tapi sedikit kurang presisi)
- Koneksi internet hanya dibutuhkan sekali untuk memuat font (Google Fonts). Jika offline, aplikasi otomatis memakai font bawaan sistem — semua fungsi tetap normal

## Struktur project

```
├── index.html      # Aplikasi lengkap (HTML + CSS + JS dalam satu file, tanpa dependency eksternal wajib)
├── README.md        # Dokumen ini
└── LICENSE           # Lisensi MIT
```

## Kontribusi & modifikasi

Karena seluruh aplikasi ada dalam satu file `index.html`, memodifikasinya cukup mudah — tidak perlu build tools, bundler, atau instalasi package apa pun. Cukup edit langsung dan refresh browser untuk melihat perubahan.

## Lisensi

Dirilis di bawah [Lisensi MIT](LICENSE) — bebas digunakan, dimodifikasi, dan dibagikan untuk keperluan pendidikan maupun lainnya.
