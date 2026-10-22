# Ticket: What does the homepage show at 50 tools?

Type: prototype
Status: open
Blocked by: 01, 02, 04

## Question

Does the homepage's "paling sering dibuka" and ranking strip degrade gracefully when there is no click data and fewer than 20 ranked tools — or should it be hidden?

## Detail

`03-homepage-copy.md` v2.0 specifies sections: search first, categories, "baru masuk", "paling sering dibuka", collections, ranking, three-label explainer, submit path.

At launch:

- No click data exists (pageview only, `12-tech-stack.md` §8).
- Ranking needs ≥20 ranked tools with ≥100 opens each. That is weeks away.
- Collections need ≥10 tools each under a deterministic rule.

So three of the six homepage sections have no data. The homepage is the only page every visitor sees, and the first 5 seconds are the brand's whole promise (`01-brand-brief.md` §10).

The question is a prototype, not a debate: build the homepage with the empty sections and see whether it reads as honest or broken. Candidates: hide the section, show a "belum cukup data" state, or show the section with a single row.

Needs the visual identity tokens from `docs/02` and the preview files in `docs/preview/`.
