Ini berhubungan sama file eksternal gitu intinya (ini cuma dipelajarin di IF/EL/EB, jadi STI ga belajar ini)

![[Screenshot 2025-07-12 at 04.16.03.png]]Gambar credit to IF1210/Skema Standar Bag. 5

Jadi kita bisa:
- Buka file
- Baca isi file
- Tulis isi file
- Tutup file

Nah sebelum ngelakuin itu semua, kita harus assign nama fisik (yang ada di hardisk) ke lojik (variabel di program kita)![[Screenshot 2025-07-12 at 04.17.23.png]]Gambar credit to IF1210/Skema Standar Bag. 5


## Buka File
![[Screenshot 2025-07-12 at 04.17.51.png]]Gambar credit to IF1210/Skema Standar Bag. 5
![[Screenshot 2025-07-12 at 04.18.05.png]]Gambar credit to IF1210/Skema Standar Bag. 5
rewrite tuh kayak nyiapin buat siap ditulis gitu deh
## Baca File
![[Screenshot 2025-07-12 at 04.18.50.png]]Gambar credit to IF1210/Skema Standar Bag. 5

## Tulis File
![[Screenshot 2025-07-12 at 04.19.12.png]]Gambar credit to IF1210/Skema Standar Bag. 5

## Tutup File
![[Screenshot 2025-07-12 at 04.19.27.png]]Gambar credit to IF1210/Skema Standar Bag. 5
Kalo ada tutup maka ada open/rewrite. Dan kalo udah ditutup gabisa diakses lagi.



Nah biasanya tuh kalo di notal gini kita harus buat fungsi EOP (boolean) dari pembacaan file (ini bentuknya biasanya kayak ada mark di file yang nandain kalo udah kelar. tapi mostly jarang buat disuruh bikin fungsi EOP nya sih)


## Skema Dasar Pembacaan File
![[Screenshot 2025-07-12 at 04.21.49.png]]Gambar credit to IF1210/Skema Standar Bag. 5
Notice ga cara baca tiap "line" atau elementnya tuh tinggal read-read lagi aja gitu, jadi gaada indeks. Makanya perlu MARK.
Bisa juga pake while-do

## Skema Dasar Penulisan File
![[Screenshot 2025-07-12 at 04.23.07.png]]Gambar credit to IF1210/Skema Standar Bag. 5
Kurang lebih sama aja kayak tadi tapi instead read ini write. Terus juga kalo udah kelar maka harus ditulis lagi MARKnya.
Bisa juga pake while-do


## Konsolidasi
Kayak pengelompokan gitu sih intinya
Ada 2 versi
- Tanpa separator = kuncinya berubah
- Dengan separator = ada yang misahin

Contoh tanpa separator =
![[Screenshot 2025-07-12 at 04.25.55.png]]Gambar credit to IF1210/Skema Standar Bag. 5
![[Screenshot 2025-07-12 at 04.26.09.png]]Gambar credit to IF1210/Skema Standar Bag. 5
![[Screenshot 2025-07-12 at 04.27.05.png]]Gambar credit to IF1210/Skema Standar Bag. 5
Contoh kalo mau ngeproses rata-rata nilai mahasiswa yang tiap mahasiswa ngambil jumlah matkulnya kan beda2.

Lebih lengkapnya baca PPT nya di [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs)


## Merging
INI GAMPANG. ASLI. intinya masukin file pertama dulu terus baru kedua. Kalo mau terurut? yaudah berarti langsung dua2nya, dicompare, kalo lebih gede/kecil dimasukin yang file itu terus di "next", dst udah sampe salah satunya kelar, kalo udah dicek mana yang masih ada kalo masih yaudah tinggal masukin (yang udah kelar diemin aja). Liat ini aja deh

- **Kalo make AND** : Ini kayak yang gw bilang di atas tadi, jadi dia dua2nya dulu tar kan kalo udah abis salah satunya (MARK) kan bakal false tuh while-do yang pertama, yaudah tar bakal jalanin while-do yang kedua (yang mananya tergantung yang belom MARK yang mana)
	![[Screenshot 2025-07-12 at 04.30.59.png]]Gambar credit to IF1210/Skema Standar Bag. 5
	- **Kalo make OR** = lebih simpel, kalo misalkan salah satu abis dia bakal tetep jalan kan pake OR soalnya, jadi gaperlu banyak loopnya.
	![[Screenshot 2025-07-12 at 04.33.40.png]]Gambar credit to IF1210/Skema Standar Bag. 5


## Sekilas kalo di C
```
FILE *NamaArsip;

//open
namaArsip = fopen(namaFisik, "r"); //nama fisik bisa juga direktori
retval = fscanf(namaArsip, <format isi file>, &nama_rek);

//rewrite
namaArsip = fopen(namaFisik, "w");

//read
retval = fscanf(namaArsip, <format isi file>, &nama_rek);

//write
retval = fscanf(namaArsip, <format isi file>, rek_baru);

//close
fclose(namaArsip);
```