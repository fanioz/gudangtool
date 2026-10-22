# Gudangtool — Memo Pivot: dari Katalog Kurasi ke Direktori Berskala

**Tanggal:** 22 Oktober 2026
**Status:** Keputusan pemilik proyek. Menggantikan asumsi pada Brand Brief v1.0; brand brief kini v2.0.
**Ringkas:** Gudangtool pindah ke model direktori besar dengan pendapatan iklan dan placement berbayar, sambil mempertahankan satu aset yang tidak dimiliki pesaing: data batas gratis yang diverifikasi.

---

## 1. Keputusan

Direktori besar, submit berbayar, ranking, UX padat, data lengkap, dan SEO seluas mungkin — dengan monetisasi AdSense dan placement.

Ini bukan penambahan fitur. Ini **pergantian identitas produk**. Tiga hal yang sebelumnya menjadi inti brand harus pensiun:

| Sebelumnya | Sekarang |
|---|---|
| "Sedikit tapi terkurasi" | "Luas, dengan verifikasi bertingkat" |
| "Direktori lain memuat ribuan tautan" | Kalimat itu dihapus — kita meniru model tersebut |
| "Tidak ada tool yang masuk karena membayar" | "Tidak ada peringkat yang dijual; placement berbayar diberi label" |
| Semua tool diuji 15 menit | Hanya tier "Diuji" yang melewati QA penuh |

Kalau kalimat lama dibiarkan sementara katalog tumbuh ke ribuan, situs akan berbohong pada dirinya sendiri — dan pembaca pertama yang menyadarinya adalah pesaing yang ingin menjatuhkan kita.

---

## 2. Positioning baru

> Direktori tool digital berbahasa Indonesia yang luas, dengan satu data yang tidak dimiliki direktori lain: **batas gratis yang ditulis apa adanya.**

Kalimat ini menyelamatkan diferensiasi tanpa menahan skala. Kita boleh punya 10.000 tool; yang tidak boleh hilang adalah satu alasan untuk memilih kita daripada Toolify.

### Tiga pilar

1. **Cakupan luas, verifikasi bertingkat.** Semua tool boleh masuk; hanya yang diuji mendapat label "Diuji". Kejujuran label adalah produknya.
2. **Batas gratis sebagai data utama.** Setiap tool menjawab: benar-benar gratis? sampai mana? perlu akun? kena watermark? Ini yang dicari orang dan tidak dijawab direktori besar.
3. **Dibangun untuk Indonesia.** Bahasa, rupiah, kebutuhan lokal, dan konteks pemakaian — bukan terjemahan mesin dari direktori Inggris.

### Anti-pilar

- **Bukan direktori yang menjual peringkat.** Slot bisa dijual; posisi ranking tidak.
- **Bukan pabrik halaman tipis.** Tidak ada halaman yang isinya hanya deskripsi vendor hasil salin.
- **Bukan situs yang mengklaim "terbesar" sebelum angka mendukungnya.**

---

## 3. Arsitektur halaman (pola Toolify, isi sendiri)

**Beranda**
1. Pencarian besar di atas — placeholder menyebut kebutuhan, bukan nama tool.
2. Kategori rapat (8 utama, "lihat semua").
3. Baru masuk.
4. Paling sering dibuka minggu ini — dari data sendiri, bukan taksiran.
5. Koleksi berbasis filter: "Gratis tanpa akun", "Jalan di browser", "Tanpa watermark".
6. Ranking bulan ini.
7. Cara kami memberi label (Diuji / Terdaftar / Berbayar).
8. Submit tool.
9. Artikel pendukung (SEO).

**Kategori**
- 8 kategori utama, lalu subkebutuhan sebagai "lorong" (mis. Desain → hapus background, bikin logo, mockup).
- **Jangan 459 kategori.** Itu taksonomi mesin, bukan bahasa manusia; juga memecah otoritas SEO menjadi ribuan halaman tipis.
- Halaman kategori wajib punya intro unik dan minimal 12 tool sebelum diindeks.

**Detail tool**
- Tabel data (hanya untuk tier Diuji): status, akun, kuota, watermark, platform, harga dalam rupiah.
- Tier Terdaftar memakai blok "yang belum kami ketahui", tanpa tabel dan tanpa klaim gratis.
- Label tier + tanggal verifikasi.
- Alternatif, riwayat, laporan perubahan.
- Ini halaman yang menghasilkan uang dan kepercayaan sekaligus.

**Ranking**
- Basis: pembukaan kartu dan simpan (bookmark) di situs sendiri.
- Tampilkan hanya jika sampel cukup (mis. minimal 100 pembukaan per periode). Tanpa ambang, ranking akan terlihat acak dan cepat kehilangan kredibilitas.
- Kalau nanti memakai data pihak ketiga (Similarweb), **wajib cantumkan sumber dan tanggal** — jangan menyajikan taksiran sebagai fakta.

---

## 4. Data: apa yang ditampilkan dan dari mana

| Data | Sumber | Catatan |
|---|---|---|
| Status gratis, akun, kuota, watermark | Uji sendiri | Aset utama; tidak bisa disalin pesaing tanpa kerja |
| Harga | Halaman resmi tool, dikonversi ke rupiah | Cantumkan tanggal kurs |
| Platform | Halaman resmi | Web, desktop, ponsel |
| Popularitas | Data sendiri (klik, simpan) | Jujur dan gratis |
| Trafik bulanan | Pihak ketiga berbayar | Tampilkan hanya jika mampu membeli lisensi dan mencantumkan sumber |
| Ranking | Data sendiri | Jangan pernah menjual posisi |

**Keputusan penting:** jangan menampilkan angka trafik yang tidak bisa dipertanggungjawabkan. Satu angka palsu menghapus seluruh kredibilitas data lain — dan di direktori, data adalah satu-satunya produk.

---

## 5. Model pendapatan

### Urutan, bukan daftar

1. **AdSense** — baru dipasang setelah ada 30+ halaman berkualitas dan kunjungan organik. Mendaftar dengan situs tipis berisiko ditolak.
2. **Placement berbayar** — jual slot di kategori ("Featured di Gudang Desain"), bukan peringkat. Butuh bukti trafik sebelum bisa dijual.
3. **Fast-track submission** — review 48 jam, **tanpa jaminan tayang**. Ini menjaga integritas: yang dijual adalah kecepatan, bukan kelulusan.
4. **Afiliasi** — hanya untuk tool yang punya program; wajib berlabel.

### Asumsi pendapatan (wajib divalidasi)

RPM iklan untuk trafik Indonesia umumnya jauh di bawah trafik Amerika. Gunakan asumsi konservatif **$0,5–2 per 1.000 pageview** sebagai perencanaan, bukan janji.

| Pageview/bulan | RPM $0,5 | RPM $1 | RPM $2 |
|---|---|---|---|
| 50.000 | $25 | $50 | $100 |
| 200.000 | $100 | $200 | $400 |
| 500.000 | $250 | $500 | $1.000 |
| 1.000.000 | $500 | $1.000 | $2.000 |

**Kesimpulan yang harus dihadapi:** AdSense tidak akan menjadi penghasilan berarti sebelum ratusan ribu pageview. **Placement berbayar adalah tuas yang jauh lebih cepat** — 10 slot × $30–100 = $300–1.000/bulan, dan itu bisa dicapai dengan trafik puluhan ribu, bukan jutaan.

Artinya: jangan bangun situs ini dengan asumsi "AdSense akan membiayai semuanya". Bangun dengan asumsi "placement dan submission yang membiayai, AdSense adalah bonus".

---

## 6. SEO: peluang dan risiko yang bisa mematikan

**Peluang:** kata kunci berbahasa Indonesia untuk kebutuhan spesifik masih longgar — "tool gratis hapus background tanpa akun", "ai bikin logo gratis bahasa indonesia", "kompres video tanpa watermark". Ini long-tail yang tidak dilayani Toolify karena ia berbahasa Inggris dan berorientasi global.

**Risiko utama:** kebijakan Google tentang **scaled content abuse** — produksi halaman dalam jumlah besar yang tidak memberi nilai tambah. Direktori 31.000 halaman dengan deskripsi hasil salin adalah profil yang persis dicari kebijakan itu. Hukumannya bukan penalti kecil: halaman bisa tidak diindeks sama sekali.

**Aturan main yang tidak boleh dilanggar:**

1. **Setiap halaman harus punya data yang tidak ada di tempat lain** — tabel batas gratis, tanggal verifikasi, alternatif, harga rupiah.
2. **Jangan menyalin deskripsi vendor.** Tulis ulang dalam bahasa sendiri; salinan identik adalah duplicate content sekaligus pelanggaran hak cipta.
3. **Jangan mengindeks halaman kosong.** Kategori dengan kurang dari 12 tool tidak masuk sitemap.
4. **Naik bertahap.** 300 halaman dulu, pantau indeks, baru 1.000. Jangan mengunggah 31.000 halaman dalam sebulan.
5. **Kedalaman mengalahkan jumlah.** 500 halaman dengan data unik lebih tahan lama daripada 10.000 halaman hasil templating kosong.

---

## 7. Peta jalan 12 bulan

**Fase 0 — Fondasi (minggu 1–2)**
Model data, 8 kategori, 50 tool diuji, label tier, struktur URL, analytics.

**Fase 1 — Traksi awal (minggu 3–8)**
300 tool, 40 halaman kebutuhan, alur submit + moderasi, 20 artikel pendukung, sitemap dan schema.

**Fase 2 — Skala pertama (bulan 3–6)**
1.000 tool, halaman koleksi programmatic dari data (bukan teks hasil spin), AdSense aktif, 5 placement pertama.

**Fase 3 — Pendapatan (bulan 6–12)**
3.000+ tool, paket placement, afiliasi selektif, ekspansi subkategori.

**Metrik per fase:**

| Waktu | Tool | Pageview/bulan | Pendapatan |
|---|---|---|---|
| Bulan 3 | 300 | 10.000 | $0 |
| Bulan 6 | 1.000 | 50.000 | $100–300 |
| Bulan 12 | 3.000 | 200.000 | $500–1.500 |

**Kriteria berhenti:** kalau pada bulan ke-9 trafik organik di bawah 20.000/bulan dan pendapatan di bawah $100, jangan tambah konten. Persempit ke satu niche yang terbukti (mis. tool gratis untuk UMKM) atau pindah ke model placement/lead generation.

---

## 8. Kepatuhan yang sering dilupakan

- **AdSense:** konten asli, navigasi jelas, halaman kebijakan privasi, persetujuan cookie, tidak ada iklan yang menyamar sebagai tombol.
- **Label berbayar:** setiap placement harus terlihat sebagai placement. Menyamarkannya sebagai pilihan editor adalah cara tercepat kehilangan kepercayaan sekaligus melanggar kebijakan.
- **UU PDP:** beri tahu data apa yang dikumpulkan (analytics, cookie), dan sediakan cara menolak.
- **Klaim "terbesar":** jangan pakai sebelum angkanya benar. Gunakan angka aktual — "1.240 tool, 380 di antaranya sudah diuji" lebih kuat daripada "terbesar di Indonesia".

---

## 9. Keputusan yang masih terbuka

1. **Pasar pertama:** Indonesia dulu (kuat di `.web.id`), atau langsung Inggris (butuh `.com` dan modal konten jauh lebih besar)? Rekomendasi: Indonesia dulu 12 bulan.
2. **Trafik pihak ketiga:** tampilkan data Similarweb berbayar sejak awal, atau bangun data sendiri dulu? Rekomendasi: data sendiri dulu.
3. **Kapasitas uji:** siapa yang menguji tool setiap minggu, dan berapa targetnya? Ini biaya operasional terbesar dan penentu kredibilitas label "Diuji".
4. **Batas tier:** berapa tool yang boleh berstatus "Terdaftar" tanpa diuji? Rekomendasi: tidak lebih dari 80% katalog; minimal 20% harus "Diuji".
5. **Submission berbayar:** dijamin tayang atau hanya dipercepat? Rekomendasi: hanya dipercepat.
