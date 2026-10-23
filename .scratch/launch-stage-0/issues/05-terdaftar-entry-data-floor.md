# Ticket: What is the minimum a `terdaftar` entry carries?

Type: grilling
Status: resolved
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

---

## Resolution — owner decisions

**2026-10-23.** Empat keputusan.

**Q1 — Dua ambang berbeda (b).** `diuji` butuh **3** data unik; `terdaftar` butuh **2**. Alasan: halaman `diuji` memang memuat semua field dan pantas disuruh lengkap; halaman `terdaftar` memang sengaja kosong klaimnya (aturan 4) dan tidak boleh dihukum seperti halaman yang berbohong. Menyeragamkan ambang berarti mematikan tier `terdaftar` dari indeks selamanya — padahal ia dibuat untuk "kami tahu ia ada, kami tidak mengklaim apa pun". Ini menyelaraskan `11-seo-architecture.md` §6 baris 90 dengan baris 99 dan dengan `14-repo-spec.md` §5/§6 yang sudah menulis 2; D19 konsekuensi yang menyebut "tiga data unik" untuk `terdaftar` digantikan oleh D23.

**Q2 — Field wajib tidak dihitung (b).** Yang **tidak** dihitung: `function` (wajib di semua entri, sama wajibnya dengan judul) dan `unknownList`/baris "Belum diperiksa" (itu kejujuran, bukan data). Yang **dihitung**:

1. Platform (dihitung satu titik berapa pun jumlah platformnya).
2. Alternatif berstatus `diuji` (dihitung satu titik berapa pun jumlah dan seberapa pun persamaan pasangannya — lihat Q4).

Ambang 2 untuk `terdaftar` = platform + **minimal satu alternatif `diuji`**. Field yang wajib dimiliki semua entri tidak boleh dihitung sebagai keunikan; kalau tidak, ambang selalu lolos dan aturan jadi teater. Konsekuensi yang disengaja: halaman `terdaftar` non-Desain (yang `alternatives`-nya `[]` karena kategorinya belum punya tool `diuji`) akan `noindex` saat peluncuran — itu yang membuat tiket 04 (strip "Baru masuk" + Pagefind) penting.

**Q3 — Tayang `noindex, follow` (a).** Halaman `terdaftar` tanpa satu pun alternatif `diuji` tetap dibangun, tampil di kategori dan di Pagefind, memakai `<meta name="robots" content="noindex, follow">`, dan tidak masuk sitemap. Ketika kategorinya nanti punya tool `diuji`, menambah field alternatif menaikkan halaman kelas **tanpa perubahan URL dan tanpa redirect**. Alternatif: mengeluarkan dari batch akan memutus tautan dari kategori/homepage; membuang dari katalog bertentangan dengan definisi `terdaftar`.

**Q4 — Keunikan dihitung per halaman (a).** Pasangan alternatif yang sama boleh muncul di banyak halaman `terdaftar`. Google menilai keunikan per halaman, bukan lintas halaman; alasan tiap alternatif memang hidup di halaman `diuji` masing-masing (yang berbeda-beda), bukan disalin ke halaman `terdaftar`. Aturan "semua pasangan alternatif harus beda" tidak bisa dijaga dan tidak sesuai cara mesin pencari menilai. Mitigasi risiko scaled content sudah ada: ambang 2 yang berarti, `noindex` untuk yang tidak lolos, dan setiap halaman `terdaftar` tetap memuat fungsi + platform + tautan keluar yang relevan.

### Perubahan dokumen

| Dokumen | Perubahan |
|---|---|
| `11-seo-architecture.md` §6 | Baris "minimal tiga" dipecah: 3 untuk `diuji`, 2 untuk `terdaftar`; daftar data unik diberi aturan hitung (field wajib tidak dihitung) |
| `14-repo-spec.md` §5/§6 | Tidak berubah — sudah menulis 2; konsisten dengan Q1 |
| D19 konsekuensi | Bagian "tiga data unik" untuk `terdaftar` digantikan D23 |

### Unblocks

- Ticket 07 (pipeline penulisan konten) sekarang tahu persis berapa field yang wajib diisi per tier.
- Fog "collection/ranking eligibility" tidak tersentuh — keputusan ini hanya menyangkut halaman tool.
