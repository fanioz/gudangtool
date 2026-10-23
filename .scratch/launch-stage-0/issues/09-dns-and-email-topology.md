# Ticket: What is the DNS and email topology?

Type: grilling
Status: claimed
Blocked by: 01

## Question

Which nameservers, which VPS serves what, and how does the site get a working sending address?

## Detail

Known state (verified 2026-10-22):

| Domain | NS | A |
|---|---|---|
| `gudangtool.web.id` | none | none |
| `gudangtools.web.id` | `ns1.sumopod.com`, `ns2.sumopod.com` | none |

`12-tech-stack.md` assumes Cloudflare DNS + cache + Access. But `gudangtools` is on Sumopod nameservers, so the two domains are managed in different places. If `gudangtool` moves to Cloudflare and `gudangtools` stays on Sumopod, the 301 redirect between them crosses two DNS providers.

Open:

1. Does `gudangtool.web.id` move to Cloudflare nameservers (per D9/stack), and is the PANDI registrar change possible for a `.web.id`?
2. Where does the redirect live — Cloudflare Bulk Redirects (outside the VPS) or Caddy on the VPS? Redirect at the edge is cheaper and survives a VPS outage.
3. Which VPS hosts the site — `sumojak` (1.9 GB, Caddy present) is recommended, with `sumocabinet` spare.
4. Sending address: `halo@gudangtool.web.id`? Brevo per `13-launch-plan.md` §2 #7, but Brevo needs domain verification via TXT/DKIM records — that has to live on whichever provider holds the zone.
5. Does the VPS need a public IPv4, or is it behind Cloudflare proxying only?

This is a task-shaped ticket with a grilling front: the topology is a decision, then DNS records are manual work.
