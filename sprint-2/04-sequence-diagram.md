<div align="center">

# ⏱️ Sequence Diagram

![Sprint](https://img.shields.io/badge/SPRINT-2-0F766E?style=flat-square)
![Dokumen](https://img.shields.io/badge/DOKUMEN-04-F59E0B?style=flat-square)

[⬅️ Kembali ke README](../README.md)

</div>

---

Lapisan yang digunakan: **Antarmuka** (halaman web), **Controller** (logika alur), dan **Database**.

## 1. Login

```mermaid
sequenceDiagram
    actor U as Pengguna
    participant UI as Antarmuka
    participant C as AuthController
    participant DB as Database

    U->>UI: Isi NIM/email dan kata sandi
    UI->>C: login(identitas, sandi)
    C->>DB: cariPengguna(identitas)
    DB-->>C: data pengguna
    alt pengguna ditemukan dan sandi cocok
        C->>C: buatSesi()
        C-->>UI: login berhasil
        UI-->>U: tampilkan halaman utama
    else data tidak cocok
        C-->>UI: login gagal
        UI-->>U: tampilkan pesan kesalahan
    end
```

## 2. Cari Barang

```mermaid
sequenceDiagram
    actor PJ as Peminjam
    participant UI as Antarmuka
    participant BC as BarangController
    participant DB as Database

    PJ->>UI: Ketik kata kunci dan pilih kategori
    UI->>BC: cariBarang(kataKunci, kategori)
    BC->>DB: query barang berstatus Tersedia
    DB-->>BC: daftar barang
    BC-->>UI: hasil pencarian
    UI-->>PJ: tampilkan daftar barang
```

## 3. Ajukan Peminjaman

```mermaid
sequenceDiagram
    actor PJ as Peminjam
    participant UI as Antarmuka
    participant PC as PeminjamanController
    participant DB as Database
    actor PM as Pemilik

    PJ->>UI: Pilih barang dan isi tanggal
    UI->>PC: ajukanPeminjaman(idBarang, tglPinjam, tglKembali)
    PC->>PC: validasiTanggal()
    PC->>DB: cekBentrokJadwal(idBarang, periode)
    DB-->>PC: hasil pengecekan
    alt tanggal valid dan tidak bentrok
        PC->>DB: simpan peminjaman (status Diajukan)
        DB-->>PC: berhasil
        PC-->>UI: pengajuan terkirim
        UI-->>PJ: tampilkan konfirmasi
        PC-->>PM: notifikasi permintaan baru
    else tidak valid atau bentrok
        PC-->>UI: pesan kesalahan
        UI-->>PJ: minta perbaiki tanggal
    end
```

## 4. Setujui atau Tolak Permintaan

```mermaid
sequenceDiagram
    actor PM as Pemilik
    participant UI as Antarmuka
    participant PC as PeminjamanController
    participant DB as Database
    actor PJ as Peminjam

    PM->>UI: Buka permintaan masuk
    UI->>PC: ambilPermintaan(idPemilik)
    PC->>DB: query peminjaman Diajukan
    DB-->>PC: daftar permintaan
    PC-->>UI: tampilkan daftar
    PM->>UI: Pilih Setujui atau Tolak
    UI->>PC: tanggapi(idPeminjaman, keputusan)
    PC->>DB: perbarui status peminjaman
    DB-->>PC: berhasil
    PC-->>PJ: notifikasi hasil keputusan
    PC-->>UI: status diperbarui
    UI-->>PM: tampilkan konfirmasi
```

## 5. Konfirmasi Pengembalian

```mermaid
sequenceDiagram
    actor PM as Pemilik
    participant UI as Antarmuka
    participant PC as PeminjamanController
    participant DB as Database

    PM->>UI: Pilih Konfirmasi Pengembalian
    UI->>PC: konfirmasiKembali(idPeminjaman, catatan)
    PC->>DB: set status Dikembalikan dan tglDikembalikan
    PC->>DB: set status barang Tersedia
    DB-->>PC: berhasil
    PC-->>UI: pengembalian tercatat
    UI-->>PM: tampilkan konfirmasi
```
