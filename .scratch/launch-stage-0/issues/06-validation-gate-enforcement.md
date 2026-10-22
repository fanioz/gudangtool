# Ticket: What does the build actually refuse?

Type: grilling
Status: open
Blocked by: 12

## Question

Which of the eight rules in `12-tech-stack.md` §5 are enforced by Zod schema, which by a separate script, and which are advisory only?

## Detail

The eight build-failure rules:

1. `diuji` missing `verified_at` / `limits` / `price_status` / `why` / `fit` / `not_fit`.
2. `terdaftar` with any claim field non-null.
3. Duplicate `slug`.
4. `category` not in the categories collection.
5. `alternatives` points at a missing tool, or one that is `terdaftar`.
6. `terdaftar` text containing "gratis".
7. `placement: true` without a placement marker on the page.
8. Category with <3 tools appearing in navigation.

Rules 1–3, 5 are pure Zod + collection reference. Rule 6 is a text lint. Rule 7 is cross-cutting: the data and the rendered output must be checked together, which Zod cannot do. Rule 8 is a page-generation rule, not a data rule.

Also open:

- `11-seo-architecture.md` §2 and `14-repo-spec.md` §6 disagree on category index threshold (12 both) but §2 of `12-tech-stack.md` says 300 pages per batch while the owner set 50.
- Does `noindex` get applied by the page template based on computed counts, or does a script emit a manifest the template reads?
- Does the lint for "gratis" run on `function` only, or also on `name`, `why`, `fit`, `not_fit`, and rendered meta description?

This ticket defines what "the build fails" means in practice, which is the whole integrity story of a file-based site.
