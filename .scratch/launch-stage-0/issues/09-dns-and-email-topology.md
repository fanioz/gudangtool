# Ticket: What is the DNS and email topology?

Type: grilling
Status: resolved
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

---

## Resolution — owner decisions

**2026-10-23.** Lima keputusan.

**Q1 — Satu zona Cloudflare untuk kedua domain (a).** `gudangtool.web.id` dan
`gudangtools.web.id` sama-sama didelegasikan ke nameserver Cloudflare. Zona tunggal
memuat: A `@` → VPS `sumojak`, CNAME `www` → `@`, TXT verifikasi/SPF/DKIM Brevo.
**Fakta yang harus diverifikasi manual (task):** perubahan NS `.web.id` dilakukan
dari panel registrar PANDI — tidak bisa diverifikasi dari luar (whois/RDAP tidak
mengembalikan data). Kalau ternyata `.web.id` tidak mendukung delegation ke NS
pihak ketiga, fallback: `gudangtool` tetap di registrar dan redirect `gudangtools`
dikonfigurasi lewat Caddy (Q2 berubah ke (b)) — dicatat sebagai fakta, bukan
kegagalan.

**Q2 — 301 `gudangtools` → `gudangtool` di Cloudflare Bulk Redirects (a).** Hidup
di edge, selamat dari kegagalan VPS, satu tempat konfigurasi. Alasan: kasus paling
butuh redirect (link lama ke domain jamak) adalah kasus di mana situs utama sedang
paling mungkin bermasalah — redirect di VPS ikut mati bareng.

**Q3 — VPS `sumojak` (a).** 2 vCPU / 1,9 GB, Caddy terpasang. `sumocabinet` tetap
cadangan: IP diketahui, tidak dikonfigurasi apa pun — agar rollback bukan proyek.

**Q4 — `halo@gudangtool.web.id` lewat Brevo dengan domain terverifikasi (a).**
Rekam di zona Cloudflare hasil Q1: record verifikasi Brevo, TXT SPF, DKIM. Alasan
bukan volume tapi identitas: balasan dari domain sendiri bagian dari kredibilitas
D22. Kuota gratis Brevo (300 email/hari) jauh di atas kebutuhan. Fallback kalau
konfigurasi merepotkan: forward polos tanpa verifikasi domain (b) — layak, bukan
kegagalan.

**Q5 — IPv4 publik + Cloudflare proxy aktif (a).** A record nyata ke VPS tapi
orange cloud: IP asli tersembunyi, cache + DDoS aktif. SSH tetap terbuka (kunci
saja) karena deploy rsync dari GitHub Actions butuh akses langsung. Cloudflare
Tunnel ditolak untuk Stage 0 — menambah komponen di luar rencana `12-tech-stack.md`.

### Topologi final

| Domain | NS | Peran |
|---|---|---|
| `gudangtool.web.id` | Cloudflare | Situs utama; A → `sumojak`, orange cloud |
| `gudangtools.web.id` | Cloudflare (dari Sumopod) | 301 ke tunggal di Cloudflare Bulk Redirects; tidak pernah diindeks |

Email `halo@` → Brevo (domain terverifikasi di zona yang sama) → forward ke pemilik.

### Checklist manual setelah keputusan ini

1. Panel PANDI: delegasi NS kedua `.web.id` ke Cloudflare — **verifikasi dulu apakah didukung**.
2. Cloudflare: buat zona, A `@`, CNAME `www`, Bulk Redirects, record Brevo.
3. `sumojak`: pasang kunci SSH GitHub Actions untuk rsync.

### Unblocks

- Ticket 11 (bootstrap repo & deploy) — seluruh topologi sudah diketahui.
