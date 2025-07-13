# Definisi dan Fungsi
![[Pasted image 20250713135939.png]]
_Linking_ adalah tahap dalam kompilasi program di mana bagian-bagian kode dan data yang terpisah digabungkan untuk membentuk satu _file_ yang dapat dieksekusi. Contohnya, saat mengkompilasi `main.c` dan `swap.c` dengan `gcc -o p main.c swap.c`, _compiler driver_ akan menggunakan _linker_ (biasanya `ld`) untuk menggabungkan _object file_ (`main.o`, `swap.o`) menjadi _executable object file_ (`p`).

Ada dua alasan mengapa linking dibutuhkan. 
- **Modularitas (Modularity)**: Memungkinkan program ditulis sebagai kumpulan _file_ sumber yang lebih kecil, daripada satu _file_ besar. Ini juga memungkinkan pembuatan _library_ fungsi-fungsi umum (misalnya, _math library_ atau _standard C library_).
- **Efisiensi (Efficiency)**:
	- **Waktu**: Dengan kompilasi terpisah, hanya _file_ sumber yang diubah yang perlu dikompilasi ulang, lalu di-_relink_, tanpa perlu mengkompilasi ulang _file_ lain.
	- **Ruang**: Fungsi-fungsi umum dapat dikelompokkan dalam satu _file library_, tetapi _file executable_ atau _memory image_ yang sedang berjalan hanya akan berisi kode untuk fungsi-fungsi yang benar-benar digunakan.

# Proses Linking 
1. **Resolusi Simbol**
	1. Program mendefinisikan dan mereferensikan simbol (variabel dan fungsi). Contoh: `void swap() {…}` mendefinisikan simbol `swap`, sementara `swap();` mereferensikannya.
	2. Definisi simbol disimpan dalam _symbol table_ oleh _compiler_.
	3. Selama langkah ini, _linker_ mengaitkan setiap referensi simbol dengan satu definisi simbol yang tepat.
2. Relokasi 
	1. Menggabungkan bagian kode (`.text`) dan data (`.data`, `.rodata`, `.bss`) yang terpisah dari _object file_ menjadi satu bagian di _executable_.
	2. Merelokasi simbol dari lokasi relatifnya dalam _object file_ ke lokasi memori absolut finalnya di _executable_.
	3. Memperbarui semua referensi ke simbol-simbol ini untuk mencerminkan posisi baru mereka.

# Jenis Object File 
- **Relocatable object file** **(****.o file): Berisi kode dan data dalam format yang dapat digabungkan dengan _object file relocatable_ lainnya untuk membentuk _executable object file_. Setiap `.o` _file_ dihasilkan dari satu _file_ sumber `.c`.
- **Executable Object File** (`a.out` file): Berisi kode dan data dalam format yang dapat langsung disalin ke memori dan dieksekusi.
- **Shared Object File** (`.so` file): Jenis _object file relocatable_ khusus yang dapat dimuat ke memori dan di-_link_ secara dinamis, baik saat _load time_ maupun _run-time_. Ini dikenal sebagai _Dynamic Link Libraries_ (DLLs) di Windows.

# Executable and Linkable Format (ELF)
ELF adalah format biner standar untuk _object file_ di Unix System V, BSD, dan Linux. Ini adalah format gabungan untuk _relocatable object files_ (`.o`), _executable object files_ (`a.out`), dan _shared object files_ (`.so`).

![[Pasted image 20250713135957.png]]
Struktur ELF: 
_Elf header_, _Segment header table_, bagian `.text` (kode), `.rodata` (data hanya-baca), `.data` (variabel global terinisialisasi), `.bss` (variabel global tidak terinisialisasi), `.symtab` (_symbol table_), `.rel.text` (_relocation info_ untuk `.text`), `.rel.data` (_relocation info_ untuk `.data`), `.debug` (info untuk _debugging_), dan _Section header table_.

# Example
![[Pasted image 20250713140114.png]]
![[Pasted image 20250713140120.png]]

# Some Rules 

## Rules
### Multiple strong symbols are not allowed
Contoh
// file1.c
`int global_data = 10; // Simbol 'global_data' adalah kuat`
`void my_function() { /* ... */ } // Simbol 'my_function' adalah kuat
// file2.c`
`int global_data = 20; // Simbol 'global_data' juga kuat, berkonflik!
void my_function() { /* ... */ } // Simbol 'my_function' juga kuat, berkonflik!`

### Given a strong symbol and multiple weak symbols, choose the strong symbol
Contoh
// file1.c
`int value = 100; // Simbol 'value' adalah kuat (dinisialisasi)`
// file2.c
`int value; `// Simbol 'value' adalah lemah (tidak diinisialisasi) 
// file3.c
`// Kita bisa menggunakan __attribute__((weak)) untuk fungsi agar lebih eksplisit`
`__attribute__((weak)) void print_message() {
	`printf("Message from weak function in file3.c\n");
}``
// file4.c
`void print_message()` { // Simbol 'print_message' ini kuat
`printf("Message from STRONG function in file4.c\n");`
}
// main.c
`extern int value;
`extern void print_message();
`int main() {`
	`printf("Value: %d\n", value);`
	`print_message();`
	`return 0;`
}`
**Output:**
**Value: 100 Message from STRONG function in file4.c**

### If there are multiple weak symbols, pick an arbitrary one

// file_weak1.c

`__attribute__((weak)) void choose_me() {
	`printf("I am the weak function from file_weak1.c\n");
`}

// file_weak2.c
`__attribute__((weak)) void choose_me() {
	`printf("I am the weak function from file_weak2.c\n");
`}
// main.c
`extern void choose_me(); // Deklarasi eksternal
`int main() {
	`choose_me(); // Memanggil fungsi lemah
	`return 0;
`}

Untuk my_program_v1 (link file_weak1.o lalu file_weak2.o),
mungkin mendapatkan:
**I am the weak function from file_weak1.c**
Untuk my_program_v2 (link file_weak2.o lalu file_weak1.o), mungkin mendapatkan:
**I am the weak function from file_weak2.c**
