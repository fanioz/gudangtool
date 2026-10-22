# Gudangtool — Copy Halaman Depan v2.0

**Tanggal:** 22 Oktober 2026
**Menggantikan:** v1.0 (model katalog kurasi)
**Dasar:** `08-pivot-memo.md` · `09-decision-log.md`
**Status:** siap dipakai. Angka dalam kurung kurawal wajib diisi dari data aktual.

---

## 0. Yang berubah dari v1.0

| v1.0 | v2.0 |
|---|---|
| "Direktori lain memuat ribuan tautan, kami memilih jumlah yang bisa dipertanggungjawabkan" | **Dihapus.** Bertentangan dengan model direktori |
| Seksi "Kenapa isinya lebih sedikit" | Diganti "Cara kami memberi label" |
| Katalog kecil sebagai identitas | Katalog luas dengan verifikasi bertingkat |
| Tanpa ranking | Ranking bulan ini dari data sendiri |
| Tanpa jalur submit | Jalur submit dan placement berbayar |
| Satu jenis kartu | Tiga label: Diuji, Terdaftar, Berbayar |

Nada tetap: tenang, langsung, tanpa superlatif. Yang berubah adalah **skala janji**, bukan cara bicaranya.

---

## 1. Metadata & SEO

**Title tag (46 karakter):**
```
Gudangtool — Direktori Tool Digital Indonesia
```

**Meta description (148 karakter):**
```
Cari tool digital untuk kerja dan usaha: gratis, freemium, atau berbayar. Setiap kartu menyebut batasnya dan apakah sudah diuji. {N} tool.
```

**OG title:**
```
Gudangtool — semua tool digital, satu gudang
```

**OG description:**
```
Direktori tool digital berbahasa Indonesia. Setiap kartu menyebut batas gratisnya — dan apakah tool itu sudah diuji atau belum.
```

**H1 (hanya satu):** `Semua tool digital, satu gudang.`

---

## 2. Header

**Wordmark:** `gudangtool`

**Navigasi:** `Gudang` · `Kategori` · `Ranking` · `Artikel`

**Tombol kanan:** `Titip tool` (sekunder, border)

**Ikon:** pencarian, simpan, mode terang/gelap (jika ada)

---

## 3. Hero

**Eyebrow:**
```
Direktori tool digital · {N} tool · {M} kategori
```

**H1:**
```
Semua tool digital, satu gudang.
```

**Sub-headline:**
```
Cari berdasarkan kebutuhan, harga, dan platform. Setiap tool punya status verifikasi yang jelas — dan placement selalu ditandai.
```

**Placeholder pencarian:**
```
Cari tool — misalnya: hapus background, transkrip audio, gabung PDF
```

**Tombol:** `Cari`

**Label chip:** `Sering dicari`

**Chip:** `Hapus background` · `Transkrip audio` · `Gabung PDF` · `Bikin logo` · `Ringkas video` · `Kompres gambar`

**Baris kepercayaan:**
```
{N} tool · {X} sudah diuji · diperbarui {Bulan Tahun}
```

> Chip harus diambil dari data pencarian nyata. Sebelum ada data, gunakan enam tugas yang tool-nya benar-benar tersedia di katalog — jangan memancing pencarian yang belum ada hasilnya.

### Alternatif H1

| Varian | Copy | Kapan dipakai |
|---|---|---|
| A (dipakai) | Semua tool digital, satu gudang. | Beranda — mempertahankan nama dan metafora |
| B | Cari tool yang benar-benar gratis. | Iklan dan bio sosial — berbasis kebutuhan |
| C | {N} tool digital, dengan batas yang jelas. | Halaman landing — berbasis angka dan diferensiasi |

Jangan memakai lebih dari satu H1 di halaman yang sama.

---

## 4. Kategori

**H2:**
```
Jelajahi gudang
```

**Sub:**
```
Delapan kategori, {L} lorong. Setiap tool punya status yang bisa kamu cek sebelum membuka.
```

**Kartu kategori** (nama · jumlah · satu baris):

| Kategori | Jumlah | Keterangan |
|---|---|---|
| Gudang AI | {n} | Menulis, meringkas, membuat gambar |
| Gudang Desain | {n} | Diagram, edit gambar, aset visual |
| Gudang Video | {n} | Potong, subtitle, kompres |
| Gudang Audio | {n} | Rekam, bersihkan, transkrip |
| Gudang Produktivitas | {n} | Catatan, tugas, otomatisasi kecil |
| Gudang Developer | {n} | Editor, API, dokumentasi |
| Gudang Marketing | {n} | Konten sosial, email, analitik |
| Gudang UMKM | {n} | Katalog, kasir, komunikasi pelanggan |

**Tautan:**
```
Lihat semua kategori
```

> Kategori dengan kurang dari 12 tool tidak diindeks, tetapi tetap tampil di navigasi selama punya minimal 3 tool. Kategori dengan kurang dari 3 tool disembunyikan.

---

## 5. Baru masuk gudang

**H2:**
```
Baru masuk gudang
```

**Sub:**
```
Tool yang terakhir kami tambahkan. Labelnya menunjukkan sudah diuji atau belum.
```

**Kartu contoh:**

```
GUDANG DESAIN · DIUJI

Excalidraw
Papan gambar sketsa untuk diagram dan wireframe.

[Diuji] [Tanpa akun] [Gratis]
```

```
GUDANG AI · TERDAFTAR

{ Nama tool }
{Satu kalimat dari halaman resmi, ditulis ulang}

[Terdaftar] [Belum diuji]
```

> Jangan mencampur label "Diuji" dan "Terdaftar" tanpa membedakan tampilannya. Perbedaan status harus terlihat dari warna badge, bukan hanya teks.

---

## 6. Paling sering dibuka

**H2:**
```
Paling sering dibuka minggu ini
```

**Sub:**
```
Dihitung dari pembukaan kartu di Gudangtool — bukan taksiran trafik.
```

**Format baris:**
```
{01}  {Nama tool}      {jumlah} pembukaan      {status}
```

**Catatan ambang:**
```
Ditampilkan jika minimal {100} pembukaan dalam sepekan.
```

**Jika data belum cukup:**
```
Ranking minggu ini belum tersedia. Kami menampilkan angka setelah sampelnya cukup.
```

> Jangan menampilkan daftar kosong atau angka acak. Ranking yang belum layak tayang lebih baik disembunyikan daripada dipalsukan.

> Ranking hanya memuat tool berlabel **Diuji**. Entri Terdaftar boleh muncul di pencarian, tetapi tidak di ranking — supaya posisi tidak pernah menjadi bentuk rekomendasi yang belum diperiksa.

---

## 7. Koleksi berbasis batasan

**H2:**
```
Cari berdasarkan batasan
```

**Sub:**
```
Filter yang paling sering dibutuhkan, langsung jadi halaman.
```

**Kartu koleksi:**

| Judul | Keterangan | Jumlah |
|---|---|---|
| Gratis tanpa akun | Bisa dipakai tanpa mendaftar | {n} tool |
| Tanpa watermark | Hasil ekspor bersih | {n} tool |
| Jalan di browser | Tanpa perlu memasang aplikasi | {n} tool |
| Tanpa kartu kredit | Tidak ada trial yang menuntut kartu | {n} tool |

**Tautan:**
```
Lihat semua koleksi
```

> Ini seksi yang paling membedakan Gudangtool dari direktori lain. Jangan diisi manual — setiap koleksi harus dihasilkan dari filter data yang nyata. Koleksi berbasis klaim gratis hanya boleh berisi tool berlabel **Diuji**.

---

## 8. Ranking bulan ini

**H2:**
```
Ranking bulan ini
```

**Sub:**
```
Disusun dari pembukaan dan simpan. Tidak ada slot yang dijual di sini.
```

**Format:**
```
{01}  {Nama tool}      {kategori}      {jumlah} pembukaan
```

**Tautan:**
```
Cara kami menyusun ranking
```

**Halaman "Cara kami menyusun ranking" — isi wajib:**
```
Ranking dihitung dari dua hal: berapa kali kartu tool dibuka, dan berapa kali tool disimpan pengguna. Tidak ada faktor lain.

Kami tidak menerima pembayaran untuk menaikkan posisi. Slot placement dijual terpisah, selalu diberi label, dan tidak mengubah ranking.

Angka diperbarui setiap awal bulan. Tool yang baru masuk belum masuk ranking sampai punya cukup data.
```

---

## 9. Cara kami memberi label

**H2:**
```
Cara kami memberi label
```

**Sub:**
```
Dua status verifikasi, satu penanda komersial. Bedanya penting, jadi kami menuliskannya di setiap kartu.
```

**Kartu 1 — Diuji**
```
Kami memakai tool-nya, mencatat batas gratisnya, dan memperbarui tanggalnya. Hanya tool berlabel ini yang kami jamin statusnya.
```

**Kartu 2 — Terdaftar**
```
Tool ini masuk katalog, tetapi belum kami uji. Kartunya tidak mengklaim gratis, dan tidak punya tabel batas.
```

**Penanda 3 — Berbayar**
```
Penanda komersial, bukan status verifikasi. Selalu diberi tanda. Tidak mengubah label dan tidak mengubah ranking.
```

**Catatan penutup:**
```
Kalau sebuah tool tidak berlabel Diuji, jangan anggap kami menjaminnya gratis.
```

---

## 10. Untuk pembuat tool

**H2:**
```
Punya tool? Titipkan.
```

**Body:**
```
Dua jalur: pengiriman biasa dengan antrean {14} hari, atau prioritas {48} jam. Keduanya melewati pemeriksaan yang sama, dan tidak ada jaminan tayang.
```

**Tombol:**
```
Lihat cara titip tool
```

**Catatan kecil:**
```
Slot placement tersedia terpisah, selalu diberi label, dan tidak memengaruhi ranking.
```

---

## 11. Artikel

**H2:**
```
Catatan dari gudang
```

**Sub:**
```
Panduan memilih tool, dan catatan saat batas gratis sebuah tool berubah.
```

**Contoh judul:**
- `Tool gratis yang diam-diam meminta kartu kredit`
- `Cara membaca batas "gratis" sebelum mulai bekerja`
- `Kapan tool berbayar sebenarnya lebih murah`

---

## 12. Footer

**Tagline:**
```
Gudangnya tool digital.
```

**Kolom 1 — Gudang:** AI · Desain · Video · Audio · Produktivitas · Developer
**Kolom 2 — Jelajah:** Kategori · Ranking · Koleksi · Artikel
**Kolom 3 — Tentang:** Cara kerja · Titip tool · Kontak · Kebijakan privasi

**Baris pengungkapan:**
```
Beberapa tautan mungkin berafiliasi dan selalu ditandai. Placement berbayar tidak memengaruhi ranking.
```

**Copyright:**
```
© 2026 Gudangtool
```

---

## 13. Bank mikrocopy

| Konteks | Copy |
|---|---|
| Pencarian kosong | Belum ada yang cocok dengan "{query}". Coba kata yang lebih umum, atau titipkan tool-nya. |
| Filter kosong | Tidak ada tool yang cocok dengan kombinasi filter ini. Coba lepaskan satu filter. |
| Memuat hasil | Membuka rak… |
| Kategori belum siap | Gudang ini sedang diisi. Kami tidak menayangkan kategori yang belum punya cukup tool. |
| Tool belum diuji | Tool ini terdaftar, belum diuji. Status gratisnya belum kami pastikan. |
| Tool sudah tidak gratis | Tool ini tidak lagi punya paket gratis sejak {bulan tahun}. Kami simpan sebagai catatan. |
| Ranking belum cukup data | Ranking minggu ini belum tersedia. Angka ditampilkan setelah sampelnya cukup. |
| Badge — Diuji | Sudah dipakai dan diperiksa. Batas gratisnya dicatat. |
| Badge — Terdaftar | Masuk katalog, belum diuji. Tidak ada klaim gratis. |
| Badge — Berbayar | Placement berbayar. Tidak memengaruhi status atau ranking. |
| Kirim tool — sukses | Masuk antrean. Kami akan memeriksa dan mengabari lewat email. |
| Kirim tool — gagal | Pengirimannya belum berhasil. Coba sekali lagi, atau kirim lewat email. |
| 404 | Rak ini tidak ada. Coba lorong lain, atau kembali ke gudang. |
| Tool tidak aktif | Situs tool ini sudah tidak bisa diakses sejak {bulan tahun}. Halaman kami pertahankan sebagai catatan. |

---

## 14. Aturan nada

**Lakukan:**
- Satu ide per kalimat.
- Sebut angka: jumlah tool, ambang ranking, lama antrean.
- Akui batasan sebelum pembaca menemukannya.
- "Kamu", bukan "Anda".

**Hindari:**
- "Terbesar", "terlengkap", "nomor satu" — sampai angkanya benar-benar mendukung.
- Superlatif dan kata vaporware: platform, solusi, ekosistem, all-in-one.
- Tanda seru lebih dari satu di seluruh halaman.
- Klaim status gratis tanpa tanggal verifikasi.
- Menyembunyikan label placement.

---

## 15. Wajib diverifikasi sebelum publikasi

- [ ] Semua `{N}`, `{M}`, `{X}`, `{L}` diisi dari data aktual, bukan perkiraan
- [ ] Ranking hanya tampil jika ambang pembukaan terpenuhi
- [ ] Setiap kartu punya salah satu dari tiga label: Diuji / Terdaftar / Berbayar
- [ ] Tidak ada kalimat "direktori lain memuat ribuan tautan" yang tersisa
- [ ] Tidak ada klaim "terbesar" tanpa angka
- [ ] Pengungkapan afiliasi dan placement terlihat, bukan tersembunyi di footer kecil
- [ ] Hanya satu H1 di halaman
- [ ] Title ≤60 karakter, meta description ≤155 karakter
