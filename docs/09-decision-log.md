# Decision Log — Gudangtool

Catatan keputusan berurutan, alasan di baliknya, dan hal-hal yang sudah tidak berlaku. Dokumen ini yang menjadi acuan ketika materi lama bertentangan dengan arah baru.

---

## 21 Oktober 2026

### D1. Nama domain: `gudangtool.web.id`

**Keputusan:** memakai `gudangtool.web.id`, bukan `laci.web.id` (sudah diambil), `awesometool`, atau kandidat lain.

**Alasan:** "gudang" adalah metafora wadah yang menyiratkan kurasi, mudah diingat, dan berbahasa Indonesia. `awesometool` gugur karena merupakan frasa generik yang dipakai untuk memuji produk apa pun — nol diferensiasi dan mustahil bersaing di SEO.

**Konsekuensi:** penulisan wordmark satu kata, huruf kecil. "Gudang Tool" dengan spasi tidak dipakai sebagai nama.

### D2. Logo: Arah A "Rak & Peti"

**Keputusan:** simbol rak dengan peti, bukan peti terbuka (B) atau label stiker (C).

**Alasan:** paling skalabel hingga 16px, tidak memakai ikon perkakas, dan bisa digambar ulang tanpa kehilangan makna. Arah C tetap dipakai sebagai bahasa label untuk kartu dan badge.

### D3. Identitas visual

**Keputusan:** paper `#F6F3EE`, ink `#12212E`, accent `#C24A18`, verified `#3E7C5A`, kraft `#C8A27A`. Space Grotesk / Inter / JetBrains Mono. Radius 2–4px, tanpa bentuk pil.

**Alasan:** oranye terang awal (`#F26B3A`) gagal uji kontras; diturunkan sampai lolos 4.5:1 untuk teks tombol. Font open-source karena produknya tentang tool gratis.

### D4. Positioning awal: katalog kurasi kecil

**Keputusan:** "sedikit tapi semua diuji", dengan kalimat penolakan terhadap direktori besar.

**Status:** **DIGANTIKAN pada 22 Oktober 2026** oleh D8. Kalimat "Direktori lain bisa memuat ribuan tautan. Kami memilih jumlah yang bisa dipertanggungjawabkan" tidak boleh dipakai lagi.

### D5. 20 tool pertama

**Keputusan:** 20 kandidat di 8 kategori, semuanya berstatus belum diverifikasi (`verified: false`).

**Alasan:** tanpa isi, copy sebagus apa pun hanya janji. Daftar disusun sebagai antrean kandidat, bukan konten tayang.

### D6. Template halaman kategori dan detail

**Keputusan:** halaman detail menampilkan status dan tabel batas gratis sebelum penjelasan panjang; wajib ada "Tidak cocok untuk" dan riwayat pemeriksaan.

**Alasan:** konsistensi struktur inilah yang membuat janji kejujuran bisa dipercaya. Tool tanpa kelemahan berarti belum diuji.

### D7. Lembar uji 5 tool paling rawan

**Keputusan:** protokol 15 menit per tool, empat status final (Gratis / Freemium / Butuh akun / Tolak), aturan "kalau ragu, pilih Freemium".

**Status:** tetap berlaku, tetapi hanya untuk tier "Diuji" setelah pivot — bukan untuk seluruh katalog.

---

## 22 Oktober 2026

### D8. Pivot: direktori berskala dengan monetisasi

**Keputusan:** Gudangtool berubah dari katalog kurasi kecil menjadi direktori besar dengan:
- skala katalog dan model bisnis direktori,
- UX ala Toolify (pencarian di depan, kategori rapat, kartu padat, alur submit),
- data lengkap (harga, popularitas, ranking),
- SEO seluas mungkin,
- pendapatan dari AdSense dan placement berbayar.

**Alasan:** pemilik proyek menargetkan situs ini sebagai mesin penghasilan, bukan proyek kurasi.

**Konsekuensi langsung:**
- Kalimat anti-direktori di halaman depan dihapus.
- Klaim "tidak ada tool yang masuk karena membayar" diubah menjadi "tidak ada peringkat yang dijual; placement diberi label".
- QA 15 menit tidak lagi berlaku untuk semua tool; hanya tier "Diuji".
- Dibutuhkan label verifikasi **Diuji** dan **Terdaftar**, plus penanda komersial **Berbayar**.

**Yang tidak berubah:** nama, logo A, sistem visual, dan tabel batas gratis sebagai data pembeda.

### D9. Model pendapatan berurutan

**Keputusan:** urutan monetisasi adalah placement & submission lebih dulu, AdSense menyusul.

**Alasan:** dengan asumsi RPM $0,5–2, AdSense baru berarti setelah ratusan ribu pageview. Placement bisa menghasilkan $300–1.000/bulan pada trafik puluhan ribu.

**Aturan yang tidak boleh dilanggar:** slot bisa dijual, peringkat tidak.

### D10. Data popularitas

**Keputusan:** memakai data sendiri (pembukaan kartu, simpan) sebelum membeli data trafik pihak ketiga.

**Alasan:** angka pihak ketiga mahal dan tidak bisa dipertanggungjawabkan tanpa mencantumkan sumber. Data sendiri jujur, gratis, dan unik.

### D11. Batas kategori

**Keputusan:** 8 kategori utama + maksimal 40 "lorong" sebagai subkebutuhan. Tidak meniru 459 kategori Toolify.

**Alasan:** taksonomi mesin memecah otoritas SEO menjadi ribuan halaman tipis dan tidak sesuai dengan cara orang mencari.

### D12. Copy halaman depan v2.0

**Keputusan:** `03-homepage-copy.md` ditulis ulang menjadi v2.0 dengan struktur direktori: pencarian di depan, kategori, "baru masuk", "paling sering dibuka", koleksi berbasis batasan, ranking bulanan, penjelasan tiga label, dan jalur submit.

**Alasan:** v1.0 masih memuat kalimat anti-direktori dan seksi "kenapa isinya lebih sedikit" yang bertentangan langsung dengan pivot. Membiarkannya berarti situs berbohong pada dirinya sendiri.

**Konsekuensi:** kalimat "direktori lain memuat ribuan tautan" dan seksi "kenapa lebih sedikit" resmi dihapus. Ranking hanya tayang jika ambang data terpenuhi; angka tidak boleh dipalsukan.

### D13. Working agreement

**Keputusan:** seluruh pekerjaan proyek GudangTool dilakukan di `workspace/gudangtool/`. Repo `~/code/blog/gudangtool` tidak disentuh kecuali diminta.

**Alasan:** folder tersebut berada di dalam workspace agen sehingga bisa dibaca dan ditulis; repo berada di luar sandbox.

**Konsekuensi:** dokumen di `workspace/gudangtool/docs/` menjadi working copy resmi. Sinkronisasi ke repo dilakukan manual bila diperlukan.

### D14. Penyelarasan seluruh dokumen dengan arah direktori

**Keputusan:** setelah audit, dokumen berikut diperbarui agar tidak lagi bertentangan dengan pivot:

| Dokumen | Perubahan |
|---|---|
| `01-brand-brief.md` | Ditulis ulang ke v2.0: positioning direktori, tiga pilar baru, tiga label, peta kompetitif, metrik |
| `02-visual-identity.md` | v1.1: badge verifikasi dan penanda komersial, kartu ringkas, baris ranking, aturan slot iklan |
| `04-category-and-tool-copy.md` | v2.0: tiga keadaan halaman detail (Diuji / Terdaftar / Berbayar), copy ranking dan submit |
| `05-seed-tools.md` | v1.1: kriteria entri Terdaftar, rasio verifikasi, target skala |
| `06-tools.json` | v2: setiap entri punya `tier` dan `placement` |
| `07-qa-test-sheet.md` | v1.1: protokol hanya untuk tier Diuji |
| `preview/homepage-preview.html` | Ditandai sebagai arsip pra-pivot |

**Alasan:** audit menemukan beberapa dokumen masih memakai asumsi katalog kecil — terutama `01` dan `04`. Membiarkannya berarti dua sumber kebenaran yang saling bertentangan.

**Konsekuensi:** `03-homepage-copy.md` v2.0 dan `04` v2.0 menjadi acuan copy. Dokumen lama tidak dihapus, tetapi diberi banner status.

### D15. Arsitektur SEO dan tipe halaman

**Keputusan:** dibuat `11-seo-architecture.md` yang menetapkan sepuluh tipe halaman, pola URL, syarat indeks, pola title/meta, aturan internal linking, dan ambang batch.

**Alasan:** arah "SEO seluas mungkin" tanpa batas halaman akan menghasilkan ribuan halaman tipis — persis profil yang dihukum kebijakan scaled content abuse. Dokumen ini mengubah ambisi menjadi aturan yang bisa diperiksa.

**Konsekuensi:** halaman di bawah ambang tidak diindeks. Batch pertama 300 halaman; penambahan hanya dilakukan jika rasio indeks minimal 60%.

### D16. Batasan teknis proyek

**Keputusan:** situs dibangun oleh AI agent, tanpa biaya langganan, di VPS 1 vCPU / 1 GB RAM.

**Konsekuensi:**
- Hanya Caddy yang berjalan sebagai daemon. PocketBase tidak dipakai di Stage 0; GoatCounter dicabut dan diganti Cloudflare Web Analytics.
- Tidak memakai Docker, Directus, PostgreSQL, Meilisearch, atau PocketBase.
- Build 3.000 halaman dilakukan di GitHub Actions, bukan di VPS.
- Swap 1 GB dan `MemoryMax` systemd tetap disarankan, walau tidak lagi kritis.
- Rekomendasi lengkap ada di `12-tech-stack.md` v3.0.

### D17. Stage 0 tanpa database

**Keputusan:** data tool disimpan sebagai file JSON di repo, divalidasi skema saat build. Tidak ada PocketBase atau SQLite di Stage 0.

**Alasan:** belum ada tulisan saat runtime. Git memberi audit log dan rollback; aturan tier bisa ditegakkan saat build; satu daemon lebih sedikit berarti satu titik gagal lebih sedikit dan RAM VPS lebih lega.

**Konsekuensi:**
- Submission lewat GitHub Issue Form atau email, bukan API.
- Ranking dihitung dari access log Caddy, bukan tabel event.
- Database baru ditambahkan jika: ada editor non-teknis, submission >50/minggu, butuh akun pengguna, butuh ranking klik yang presisi, atau katalog >10.000 tool.

### D18. Scope peluncuran Stage 0 dikunci ulang

**Keputusan:** enam hal dikunci ulang untuk Stage 0. Beberapa **menggantikan** keputusan sebelumnya — bagian yang digantikan tetap tercatat, tidak dihapus.

| # | Keputusan | Status terhadap log ini |
|---|---|---|
| 1 | Meluncur di `gudangtool.web.id`; upgrade ke `gudangtool.id` direncanakan sebagai 301 di kemudian hari, bukan keputusan peluncuran | Melanjutkan D1; tidak bertentangan |
| 2 | Kategori percontohan **hanya Desain**, bukan Desain + AI | **Menggantikan** `13-launch-plan.md` §6 #1 dan P0 #2 |
| 3 | `gudangtools.web.id` (jamak) **301 ke** `gudangtool.web.id`; tidak pernah diindeks | Keputusan baru; belum pernah dicatat |
| 4 | Skala peluncuran **50 halaman**, bukan batch pertama 300 halaman | **Menggantikan** `11-seo-architecture.md` §5 untuk batch pertama |
| 5 | Verifikasi **hibrida**: agent memeriksa mekanis (dinding akun, watermark, teks kuota), pemilik proyek menjalankan tugas nyata 10 menit lalu menilai `fit` dan `not_fit` | **Menggantikan** protokol tunggal 15 menit di D7 dan `05-seed-tools.md` §4 |
| 6 | Repo kerja adalah folder workspace `gudangtool/`; di-`git init`, dipush ke GitHub `fanioz/gudangtool`. `~/code/blog/gudangtool` **tidak dipakai** | **Menggantikan** D13 |

**Alasan:**

- **#2 dan #4** saling terkait. Dengan 50 tool, delapan kategori masing-masing hanya memuat 5 tool — tidak ada yang mencapai ambang indeks 12. Memilih dua kategori peluncuran berarti dua kategori setengah kosong yang sama-sama tidak bisa diindeks. Satu kategori yang selesai membuktikan model; dua yang terbelah tidak membuktikan apa-apa. Ini sejalan dengan `13-launch-plan.md` §9: "bukti dulu, skala kemudian".
- **#4** juga menyelamatkan ambang di `11-seo-architecture.md` §5 dari menjadi aturan mati. Batch 300 halaman tetap berlaku sebagai batas atas untuk penambahan berikutnya; ia bukan target peluncuran.
- **#3** mencegah dua domain menayangkan konten serupa dan memecah otoritas tautan sebelum ada yang bisa dibagi.
- **#5** menjaga arti kata "Diuji": seseorang benar-benar memakai tool itu. Bagian mekanis boleh diamati agent, tetapi penilaian `fit` dan `not_fit` harus datang dari manusia. Protokolnya sendiri dirinci di `.scratch/launch-stage-0/issues/03-verification-protocol-for-two-testers.md`.
- **#6** D13 dibuat ketika repo tujuan berada di luar sandbox agent. Pindah ke folder workspace menghapus langkah sinkronisasi manual yang sebelumnya harus dijaga manusia.

**Konsekuensi:**

- `13-launch-plan.md` §6 #1 (kategori peluncuran) dan §2 P0 #2 tidak lagi menjadi acuan; ganti dengan D18 #2.
- `11-seo-architecture.md` §5: batch pertama dibaca sebagai "penambahan berikutnya setelah peluncuran", bukan "isi peluncuran".
- `05-seed-tools.md` §4 diganti protokol hibrida; lembar uji `07-qa-test-sheet` tetap dipakai sebagai alat pencatatan, bukan sebagai definisi protokol.
- Keputusan yang masih terbuka #2 (rasio tier) tetap terbuka, tetapi di bawah D18 #2 yang berlaku adalah rasio katalog keseluruhan, bukan per kategori.

### D19. Skema kanonis dan jalur konversi seed

**Keputusan:** `docs/14-repo-spec.md` §4 adalah skema kanonis. `docs/06-tools.json` diarsipkan menjadi `docs/06-tools-seed.json` dan tidak lagi menjadi sumber data.

| Hal | Keputusan |
|---|---|
| Jalur konversi | Skrip satu kali: 20 seed → file produksi; 30 sisanya ditulis tangan dari skema |
| Lokasi file | Satu file per tool di `src/content/tools/` |
| `alternatives` | Boleh `[]` bila belum ada tool `diuji` yang sebanding; setiap item yang ada wajib bertier `diuji` |
| `internal_note` | **Objek** `{sources, evidence, note}`, bukan string |
| Field baru | `observed_at`, `observed_by` (lihat D18 #5) |
| Seed | Diarsipkan, tidak dihapus |

**Alasan:**

- Satu file per tool karena `AGENTS.md` §7 mengizinkan content agent mengoreksi satu file per PR. Satu file besar berarti setiap PR berkonflik.
- `alternatives: []` menghindari tautan lintas kategori yang menyesatkan. Tool Video yang belum punya pembanding teruji lebih jujur tanpa seksi alternatif daripada menautkan ke Figma.
- `internal_note` sebagai objek karena build harus bisa memastikan setiap entri `diuji` punya sumber untuk tiap klaim dan punya bukti. String bebas tidak bisa diperiksa mesin.

**Konsekuensi:**

- `07-qa-test-sheet.md` v2.0 disesuaikan: `internal_note.sources` dan `internal_note.evidence` wajib untuk `diuji`.
- `tier: diuji` gagal build bila `observed_at`, `observed_by`, `internal_note.sources`, atau `internal_note.evidence` kosong.
- Halaman `terdaftar` dengan `alternatives: []` yang tidak memenuhi tiga data unik tetap `noindex`.

### D20. Matriks penegakan aturan build

**Keputusan:** delapan aturan build dari `12-tech-stack.md` §5 dipetakan ke mekanisme penegakan, dicatat di `14-repo-spec.md` §5 sebagai matriks penegakan.

| Mekanisme | Aturan |
|---|---|
| Zod `superRefine` | 1 (field klaim `diuji`), 2 (field klaim `terdaftar` null), 4 (kategori ada), 5 (`alternatives` sah) |
| Content collection | 3 (`slug` unik — key unik per file) |
| Script `validate:content` | 6 (lint "gratis" pada `function`, `why`, `fit`, `not_fit`, meta description) |
| Script pasca-build | 7 (penanda "Placement" ada di HTML) |
| Logika navigasi | 8 (kategori <3 tool disembunyikan dari navigasi) |
| Template per halaman | Threshold `noindex` dihitung saat render; tidak ada manifest terpisah |

**Alasan:**

- Aturan 1–5 adalah validasi data murni: satu file yang melanggar membuat `astro check` gagal sebelum halaman dirender.
- Aturan 6 butuh lint teks terpisah karena Zod tidak bisa memeriksa substring case-insensitive pada lintas field.
- Aturan 7 adalah satu-satunya yang butuh pandangan manusia, tetapi script memeriksanya otomatis di HTML hasil render — menangkap bug template yang tidak terlihat di data.
- Threshold `noindex` dihitung oleh template karena menambah manifest berarti menambah sumber kebenaran kedua. Sitemap script menghitung ulang secara independen; perbedaan adalah bug.

**Konsekuensi:**

- `astro check` (Zod) adalah gerbang pertama; `validate:content` adalah gerbang kedua.
- Script pasca-build untuk penanda placement adalah bagian dari `check:links` atau script terpisah di `scripts/`.
- `noindex` tidak perlu koordinasi lintas komponen: template menghitung sendiri.

### D21. Taksonomi kategori dan lorong saat peluncuran

**Keputusan:** delapan kategori tetap tayang sebagai halaman, tetapi **hanya Desain yang diindeks**. Tujuh kategori lain `noindex` sampai mencapai ambang 12 tool. **Tidak ada lorong (subcategory) yang tayang saat peluncuran** meski field `subcategory` ada di skema. Homepage memakai strip "Baru masuk" lintas kategori plus Pagefind untuk penemuan di luar Desain.

| Hal | Keputusan |
|---|---|
| Kategori tayang | Semua 8; hanya Desain (≥12 tool) terindeks, 7 lainnya `noindex` |
| Lorong | Ditunda; tayang saat satu kategori punya ≥8 tool dengan kebutuhan serupa |
| URL lorong (ketika tayang) | `/kategori/{slug}/{lorong}` |
| Penemuan lintas kategori | Strip "Baru masuk" di homepage + Pagefind (termasuk halaman `noindex` untuk pencarian di-situs) |

**Alasan:**

- 50 tool dibagi 8 kategori = rata-rata 6 per kategori; hanya Desain (15) yang lolos ambang 12. Tujuh halaman `noindex` yang jujur lebih baik daripada tujuh kategori yang disembunyikan — navigasi tetap utuh dan pengunjung tetap bisa menemukan tool-nya.
- Lorong di bawah ambang 8 akan menghasilkan halaman tipis — persis yang dihindari `11-seo-architecture.md`. Field dan pola URL didokumentasikan agar keputusan ini bisa dibalik tanpa migrasi.
- Strip "Baru masuk" adalah satu-satunya permukaan terindeks yang menjangkau luar Desain; Pagefind menutup sisanya tanpa mengandalkan indeks mesin pencari.

**Konsekuensi:**

- Navigasi menampilkan 8 kategori; hanya Desain yang lolos ke sitemap.
- `11-seo-architecture.md` §5 (lorong ≥8) tetap berlaku sebagai syarat tayang ketika keputusan ini dibuka kembali.
- Ticket 10 (homepage) memakai strip "Baru masuk" + Pagefind, bukan daftar kategori terindeks.

---

## Hal yang sudah kedaluwarsa

| Materi | Status | Tindakan |
|---|---|---|
| Kalimat "direktori lain memuat ribuan tautan" | Selesai | Dihapus di `03-homepage-copy.md` v2.0 |
| Seksi "Kenapa isinya lebih sedikit" | Selesai | Diganti "Cara kami memberi label" di v2.0 |
| Klaim "tidak ada tool yang masuk karena membayar" | Selesai | Diganti pengungkapan afiliasi dan placement di v2.0 |
| QA 15 menit untuk semua tool | Tidak mungkin | Berlaku hanya untuk tier "Diuji" |
| "Katalog kecil" sebagai identitas | Batal | Ganti "luas dengan verifikasi bertingkat" |
| Asumsi pasar global berbahasa Inggris | Ditunda | Rekomendasi: Indonesia 12 bulan pertama |

---

## Keputusan yang masih terbuka

1. **Pasar pertama:** Indonesia (rekomendasi) atau langsung Inggris? `.web.id` adalah aset di Indonesia, beban di pasar global.
2. **Rasio tier:** berapa persen katalog boleh "Terdaftar" tanpa diuji? Rekomendasi: maksimal 80%, minimal 20% "Diuji".
3. **Submission berbayar:** jaminan tayang atau hanya percepatan review? Rekomendasi: hanya percepatan.
4. **Sumber data trafik:** data sendiri selamanya, atau berlangganan pihak ketiga setelah pendapatan stabil?
5. **Kapasitas uji:** siapa yang menguji tool setiap minggu, dan berapa target per minggu? Ini penentu kredibilitas label "Diuji".

---

## Prinsip yang bertahan dari awal

1. **Jangan pernah menulis "gratis" untuk sesuatu yang menuntut kartu kredit.**
2. **Setiap entri harus punya fungsi yang jelas.** Entri Diuji wajib punya alasan kurasi; entri Terdaftar wajib punya kategori dan fungsi yang bisa dipahami, tanpa klaim gratis.
3. **Tanggal verifikasi harus nyata**, bukan tanggal yang diperbarui otomatis.
4. **Uang tidak boleh mengubah peringkat**, hanya visibilitas yang diberi label.
5. **Lebih baik menunda satu tool daripada menayangkan klaim yang salah.**
