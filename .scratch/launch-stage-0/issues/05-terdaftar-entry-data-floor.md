# Ticket: What is the minimum a `terdaftar` entry carries?

Type: grilling
Status: open
Blocked by: 03, 06

## Question

Which fields does a `terdaftar` tool need so that its page clears the "≥2 unique data points" index bar — or does it ship `noindex` instead?

## Detail

`14-repo-spec.md` §4 says `alternatives` needs ≥2 entries and **every one must be `diuji`**. With 15 `diuji` tools at launch, that is feasible for the first ~35 registrations. It becomes a hard ceiling as the catalogue grows: 50 `terdaftar` tools against 15 `diuji` alternatives cannot all satisfy "2 distinct `diuji` alternatives".

`11-seo-architecture.md` §6 requires three unique data points from a six-item list for a tool page to avoid being thin, then §7 says a `terdaftar` page with fewer than two is `noindex`.

Conflicts to resolve:

1. §4 allows only 2 `alternatives`, and both must be `diuji`. If 5 tools all list the same 3 alternatives, are those still "unique data points"?
2. §6 wants 3, §4 allows 2. Which is the build gate?
3. If a `terdaftar` tool has no `diuji` alternative yet, does it (a) ship `noindex`, (b) get excluded from alternatives entirely, or (c) get dropped from the batch?
4. `unknownList` renders four "Belum diperiksa" rows. That is honest, but it is not data — it does not count toward the threshold.
