# Ticket: Which schema is canonical?

Type: grilling
Status: open
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
