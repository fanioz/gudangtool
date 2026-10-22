# Gudangtool — Status & Rencana Peluncuran v1.0

**Tanggal:** 22 Oktober 2026
**Dasar:** seluruh dokumen `docs/01`–`12`
**Tujuan:** memisahkan yang sudah selesai dari yang menghalangi peluncuran.

---

## 1. Status per area

| Area | Status | Catatan |
|---|---|---|
| Strategi & positioning | **Selesai** | Pivot terdokumentasi, pilar dan anti-pilar jelas |
| Brand & identitas | **70%** | Logo A dikunci; SVG, favicon, dan OG image belum dibuat |
| Copy | **85%** | Homepage, kategori, detail, microcopy selesai; halaman legal belum |
| Model data | **90%** | Skema JSON jelas; template impor massal belum |
| Isi katalog | **10%** | 20 kandidat, **0 terverifikasi**; target 300 |
| Implementasi | **0%** | Belum ada repo Astro, template, CI, atau Caddy |
| SEO teknis | **80%** | Aturan dan tipe halaman selesai; sitemap/GSC belum jalan |
| Infrastruktur | **0%** | VPS belum dikonfigurasi, DNS belum di Cloudflare |
| Monetisasi | **10%** | Rencana ada; AdSense, harga placement, pembayaran belum |
| Operasional | **20%** | Lembar uji ada; alur submission dan ranking belum |
| Legal | **0%** | Privasi, ketentuan, kontak, pengungkapan afiliasi belum |

**Kesimpulan:** pekerjaan berpikir sudah 80–90%; pekerjaan membangun dan membuktikan masih mendekati nol.

---

## 2. Blocker peluncuran (P0)

1. **Verifikasi 20 tool.** Belum ada satu pun entri berlabel Diuji. Tanpa ini, janji utama produk tidak punya bukti. Waktu: 75 menit untuk lima tool paling rawan, lalu sisanya.
2. **Kedalaman satu kategori.** Aturan indeks: kategori butuh 12 tool. Dengan 20 tool di 8 kategori, **tidak ada satu pun kategori yang layak indeks**. Pilih dua kategori peluncuran (rekomendasi: **Desain** dan **AI**), tambah masing-masing menjadi 15+.
3. **Repo dan implementasi.** Belum ada proyek Astro, skema Zod, template halaman, Pagefind, CI, atau Caddy. Ini pekerjaan agent berikutnya.
4. **`AGENTS.md` untuk agent pembangun.** Tanpa aturan tertulis, tiap agent akan mengarang struktur folder dan aturan indeks sendiri.
5. **Aset merek produksi.** Logo A dalam SVG (penuh, 16px, satu warna), favicon set, OG image 1200×630, avatar sosial.
6. **Halaman legal.** Kebijakan privasi, ketentuan pemakaian, kontak, pengungkapan afiliasi dan placement. Ini syarat AdSense sekaligus kewajiban UU PDP.
7. **DNS, email, dan SSL.** Cloudflare nameserver, alamat pengirim (Brevo), SPF/DKIM/DMARC, dan Caddy HTTPS.
8. **Deploy dan backup.** Caddy, systemd, rsync release, backup SQLite—tanpa SQLite: cukup artefak release + git—dan uji restore.

---

## 3. Sebelum scale (P1)

9. **Taksonomi lorong.** Maksimal 40 subkategori, dengan pemetaan tool. Tanpa ini, agent akan membuat kategori baru setiap kali ada satu tool.
10. **Runbook konten.** Cara menambah 50 tool/minggu: sumber, penulisan satu kalimat, penentuan tier, QA, dan penolakan.
11. **Template impor CSV/JSON.** Kolom tetap agar agent tidak mengarang field.
12. **Pipeline ranking.** Parsing access log Caddy, filter bot, snapshot bulanan, ambang 100 pembukaan.
13. **Alur submission.** GitHub Issue Form + label + template email fallback.
14. **Search Console dan Bing.** Verifikasi, sitemap tersegmentasi, robots.txt, pemantauan indeks.
15. **Performance budget.** Batas JS, CSS, font, gambar; Lighthouse CI di setiap PR.
16. **Checklist aksesibilitas.** Fokus keyboard, kontras badge, heading hierarchy, alt text.
17. **Peta internal linking.** Tool → kategori → koleksi → alternatif, tanpa halaman yatim.
18. **Halaman 404 dan empty state** dalam bentuk visual, bukan hanya copy.
19. **Kebijakan logo tool.** Simpan lokal atau hotlink, lisensi, ukuran, fallback.

---

## 4. Sebelum monetisasi (P2)

20. **Kesiapan AdSense.** Halaman kebijakan, `ads.txt`, peta penempatan, larangan iklan di halaman Terdaftar yang tipis.
21. **Paket placement.** Harga, durasi, posisi, dan aturan bahwa placement tidak mengubah ranking.
22. **Submission prioritas.** Harga, SLA 48 jam, tanpa jaminan tayang.
23. **Kebijakan afiliasi.** Kapan dipakai, bagaimana dilabeli, dan siapa yang menyetujui.

---

## 5. Nanti (P3)

24. Akun pengguna dan sinkronisasi simpanan (pemicu database).
25. Newsletter.
26. Mode gelap.
27. Versi bahasa Inggris.
28. Halaman perbandingan dan "alternatif" dalam jumlah besar.

---

## 6. Keputusan yang harus diambil sekarang

| # | Keputusan | Rekomendasi |
|---|---|---|
| 1 | Kategori peluncuran | **Desain + AI**, masing-masing 15+ tool |
| 2 | Ambang indeks kategori | Tetap 12; jangan diturunkan hanya agar terlihat penuh |
| 3 | Repo publik atau privat | Privat selama konten belum siap; publik jika mengejar menit Actions tak terbatas |
| 4 | Form submission | GitHub Issue Form; email sebagai fallback |
| 5 | Sumber ranking | Access log Caddy; Cloudflare sebagai pembanding |
| 6 | Alamat email pengirim | `halo@gudangtool.web.id` atau subdomain `mail.` |

---

## 7. Critical path 14 hari

| Hari | Pekerjaan |
|---|---|
| 1–2 | Kunci keputusan di atas; finalkan taksonomi dua kategori peluncuran |
| 3–5 | Verifikasi 20 tool; tambah 10–15 tool Desain dan AI |
| 6–10 | Bangun repo Astro, skema, template, Pagefind, CI, Caddy, deploy |
| 11–12 | Halaman legal, DNS, email, analytics, Search Console |
| 13 | QA: label, kontras, performa, 404, sitemap, backup |
| 14 | Soft launch; pantau indeks dan error |

---

## 8. Definisi selesai untuk peluncuran

- [ ] Minimal 50 tool tayang, **30 di antaranya Diuji**
- [ ] Dua kategori punya 12+ tool dan bisa diindeks
- [ ] Tidak ada halaman Terdaftar yang memuat kata "gratis", tabel batas, atau skor
- [ ] Semua halaman punya label verifikasi yang terlihat
- [ ] Halaman privasi, ketentuan, kontak, dan pengungkapan aktif
- [ ] Sitemap terkirim ke Search Console dan Bing
- [ ] Lighthouse mobile: performa ≥85, SEO 100, aksesibilitas ≥95
- [ ] Backup dan restore diuji minimal sekali
- [ ] Uptime monitoring aktif
- [ ] Tidak ada tautan mati di 50 halaman pertama

---

## 9. Risiko terbesar

Bukan teknologi, dan bukan SEO. Risiko terbesar adalah **meluncurkan katalog besar yang belum punya satu pun bukti "Diuji"**. Kalau itu terjadi, Gudangtool menjadi direktori biasa dengan label yang tidak berarti — dan tidak ada alasan bagi pengunjung untuk kembali.

Karena itu urutan kerjanya harus: **bukti dulu, skala kemudian.**
