# 📜 Project Charter: BorrowMate

| | |
|---|---|
| **Nama project** | BorrowMate |
| **Product Owner** | Abdul Wahab |
| **Scrum Master (Sprint 1)** | Arif Firmansyah |
| **Mata kuliah / Dosen** | `[isi]` / `[isi]` |
| **Tanggal dokumen** | 21 November 2026 |
| **Versi** | 1.0 (Sprint 1) |

---

## 1. Latar Belakang

Mahasiswa sering memiliki barang yang jarang digunakan, sementara mahasiswa lain membutuhkannya untuk keperluan sementara. Proses peminjaman informal rawan jadwal bertabrakan, status barang tidak jelas, keterlambatan, dan tidak adanya riwayat. BorrowMate dibangun untuk mengelola proses ini secara terstruktur.

## 2. Tujuan Project

1. Menyediakan aplikasi web yang mendukung siklus peminjaman penuh: publikasi barang, pengajuan, persetujuan, serah-terima, pengembalian, dan riwayat.
2. Mencegah peminjaman ganda pada rentang tanggal yang bertabrakan.
3. Menerapkan Agile Scrum secara disiplin, dengan kemajuan terdokumentasi di GitHub setiap sprint.

## 3. Kriteria Keberhasilan

| No | Kriteria | Cara mengukur |
|---|---|---|
| 1 | Satu transaksi dapat berjalan dari pengajuan sampai selesai | Didemokan pada Sprint Review akhir |
| 2 | Dua pengajuan bentrok untuk barang yang sama tidak dapat sama-sama disetujui | Lulus uji otomatis dan uji manual |
| 3 | Perpindahan status transaksi mengikuti aturan yang ditetapkan | Lulus uji perpindahan status |
| 4 | Setiap anggota berkontribusi lewat commit di setiap sprint | Riwayat commit GitHub |
| 5 | Repositori diperbarui setiap sprint beserta dokumentasinya | Tag/rilis sprint dan folder `docs/` |

## 4. Ruang Lingkup

**Termasuk:** registrasi dan login; katalog barang (foto, kategori, kondisi, lokasi umum); pencarian dan filter; pengajuan peminjaman; pengecekan bentrok jadwal; persetujuan/penolakan; manajemen status; konfirmasi serah-terima dan pengembalian; keterlambatan dan riwayat; ulasan; dashboard admin.

**Tidak termasuk (versi awal):** pembayaran dan deposit online, chat real-time, layanan pengiriman/logistik, notifikasi email, penanganan laporan konflik tingkat lanjut.

## 5. Hasil Kerja per Sprint (rencana awal)

| Sprint | Sasaran | Hasil utama |
|---|---|---|
| 1 | Fondasi dokumentasi dan repositori | Repositori kelompok, Profil Kelompok, Profil Project, Project Charter, commit seluruh anggota |
| 2 | Akun dan barang dapat dikelola | Login/registrasi, CRUD barang, kategori, foto, katalog, pencarian |
| 3 | Siklus peminjaman berjalan | Formulir pengajuan, validasi tanggal, cek bentrok, persetujuan/penolakan, status transaksi, konfirmasi serah-terima dan pengembalian |
| 4 | Siap diuji dan dipresentasikan | Riwayat, keterlambatan, ulasan, dashboard admin, pengujian, perbaikan bug, dokumentasi, demo |

Rincian setiap sprint ditetapkan pada Sprint Planning dan menyesuaikan arahan dosen.

## 6. Pemangku Kepentingan

| Pihak | Peran terhadap project |
|---|---|
| Dosen pengampu | Pemberi tugas, penilai, dan peninjau Sprint Review |
| Tim pengembang | Merancang, membangun, menguji, dan mendokumentasikan |
| Calon pengguna (mahasiswa) | Pengguna sasaran: pemilik barang dan peminjam |
| Administrator sistem | Memoderasi akun, barang, dan kategori |

## 7. Struktur Tim

| Nama | NIM | GitHub | Peran |
|---|---|---|---|
| Abdul Wahab | 240504113 | Xzen-tech | Product Owner |
| Arif Firmansyah | 240504123 | kecearif786-lgtm | Scrum Master (Sprint 1) |
| Riska Fauziati | 250504114 | Riskafzti | Developer, Scrum Master (Sprint 2) |
| M. Fariel Faisa | 250504121 | farielfaisa09-sudo | Developer, Scrum Master (Sprint 3) |
| Afdeli Lia Sari Br Sembiring | 250504129 | Afdeliliasaribrsembiring | Developer, Scrum Master (Sprint 4) |

## 8. Asumsi dan Batasan

**Asumsi**
- Pengguna berkomitmen pada kesepakatan antar mahasiswa tanpa pembayaran.
- Seluruh alat yang digunakan gratis, sehingga tidak ada anggaran berbayar.
- Tim bekerja dengan sprint mingguan dan setiap anggota memiliki akses ke GitHub.

**Batasan**
- Waktu pengerjaan terbatas (sekitar satu bulan).
- Sebagian anggota masih pemula dalam pemrograman, sehingga perlu waktu belajar dan *pair programming*.
- Versi awal hanya mengizinkan satu transaksi aktif pada satu barang untuk rentang tanggal tertentu.

## 9. Risiko dan Mitigasi

| No | Risiko | Dampak | Mitigasi |
|---|---|---|---|
| 1 | Anggota pemula belum menguasai Git/Django | Pekerjaan lambat, banyak kesalahan | Panduan Git pemula, *pair programming*, tugas awal berskala kecil |
| 2 | Logika bentrok jadwal salah | Peminjaman ganda, inti sistem gagal | Pengecekan ulang saat persetujuan, uji otomatis, uji manual saat Sprint Review |
| 3 | Lingkup membengkak | Fitur inti tidak selesai | Batasan lingkup jelas, prioritas oleh Product Owner |
| 4 | Waktu tidak cukup | Sprint tidak tercapai | Prioritas *must/should*, fitur kecil, pemantauan mingguan |
| 5 | Konflik penggabungan kode (*merge conflict*) | Pekerjaan hilang atau terhambat | Cabang fitur kecil, Pull Request sering, `git pull` sebelum bekerja |
| 6 | Kontribusi tidak merata | Penilaian individu terganggu | Pembagian tugas jelas, Scrum Master memantau, riwayat commit ditinjau tiap sprint |

## 10. Aturan Kerja dan Peralatan

- **Metode:** Agile Scrum dengan sprint mingguan, pertemuan rutin, Sprint Review, dan Retrospektif.
- **Peralatan:** Git, GitHub (Issues, Projects, Pull Request), Python, Django, editor kode pilihan masing-masing.
- **Alur cabang:** `main` (stabil) ← `dev` ← `feature/*`; tanpa *push* langsung ke `main` untuk kode aplikasi.
- **Pesan commit:** awalan `feat:`, `fix:`, `docs:`, `chore:`.
- **Dokumentasi:** hasil tiap sprint disimpan di `docs/sprint-N/`.

## 11. Persetujuan

| Nama | Peran | Tanggal | Tanda tangan |
|---|---|---|---|
| Abdul Wahab | Product Owner | | |
| Arif Firmansyah | Scrum Master | | |
| Riska Fauziati | Developer | | |
| M. Fariel Faisa | Developer | | |
| Afdeli Lia Sari Br Sembiring | Developer | | |
