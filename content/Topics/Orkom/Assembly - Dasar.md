# Assembly Programmer's View 
Berikut merupakan diagram hubungan antara CPU dengan Memory. Instruksi dalam memori menggunakan bahasa level mesin. Namun, agar dapat dibaca manusia, maka digunakan bahasa Assembly. 

![[Pasted image 20250713123836.png]]
- Program Counter (PC): Alamat instruksi berikutnya, disebut "EIP". 
- Register File: Digunakan secara intensif untuk data program.
- Condition Codes: Menyimpan informasi status dari operasi matematika terbaru untuk percabangan kondisional.
- MemoriL Sebuah array untuk mengakses per byte kode, data pengguna, dan stack. 
	- *note: Penjelasan di atas tidak akan masuk akal jika tidak dibaca sampai bawah :D.*

# C to Object Process
Program C diterjemahkan menjadi file objek yang dapat dieksekusi melalui proses yang melibatkan compiler, assembler, dan linker.
- **Compiler** (misalnya, `gcc -S`): Menghasilkan **kode assembly** (file `.s`) dari kode C (file `.c`).
- **Assembler**: Menerjemahkan kode assembly menjadi **kode objek** (file `.o`), yang merupakan encoding biner instruksi.
- [[**Linker**]]: Menyelesaikan referensi antar file objek yang berbeda dan menggabungkannya dengan pustaka _runtime_ statis (seperti `malloc`, `printf`) untuk membentuk program yang dapat dieksekusi sepenuhnya. Beberapa pustaka dapat di-_link_ secara dinamis saat _runtime_.

![[Pasted image 20250713124403.png]]
# Assembly Language Structure 
Contoh IA32 Assembly Code generation dari C code. 
![[Pasted image 20250713124500.png]]
*Wow, tentunya sangat tidak masuk akal!, gapapa, bear with me for a second.*

## Karakteristik Assembly 
- **Tipe Data**: Assembly menangani data integer berukuran 1, 2, atau 4 byte, dan data _floating-point_ berukuran 4, 8, atau 10 byte. **Tidak mendukung tipe agregat seperti array atau struktur secara langsung**; ini diperlakukan sebagai byte yang dialokasikan secara berurutan dalam memori.
- **Operasi**: Assembly melakukan fungsi aritmatika pada data register atau memori, mentransfer data antara memori dan register (load/store), dan mengontrol aliran program melalui jump tak bersyarat dan percabangan kondisional.
- Disassembly Tools: Alat seperti `objdump -d` atau `gdb` dapat membongkar kode objek, menganalisis pola bit untuk merekonstruksi perkiraan kode assembly. Ini berguna untuk memeriksa kode yang dapat dieksekusi.

## Registers dan Move 
### Registers
**Register Integer (IA32)**: Prosesor IA32 memiliki 8 register integer (misalnya, `%eax`, `%ebx`, `%ecx`, `%edx`, `%esi`, `%edi`, `%esp`, `%ebp`), masing-masing sepanjang 32 bit. Beberapa register memiliki penggunaan tradisional, seperti `%eax` untuk akumulasi dan nilai pengembalian, `%ecx` sebagai penghitung, dan `%esp`/`%ebp` untuk manajemen stack.
![[Pasted image 20250713124757.png]]

### Move
Seperti yang dijelaskan pada [[Assembly - Dasar#Karakteristik Assembly]], cara kerja assembly adalah memindahkan data dari satu register (atau memori) ke register (atau memori) yang lain. Pada IA 32, digunakan operasi:
`movl Source, Dest`. Terdapat juga beberapa *operand* yang dapat dipindahkan, yaitu: 
- Immediate: Constant integer data
	- Example: $0x400, $-533
- Register: One of 8 integer registers
	- Example: %eax, %edx
- Memory: Address given by a register 
	- Example: (%eax)

Terdapat juga batasan dalam operasi movl, yaitu: 
![[Pasted image 20250713125213.png]]
Artinya, kita tidak dapat memindahkan suatu memori ke memori lain dalam satu instruksi `mov`. 

### Assembly Example - Simple Swap 
Misalkan terdapat sebuah kode berikut. 
`void swap(int *xp, int *yp)
{
	`int t0 = *xp`;
	`int t1 = *yp`; 
	`*xp = t1;`
	`*yp = t0;`
}
`
Salah satu Generated IA 32 Assembly adalah sebagai berikut. 
![[Pasted image 20250713125540.png]]

Berikut visualisasi di dalam stack dan memory. 
![[Pasted image 20250713125716.png]]
Pada dua instruksi pertama, kita memindahkan nilai variabel xp ke %edx dan yp ke %ecx. 

![[Pasted image 20250713125802.png]]
Dua instruksi selanjutnya, nilai pada address %edx, yaitu 0x124 yang berisi integer 123, dipindahkan ke %ebx dan nilai pada address %ecx, yaitu 0x120 yang berisi integer 456 dipindahkan ke %eax.   

![[Pasted image 20250713125941.png]]

Dua instruksi terakhir, nilai pada %ebx dipindahkan ke address dari %edx (0x124) sehingga nilai awalnya (yaitu 123) ter-*overwrite* menjadi. Begitu juga terjadi pada %eax dan address dari %ecx. 

