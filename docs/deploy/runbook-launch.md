# Runbook peluncuran — dari repo ke https://gudangtool.web.id

Runbook ini adalah bentuk yang bisa dieksekusi dari daftar periksa tiket 11 (`.scratch/launch-stage-0/issues/11-bootstrapping-the-repo-and-deploy.md`).
Semua langkah memakai akun dan kredensial yang sudah ada; tidak ada langkah yang bergantung pada model.

**Status:** langkah A–C belum dijalankan. Pipeline CI sudah siap dan terbukti sampai gerbang yang salah.

---

## Prasyarat (sudah selesai, tidak perlu diulang)

| Hal | Nilai |
|---|---|
| Repo | `github.com/fanioz/gudangtool` (private), branch `main` |
| Pipeline | `.github/workflows/deploy.yml` — rsync → tukar symlink → sisakan 3 release → purge Cloudflare |
| Secret Actions | `SSH_HOST` `43.173.26.57`, `SSH_PORT` `4321`, `SSH_USER` `ubuntu`, `TARGET_PATH` `/var/www/gudangtool`, `SSH_PRIVATE_KEY`, `SSH_KNOWN_HOSTS` |
| Kunci deploy | `~/.ssh/gudangtool_deploy_ed25519` di Mac pemilik; pasangannya sudah ada di `authorized_keys` sumojak |
| Konfigurasi Caddy | `docs/deploy/Caddyfile.gudangtool` (siap ditempel) |

---

## Langkah A — satu kali di server (butuh sudo)

`/var/www` **belum ada** di sumojak. Caddy masih melayani `omni.pecutai.web.id` dan tidak boleh terganggu.

```bash
ssh sumojak

# 1. Direktori deploy
sudo mkdir -p /var/www/gudangtool/releases
sudo chown -R ubuntu:ubuntu /var/www/gudangtool

# 2. Blok situs Gudangtool (dari repo)
sudo tee -a /etc/caddy/Caddyfile < docs/deploy/Caddyfile.gudangtool

# 3. Validasi lalu muat ulang — jangan lewati validasi
sudo caddy validate --config /etc/caddy/Caddyfile && sudo systemctl reload caddy
```

Selesai bila `systemctl is-active caddy` mengembalikan `active` dan `caddy validate` tidak memunculkan error.

---

## Langkah B — Cloudflare (akun pemilik)

1. Tambah **dua zona** di satu akun: `gudangtool.web.id` dan `gudangtools.web.id` (Free).
   Satu zona per domain — Cloudflare membuat zona per domain yang bisa didaftarkan, dan keduanya adalah domain saudara.
2. Zona `gudangtool.web.id`: `A` → `43.173.26.57`, proxy **oranye**.
3. Zona `gudangtools.web.id`: `A` → `192.0.2.1`, proxy **oranye** (dummy — redirect menyala di edge, origin tidak pernah dihubungi), lalu **Bulk Redirect**: pola `gudangtools.web.id/*` → `https://gudangtool.web.id/*`, status 301.
4. SSL/TLS mode **Full (strict)** di kedua zona. Tanpa ini, Caddy yang sudah HSTS akan ditolak Cloudflare.
5. Catat pasangan NS yang diberikan Cloudflare untuk masing-masing zona — dipakai di langkah C.

---

## Langkah C — delegasi NS di registrar

Domain `gudangtool.web.id` terdaftar 2026-10-21 melalui **PT Exabytes Network Indonesia** (daftarnama.id),
NS saat ini `ns1/ns2.sumopod.com` — yang tidak menyajikan zona untuk domain itu, makanya domain gelap.
`.web.id` **memperbolehkan delegasi pihak ketiga**, jadi yang perlu diganti hanya Nameserver di panel registrar.

1. Masuk ke panel Exabytes/daftarnama.id.
2. Ganti NS `gudangtool.web.id` ke pasangan NS Cloudflare dari langkah B.
3. Ganti NS `gudangtools.web.id` ke pasangan NS Cloudflare dari langkah B (domain jamak sekarang juga di sumopod).
4. Verifikasi:

```bash
dig +short NS gudangtool.web.id     # harus pasangan Cloudflare
dig +short NS gudangtools.web.id    # harus pasangan Cloudflare
```

Setelah delegasi hidup, Caddy menerbitkan sertifikat sendiri pada percobaan berikutnya.
Bila sertifikat belum terbit, paksa sekali: `sudo systemctl reload caddy`.

---

## Langkah D — selesaikan pipeline

```bash
# Token API Cloudflare: Zone → Cache Purge → Purge, untuk zona gudangtool
gh secret set CLOUDFLARE_API_TOKEN -R fanioz/gudangtool -b"<token>"
gh secret set CLOUDFLARE_ZONE_ID  -R fanioz/gudangtool -b"<zone id>"

# Jalankan deploy
gh workflow run deploy.yml -R fanioz/gudangtool
gh run watch --repo fanioz/gudangtool
```

---

## Verifikasi akhir

```bash
curl -sI https://gudangtool.web.id | head -5          # 200 + cache-control
curl -s https://gudangtool.web.id | grep -o "sedang dibangun"   # isi placeholder
ssh sumojak 'ls -1 /var/www/gudangtool/releases'      # ada release
ssh sumojak 'readlink /var/www/gudangtool/current'    # symlink ke release terbaru
```

Bukti bahwa CI benar-benar menukar isi: ubah satu kalimat di `site/index.html`, commit ke `main`,
lalu ulangi `curl` di atas. Konten berubah tanpa ada perintah manual di server.

---

## Pemecahan masalah

| Gejala | Penyebab | Tindakan |
|---|---|---|
| `rsync: mkdir … Permission denied (13)` | `/var/www/gudangtool` belum ada atau salah pemilik | Langkah A |
| `No ED25519 host key is known` | Kunci host VPS berubah (server dibangun ulang) | `ssh-keyscan -p 4321 43.173.26.57 > /tmp/kh && gh secret set SSH_KNOWN_HOSTS -R fanioz/gudangtool < /tmp/kh` — jangan menyalin manual, itu yang sempat merusak run pertama |
| `Host key verification failed` | Baris `known_hosts` tidak cocok dengan host yang/presentation | Perbarui seperti baris di atas, lalu `gh run rerun` |
| Sertifikat tidak terbit | Domain belum ter-delegasi, atau DNS belum mengarah ke VPS | `dig +short A gudangtool.web.id` harus `43.173.26.57`; lalu `sudo systemctl reload caddy` |
| Cloudflare 525/526 | SSL mode belum Full (strict), atau sertifikat origin belum ada | Perbaiki mode SSL; tunggu penerbitan sertifikat |
| Placeholder 404 | Belum ada release — symlink `current` baru ada setelah rsync pertama | Jalankan langkah D, cek `readlink /var/www/gudangtool/current` |
