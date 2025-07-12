- Kenapa penting? Karena dengan ini membuat sebuah program itu *Modular*, yang artinya lebih gampang buat debug, team work, dll. Fungsi dan prosedur juga memudahkan programmer dalam coding, code reuse instead of rewriting.
- INI BAKAL KEPAKE BANGET DI ADT NANTI!!!
- Note = Di fungsi/prosedur tuh ada KAMUS LOKAL (beda sama KAMUS biasa)

## Fungsi
**Penulisan dalam Notasi Algoritmik**
![[Screenshot 2025-07-11 at 18.05.06.png]]Gambar credit to PPT IF1210/Modular Programming
- param1, param2, dst = Itu ibarat kata kayak variabel cuma only on that function. Jadi misalkan di contoh itu ada param x kan, nah dia bakal nge return nilai x \* x, nah nanti misalkan di kode utama ada variabel y gitu dan kita mau pake function Kuadrat itu yaudah tinggal Kuadrat(y), x yang ada di param tadi bakal digantiin sama y dan bakal return y \* y.
- type1, type2, dst = Tipe data si parameter
- type_hasil = Tipe data dari hasil atau apa yang di return
- Note = perlu ada -> di fungsi karena fungsi harus membuahkan suatu hasil (beda dengan prosedur).

## Prosedur
**Penulisan dalam Notasi Algoritmik**
![[Screenshot 2025-07-11 at 18.41.57.png]]Gambar credit to PPT IF1210/Modular Programming
- input/output = GAMPANGNYA GINI, misalkan di *main* atau kode utama ada variabel x. nah **input** itu misalkan di dalam prosedur itu ada suatu skema penjumlahan dan disana bakal **dipake** variabel x, nah maka itu menjadi input. Kalo **output**, misalkan di dalam prosedur tuh ada x = 60 (terlepas x nya berapa pas awal sebelum masuk ke prosedur), maka nanti di *main* atau **kode utamanya** bakal **keubah** jadi x = 60 juga (beda sama fungsi tadi kalo fungsi kan dia ngereturn, kalo ini dia ngubah variabel yang ada di kode utama atau *main*).
- param, type itu sama kayak di fungsi
- I.S. = Initial State, jadi kayak sebelum prosedur itu tuh dia kondisinya gimana
- F.S. = Final State, setelah prosedur itu dia kondisinya gimana


## Pemanggilannya
![[Screenshot 2025-07-11 at 18.51.05.png]]Gambar credit to PPT IF1210/Modular Programming
Asumsi CetakInt sama Kuadrat itu udah ada fungsi/prosedurnya. 


## Implementasi di C
### Fungsi
```
int kpk(int a, int b) {
	if (a == 0 || b == 0) {
	return 0;
	}
	else {
	return (a*b)/fpb(a,b);
	}
}
```
Ini kalo di notal bentuknya gini nih![[Screenshot 2025-07-11 at 19.02.33.png]]

### Prosedur
```
void BacaPOINT (POINT *p){
	scanf("%d", &p->x);
	scanf("%d", &p->y);
}

void TulisPOINT (POINT p){
	printf("%d", p.x);
	printf("%d", p.y);
}
```
Ini jujur harus ngerti konsep pointers dikit sih. Kalo di notal begini (note: POINT itu intinya sebuah tipe data bentukan yang isinya x dan y)![[Screenshot 2025-07-11 at 19.15.04.png]]


Buat pemanggilan itu sebenernya kurang lebih sama aja kayak di notal, paling buat prosedur itu agak sedikit beda karena harus paham sedikit mengenai pointers (bakal dibahas di bagian lain) tapi intinya gini![[Screenshot 2025-07-11 at 19.19.26.png]]Gambar credit to PPT IF1210/Modular Programming

