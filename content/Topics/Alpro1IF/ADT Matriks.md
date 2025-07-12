Matriks itu kumpulan informasi yang tiap elemennya ditentuin sama dua indeks (baris dan kolom). Ini struktur data statik, jadi ukurannya ditentuin di awal.

- Memori: Kita harus bedain antara memori total matriks dan memori yang efektif dipake (rowEff dan colEff). Sebenernya mirip2 Neff sih.
- Notasi Algoritmik:
    - Akses elemen:
        namaMatriks\[indeks1, indeks2].
    - ADT biasanya disimpen dalam bentuk
- Operasi:
    - CreateMatrix: Bikin matriks kosong dengan ukuran tertentu.
    - getRowEff/getColEff: Dapetin ukuran baris/kolom efektif.
    - isIdxEff: Ngecek apakah indeks itu valid dan efektif.
    - getElmt/setElmt: Akses dan ubah nilai elemen.
    - copyMatrix: Salin matriks.
    - Dll (baca aja di [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs))

Contoh: 
![[Screenshot 2025-07-12 at 17.58.37.png]]
![[Screenshot 2025-07-12 at 17.52.26.png]]

Kalo di C contohnya:
```
int ini_array[3][4];

ini_array[0][1] = 9;
x = ini_array[2][3];
```
Nah kemaren praknya tuh disuruh implementasi Operasi2 ADT Matrix ke C (baca [githubnya nicholaswisee aja\(shoutout to wise)](https://github.com/nicholaswisee) kalo mau belajar2)