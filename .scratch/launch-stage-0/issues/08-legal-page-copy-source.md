# Ticket: Where does legal copy come from?

Type: grilling
Status: resolved
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

---

## Resolution — owner decisions

**2026-10-23.** Empat keputusan.

**Q1 — Ditulis sendiri, tanpa pengacara di peluncuran (a).** Empat halaman ditulis
dalam bahasa Indonesia jelas, tanpa jargon hukum. Tinjauan pengacara dijadwalkan
sebagai prasyarat **sebelum mengajukan AdSense**, bukan sebelum peluncuran. Pada
titik itu materi sudah nyata (trafik, placement pertama) sehingga tinjauan punya
objek untuk diperiksa.

**Q2 — Privasi memuat tiga pemroses saat ini, dengan struktur yang tahan perubahan (a+).**

Halaman `/privasi` menyebut, dengan bahasa awam:

1. **Cloudflare Web Analytics** — tanpa cookie; alamat IP diproses Cloudflare (di luar Indonesia).
2. **Pagefind** — pencarian berjalan sepenuhnya di browser; tidak ada permintaan ke server kami, tidak ada data yang terkirim.
3. **GitHub Issue Form** — data submit masuk ke GitHub (server AS), bukan ke situs ini.

Ditambah: tidak ada akun pengguna, tidak ada cookie pihak ketiga di peluncuran (iklan belum ada).

**Ketentuan perubahan (jawaban atas "bagaimana jika nari pakai GA"):** bagian
pemroses data di halaman privasi ditulis sebagai **daftar bertanggal**, bukan
prosa tunggal. Menambah atau mengganti analitik — termasuk pindah ke Google
Analytics — mensyaratkan tiga hal dalam **satu PR yang sama**: (1) entri decision
log baru, (2) pembaruan daftar pemroses, (3) evaluasi kebutuhan *consent banner*
(karena GA berarti cookie → UU PDP + Google Consent Mode). Tidak ada jalur diam-diam
untuk menambah pemroses. Status quo Cloudflare Web Analytics dipertahankan selama
mungkin: cookieless, ringan, sejalan dengan statis-tanpa-framework.

**Q3 — Kontak `halo@gudangtool.web.id`, diforward ke email pemilik (a).** Halaman
kontak menulis SLA balas yang jujur sesuai kapasitas nyata pemilik (disarankan:
3 hari kerja — angka final diisi saat forward dikonfigurasi). Alamat tanpa pemantauan
tidak boleh tayang.

**Q4 — Kebijakan afiliasi ditulis sekarang (b).** Aturan yang dikunci:

1. Tautan afiliasi hanya pada tool berstatus `diuji`.
2. Setiap tautan afiliasi selalu diberi label terlihat ("tautan afiliasi"), di halaman detail maupun di kartu.
3. Afiliasi **tidak pernah** mengubah `tier`, `verified_at`, `limits`, `why`, `fit`, `not_fit`, atau posisi ranking.
4. Penempatan berbayar (placement) tetap jalur terpisah dengan label "Placement", sesuai D9.
5. Halaman pengungkapan di peluncuran menyatakan: aturan ini berlaku, dan saat ini belum ada tautan afiliasi tayang.

### Empat halaman — ringkasan keputusan

| Halaman | Keputusan kunci |
|---|---|
| `/privasi` | Tiga pemroses (Cloudflare WA, Pagefind, GitHub Issue Form); daftar bertanggal; perubahan pemroses = satu PR dengan decision log |
| `/ketentuan` | Ditulis sendiri, bahasa awam; cakup: penggunaan situs, batas tanggung jawab atas tool pihak ketiga, hak konten pengirim submit |
| `/kontak` | `halo@gudangtool.web.id` forward ke pemilik; SLA tertulis (disarankan 3 hari kerja) |
| Pengungkapan afiliasi & placement | Aturan afiliasi di atas; "belum ada tautan afiliasi tayang" saat peluncuran |

### Unblocks

- Peluncuran tidak lagi terblokir oleh P0 #6 (legal pages).
- Ticket 09 (DNS & email) sekarang punya konsumen nyata untuk record MX/forward `halo@`.
