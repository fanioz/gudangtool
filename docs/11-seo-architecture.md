# Gudangtool — Arsitektur SEO & Tipe Halaman v1.0

**Tanggal:** 22 Oktober 2026
**Dasar:** `08-pivot-memo.md` · `01-brand-brief.md` v2.0 · `04-category-and-tool-copy.md` v2.0
**Tujuan:** menentukan halaman apa yang dibuat, kapan diindeks, dan apa yang tidak boleh dibuat.

---

## 1. Prinsip

Skala SEO hanya aman jika setiap halaman yang diindeks punya **data atau fungsi yang tidak ada di tempat lain**. Menambah halaman tanpa itu adalah cara tercepat terkena kebijakan *scaled content abuse*.

Tiga aturan yang mengikat:

1. **Satu halaman, satu niat pencarian.** Jangan membuat halaman yang bersaing dengan halaman sendiri.
2. **Ambang sebelum indeks.** Halaman tipis ditahan sampai isinya cukup, bukan dipublikasikan lalu diperbaiki.
3. **Naik bertahap.** Tambah 300–500 halaman per batch, pantau rasio indeks, baru lanjut.

---

## 2. Tipe halaman

| Tipe | Pola URL | Diindeks jika | Prioritas |
|---|---|---|---|
| Tool — Diuji | `/tool/{slug}` | Selalu, setelah lulus QA | Tinggi |
| Tool — Terdaftar | `/tool/{slug}` | Punya minimal 2 data unik (platform + alternatif yang sudah diuji); jika tidak, `noindex` | Rendah |
| Kategori | `/kategori/{slug}` | Minimal 12 tool | Tinggi |
| Lorong | `/kategori/{slug}/{lorong}` | Minimal 8 tool | Sedang |
| Koleksi | `/koleksi/{slug}` | Minimal 10 tool dan niat pencarian berbeda dari kategori | Sedang |
| Ranking | `/ranking/{yyyy-mm}` | Minimal 20 tool berperingkat | Sedang |
| Perbandingan | `/bandingkan/{a}-vs-{b}` | Keduanya berlabel Diuji dan tabel batasnya lengkap | Rendah |
| Alternatif | `/alternatif/{slug}` | Tool sumber Diuji dan minimal 5 alternatif berdata | Sedang |
| Use case | `/untuk/{kebutuhan}` | Minimal 8 tool yang benar-benar cocok | Sedang |
| Artikel | `/artikel/{slug}` | Tulisan asli, minimal 600 kata, bukan ringkasan vendor | Sedang |
| Submit | `/submit` | Selalu | Rendah |
| Kebijakan privasi | `/privasi` | `noindex` | — |

**Halaman yang dilarang dibuat:**
- Kategori kosong atau kategori dengan 1–2 tool.
- Perbandingan otomatis untuk semua pasangan tool.
- Halaman "alternatif" untuk tool yang belum diuji.
- Terjemahan mesin tanpa penyuntingan.
- Halaman tag yang hanya mengulang kategori.

---

## 3. Pola title & meta

| Tipe | Title | Meta |
|---|---|---|
| Tool Diuji | `{Nama} — {fungsi singkat} \| Gudangtool` | `{Nama} adalah {fungsi}. {Status}, {syarat akun}. Batas gratis dan alternatifnya kami catat.` |
| Tool Terdaftar | `{Nama} — {fungsi singkat} \| Gudangtool` | `{Nama} terdaftar di Gudangtool dan belum diuji. Lihat fungsi, platform, dan alternatif yang sudah diuji.` |
| Kategori | `{Kategori} — Tool {bidang} \| Gudangtool` | `{n} tool {bidang}: {3 contoh kebutuhan}. Status gratis dan label verifikasinya tercantum di setiap kartu.` |
| Lorong | `{Kebutuhan} — {n} Tool Gratis \| Gudangtool` | `Tool untuk {kebutuhan}, dengan catatan batas gratis dan label sudah diuji atau belum.` |
| Koleksi | `{Nama koleksi} — {n} Tool \| Gudangtool` | `Kumpulan tool yang {syarat}. Dihitung ulang setiap katalog berubah.` |
| Ranking | `Ranking Tool {Bulan Tahun} \| Gudangtool` | `Tool paling sering dibuka bulan ini, disusun dari data pemakaian di Gudangtool. Tidak ada posisi yang dijual.` |
| Perbandingan | `{A} vs {B} — Perbedaan dan Batas Gratis \| Gudangtool` | `Perbandingan {A} dan {B}: batas gratis, kebutuhan akun, platform, dan mana yang lebih cocok untuk {kebutuhan}.` |
| Alternatif | `{n} Alternatif {Nama} yang Sudah Diuji \| Gudangtool` | `Alternatif {Nama} dengan batas gratis yang sudah kami catat. Cocok kalau {kebutuhan}.` |
| Use case | `Tool Gratis untuk {Kebutuhan} \| Gudangtool` | `{n} tool untuk {kebutuhan}, lengkap dengan status gratis dan batasnya.` |

**Larangan:** kata "gratis" di title/meta halaman **Terdaftar**; kata "terbaik", "terlengkap", "nomor satu" di semua halaman.

---

## 4. Aturan internal linking

- Setiap halaman tool menaut ke: kategori induk, dua alternatif, satu koleksi relevan.
- Setiap kategori menaut ke 8–12 tool teratas dan 2–3 koleksi terkait.
- Setiap koleksi menaut ke kategori induk dan minimal 6 tool.
- Tidak ada halaman yang berjarak lebih dari **3 klik** dari beranda.
- Tidak ada halaman yatim. Sebelum publish, pastikan minimal satu halaman lain menaut ke halaman baru.
- Ranking menaut ke halaman tool, bukan langsung ke situs eksternal.

---

## 5. Ambang dan bertahap

| Batch | Jumlah halaman | Syarat lanjut |
|---|---|---|
| 1 | 300 | Rasio indeks ≥60% dalam 4 minggu |
| 2 | +700 (total 1.000) | Rasio indeks ≥65%, impresi naik |
| 3 | +2.000 (total 3.000) | Rasio indeks ≥70%, tidak ada penalti manual |

Jika rasio indeks batch pertama di bawah 60%, **jangan tambah halaman**. Perbaiki konten yang ada: tambah data unik, perbaiki internal linking, atau gabungkan halaman yang tumpang tindih.

---

## 6. Data unik minimum per halaman

Agar tidak dianggap halaman tipis, setiap halaman tool wajib punya minimal **tiga** dari daftar ini:

- Tabel batas gratis (akun, kuota, watermark, ekspor).
- Harga dalam rupiah dan tanggal kurs.
- Platform yang didukung.
- Tanggal verifikasi yang nyata.
- Dua alternatif dengan alasan.
- Satu catatan pemakaian atau peringatan.

Halaman Terdaftar yang tidak punya minimal dua data unik **tidak diindeks**.

---

## 7. Structured data

- `SoftwareApplication` pada halaman tool: nama, kategori, sistem operasi, dan `offers` **hanya jika status gratis benar**.
- `BreadcrumbList` pada semua halaman.
- `ItemList` pada kategori dan koleksi.
- `FAQPage` hanya jika pertanyaan dan jawaban benar-benar ada di halaman.
- **Jangan** memakai `aggregateRating` tanpa ulasan nyata. Rating palsu adalah pelanggaran kebijakan sekaligus risiko hukum.

---

## 8. Pengukuran

| Metrik | Alat | Ambang sehat |
|---|---|---|
| Halaman terindeks | Search Console | ≥60% dari halaman yang diizinkan |
| Impresi | Search Console | Naik tiap bulan |
| CTR | Search Console | ≥2% untuk halaman tool |
| Posisi rata-rata | Search Console | ≤30 untuk long-tail |
| Halaman "discovered, not indexed" | Search Console | <20% dari total |
| Pencarian tanpa hasil | Analytics internal | <10% |

---

## 9. Yang tidak boleh dilakukan

- Mengunggah 10.000 halaman sekaligus.
- Menyalin deskripsi vendor.
- Membuat kategori baru hanya karena ada satu tool.
- Membuat halaman perbandingan tanpa data batas yang lengkap.
- Menaruh iklan di dalam kartu tool atau di atas H1 pada mobile.
- Menampilkan angka trafik tanpa sumber.
- Menjual posisi ranking.
