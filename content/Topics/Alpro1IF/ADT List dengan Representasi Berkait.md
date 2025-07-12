## Perkenalan Singkat
- Definisi: Struktur berkait itu isinya node yang saling terkait. Tiap node ada dua bagian: **info** (nilainya) dan **next** (penunjuk ke node lain). Ini bikin kita bisa nyimpen elemen tanpa harus di lokasi memori yang bersebelahan. Intinya kayak tiap node tuh punya data VALUE dia berapa, sama nilai selanjutnya apa nih nah dia megang alamatnya tuh.![[Screenshot 2025-07-12 at 19.51.34.png]]![[Screenshot 2025-07-12 at 19.54.15.png]]
- **Ciri2**:
    - List diacu lewat alamat elemen pertamanya (first)
    - Elemen terakhir tuh kalo next-nya nunjuk ke NIL
    - List kosong kalo first = NIL
![[Screenshot 2025-07-12 at 19.55.15.png]]
Ini penting banget si, jadi kan sebenernya kita tuh cuma punya sebuah node yang isinya value dan alamat next kan. Berarti misalkan ada sebuah l: list. ini tuh maksudnya kayak sebuah alamat menuju ke indeks atau node pertama gitu. NAH makanya penting banget harus buat sebuah variabel baru berbentuk address yang gunanya kita "copy" dulu alamat node pertama, terus kan variabel itu jadi node pertama, yaudah nanti kalo mau menelusuri atau intinya kalo mau akses node2 lain pake si var ini (misal p <- l, maka p <- p^.next itu artinya p jadi node kedua gitu). INI JADI PENTING kenapa, karena kalo yang kita otak atik si l nya itu nanti kita jadi gatau node pertamanya dimana, karena kesannya "digeser-geser" gitu (ini cara gw mahamin konsep node sih).
- **Skema Pemrosesan**:
    - **Traversal**: Kunjungin semua elemen dari awal sampe akhir. Contoh: ![[Screenshot 2025-07-12 at 20.00.06.png]]
    - **Pencarian Sekuensial**: Cari elemen satu per satu sampe ketemu atau sampe akhir list. Contoh: ![[Screenshot 2025-07-12 at 20.00.18.png]]
    Lebih lengkapnya baca slide aja asli ada di [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWzumlZLdeoacFVHPXoEs))
- Note = sebenernya ribet karena kalo mau akses suatu indeks tuh harus nelusurin dari awal dulu.
- Operasi:
    - isEmpty: Ngecek list kosong atau ngga.
    - length: Ngitung jumlah elemen.
    - indexOf: Nyari indeks dari sebuah elemen.
    - getElmt/setElmt: Buat akses dan ubah nilai elemen di indeks tertentu.
    - insertFirst: Nambahin elemen di awal.
    - insertAt: Nambahin elemen di indeks tertentu.
    - insertLast: Nambahin elemen di akhir.
    - deleteFirst: Ngapus elemen pertama.
    - deleteAt: Ngapus elemen di indeks tertentu.
    - deleteLast: Ngapus elemen terakhir.
    - Dll
	Contoh C nya
	```
	void setElmt(List *l, int idx, ElType val){
		Address p;
		p = *l;
		for (int i = 0; i < idx; i++)
		{
			p = NEXT(p);
		}
		INFO(p) = val;
	}
	```

## Representasi Fisik, Implisit vs Eksplisit
### Representasi Fisik
Ada 2 cara buat representasiin list secara fisik:
1. **Struktur Berkait dengan Pointer**: Ini yang udah biasa kita bahas, tiap Node dialokasiin satu per satu.
2. **Struktur Berkait dengan Array**: Biar lebih efisien, kita bisa alokasiin beberapa Node sekaligus dalam bentuk array of Node. Di sini, next dari Node itu bukan alamat memori, tapi indeks array. Kita juga butuh FirstAvail buat nyatet Node pertama yang kosong.

### Representasi Implisit vs. Eksplisit
- **Implisit**: Menunjuk ke list sama dengan menunjuk ke elemen pertamanya. Ini cocok sama definisi rekursif list.![[Screenshot 2025-07-12 at 20.53.24.png]]
- **Eksplisit**: Elemen pertama list (first) jadi bagian dari struktur data list itu sendiri (type List: < first: Address >). Representasi ini berguna banget buat implementasi Queue.![[Screenshot 2025-07-12 at 20.53.40.png]]


## Stack dan Queue dengan Representasi Berkait

### Stack
- Konsep: Stack itu LIFO (Last In First Out), jadi elemen yang terakhir masuk, itu yang pertama keluar.
- Implementasi: Mirip kayak list linier biasa, di mana "First" pada list itu sama dengan "Top" pada stack.
- Operasi Dasar:
    - CreateStack = CreateList.
    - push = insertFirst.
    - pop = deleteFirst.  
- ADT: Deklarasi ADT stack pake representasi list ini mirip banget, cuma beda penamaan aja buat addressTop sebagai penunjuk elemen puncak
- Contoh:![[Screenshot 2025-07-12 at 21.02.43.png]] Lengkapnya cek aja [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs))
### Queue
- Konsep: Queue itu FIFO (First In First Out), elemen yang pertama masuk, itu juga yang pertama keluar. Punya HEAD (elemen depan) dan TAIL (elemen belakang).
- Implementasi: Pake list linier yang nyatet First dan Last. First jadi Head, Last jadi Tail.
- Operasi Dasar:
    - enqueue (nambahin elemen) itu = insertLast.
    - dequeue (ngapus elemen) itu = deleteFirst.
- ADT: Deklarasi ADT queue juga mirip, tapi nyimpen dua alamat: addrHead buat ngapus dan addrTail buat nambah.
- Contoh: 
![[Screenshot 2025-07-12 at 21.03.39.png]]Lengkapnya cek aja [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs))