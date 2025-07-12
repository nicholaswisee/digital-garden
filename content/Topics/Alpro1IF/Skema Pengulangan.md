Terbagi menjadi beberapa jenis berdasarkan:
## Jumlah Pengulangan
![[Screenshot 2025-07-11 at 01.23.05.png]](Gambar credit to PPT IF1210/Pengantar Dunia Pemrograman)
Intinya, ini dia **harus tau berapa kali** aksinya dilakuin (jadi programmer udah tau duluan dia harus berapa kali jalan intinya gitu lah)

Contoh:
![[Screenshot 2025-07-11 at 01.25.20.png]](Gambar credit to PPT IF1210/Pengantar Dunia Pemrograman)

## Kondisi Berhenti
![[Screenshot 2025-07-11 at 01.26.07.png]](Gambar credit to PPT IF1210/Pengantar Dunia Pemrograman)
\<kondisi-berhenti> itu kayak if lah intinya (jadi bentuknya ekspresi boolean)

Alur berpikirnya gini
- Line 1 (repeat) bakal baca repeat (masuk loop)
- Line 2 (\<aksi>) bakal ngelakuin aksinya
- Line 3 (until \<kondisi-berhenti>) bakal ngecek apakah kondisi-berhenti terpenuhi apa ga
- kalo ga terpenuhi maka bakal masuk ke line 2 lagi dan lanjut ke line 3, gitu terus
Maka? dia pasti ngejalanin aksinya minimal 1x meskipun sebenernya dari awal \<kondisi-berhenti>nya udah terpenuhi

## Kondisi Mengulang
![[Screenshot 2025-07-11 at 01.30.05.png]](Gambar credit to PPT IF1210/Pengantar Dunia Pemrograman)
\<kondisi-mengulang> kayak \<kondisi-berhenti> tadi

Alur berpikirnya gini
- Line 1 (while) dia bakal ngecek apakah \<kondisi-mengulang> terpenuhi apa ga, kalo iya maka dia akan masuk ke loopnya
- Line 2 dia bakal ngelakuin aksinya
- Masuk ke line 1 lagi, cek lagi, kalo terpenuhi ke line 2, gitu terus
Maka? dia bisa kemungkinan aksi ga pernah dilakuin (kalo dari awal \<kondisi-mengulang> udah tidak terpenuhi) ini disebut **kasus kosong**

## Dua Aksi (1)
![[Screenshot 2025-07-11 at 01.35.39.png]](Gambar credit to PPT IF1210/Pengantar Dunia Pemrograman)

Alur berpikirnya gini
- Line 1 (iterate) dia bakal masuk ke \<aksi-1>
- Line 2 (\<aksi-1>) dia bakal ngelakuin \<aksi-1> dulu
- Line 2 (stop) dia bakal ngecek apakah \<kondisi-berhenti> terpenuhi apa ga (kalo iya yaudah stop loopnya)
- Kalo ngga dia bakal lanjut ke \<aksi-2>
- Terus lanjut ke \<aksi-1> lagi
Maka? dia minimal 1x ngelakuin \<aksi-1> dan \<aksi-2> bisa ga sama sekali. Tipe ini merupakan gabungan dari repeat-until dan while-do

## Pencacah
![[Screenshot 2025-07-11 at 01.44.22.png]](Gambar credit to PPT IF1210/Pengantar Dunia Pemrograman)

Ya itu intinya anggaplah ada sebuah variabel i (pencacahnya), itu dia bakal start dengan i = \<min>, nah nanti dia bakal lakuin \<aksi> terus i nya akan i++, nah nanti bakal lakuin \<aksi> lagi, terus sampe i = \<maks>. Buat yang cacah mundur sama aja cuma i--.
Pencacah harus ordinal (ex: integer) dan harus tau nilai min dan maksnya dari awal.


Notice that banyak banget tipe pengulangan kan. Lantas, pake yang mana? nah itu serunya Alpro ini, karena justru kita harus nentuin pengulangan yang benar dan tepat buat persoalan tertentu.


## Contoh Implementasinya di C
### repeat-until
```
do {
	printf("Argha ganteng!");
	i++; //anggap i udah di declare dan inisialisasi
} while (i < 5)
```

### while-do
```
while (i < 5) {
	printf("Argha ganteng!");
	i++; //anggap i udah di declare dan inisialisasi
}
```

### traversal
```
for (int i = 0; i < 5; i++){
	printf("Argha ganteng!);
}

for (int i = 5; i > 0; i++){
	printf("Argha ganteng!");
}
```
Note: akan ada perbedaan ketika int i di dalam for (...) sama kalo di declare dulu di luar for. Kalo di dalam yaudah once loopnya kelar dan mau pake variabel i lagi ya gabakal kesimpen nilai i yang terakhir (misalkan di for loop pertama itu i terakhir di i = 4), sedangkan kalo di luar maka kalo abis loopnya kelar dan mau dipake lagi i nya maka bakal i = 4 tetep.

### iterate-stop
```
for (;;){ //ini intinya ya infinite loop sih si ;;
	printf("Argha ganteng!");
	i++; //anggap i udah di declare dan inisialisasi
	if (i > 5){
		break; // dia bakal berhenti ngeloop
	}
	else {
		printf("\n"); // \n berguna buat bikin new line, kalo ga gini dia bakal Argha ganteng!Argha ganteng!... outputnya
	}
}
```
#Latihan_Soal_SkemaPengulangan