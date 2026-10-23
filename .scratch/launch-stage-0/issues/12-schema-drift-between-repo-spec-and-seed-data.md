# Ticket: Which schema is canonical?

Type: grilling
Status: resolved
Blocked by: 01

## Question

`docs/06-tools.json` uses `tier: kandidat` with a flat `limits` string, while `docs/14-repo-spec.md` §4 requires `tier: diuji|terdaftar` with `limits` as a five-field object. Which one do the 50 tool files start from?

## Detail

`AGENTS.md` rule 2 says `kandidat` is an internal queue status that never ships. `docs/06-tools.json` is the only existing structured data and it is entirely `kandidat`, with `verified_at: null` and a `limits` field that is prose, not an object.

`14-repo-spec.md` §4 defines the production schema:

- `limits` is an object with `account`, `quota`, `watermark`, `export`, and optional `storage`.
- `price_status` is an enum `gratis | freemium | butuh-akun`.
- `requires_account` is a boolean or null.
- `alternatives` is an array of **slugs that must already be `diuji`**.

Also:

- `05-seed-tools.md` and `06-tools.json` disagree on `price_status` wording (`Gratis` versus `gratis`; the JSON entries use `kandidat` with no `price_status`).
- If the 50 tool files start from the seed list, either the seed is converted (script) or rewritten (one file at a time).
- `internal_note` exists in the spec but not in the seed data.

Resolved when: the canonical schema is named, the seed conversion path is chosen, and the init script writes a valid empty collection tree.

This blocks ticket 6 (build gate) from having anything to validate against.

---

## Resolution — owner decisions

**2026-10-23.** `docs/14-repo-spec.md` §4 is canonical, now **v1.1**. Recorded as **D19**.

**Q1 — Converter script, (a).** A one-time script maps the 20 seed entries into production files. The remaining 30 are hand-authored from the schema. The converter carries `name`, `slug`, `url`, `platform`, `category`, `function`, `added_at`; every claim field stays null.

**Q2 — `alternatives: []` allowed, (a).** Every listed item must be `diuji`, but an empty array is legal. A Video registration with no tested sibling shows no alternatives section rather than linking across categories. If it also lacks three unique data points, the page is `noindex`.

**Q3 — Structured `internal_note`, (b).** The field changes type from `string` to an object:

```json
"internal_note": {
  "sources": [{ "field": "limits.quota", "url": "https://…" }],
  "evidence": ["excalidraw/2026-10-22-01.png"],
  "note": "optional freeform"
}
```

`sources` and `evidence` are required for `diuji`; the build fails without them. `07-qa-test-sheet.md` was updated in the same pass so the protocol and the schema agree.

**Q4 — One file per tool, (a).** `src/content/tools/{slug}.json`, per `AGENTS.md` §7.

**Q5 — Archive the seed, (a).** `git mv docs/06-tools.json docs/06-tools-seed.json`, with a `status_dokumen` banner marking it as history. `docs/README.md` updated.

### Files changed

- `docs/14-repo-spec.md` → v1.1: `observed_at`, `observed_by`, `internal_note` object, `alternatives` relax, new build rules
- `docs/07-qa-test-sheet.md` → aligned to `internal_note.sources` / `.evidence`
- `docs/09-decision-log.md` → D19
- `docs/06-tools.json` → `docs/06-tools-seed.json` (archived)
- `docs/README.md` → references updated

### Unblocks

Ticket 06 (build gate) now has a complete schema to enforce.
