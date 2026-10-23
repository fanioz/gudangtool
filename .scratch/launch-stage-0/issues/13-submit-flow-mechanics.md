# Ticket: How does a tool submission actually reach us?

Type: grilling
Status: open

## Question

What is the real mechanism behind "Titip tool" at Stage 0, and does it survive the fact that the repository is private?

## Detail

The launch plan recommends a mechanism, but never specs it, and the recommendation collides with a locked decision.

**What is already written down**

- `13-launch-plan.md` §13: "Alur submission. GitHub Issue Form + label + template email fallback." Priority table row 4: "Form submission — GitHub Issue Form; email sebagai fallback." The map recorded this as a recommendation, not a spec.
- `11-seo-architecture.md` line 35: `Submit` is a page type at `/submit`, index "Selalu" (always), priority "Rendah". So the page ships.
- `13-launch-plan.md` line 114: "Tidak ada tautan mati di 50 halaman pertama" — no dead links in the first 50 pages.

**The collision**

D18 (ticket 01) locked the manifest as `fanioz/gudangtool`, **private**. A GitHub Issue Form on a private repository is unusable by the public: nobody outside the organisation can open an issue on it. So the recommended mechanism either needs the repository to become public (contradicting D18), or a second public repository dedicated to submissions, or a different form surface entirely.

This was invisible until the homepage prototype (ticket 10) put a "Titip tool" CTA on all three variants. That CTA has to resolve to something, and `/submit` has to say something true.

**What has to be decided**

1. **Mechanism**: GitHub Issue Form on a public submissions repository, Tally, a static form posting to a serverless function, or email-only. Anything that adds a service needs an entry in `docs/09-decision-log.md` before it ships (AGENTS.md rule 9).
2. **Privacy**: ticket 08 locked the privacy posture — Cloudflare Web Analytics, Pagefind, GitHub Issue Form, dated list. If the mechanism changes, ticket 08's answer moves with it.
3. **Triage**: where the `submission` label is triaged and by whom, and whether the queue lives in the same repo as the catalogue.
4. **What the two lanes promise**: the homepage copy (§10 of `03-homepage-copy.md`) sells "pengiriman biasa, antrean {14} hari" and "prioritas, review {48} jam" — the second lane is paid placement (D9). A public submission surface has to state which lane is which without implying that payment buys a listing (AGENTS.md rule 5, and the 10 non-negotiables).
5. **Page budget**: the destination is "50 pages total". 1 homepage + 1 category + 15 Diuji + ~35 Terdaftar + legal pages already lands close to the ceiling, and `/submit` is another page. If `/submit` does not fit, the homepage CTA has to point somewhere else, and that changes the answer to variant picking in ticket 10.

**Why this is a decision, not a build step**: every option above changes what the homepage promises, what the legal pages say, and what the owner maintains weekly. Choosing wrong means a public surface that cannot be received, or a paid lane that reads as a sold ranking.

**Not yet specified here**: exact field list for the form, spam handling, and what the submitter gets back. Those follow from whichever mechanism is chosen.
