<div align="center">

<img src="assets/banner.svg" alt="BorrowMate: pinjam apa saja, antar sesama mahasiswa" width="100%">

</div>

<img src="assets/divider.svg" alt="" width="100%" height="18">

<h2 align="center"><img src="assets/header-kenapa.svg" alt="Kenapa BorrowMate?" width="100%"></h2>

Banyak mahasiswa punya barang yang jarang dipakai: tripod, kalkulator ilmiah, alat praktikum, buku referensi. Mahasiswa lain hanya butuh barang itu sebentar. Selama ini urusannya lewat chat dan ingatan, sehingga jadwal mudah bentrok, barang lupa dikembalikan, dan tidak ada catatan.

BorrowMate merapikan seluruh prosesnya: **barang dipublikasikan, diajukan, disetujui, diserahkan, dikembalikan, lalu tercatat** sebagai riwayat dan ulasan.

<img src="assets/kenapa-kartu.svg" alt="Masalah: jadwal bentrok, barang lupa dikembalikan, tidak ada catatan. Solusi: proses dari pengajuan sampai tercatat sebagai riwayat dan ulasan. Lingkup: peminjaman berbasis kesepakatan, tanpa pembayaran dan tanpa pengiriman barang." width="100%">

> [!NOTE]
> Lingkup tugas kuliah: peminjaman berbasis kesepakatan antar pengguna, tanpa pembayaran dan tanpa pengiriman barang.

<img src="assets/divider.svg" alt="" width="100%" height="18">

<h2 align="center"><img src="assets/header-cara-kerja.svg" alt="Cara kerja" width="100%"></h2>

<img src="assets/alur-kerja.svg" alt="Alur kerja: pemilik mendaftarkan barang, peminjam mencari dan mengajukan, sistem mengecek jadwal bentrok (jika ya, ditolak sistem), pemilik menyetujui atau menolak, serah-terima dikonfirmasi kedua pihak, barang kembali dan pemilik konfirmasi, selesai dan ulasan." width="100%">

<details>
<summary><sub>Lihat versi diagram yang bisa diedit (Mermaid)</sub></summary>

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
    classDef ask fill:#F9F1D2,stroke:#B8A45A,color:#5C5030;
    classDef sand fill:#F8E4D9,stroke:#C99A82,color:#6B4A3A;
    classDef done fill:#B7D0C2,stroke:#5F8574,color:#22392F;
    class A,B,D,E,F calm;
    class C ask;
    class X sand;
    class G done;
```

</details>

<h3 align="center"><img src="assets/header-status.svg" alt="Siklus status transaksi" width="100%"></h3>

```mermaid
%%{init: {'theme':'base','themeVariables':{'fontFamily':'Georgia, serif','primaryColor':'#DDE8E2','primaryBorderColor':'#7FA391','primaryTextColor':'#2E4A42','lineColor':'#6E8F9E','secondaryColor':'#DCE7EE','tertiaryColor':'#F3F0FA','tertiaryBorderColor':'#D3C9EA','transitionColor':'#6E8F9E','transitionLabelColor':'#2E4A42','stateBkg':'#DDE8E2','stateLabelColor':'#2E4A42','specialStateColor':'#9A8CC0','labelColor':'#2E4A42'}}}%%
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

<h2 align="center"><img src="assets/header-tim.svg" alt="Tim" width="100%"></h2>

<table align="center">
  <tr>
    <td align="center" width="20%">
      <a href="https://github.com/Xzen-tech"><img src="https://github.com/Xzen-tech.png?size=120" width="88" alt="Foto GitHub Abdul Wahab"></a><br>
      <a href="https://github.com/Xzen-tech"><img src="assets/team-abdul.svg" width="170" alt="Abdul Wahab, Product Owner, NIM 240504113"></a>
    </td>
    <td align="center" width="20%">
      <a href="https://github.com/kecearif786-lgtm"><img src="https://github.com/kecearif786-lgtm.png?size=120" width="88" alt="Foto GitHub Arif Firmansyah"></a><br>
      <a href="https://github.com/kecearif786-lgtm"><img src="assets/team-arif.svg" width="170" alt="Arif Firmansyah, Scrum Master Sprint 1, NIM 240504123"></a>
    </td>
    <td align="center" width="20%">
      <a href="https://github.com/Riskafzti"><img src="https://github.com/Riskafzti.png?size=120" width="88" alt="Foto GitHub Riska Fauziati"></a><br>
      <a href="https://github.com/Riskafzti"><img src="assets/team-riska.svg" width="170" alt="Riska Fauziati, Scrum Master Sprint 2, NIM 250504114"></a>
    </td>
    <td align="center" width="20%">
      <a href="https://github.com/fariel-hub"><img src="https://github.com/fariel-hub.png?size=120" width="88" alt="Foto GitHub M. Fariel Faisa"></a><br>
      <a href="https://github.com/fariel-hub"><img src="assets/team-fariel.svg" width="170" alt="M. Fariel Faisa, Scrum Master Sprint 3, NIM 250504121"></a>
    </td>
    <td align="center" width="20%">
      <a href="https://github.com/Afdeliliasaribrsembiring"><img src="https://github.com/Afdeliliasaribrsembiring.png?size=120" width="88" alt="Foto GitHub Afdeli Lia Sari Br Sembiring"></a><br>
      <a href="https://github.com/Afdeliliasaribrsembiring"><img src="assets/team-afdeli.svg" width="170" alt="Afdeli Lia Sari Br Sembiring, Scrum Master Sprint 4, NIM 250504129"></a>
    </td>
  </tr>
</table>

<p align="center"><sub>Peran Scrum Master bergilir tiap sprint. Semua anggota selain Product Owner juga bertugas sebagai Developer.</sub></p>

<img src="assets/divider.svg" alt="" width="100%" height="18">

<h2 align="center"><img src="assets/header-roadmap.svg" alt="Roadmap" width="100%"></h2>

<img src="assets/roadmap.svg" alt="Sprint 1 (berjalan): repositori, profil kelompok, profil project, project charter. Sprint 2 (direncanakan): akun pengguna, CRUD barang, katalog, pencarian. Sprint 3 (direncanakan): pengajuan, pengecekan bentrok jadwal, persetujuan, status, serah-terima. Sprint 4 (direncanakan): riwayat, keterlambatan, ulasan, dashboard admin, pengujian, demo." width="100%">

> [!TIP]
> Rencana Sprint 2 sampai 4 masih awal. Rinciannya ditetapkan saat Sprint Planning masing-masing sprint, mengikuti arahan dosen.

<h2 align="center"><img src="assets/header-teknologi.svg" alt="Teknologi" width="100%"></h2>

<img src="assets/teknologi.svg" alt="Python, Django (template HTML), HTML/CSS/JavaScript, SQLite saat pengembangan (MySQL bila diwajibkan), Git dan GitHub." width="100%">

<img src="assets/divider.svg" alt="" width="100%" height="18">

<h2 align="center"><img src="assets/header-dokumen.svg" alt="Dokumen Sprint 1" width="100%"></h2>

<table align="center">
  <tr>
    <td align="center" width="33%"><a href="Sprint-1/profil-kelompok.md"><img src="assets/dokumen-kelompok.svg" alt="Profil Kelompok" width="100%"></a></td>
    <td align="center" width="33%"><a href="Sprint-1/profil-project.md"><img src="assets/dokumen-project.svg" alt="Profil Project" width="100%"></a></td>
    <td align="center" width="33%"><a href="Sprint-1/project-charter.md"><img src="assets/dokumen-charter.svg" alt="Project Charter" width="100%"></a></td>
  </tr>
</table>

<br>

<img src="assets/footer.svg" alt="Dibuat bersama untuk tugas kuliah, satu sprint dalam satu waktu." width="100%">
