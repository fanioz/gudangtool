# Ticket: Locked decisions need a decision-log entry

Type: task
Status: resolved

## Question

Can the 2026-10-22 owner decisions be recorded in `docs/09-decision-log.md` as D18, without contradicting anything already there?

## Detail

These decisions were made in the wayfinder session and currently exist only in the map's Notes. `docs/AGENTS.md` rule 9 and the working agreement both require a decision-log entry before implementation.

1. Launch on `.web.id`; `gudangtool.id` upgrade is a later 301, not a launch decision.
2. Pilot category is **Desain only** (replaces launch plan P0 #2 and §6 decision #1, which said Desain + AI).
3. `gudangtools.web.id` (plural) 301-redirects to `gudangtool.web.id`.
4. Launch scale is **50 pages**, not the 300-page first batch in `11-seo-architecture.md` §5.
5. Verification is hybrid (agent mechanical + owner real-task), not 15-minute QA for all tools.
6. Repo location is `~/code/blog/gudangtool`, contradicting D13 which froze work in the workspace folder.

Item 6 is the only one that must *supersede* an existing decision rather than extend it.

---

## Answer

**Resolved 2026-10-22.** Written as **D18** in `docs/09-decision-log.md`.

All six decisions recorded. Verdict per item: #1 extends D1; #2 supersedes `13-launch-plan.md` §6 #1 and P0 #2; #3 is new; #4 supersedes `11-seo-architecture.md` §5 for the first batch; #5 supersedes D7 / `05-seed-tools.md` §4; #6 supersedes D13.

Repo decision amended by the owner during this ticket: work happens in the workspace folder `gudangtool/` (not `~/code/blog/gudangtool`, which is ignored from here on). The folder is now a git repo on `main`, pushed to GitHub `fanioz/gudangtool`.

This unblocks tickets 08, 09, 10, 11, 12.
