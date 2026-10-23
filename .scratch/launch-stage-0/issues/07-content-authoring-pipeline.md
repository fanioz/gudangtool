# Ticket: How do 50 tool files get written?

Type: grilling
Status: resolved
Blocked by: 03, 12

## Question

What is the mechanical pipeline from "tool observed" to "JSON merged into `src/content/tools/`", and who is allowed to run which step?

## Detail

`05-seed-tools.md` §7 requires the `function` line be rewritten, not copied from the vendor. `AGENTS.md` §7 splits ownership: content agent edits `src/content/tools/**` one file per PR for corrections, mass import only via script.

Open:

1. What is the input format for a batch? The seed data is in `docs/06-tools.json` with `tier: kandidat` — is there a converter, or does every tool get hand-written?
2. Is there a single import script with a fixed CSV/JSON column list (launch-plan P1 #11 says "template impor CSV/JSON" but none exists)?
3. Who runs the mechanical half of verification — agent writes a candidate JSON file, opens PR, then the owner's real-task note is added before merge?
4. Does a PR get one tool or a batch? `AGENTS.md` §5 wants one task per branch; 50 tool PRs is 50 PRs.
5. Where does `internal_note` (never rendered) record the verification session — date, tester, observed limits?

The pipeline decision determines how fast the 50-page batch can be produced without breaking the "one file per tool" rule.

---

## Resolution — owner decisions

**2026-10-23.** Tiga keputusan.

**Q1 — Impor awal satu PR batch; setelah itu satu file per PR (a).** Konversi satu
kali dari `docs/06-tools-seed.json` (20 entri) + 30 entri tulis tangan menghasilkan
seluruh batch 50 file, masuk sebagai **satu PR**. Review batch bukan per file:
menjalankan `npm run check`, `validate:content`, dan `build` adalah reviewer yang
sesungguhnya untuk data sebanyak ini; manusia memeriksa sampel. Setelah batch
merge, disiplin `AGENTS.md` §7 berlaku penuh: koreksi = satu file per PR. Jalur
"impor massal lewat skrip" dipakai persis sekali.

**Q2 — Tulis dulu sebagai `terdaftar`, naik kelas belakangan (a).** Pipeline per tool:

1. Agent menulis seluruh field mekanis (amati vendor, isi `limits`/`platform`/`url`,
   catat `internal_note.sources`, `observed_at`, `observed_by`) — entri merge
   sebagai `terdaftar` begitu `validate:content` lulus.
2. Pemilik mengerjakan uji tugas nyata 10 menit kapan pun sempat.
3. Setiap uji selesai = **satu PR kecil** menaikkan tier: isi `verified_at`,
   `why`, `fit`, `not_fit`, koreksi `limits` bila berbeda, tambah
   `internal_note.evidence`.

Tidak ada cabang hidup berhari-hari menunggu jadwal uji. Kenaikan tier per tool
menjadi audit trail yang terlihat di git — persis yang diminta protokol hibrida.
Halaman `terdaftar` tampil jujur selama beberapa hari tanpa ruginya (D23).

**Q3 — Pemilik menulis `why`/`fit`/`not_fit`; agent hanya memformat (a).** Pemilik
boleh menulis kasar dan singkat ("Figma: bagus buat prototipe, batas 3 file
nyebelin, jangan buat raster") — agent memindahkan ke JSON tanpa menghaluskan
kalimat. `not_fit` adalah bagian paling berharga halaman ini; kalimat itu harus
keluar dari kepala orang yang benar-benar memakai tool. Agent **dilarang**
mendrafit atau menebak `why`/`fit`/`not_fit` dari bacaan halaman.

### Peta jawaban atas pertanyaan lama di badan tiket

1. Input batch: konverter satu kali dari `06-tools-seed.json` (D19); 30 sisanya tulis tangan.
2. Template CSV/JSON impor: tidak diperlukan — satu file per tool, skrip konversi hanya untuk seed.
3. Mekanis agent → PR → uji pemilik: ya, dengan urutan Q2 (merge dulu sebagai `terdaftar`).
4. PR batch: ya untuk impor awal; koreksi menyusul satu file per PR (Q1).
5. `internal_note`: objek `{sources, evidence, note}` (D19) — sesi verifikasi tercatat lewat `sources` (URL klaim), `evidence` (path bukti), dan `note` (kebebasan).

### Unblocks

- Seluruh jalur konten Stage 0 terbuka: 50 file bisa diproduksi tanpa keputusan tersisa.
- Sisa peta: 09/10/11 (simpul DNS–deploy–homepage yang saling memblokir).
