<div align="center">

<img src="assets/banner.svg" alt="BorrowMate: pinjam apa saja, antar sesama mahasiswa" width="100%">

<br>

![Sprint](https://img.shields.io/badge/Sprint-1-9DB8AA?style=flat-square&labelColor=2E4A42)
![Metode](https://img.shields.io/badge/Metode-Agile%20Scrum-8FB0C2?style=flat-square&labelColor=2E4A42)
![Platform](https://img.shields.io/badge/Platform-Web-B5CBC0?style=flat-square&labelColor=2E4A42)
![Stack](https://img.shields.io/badge/Stack-Python%20%2B%20Django-7F9A8F?style=flat-square&labelColor=2E4A42)

</div>

<img src="assets/divider.svg" alt="" width="100%" height="18">

## Kenapa BorrowMate?

Banyak mahasiswa punya barang yang jarang dipakai: tripod, kalkulator ilmiah, alat praktikum, buku referensi. Mahasiswa lain hanya butuh barang itu sebentar. Selama ini urusannya lewat chat dan ingatan, sehingga jadwal mudah bentrok, barang lupa dikembalikan, dan tidak ada catatan.

BorrowMate merapikan seluruh prosesnya: **barang dipublikasikan, diajukan, disetujui, diserahkan, dikembalikan, lalu tercatat** sebagai riwayat dan ulasan.

> [!NOTE]
> Lingkup tugas kuliah: peminjaman berbasis kesepakatan antar pengguna, tanpa pembayaran dan tanpa pengiriman barang.

<img src="assets/divider.svg" alt="" width="100%" height="18">

## Cara kerja

```mermaid
%%{init: {'theme':'base','themeVariables':{'fontFamily':'Georgia, serif','primaryColor':'#DDE8E2','primaryBorderColor':'#7FA391','primaryTextColor':'#2E4A42','lineColor':'#6E8F9E','secondaryColor':'#DCE7EE','tertiaryColor':'#F2F5F4','edgeLabelBackground':'#F2F5F4'}}}%%
flowchart LR
    A[Pemilik mendaftarkan barang] --> B[Peminjam mencari dan mengajukan]
    B --> C{Jadwal bentrok?}
    C -- Ya --> X[Ditolak sistem]
    C -- Tidak --> D[Pemilik menyetujui atau menolak]
    D --> E[Serah-terima dikonfirmasi kedua pihak]
    E --> F[Barang kembali, pemilik konfirmasi]
    F --> G[Selesai dan ulasan]
    classDef calm fill:#DDE8E2,stroke:#7FA391,color:#2E4A42;
    classDef sand fill:#EADFD2,stroke:#B9A58F,color:#4A4036;
    classDef done fill:#B7D0C2,stroke:#5F8574,color:#22392F;
    class A,B,C,D,E,F calm;
    class X sand;
    class G done;
```

### Siklus status transaksi

```mermaid
%%{init: {'theme':'base','themeVariables':{'fontFamily':'Georgia, serif','primaryColor':'#DDE8E2','primaryBorderColor':'#7FA391','primaryTextColor':'#2E4A42','lineColor':'#6E8F9E','secondaryColor':'#DCE7EE','tertiaryColor':'#F2F5F4'}}}%%
stateDiagram-v2
    [*] --> Diajukan
    Diajukan --> Disetujui
    Diajukan --> Ditolak
    Diajukan --> Dibatalkan
    Disetujui --> Dipinjam
    Disetujui --> Dibatalkan
    Dipinjam --> MenungguKonfirmasi
    MenungguKonfirmasi --> Selesai
    Selesai --> [*]
    Ditolak --> [*]
    Dibatalkan --> [*]
```

Status akhir (Selesai, Ditolak, Dibatalkan) tidak bisa kembali ke status sebelumnya. Peminjaman baru dibuat sebagai transaksi baru.

<img src="assets/divider.svg" alt="" width="100%" height="18">

## Tim

<table align="center">
  <tr>
    <td align="center" width="20%">
      <a href="https://github.com/Xzen-tech"><img src="https://github.com/Xzen-tech.png?size=120" width="88" alt="Abdul Wahab"></a><br>
      <b>Abdul Wahab</b><br>Product Owner<br><sub>240504113</sub>
    </td>
    <td align="center" width="20%">
      <a href="https://github.com/kecearif786-lgtm"><img src="https://github.com/kecearif786-lgtm.png?size=120" width="88" alt="Arif Firmansyah"></a><br>
      <b>Arif Firmansyah</b><br>Scrum Master Sprint 1<br><sub>240504123</sub>
    </td>
    <td align="center" width="20%">
      <a href="https://github.com/Riskafzti"><img src="https://github.com/Riskafzti.png?size=120" width="88" alt="Riska Fauziati"></a><br>
      <b>Riska Fauziati</b><br>Scrum Master Sprint 2<br><sub>250504114</sub>
    </td>
    <td align="center" width="20%">
      <a href="github.com/fariel-hub"><img src="github.com/fariel-hub.png?size=120" width="88" alt="M. Fariel Faisa"></a><br>
      <b>M. Fariel Faisa</b><br>Scrum Master Sprint 3<br><sub>250504121</sub>
    </td>
    <td align="center" width="20%">
      <a href="https://github.com/Afdeliliasaribrsembiring"><img src="https://github.com/Afdeliliasaribrsembiring.png?size=120" width="88" alt="Afdeli Lia Sari Br Sembiring"></a><br>
      <b>Afdeli Lia Sari Br Sembiring</b><br>Scrum Master Sprint 4<br><sub>250504129</sub>
    </td>
  </tr>
</table>

<p align="center"><sub>Peran Scrum Master bergilir tiap sprint. Semua anggota selain Product Owner juga bertugas sebagai Developer.</sub></p>

<img src="assets/divider.svg" alt="" width="100%" height="18">

## Roadmap

| Sprint | Fokus | Status |
|:---:|---|---|
| **1** | Repositori, Profil Kelompok, Profil Project, Project Charter | ● Berjalan |
| 2 | Akun pengguna, CRUD barang, katalog, pencarian | ○ Direncanakan |
| 3 | Pengajuan, pengecekan bentrok jadwal, persetujuan, status, serah-terima | ○ Direncanakan |
| 4 | Riwayat, keterlambatan, ulasan, dashboard admin, pengujian, demo | ○ Direncanakan |

> [!TIP]
> Rencana Sprint 2 sampai 4 masih awal. Rinciannya ditetapkan saat Sprint Planning masing-masing sprint, mengikuti arahan dosen.

## Teknologi

Python, Django (template HTML), HTML/CSS/JavaScript, SQLite saat pengembangan (MySQL bila diwajibkan), Git dan GitHub.

<img src="assets/divider.svg" alt="" width="100%" height="18">

## Dokumen Sprint 1

- [Profil Kelompok](Sprint-1/profil-kelompok.md)
- [Profil Project](Sprint-1/profil-project.md)
- [Project Charter](Sprint-1/project-charter.md)



<br>

<p align="center"><sub>Dibuat bersama untuk tugas kuliah, satu sprint dalam satu waktu.</sub></p>
