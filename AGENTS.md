# AGENTS.md — Gudangtool

**Baca dokumen ini sebelum menyentuh kode atau konten.** Aturan di sini mengikat semua AI agent yang bekerja di repo ini.

---

## 1. Konteks proyek

Gudangtool adalah direktori tool digital berbahasa Indonesia dengan verifikasi bertingkat. Situs dibangun **statis**: Astro menghasilkan HTML, Caddy menyajikan file, Cloudflare menyimpan cache. Tidak ada database, tidak ada API runtime, tidak ada Docker.

Stack: **Astro 5 + JSON content collections + Zod + Pagefind + Caddy + Cloudflare Free + GitHub Actions**.

---

## 2. Urutan baca

1. `AGENTS.md` (dokumen ini)
2. `docs/09-decision-log.md` — keputusan terbaru dan hal yang sudah kedaluwarsa
3. `docs/01-brand-brief.md` — positioning dan pilar
4. `docs/11-seo-architecture.md` — tipe halaman dan aturan indeks
5. `docs/12-tech-stack.md` — arsitektur dan alasan di baliknya
6. `docs/04-category-and-tool-copy.md` — template copy dan tiga keadaan tool
7. `docs/14-repo-spec.md` — blueprint teknis rinci

Jika dua dokumen bertentangan, urutan prioritasnya: decision log → repo spec → dokumen lain.

---

## 3. Sepuluh aturan yang tidak bisa dilanggar

1. **Jangan pernah menulis "gratis" pada entri `tier: terdaftar`** — di JSON, judul, deskripsi, meta, atau badge.
2. **`tier` hanya boleh `diuji` atau `terdaftar`.** `kandidat` hanya status internal di antrean impor, tidak pernah tayang.
3. **Entri `diuji` wajib punya** `verified_at`, `price_status`, `limits`, `why`, `fit`, dan `not_fit`. Tanpa itu, build harus gagal.
4. **Entri `terdaftar` wajib `null`** pada semua field klaim: `price_status`, `requires_account`, `limits`, `why`, `fit`, `not_fit`, `verified_at`.
5. **Peringkat tidak dijual.** Placement boleh, tetapi selalu berlabel dan tidak mengubah tier atau ranking.
6. **Indeks dihitung kode**, bukan diputuskan editor. Halaman di bawah ambang: `noindex, follow` dan tidak masuk sitemap.
7. **Jangan membuat tipe halaman baru** di luar daftar `docs/11-seo-architecture.md`.
8. **Jangan menyalin deskripsi vendor.** Tulis ulang dalam bahasa sendiri.
9. **Jangan menambah layanan baru** (database, Docker, SSR, API, framework client-side) tanpa keputusan tertulis di `docs/09-decision-log.md`.
10. **Jangan mengubah token brand, logo, atau nada copy** tanpa persetujuan pemilik proyek.

---

## 4. Struktur repo

```
/
├── AGENTS.md
├── docs/                     # dokumen kanonis
├── src/
│   ├── content/
│   │   ├── tools/            # satu JSON per tool
│   │   ├── categories/
│   │   ├── collections/
│   │   └── rankings/
│   ├── pages/
│   │   ├── index.astro
│   │   ├── tool/[slug].astro
│   │   ├── kategori/[slug].astro
│   │   ├── koleksi/[slug].astro
│   │   ├── ranking/[periode].astro
│   │   ├── artikel/[slug].astro
│   │   ├── submit.astro
│   │   └── 404.astro
│   ├── components/
│   └── layouts/
├── public/
│   ├── favicon/
│   ├── og/
│   └── ads.txt
├── scripts/                  # validasi konten, ranking, link check
└── .github/workflows/
```

---

## 5. Cara bekerja

- **Satu tugas per branch dan per PR.** Jangan mencampur refactor, konten, dan infrastruktur dalam satu PR.
- **Jangan menyentuh file di luar lingkup tugas.** Jika perlu perubahan lain, buka issue terpisah.
- **Konten:** satu file JSON per tool. Jangan menulis ulang banyak file sekaligus tanpa skrip.
- **Sebelum PR:** jalankan `check`, `validate:content`, dan `build`. Ketiganya wajib lulus.
- **Jika aturan tidak jelas:** berhenti dan buka issue. Jangan mengarang keputusan.
- **Commit message:** `feat:`, `fix:`, `content:`, `docs:`, `chore:` — satu kalimat, bahasa Indonesia atau Inggris, konsisten.

---

## 6. Definisi selesai

Sebuah pekerjaan dianggap selesai jika:

- [ ] `npm run check` lulus tanpa error.
- [ ] `npm run validate:content` lulus.
- [ ] `npm run build` menghasilkan halaman tanpa broken link internal.
- [ ] Tidak ada halaman `terdaftar` yang memuat kata "gratis" atau tabel batas.
- [ ] Lighthouse mobile: performa ≥85, SEO 100, aksesibilitas ≥95.
- [ ] Tidak ada layout shift dari iklan atau gambar.
- [ ] Perubahan UI disertai tangkapan layar di PR.

---

## 7. Kepemilikan area

| Area | Boleh diubah oleh | Catatan |
|---|---|---|
| `src/content/tools/**` | Content agent | Satu file per PR untuk koreksi; impor massal lewat skrip |
| `src/components/**`, `src/pages/**` | Frontend agent | Ikuti token dan komponen di `docs/02` |
| `.github/workflows/**`, `scripts/**` | Infra agent | Jangan menambah service baru |
| `docs/**` | Siapa pun | Perubahan keputusan wajib dicatat di `09-decision-log.md` |
| `public/ads.txt`, halaman legal | SEO agent | Ikuti kebijakan AdSense |

Jika dua agent perlu mengubah file yang sama, salah satu harus menunggu. Jangan menyelesaikan konflik dengan menimpa.

---

## 8. Yang dilarang

- Menambahkan database, Docker, SSR, atau API route untuk konten.
- Memakai framework client-side untuk halaman yang bisa statis.
- Membuat halaman kategori, koleksi, atau perbandingan di bawah ambang.
- Menulis angka trafik atau popularitas yang tidak berasal dari data nyata.
- Menaruh iklan di dalam kartu tool atau di atas H1 pada mobile.
- Menyalin teks dari situs tool tanpa menulis ulang.
- Mengubah slug tanpa menambahkan redirect 301.
- Menghapus riwayat atau tanggal verifikasi untuk merapikan tampilan.

---

## 9. Jika ragu

1. Cari di `docs/09-decision-log.md`.
2. Jika tidak ada, buka issue dengan opsi dan rekomendasi.
3. Jangan mengubah arsitektur atau brand berdasarkan asumsi sendiri.
4. Setelah keputusan diambil, catat di decision log sebelum implementasi.

---

## Agent skills

### Issue tracker

Issues and specs live as markdown files under `.scratch/<feature-slug>/`. See `docs/agents/issue-tracker.md`.

### Triage labels

Default five-role vocabulary, label strings identical to role names. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `GLOSSARY.md` and `docs/adr/` at the repo root. See `docs/agents/domain.md`.
