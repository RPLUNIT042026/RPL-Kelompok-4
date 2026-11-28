# Sprint 2 -- Sequence Diagram

## Sistem Peminjaman Barang Antar Mahasiswa (Peer-to-Peer Lending)

### 1. Tujuan

Sequence Diagram ini menjelaskan urutan interaksi antara peminjam,
aplikasi/web, backend, database, dan pemilik barang ketika mahasiswa
mengajukan peminjaman barang.

### 2. Objek yang terlibat

1.  **Peminjam:** mahasiswa yang ingin meminjam barang.
2.  **Aplikasi/Web:** antarmuka yang digunakan mahasiswa.
3.  **Backend/Sistem:** memproses pengajuan peminjaman.
4.  **Database:** menyimpan dan memeriksa data barang serta transaksi.
5.  **Pemilik:** mahasiswa yang menawarkan barang untuk dipinjam.

### 3. Sequence Diagram

``` mermaid
sequenceDiagram
    actor Peminjam
    participant UI as Aplikasi/Web
    participant Sistem as Backend
    participant DB as Database
    actor Pemilik

    Peminjam->>UI: Memilih barang
    Peminjam->>UI: Mengisi tanggal peminjaman
    Peminjam->>UI: Menekan tombol Ajukan Pinjam
    UI->>Sistem: Mengirim data pengajuan
    Sistem->>DB: Memeriksa ketersediaan barang
    DB-->>Sistem: Mengirim status barang

    alt Barang tersedia
        Sistem->>DB: Menyimpan transaksi berstatus Menunggu Persetujuan
        DB-->>Sistem: Konfirmasi data tersimpan
        Sistem-->>UI: Pengajuan berhasil dikirim
        UI-->>Peminjam: Menampilkan status Menunggu Persetujuan
        Sistem-->>Pemilik: Mengirim pemberitahuan pengajuan
        Pemilik->>UI: Membuka detail pengajuan
        Pemilik->>UI: Memilih Setujui atau Tolak
        UI->>Sistem: Mengirim keputusan pemilik
        Sistem->>DB: Memperbarui status transaksi
        DB-->>Sistem: Konfirmasi perubahan status
        Sistem-->>UI: Mengirim hasil keputusan
        UI-->>Peminjam: Menampilkan status pengajuan
    else Barang tidak tersedia
        Sistem-->>UI: Mengirim informasi barang tidak tersedia
        UI-->>Peminjam: Menampilkan pesan barang tidak tersedia
    end
```

### 4. Penjelasan alur

1.  Peminjam membuka aplikasi, memilih barang, lalu mengisi tanggal
    peminjaman.
2.  Peminjam menekan tombol **Ajukan Pinjam**.
3.  Aplikasi mengirim data pengajuan ke backend.
4.  Backend memeriksa ketersediaan barang melalui database.
5.  Jika barang tersedia, sistem menyimpan transaksi dengan status
    **Menunggu Persetujuan**.
6.  Sistem mengirim pemberitahuan kepada pemilik barang.
7.  Pemilik membuka detail pengajuan, kemudian memilih untuk menyetujui
    atau menolak.
8.  Sistem menyimpan keputusan pemilik dan memperbarui status transaksi
    di database.
9.  Peminjam menerima informasi mengenai hasil pengajuan.
10. Jika barang tidak tersedia, aplikasi menampilkan pemberitahuan
    kepada peminjam.

### 5. Kesimpulan

Sequence Diagram ini menunjukkan urutan komunikasi dalam proses
pengajuan peminjaman barang antar mahasiswa. Dengan diagram ini,
interaksi antara pengguna, aplikasi, backend, dan database dapat
dipahami secara lebih terstruktur.
