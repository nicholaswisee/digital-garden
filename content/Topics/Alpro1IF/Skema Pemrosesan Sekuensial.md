Definisi = Pemrosesan satu per satu

Type elemen yang akan diproses ada 2 : Dasar dan bentuan

**Keywords**
- Elemen pertama = First_Elmt
- Elemen yang lagi diproses atau siap diproses = Current_Elmt
- Elemen yang akan diakses setelah Current_Elmt = Next_Elmt
- Tanda akhir proses atau End Of Process = EOP
Anggaplah EOP tuh kayak artinya prosesnya dah kelar, nah buat nentuin apakah dia udah kelar apa belom tuh ada 2
- dengan **MARK** = Misalkan kalo lu lagi baca buku nih, terus di bagian belakangnya pas ceritanya udah abis ada halaman tulisannya THE END, nah yaudah **MARK** tuh kayak gitu. Kayak halaman itu tuh nandain kalo prosesnya udah selesai atau ceritanya udah abis, tapi si halaman itu ga masuk ke ceritanya
- tanpa **MARK** = Misalkan lu lagi baca buku nih, terus di awal bukunya tuh dikasih tau kayak "eh ceritanya kelar pas milea nikah ya", terus pas lu lagi baca2 bukunya lu baca bagian milea nikah, itu berarti bahwa ceritanya udah abis. Ya intinya kayak gitu, kayak milea nikah tetep part of the story atau proses, tapi kita udah tau duluan kalo prosesnya berakhir setelah milea nikah atau setelah bagian itu.

Contoh:
- **Dengan MARK tanpa penanganan kosong**
	![[Screenshot 2025-07-11 at 02.16.59.png]]
	Anggaplah kamu punya array, nah array itu punya sedemikian buah isi dengan tiap isinya berbentuk integer. Nah, disini kita anggap **MARK** nya adalah 999. Misalkan kita akses array ke - 1 dan pas dicek isinya bukan 999, maka dia bakal nge output isi array ke - 1 itu. Dan dia bakal ngecek array ke - 2 dan kalo dicek bukan 999 bakal nge output. Nah begitu terus sampe pas array ke sekian itu isinya = 999 baru dia berhenti nge loop dan gabakal ngeoutput array ke sekian itu juga.

- **Dengan MARK dengan penanganan kosong**
	![[Screenshot 2025-07-11 at 02.29.05.png]]
	Notice that dia ngecek sendiri dulu apakah array ke idx awalnya = MARK, kalo iya maka output itu. Kalo ngga maka dia bakal ngeoutput array ke idx awalnya dan dia bakal lanjut ke idx selanjutnya dan bakal loop sampe array ke idx nya = 999. Nah dia pake loop yang gaperlu ngecek pas awal lagi karena kalo udah masuk loop dia udah pasti array ke idxnya bukan **MARK** jadi langsung loop aja.

- **Tanpa MARK tanpa penanganan kosong (1)**
	![[Screenshot 2025-07-11 at 17.35.15.png]]
	
	Nah disini keliatan kan kalo dia tuh gaada tanda di dalam isi arraynya kalo udah EOP tuh di mana. Tapi kita bisa tau kalo dia udah EOP dengan apa, dengan indeksnya. jadi misalkan udah array ke 4 berarti yaudah itu yang terakhir.

- **Tanpa MARK tanpa penanganan kosong (2)**
	![[Screenshot 2025-07-11 at 17.39.52.png]]
	Ya ini basically sama aja kayak tadi sih
Intinya tanpa mark ngeproses minimal sekali, mark bisa ga proses sama sekali (kalo kasus kosong).

Tips and Tricks : Bakal lebih enak kalo paham konsepnya aja, Mark atau tanpa Mark, dibanding hapalin kayak "oh kalo tanpa mark pake repeat until bla2" karena ya di case yang dikasih di atas pun repeat until bisa dua2nya kan. Terus buat penanganan kasus kosong tuh dia intinya kayak di awal ngecek dulu apakah data awalnya udah EOP apa belom, kalo iya dia bakal ngeprosesnya beda dengan kayak normalnya (and **kasus kosong** **cuma ada** di **MARK** aja)


#Latihan_Soal_SkemaPemrosesan