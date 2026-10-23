# Ticket: How is the Astro scaffold structured?

Type: grilling
Status: resolved

## Question

With the stack locked (Astro 5 + JSON content collections + Zod + Pagefind), how is the project actually organised — component decomposition, CSS/token delivery, search approach at 50 pages, and font hosting?

## Detail

**Sudah terkunci — tidak boleh diputuskan ulang di sini:**

- Kerangka direktori: `14-repo-spec.md` §4 (pages, components, layouts, content, public, scripts, workflows).
- Model konten: satu JSON per tool, schema v1.1 (D19); gerbang validasi D20.
- Tanpa framework client-side untuk halaman statis; tanpa database/SSR/API (AGENTS.md §8).
- Identitas visual: `02-visual-identity.md` (token warna, skala tipografi, komponen inti §8/§14, motion §9).
- Pipeline: sudah hidup; langkah build tinggal diganti `npm ci && npm run build` (tiket 11).
- `12-tech-stack.md` tabel: Pencarian = **Pagefind (indeks statis)**; urutan build menyertakan langkah `pagefind`.

**Empat keputusan yang terbuka:**

1. **CSS delivery** — bagaimana token `02` menjadi style: (a) satu stylesheet global dengan custom properties + kelas semantik; (b) token di satu file + `<style>` scoped per komponen Astro; (c) utility framework (Tailwind — tanpa runtime, tapi dependensi build baru). Sendi dengan fog "Design token → CSS delivery" dan budget font ≤120 KB.
2. **Font** — self-host subset WOFF2 vs Google Fonts CDN (yang dipakai semua pratinjau). Sendi dengan postur privasi ticket 08 (Cloudflare WA + Pagefind, daftar pihak ketiga bertanggal) dan Lighthouse mobile ≥85 (DoD).
3. **Pencarian di 50 halaman** — Pagefind terkunci di `12-tech-stack.md`, tetapi fog map menduga di 50 halaman mesinnya bisa berlebihan. Alternatifnya: indeks JSON ~10–15 KB dibangun saat build + filter vanilla JS (butuh entri decision log karena mengubah tabel terkunci). Pertanyaannya bukan "Pagefind atau tidak" saja, tapi kapan Pagefind masuk akal: sekarang, atau setelah katalog tumbuh melewati ratusan.
4. **Dekomposisi komponen** — daftar minimal yang diturunkan dari matriks halaman (ToolCard, CategoryCard, Badge/PriceLabel, RankRow, CollectionCard, Header, Footer, SearchBox, AdSlot, LabelExplainer, SubmitBand …). Pemilik bereaksi, bukan mengarang dari nol.

**Batasan penerimaan (DoD AGENTS.md §6):** Lighthouse mobile performa ≥85, SEO 100, aksesibilitas ≥95; tanpa layout shift dari iklan/gambar; `check`, `validate:content`, `build`, `check:links` lulus.

**Konsekuensi keputusan:** struktur komponen dan CSS menentukan bentuk semua PR konten berikutnya (tiket 07: impor batch), dan keputusan search menentukan apakah `12-tech-stack.md` perlu revisi + entri decision log sebelum scaffold pertama.

## Answer

**2026-10-23 — sesi grilling langsung dengan pemilik; keempat rekomendasi diterima semua.** Tercatat sebagai **D26** di `docs/09-decision-log.md`.

| Keputusan | Pilihan |
|---|---|
| CSS | Token di `src/styles/tokens.css` + `<style>` scoped per komponen Astro |
| Font | Self-host subset WOFF2 ≤120 KB (tanpa Google Fonts CDN) |
| Pencarian | Pagefind tetap; Lighthouse <85 mobile adalah pemicu revisit dengan entri decision log baru |
| Komponen | Set launch (Header, Footer, SearchBox, ToolCard, CategoryCard, Badge & PriceLabel, LabelExplainer, SubmitBand) + kondisional (RankRow, CollectionCard, AdSlot); tanpa Pagination |

Gerbang scaffolding dibuka lebih awal oleh pemilik pada sesi yang sama — fog "Scaffolding", "Design token → CSS delivery", dan "Search at 50 pages" selesai ketiganya. Sisa pekerjaan menuju build: tidak ada keputusan struktur yang tertahan; yang tersisa dari peta adalah keputusan milik pemilik di tiket 10, 11, 13, dan 14.
