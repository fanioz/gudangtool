# Map: Gudangtool Stage 0 launch

## Destination

A Stage 0 site running from `~/code/blog/gudangtool` (git repo → GitHub → Actions → VPS), on `gudangtool.web.id`, containing: the homepage, one indexable pilot category (Desain) with 15 Diuji tools, ~35 Terdaftar tools, legal pages, and a working `validate:content` build gate. 50 pages total. Other categories ship `noindex` until each reaches its threshold.

**This map decides; it does not build.** The build is the handoff at the end.

## Notes

- Read `docs/09-decision-log.md` first; it outranks every other doc. `docs/14-repo-spec.md` defines the schema and page matrix this effort must obey.
- Superseded by owner decision on 2026-10-22 (needs a decision-log entry — see ticket 10):
  - Launch plays on **`.web.id`** with a planned `.id` upgrade later (D1 still holds).
  - Pilot is **Desain only**, not Desain + AI (replaces P0 #2 / launch-plan §6 #1).
  - `gudangtools.web.id` (plural) **301-redirects** to `gudangtool.web.id`.
  - Scale is **50 pages**, not the 300-page first batch in `11-seo-architecture.md` §5.
- Verification is **hybrid**: agent does mechanical checks (signup wall, watermark, quota text), owner does the 10-minute real-task test on the 5 riskiest tools. "Diuji" requires a human who actually used it.
- Standing rule: never write "gratis" on a `terdaftar` entry. Build must fail on violation.
- The `research` and `prototype` skills referenced by wayfinder are **not installed** in this environment. Research tickets use the `Agent` tool (`general-purpose`) instead.
- `sumoclaw` VPS is down. `sumojak` (2 vCPU / 1.9 GB, Caddy installed) is the target. `sumocabinet` is spare capacity.
- Repo lives in **this folder**, `git init` on `main`, pushed to `github.com/fanioz/gudangtool` (private). `~/code/blog/gudangtool` is ignored from here on.

## Decisions so far

- [Locked decisions need a decision-log entry](issues/01-locked-decisions-need-a-decision-log-entry.md): Six launch decisions recorded as **D18**. Repo is the workspace folder, `D13` superseded, manifest `fanioz/gudangtool` (private). Unblocks tickets 08–12.
- [Which 15 Desain tools form the pilot category?](issues/02-desain-pilot-source-list.md): Pilot list locked — 15 tools, 5 flagged for owner real-task test (Figma, Tldraw, remove.bg, Penpot, SVG Viewer). remove.bg ships Diuji with a 1 Dec 2026 expiry note. Photopea's unsupported seed claim corrected. Fallbacks: SVG Viewer→SVGOMG, Tldraw→Miro.
- [What is the split-verification protocol?](issues/03-verification-protocol-for-two-testers.md): Two dates — `observed_at` (agent, mechanical) and `verified_at` (owner, real task); `diuji` needs both. Failed verification falls to `terdaftar`. Evidence lives outside the repo.
- [Which schema is canonical?](issues/12-schema-drift-between-repo-spec-and-seed-data.md): `14-repo-spec.md` v1.1 is canonical (D19). One file per tool; `alternatives: []` allowed; `internal_note` is a structured object; seed archived as `06-tools-seed.json`.
- [What does the build actually refuse?](issues/06-validation-gate-enforcement.md): Eight rules mapped to mechanisms (D20). Zod gates 1–5; lint gates 6; post-build script gates 7; nav logic gates 8; noindex is template-computed, no manifest.
- [What is the category and lane map at 50 tools?](issues/04-category-taxonomy-at-50-tools.md): All 8 categories ship; only Desain is indexable. No lanes at launch (deferred). Homepage "Baru masuk" strip + Pagefind search for cross-category discovery.
- [Where does legal copy come from?](issues/08-legal-page-copy-source.md): Ditulis sendiri, tanpa pengacara di peluncuran; tinjauan pengacara jadi prasyarat sebelum AdSense. Privasi: Cloudflare WA + Pagefind + GitHub Issue Form, daftar bertanggal. Kontak: halo@gudangtool.web.id forward ke pemilik. Kebijakan afiliasi dikunci (hanya tool diuji, selalu berlabel, tidak pernah mengubah tier/ranking).

## Not yet specified

- **Scaffolding after the schema is locked.** Framework layout, component decomposition, layout and island strategy for search. Depends on the build-gate ticket; cannot be sharpened until the schema stops moving.
- **Design token → CSS delivery.** `docs/02-visual-identity.md` locks colours, fonts, radii; how that becomes tokens, and whether fonts are self-hosted at the stated ≤120 KB budget, is open.
- **Search at 50 pages.** Pagefind is specified, but at 50 pages a client-side island may be the wrong call. Revisit once catalogue size stabilises.
- **Submit flow mechanics.** GitHub Issue Form vs Tally, and where the `submission` label is triaged. The decision is recorded in the launch plan as a recommendation, not a spec.
- **AdSense application timing.** D9 puts AdSense behind placement revenue. Whether `ads.txt` and ad slots ship empty on day one or not at all is open.
- **Collection/ranking eligibility at 50 tools.** Native thresholds (≥10 tool collection, ≥20 ranked tool, ≥100 opens) may make both unshippable at this size.

## Out of scope

<!-- work ruled beyond this destination -->
