# Gudangtool — Spesifikasi Repo v1.1

**Tanggal:** 23 Oktober 2026
**Menggantikan:** v1.0 (skema tool tanpa `observed_at`/`observed_by`, `internal_note` sebagai string, `alternatives` wajib ≥2)
**Dasar:** `12-tech-stack.md` v3.0 · `11-seo-architecture.md` · `04-category-and-tool-copy.md` v2.0 · D18 · D19
**Untuk:** AI agent pembangun dan reviewer manusia.

---

## 1. Tujuan

Membangun situs statis yang:

- menghasilkan HTML untuk semua halaman yang diindeks;
- memvalidasi integritas data saat build;
- tidak membutuhkan database atau API runtime;
- bisa dipindahkan ke host lain tanpa menulis ulang template.

**Non-goals Stage 0:** akun pengguna, pencarian real-time berbasis server, event klik presisi, admin UI, mode gelap, versi bahasa Inggris.

---

## 2. Arsitektur

```
Repo (JSON + Astro)
   ↓ GitHub Actions: check → validate → build → pagefind
   ↓ rsync
VPS: /var/www/gudangtool/releases/{timestamp}
   ↓ symlink current
Caddy (static file server)
   ↓
Cloudflare (cache, DNS, Access)
```

Tidak ada proses yang membaca database saat request. Tidak ada Node.js yang berjalan di VPS.

---

## 3. Struktur folder

```
src/
  content/
    config.ts
    tools/*.json
    categories/*.json
    collections/*.json
    rankings/*.json
  layouts/
    BaseLayout.astro
    ToolLayout.astro
  components/
    ToolCard.astro
    TierBadge.astro
    PriceBadge.astro
    LimitsTable.astro
    UnknownList.astro
    SearchBar.astro
    FilterBar.astro
    RankRow.astro
    AdSlot.astro
    Breadcrumbs.astro
    EmptyState.astro
  pages/
    index.astro
    tool/[slug].astro
    kategori/[slug].astro
    kategori/[slug]/[lorong].astro
    koleksi/[slug].astro
    ranking/[periode].astro
    artikel/[slug].astro
    submit.astro
    privasi.astro
    ketentuan.astro
    kontak.astro
    cari.astro
    404.astro
public/
  favicon/
  og/
  ads.txt
scripts/
  validate-content.ts
  check-links.ts
  build-ranking.ts
```

---

## 4. Skema tool

### Field

| Field | Tipe | Wajib | Aturan |
|---|---|---|---|
| `name` | string | ya | Nama resmi tool |
| `slug` | string | ya | kebab-case, unik, tidak berubah tanpa redirect |
| `tier` | enum | ya | `diuji` atau `terdaftar` |
| `placement` | boolean | ya | Default `false` |
| `category` | string | ya | Harus ada di `categories/` |
| `subcategory` | string/null | tidak | Harus ada jika diisi |
| `function` | string | ya | Maksimal 160 karakter, satu kalimat |
| `platform` | array | ya | Minimal 1 dari `web`, `desktop`, `mobile` |
| `url` | string | ya | HTTPS |
| `added_at` | date | ya | `YYYY-MM-DD` |
| `verified_at` | date/null | kondisional | Wajib untuk `diuji`; null untuk `terdaftar` |
| `observed_at` | date/null | kondisional | Wajib untuk `diuji`; null untuk `terdaftar`. Boleh lebih awal dari `verified_at` |
| `observed_by` | string/null | kondisional | `"agent"` atau nama orang; wajib untuk `diuji`, null untuk `terdaftar` |
| `price_status` | enum/null | kondisional | `gratis`, `freemium`, `butuh-akun`; null untuk `terdaftar` |
| `requires_account` | boolean/null | kondisional | Wajib untuk `diuji`; null untuk `terdaftar` |
| `limits` | object/null | kondisional | Wajib untuk `diuji`; null untuk `terdaftar` |
| `why` | string/null | kondisional | Wajib untuk `diuji`; null untuk `terdaftar` |
| `fit` | string/null | kondisional | Wajib untuk `diuji`; null untuk `terdaftar` |
| `not_fit` | string/null | kondisional | Wajib untuk `diuji`; null untuk `terdaftar` |
| `alternatives` | array slug | ya | Setiap item harus `diuji`. Boleh `[]` bila belum ada tool `diuji` yang sebanding |
| `internal_note` | object/null | tidak | Tidak pernah dirender |

### Objek `limits`

| Field | Tipe | Wajib |
|---|---|---|
| `account` | string | ya |
| `quota` | string | ya |
| `watermark` | string | ya |
| `export` | string | ya |
| `storage` | string | tidak |

Nilai yang tidak ada batasnya ditulis "Tidak ada", bukan dikosongkan. Nilai yang belum bisa diperiksa tanpa akun ditulis "Belum diperiksa".

### Objek `internal_note`

Jejak audit, tidak pernah dirender.

| Field | Tipe | Wajib | Aturan |
|---|---|---|---|
| `sources` | array `{field, url}` | ya untuk `diuji` | Satu entri per klaim yang punya sumber; `field` memakai path bertitik, mis. `limits.quota` |
| `evidence` | array string | ya untuk `diuji` | Path relatif bukti tangkapan layar, mis. `excalidraw/2026-10-22-01.png` |
| `note` | string | tidak | Catatan bebas, mis. "klaim vendor bertentangan dengan hasil uji" |

### Validasi lintas file

- `slug` unik di seluruh katalog.
- `category` dan `subcategory` ada.
- Setiap `alternatives` ada, bukan dirinya sendiri, dan bertier `diuji`. Array kosong diperbolehkan.
- `tier: diuji` gagal build jika `observed_at`, `observed_by`, `verified_at`, `limits`, `price_status`, `requires_account`, `why`, `fit`, atau `not_fit` kosong.
- `tier: diuji` gagal build jika `internal_note.sources` atau `internal_note.evidence` kosong.
- `placement: true` wajib punya penanda di halaman.
- Tidak ada kata "gratis" pada teks entri `terdaftar` (cek case-insensitive pada `function`, `why`, `fit`, `not_fit`).
- Tanggal tidak di masa depan.

---

## 5. Skema kategori, koleksi, ranking

### Kategori

| Field | Tipe | Wajib |
|---|---|---|
| `name` | string | ya |
| `slug` | string | ya |
| `description` | string | ya |
| `intro` | string | ya |
| `order` | number | ya |
| `parent` | string/null | tidak |
| `seo_title` | string | ya |
| `seo_description` | string | ya |

### Koleksi

| Field | Tipe | Wajib |
|---|---|---|
| `name` | string | ya |
| `slug` | string | ya |
| `description` | string | ya |
| `rule` | object | ya |
| `seo_title` | string | ya |
| `seo_description` | string | ya |

`rule` hanya boleh memakai field yang deterministik: `price_status`, `requires_account`, `platform`, `limits.watermark`. Koleksi hanya menghitung tool `diuji`.

### Ranking

| Field | Tipe |
|---|---|
| `period` | `YYYY-MM` |
| `generated_at` | date |
| `source` | `caddy` atau `cloudflare` |
| `entries` | array `{ slug, opens, position }` |

Hanya tool `diuji` yang boleh masuk. Minimal 100 pembukaan per tool.

---

## 6. Matriks halaman

| Halaman | URL | Sumber | Diindeks jika | Sitemap |
|---|---|---|---|---|
| Beranda | `/` | kategori + tool | Selalu | Ya |
| Tool Diuji | `/tool/{slug}` | tool | `tier = diuji` | Ya |
| Tool Terdaftar | `/tool/{slug}` | tool | Minimal 2 data unik | Ya |
| Kategori | `/kategori/{slug}` | kategori + tool | ≥12 tool | Ya |
| Lorong | `/kategori/{slug}/{lorong}` | subkategori | ≥8 tool | Ya |
| Koleksi | `/koleksi/{slug}` | rule | ≥10 tool | Ya |
| Ranking | `/ranking/{YYYY-MM}` | ranking | ≥20 entri | Ya |
| Artikel | `/artikel/{slug}` | artikel | ≥600 kata | Ya |
| Submit | `/submit` | statis | Selalu | Ya |
| Cari | `/cari` | Pagefind | Tidak | Tidak |
| 404 | `/404` | statis | Tidak | Tidak |

Halaman yang tidak lolos: `<meta name="robots" content="noindex, follow">`.

---

## 7. Template dan komponen

### ToolCard

- Strip kategori (mono 9–10px, latar `kraft`).
- Nama tool (Space Grotesk 17–18px).
- Fungsi maksimal 2 baris.
- Baris badge: tier + label harga.
- Seluruh kartu satu tautan.

### TierBadge

- `diuji`: solid `verified`, teks putih, ikon centang.
- `terdaftar`: border putus-putus `muted`, teks `muted`.
- `berbayar`: latar `kraft`, teks `ink`, selalu didahului kata "Placement" di halaman detail.

### LimitsTable

Hanya dirender untuk `tier = diuji`. Lima baris: akun, kuota, watermark, ekspor, penyimpanan.

### UnknownList

Hanya dirender untuk `tier = terdaftar`. Empat baris, semuanya "Belum diperiksa". Tidak boleh ada nilai lain.

### AdSlot

- Label "Iklan" selalu terlihat.
- Tinggi tetap; tanpa label tidak boleh dirender.
- Maksimal 2 per halaman.
- Tidak dirender pada halaman `terdaftar` dengan kurang dari 3 data unik.

---

## 8. SEO implementasi

- Satu `h1` per halaman.
- Canonical ke URL sendiri (tanpa trailing slash).
- Title dan meta mengikuti pola di `11-seo-architecture.md`.
- Sitemap index: `sitemap.xml` → `sitemap-tools.xml`, `sitemap-categories.xml`, `sitemap-collections.xml`, `sitemap-articles.xml`.
- `lastmod` diambil dari `verified_at` atau `added_at`, bukan waktu build.
- `robots.txt` melarang `/cari` dan halaman `noindex`.
- JSON-LD: `SoftwareApplication` hanya untuk `diuji`; `BreadcrumbList` semua halaman; `ItemList` kategori/koleksi.
- `offers` pada schema hanya jika `price_status = gratis`; jangan memakai harga 0 untuk freemium.
- Redirect 301 untuk perubahan slug; 410 untuk tool yang dihapus permanen.
- Internal link: setiap tool → kategori + 2 alternatif + 1 koleksi.

---

## 9. Pencarian

- Pagefind dijalankan setelah build, indeks disimpan di `dist/pagefind`.
- Halaman `/cari` memakai island kecil; hasil tidak diindeks.
- Placeholder dan empty state mengikuti `03-homepage-copy.md`.
- Jika hasil kosong, tampilkan tautan "Titipkan tool".

---

## 10. Performa dan aksesibilitas

**Budget:**

| Aset | Batas |
|---|---|
| HTML per halaman | ≤120 KB (uncompressed) |
| CSS | ≤30 KB (compressed) |
| JS awal | ≤30 KB (compressed) |
| Font | maksimal 2 file, ≤120 KB total, woff2 |
| Gambar raster | ≤100 KB per gambar |

**Target lapangan:** LCP ≤2,5 dtk, INP ≤200 ms, CLS ≤0,1.

**Aksesibilitas:** kontras teks ≥4,5:1, fokus terlihat, skip link, landmark, heading berurutan, `prefers-reduced-motion`, dan hasil pencarian diumumkan lewat `aria-live`.

---

## 11. Build, CI, dan deploy

**Script yang wajib ada:**

```
dev
build
preview
check
validate:content
check:links
```

**CI pada PR:** install → check → validate:content → build → check:links. Lighthouse dijalankan pada PR yang mengubah UI.

**Deploy pada `main`:**

1. Build di GitHub Actions.
2. `rsync` ke `/var/www/gudangtool/releases/{timestamp}`.
3. Ganti symlink `current`.
4. Simpan 3 release terakhir.
5. Purge cache Cloudflare.

**Rollback:** ganti symlink ke release sebelumnya. Tidak ada build ulang.

---

## 12. Caddy

- Menyajikan `current/` sebagai root.
- HTTPS otomatis, HTTP/3, Brotli/gzip.
- `/_astro/*`: `Cache-Control: public, max-age=31536000, immutable`.
- HTML: `public, max-age=0, s-maxage=1800, stale-while-revalidate=86400`.
- 404 kustom.
- Header keamanan: HSTS, `X-Content-Type-Options`, `Referrer-Policy`.
- Tidak ada reverse proxy API di Stage 0.

---

## 13. Kriteria penerimaan

- [ ] Semua halaman yang diindeks punya HTML lengkap tanpa JavaScript.
- [ ] Build gagal jika aturan tier dilanggar.
- [ ] Tidak ada halaman `terdaftar` dengan kata "gratis" atau tabel batas.
- [ ] Sitemap hanya memuat halaman yang lolos ambang.
- [ ] `npm run check:links` nol tautan mati.
- [ ] Lighthouse mobile: performa ≥85, SEO 100, aksesibilitas ≥95.
- [ ] Deploy dan rollback diuji di VPS.
- [ ] Backup artefak release tersimpan.

---

## 14. Keputusan terbuka

1. Form submission: GitHub Issue Form atau Tally.
2. Alamat email pengirim dan fallback.
3. Repo publik atau privat.
4. Sumber ranking: access log Caddy atau ekspor Cloudflare.
