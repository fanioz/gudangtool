# Gudangtool — Brief Identitas Visual v1.1

**Domain:** gudangtool.web.id
**Tanggal:** 22 Oktober 2026 (revisi v1.1)
**Turunan dari:** Brand Brief v2.0
**Status:** Logo Arah A dikunci. Sistem visual berlaku untuk model direktori.

---

## 1. Prinsip

Identitas ini harus menyelesaikan satu masalah spesifik: **"gudang tool" di Indonesia masih berarti toko perkakas fisik.** Setiap keputusan visual harus menjauhkan asosiasi itu, bukan mendekatkannya.

Tiga prinsip yang mengikat semua keputusan:

1. **Gudang, bukan bengkel.** Rak, peti, label, lorong. Bukan bor, kunci pas, palu, tekstur besi.
2. **Rapi, bukan ramai.** Ruang kosong adalah bagian dari pesan. Situs ini menjual kejelasan, bukan keramaian.
3. **Terbaca dulu, baru pintar.** Simbol harus masih terbaca di 16px sebelum ia boleh punya makna ganda.

---

## 2. Arah logo (A dikunci)

> **Keputusan:** Arah A dipakai. B dan C disimpan sebagai catatan, bukan opsi aktif.

### Arah A — Rak & Peti (rekomendasi)

Simbol geometris: satu penyangga vertikal, dua garis rak, satu peti kecil di rak atas.

- **Membaca:** rak yang menampung barang pilihan — metafora kurasi dalam bentuk paling dasar.
- **Kekuatan:** skalabel sampai 16px; tidak memakai ikon perkakas sama sekali; mudah digambar ulang oleh siapa pun.
- **Risiko:** bisa dibaca sebagai diagram/grafik kalau garisnya terlalu tipis. Solusi: stroke 3px pada grid 48, ujung datar.

### Arah B — Peti Terbuka

Simbol: badan peti dengan dua tutup terbuka ke samping.

- **Membaca:** sesuatu baru dibuka, isinya siap diambil.
- **Kekuatan:** lebih hangat dan ekspresif; bagus untuk ilustrasi dan animasi.
- **Risiko:** pada ukuran kecil tutupnya menyatu dengan badan; kurang tajam sebagai favicon.

### Arah C — Label Stiker

Tanpa simbol. Wordmark mono kapital di dalam label kraft, dengan elemen barcode.

- **Membaca:** label gudang, arsip, inventaris.
- **Kekuatan:** paling editorial dan paling dewasa; sangat cocok dengan sistem kartu tool.
- **Risiko:** tidak punya ikon untuk favicon/app icon; butuh disiplin tinggi agar tidak terasa seperti template.

### Rekomendasi

**Pakai A sebagai simbol utama, dan C sebagai bahasa label untuk UI.** Keduanya tidak bersaing — A mengisi peran ikon (favicon, avatar, penanda kategori), C mengisi peran tipografi (badge, strip kartu, penanda rak). B disimpan sebagai alternatif kalau kamu ingin nada yang lebih hangat dan bersedia mengorbankan ketajaman di ukuran kecil.

---

## 3. Sistem logo

| Varian | Penggunaan | Ukuran minimum |
|---|---|---|
| Horizontal (simbol + wordmark) | Header situs, OG image, presentasi | lebar 88px |
| Vertikal (simbol di atas wordmark) | Sampul, merchandise, halaman 404 | lebar 64px |
| Simbol saja | Favicon, app icon, avatar sosial | 16px |
| Wordmark saja | Footer, dokumen, konteks yang sudah jelas | lebar 72px |

**Wordmark:** `gudangtool`, huruf kecil semua, Space Grotesk Medium, letter-spacing −0.02em. Tidak ada gimmick pada huruf — seluruh ide ditanggung simbol. Ini disengaja: wordmark yang "pintar" akan bersaing dengan simbol dan melemahkan keduanya.

**Ruang aman:** minimal setinggi huruf kapital "G" di semua sisi. Tidak ada elemen lain yang boleh masuk area itu.

**Versi warna:**
- Utama: ink `#12212E` di atas paper `#F6F3EE`
- Invers: paper di atas ink
- Aksen: paper di atas accent `#C24A18`
- Satu warna: hitam 100% untuk dokumen dan cetak

**Larangan:** jangan regangkan, jangan beri bayangan, jangan beri gradien, jangan ubah urutan simbol dan wordmark, jangan bungkus dengan bentuk pil.

---

## 4. Warna

| Token | Hex | Peran | Kontras |
|---|---|---|---|
| `paper` | `#F6F3EE` | Latar utama | — |
| `surface` | `#FFFDF9` | Kartu, panel | — |
| `ink` | `#12212E` | Teks utama, simbol | 14.8:1 di paper ✓ |
| `muted` | `#5C6A73` | Teks sekunder, metadata | 5.0:1 di paper ✓ |
| `line` | `#DCD3C4` | Garis, border kartu | Non-teks |
| `kraft` | `#C8A27A` | Label kategori, aksen hangat | Non-teks |
| `accent` | `#C24A18` | Tombol utama, penanda aktif | 4.9:1 dengan teks putih ✓ |
| `accent-strong` | `#9E3A12` | Tautan dan teks aksen | 6.2:1 di paper ✓ |
| `verified` | `#3E7C5A` | Badge **Diuji**, status terverifikasi | 4.95:1 dengan teks putih ✓ |

**Aturan pakai:**
- Oranye `accent` **hanya** untuk tombol utama, garis aktif, dan penanda kecil. Jangan dipakai sebagai latar halaman atau teks paragraf.
- `accent-strong` adalah satu-satunya oranye yang boleh dipakai untuk teks di atas paper.
- Hijau `verified` hanya untuk badge **Diuji**. Tidak untuk dekorasi, tidak untuk label harga.
- Tidak ada gradien. Tidak ada warna keempat di luar tabel ini tanpa alasan kuat.

**Mode gelap:** ditunda ke v2. Menambah mode gelap sekarang akan menggandakan pekerjaan QA tanpa manfaat yang sebanding untuk peluncuran.

---

## 5. Tipografi

| Peran | Font | Ukuran | Berat | Line-height |
|---|---|---|---|---|
| Display | Space Grotesk | 39–61px | 500 | 1.05 |
| H1 | Space Grotesk | 31px | 500 | 1.15 |
| H2 | Space Grotesk | 25px | 500 | 1.2 |
| H3 | Space Grotesk | 20px | 500 | 1.3 |
| Body | Inter | 16px | 400 | 1.6 |
| Body kecil | Inter | 14px | 400 | 1.55 |
| Label | JetBrains Mono | 11–12px | 500 | 1.2, tracking +0.08em, kapital |
| Tombol | Inter | 14px | 600 | 1 |

Ketiganya open-source. Ini bukan kebetulan: direktori yang membantu orang memilih tool sebaiknya tidak memakai font berbayar di identitasnya sendiri.

**Aturan:** mono hanya untuk label, kategori, angka, dan metadata. Jangan pernah untuk paragraf — huruf mono di badan teks membuat situs terasa seperti dokumentasi teknis, bukan katalog yang ramah.

---

## 6. Grid, spasi, bentuk

- **Grid:** 12 kolom, lebar maksimum konten 1120px, gutter 24px, margin halaman 24px (mobile) / 64px (desktop).
- **Spasi:** kelipatan 4 — 4, 8, 12, 16, 24, 32, 48, 64, 96.
- **Radius:** 2px untuk kontrol (tombol, input, chip), 4px untuk kartu. **Tidak ada bentuk pil.** Sudut tajam adalah bagian dari karakter gudang.
- **Border:** 1px `line`. Bayangan hanya muncul saat hover, tidak pernah dalam keadaan diam.
- **Bayangan hover:** `0 2px 0 rgba(18,33,46,0.08)` — keras dan pendek, bukan blur lembut khas SaaS.

---

## 7. Ikonografi

- Grid 24×24, stroke 2px, ujung dan sambungan datar, radius sudut 2px.
- Bahasa bentuk: kotak, rak, label, panah. Tidak ada ikon perkakas.
- Ikon tidak boleh mengandung lebih dari 3 elemen garis.
- Ikon status memakai `verified`; ikon navigasi memakai `ink`.
- Ikon dekoratif tidak diperlukan — setiap ikon harus punya fungsi.

**Set minimum untuk peluncuran:** kotak, rak, label, panah kanan, panah keluar, cari, centang, silang, filter, salin.

---

## 8. Komponen inti

### Kartu tool

- Latar `surface`, border 1px `line`, radius 4px.
- Strip label di atas: mono 11px kapital, latar `kraft`, teks `ink` — berisi nama kategori.
- Nama tool: Space Grotesk 20px.
- Satu kalimat fungsi: Inter 14px, `muted`, maksimal 2 baris.
- Baris label harga: `GRATIS`, `FREEMIUM`, `BUTUH AKUN` — semuanya netral (`ink`/`muted`). Hijau hanya dipakai untuk badge Diuji.
- Hover: naik 2px, bayangan keras muncul, tidak ada perubahan warna.
- Seluruh kartu adalah satu tautan. Tidak ada tombol "selengkapnya" di dalam kartu.

### Tombol

- Primer: latar `accent`, teks putih, radius 2px, padding 12×18px.
- Sekunder: transparan, border 1px `ink`, teks `ink`.
- Tidak ada tombol hantu tanpa border. Di latar paper, tombol tanpa border menghilang.

### Chip kategori

- Latar `kraft` 20%, border 1px `kraft`, teks mono 11px kapital.
- Radius 2px. Tidak ada bentuk pil.
- Keadaan aktif: latar `ink`, teks paper.

### Label harga

- Bentuk label stempel: border 1px, latar transparan, teks mono 10px kapital, warna `ink` atau `muted`.
- `GRATIS`, `FREEMIUM`, `BUTUH AKUN` semuanya netral. Hijau tidak dipakai di sini.
- Badge verifikasi (Diuji / Terdaftar / Berbayar) diatur di bagian 14.1 dan selalu terpisah dari label harga.

---

## 9. Motion

- Durasi 140ms, easing `cubic-bezier(0.2, 0, 0, 1)`.
- Hover kartu: translateY(−2px) + bayangan.
- Buka filter: geser 8px, fade 120ms.
- Tidak ada bounce, tidak ada parallax, tidak ada animasi masuk yang memaksa pengguna menunggu.
- Hormati `prefers-reduced-motion`.

---

## 10. Aplikasi

**Favicon:** simbol A disederhanakan — hanya peti dan satu garis rak. Pada 16px, detail rak kedua dihilangkan.

**OG image (1200×630):** paper, simbol di kiri atas, wordmark besar, tagline "Gudangnya tool digital.", dan satu baris label kategori di bagian bawah. Tanpa mockup dashboard.

**Avatar sosial:** latar `ink`, simbol paper, satu strip `accent` di bawah.

**Halaman 404 dan empty state:** gunakan ilustrasi garis rak kosong, bukan ilustrasi 3D.

---

## 11. Yang dilarang

- Ikon kunci pas, bor, palu, gerinda, atau tekstur logam.
- Gradien ungu-biru, ilustrasi blob 3D, mockup dashboard palsu.
- Bentuk pil untuk chip, badge, atau tombol.
- Bayangan blur lembut sebagai dekorasi.
- Foto stok orang bekerja di depan laptop.
- Wordmark yang dimiringkan, diberi outline, atau dijadikan pola.
- Lebih dari tiga warna aksen dalam satu halaman.

---

## 12. Design test

1. Di 16px, simbol masih dikenali sebagai rak/peti, bukan noda.
2. Orang yang melihat kartu tool paham status gratis **dan** label verifikasinya dalam **2 detik**, tanpa membaca paragraf.
3. Tidak ada yang menyebut situs ini "toko perkakas" setelah melihat halaman depan.
4. Halaman tetap terbaca jika seluruh warna dihapus — hierarki datang dari tipografi dan spasi, bukan dari warna.
5. Desainer lain bisa membuat halaman baru tanpa bertanya, hanya dengan brief ini.

---

## 13. Checklist handoff ke desainer

- [ ] Simbol A dalam SVG: versi penuh, versi 16px, versi satu warna
- [ ] Wordmark `gudangtool` dalam SVG (outline, bukan teks hidup)
- [ ] Empat lockup: horizontal, vertikal, simbol, wordmark
- [ ] Token warna sebagai CSS variables dan file JSON
- [ ] Skala tipografi sebagai kelas utilitas
- [ ] Set ikon 24px (10 ikon minimum)
- [ ] Komponen: kartu besar, kartu ringkas, tombol, chip, badge tier, label harga, input pencarian, baris ranking, slot iklan, pagination
- [ ] Template OG 1200×630
- [ ] Favicon set: 16, 32, 180, 512
- [ ] Halaman contoh: beranda, kategori, detail tool, 404, empty state

---

## 14. Komponen direktori (tambahan v1.1)

### 14.1 Badge verifikasi dan penanda komersial

| Label | Tampilan | Aturan |
|---|---|---|
| **Diuji** | Latar `verified` `#3E7C5A`, teks putih, ikon centang, mono 9px kapital, radius 1px | Hanya untuk tool yang benar-benar melewati QA |
| **Terdaftar** | Transparan, border 1px **putus-putus** `muted`, teks `muted`, mono 9px | Tidak boleh memakai hijau atau kata "gratis" |
| **Berbayar** | Latar `kraft` `#C8A27A`, teks `ink`, mono 9px | Selalu didahului kata "Placement" di halaman detail |

**Aturan:**
- Dua badge adalah tingkat verifikasi (Diuji, Terdaftar); Berbayar adalah penanda komersial yang menempel pada salah satunya.
- Hijau hanya untuk Diuji. Jangan dipakai untuk dekorasi, label harga, atau status lain.
- Oranye `accent` tidak boleh untuk badge Berbayar — oranye milik tombol aksi.
- Badge menempel pada nama tool, bukan di footer kartu.
- Jangan mengandalkan warna saja; teks label wajib ada.
- Badge Terdaftar memakai garis putus-putus karena statusnya sementara — begitu diuji, garisnya menjadi solid.

### 14.2 Kartu ringkas (mode direktori)

- Tinggi minimum 84px; logo 32px; nama 17px; deskripsi maksimal 2 baris.
- Baris badge setinggi 20px, selalu di bawah deskripsi.
- Tanpa gambar besar. Direktori butuh kepadatan, bukan galeri.
- Seluruh kartu adalah satu tautan; tidak ada tombol terpisah di dalamnya.
- Hover: naik 2px dan bayangan keras `0 2px 0 rgba(18,33,46,.08)`.

### 14.3 Baris ranking

- Kolom: peringkat (mono 24px), nama, kategori (mono 10px), metrik, badge, perubahan.
- Angka rata kanan dan memakai angka tabular.
- Peringkat 1–3 boleh diberi penanda tipis, bukan medali atau emas.
- Baris ranking tidak boleh memuat iklan di dalamnya.

### 14.4 Pencarian & filter

- Kolom pencarian 56px, border 1px `ink`, radius 2px, tanpa bayangan.
- Chip filter persegi (radius 2px), bukan pil.
- Filter aktif: latar `ink`, teks `paper`.
- Jumlah hasil ditampilkan di samping filter, bukan di dalam tombol.

### 14.5 Slot iklan

- Label `Iklan` mono 9px di atas unit, selalu terlihat.
- Maksimal 2 unit per halaman; tidak boleh di dalam kartu tool.
- Tinggi slot dicadangkan untuk mencegah layout shift.
- Iklan tidak boleh meniru kartu tool: border, label kategori, dan tombolnya harus berbeda.
- Tidak ada iklan di atas H1 pada tampilan mobile.

### 14.6 Keadaan kosong dan ambang

- Ranking belum cukup data: satu baris penjelasan, bukan daftar kosong.
- Kategori kurang dari 12 tool: halaman tidak diindeks.
- Koleksi kosong: disembunyikan, bukan ditampilkan dengan angka nol.
