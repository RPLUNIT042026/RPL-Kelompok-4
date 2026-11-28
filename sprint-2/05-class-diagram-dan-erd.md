<div align="center">

# 🧱 Class Diagram & ERD

![Sprint](https://img.shields.io/badge/SPRINT-2-0F766E?style=flat-square)
![Dokumen](https://img.shields.io/badge/DOKUMEN-05-F59E0B?style=flat-square)

[⬅️ Kembali ke README](../README.md)

</div>

---

## 1. Class Diagram

```mermaid
classDiagram
    class Pengguna {
        +int idPengguna
        +String nim
        +String nama
        +String email
        +String passwordHash
        +String noHp
        +String role
        +boolean aktif
        +registrasi() boolean
        +login() boolean
        +logout() void
        +ubahProfil() void
    }

    class Kategori {
        +int idKategori
        +String namaKategori
    }

    class Barang {
        +int idBarang
        +int idPemilik
        +int idKategori
        +String namaBarang
        +String deskripsi
        +String kondisi
        +String fotoUrl
        +String status
        +tambah() void
        +ubah() void
        +hapus() void
        +cekKetersediaan(tglPinjam, tglKembali) boolean
    }

    class Peminjaman {
        +int idPeminjaman
        +int idBarang
        +int idPeminjam
        +Date tglPengajuan
        +Date tglPinjam
        +Date tglKembali
        +Date tglDikembalikan
        +String status
        +String catatan
        +ajukan() void
        +batalkan() void
        +setujui() void
        +tolak() void
        +konfirmasiSerahTerima() void
        +konfirmasiPengembalian() void
    }

    class Ulasan {
        +int idUlasan
        +int idPeminjaman
        +int rating
        +String komentar
        +Date tanggal
        +kirim() void
    }

    class Notifikasi {
        +int idNotifikasi
        +int idPengguna
        +String pesan
        +boolean dibaca
        +Date waktu
        +kirim() void
    }

    Pengguna "1" --> "0..*" Barang : memiliki
    Kategori "1" --> "0..*" Barang : mengelompokkan
    Barang "1" --> "0..*" Peminjaman : dipinjam dalam
    Pengguna "1" --> "0..*" Peminjaman : mengajukan
    Peminjaman "1" --> "0..1" Ulasan : memiliki
    Pengguna "1" --> "0..*" Notifikasi : menerima
```

### Kamus Kelas

| Kelas | Tanggung jawab |
|---|---|
| Pengguna | Menyimpan data akun mahasiswa dan admin. Atribut `role` bernilai `mahasiswa` atau `admin` |
| Kategori | Pengelompokan barang (dokumentasi, kalkulator, alat praktikum, buku, perlengkapan kegiatan) |
| Barang | Data barang yang ditawarkan pemilik beserta statusnya |
| Peminjaman | Transaksi peminjaman dan seluruh siklus statusnya |
| Ulasan | Penilaian peminjam terhadap peminjaman yang selesai |
| Notifikasi | Pemberitahuan perubahan status kepada pengguna |

### Nilai Status

| Atribut | Nilai |
|---|---|
| `Barang.status` | Tersedia, Dipinjam, Nonaktif |
| `Peminjaman.status` | Diajukan, Disetujui, Ditolak, Dibatalkan, Kedaluwarsa, Dipinjam, Terlambat, Dikembalikan |

## 2. Entity Relationship Diagram

ERD merupakan turunan class diagram untuk perancangan basis data.

```mermaid
erDiagram
    PENGGUNA ||--o{ BARANG : memiliki
    KATEGORI ||--o{ BARANG : mengelompokkan
    BARANG ||--o{ PEMINJAMAN : dipinjam
    PENGGUNA ||--o{ PEMINJAMAN : mengajukan
    PEMINJAMAN ||--o| ULASAN : memiliki
    PENGGUNA ||--o{ NOTIFIKASI : menerima

    PENGGUNA {
        int id_pengguna PK
        string nim UK
        string nama
        string email UK
        string password_hash
        string no_hp
        string role
        boolean aktif
    }
    KATEGORI {
        int id_kategori PK
        string nama_kategori
    }
    BARANG {
        int id_barang PK
        int id_pemilik FK
        int id_kategori FK
        string nama_barang
        text deskripsi
        string kondisi
        string foto_url
        string status
    }
    PEMINJAMAN {
        int id_peminjaman PK
        int id_barang FK
        int id_peminjam FK
        date tgl_pengajuan
        date tgl_pinjam
        date tgl_kembali
        date tgl_dikembalikan
        string status
        text catatan
    }
    ULASAN {
        int id_ulasan PK
        int id_peminjaman FK
        int rating
        text komentar
        date tanggal
    }
    NOTIFIKASI {
        int id_notifikasi PK
        int id_pengguna FK
        string pesan
        boolean dibaca
        datetime waktu
    }
```

## 3. Konsistensi Antar Diagram

| Diagram | Menjawab pertanyaan | Mengacu ke |
|---|---|---|
| Use Case | Apa yang bisa dilakukan tiap aktor? | Analisis kebutuhan |
| Activity | Bagaimana alur prosesnya? | Use case |
| State | Bagaimana status berubah? | Activity dan class |
| Sequence | Bagaimana objek saling berinteraksi? | Use case dan class |
| Class | Apa struktur data dan perilaku sistem? | Seluruh diagram di atas |
| ERD | Bagaimana data disimpan? | Class diagram |
