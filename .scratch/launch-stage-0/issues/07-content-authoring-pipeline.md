# Ticket: How do 50 tool files get written?

Type: grilling
Status: claimed
Blocked by: 03, 12

## Question

What is the mechanical pipeline from "tool observed" to "JSON merged into `src/content/tools/`", and who is allowed to run which step?

## Detail

`05-seed-tools.md` §7 requires the `function` line be rewritten, not copied from the vendor. `AGENTS.md` §7 splits ownership: content agent edits `src/content/tools/**` one file per PR for corrections, mass import only via script.

Open:

1. What is the input format for a batch? The seed data is in `docs/06-tools.json` with `tier: kandidat` — is there a converter, or does every tool get hand-written?
2. Is there a single import script with a fixed CSV/JSON column list (launch-plan P1 #11 says "template impor CSV/JSON" but none exists)?
3. Who runs the mechanical half of verification — agent writes a candidate JSON file, opens PR, then the owner's real-task note is added before merge?
4. Does a PR get one tool or a batch? `AGENTS.md` §5 wants one task per branch; 50 tool PRs is 50 PRs.
5. Where does `internal_note` (never rendered) record the verification session — date, tester, observed limits?

The pipeline decision determines how fast the 50-page batch can be produced without breaking the "one file per tool" rule.
