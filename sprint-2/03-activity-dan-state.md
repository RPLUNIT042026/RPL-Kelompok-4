<div align="center">

# 🔀 Activity & State Diagram

![Sprint](https://img.shields.io/badge/SPRINT-2-0F766E?style=flat-square)
![Dokumen](https://img.shields.io/badge/DOKUMEN-03-F59E0B?style=flat-square)

[⬅️ Kembali ke README](../README.md)

</div>

---

## 1. Activity Diagram: Proses Peminjaman

Diagram memperlihatkan alur dari pengajuan sampai barang kembali, dengan tiga jalur tanggung jawab (*swimlane*): Peminjam, Sistem, dan Pemilik.

```mermaid
flowchart TD
    START((" ")) --> P1

    subgraph PEMINJAM["👤 Peminjam"]
        P1["Login dan cari barang"]
        P2["Pilih barang lalu ajukan pinjam"]
        P3["Isi tanggal pinjam dan kembali"]
        P4["Terima barang dan pakai"]
        P5["Kembalikan barang"]
    end

    subgraph SISTEM["⚙️ Sistem"]
        S1{"Tanggal valid dan tidak bentrok?"}
        S2["Simpan pengajuan: Diajukan"]
        S3["Ubah status: Disetujui"]
        S4["Ubah status: Ditolak"]
        S5["Ubah status: Dipinjam"]
        S6["Ubah status: Dikembalikan, barang Tersedia"]
    end

    subgraph PEMILIK["📦 Pemilik"]
        M1{"Setujui permintaan?"}
        M2["Serahkan barang"]
        M3["Periksa dan konfirmasi pengembalian"]
    end

    P1 --> P2 --> P3 --> S1
    S1 -- Tidak --> P3
    S1 -- Ya --> S2 --> M1
    M1 -- Ya --> S3 --> M2 --> S5 --> P4 --> P5 --> M3 --> S6 --> FIN((" "))
    M1 -- Tidak --> S4 --> FIN
```

## 2. Activity Diagram: Tambah Barang

```mermaid
flowchart TD
    A((" ")) --> B["Login sebagai pemilik"]
    B --> C["Pilih menu Tambah Barang"]
    C --> D["Isi nama, kategori, deskripsi, kondisi"]
    D --> E["Unggah foto barang"]
    E --> F{"Data lengkap dan foto valid?"}
    F -- Tidak --> G["Tampilkan pesan kesalahan"] --> D
    F -- Ya --> H["Simpan barang dengan status Tersedia"]
    H --> I["Tampilkan di daftar barang"]
    I --> J((" "))
```

## 3. State Diagram: Status Peminjaman

```mermaid
stateDiagram-v2
    [*] --> Diajukan : peminjam mengajukan
    Diajukan --> Disetujui : pemilik menyetujui
    Diajukan --> Ditolak : pemilik menolak
    Diajukan --> Dibatalkan : peminjam membatalkan
    Diajukan --> Kedaluwarsa : tidak diproses 2 hari
    Disetujui --> Dipinjam : serah terima barang
    Disetujui --> Dibatalkan : dibatalkan sebelum serah terima
    Dipinjam --> Dikembalikan : pemilik konfirmasi pengembalian
    Dipinjam --> Terlambat : melewati tanggal kembali
    Terlambat --> Dikembalikan : pemilik konfirmasi pengembalian
    Ditolak --> [*]
    Dibatalkan --> [*]
    Kedaluwarsa --> [*]
    Dikembalikan --> [*]
```

| Status | Arti |
|---|---|
| Diajukan | Menunggu tanggapan pemilik |
| Disetujui | Pemilik setuju, menunggu serah terima |
| Dipinjam | Barang sedang berada di peminjam |
| Dikembalikan | Barang sudah kembali ke pemilik |
| Terlambat | Barang belum kembali setelah tanggal kembali |
| Ditolak / Dibatalkan / Kedaluwarsa | Peminjaman tidak jadi berlangsung |

## 4. State Diagram: Status Barang

```mermaid
stateDiagram-v2
    [*] --> Tersedia : barang ditambahkan
    Tersedia --> Dipinjam : peminjaman berjalan
    Dipinjam --> Tersedia : barang dikembalikan
    Tersedia --> Nonaktif : pemilik atau admin menonaktifkan
    Nonaktif --> Tersedia : diaktifkan kembali
    Nonaktif --> [*] : dihapus
```
