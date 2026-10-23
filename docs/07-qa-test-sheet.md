# Gudangtool — Protokol Verifikasi Hibrida v2.0

> **Status:** menggantikan v1.1. Protokol ini hanya berlaku untuk tool berlabel **Diuji**. Entri **Terdaftar** tidak melewati protokol ini dan tidak boleh menampilkan klaim gratis.

**Tanggal:** 22 Oktober 2026
**Menggantikan:** v1.1 (protokol tunggal 15 menit)
**Dasar:** D18 #5 · hasil riset `.scratch/launch-stage-0/issues/02-answer.md`
**Keluaran:** `diuji` hanya jika **kedua** bagian selesai — pengamatan mekanis dan uji tugas nyata oleh pemilik.

---

## 1. Dua bagian, satu label

Label **Diuji** berarti dua hal sekaligus: *kami sudah membaca halaman batasnya* dan *seseorang benar-benar memakainya*. Keduanya perlu tanggal sendiri, karena keduanya bisa kedaluwarsa terpisah.

| Bagian | Siapa | Yang dihasilkan | Field |
|---|---|---|---|
| **Mekanis** | Agent | `limits`, `platform`, `url`, URL vendor untuk setiap klaim, warna status | `observed_at`, `observed_by` |
| **Tugas nyata** | Pemilik proyek | `why`, `fit`, `not_fit`, konfirmasi atau koreksi `limits` | `verified_at` |

**Aturan mutlak:** `tier` berubah menjadi `diuji` hanya setelah **`observed_at` dan `verified_at` sama-sama terisi**. Satu bagian saja tetap `terdaftar`.

**Konsekuensi yang disengaja:** `verified_at` selalu tanggal manusia memakai tool itu. Tool yang sudah diamati agent tetapi belum dicoba manusia tetap `terdaftar` — dan itu boleh dikatakan terang-terangan di halaman.

---

## 2. Bagian mekanis (agent)

Untuk setiap tool, dalam satu sesi, tanpa mengubah apa pun di akun pemilik:

1. Buka URL resmi di jendela privat. Catat apakah langsung meminta login.
2. Cari halaman harga, kuota, atau bantuan. **Catat URL-nya** — setiap klaim harus punya sumber.
3. Baca halaman lisensi atau repositori untuk tool open source; "tidak ada batas" karena lisensi adalah klaim yang paling mudah dipertahankan.
4. Isi lima field `limits`: `account`, `quota`, `watermark`, `export`, `storage`.
5. Kalau satu field tidak bisa ditentukan tanpa akun atau tanpa uji, tulis **"Belum diperiksa"** — bukan tebakan, bukan "tidak ada".
6. Tulis `observed_at` (tanggal) dan `observed_by` (`agent` atau nama orang).
7. Simpan URL sumber tiap klaim di `internal_note.sources` sebagai array `{field, url}`. `field` memakai path bertitik, mis. `limits.quota`.

**Yang dilarang di bagian ini:** menulis `fit`, `not_fit`, atau `why`. Itu penilaian manusia, bukan hasil membaca halaman.

**Kalau klaim vendor bertentangan dengan yang Anda lihat:** yang Anda lihat menang untuk `limits`. Klaim vendor tetap dicatat di `internal_note.sources` beserta URL-nya sebagai jejak audit.

---

## 3. Bagian tugas nyata (pemilik)

Timebox **10 menit** per tool. Akun uji khusus, bukan akun pribadi. Hanya file milik sendiri.

1. Kerjakan satu tugas nyata sampai selesai — bukan melihat halaman depan.
2. Ekspor atau simpan hasilnya.
3. Cari langkah yang biasanya dikunci: ekspor resolusi tinggi, format tertentu, fitur bertanda Pro.
4. **Konfirmasi atau koreksi** `limits` dari bagian mekanis. Kalau berbeda, koreksi field-nya — versi Anda yang berlaku.
5. Tulis `why` (satu kalimat, alasan tool ini masuk), `fit`, dan `not_fit`.
6. Ambil satu tangkapan layar hasil ekspor dan satu untuk halaman batas/kuota.
7. Isi `verified_at` dengan tanggal uji.

**Aturan penentu:** kalau ragu antara Gratis dan Freemium, pilih **Freemium**.

---

## 4. Tiga jalur keluar

Setiap tool berakhir di salah satu dari tiga keadaan. Tidak ada keadaan keempat.

| Keadaan | Kapan | Yang tertulis di katalog |
|---|---|---|
| **Diuji** | Kedua bagian selesai | Tabel batas lengkap, `why`/`fit`/`not_fit`, dua tanggal |
| **Terdaftar** | Hanya bagian mekanis selesai, **atau** batas tidak bisa ditentukan dalam timebox | Nama, fungsi, kategori, platform, URL. Tidak ada klaim. |
| **Tidak masuk** | Ditolak kriteria seleksi (kartu kredit, trial berbatas waktu, ekspor berwatermark tersembunyi) | Tidak ada entri |

**Tool yang gagal verifikasi tidak ditahan di antrean.** Ia turun ke `terdaftar` — itu memang slot untuk "kami tahu ia ada, kami tidak mengklaim apa pun". `kandidat` tetap hanya status antrean impor dan tidak pernah tayang.

---

## 5. Bukti: di mana disimpan

**Screenshots di luar repo.** Git menyimpan teks, bukan PNG; 3.000 tool × 2 tangkapan layar akan membengkakkan repo selamanya dan memperlambat setiap clone.

- Lokasi: `~/gudangtool-evidence/{slug}/{YYYY-MM-DD}-{01}.png`, di luar repo.
- Di setiap file JSON tool, path relatifnya dicatat di `internal_note.evidence` sebagai array string: `"{slug}/{YYYY-MM-DD}-{01}.png"`.
- `internal_note` **tidak pernah dirender** — ia hanya jejak audit untuk peninjau PR.
- Kalau pemilik ingin bukti ikut di repo, pindahkan folder ke `qa/evidence/` dan tambahkan ke `.gitignore` per folder; keputusan tetap di pemilik.

**Yang wajib ada di `internal_note` untuk setiap entri `diuji`:** `sources` (URL tiap klaim) dan `evidence` (path bukti). Tanpa keduanya, build gagal.

---

## 6. Perubahan skema yang dibutuhkan

Protokol ini menambah dua field ke skema `14-repo-spec.md` §4:

| Field | Tipe | Wajib | Aturan |
|---|---|---|---|
| `observed_at` | date/null | ya untuk `diuji`, null untuk `terdaftar` | Boleh lebih awal dari `verified_at` |
| `observed_by` | `"agent"` atau string nama | ya untuk `diuji`, null untuk `terdaftar` | Siapa yang menjalankan bagian mekanis |

Aturan build yang ditambahkan: `tier = diuji` gagal build jika `observed_at` atau `verified_at` kosong.

---

## 7. Protokol uji spesifik per tool — 5 paling rawan

Pemilihan berdasarkan **risiko × konsekuensi**, bukan popularitas. Detail kandidat ada di `.scratch/launch-stage-0/issues/02-answer.md` §4.

## 8. Figma — risiko: batas file tidak lagi tertulis di halaman harga

**Yang paling mungkin berubah:** batas file kolaboratif, riwayat versi, dan apa yang masuk Pro.

Halaman harga hanya menyebut "Unlimited drafts"; angka "3 file kolaboratif" hanya ada di blog Figma tahun 2024.

**Uji wajib:**
1. Buat file desain baru di akun gratis.
2. Undang akun kedua sebagai editor. Berapa file yang bisa dibagi sebelum diblokir?
3. Cek riwayat versi: 30 hari atau lebih?
4. Coba prototipe dengan kondisi (conditional logic) — terkunci?
5. Cari halaman harga: fitur mana yang khusus Pro?

**Keputusan:** tulis batas sesuai yang **Anda alami**, bukan yang blog katakan. Kalau angka berbeda dari 3, itu yang tayang.

---

## 9. Tldraw — risiko: vendor tidak menulis batasnya di mana pun

**Yang paling mungkin berubah:** syarat berbagi tautan dan kolaborasi tamu.

halaman publik hanya menyebut "free whiteboard"; tombol berbagi membaca "Sign in to share", tetapi tidak jelas apakah itu dinding keras atau sekadar ajakan.

**Uji wajib:**
1. Buka tldraw.com tanpa akun — bisa menggambar sepenuhnya?
2. Simpan sebagai file lokal — berhasil?
3. Klik berbagi tanpa akun — apa yang terjadi?
4. Coba buat tautan tamu yang bisa diedit dari akun kedua.
5. Cari halaman harga atau bantuan — ada batas tertulis?

**Keputusan:** kalau tautan tamu bisa diedit tanpa akun, `requires_account` = false dan batasnya ditulis "berbagi tautan butuh akun" hanya jika terbukti. Kalau kolaborasi tanpa akun bekerja, itu keunggulan, bukan batas.

---

## 10. remove.bg — risiko: situs mandiri ditutup 1 Desember 2026

Banner di halaman harga menyatakan pemindahan ke Canva dan penutupan situs mandiri per 1 Des 2026, 09.00 CET.

**Uji wajib:**
1. Unggah foto potret, tanpa akun. Hasilnya pratinjau resolusi berapa?
2. Unduh pratinjau — bisa dipakai (mis. untuk thumbnail)?
3. Coba unduh resolusi penuh — berapa kredit, dan apakah akun wajib?
4. Buka halaman `/id` — apakah banner tanggal yang sama muncul?
5. Catat tanggal banner persis.

**Keputusan:** halaman detail wajib memuat catatan "status ini kedaluwarsa per 1 Desember 2026". Tanpa catatan itu, tool tidak boleh tayang sebagai Diuji.

---

## 11. Penpot — risiko: tumpang tindih dengan Figma

**Uji wajib:**
1. Buat proyek di plan gratis cloud.
2. Undang anggota tim sampai batas 8 tercapai.
3. Ekspor sebagai CSS/SVG — apakah perlu plan berbayar?
4. Cek riwayat versi: 7 hari?
5. Coba fitur yang di Figma berbayar (prototipe lanjutan, pustaka tim) — gratis di sini?

**Keputusan:** kalimat pembeda dengan Figma wajib ada di halaman: Penpot untuk ekspor standar web dan pemasangan sendiri; Figma untuk prototipe interaktif dan ekosistem. Kalau perbedaan itu tidak bisa ditulis satu baris, salah satu keluar dari katalog.

---

## 12. SVG Viewer — risiko: tanpa halaman harga, tanpa pembaruan sejak 2019

**Uji wajib:**
1. Buka svgviewer.dev tanpa akun — bisa mengunggah SVG?
2. Optimalkan satu SVG yang berantakan — berapa node yang hilang?
3. Unduh hasilnya — apa ada dinding atau kredit AI?
4. Cermati fitur "Edit with AI" dan "Create" di sidebar — dikunci?
5. Cari halaman syarat atau privasi — masih tanggal 2019?

**Keputusan:** kalau ada dinding ekspor atau kredit, ganti ke **SVGOMG** dan jangan simpan keduanya. Kalau tidak ada dinding tetapi situs tidak dipelihara, tayang sebagai Diuji dengan catatan "tidak ada pembaruan terlihat sejak 2019".

---

## 13. Mengisi hasil

- **`price_status`** — `gratis`, `freemium`, atau `butuh-akun`.
- **`limits`** — lima field; nilai yang tidak ada batasnya ditulis "Tidak ada".
- **`why`** — satu kalimat yang dibaca pengunjung.
- **`verified_at`** — tanggal uji tugas nyata.
- **`observed_at`** — tanggal pengamatan mekanis.
- **`internal_note`** — objek `{sources, evidence, note}`. Sumber tiap klaim + path bukti. Tidak pernah dirender.

---

## 14. Setelah pengujian

- [ ] `tier` menjadi `diuji` hanya jika `observed_at` dan `verified_at` keduanya terisi
- [ ] Riwayat di halaman detail: "Diperiksa {verified_at}. {perubahan}."
- [ ] Kalau status berubah dari perkiraan awal, perbarui ringkasan di `05-seed-tools.md`
- [ ] Laporkan ke pemilik: berapa lolos, berapa turun ke `terdaftar`, dan alasannya
