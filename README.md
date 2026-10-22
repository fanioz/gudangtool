# gudangtool

Direktori tool digital berbahasa Indonesia dengan verifikasi bertingkat.

**Status:** pra-kode. Dokumen di `docs/` masih menjadi sumber kebenaran sampai situs dibangun.

## Mulai dari sini

1. [`AGENTS.md`](AGENTS.md) — aturan kerja yang mengikat semua agent dan kontributor
2. [`docs/09-decision-log.md`](docs/09-decision-log.md) — keputusan terbaru, termasuk D18 yang mengunci scope peluncuran
3. [`.scratch/launch-stage-0/map.md`](.scratch/launch-stage-0/map.md) — peta jalan menuju Stage 0

## Struktur

| Path | Isi |
|---|---|
| `docs/` | Dokumen kanonis: brand, copy, skema, SEO, stack |
| `docs/agents/` | Konfigurasi skill: issue tracker, label triage, dokumen domain |
| `.scratch/` | Issue dan spec dalam markdown, per fitur |
| `src/`, `scripts/`, `public/` | Belum ada — dibuat oleh tiket scaffold |

## Stage 0

Situs statis Astro, tanpa database, tanpa API runtime. Data tool sebagai file JSON, diverifikasi skema saat build. Deploy lewat GitHub Actions ke VPS yang menyajikan lewat Caddy.

Target peluncuran: 50 halaman, kategori Desain terindeks dengan 15 tool berlabel Diuji.
