# Gudangtool — Lembar Uji 5 Tool Paling Rawan v1.1

> **Status:** protokol ini hanya berlaku untuk tool yang akan diberi label **Diuji**. Entri **Terdaftar** tidak melewati protokol ini dan tidak boleh menampilkan klaim gratis.

**Tanggal:** 21 Oktober 2026
**Untuk:** penanggung jawab kurasi
**Total waktu:** 75 menit (15 menit per tool)
**Keluaran:** status final + batas satu baris + `verified: true` di `tools.json`

---

## 0. Aturan main

1. **Pakai akun uji khusus**, bukan akun pribadi yang berisi data klien. Kalau tool meminta akses Google Drive, berikan akun kosong.
2. **Uji dengan file milik sendiri.** Jangan mengunggah materi berhak cipta atau data orang lain.
3. **Timebox 15 menit per tool.** Kalau lewat 15 menit dan status belum jelas, hentikan dan tandai `TUNDA` — jangan menebak.
4. **Ambil bukti.** Satu tangkapan layar untuk hasil ekspor, satu untuk halaman batas/kuota. Nama file: `{tool}-{YYYY-MM-DD}-{01}.png`.
5. **Jangan memperbaiki tool.** Kalau ada bug, catat, jangan laporkan ke vendor atas nama Gudangtool tanpa persetujuan.

---

## 1. Empat status final

| Status | Definisi | Syarat |
|---|---|---|
| **Gratis** | Tugas inti bisa diselesaikan tanpa membayar | Tanpa kartu kredit, tanpa watermark pada hasil, batas jelas |
| **Freemium** | Ada versi gratis dengan batas | Batas bisa dijelaskan dalam satu baris |
| **Butuh akun** | Gratis, tapi wajib mendaftar sebelum bisa dipakai | Akun gratis, tanpa kartu |
| **Tolak** | Tidak layak masuk gudang | Butuh kartu kredit, trial berbatas waktu, atau batas tidak dapat dijelaskan |

**Aturan penentu:** kalau ragu antara Gratis dan Freemium, pilih **Freemium**. Label yang lebih konservatif selalu lebih aman daripada klaim yang berlebihan.

---

## 2. Prosedur umum (berlaku untuk semua tool)

| Menit | Langkah | Yang dicatat |
|---|---|---|
| 0–2 | Buka URL di jendela privat | Apakah langsung meminta login? |
| 2–7 | Kerjakan satu tugas nyata sampai selesai | Berhasil? Di langkah mana macet? |
| 7–10 | Ekspor atau simpan hasil | Format apa? Ada watermark? |
| 10–12 | Cari halaman harga/kuota | Angka batasnya berapa? |
| 12–14 | Coba langkah yang biasanya dikunci | Muncul ajakan berlangganan? |
| 14–15 | Tulis status + batas satu baris | Simpan bukti |

---

## 3. CapCut — risiko: watermark dan batas ekspor

**Yang paling mungkin berubah:** kebijakan watermark, resolusi ekspor, dan fitur yang dikunci untuk pengguna gratis.

**Uji wajib:**
1. Buka `capcut.com` di jendela privat — bisa mulai proyek tanpa login?
2. Buat video 15 detik dari dua klip, tambahkan subtitle otomatis.
3. Ekspor 1080p. **Periksa pojok kanan bawah** hasil ekspor: ada watermark?
4. Ulangi ekspor 4K. Apakah diminta upgrade?
5. Cek template yang ditandai "Pro" — berapa proporsinya di halaman depan?
6. Cari halaman harga: apa yang didapat versi gratis?

**Tanda bahaya:**
- Ekspor 1080p kena watermark → status **Freemium**, tulis "watermark pada ekspor 1080p".
- Muncul trial dengan kartu kredit → **Tolak**.
- Subtitle otomatis hanya untuk pengguna Pro → tulis jelas di batas.

**Keputusan:** kalau watermark hanya di fitur tertentu (bukan ekspor dasar), tetap Freemium dan sebutkan fitur mana yang bersih.

---

## 4. Adobe Podcast Enhance — risiko: batas durasi dan kuota

**Yang paling mungkin berubah:** panjang audio maksimum, kuota harian, dan syarat akun.

**Uji wajib:**
1. Buka `podcast.adobe.com/enhance` tanpa login — langsung diarahkan ke halaman masuk?
2. Masuk dengan Adobe ID gratis (bukan akun Creative Cloud berbayar).
3. Unggah rekaman 5 menit dengan suara sendiri. Catat waktu proses.
4. Unggah rekaman 30 menit. Berhasil, atau ada pesan batas?
5. Unduh hasilnya. Format apa? Ada tanda air audio?
6. Cari keterangan kuota: berapa file per hari/bulan?

**Tanda bahaya:**
- Batas durasi di bawah 10 menit → sebutkan angkanya, jangan tulis "ada batas".
- Kuota harian sangat kecil (mis. 1 file/hari) → tetap Freemium, tapi turunkan prioritas di daftar.
- Diminta langganan Creative Cloud untuk mengunduh → **Tolak**.

**Keputusan:** catat batas dalam format "{X} menit per file, {Y} file per {periode}".

---

## 5. Canva — risiko: elemen berbayar yang tidak terlihat

**Yang paling mungkin berubah:** proporsi template gratis, syarat ekspor transparan, dan batas folder.

**Uji wajib:**
1. Buka `canva.com` tanpa login — bisa membuat desain?
2. Masuk dengan akun gratis. Pilih template "Instagram Post" dari daftar teratas.
3. Hitung berapa elemen bertanda mahkota dalam template itu (perkiraan cukup).
4. Ekspor PNG. Lalu coba ekspor PNG transparan (hapus latar).
5. Cek apakah ekspor transparan meminta Pro.
6. Cari halaman harga: apa yang dikunci di versi gratis?

**Tanda bahaya:**
- Ekspor standar kena watermark → **Tolak** (Canva tidak seharusnya begitu; kalau terjadi, ada perubahan besar).
- Template gratis hanya sedikit di kategori populer → tulis "mayoritas template populer berbayar".
- Trial 30 hari yang menuntut kartu → jangan tulis "gratis", tulis "Pro trial".

**Keputusan:** Canva tetap **Freemium**; yang menentukan adalah seberapa jujur batasnya ditulis, bukan apakah ada fitur berbayar.

---

## 6. Raycast — risiko: fitur inti yang bergeser ke Pro

**Yang paling mungkin berubah:** pemisahan fitur gratis vs Pro, dan ketersediaan platform.

**Uji wajib:**
1. Pasang di macOS. Bisa dipakai tanpa akun?
2. Uji tiga fitur inti: peluncur aplikasi, riwayat clipboard, dan manajemen jendela.
3. Uji satu fitur AI. Berapa banyak permintaan gratis sebelum diminta upgrade?
4. Cari halaman harga: fitur mana yang khusus Pro?
5. Cek apakah tersedia untuk Windows (kalau belum, tulis "khusus macOS").
6. Cek apakah data clipboard disimpan lokal atau cloud.

**Tanda bahaya:**
- Fitur inti (clipboard, jendela) masuk Pro → status berubah jadi **Freemium** dengan catatan tegas.
- Wajib akun hanya untuk membuka aplikasi → tulis "Butuh akun".
- Data clipboard dikirim ke cloud tanpa pilihan lokal → catat sebagai risiko privasi.

**Keputusan:** kalau tiga fitur inti tetap gratis, status **Gratis** dengan catatan "fitur AI berbayar".

---

## 7. Google AI Studio — risiko: kuota harian per model

**Yang paling mungkin berubah:** kuota gratis per model, ketersediaan model baru, dan syarat billing.

**Uji wajib:**
1. Buka `aistudio.google.com` dengan akun Google kosong.
2. Jalankan prompt teks panjang (sekitar 1.000 kata) pada model default.
3. Unggah satu gambar dan satu PDF; minta ringkasannya.
4. Ulangi sampai muncul pesan kuota. Catat berapa permintaan yang berhasil.
5. Cari halaman harga/kuota: apakah ada model yang meminta billing aktif?
6. Cek catatan privasi: apakah data uji dipakai untuk pelatihan?

**Tanda bahaya:**
- Model default langsung meminta billing → gunakan model lain yang gratis, atau **Tolak**.
- Kuota sangat kecil (mis. 5 permintaan/hari) → tulis angkanya; masih layak, tapi jangan diposisikan sebagai pengganti harian.
- Data pelatihan tidak bisa dimatikan → catat sebagai peringatan privasi di kartu.

**Keputusan:** tulis batas dalam format "{X} permintaan per {periode} untuk model {nama}".

---

## 8. Cara mengisi hasil

Setelah selesai, isi `test-sheet.csv` dengan aturan:

- **`status_final`** — salah satu dari empat status di bagian 1.
- **`batas_satu_baris`** — kalimat yang akan dibaca pengunjung. Contoh: "Watermark di semua ekspor 1080p; 4K khusus Pro."
- **`verified`** — `true` hanya kalau bukti sudah diambil dan batas sudah ditulis.
- **`checked_at`** — tanggal uji, format `YYYY-MM-DD`.
- **`catatan`** — hal yang tidak masuk kategori lain, misalnya "UI berbahasa Inggris".

Kalau satu tool gagal di salah satu uji wajib, **keluarkan dari peluncuran pertama**. Gudang dengan 15 tool yang benar lebih kuat daripada 20 tool yang dua di antaranya perlu dikoreksi di hari kedua.

---

## 9. Setelah pengujian

- [ ] Perbarui `tools.json`: `status`, `limits`, `why`, `verified`, `checked_at`
- [ ] Tambahkan baris riwayat di halaman detail: "Diperiksa. {perubahan}."
- [ ] Simpan bukti tangkapan layar di folder `qa/evidence/{slug}/`
- [ ] Kalau status berubah dari perkiraan awal, perbarui juga ringkasan di `seed-tools.md`
- [ ] Laporkan ke pemilik proyek: berapa yang lolos, berapa yang ditolak, dan alasannya
