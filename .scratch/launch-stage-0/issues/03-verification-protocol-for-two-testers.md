# Ticket: What is the split-verification protocol?

Type: grilling
Status: open

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
