- Array = Sekumpulan elemen yang bertipe sama, diakses dengan indeks
## Implementasi dalam Notal
![[Screenshot 2025-07-11 at 19.22.16.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 3
### Akses sebuah array
- Kalo ditulis tangan = ![[Screenshot 2025-07-11 at 19.23.31.png]]
- Kalo diketik = nama-var\[indeks]

Array bisa jadi salah satu komponen dalam tipe bentukan juga.
### Array Rata Kiri Eksplisit
Intinya array dimulai dari NMin dan "yang kepake" itu terdefinisi (Neff atau N Effektif). ![[Screenshot 2025-07-11 at 23.07.28.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 3. Nah disini berarti Neff nya = NMin + 3. Meskipun sebenernya ukuran arraynya masih sampe NMax, tapi yang boleh diakses cuma sampe Neff.

- Tipe 1
	![[Screenshot 2025-07-11 at 23.09.27.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 3
- Tipe 2
	![[Screenshot 2025-07-11 at 23.10.15.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 3
Bedanya cuma Neffnya yang satu ga masuk ke tipe TabInt dan yang satu lagi masuk.

### Skema Pemrosesan Sekuensial
bisa pake traversal
![[Screenshot 2025-07-11 at 23.13.37.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 3

#### Tulis Baca Array
Buat nulis, baca, dll itu gampang lah.

#### Pencarian Nilai Max
Buat nyari nilai max tuh intinya
- Asumsiin nilai max itu array indeks pertama
- terus di loop, kalo nilai max < indeks saat itu maka max nya jadi array indeks itu
![[Screenshot 2025-07-11 at 23.18.42.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 3 ![[Screenshot 2025-07-11 at 23.19.33.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 3


#### Searching
Searching = Mencari suatu hal. Maksudnya disini adalah misalkan kita mau nyari kayak di array ini, nilai 10 ada di indeks keberapa, nah itu disebut searching.
Ada beberapa versi
- **Tanpa Boolean** yang intinya
	- Ngeloop (while indeks < Neff dan Array\[indeks] != yang_dicari)
	- dia kan bakal ngeloop sampe antara indeksnya = Neff atau ga udah ketemu
	- terus dicek apakah array indeks tersebut = yang_dicari apa ga
	- kalo ngga ya direturn sesuatu yang jadi tanda gitu (bisa misalkan -1 atau apa gitu), kalo iya ya yaudah return si indeksnya
	![[Screenshot 2025-07-11 at 23.25.14.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
- **Dengan Boolean** yang intinya
	- Di declare dulu sebuah variable berbentuk boolean dan di inisialisasi dengan false (misalkan found)
	- terus loop (while indeks < Neff dan not(found))
	- di dalam loop, dicek apakah array\[indeks] tersebut sama dengan yang dicari ga
	- kalo iya maka ubah found jadi true
	- kalo ngga maka indeks + 1
	- nah kan berarti loop berhenti bisa karena 2 hal, antara indeks = Neff atau ga ya karena found = true, maka perlu dicek juga
	- kalo found = true maka return indeks nya
	- kalo found = false ya kayak yang sebelumnya lah intinya
	![[Screenshot 2025-07-11 at 23.28.20.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
- **Search pada Tabel Terurut** yang intinya
	Tabel terurut tuh misalkan [1,2,3,7,9,10,40,100]
	- Dia kayak yang tanpa boolean, tapi array\[indeks] < target
	- Contoh liat di PPT aja di [DRIVE ACADSNYA ACATRIX](https://drive.google.com/drive/u/1/folders/1TpurlRX6myMkJZpm3nAaVV0MS7ZKNJac)
- **Search dengan Sentinel** yang intinya
	Ini menarik sih, jadi kayak misal ada \[1,2,3,47,8,100] dan mau nyari 100 tuh indeks ke berapa, maka kan kita tau ya kalo ini Neff itu 6, nah dia tuh bakal naro 100 juga di setelah indeks paling akhir \[1,2,3,47,8,100,100]. Nah misalkan nanti pas disearch dia ketemunya di indeks paling akhir + 1 (yang kita tambahin tadi) berarti ya 100 gaada di array itu, tapi kalo ketemunya di <= indeks paling akhir, maka array ada disitu dan di indeks tersebut gitu.
	Contoh liat di PPT aja di [DRIVE ACADSNYA ACATRIX](https://drive.google.com/drive/u/1/folders/1TpurlRX6myMkJZpm3nAaVV0MS7ZKNJac)


#### Sorting
INI MENARIK BAT JUJUR
Sorting = Ngurutin, intinya ada sebuah data yang nilainya ga berurutan (misal dari \[1,50,3,4,90]) dan lu disuruh buat ngurutin (jadi \[1,3,4,50,90]).

Ada beberapa versi (note untuk tiap versi itu mau ascending atau descending sesuaiin bisa2 aja tinggal disesuaiin notalnya (sekalian latihan buat yang baca hehe))
- **Counting Sort** yang intinya
	- Kita perlu tau dulu dia nilai min dan max di arraynya berapa (bukan indeksnya ya tapi nilainya)
	- Kita buat dulu sebuah array yang indeksnya dari nilai min sampai nilai max array yang mau kita sort (anggap kita panggil ini array sebagai count) dan diinisialisasi tiap isinya dengan 0.
	- Terus loop, dia bakal ngecek array yang mau kita sort, misal pas dicek indeks pertama itu nilainya 50, maka pada count\[50] itu nilainya bakal + 1.
	- Kalo udah loopnya maka bakal ditimpalah array yang tadi jadi array based on count tadi dalam bentuk udah ke sort
	![[Screenshot 2025-07-11 at 23.49.05.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
- **Selection Sort** yang intinya
	Misalkan mau sort max-min, maka yang dilakukan adalah
	- Cari nilai max di array tersebut
	- tuker isinya dengan indeks pertama
	- cari nilai max di array tersebut (tapi mulai dari indeks kedua)
	- tuker isinya dengan indeks kedua
	- dst
	![[Screenshot 2025-07-11 at 23.52.54.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
	
- **Insertion Sort** yang intinya
	- Proses dilakuin sebanyak N-1 (disebut pass)
	- Setiap pass tuh ada 2 bagian (yang udah terurut yaitu \[1..pass-1] dan yang belum \[pass..N])
	- Ambil elemen TPass dan disisipin ke T\[1..pass-1] dengan tetep jaga urutan dengan **geser** elemeen sampe tempatnya cocok
	![[Screenshot 2025-07-11 at 23.56.34.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
	![[Screenshot 2025-07-11 at 23.56.47.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
- **Bubble Sort (the legend)** yang intinya
	Anggep kayak gelembung yang ngapung (asumsi disini mau sort dari min-max)
	- Misalkan di pass 1 nih, dia bakal ngecek dari akhir sampe indeks pertama DAN bakal compare tiap 2 indeks apakah indeks_saat_itu > indeks_saat_itu - 1, kalo iya mereka bakal tukeran. Dan indeks_saat_itu nya bakal --, gitu terus sampe indeks_saat_itu = indeks pertama
	- Nah lanjut pass 2 kayak gitu juga sampe pass = N-1
	![[Screenshot 2025-07-12 at 00.02.48.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
	![[Screenshot 2025-07-12 at 00.02.59.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
	Ya you get the point lah.
	![[Screenshot 2025-07-12 at 00.03.55.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
	![[Screenshot 2025-07-12 at 00.04.05.png]]Gambar credit to PPT IF1210/Skema Standar Bag. 4
	Pake yang optimum aja (kecuali kepepet pas ujian ingetnya yang asli yauds mo gimans)

Implementasi di C nya basically kalo bentuknya tipe bentukan ya kayak di bagian sebelum2nya aja kok.
Paling basic-basicnya contoh
```
int T[N]; //N = ukuran array
T[i] = 1; //i = lagi ngakses indeks ke brp

```