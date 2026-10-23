# Ticket: Where does legal copy come from?

Type: grilling
Status: claimed
Blocked by: 01

## Question

Do we write privacy / terms / contact / affiliate+placement disclosure in-house from `docs/`, or bring in reviewed wording?

## Detail

Launch-plan P0 #6 makes these a launch blocker: AdSense requires them, and Indonesian UU PDP requires a privacy notice for a site using Cloudflare Analytics and Pagefind.

Four pages, each currently a stub in the page matrix and nothing else:

- `/privasi`
- `/ketentuan`
- `/kontak`
- affiliate and placement disclosure — `11-seo-architecture.md` §9 says paid placement must always be labelled; the policy for when affiliate links are used is P2 #23 and unwritten.

Open:

1. Is a lawyer needed, or is a plain-language Indonesian policy enough for a launch at this scale?
2. What does the privacy page have to say about Cloudflare Web Analytics, Pagefind (client-side, no server), and the GitHub Issue Form (data lands in GitHub, not the site)?
3. Which email is the contact — `halo@gudangtool.web.id`, per launch plan §6 #6, and who monitors it?
4. Does the affiliate policy say "zero affiliate links at launch" (simplest) or specify when they become allowed?
