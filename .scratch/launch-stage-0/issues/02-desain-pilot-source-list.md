# Ticket: Which 15 Desain tools form the pilot category?

Type: research
Status: resolved

## Question

What is the final list of 15 Desain tools for the pilot category, given only 3 seed candidates (Excalidraw, Photopea, unDraw), so that at least 12 can realistically be verified `diuji`?

## Detail

`11-seo-architecture.md` §2 requires ≥12 tools for a category to be indexed. `05-seed-tools.md` §7 requires ≥20% of the catalogue to be `diuji`, and launch-plan §8 wants ≥30 `diuji` across the site.

The 3 seeds pass the five selection criteria in `05-seed-tools.md` §1. The other 12 need to clear the same bar, plus the README rule: the pilot must not be a list of 15 tools that replace each other.

The `05-seed-tools.md` §5 queue already names Penpot, Tldraw, Krita, Inkscape, GIMP, Miro — a starting point, not a decision.

Deliverable: a ranked list of 12 further candidates with, for each, the criteria it is expected to satisfy, the limit that will be written, and a flag for whether it needs the owner's 10-minute real-task test.

---

## Answer (research complete — awaiting owner decision)

Findings in [`02-answer.md`](02-answer.md). Every limit cites the vendor URL checked; §6 of that file lists the seven claims that could not be verified at all.

Headline: **8 of the 12 clear all five criteria cleanly.** The remaining 4 carry a caveat that only the owner's real-task test can settle. All 15 are vendor-*claimed* limits, not exercised limits — `verified_at` belongs to the human test, not to this document.

---

## Resolution — owner decisions

**2026-10-22.** Owner accepted all three recommendations.

**Q1 — remove.bg: Diuji with an expiry note.** The Diuji page carries "status acuan ini kedaluwarsa per 1 Desember 2026"; the standalone site moves to Canva after that date. The job "background removal" stays covered at launch.

**Q2 — Figma + Penpot both stay.** The copy must state the split in one line per tool: Figma → interactive prototyping and ecosystem; Penpot → open-source, standard-web export, self-hostable. If the split can't be stated in one line, one of them leaves.

**Q3 — Photopea seed claim corrected.** `docs/05-seed-tools.md` row 5 now reads "Premium opsional (satu kali bayar) — batas gratis belum terverifikasi", and Photopea is added to the §6 list of claims that must stay unwritten until tested.

### Locked pilot list — 15

| Job | Tool | Risk |
|---|---|---|
| Sketching / whiteboard | Excalidraw *(seed)* | Low |
| Raster (PSD) in browser | Photopea *(seed)* | Medium — limit unverified |
| Illustration library | unDraw *(seed)* | Low |
| UI/UX + prototyping | Figma | **High** — owner test |
| UI/UX open source | Penpot | Medium — owner test |
| File-based whiteboarding | Tldraw | **High** — owner test |
| Digital painting | Krita | Low |
| Vector editing | Inkscape | Low |
| Photo retouching | GIMP | Low |
| Icon font | Material Symbols | Low |
| Colour + contrast | Coolors | Low |
| Background removal | remove.bg | **High** — owner test + sunset |
| Image compression | Squoosh | Medium |
| Icon search across sets | Iconify | Medium — URL unverified |
| SVG inspect + optimise | SVG Viewer | Medium — owner test |

**Five owner real-task tests:** Figma, Tldraw, remove.bg, Penpot, SVG Viewer.

**Fallbacks if a test fails:** SVG Viewer → SVGOMG. Tldraw → Miro (workshop facilitation, not whiteboarding — the copy must say so). If two or more fail, the category still clears 12 with Iconify and Inkscape held in `Terdaftar`.

Nothing enters `tools.json` with a `verified_at` until the corresponding owner test is recorded.
