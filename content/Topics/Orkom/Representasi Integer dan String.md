# Representasi biner dan Organisasi Memori 
## Nilai Byte
Nilai byte terdiri dari 8 bit. Rentangnya adalah `00000000` hingga `11111111` (desimal 255) dalam biner, atau 00 hingga FF dalam heksadesimal. Contoh nilai heksadesimal adalah 0xdeadbeef .

## Ukuran Kata ("Word")
"Word Size" adalah ukuran nominal data integer dan alamat. 
- Umumnya, mesin saat ini menggunakan kata **32-bit** (4-byte), yang membatasi alamat hingga 4GB. 
- Sistem high-end menggunakan **kata 64-bit (8 byte)**, menawarkan ruang alamat potensial sekitar 1.8 x 10^19 byte. Mesin x86-64 mendukung alamat 48-bit (256 Terabytes).
- **Alamat menentukan lokasi byte**, yang berarti alamat sebuah kata merujuk pada byte pertamanya. Kata-kata berurutan memiliki perbedaan alamat sebesar 4 byte (untuk 32-bit) atau 8 byte (untuk 64-bit)
## Endianness
Terdapat dua cara sebuah memori mengurutkan byte, yaitu **Big Endian & Little Endian**.
- **Big Endian**: Byte paling tidak signifikan memiliki **alamat tertinggi** (misalnya, Sun, PPC Mac, Internet).
- **Little Endian**: Byte paling tidak signifikan memiliki **alamat terendah** (misalnya, arsitektur x86 seperti IA32 dan x86-64).

![[Pasted image 20250713115946.png]]

## Representasi Integer 
Terdapat dua tipe data yang merepresentasikan integer, *signed (Two's Complement)* dan *unsigned*. 

### Unsigned Integers
- Nilai minimum `UMin` adalah `0`. 
- Nilai maksikum `UMax` adalah `2^w - 1` untuk sistem w-bit. 
### Signed Integers (Two's Complement)
- Bit paling signifikan (MSB) berfungsi sebagai bit tanda: 0 untuk non-negatif, 1 untuk negatif. 
- `TMin` (Nilai signed minimum) adalah `-2^(w-1)`
- `TMax` (nilai signed maksimum) adalah `2^(w-1) - 1`
- `|TMin| = TMax + 1`
- **Konversi antara nilai bertanda dan tak bertanda** melibatkan reinterpretasi pola bit yang sama sehingga ada sebuah *case* yang menyebabkan nilai konversi signed menjadi bilangan unsigned yang sangat besar. 
- Contoh
	`int signed_num = -10;
	`unsigned int unsigned_num = static_cast<unsigned int>(signed_num);`
	`//unsigned_num will be 4294967286 (for a 32-bit int) due to the wrap-around.`	

## Representasi String 
Setiap karakter dikodekan menggunakan format ASCII. Misalnya, karakter "0" memiliki kode `0x30`, dan digit i memiliki kode `0x30 + i`.
- Pada C, String diakhiri dengan null, hal ini disebut sebagai null-termination.
 ![[Pasted image 20250713120942.png]]

## Aljabar Boolean dan Operasi Tingkat Bit 

### Bit Manipulation
- **Operasi**: AND (`&`), OR (`|`), NOT (`~`), dan Exclusive-OR (`^`) diterapkan bitwise ke tipe data "integral" apa pun (misalnya, `long`, `int`, `short`, `char`, `unsigned`.
![[Pasted image 20250713121111.png]]
- Operasi ini berbeda dari operator logis C (`&&`, `||`, `!`), yang memperlakukan 0 sebagai "False" dan nilai non-nol sebagai "True", selalu mengembalikan 0 atau 1, dan menggunakan _early termination_ (penghentian dini).

### Shift Operation 
- **Left Shift (x << y)**: Menggeser vektor bit `x` ke kiri sebanyak `y` posisi, membuang bit di kiri dan mengisi dengan 0 di kanan. Operasi ini setara dengan `x * 2^y` untuk unsigned dan signed.
- **Right Shift (x >> y)**: Menggeser vektor bit `x` ke kanan sebanyak `y` posisi, membuang bit di kanan.
	- Logical Shift: Mengisi dengan 0 di kiri.
	- Arithmetic Shift: Mereplikasi *Most Significant Bit * di kiri.
		![[Pasted image 20250713121453.png]]
