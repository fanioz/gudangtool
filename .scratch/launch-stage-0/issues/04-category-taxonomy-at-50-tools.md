# Ticket: What is the category and lane map at 50 tools?

Type: grilling
Status: open

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
