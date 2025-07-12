Jadi ITB tuh unik, dia bikin kek bahasa sendiri gitu yang tujuannya mirip2 kayak pseudocode lah sebenernya, tapi dikasih semacam batasan atau aturan dalam penulisannya aja yang disebut dengan **Notasi Algoritmik**, we'll get to that later. 
(Notal atau Notasi Algoritmik itu **penting** buat perkuliahan ini karena kita Kuis/UTS/UAS akan make ini dan ga nyentuh bahasa pemrograman sama sekali!)

## Tentang Pemrograman Prosedural
- Penting buat paham **Computational Thinking** (dipelajari di WI1102) karena ya bahasa bisa apa aja, tapi kemampuan buat mikirnya itu yang **overall** sama aja.
- ![[Screenshot 2025-07-10 at 18.38.39.png]] (Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)
- Imperative Programming = Imperatif kan artinya perintah, yaudah berarti Imperative Programming adalah suatu untaian instruksi. Dipake di bahasa mesin ataupun *assembly*. Biasanya pake *goto*. Contoh :
	```
	Code C:
	#Include <stdio.h>

	int main(){
		int i = 0;
		loop:
		printf("%d\n", i);
		if (++i < 5) goto loop;
		printf("Done!\n);
	}

	Output:
	0
	1
	2
	3
	4
	Done!
	```
	Buat yang belum ngerti C gapapa, tapi basically dia punya sebuah angka yang "dilabelin" i dan valuenya = 0. Nah dia bakal melakukan loop di mana dia bakal nampilin angka i, nah terus dia bakal nambah i dengan 1 (++i) dan bakal ngecek apakah i < 5, kalo **iya** maka bakal masuk ke loop lagi di mana dia bakal output nilai i lagi. Nah ketika i nya udah >= 5, maka dia bakal ga masuk loop dan bakal lanjut ke next line yaitu Done!.

	goto tuh dianggep berbahaya karena bisa buat alur program lompat ke mana aja yang buat kode tuh akses ke memori yang ga valid (ini di bahas di orkom i guess tapi secara singkat gitu), take a look at this:
	```
	int x = 0;
	goto there;
	int y = 1;
	there:
	printf("%d, %d\n", x, y);
	``` 
	As you can see, dia kan nge "labelin" x = 0 terus masuk ke there, di mana there itu dia nge output nilai x dan y. x nya udah ada, tapi y nya belom karena ya belom di "labelin" karena peng"labelan" y itu terjadi setelah goto there.

	Makanya dikenalin ***control flow* berbasis blok**. Basically dibatasin lah biar ga akses memori di luar blok tersebut.
	```
	Code C:
	int x = 5;
	if (x != 10) {
		int y = 8;
		printf("%d\n", y);
		// z ga di declare jadi gakenal
	}
	else {
		int z = 9;
		printf("%d\n", z);
		// y ga di declare jadi gakenal
	}
	// y dan z ga di declare jadi gakenal

	Output:
	8
	```
- LALU, **Prosedural** **Programming** = nambahin reusability subprogram berbentuk **Prosedur** (ngubah *state program*, tidak ngebalikin sebuah nilai) dan **Fungsi** (ngelakuin pemetaan ke nilai lain (return value) tapi tidak ngubah *state program*). Prosedur tuh kalo di C bentuknya **void** kalo fungsi tuh bentuk datanya (bisa **int, float, dll**. yang kalo kalian notice biasanya ada int main nah itu tuh fungsi). Nah reusability ini nanti ada hubungannya sama ADT (Abstract data type) bakal di bagian lain.

## Tentang Notasi Algoritmik
As i said, ini basically kayak pseudocode aja karena gamungkin kita belajar semua bahasa pemrograman, tapi kita bisa belajar computational thinkingnya -> lewat notasi algoritmik.
- Notal basically berbasis paradigma prosedural.
- Ada beberapa aturan yang wajib untuk diingat dalam melakukan penulisan dengan notasi algoritmik
- Contoh : ![[Screenshot 2025-07-10 at 19.08.31.png]](Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)
	Notice that di bagian input tuh ada underline dan bold, nah itu harus ada (tapi kalo di tulisan biasanya cuma underlinenya aja)
	Nah ini bisa diimplementasiin ke bahasa lain kayak C, C++, Python, dll.

### Struktur Dasar di Notal
![[Screenshot 2025-07-10 at 19.12.22.png]](Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)
- Spesifikasi Program = Basically ngasih tau ini program ngapain aja, outputnya apa, inputnya apa, dll.
- **KAMUS** = Ini kayak ngasih tau variabel yang dipake apa aja, konstanta, fungsi, prosedur. Dan dikasih tau juga kayak tipe datanya apa (integer kah, boolean kah, dll)
- **ALGORITMA** = ya langkah2nya
- {} = ini bentuk komentar

Contoh Program Notasi Algoritmik
![[Screenshot 2025-07-10 at 19.17.29.png]](Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)
Perhatiin cara nulisnya, indentasinya, underlinenya, boldnya, dll

### Tipe Data di Notal
#### Tipe Dasar

| Notal (bagian ini harusnya diunderline semua) | Domain Nilai                           |
| --------------------------------------------- | -------------------------------------- |
| boolean                                       | true, false (harusnya undelrine)       |
| integer                                       | -∞ ≤ 0 ≤ ∞, tapi bilangan bulat        |
| real                                          | bilangan rill (desimal)                |
| character                                     | karakter atau huruf 'A', '#', 'b', dll |
| string                                        | kumpulan karakter "Acatrix", dll       |
#### Tipe Bentukan
Some of tipe data tuh ga tersedia secara otomatis, jadi harus dibuat sama programmer (dibentuk dari gabungan tipe dasar yang disebutin di tabel atas). Contoh: ![[Screenshot 2025-07-10 at 19.42.12.png]](Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)

#### Konstanta
Konstanta = Nilainya tetap!
Contoh:
![[Screenshot 2025-07-10 at 19.46.04.png]](Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)

#### Assignment
Simplenya kalo di C tuh
```
int a;
a = 5;
```
Kalo di Notal tuh jadinya
```
a <- 5 {int a nya anggap udah ada di bagian KAMUS}
```

#### Ekspresi
- + - \* / 
- < > = ≠ ≥ ≤
- ![[Screenshot 2025-07-10 at 19.52.17.png]](Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)
- ![[Screenshot 2025-07-10 at 19.51.32.png]](Gambar credit to PPT IF1210/Pemrograman Prosedural dan Notasi Algoritmik)



Lebih lanjut sebenernya bisa baca di Diktat Dasar Pemrograman Bagian Pemrograman Prosedural (gausah semua tapi beberapa yang dirasa aja, tapi jujur beberapa di Diktat tuh ada yang beda dibanding yang ada di notes ini, notes ini based on PPT sih jadi kayanya mending ikut ini).

