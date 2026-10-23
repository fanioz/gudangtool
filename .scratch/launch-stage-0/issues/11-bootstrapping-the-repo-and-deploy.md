# Ticket: How does an empty VPS become a served site?

Type: task
Status: claimed
Blocked by: 01, 09

## Question

What are the exact steps, in order, to go from an empty `~/code/blog/gudangtool` to `https://gudangtool.web.id` serving a built site, and what must exist on the VPS before the first automated deploy can work?

## Detail

`14-repo-spec.md` §11 specifies the deploy: Actions → rsync → symlink swap → 3 releases kept → Cloudflare purge. `12-tech-stack.md` §9 adds a 6-hour cron rebuild.

None of that can run until some one-time state exists. This ticket is the checklist for that state — it does not decide anything, it does a thing that unblocks every deploy ticket.

Known facts: `sumojak` reachable, Caddy installed at `/usr/bin/caddy`, 2 vCPU / 1.9 GB. `sumoclaw` down.

The checklist must cover:

1. Create the git repo in `~/code/blog/gudangtool`, initial commit of existing `docs/` (with `.DS_Store` removed, or `.gitignore` it).
2. GitHub repo `fanioz/gudangtool` — private (launch-plan §6 #3 recommends private while content is unready).
3. SSH key / deploy user on `sumojak`; does root SSH in as root or should a `deploy` user exist?
4. Directory `/var/www/gudangtool/{releases,current}` and permissions.
5. Caddyfile skeleton with the domain, root `current/`, headers from `14-repo-spec.md` §12. Not yet serving — no release exists.
6. GitHub Actions secrets: SSH host, user, key, target path.
7. Cloudflare zone for `gudangtool.web.id` — verify nameserver change is possible for `.web.id`.

Resolved when: a placeholder `index.html` is reachable at the domain over HTTPS, and a test commit on `main` replaces it via CI.

## Comments

### 2026-10-23 — sesi agent: bagian AFK selesai, menunggu langkah pemilik

**Keputusan (dalam lingkup tugas):**

- Deploy sebagai **`ubuntu`** (konvensi D25 "SSH publik + kunci"), bukan user root dan bukan user `deploy` baru — satu admin VPS, user terpisah hanya menambah beban rawat.
- Aksi GitHub Actions memakai **keypair khusus** `~/.ssh/gudangtool_deploy_ed25519` (di Mac pemilik), bukan kunci pribadi pemilik — bisa dicabut sendiri di `~/.ssh/authorized_keys` sumojak tanpa menyentuh akses pemilik.

**Checklist yang sudah selesai (1, 2, 3, 6):**

1. Repo git di folder kerja ini, branch `main`, `.gitignore` menutup `.DS_Store` — sudah ada sebelum sesi, terverifikasi. (`~/code/blog/gudangtool` ditinggalkan sesuai catatan map.)
2. Repo GitHub `fanioz/gudangtool` — private, default `main`, sinkron — sudah ada sebelum sesi.
3. Kunci deploy terpasang di `authorized_keys` sumojak; login dengan kunci itu terverifikasi.
4. Workflow `.github/workflows/deploy.yml` (push `main` + manual): stage → rsync ke `releases/<timestamp>` → tukar symlink `current` → sisakan 3 release → purge Cloudflare (langkah terakhir lewati otomatis bila token belum diisi). Halaman placeholder `site/index.html` (`noindex`, bahasa Indonesia). Langkah build masih placeholder `site/` → `dist/`; diganti `npm ci && npm run build` saat fog "Scaffolding" tumbuh jadi tiket.
5. Enam secret Actions terisi: `SSH_HOST`, `SSH_PORT` (4321), `SSH_USER` (ubuntu), `SSH_PRIVATE_KEY`, `SSH_KNOWN_HOSTS` (pin host key ed25519 — TOFU dihindari), `TARGET_PATH=/var/www/gudangtool`. `CLOUDFLARE_API_TOKEN`/`CLOUDFLARE_ZONE_ID` sengaja belum diisi.
6. CI terbukti sampai gerbang: run [39892195851](https://github.com/fanioz/gudangtool/actions/runs/39892195851) gagal **tepat** di `mkdir /var/www/gudangtool/releases/… → Permission denied` — persis prasyarat root satu kali di bawah. Semua sebelumnya (checkout, stage, SSH dengan kunci deploy + host key pin, koneksi rsync) hijau. Catatan: run pertama gagal di host key karena saya menyalin base64 pin secara manual dan mengubah satu karakter; diperbaiki dengan menyalurkan file keyscan langsung ke `gh secret set`. Konsekuensi sementara: setiap commit ke `main` akan memerah di langkah rsync sampai langkah A di bawah selesai — itu tripwire yang disengaja, bukan regresi.

**Fakta baru (DNS, jawaban untuk D25):**

- `gudangtool.web.id` **terdaftar** 2026-10-21 (RDAP `31651918_DOMAIN_ID-ID`), registrar **PT Exabytes Network Indonesia** (daftarnama.id), kadaluarsa 2027-10-21. NS saat ini `ns1/ns2.sumopod.com`, tetapi sumopod **tidak menyajikan zona** untuk domain ini → delegasi kosong (lame) → domain gelap. Tidak ada yang rusak bila NS dipindah.
- `.web.id` **terbukti mendukung delegasi NS pihak ketiga** — domain ini sekarang sudah didelegasikan ke sumopod, bukan NS registrar. Pertanyaan verifikasi manual di D25 terjawab; sisa langkahnya hanya swap NS di panel registrar.
- `gudangtools.web.id` (jamak) juga terdaftar, NS sumopod; zonanya ada tapi tanpa record A — juga aman dipindah.
- Catatan teknis untuk D25: "satu zona Cloudflare" secara teknis = **satu akun Cloudflare dengan dua zona** (Cloudflare membuat zona per domain yang bisa didaftarkan; `gudangtool.web.id` dan `gudangtools.web.id` adalah dua domain saudara). Substansi keputusan tidak berubah: satu tempat konfigurasi, redirect di edge.

**Checklist pemilik (urut, copy-paste):**

A. **Root sekali di sumojak** (kebijakan proyek melarang agent memakai sudo):

Daftar periksa lengkapnya sudah menjadi runbook di repo: [`docs/deploy/runbook-launch.md`](../../../docs/deploy/runbook-launch.md), dengan blok Caddy siap ditempel di [`docs/deploy/Caddyfile.gudangtool`](../../../docs/deploy/Caddyfile.gudangtool).

```bash
ssh sumojak
sudo mkdir -p /var/www/gudangtool/releases
sudo chown -R ubuntu:ubuntu /var/www/gudangtool
sudo tee -a /etc/caddy/Caddyfile < docs/deploy/Caddyfile.gudangtool
sudo caddy validate --config /etc/caddy/Caddyfile && sudo systemctl reload caddy
```

Catatan: `/var/www` sendiri **belum ada** di sumojak (diverifikasi 2026-10-23) — `mkdir -p` yang membuatnya. `encode gzip zstd` mengikuti Caddyfile yang berjalan (Brotli bukan bawaan Caddy standar) — menyimpang dari §12 "Brotli/gzip"; dicatat sebagai fakta, bukan perubahan spec. Blok `404` kustom menyusul bersama scaffold (placeholder belum punya 404.html).

B. **Cloudflare** (akun pemilik): tambah zona `gudangtool.web.id` + `gudangtools.web.id` (Free, satu akun). Zona gudangtool: `A @ → 43.173.26.57` proxy oranye. Zona gudangtools: `A @ → 192.0.2.1` proxy oranye (dummy; redirect menyala di edge) + **Bulk Redirect** 301 `gudangtools.web.id/*` → `https://gudangtool.web.id` + SSL mode **Full (strict)** di kedua zona.

C. **Registrar** (panel Exabytes/daftarnama.id): ganti NS kedua domain ke pasangan yang diberikan Cloudflare. Setelah delegasi hidup (`dig NS gudangtool.web.id`), Caddy menerbitkan sertifikat otomatis di percobaan berikutnya — bila perlu, `sudo systemctl reload caddy` sekali lagi.

D. **Kembali ke CI**: isi dua secret sisanya lalu jalankan ulang deploy:

```bash
gh secret set CLOUDFLARE_API_TOKEN -R fanioz/gudangtool -b"<token Zone.Cache Purge>"
gh secret set CLOUDFLARE_ZONE_ID -R fanioz/gudangtool -b"<zone id gudangtool>"
gh workflow run deploy.yml -R fanioz/gudangtool
```

Placeholder harus hidup di `https://gudangtool.web.id`. Lalu satu commit isi (misal ubah kalimat placeholder) membuktikan swap via CI — kondisi "resolved when" tercapai dan tiket ini bisa ditutup.

### 2026-10-23 (sesi kedua) — checklist dipindah ke runbook, preflight ditambahkan

Pemilik belum menjalankan langkah manual (diverifikasi: `/var/www` belum ada, Caddyfile sumojak belum berubah, delegasi NS `gudangtool.web.id` masih kosong). Supaya langkah HITL semurah mungkin:

- Checklist A–D dipindah ke [`docs/deploy/runbook-launch.md`](../../../docs/deploy/runbook-launch.md) — termasuk tabel verifikasi akhir (curl, `readlink`, `ls releases`) dan tabel pemecahan masalah (host key berubah, sertifikat belum terbit, 525/526, 404 placeholder).
- Blok Caddy dipisah ke [`docs/deploy/Caddyfile.gudangtool`](../../../docs/deploy/Caddyfile.gudangtool) — owner menempel file yang sudah direview, bukan menyalin dari komentar.
- Pipeline tambah langkah **"Cek prasyarat di VPS"** sebelum rsync. Kegagalan sekarang berhenti dengan pesan yang menyebut runbook, bukan `Permission denied` mentah. Terbukti di run [39938660476](https://github.com/fanioz/gudangtool/actions/runs/39938660476): gagal tepat di preflight dengan pesan "Jalankan langkah A di docs/deploy/runbook-launch.md".

Status tiket tetap **claimed** — hanya pemilik yang bisa menyelesaikan langkah A–C.
