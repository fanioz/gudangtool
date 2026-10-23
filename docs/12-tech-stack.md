# Gudangtool — Technical Stack v3.0 (File-based, tanpa database)

**Tanggal:** 22 Oktober 2026
**Menggantikan:** v2.1 (PocketBase + SQLite)
**Batasan:** VPS 1 vCPU / 1 GB, Ubuntu LTS, dibangun AI agent, biaya langganan nol.
**Status:** rekomendasi Stage 0.

---

## 1. Keputusan

**Stage 0 tidak memakai database.** Data tool disimpan sebagai file JSON di dalam repo, divalidasi skema saat build, dan dirender Astro menjadi HTML statis.

Database baru dibutuhkan ketika ada **tulisan saat runtime** — submission, event klik, akun pengguna — atau ketika ada editor non-teknis yang butuh admin UI. Selama belum ada, database hanya menambah satu daemon, satu backup, dan satu titik gagal.

---

## 2. Kenapa file-based lebih tepat sekarang

| Alasan | Penjelasan |
|---|---|
| **Skema tetap bisa ketat** | Astro content collections memakai Zod; build gagal kalau field wajib hilang atau tipe salah |
| **Aturan bisnis bisa ditegakkan** | Entri `terdaftar` yang punya tabel batas atau klaim gratis otomatis gagal build |
| **Git menjadi audit log** | Setiap perubahan punya diff, pelaku, dan alasan; rollback = `git revert` |
| **Tidak ada backup database** | Backup = repo + artefak release |
| **Tidak ada daemon tambahan** | Hanya Caddy; RAM turun ke ±150–220 MB |
| **Agent mudah bekerja** | Satu file per tool, konflik jarang, review lewat PR |
| **Portabel** | Pindah ke database kapan saja dengan skrip impor |

Kekurangan yang harus diterima: editor non-teknis belum punya UI, dan setiap perubahan memerlukan rebuild.

---

## 3. Struktur repo

```
src/
  content/
    tools/
      excalidraw.json
      photopea.json
      ...
    categories/
      desain.json
      ai.json
    collections/
      gratis-tanpa-akun.json
    rankings/
      2026-10.json
  pages/
    tool/[slug].astro
    kategori/[slug].astro
    koleksi/[slug].astro
    ranking/[periode].astro
  components/
    ToolCard.astro
    TierBadge.astro
    LimitsTable.astro
```

Tidak ada `server/`, tidak ada `db/`, tidak ada API route untuk konten.

---

## 4. Skema data

### Entri Diuji

```json
{
  "name": "Excalidraw",
  "slug": "excalidraw",
  "tier": "diuji",
  "placement": false,
  "category": "desain",
  "function": "Papan gambar sketsa untuk diagram dan wireframe.",
  "platform": ["web"],
  "url": "https://excalidraw.com",
  "added_at": "2026-08-12",
  "verified_at": "2026-10-21",
  "price_status": "gratis",
  "requires_account": false,
  "limits": {
    "account": "Tidak perlu",
    "quota": "Tidak ada",
    "watermark": "Tidak ada",
    "export": "PNG, SVG, dan .excalidraw",
    "storage": "Browser (penyimpanan lokal)"
  },
  "why": "Bisa dipakai tanpa akun; hasil ekspor bersih.",
  "fit": "Diagram alur, wireframe kasar, penjelasan saat rapat.",
  "not_fit": "Ilustrasi detail, desain cetak, presisi vektor.",
  "alternatives": ["draw-io", "miro"]
}
```

### Entri Terdaftar

```json
{
  "name": "Krea",
  "slug": "krea",
  "tier": "terdaftar",
  "placement": false,
  "category": "ai",
  "function": "Platform gambar generatif untuk eksplorasi visual.",
  "platform": ["web"],
  "url": "https://www.krea.ai",
  "added_at": "2026-10-22",
  "verified_at": null,
  "price_status": null,
  "requires_account": null,
  "limits": null,
  "why": null,
  "fit": null,
  "not_fit": null,
  "alternatives": ["excalidraw"]
}
```

Perhatikan: semua field klaim **wajib null** untuk tier Terdaftar. Ini bukan konvensi — ini aturan yang divalidasi.

---

## 5. Aturan yang ditegakkan saat build

Build gagal jika:

1. `tier = diuji` tetapi `verified_at`, `limits`, `price_status`, `why`, `fit`, atau `not_fit` kosong.
2. `tier = terdaftar` tetapi salah satu field klaim tidak null.
3. `slug` duplikat.
4. `category` tidak ada di koleksi kategori.
5. `alternatives` merujuk tool yang tidak ada, atau berstatus `terdaftar`.
6. Teks entri `terdaftar` mengandung kata "gratis" (lint kata terlarang).
7. `placement = true` tetapi tidak ada penanda placement di halaman.
8. Kategori punya kurang dari 3 tool (tidak boleh tampil di navigasi).

Ini keunggulan utama file-based: **integritas data menjadi bagian dari build**, bukan hasil disiplin editor.

---

## 6. Apa yang menggantikan database

| Kebutuhan | Solusi tanpa database |
|---|---|
| Menyimpan tool | Satu file JSON per tool |
| Relasi kategori | Slug referensi + validasi build |
| Filter dan koleksi | Dihitung saat build dari data |
| Pencarian | Pagefind (indeks statis) |
| Ranking | Snapshot JSON bulanan dari log/analytics |
| Submission | Google Form, dengan fallback email (D27) |
| Moderasi | Label issue + PR review |
| Edit oleh non-teknis | Belum ada; agent + PR |
| Analytics | Cloudflare Web Analytics |
| Event klik | Ditunda; pageview sebagai proksi |
| Backup | Git + artefak release |

---

## 7. Alur submission

1. Tombol "Titip tool" membuka **GitHub Issue Form** dengan field: nama, URL, kategori, fungsi satu kalimat, status gratis yang diklaim, email.
2. Issue diberi label `submission`.
3. Agent memeriksa; jika layak, membuat file JSON di branch baru dan membuka PR.
4. PR di-review, lalu merge. Build berjalan, halaman tayang.

Keuntungan: tidak ada server form, tidak ada spam bot, dan seluruh percakapan tersimpan sebagai audit. Kekurangan: pengaju harus punya akun GitHub. Untuk pembuat tool, itu wajar; sediakan email sebagai fallback.

---

## 8. Ranking tanpa database

- Caddy menulis access log JSON.
- Skrip build menghitung jumlah pembukaan halaman `/tool/*` per bulan, dengan filter bot berdasarkan user-agent.
- Hasilnya disimpan sebagai `src/content/rankings/2026-10.json`.
- Halaman ranking hanya menampilkan tool berlabel **Diuji** dan hanya jika minimal 100 pembukaan.
- Tidak ada pelacakan klik pada Stage 0. Pageview adalah proksi yang cukup untuk "paling sering dibuka".

Jika nanti butuh klik dan simpan yang presisi, di situlah database mulai masuk akal.

---

## 9. Deploy

Sama seperti sebelumnya:

```
git push → GitHub Actions
  ├─ astro check (validasi skema)
  ├─ astro build
  ├─ pagefind
  └─ rsync ke /var/www/gudangtool/releases/{timestamp}

VPS:
  Caddy menyajikan current/ (symlink)
  cron 6 jam → rebuild
```

Tidak ada reverse proxy API, tidak ada service PocketBase, tidak ada port 8090.

---

## 10. Kapan database benar-benar dibutuhkan

Tambahkan database hanya jika salah satu pemicu ini terjadi:

| Pemicu | Ambang |
|---|---|
| Editor non-teknis | Ada orang yang tidak bisa memakai git/PR |
| Submission | >50 pengajuan per minggu |
| Akun pengguna | Simpan/bookmark yang perlu sinkron antar perangkat |
| Ranking presisi | Butuh klik dan simpan, bukan hanya pageview |
| Katalog | >10.000 tool atau build >10 menit |
| Konflik konten | Dua agent sering mengedit file yang sama |

Urutan penambahan: **PocketBase + SQLite** dulu. PostgreSQL + Directus hanya jika ada banyak editor atau kebutuhan transaksi bersamaan.

---

## 11. Jalur migrasi (jika database ditambahkan)

1. Skema JSON sudah menyerupai kolom database; impor satu kali dengan skrip.
2. PocketBase menjadi sumber data; file JSON menjadi ekspor cadangan.
3. Astro tetap membangun halaman secara statis; hanya sumber datanya berubah.
4. Halaman publik tidak berubah — tidak ada migrasi URL.

Karena skema sudah eksplisit, perpindahan ini tidak memerlukan penulisan ulang template.

---

## 12. Sumber daya dan biaya

| Komponen | RAM |
|---|---|
| Ubuntu LTS minimal + SSH | 150–220 MB |
| Caddy | 25–40 MB |
| **Total** | **±175–260 MB** |

Sisa RAM untuk page cache. Swap 1 GB tetap disarankan, tetapi tidak lagi kritis karena tidak ada database yang menulis saat runtime.

**Biaya:** Rp 0/bulan + domain. Tidak ada PocketBase, tidak ada GoatCounter, tidak ada layanan tambahan.

---

## 13. Risiko

| Risiko | Mitigasi |
|---|---|
| Konflik git antar-agent | Satu file per tool; PR kecil; hindari edit massal |
| Data tidak konsisten | Skema Zod + aturan build |
| Submission butuh GitHub | Sediakan email fallback |
| Ranking tercemar bot | Filter user-agent + ambang minimum |
| Rebuild basi | Jadwal 6 jam + tombol manual |
| Repo membengkak | File JSON kecil; gambar disimpan di `public/` atau R2 |

---

## 14. Keputusan terbuka

1. **Form submission:** GitHub Issue Form atau Tally?
2. **Email fallback:** alamat mana yang dipakai?
3. **Ranking:** dari access log Caddy atau ekspor Cloudflare Web Analytics?
4. **Repo:** privat atau publik? (menentukan kuota GitHub Actions)
