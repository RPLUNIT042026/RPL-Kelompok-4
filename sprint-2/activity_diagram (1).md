# 🔄 Activity Diagram (Wajib)

Menggambarkan alur proses bisnis dari awal hingga selesai secara
berurutan.

## Alur Unggah Barang

Pemilik mengisi detail barang, harga/jaminan (jika ada), dan syarat
pinjam.

## Alur Transaksi Peminjaman

Peminjam mencari barang → mengajukan tanggal pinjam → pemilik menyetujui
→ serah terima barang → pengembalian barang → selesai.

## Activity Diagram

``` mermaid
flowchart TD
    A((Mulai)) --> B[Pemilik mengisi detail barang]
    B --> C[Menentukan harga/jaminan jika ada]
    C --> D[Mengisi syarat pinjam]
    D --> E[Barang tersedia untuk dipinjam]

    E --> F[Peminjam mencari barang]
    F --> G[Mengajukan tanggal pinjam]
    G --> H[Pemilik menyetujui permintaan]
    H --> I[Serah terima barang]
    I --> J[Peminjam mengembalikan barang]
    J --> K((Selesai))
```
