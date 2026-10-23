# Ticket: Do `/ranking` and `/koleksi` ship at 50 tools?

Type: grilling
Status: resolved
Blocked by: 10

## Question

At Stage 0, do the `/ranking` and `/koleksi` pages exist — and if they exist with no qualifying data, what do they say?

## Detail

The map recorded this as fog: "Native thresholds (≥10 tool collection, ≥20 ranked tool, ≥100 opens) may make both unshippable at this size." The thresholds are known and the launch catalogue size is known, so the question is sharp enough to decide.

**The facts**

- Ranking needs ≥20 ranked tools, each with ≥100 opens in a week. At launch: 15 Diuji tools, zero page opens, zero click data (`12-tech-stack.md` §8 — pageview only).
- A collection needs ≥10 tools under a deterministic rule. Ticket 05 locked the `terdaftar` data floor and ticket 12 locked the schema, so a collection's membership is computable — but the count at launch depends on which claims the 15 Diuji tools actually have.
- `11-seo-architecture.md` treats ranking and collection pages as indexable page types, with thresholds below which they go `noindex, follow` and leave the sitemap (AGENTS.md rule 6).
- Copy v2 §6 already holds the honest empty state for ranking: "Ranking minggu ini belum tersedia. Angka ditampilkan setelah sampelnya cukup." Copy v2 §7 and 02 §14.6 require empty collections to be hidden rather than shown with a zero.

**Why it needs its own decision**

Two sub-questions that the homepage choice depends on:

1. **Existence**: does the page exist at Stage 0 (thin, `noindex`, stating its threshold), or does it not exist until the data arrives? A page that exists but is `noindex` and states its threshold is a promise; a page that appears later is a change to the site's shape.
2. **Collection eligibility at 50 tools**: several of the four copy-v2 collections (Gratis tanpa akun, Tanpa watermark, Jalan di browser, Tanpa kartu kredit) may or may not clear ≥10 Diuji tools at launch. If none clear, `/koleksi` has nothing to list, and the honest answer is that the page does not ship — not that it ships empty.

**Coupling to ticket 10**: the homepage variant decides whether the nav and footer link to these pages at all. Variant B (rack without a queue) drops both links; variants A and C keep "Ranking". A homepage link to a page that does not exist is a dead internal link, and `13-launch-plan.md` line 114 forbids dead links in the first 50 pages. So this ticket is blocked by ticket 10, and its answer feeds the nav-gating logic in D20 gate 8.

**Not decided here**: the exact rule set for each collection, and whether a collection may include `terdaftar` tools. Copy v2 §7 restricts claim-based collections to Diuji tools only; ticket 05 already governs that elsewhere.

## Answer

**2026-10-23 — pemilik memilih (a): keduanya terbit di Stage 0 sebagai halaman `noindex, follow`, di luar sitemap.**

- `/ranking` berisi penjelasan ambang + kalimat "belum cukup data" (copy v2 §6); `/koleksi` sama, dengan aturan 02 §14.6 (koleksi yang belum memenuhi ≥10 tool tidak ditampilkan sebagai kartu — halaman menjelaskan ambangnya).
- Aturan AGENTS #6 (indeks dihitung kode) otomatis menangani status indeks; tidak ada manifest manual.
- Konsekuensi nav: tautan "Ranking" di varian A selalu punya tujuan; tautan "Koleksi" hanya muncul bila minimal satu koleksi memenuhi ambang (keputusan 02 §14.6 tetap berlaku).
- RankRow & CollectionCard masuk komponen kondisional D26; keduanya dirender dalam keadaan "belum cukup data" di halaman masing-masing.
