
## Pointer
Ini bakal singkat banget tapi intinya ![[Screenshot 2025-07-12 at 04.38.34.png]]Gambar credit to PPT IF1210/Pointer
Take a look at this, anggep pointer tuh kayak lu nunjuk sebuah alamat. Setiap nilai yang lu punya di program tuh bakal disimpen di suatu alamat, nah misal lu mau buat variabel baru dengan nilai yang sama, instead lu bikin "rumah" baru, lu bisa bilang kayak oke variabel ini nilainya ngerujuk ke "rumah" itu (di mana rumah itu maksudnya adalah nilai yang sebelumnya dah ada). Jadi kayak kalo di foto tuh px = alamat dari x di mana di dalem x itu = 13.

![[Screenshot 2025-07-12 at 04.41.21.png]]Gambar credit to PPT IF1210/Pointer

demi apapun ya, pointer would be SO MUCH EASIER kalo lu nonton youtube aja DAN SAMBIL PRAKTEK DI LAPTOP karena ya materinya sebutuh practice itu. gw disini gabakal jelasin detail kayak syntaxnya gimana dll BENERAN BUKA YOUTUBE AJA (atau kalo make vscode dan extension C nya gacor sih biasanya bakal muncul error jg kalo syntaxnya salah jd yaudah aja)

**YOUTUBE REFERENCE BUAT BELAJAR POINTER**
- [Kalo mau gacor bat tapi minus 3 jam aje videonya](https://youtu.be/zuegQmMdy8M?si=cc1Feilpeiw-8GFa)
- [Kalo mau yaudah sepahamnya aja tapi ga sesingkat itu juga](https://youtu.be/KGhacRRMnDw?si=Wv370GqiSRnqPKJe)
- [Ini yang gw personally nonton dan cukup paham si jujur](https://youtu.be/2ybLD6_2gKM?si=47hSZvKPMBF0nBsn)


## ADT
ADT TUH APASI

Abstract Data Type. Intinya, anggeplah lu punya PC. Kan PC tuh kalo ngerakit kayak banyak partsnya yang bisa lu pilih dan customize kan, ya basically ADT tuh kayak gitu. Kayak, kalo di macbook deh misalkan kan lu gabisa customize banyak hardwarenya ya karena semua disolder, nah PC kan bisa.

Jadiiii, ADT tuh sebuah model konseptual yang fokusnya tuh pada PERILAKUNYA, yang based on
- **Data** apa yang disimpen
- **Nilai-nilai** apa yang mungkin buat data itu
- **Operasi** apa yang bisa dilakuin

Contoh: ![[Screenshot 2025-07-12 at 04.51.08.png]]Gambar credit to PPT IF1210/Pengantar Abstract Data Type

Jadi kayak misal lu mau buat program jam, nah daripada langsung kode secara langsung di "main" mending buat fungsi aja tiap komponen biar apa, biar nanti di main tinggal manggil fungsi2nya aja.
ADT Time tuh bisa banyak kayak misalkan setHours, readHours,  printTime, dll. Lebih lengkapnya baca di diktat aja.

### Implementasi di C
Ada 4 bagian
- Header .h = Ini intinya kayak sebuah kamus tapi gaada implementasi dari si fungsi2nya
- Body .c = Ini implementasi dari fungsi2 yang didefinisiin di header tadi
- Driver .c = Ini mainnya, intinya berisi program utama lah
- Tes .c = Jarang kepake si.

```
// point.h
#ifndef POINT_H
#define POINT_H

/* Definisi type POINT */
typedef struct {
	float X; /* absis (sumbu X) */
	float Y; /* ordinat (sumbu Y) */
} POINT;

/* Macro selektor komponen */
#define Absis(P) (P).X
#define Ordinat(P) (P).Y

/* Membentuk POINT P dengan komponen X dan Y */
void CreatePoint(POINT *P, float X, float Y);

/* Membaca nilai POINT dari stdin: masukkan X Y */
void BacaPOINT(POINT *P);

/* Menulis POINT ke stdout dalam format "(X,Y)" */
void TulisPOINT(POINT P);


// point.c
#include <stdio.h>

void CreatePoint(POINT *P, float X, float Y){
	Absis(*P) = X;
	Ordinat(*P) = Y;
}

void BacaPOINT(POINT *P){
	scanf("%f", &Absis(*P));
	scanf("%f", &Ordinat(*P));
}

void TulisPOINT(POINT P){
	printf("(%f,%f)", Absis(P), Ordinat(P));
}
```


Nah, ADT tuh bakal kebagi jadi beberapa bagian jadi liat aja tar


## Array Statik dan Dinamik
Intinya
- **Statik** = Ukuran ditentuin pas compile-time **dan** ukuran arraynya gabisa diubah
- **Dinamis** = Ukuran ditentuin pas run-time (pas compile-time belom tau ukurannya) **dan** ukuran arraynya bisa diubah.
Implementasi di C? liat di youtube aja asli pokoknya yang malloc2 gitu kalo dinamik![[Screenshot 2025-07-12 at 05.06.36.png]] (perlu stdlib.h)