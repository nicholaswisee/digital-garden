Yah tentunya kalian sudah tahu tentang tipe data `structure` dalam C / C++. Di bab ini dibahas mengenai bagaimana tata letak memori program bekerja untuk tipe data *structure*. 

# Structure 
Struktur adalah wilayah memori yang dialokasikan secara bersebelahan (_contiguously-allocated region_). Anggota (_members_) dalam struktur direferensikan berdasarkan nama dan dapat memiliki tipe data yang berbeda. Anggota struktur diakses menggunakan _pointer_ yang menunjuk ke _byte_ pertama struktur, dan elemen-elemen diakses dengan _offset_ dari _pointer_ tersebut. _Offset_ setiap anggota struktur ditentukan pada waktu kompilasi.

## Alignment 
Tipe data primitif yang membutuhkan `K` _byte_ harus memiliki alamat yang merupakan kelipatan `K`. Ini wajib pada beberapa mesin dan disarankan pada IA32.

- But Why? Memori diakses dalam _chunk_ 4 atau 8 _byte_ (tergantung sistem), sehingga tidak efisien jika data melintasi batas _word_ atau halaman memori virtual. _Compiler_ akan menyisipkan celah (_gaps_) dalam struktur untuk memastikan _alignment_ yang benar.

Contohnya, pada kode berikut: 
`struct S1{
	`char c;`
	`int i[2];`
	`double v;`
}

![[Pasted image 20250713141532.png]]

TL;DR: Disarankan untuk menempatkan tipe data berukuran besar terlebih dahulu dalam deklarasi struktur untuk mengoptimalkan penggunaan ruang memori dan menghindari banyak _padding_.

# Union
Memori dialokasikan berdasarkan elemen terbesar dalam *union*. Hanya satu _field_ yang dapat digunakan pada satu waktu. Contohnya: 
![[Pasted image 20250713141930.png]]
