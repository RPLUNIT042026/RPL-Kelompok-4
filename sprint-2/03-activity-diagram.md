# 🔄 Activity Diagram (Wajib)

Menggambarkan alur proses bisnis dari awal hingga selesai secara berurutan.

## 1. Alur Unggah Barang

Pemilik mengisi detail barang, harga/jaminan (jika ada), dan syarat pinjam. Setelah informasi barang diisi, barang tersedia untuk dipinjam.

### Activity Diagram Alur Unggah Barang (dengan simbol)

```mermaid
flowchart TD
    A((Mulai)) --> B[Pemilik mengisi detail barang]
    B --> C[Menentukan harga atau jaminan jika ada]
    C --> D[Mengisi syarat pinjam]
    D --> E{Informasi sudah lengkap?}
    E -- Tidak --> B
    E -- Ya --> F[Barang tersedia untuk dipinjam]
    F --> G(((Selesai)))

    subgraph Pemilik
        B
        C
        D
        E
    end
    subgraph Sistem
        F
    end
```

## 2. Alur Transaksi Peminjaman

Peminjam mencari barang, mengajukan tanggal pinjam, pemilik menyetujui permintaan, kemudian dilakukan serah terima barang dan pengembalian barang hingga transaksi selesai.

### Activity Diagram Alur Transaksi Peminjaman (dengan simbol)

```mermaid
flowchart TD
    A((Mulai)) --> B[Peminjam mencari barang]
    B --> C[Mengajukan tanggal pinjam]
    C --> D{Permintaan disetujui?}
    D -- Tidak --> E[Permintaan ditolak]
    E --> H(((Selesai)))
    D -- Ya --> F[Serah terima barang]
    F --> G[Peminjam mengembalikan barang]
    G --> I[Transaksi selesai]
    I --> J(((Selesai)))

    subgraph Peminjam
        B
        C
        G
    end
    subgraph Pemilik
        D
        E
        F
    end
    subgraph Sistem
        I
    end
```

## 3. Keterangan Simbol Activity Diagram

| No. | Nama Simbol | Bentuk / sintaks Mermaid | Keterangan |
|---|---|---|---|
| 1 | Start State | `A((Mulai))` | Menandai awal aktivitas/proses. |
| 2 | End State | `A(((Selesai)))` | Menandai akhir aktivitas/proses. |
| 3 | Swimlane | `subgraph Nama ... end` | Mengelompokkan aktivitas berdasarkan pelaku atau fungsi. |
| 4 | Transition | `A --> B` | Menunjukkan hubungan/alur antar simbol. |
| 5 | Decision | `A{Kondisi?}` | Menunjukkan percabangan berdasarkan kondisi, misalnya Ya/Tidak. |
| 6 | State | `A([Nama keadaan])` | Menunjukkan keadaan atau kondisi sistem. |
| 7 | Fork / Join | Bar tebal pada notasi UML Activity Diagram | Menunjukkan pemecahan atau penggabungan aktivitas paralel. |

**Catatan:** Mermaid memakai bentuk flowchart yang mendekati simbol pada referensi. Swimlane ditampilkan sebagai kelompok `subgraph`. Simbol Fork/Join UML berupa bar tebal tidak direpresentasikan persis oleh flowchart Mermaid.
