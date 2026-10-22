# Gudangtool — Copy Halaman Kategori & Detail Tool v2.0

**Tanggal:** 22 Oktober 2026
**Menggantikan:** v1.0
**Dasar:** `01-brand-brief.md` v2.0 · `03-homepage-copy.md` v2.0 · `08-pivot-memo.md`
**Status:** template berlaku untuk model direktori dengan tiga label.

---

# BAGIAN A — HALAMAN KATEGORI

## A1. Struktur

```
Breadcrumb
H1 + intro kategori + baris meta
Pencarian dalam kategori
Filter: status (Semua / Diuji / Terdaftar), akses, platform
Urutan: Paling relevan / Terbaru diperiksa / Nama A–Z
Grid kartu
Muat lebih banyak
Kategori lain
```

## A2. Copy per elemen

**Breadcrumb:**
```
Gudang / Gudang Desain
```

**Baris meta:**
```
{n} tool · {x} diuji · diperbarui {Bulan Tahun}
```

**Pencarian:**
```
Cari di Gudang Desain…
```

**Filter status:** `Semua` · `Diuji` · `Terdaftar`
**Filter akses:** `Tanpa akun` · `Butuh akun`
**Filter platform:** `Web` · `Desktop` · `Ponsel`

**Urutan:**
```
Urutkan: Paling relevan
```
Pilihan: `Paling relevan` · `Terbaru diperiksa` · `Nama A–Z`

**Baris jumlah:**
```
Menampilkan {12} dari {n} tool
```

**Tombol muat:**
```
Muat {12} tool lagi
```

**Penutup daftar:**
```
Itu semua isi Gudang Desain. Tool yang belum diuji diberi label Terdaftar.
```

**Empty state filter:**
```
Tidak ada tool yang cocok dengan filter ini.
Coba lepaskan satu filter.
```
Tombol: `Hapus semua filter`

**Empty state kategori:**
```
Gudang ini belum cukup isi untuk ditampilkan.
Kami menunggu minimal 12 tool sebelum membukanya.
```
Tombol: `Titipkan tool`

**Kategori lain:**
```
Gudang lain
```

## A3. Intro delapan kategori

**Gudang AI**
```
Tool untuk menulis, meringkas, membuat gambar, dan mengolah dokumen dengan model bahasa. Batas hariannya kami tulis di setiap kartu — termasuk tool yang belum diuji, yang diberi label Terdaftar.
```

**Gudang Desain**
```
Untuk membuat diagram, mengedit gambar, dan menyiapkan aset visual tanpa berlangganan. Hampir semuanya berjalan di browser; yang butuh dipasang kami tandai.
```

**Gudang Video**
```
Potong, gabung, beri subtitle, dan kompres video. Tool yang harus diinstal diberi tanda, karena tidak semua orang mau memasang aplikasi untuk satu tugas.
```

**Gudang Audio**
```
Merekam, membersihkan, dan menyunting suara. Tiga tugas berbeda, dan kami tidak mencampurnya dalam satu kategori abu-abu.
```

**Gudang Produktivitas**
```
Catatan, tugas, dan pintasan kerja yang mengurangi klik. Dipilih karena dipakai setiap hari, bukan karena daftar fiturnya panjang.
```

**Gudang Developer**
```
Editor, penguji regex, dan dokumentasi. Untuk yang menulis kode setiap hari dan tidak ingin memasang lima aplikasi untuk lima tugas kecil.
```

**Gudang Marketing**
```
Materi visual, pengukuran, dan konten sosial. Cukup untuk tim satu orang yang mengerjakan semuanya sendiri.
```

**Gudang UMKM**
```
Katalog, kehadiran di pencarian, dan komunikasi pelanggan. Dipilih untuk usaha yang belum punya tim IT dan tidak punya waktu belajar tool rumit.
```

## A4. SEO per kategori

| Kategori | Title (≤60) | Meta description (≤155) |
|---|---|---|
| AI | Gudang AI — Tool AI Gratis \| Gudangtool | Tool AI untuk menulis, meringkas, dan membuat gambar. Batas gratis setiap tool ditulis apa adanya, dengan label sudah diuji atau belum. |
| Desain | Gudang Desain — Tool Desain Gratis \| Gudangtool | Tool desain gratis: diagram, edit gambar, dan aset ilustrasi. Status gratis dan label verifikasinya tercantum di setiap kartu. |
| Video | Gudang Video — Tool Video Gratis \| Gudangtool | Potong, subtitle, dan kompres video tanpa langganan. Tool web maupun yang perlu dipasang, lengkap dengan batas gratisnya. |
| Audio | Gudang Audio — Tool Audio Gratis \| Gudangtool | Rekam, bersihkan, dan sunting suara dengan tool gratis. Setiap batas kuota dan watermark ditulis terbuka. |
| Produktivitas | Gudang Produktivitas — Tool Gratis \| Gudangtool | Catatan, tugas, dan pintasan kerja yang dipakai sehari-hari. Gratis, dengan catatan jelas soal fitur berbayarnya. |
| Developer | Gudang Developer — Tool Developer Gratis \| Gudangtool | Editor kode, penguji regex, dan dokumentasi. Tool untuk kerja harian, dengan batas yang tidak disembunyikan. |
| Marketing | Gudang Marketing — Tool Marketing Gratis \| Gudangtool | Materi visual, analitik, dan konten sosial untuk tim kecil. Status gratis dan batas fiturnya ditulis apa adanya. |
| UMKM | Gudang UMKM — Tool Usaha Gratis \| Gudangtool | Katalog, Maps, dan chat pelanggan untuk usaha kecil. Tool yang bisa dipakai tanpa tim IT. |

## A5. Aturan kategori

- Kategori dengan kurang dari 12 tool tidak diindeks, tetapi tetap tampil di navigasi selama punya minimal 3 tool.
- Angka di baris meta dihitung otomatis, termasuk jumlah tool berlabel Diuji.
- Filter "Diuji" tidak boleh menghasilkan halaman kosong tanpa penjelasan; jika kosong, tampilkan ajakan menitipkan tool.
- Intro kategori tidak boleh memakai superlatif.

---

# BAGIAN B — HALAMAN DETAIL TOOL

## B1. Prinsip

Halaman detail tidak boleh menyiratkan verifikasi yang belum dilakukan. Karena itu ada **tiga keadaan**, bukan satu template yang dipakai untuk semua:

| Keadaan | Isi | Klaim gratis |
|---|---|---|
| **Diuji** | Halaman penuh: tabel batas, alasan, kecocokan, alternatif, riwayat | Boleh, dengan tanggal |
| **Terdaftar** | Halaman ringkas: apa ini, kategori, platform, tautan resmi, status belum diuji | Dilarang |
| **Berbayar** | Penanda placement di atas halaman; keadaan dasar tetap Diuji atau Terdaftar | Mengikuti keadaan dasar |

## B2. Template — Diuji

**Breadcrumb:** `Gudang / {Kategori} / {Nama}`

**Baris status:**
```
Diuji · {Gratis | Freemium | Butuh akun} · Terakhir diperiksa {tanggal}
```

**Deck:**
```
{Satu kalimat: tool ini untuk apa}
```

**Tombol:**
```
Buka {domain}
```
Catatan: `Terbuka di tab baru. {Tidak perlu akun | Perlu akun.}`

**Panel info:** kategori · platform · status · akun · terakhir diperiksa

**Kenapa ada di gudang**
```
{2–3 kalimat: apa yang kami uji dan mengapa tool ini layak}
```

**Batas gratis**
```
Ini yang kami temukan saat memakainya. Kalau ada yang berubah, tanggal di atas ikut berubah.
```
Tabel: akun · kuota · watermark · ekspor · penyimpanan

**Cocok untuk / Tidak cocok untuk** — keduanya wajib diisi.

**Alternatif** — dua tool, masing-masing dengan alasan satu kalimat.

**Riwayat pemeriksaan** — minimal dua baris.

**Laporkan perubahan** — tautan.

## B3. Template — Terdaftar

**Breadcrumb:** `Gudang / {Kategori} / {Nama}`

**Baris status:**
```
Terdaftar · Belum diuji
```

**Deck:**
```
{Satu kalimat fungsi, diambil dari situs resmi dan ditulis ulang}
```

**Blok peringatan (wajib, di atas konten):**
```
Kami belum menguji tool ini. Status gratisnya belum dipastikan — bisa saja berubah, atau tidak sesuai yang tertulis di situsnya. Kalau kamu memakainya, kabari kami.
```

**Tombol:**
```
Buka situs resmi
```
Catatan: `Terbuka di tab baru. Kami tidak menerima pembayaran dari tautan ini.`

**Panel info:** kategori · platform · label · tanggal ditambahkan

**Yang belum kami ketahui**
```
Apakah perlu akun · Apakah ada kuota · Apakah ada watermark · Apakah perlu kartu kredit
```
Semua diisi "Belum diperiksa" — jangan dikosongkan.

**Alternatif yang sudah diuji**
```
Kalau kamu butuh kepastian sebelum mencoba, ini tool sejenis yang sudah kami uji.
```
Dua kartu berlabel Diuji.

**Laporkan pengalamanmu**
```
Sudah memakai tool ini? Kabari apa yang kamu temukan — kami akan menjadikannya Diuji.
```

**Yang tidak boleh ada di halaman Terdaftar:**
- Kata "gratis" di judul, deck, atau meta description.
- Tabel batas gratis.
- Bagian "Kenapa ada di gudang".
- Bagian "Cocok untuk".
- Peringkat atau skor.

## B4. Penanda Berbayar

Jika sebuah tool adalah placement, tambahkan di atas judul:

```
PLACEMENT BERBAYAR
```

Dan satu baris di panel info:
```
Status verifikasi dan ranking tidak dipengaruhi pembayaran.
```

Penanda ini tidak boleh disembunyikan di footer, dan tidak boleh memakai warna aksen yang sama dengan tombol aksi.

## B5. Contoh terisi — Diuji (Excalidraw)

**Status:** `Diuji · Gratis · Terakhir diperiksa 21 Oktober 2026`

**Deck:** `Papan gambar sketsa untuk diagram dan wireframe.`

**Kenapa ada di gudang:**
```
Karena bisa dipakai tanpa akun sama sekali — jarang untuk tool gambar sekelas ini. Kami memakainya untuk membuat diagram alur dan wireframe kasar; hasilnya bisa diekspor ke PNG atau SVG tanpa watermark.
```

**Batas gratis:**

| Aspek | Isi |
|---|---|
| Akun | Tidak perlu |
| Kuota | Tidak ada |
| Watermark | Tidak ada |
| Ekspor | PNG, SVG, dan file `.excalidraw` |
| Penyimpanan | Di browser (penyimpanan lokal) |

**Peringatan:**
```
Gambar tersimpan di browser, bukan di akun. Kalau cache dibersihkan atau kamu berpindah perangkat, gambarnya tidak ikut. Ekspor dulu sebelum menutup.
```

**Cocok untuk:** `Diagram alur, wireframe kasar, dan menjelaskan ide saat rapat.`
**Tidak cocok untuk:** `Ilustrasi detail, desain cetak, atau pekerjaan yang butuh presisi vektor.`

## B6. Contoh terisi — Terdaftar (placeholder)

**Status:** `Terdaftar · Belum diuji`

**Deck:** `{Satu kalimat fungsi, ditulis ulang dari situs resmi.}`

**Yang belum kami ketahui:** semua baris diisi `Belum diperiksa`.

**Alternatif yang sudah diuji:** dua kartu dari kategori yang sama, masing-masing berlabel Diuji.

> Jangan mengisi contoh ini dengan tool nyata sebelum benar-benar diperiksa. Halaman Terdaftar yang mengarang satu detail saja merusak alasan keberadaan label itu.

## B7. SEO per keadaan

**Diuji:**
```
{Nama} — {fungsi singkat} | Gudangtool
{Nama} adalah {fungsi}. {Status}, {syarat akun}. Batas gratis dan alternatifnya kami catat.
```

**Terdaftar:**
```
{Nama} — {fungsi singkat} | Gudangtool
{Nama} terdaftar di Gudangtool dan belum diuji. Lihat fungsinya, platformnya, dan alternatif yang sudah diuji.
```
> Kata "gratis" dilarang di title dan meta untuk halaman Terdaftar.

## B8. Aturan penulisan

1. Kalimat pertama menjawab "ini apa", bukan "ini bagus".
2. Tabel batas wajib untuk Diuji; dilarang untuk Terdaftar.
3. "Tidak cocok untuk" tidak boleh kosong pada halaman Diuji.
4. Riwayat tidak boleh dihapus.
5. Tanggal harus nyata.
6. Halaman Terdaftar yang sudah diuji harus dinaikkan labelnya, bukan dibiarkan setengah jadi.

---

# BAGIAN C — HALAMAN PENDUKUNG

## C1. Halaman ranking

**H1:** `Ranking bulan ini`

**Intro:**
```
Disusun dari pembukaan kartu dan simpan. Diperbarui setiap awal bulan.
```

**Header tabel:** `Peringkat · Tool · Kategori · Pembukaan · Status`

**Catatan metode:**
```
Ranking tidak dijual. Slot placement diberi label dan tidak mengubah posisi.
```

**Aturan:** hanya tool berlabel **Diuji** yang masuk ranking. Entri Terdaftar tidak diikutkan, walau jumlah pembukaannya tinggi.

**Empty state:**
```
Ranking bulan ini belum tersedia. Kami menampilkan angka setelah sampelnya cukup.
```

## C2. Halaman submit

**H1:** `Titipkan tool`

**Intro:**
```
Dua jalur. Keduanya melewati pemeriksaan yang sama.
```

**Kartu jalur:**

| Jalur | Waktu | Biaya | Jaminan |
|---|---|---|---|
| Biasa | Antrean {14} hari | Gratis | Tidak ada |
| Prioritas | {48} jam | Berbayar | Tidak ada |

**Yang kami periksa:**
```
Relevansi dengan kategori · status gratis yang bisa dijelaskan · kualitas dasar · keamanan situs
```

**Aturan:**
```
Satu pengajuan per tool. Tidak ada jaminan tayang. Kami menolak tool yang menyembunyikan biaya atau meminta kartu kredit untuk versi "gratis".
```

**Field:** nama tool · URL · kategori · satu kalimat fungsi · status gratis yang diklaim · email

**Sukses:** `Masuk antrean. Kami akan memeriksa dan mengabari lewat email.`
**Gagal:** `Pengirimannya belum berhasil. Coba sekali lagi, atau kirim lewat email.`

## C3. Halaman koleksi

**H1:** `{Nama koleksi}` — mis. `Tool gratis tanpa akun`

**Intro:**
```
Tool yang {syarat}. Dihitung ulang setiap kali katalog berubah.
```

**Baris jumlah:** `{n} tool · {x} sudah diuji`

**Aturan:** koleksi hanya berisi entri berlabel **Diuji**. Entri Terdaftar tidak boleh muncul di halaman koleksi, karena koleksi menyiratkan jaminan yang belum tentu dimiliki.

**Empty state:**
```
Koleksi ini belum punya cukup tool. Kami tidak menampilkannya sampai isinya layak.
```

---

# BAGIAN D — MIKROCOPY

| Konteks | Copy |
|---|---|
| Tool Terdaftar | Kami belum menguji tool ini. Status gratisnya belum dipastikan. |
| Tool sudah tidak gratis | Tool ini tidak lagi punya paket gratis sejak {bulan tahun}. Kami simpan sebagai catatan. |
| Tool tidak aktif | Situs tool ini sudah tidak bisa diakses sejak {bulan tahun}. Halaman kami pertahankan sebagai catatan. |
| Laporkan — sukses | Terima kasih. Kami akan memeriksa ulang dan memperbarui tanggalnya. |
| Laporkan — gagal | Laporannya belum terkirim. Coba lagi, atau kirim lewat email. |
| Placement | Placement berbayar. Tidak memengaruhi status verifikasi atau ranking. |
| Alternatif | Bukan pengganti langsung, tapi cocok kalau kamu butuh {kebutuhan spesifik}. |

---

# BAGIAN E — KEPUTUSAN TERBUKA

1. **Batas waktu antrean biasa** — {14} hari masih placeholder; tentukan setelah kapasitas uji diketahui.
2. **Harga prioritas** — belum ditetapkan; jangan tulis angka sebelum ada keputusan bisnis.
3. **Apakah halaman Terdaftar diindeks?** Rekomendasi: ya, tetapi tanpa kata "gratis" dan dengan tanggal ditambahkan. Halaman Terdaftar yang tipis tanpa data sebaiknya `noindex`.
4. **Apakah ranking memakai pembukaan saja atau pembukaan + simpan?** Rekomendasi: keduanya, dengan bobot yang dipublikasikan.
