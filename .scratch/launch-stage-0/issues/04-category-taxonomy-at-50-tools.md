# Ticket: What is the category and lane map at 50 tools?

Type: grilling
Status: resolved

## Question

With 15 `diuji` tools in Desain and ~35 `terdaftar` tools across the other 7 categories, what exactly is the taxonomy — which categories exist, which get a lane, and which render `noindex`?

## Detail

Constraints already fixed:

- 8 top-level categories (`01-brand-brief.md` §8).
- A category is indexed at ≥12 tools, but appears in navigation from 3 (`11-seo-architecture.md` §2; `12-tech-stack.md` §5 rule 8).
- Lanes are indexed at ≥8 tools, capped at 40 total.

At 50 tools the arithmetic is tight. 15 in Desain leaves 35 across 7 categories — 5 each. None of those is indexable, all appear in nav, and none can carry a lane.

Open:

1. Are 35 near-empty `terdaftar` pages a net positive? Each needs ≥2 unique data points to be indexed; if not, every one of them is a `noindex` page linked from the homepage.
2. Do lanes exist at launch (a Desain lane needs 8 tools that genuinely share a need), or is the lane system deferred?
3. Does shipping 7 unindexable categories in navigation dilute the one category that is indexed?
4. What is the exact URL for a lane — `/kategori/{slug}/{lorong}` per the tech stack, or a single flat `/kategori/{slug}` with filter state?

---

## Resolution — owner decisions

**2026-10-23.** All three recommendations accepted.

**Q1 — All 8 categories ship as pages (a).** Desain is indexable (≥12 tools, ≥12 `diuji`). The other 7 ship as `noindex` pages with their `terdaftar` tools listed. Nav shows all 8; only Desain is indexable. A category page with 5 `terdaftar` tools is honest — it shows the tools, each says "belum diuji", and `noindex` keeps it out of search.

**Q2 — No lanes at launch (a).** The `subcategory` field exists in the schema and the URL pattern `/kategori/{slug}/{lorong}` is documented, but no lane ships until a category has ≥8 tools that genuinely share a sub-need. Desain at 15 could theoretically support one lane, but the copy and URL structure aren't written yet. Deferred, not abandoned.

**Q3 — Homepage "Baru masuk" strip + search (c).** The homepage strip shows recently added tools regardless of category — the only indexable surface that reaches outside Desain. Pagefind search covers everything else, including `noindex` pages (on-site search only). Neither substitutes for the other: the strip is discovery, search is intent.

### Taxonomy at launch

| Category | Tools | Indexable | Nav |
|---|---|---|---|
| Gudang Desain | 15 | Yes (≥12, all `diuji` or `terdaftar`) | Yes |
| Gudang AI | ~5 | No | Yes |
| Gudang Video | ~5 | No | Yes |
| Gudang Audio | ~3 | No | Yes |
| Gudang Produktivitas | ~5 | No | Yes |
| Gudang Developer | ~5 | No | Yes |
| Gudang Marketing | ~5 | No | Yes |
| Gudang UMKM | ~3 | No | Yes |

Lanes: none at launch. `subcategory` field exists in schema; URL pattern is `/kategori/{slug}/{lorong}`; deferred until a category has ≥8 tools sharing a sub-need.

### Unblocks

Ticket 10 (homepage prototype at 50 tools) now has a clear category picture.
