# Ticket: What is the split-verification protocol?

Type: grilling
Status: resolved

## Question

What exactly does each half of a hybrid verification produce, and how is a tool marked `diuji` only when both halves are done?

## Detail

The `05-seed-tools.md` §4 protocol was written for one person doing 15 minutes. It assumes the tester both exercises the tool and records the limits. Under the hybrid split:

- **Agent** observes: signup wall, watermark presence, quota text, export formats, platform, last-update date.
- **Owner** exercises: 10 minutes on a real task, then judges `fit` and `not_fit`.

Open questions the protocol must answer:

1. What does the agent record when its observation and the vendor's claim disagree?
2. Which five tools get the owner's real-task test (seed §6 names CapCut, Adobe Podcast, Canva, Raycast, Google AI Studio — but the pilot is Desain, so a different five apply).
3. How does a partially verified tool stay out of the catalogue? `kandidat` exists only in the import queue and never ships.
4. What is the minimum for the five `limits` fields when a limit genuinely cannot be observed without an account?
5. Where does the audit trail live — `internal_note`, a separate CSV, or the PR description?

This must be settled before any tool is marked `diuji`, because it defines what the word means.

---

## Resolution — owner decisions

**2026-10-22.** Owner accepted all five recommendations. Protocol rewritten as **`docs/07-qa-test-sheet.md` v2.0** (replaces v1.1).

**Q1 — Two dates, (c).** `observed_at` (agent mechanical pass) and `verified_at` (owner real task) are separate. `tier: diuji` requires both. A tool observed but not tried stays `terdaftar`, and the page may say so.

**Q2 — Owner wins, (a).** When vendor claim and owner observation disagree, the owner's observation sets `limits`; the vendor claim and its URL go into `internal_note` as the audit trail.

**Q3 — Falls to `terdaftar`, (a).** A tool whose limit cannot be established in the timebox ships listed with no claims. No fourth state, no `TUNDA`, no "batas tidak diketahui" on a `diuji` page.

**Q4 — Evidence outside the repo, (b).** Screenshots in `~/gudangtool-evidence/{slug}/`; `internal_note` records the relative path. Git stores text, not PNGs. Owner may move them in-repo later.

**Q5 — Agent does the mechanical pass, (a)** for the 10 low-risk tools; a fresh subagent per batch past ~15.

### Schema additions (block ticket 06)

| Field | Type | `diuji` | `terdaftar` |
|---|---|---|---|
| `observed_at` | date/null | required | null |
| `observed_by` | `"agent"` \| name | required | null |

Build rule added: `tier: diuji` fails if either is missing.

### Unblocks

Ticket 05 (terdaftar data floor) now has the three-exit state model. Ticket 07 (authoring pipeline) now has the two-part split to encode.
