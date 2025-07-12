- Blok Program biasanya di antara {}, contoh:
	```
	if (a != 0) {
	printf("Bukan nol");
	}
	```
	Perhatiin {} di if nya.
- Note: Bahasa C itu **Case Sensitive**

## Konstanta dan Variabel
### Konstanta
```
//cara 1 pake const
const [<type>] <nama> = <harga>;

//cara 2 pake macro
#define <nama> <harga>
```
Note: macro itu berarti compiler bakal jalanin itu dulu sebelum compile.
### Variabel
```
//deklarasi
<type> <nama>;

//assign
<nama> = <harga>;

//deklarasi sekaligus assign
<type> <nama> = <harga>;
```

## Tipe Data
### Bilangan

| Tipe                                                        | Deskripsi                                                                                                                                                                                                                           |
| ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[signed] int**                                            | Integer yang natural, (signed tuh tanda, artinya bisa -), biasanya kalo kita declare pake int doang itu dia signed. Ukurannya misalkan 32 bits (ngikut mesin), lebih panjang dari **short int** tapi lebih pendek dari **long int** |
| **[signed] short [int]**                                    | Minimal 16 bits of integer                                                                                                                                                                                                          |
| **[signed] long [int]**                                     | Minimal 32 bits of integer                                                                                                                                                                                                          |
| **unsigend int, unsigned short [int], unsigned long [int]** | integer >= 0                                                                                                                                                                                                                        |
| **int, short int, long int**                                | biasanya sih make ini ya in most cases.                                                                                                                                                                                             |
| **float**                                                   | single-precision, ex. 6 digits decimal                                                                                                                                                                                              |
| **double**                                                  | double-precision, ex. 10 digits decimal                                                                                                                                                                                             |
| **long double**                                             | extended-precision, ex. 18 digits decimal                                                                                                                                                                                           |

### Boolean
- C tuh gaada boolean
- Jadi ada 2 cara.
	- Pake integer (misal 0 = false, selain 0 = true)
	- Pake konstanta (misalkan \#define boolean unsigned char, \#define TRUE 1, \#define FALSE 0). Semua ini bisa aja di definisiin di boolean.h biar gampang (tentang .h ini bakal di bahas di bagian yang lain)

### String or Character
- **Character** tuh kayak sebuah huruf
- **String** = kumpulan character
- Kalo belajar Berpikir Komputasional pasti tau soal Array, nah **String** itu basically array of **char** dengan tambahan \0 (ini kayak tandanya akhir gt lah atau nothing).

### Enumerasi
Think of it kayak array tapi ga juga. Liat contohnya aja ya
```
typedef enum {
	senin, selasa, rabu, kamis, jumat, sabtu, minggu
} hari; // artinya senin = 0, selasa = 1, dst

int main() {
	hari h;
	h = senin; // h = 0
}
```

### Bentukan (tuple)
Balik lagi, kayak array cuma di dalemnya bisa banyak tipe data. Liat contohnya aja dah
```
typedef struct Point {
	float X;
	float Y;
} point;

int main() {
	point a;
	float b;

	b = a.X;
	a.Y = 5.9;
}
```

## Operator
| Notal           | C    |
| --------------- | ---- |
| +               | +    |
| \-              | \-   |
| \*              | \*   |
| /               | /    |
| div (underline) | /    |
| mod (underline) | %    |
| var = var + 1   | \++  |
| var = var - 1   | \--  |
| >               | >    |
| <               | <    |
| =               | ==   |
| ≠               | !=   |
| ≥               | >=   |
| ≤               | <=   |
| and (underline) | &&   |
| or (underline)  | \|\| |
| not (underline) | !    |
### Operator Bit
Ini lebih dipelajarin di IF1230 Organisasi dan Arsitektur Komputer tapi gapapa sekilas aje
- << = shift left
- >> = shift right
- & = and
- | = or
- ^ = xor
- ~ = not

## Input/Output
### Input
intinya pake
```
scanf("<format>", <list-nama>);

//contoh
scanf("%d", &x);
scanf("%d %d", &x, &y);
```
- %d = integer
- %f = real
- %c = character
- %s = string

### Output
intinya
```
printf("<format>", <list-nama>);

//contoh
printf("%d %d", x, y);
```
- %d = integer
- %f = real
- %c = character
- %s = string

BELAJAR JANGAN DARI SINI DOANG TAPI TEMPAT LAIN JUGA
Rekomendasi link
- [w3schools](https://www.w3schools.com/c/)
- [FCC (personally gw belajar dr sini doang)](https://youtu.be/KJgsSFOSQv0?si=UgJ_N80153ZCPoaE)
