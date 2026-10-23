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
- Launch runbook lives in `docs/deploy/runbook-launch.md`; the Caddy site block in `docs/deploy/Caddyfile.gudangtool`. The deploy pipeline has a preflight step that points to the runbook when the VPS prerequisite is missing.
- **Owner decision 2026-10-23:** the scaffolding gate opened early. Ticket 15 (scaffold structure) graduates now, in parallel with ticket 11's operational remainder — the repo/deploy shape is settled, so nothing in the scaffold depends on 11 closing. "The map decides, does not build" still holds: the build itself remains the handoff.

## Decisions so far

- [Locked decisions need a decision-log entry](issues/01-locked-decisions-need-a-decision-log-entry.md): Six launch decisions recorded as **D18**. Repo is the workspace folder, `D13` superseded, manifest `fanioz/gudangtool` (private). Unblocks tickets 08–12.
- [Which 15 Desain tools form the pilot category?](issues/02-desain-pilot-source-list.md): Pilot list locked — 15 tools, 5 flagged for owner real-task test (Figma, Tldraw, remove.bg, Penpot, SVG Viewer). remove.bg ships Diuji with a 1 Dec 2026 expiry note. Photopea's unsupported seed claim corrected. Fallbacks: SVG Viewer→SVGOMG, Tldraw→Miro.
- [What is the split-verification protocol?](issues/03-verification-protocol-for-two-testers.md): Two dates — `observed_at` (agent, mechanical) and `verified_at` (owner, real task); `diuji` needs both. Failed verification falls to `terdaftar`. Evidence lives outside the repo.
- [Which schema is canonical?](issues/12-schema-drift-between-repo-spec-and-seed-data.md): `14-repo-spec.md` v1.1 is canonical (D19). One file per tool; `alternatives: []` allowed; `internal_note` is a structured object; seed archived as `06-tools-seed.json`.
- [What does the build actually refuse?](issues/06-validation-gate-enforcement.md): Eight rules mapped to mechanisms (D20). Zod gates 1–5; lint gates 6; post-build script gates 7; nav logic gates 8; noindex is template-computed, no manifest.
- [What is the category and lane map at 50 tools?](issues/04-category-taxonomy-at-50-tools.md): All 8 categories ship; only Desain is indexable. No lanes at launch (deferred). Homepage "Baru masuk" strip + Pagefind search for cross-category discovery.
- [Where does legal copy come from?](issues/08-legal-page-copy-source.md): Ditulis sendiri, tanpa pengacara di peluncuran; tinjauan pengacara jadi prasyarat sebelum AdSense. Privasi: Cloudflare WA + Pagefind + GitHub Issue Form, daftar bertanggal. Kontak: halo@gudangtool.web.id forward ke pemilik. Kebijakan afiliasi dikunci (hanya tool diuji, selalu berlabel, tidak pernah mengubah tier/ranking).
- [What is the minimum a `terdaftar` entry carries?](issues/05-terdaftar-entry-data-floor.md): Dua ambang — `diuji` 3 data unik, `terdaftar` 2. Field wajib (`function`) dan "Belum diperiksa" tidak dihitung; yang dihitung platform + alternatif `diuji`. Halaman tanpa alternatif `diuji` tetap tayang `noindex, follow`. Keunikan per halaman, bukan lintas halaman.
- [How do 50 tool files get written?](issues/07-content-authoring-pipeline.md): Impor awal satu PR batch (konversi seed + 30 tulis tangan); koreksi menyusul satu file per PR. Tulis dulu sebagai `terdaftar`, naik kelas belakangan — satu PR kecil per uji tuntas. Pemilik menulis `why`/`fit`/`not_fit` sendiri (boleh kasar), agent hanya memformat.
- [What is the DNS and email topology?](issues/09-dns-and-email-topology.md): Satu zona Cloudflare untuk kedua domain; 301 `gudangtools`→`gudangtool` di Bulk Redirects (edge); VPS `sumojak` (A record, orange cloud); `halo@` lewat Brevo domain terverifikasi; SSH tetap publik + kunci. Verifikasi manual: dukungan delegasi NS `.web.id` di panel PANDI.
- [How is the Astro scaffold structured?](issues/15-astro-scaffold-structure.md): **D26** — token CSS (`tokens.css`) + scoped style per komponen; font self-host subset WOFF2 ≤120 KB; Pagefind tetap (Lighthouse <85 = pemicu revisit); set komponen launch + kondisional, tanpa Pagination. Gerbang scaffolding dibuka awal oleh pemilik; fog scaffolding selesai.
- [What does the homepage show at 50 tools?](issues/10-homepage-filter-behaviour-at-50-tools.md): **Varian A — rangka penuh.** Ranking tampil satu kotak "belum cukup data" + ambang; koleksi disembunyikan; slot iklan dipertahankan (fog AdSense mulai menggigit). Konsekuensi: nav "Ranking" butuh halaman nyata → tiket 14 terbuka.
- [Do `/ranking` and `/koleksi` ship at 50 tools?](issues/14-ranking-and-collection-pages-at-50-tools.md): **Terbit, `noindex, follow`, di luar sitemap** (pilihan a). Halaman menjelaskan ambang + "belum cukup data"; tautan nav tidak pernah mati; tautan "Koleksi" hanya muncul bila ada koleksi yang memenuhi ambang.

## Not yet specified

- **AdSense application timing.** D9 puts AdSense behind placement revenue. Whether `ads.txt` and ad slots ship empty on day one or not at all is open — it only bites if the homepage keeps a reserved ad slot (variant A of ticket 10; variants B and C drop it).

## Out of scope

<!-- work ruled beyond this destination -->
