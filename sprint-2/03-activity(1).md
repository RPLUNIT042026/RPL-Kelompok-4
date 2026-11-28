# 🔄 Activity Diagram (Wajib)

Menggambarkan alur proses bisnis dari awal hingga selesai secara berurutan.

## 1. Alur Unggah Barang

Pemilik mengisi detail barang, harga/jaminan (jika ada), dan syarat pinjam. Setelah informasi barang diisi, barang tersedia untuk dipinjam.

### Activity Diagram Alur Unggah Barang

```mermaid
flowchart TD
    A((Mulai)) --> B[Pemilik mengisi detail barang]
    B --> C[Menentukan harga atau jaminan jika ada]
    C --> D[Mengisi syarat pinjam]
    D --> E[Barang tersedia untuk dipinjam]
    E --> F((Selesai))
```

## 2. Alur Transaksi Peminjaman

Peminjam mencari barang, mengajukan tanggal pinjam, pemilik menyetujui permintaan, kemudian dilakukan serah terima barang dan pengembalian barang hingga transaksi selesai.

### Activity Diagram Alur Transaksi Peminjaman

```mermaid
flowchart TD
    A((Mulai)) --> B[Peminjam mencari barang]
    B --> C[Mengajukan tanggal pinjam]
    C --> D[Pemilik menyetujui permintaan]
    D --> E[Serah terima barang]
    E --> F[Peminjam mengembalikan barang]
    F --> G((Selesai))
```
