# Ticket: What does the homepage show at 50 tools?

Type: prototype
Status: claimed
Blocked by: 01, 02, 04

## Question

Does the homepage's "paling sering dibuka" and ranking strip degrade gracefully when there is no click data and fewer than 20 ranked tools — or should it be hidden?

## Detail

`03-homepage-copy.md` v2.0 specifies sections: search first, categories, "baru masuk", "paling sering dibuka", collections, ranking, three-label explainer, submit path.

At launch:

- No click data exists (pageview only, `12-tech-stack.md` §8).
- Ranking needs ≥20 ranked tools with ≥100 opens each. That is weeks away.
- Collections need ≥10 tools each under a deterministic rule.

So three of the six homepage sections have no data. The homepage is the only page every visitor sees, and the first 5 seconds are the brand's whole promise (`01-brand-brief.md` §10).

The question is a prototype, not a debate: build the homepage with the empty sections and see whether it reads as honest or broken. Candidates: hide the section, show a "belum cukup data" state, or show the section with a single row.

Needs the visual identity tokens from `docs/02` and the preview files in `docs/preview/`.

## Comments

### 2026-10-23 — prototype siap, menunggu reaksi pemilik

Aset: [`docs/preview/homepage-launch-prototype.html`](../../../docs/preview/homepage-launch-prototype.html) — buka langsung di browser (file mandiri), ganti varian lewat tombol panah di bawah, tombol ← →, atau `?variant=a|b|c`.

Tiga varian yang berbeda **struktur** pada satu sumbu tiket (apa yang terjadi pada tiga seksi tanpa data):

- **A — Rangka penuh**: paling setia ke `03-homepage-copy.md` v2.0 — ranking tampil sebagai satu baris "belum cukup data" + ambangnya, koleksi disembunyikan (02 §14.6). Slot iklan dipertahankan untuk diuji pada skala peluncuran.
- **B — Rak tanpa antrean**: seksi tanpa data dihilangkan sama sekali; rak "Baru masuk" digenapkan jadi 9 kartu nyata; tautan nav/footer Ranking & Koleksi ikut dihilangkan agar tidak ada broken link.
- **C — Papan status**: seksi data diganti modul "Gudang dalam angka" — 50/15/8/35 dan ambang transparan. Data yang belum ada jadi bukti metode.

Semua varian memakai angka terkunci (tiket 02/04): 50 tool, 15 diuji, 8 kategori; kartu "Baru masuk" memakai nama seed/pilot nyata dengan badge yang benar; chip "Sering dicari" diganti enam tugas yang tool-nya benar-benar ada di kategori percontohan (catatan di copy v2 §3). Dua hal ditemukan saat membangun: (1) chip default di copy v2 (transkrip audio, gabung PDF) tidak semua punya tool nyata di 50 awal — chip harus diambil dari data, bukan daftar statis; (2) seksi Artikel disembunyikan di semua varian karena nol artikel saat peluncuran — prinsip yang sama dengan kategori <3.

Menunggu keputusan pemilik: varian mana (atau gabungan mana) yang jadi homepage peluncuran. Setelah dipilih: jawaban dicatat di tiket ini, aturan gating seksi masuk ke logika nav (D20 gate 8), dan copy v2 diperbarui bila varian bukan A.

### 2026-10-23 (sesi kedua) — banding varian, supaya keputusan murah diambil

Pemilik belum memilih varian. Yang bisa disiapkan tanpa keputusan: konsekuensi tiap pilihan, supaya yang ditanyakan tinggal "mana".

| Kriteria | A — Rangka penuh | B — Rak tanpa antrean | C — Papan status |
|---|---|---|---|
| Setuju copy v2 §4–§11 | Ya, persis | Sebagian — §6/§7/§8 jadi opsional | Tidak — modul baru belum ada di copy v2 |
| Prinsip 02 "rapi, bukan ramai" | 5 seksi + 1 kotak kosong | 4 seksi, terpendek | 5 seksi + papan angka |
| Aturan nada 03 §14 "akui batasan sebelum pembaca menemukannya" | Satu baris mengakui batas | Batas tidak disebut — seksi hilang diam-diam | Batas disebut eksplisit (angka + ambang) |
| Risiko broken link | Tautan Ranking perlu halaman /ranking | Tautan Ranking/Koleksi ikut dihapus | Tautan Ranking perlu halaman /ranking |
| Saat data arrive | Ranking terisi di tempat | Homepage berubah bentuk — seksi baru muncul di atas label | Papan mendapat baris hidup; ranking tetap seksi sendiri |
| Perubahan yang harus ditulis | Tidak ada | 03 §6–§8 ditandai "muncul setelah ambang" | Modul "Gudang dalam angka" + copy baru di 03 §13 |
| Risiko kebuntuan | Kotak kosong bisa terbaca "halaman rusak" | Terlalu tipis untuk 50 tool | Papan angka bisa terasa seperti dasbor, bukan direktori |

**Rekomendasi: A.** Alasannya: A satu-satunya varian yang tidak perlu mengubah keputusan yang sudah dikunci (copy v2 §6 sudah menyediakan kalimat "belum cukup data"; 02 §14.6 sudah menyuruh koleksi disembunyikan), jadi biayanya hanya aturan gating di build. B dan C sama-sama lebih jujur soal ambang, tetapi keduanya menuntut penulisan ulang copy dan, untuk B, homepage yang berubah bentuk beberapa minggu setelah peluncuran.

**Satu hal yang harus diputuskan bersama pilihannya** (kalau tidak, A dan C jadi tautan mati): apakah halaman `/ranking` ada di Stage 0. Ini adalah item fog "Collection/ranking eligibility at 50 tools" — begitu tiket ini selesai, item itu jadi tiket tersendiri dengan pertanyaan: "Apakah `/ranking` dan `/koleksi` terbit di Stage 0, dan apa yang ditampilkan saat belum ada data?"
