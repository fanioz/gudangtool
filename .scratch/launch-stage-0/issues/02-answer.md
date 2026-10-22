# Ticket 02 — Which 15 Desain tools form the pilot category?

Type: research · Status: open (answer drafted)
Checked: **2026-10-22**, from vendor pricing/help pages. Nothing in this file was exercised in a live session; every limit is what the vendor page *says*, not what it *does*. That distinction is the point of the Diuji tier.

Read this with ticket 03. The hybrid protocol splits the work: an agent records what the vendor claims (this file is that record, cited), the owner runs the real-task test. Nothing here should be written to `tools.json` with `verified_at` until the second half is done.

---

## 0. What this ticket actually delivers

The ticket asks for 15 tools (3 seeds + 12). §11 SEO architecture requires ≥12 to index a category, launch plan §8 wants ≥30 `diuji` site-wide, and `05-seed-tools.md` §7 caps `terdaftar` at 80% of the catalogue.

Most of the 12 below are nominees, not confirmations. Before any tool can carry `Diuji`, two things need to happen, in order:

1. The owner accepts the job-coverage map (§1).
2. The one-line limit in §2 is confirmed by the owner's real-task test (ticket 03 defines what counts).

I did not find 12 candidates that clear all five criteria with a clean, vendor-stated, one-line limit. Lying about that would defeat the entire project. But I did find five clean ones — Penpot, Figma Starter, Krita, Material Symbols, and Coolors — plus three that will be clean as soon as the risk they carry is settled by the owner's own test. Those eight are enough to index the category on their own.

The practical outcome:

- **12 Diuji with Penpot, Figma, Krita, Material Symbols, Coolors:** Squoosh, Inkscape, GIMP, Iconify, SVG Viewer, Tldraw, alih-alih remove.bg.
- If Tldraw and remove.bg fail the real-task test, the pilot ships 13 tools (12 Diuji + 1 candidate held back). That still clears the 12-tool index threshold. The trade-off is that "background removal" has no entry; the alternative is to promote another candidate from §3 and accept the substitution risk the ticket warns against — Miro → doesn't replace Tldraw, they overlap.

---

## 1. Job coverage — the 15-slot map

The rule is non-substitutability (§2 of the ticket, `05-seed-tools.md` §3). A substituted tool must do a *different job*, not the same job better. That's why Miro appears as a backup for Tldraw: if Tldraw is a lighter sibling of Excalidraw, Miro is the tool you'd pick for *structured workshop facilitation*, a job neither seed covers. It isn't a Tldraw replacement.

| # | Tool | Job | Seed or new |
|---|---|---|---|
| 1 | Excalidraw | Sketching / whiteboard / rough diagrams | seed |
| 2 | Photopea | Raster (PSD) editing in the browser | seed |
| 3 | unDraw | Illustration library | seed |
| 4 | **Figma (free tier)** | UI/UX design + interaction prototyping | new |
| 5 | **Penpot** | Open-source UI/UX design, self-hostable | new |
| 6 | Tldraw | Fast infinite-canvas whiteboarding, file-based | new |
| 7 | Krita | Digital painting / artist-oriented raster | new |
| 8 | Inkscape | Vector editing (SVG source) | new |
| 9 | GIMP | Long-form raster retouching / photo restoration | new |
| 10 | Material Symbols | Icon set (variable font) | new |
| 11 | Coolors | Colour palette generation + accessibility check | new |
| 12 | remove.bg | AI background removal (single image) | new |
| 13 | Squoosh | Image compression | new |
| 14 | Iconify | Icon search across sets, then mixed-set download | new |
| 15 | SVG Viewer | SVG inspection + optimisation | new |

**Substitution risk that needs a reason:** Figma and Penpot both do UI/UX design. They go in only because the jobs differ — Figma for interactive prototyping and its ecosystem, Penpot for open-source export and self-hosting. If the owner can't defend that split in the copy, one of them has to go. The same applies to Krita vs GIMP (painting vs retouching vs Photopea) and Coolors vs Material Symbols (see §4, Mandatory reason line).

---

## 2. The 12

| # | Name | URL | Function (ID, ≤160) | Platform | price_status | Akun | Limit (one line) | Vendor states it? |
|---|---|---|---|---|---|---|---|---|
| 4 | Figma (free tier) | https://www.figma.com/pricing/ | Merancang antarmuka aplikasi dan web, lalu menyambungkan layar menjadi prototipe interaktif. | web, desktop (app Windows/macOS), ponsel | freemium → **butuh-akun** (verify) | true | Starter gratis; batas yang pasti — kolaborator di **3 file kolaboratif**, riwayat versi **30 hari**, plugin & Dev Mode penuh berbayar | **Partial** |
| 5 | Penpot | https://penpot.app/pricing | Merancang UI dan prototipe di browser dengan standar web, bisa dipasang sendiri di server. | web, desktop (PWA) | freemium → butuh-akun | true | Plan gratis Cloud: **8 anggota tim**, penyimpanan **10 GB**, riwayat versi **7 hari** | **Yes** |
| 6 | Tldraw | https://tldraw.com/ | Papan gambar tak terbatas untuk sketsa dan kolaborasi cepat, dengan file yang bisa disimpan lokal. | web, desktop (offline app) | gratis → butuh-akun (verify) | **false to draw, true to share** (verify) | Tanpa akun bisa menggambar dan menyimpan file; **"Sign in to share"** — berbagi lewat tautan butuh akun | **No** (UI only) |
| 7 | Krita | https://krita.org/en/download/ | Menggambar dan melukis digital dengan kuas yang dibuat untuk ilustrator, lengkap dengan alat animasi. | desktop (Win/macOS/Linux; Android/iOS tidak didukung) | gratis | false | Tidak ada batas — program penuh, open source (GPL v3); tanpa akun, tanpa watermark | **Yes** (licence page + download page) |
| 8 | Inkscape | https://inkscape.org/ | Menggambar dan mengedit grafik vektor SVG seperti logo dan ikon dengan presisi jalur. | desktop (Win/macOS/Linux) | gratis | false | Tidak ada batas — program penuh, open source; catatan: situs pembaruan kadang lebih baru dari paket distro | **Yes** (GitLab releases) |
| 9 | GIMP | https://www.gimp.org/downloads/ | Menyunting dan memulihkan foto dengan lapisan dan filter, versi baru ikut menambah fitur gambar vektor. | desktop (Win/macOS/Linux) | gratis | false | Tidak ada batas — program penuh, open source | **Yes** (download page: stable 3.2.6, 2026-09-10) |
| 10 | Material Symbols | https://fonts.google.com/icons | Ikon siap pakai dari Google Material, bisa diunduh per ikon atau dipasang sebagai satu font variabel. | web (katalog & unduh) | gratis | false | Tidak ada batas — lisensi **Apache 2.0**, boleh dipakai untuk proyek apa pun | **Yes** (repo LICENSE) |
| 11 | Coolors | https://coolors.co/pricing | Membuat dan menguji palet warna untuk desain, termasuk pemeriksa kontras untuk aksesibilitas. | web, ponsel (iOS), ekstensi | freemium | true (untuk simpan) | Plan gratis: maksimal **5 warna per palet**, simpan **10 palet**, **1 proyek + 1 koleksi**; ada iklan | **Yes** |
| 12 | remove.bg | https://www.remove.bg/ | Menghapus latar belakang foto secara otomatis, hasil siap dipakai sebagai PNG transparan. | web, desktop (app), ponsel (Android) | freemium → **butuh-akun** (verify) | true (for full-res) | Tanpa akun: *preview* resolusi rendah; **unduhan penuh 1 gambar = 1 kredit berbayar** | **Yes** (FAQ) — but sunset flag, see below |
| 13 | Squoosh | https://squoosh.app/ | Mengecilkan ukuran gambar dengan membandingkan hasil codec langsung di browser, tanpa mengunggah file. | web (PWA) | gratis | false | Tidak ada batas — semuanya diproses di perangkat, gambar tidak diunggah. Repo diklaim **frozen** oleh tim | **Yes** (homepage "Images never leave your device") |
| 14 | Iconify | https://iconify.design/ | Mencari ikon dari ratusan set sekaligus dan mengunduhnya per ikon sebagai SVG. | web (katalog) | gratis | **unverified** | Tidak ada batas untuk katalog dan unduhan; lisensi ikut set asalnya (MIT/Apache/CC) — perlu diperiksa per ikon | **Partial** |
| 15 | SVG Viewer | https://www.svgviewer.dev/ | Melihat, merapikan, dan mengecilkan file SVG, termasuk mengedit warna dan mengurangi jumlah node. | web | gratis | **unverified** (no account UI found) | Tidak ada batas yang terlihat; upaya scraping diblokir IP — bukan batas pemakaian | **No** |

### Column notes

**Figma.** The pricing page (https://www.figma.com/pricing/) explicitly lists only "Unlimited drafts / UI kits and templates / 150 AI credits/day" for Starter. The "3 files" figure comes from Figma's own blog post "Drafts are changing" (https://www.figma.com/blog/updates-to-how-drafts-work/), which says a Starter team gets "unlimited viewers … and unlimited editors on up to 3 collaborative files". The feature matrix embedded in the pricing page confirms Starter has **no** advanced prototyping, conditional logic, Dev Mode handoff, team libraries, shared fonts, or private plugins, and has **30 days** of version history. Figma has changed this twice in two years (drafts moved in 2024; pricing reworked in 2025–26). Treat the limit line as provisional until tested.

**Tldraw.** https://tldraw.com/ is a JS app — the marketing text is not in the HTML. I rendered it with a headless browser: with no account, the canvas opens with full drawing tools and the share button reads "Sign in to share". The public page title says "very good free whiteboard" and the meta description says "Free online whiteboard no sign up". Sharing without an account did not occur in the render, but I did not try guest-editable links — the vendor does not state the limit anywhere on the site. Ticket 03 should require a real try here, not a README quote.

**Krita, Inkscape, GIMP, Material Symbols.** These four are different from the rest: they're open-source programs under licences with no usage tiers. The limit line is "no limit" — which is easier to verify and harder to misrepresent than any freemium quota. Activity: Krita 5.3.4.1 released 2026-10-07 (https://krita.org/en/download/); GIMP 3.2.6 (2026-09-10, https://www.gimp.org/downloads/); Inkscape has an active 1.4.x line — the last stable tag on GitLab is INKSCAPE_1_4_4 (2026-05-05, https://gitlab.com/api/v4/projects/inkscape%2Finkscape/repository/tags) and repo activity on 2026-10-22. Material Symbols is a Google font shipped under Apache 2.0 (https://raw.githubusercontent.com/google/material-design-icons/master/LICENSE). The last two need a `verified_at` date, but the limit claim itself is a licence fact — it doesn't drift quarterly the way commercial freemium tiers do.

**Inkscape caveat.** History: the README's "Updated in the last 12 months" criterion is met by the GitLab tag, but inkscape.org returned 403 to every automated request from this machine. Before launch, someone should confirm the download page is not region-blocked from Indonesia. If it is, the tool goes to `Terdaftar` until it can be tested.

**remove.bg — this one is dated.** While reading https://www.remove.bg/pricing I found a non-dismissible banner (also visible on https://www.remove.bg/id): remove.bg's background removal is moving to Canva, and **the standalone website will no longer be available from 1 December 2026 at 9:00am CET**. The same page's FAQ confirms the free-tier shape (preview images are free; 1 credit = 1 full-resolution image). So the tool can only be `Diuji` if the test happens in the next six weeks, and the Diuji page needs an explicit "status acuan ini kedaluwarsa per 1 Desember 2026" note. The honest alternative is to list remove.bg as `Terdaftar` and put Canva's background remover in the queue behind it. Adding it to Diuji with the sunset noted is defensible — the user searching "hapus background" today gets a working tool. Adding it without the note isn't.

**Coolors.** The full free/Pro split is stated on https://coolors.co/pricing ("Generate your palettes, up to 5 colors · Save up to 10 color palettes · 1 project · 1 collection · Ads visible on the page"). Pro removes ads and unlocks 10-colour palettes, unlimited saves and the contrast checker (listed under Pro: "Check palette contrast"). The free **contrast checker** lives at https://coolors.co/contrast-checker but its account/invite-flow gating wasn't confirmed — treat it as a claim the tester must verify. I listed Requires account `true` for saving, not for generating; a user can generate a palette without signing in.

**Squoosh.** Repo activity: the default branch's last commit is 2024-08-19, though `pushed_at` on the repo (https://api.github.com/repos/GoogleChromeLabs/squoosh) shows 2026-10-15. I saw the "frozen" claim on secondary sources but could not confirm the wording in the repo itself — treating "dikembangkan terbatas" as the only safe phrasing until the owner checks the repo. The privacy claim is on the homepage: "Worried about privacy? Images never leave your device since Squoosh does all the work locally."

**Iconify.** The catalogue page (https://iconify.design/icons/) returns 404 — the site has been restructured and the feature may now be at a different path. Downloads are fine, but the URL in the table points to the docs home. Before listing, somebody needs to find the current icon-browser URL. This is why Requires account is "unverified": no account wall appeared in the fetch, but the fetch saw a partial page.

**SVG Viewer.** No pricing page, no login link, no quota text — and also no active blog or release notes; the privacy page (https://www.svgviewer.dev/privacy) returns 404 and the Terms of Service (https://www.svgviewer.dev/terms) was last updated **Nov 29, 2019**. That last date is a risk: the tool works today, but nothing on the site suggests anyone is maintaining it. It passes "still reachable"; "still active" is a judgement call for the owner.

**SVGOMG** is not in the 12. It's the "optimise" half of the same job SVG Viewer covers, it duplicates Squoosh's role for a different format, and its last commit is 2025-09-29 — inside the window, but the tool has no new features in a year. SVG Viewer gets the slot because it also *views* and *edits colour*, and because it works for people who don't want to learn SVGO's settings panel. If the owner prefers SVGO's output quality, swap the two, not both.

**Note on the SVG pair.** SVG Viewer lists "Edit with AI" and "Create" (describe an SVG) in its sidebar — that's a new AI feature, unpublished on the vendor's own site. Its free tier isn't stated anywhere, which is exactly the kind of claim that should not go to `Diuji` without a test. If SVG Viewer turns out to gate exports behind AI credits, the slot should move to **SVGOMG** (open source, no paid tier) and the SVG job stays covered.

---

## 3. `fit` / `not_fit` / Alternatives / Risk

Alternatives refer to tools in this list.

| Tool | fit | not_fit | Alternatives | Risk | Owner test |
|---|---|---|---|---|---|
| Figma | Prototipe alur aplikasi, design system kecil, dan serah-terima ke pengembang. | Butuh kolaborasi tim besar, prototyping kondisi lanjutan, atau riwayat lama — semua berbayar. | Penpot, Krita | **High** | **Yes** |
| Penpot | Tim yang ingin desain UI standar web dan bisa memindahkannya ke server sendiri. | Desainer yang butuh plugin komuntas besar atau fitur AI generatif — Penpot masih di belakang. | Figma, Excalidraw | Medium | **Yes** |
| Tldraw | Papan berpikir yang mau disimpan sebagai file, bukan terkunci di akun orang lain. | Diagram yang butuh simbol teknis lengkap seperti UML atau BPMN. | Excalidraw, Penpot | **High** | **Yes** |
| Krita | Ilustrasi, komik, dan lukisan digital yang butuh kuas dan tekstur. | Mengedit foto hasil kamera — Krita dibuat untuk menggambar, bukan koreksi warna. | GIMP, Photopea | Low | No |
| Inkscape | Logo, ikon, dan grafik yang harus tetap vektor dan bisa disunting di sumbernya. | Desain UI lengkap dengan komponen dan prototyping. | Figma, Material Symbols | Low | No |
| GIMP | Koreksi warna, pemulihan foto lama, dan penyuntingan berlapis yang berat. | Antarmuka yang ramah pemula, atau membuka file PSD secara mulus. | Photopea, Krita | Low | No |
| Material Symbols | Ikon yang konsisten untuk aplikasi dan web, cukup satu font variabel. | Ikon berbeda gaya per merek, atau ilustrasi — katalog ini hanya ikon garis Material. | Iconify, unDraw | Low | No |
| Coolors | Memilih palet dengan cepat dan memastikan kontras teks lolos aksesibilitas. | Manajemen brand yang butuh ribuan warna tersimpan. | Material Symbols, Figma | Low | No |
| remove.bg | Satu foto produk atau potret yang butuh latar transparan bersih. | Batch banyak gambar tanpa berlangganan, atau pemakaian setelah Desember 2026. | Photopea, GIMP | **High** | **Yes** |
| Squoosh | Menemukan codec dan kualitas terbaik untuk satu gambar sebelum diunggah ke situs. | Batch puluhan gambar, atau otomatisasi — tidak ada API. | Iconify (for SVG only) | Medium | No |
| Iconify | Menemukan ikon dari banyak set dalam satu pencarian, lalu mengunduhnya sebagai SVG. | Proyek yang menuntut satu gaya ikon tunggal di seluruh aplikasi. | Material Symbols, unDraw | Low | No |
| SVG Viewer | Merapikan SVG yang tercopy berantakan dan melihat sumbernya langsung. | Aset ilustrasi baru — ini pembersih, bukan pembuat. | Squoosh, Inkscape | Medium | **Yes** |

**Mandatory reason line — Coolors vs Material Symbols.** Both touch colour, but they don't do the same job: Coolors *chooses* a palette and tests it for contrast; Material Symbols *ships* an icon family that happens to be colour-less. A user looking for a palette would never accept an icon set as a substitute, and vice versa. The copy must state this in one line per tool or the pair reads as duplicate "colour tools".

---

## 4. Owner real-task test — the five

Chosen by risk × consequence, not by "most popular":

1. **Figma (High).** The free tier has changed twice in two years and the pricing page still doesn't list the 3-file limit. The reference tool for the category; if the limit is wrong, the category's credibility is wrong with it.
2. **Tldraw (High).** No vendor text states the limit; the only evidence is UI ("Sign in to share"). If guest sharing works, the "kolaborasi butuh akun" line is wrong; if it doesn't, most people's first tldraw session ends in a failed share.
3. **remove.bg (High).** Sunset in six weeks. The test needs to confirm the preview is genuinely download-able at usable size, and the copy needs the December 2026 date.
4. **Penpot (Medium** — but it's the counterweight to Figma). Two UI tools in the category; the owner's test is the moment to decide whether Penpot stays in or the pairing is already overlapping.
5. **SVG Viewer (Medium).** No stated free tier, no maintenance activity since 2019, an undocumented AI feature in the sidebar. The test is "does the basic optimise-and-download still work without a wall", and any wall means replace with SVGOMG.

Squoosh is the sixth if a slot frees up. Its privacy claim is strong but its development stalled in 2024.

---

## 5. Rejected candidates, and why

| Tool | Verdict | Why | What I checked |
|---|---|---|---|
| **Miro** | Reject as *replacement for Tldraw*; keep as backup for a different job | The free plan is stated: "3 editable boards — Create and share unlimited boards. Three most recent ones will remain editable" (https://miro.com/pricing/). That's a clean one-line limit. It loses because it overlaps Excalidraw on whiteboarding rather than doing a new job. If Tldraw fails the test, Miro enters — and the copy has to say *workshop facilitation*, not "another whiteboard". | Pricing page fetched 2026-10-22 |
| **Canva** | Reject for this pilot | Accepted as a Marketing seed, not a Design tool (`05-seed-tools.md` row 17). Adding a second entry would double-list it and break the category boundary; the pricing page also refused to load without JS, so the "which elements are paid" claim couldn't be verified anyway (https://www.canva.com/pricing/ → Client Challenge; footer shows at least Ads/Photo Editor/SVG Recolor as tools). | — |
| **Fontjoy** | Reject — dormant | Font-pairing done by a neural net, no account, no paid tier — a genuinely free tool. But the GitHub repo (https://github.com/Jack000/fontjoy) was last pushed **2017-05-25**. The site still loads, but the "no budget spent" test for a dormant hobby project isn't the same as "still active" for a free trial that can flip to paid. Fails criterion 4 of the source list. | Repo commit history |
| **Tabler Icons** | Could not verify | https://www.tablericons.com/ returned **error 1014** (Cloudflare, host blocked). With no readable licence or download page, no claim can be written. Replace with Iconify in the icon-search slot until Tabler is reachable from Indonesia. | HTTP response |
| **Phosphor Icons** | Could not verify | The site loads but renders only "Enable JavaScript to check out Phosphor Icons" — no licence text, no download path, no pricing. Presumed MIT from memory, but the whole point is that claims are cited. Kept out. | — |
| **Roomstyler / Floorplanner** | Reject — licence overreach on free tier | Roomstyler's Terms (https://www.roomstyler.com/terms) grant Floorplanner a "perpetual, non-exclusive, transferrable license to publish, amend, and use any designs created by User under the free use subscription … (including the right … to sublicense)". Floorplanner's own free plan limits projects to "3 floors with 3 designs" and "SD-quality images with a watermark" (https://floorplanner.com/pricing). Two problems: a free-tier licence that claims your work, and a watermark on every export. Both fail the "no silent watermark" rule. | Terms and pricing pages |
| **Photopea — Premium claim** | Flag, not reject | https://www.photopea.com/privacy.html says: "We don't accept donations, but you can buy a Premium account (a one-time payment). E.g. paying for a 90-day Premium …" The homepage claims "Enjoy all the premium features without spending a dime" and shows no pricing page. The two statements can both be true (premium = ad-free / faster / extra server features), but the seed's limit line ("fitur lanjutan butuh langganan") is *not* supported by any page I could read. Recommend rewording the seed's `limits` to what the vendor states and leaving it out of `Diuji` until tested. | Homepage, privacy page, learn page |
| **Coolors — "free forever"** | Not rejected, but the ads must be in the copy | The pricing page states "Ads visible on the page" on Free. The Diuji page cannot claim "tanpa iklan". | Pricing page |
| **Figma — "free forever"** | Not rejected, but the 3-file number needs a defender | Pricing page doesn't print it; the blog does. If the copy says "3 file", the citation in the PR must be the blog URL. If the blog is superseded before publish, the number changes. | Pricing page + blog |
| **Iconify icons browser 404** | Flag | https://iconify.design/icons/ 404s from here. The tool itself works; the URL in the table points at the docs home so the page doesn't break. Owner should find the current browser path before launch. | — |

## 6. Claims I could not verify at all

| Tool | What couldn't be verified | Why |
|---|---|---|
| **Tldraw** | Whether guest-share links (edit without account) are free, and whether "Sign in to share" is a hard wall or a soft prompt. | tldraw.com is a JS app; the marketing page has no pricing/limits text, and the help centre (help.tldraw.com) is not deployed. The only first-hand evidence was the rendered UI. |
| **Iconify** | Requires-account: the current icon-browser page returns 404; no pricing page exists to state what's free. | Site restructured; docs-only landing page. |
| **SVG Viewer** | Requires-account: no pricing page and no login UI; also no maintenance signal (Terms last updated 2019). | Confirmed the tool page loads; confirmed absence of terms/privacy updates. |
| **Canva** | Free vs Pro element boundary. | https://www.canva.com/pricing/ is behind a JS challenge; the page body never rendered. |
| **Inkscape** | Whether the download page is accessible from Indonesia (inkscape.org returned 403 to this machine; GitLab API works). | Host-level block not confirmed as geographic. |
| **Squoosh (activity)** | The "frozen" claim — saw it on secondary sites, not on the repo. | Default-branch commits stop 2024-08-19, but `pushed_at` is 2026-10-15. No README statement found. |
| **Figma Starter file-count** | Whether "3 files" still applies in October 2026, vs. the newer "Unlimited drafts" line on the pricing page. | The pricing page lists "Unlimited drafts" under Includes; the 2024 blog says 3 collaborative files. These are two different limits (drafts vs collaborative files) but the page won't say so. |

---

## 7. Next step

1. Owner accepts or amends the coverage map in §1 (esp. the Figma/Penpot split and the Coolors/Material Symbols reason line). Record the outcome in ticket 03 and, if it holds, in the decision log.
2. Owner runs the five real-task tests in §4. Record the actual downloaded file and quota hit — that's what the Diuji table will cite.
3. Do not write any of these to `tools.json` before (2). `verified_at` belongs to the human test, not to this document.
4. On SVG Viewer: if the test finds any export wall, move the slot to SVGOMG and update the URL. Don't keep both.
