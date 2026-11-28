<div align="center">

# 🔍 Analisis Kebutuhan

![Sprint](https://img.shields.io/badge/SPRINT-2-0F766E?style=flat-square)
![Dokumen](https://img.shields.io/badge/DOKUMEN-01-F59E0B?style=flat-square)

[⬅️ Kembali ke README](../README.md)

</div>

---

Dokumen ini menjadi dasar seluruh diagram UML pada Sprint 2: aktor, kebutuhan fungsional, kebutuhan non-fungsional, dan aturan bisnis BorrowMate.

## 🎭 Aktor

| Aktor | Deskripsi |
|---|---|
| **Peminjam** | Mahasiswa yang mencari dan mengajukan peminjaman barang |
| **Pemilik** | Mahasiswa yang menawarkan barangnya untuk dipinjam |
| **Admin** | Pengelola sistem yang memoderasi pengguna dan barang |

> [!NOTE]
> Satu akun mahasiswa dapat berperan sebagai Pemilik sekaligus Peminjam. Pembedaan aktor dilakukan menurut aktivitas yang sedang dilakukan.

## ⚙️ Kebutuhan Fungsional

Prioritas memakai skala MoSCoW: **M** = Must, **S** = Should, **C** = Could.

| Kode | Kebutuhan | Aktor | Prioritas |
|---|---|---|:-:|
| FR-01 | Sistem memungkinkan mahasiswa mendaftar dengan NIM, nama, email, dan kata sandi | Semua | M |
| FR-02 | Sistem memungkinkan pengguna login dan logout | Semua | M |
| FR-03 | Sistem memungkinkan pengguna mengubah data profil | Semua | S |
| FR-04 | Sistem menampilkan daftar barang yang tersedia | Peminjam | M |
| FR-05 | Sistem memungkinkan pencarian barang berdasarkan kata kunci | Peminjam | M |
| FR-06 | Sistem memungkinkan penyaringan barang berdasarkan kategori | Peminjam | S |
| FR-07 | Sistem menampilkan detail barang (foto, kondisi, pemilik, ketersediaan) | Peminjam | M |
| FR-08 | Sistem memungkinkan pengajuan peminjaman dengan tanggal pinjam dan kembali | Peminjam | M |
| FR-09 | Sistem memungkinkan pembatalan pengajuan yang belum diproses | Peminjam | S |
| FR-10 | Sistem menampilkan riwayat dan status peminjaman | Peminjam, Pemilik | M |
| FR-11 | Sistem memungkinkan pemilik menambah, mengubah, dan menghapus barang | Pemilik | M |
| FR-12 | Sistem memungkinkan pemilik menyetujui atau menolak permintaan | Pemilik | M |
| FR-13 | Sistem memungkinkan pemilik mengonfirmasi serah terima barang | Pemilik | S |
| FR-14 | Sistem memungkinkan pemilik mengonfirmasi pengembalian barang | Pemilik | M |
| FR-15 | Sistem memungkinkan peminjam memberi ulasan setelah barang dikembalikan | Peminjam | C |
| FR-16 | Sistem memungkinkan admin mengelola akun pengguna | Admin | S |
| FR-17 | Sistem memungkinkan admin memoderasi barang yang tidak layak | Admin | S |

## 🛡️ Kebutuhan Non-Fungsional

| Kode | Kategori | Kebutuhan |
|---|---|---|
| NFR-01 | Keamanan | Kata sandi disimpan dalam bentuk hash |
| NFR-02 | Keamanan | Hanya pengguna yang login dapat mengajukan peminjaman atau mengelola barang |
| NFR-03 | Kegunaan | Antarmuka mudah dipahami mahasiswa tanpa pelatihan |
| NFR-04 | Kompatibilitas | Dapat diakses melalui peramban modern di komputer dan ponsel (responsif) |
| NFR-05 | Kinerja | Halaman utama dimuat maksimal 3 detik pada koneksi normal |
| NFR-06 | Keandalan | Data peminjaman tidak hilang saat terjadi gangguan |
| NFR-07 | Integritas | Barang yang sedang dipinjam tidak dapat diajukan pada periode yang bentrok |

## 📏 Aturan Bisnis *(usulan, dapat disesuaikan)*

| Kode | Aturan |
|---|---|
| BR-01 | Hanya pengguna terdaftar dengan NIM yang valid yang dapat meminjam atau meminjamkan |
| BR-02 | Pemilik tidak dapat meminjam barangnya sendiri |
| BR-03 | Tanggal kembali harus setelah tanggal pinjam |
| BR-04 | Durasi peminjaman maksimal 7 hari |
| BR-05 | Satu barang hanya dapat dipinjam satu orang pada periode yang sama |
| BR-06 | Pengajuan yang tidak diproses pemilik dalam 2 hari otomatis kedaluwarsa |
| BR-07 | Ulasan hanya dapat diberikan setelah barang berstatus dikembalikan |

## 📖 User Story

| ID | Sebagai | Saya ingin | Agar | Kebutuhan |
|---|---|---|---|---|
| US-01 | Peminjam | mencari tripod berdasarkan kata kunci | cepat menemukan barang yang saya butuhkan | FR-05 |
| US-02 | Peminjam | mengajukan peminjaman pada tanggal tertentu | bisa memakai barang sesuai jadwal kegiatan | FR-08 |
| US-03 | Peminjam | melihat status pengajuan saya | tahu apakah sudah disetujui | FR-10 |
| US-04 | Pemilik | mengunggah barang dengan foto dan kondisi | peminjam mengetahui keadaan barang | FR-11 |
| US-05 | Pemilik | menyetujui atau menolak permintaan | bisa mengatur barang sesuai kesiapan saya | FR-12 |
| US-06 | Pemilik | mengonfirmasi barang sudah kembali | riwayat peminjaman tercatat dengan benar | FR-14 |
| US-07 | Admin | menonaktifkan akun atau barang bermasalah | platform tetap aman dan tertib | FR-16, FR-17 |

## 🔗 Keterlacakan Kebutuhan ke Use Case

| Use case | Kebutuhan terkait |
|---|---|
| UC-01 Registrasi | FR-01 |
| UC-02 Login | FR-02 |
| UC-03 Kelola Profil | FR-03 |
| UC-04 Cari Barang | FR-04, FR-05 |
| UC-05 Lihat Detail Barang | FR-07 |
| UC-06 Ajukan Peminjaman | FR-08 |
| UC-07 Batalkan Pengajuan | FR-09 |
| UC-08 Lihat Riwayat | FR-10 |
| UC-09 Beri Ulasan | FR-15 |
| UC-10 Kelola Barang | FR-11 |
| UC-11 Setujui atau Tolak | FR-12 |
| UC-12 Konfirmasi Serah Terima | FR-13 |
| UC-13 Konfirmasi Pengembalian | FR-14 |
| UC-14 Kelola Pengguna | FR-16 |
| UC-15 Moderasi Barang | FR-17 |
| UC-16 Filter Kategori | FR-06 |
