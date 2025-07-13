Kita sudah membahas *basics of Assembly* pada [[Assembly - Dasar]] dengan contoh swap. Sekarang, kita akan meng-*explore* lebih banyak soal *conditionals* dan *loops*. Untuk memahami dengan lebih baik, lakukanlah *learning by doing* dengan menggunakan soal-soal picoCTF *reverse engineering*. Saya merekomendasi soal picoCTF 2023 "Reverse", good luck!. 

# Complete Memory Addressing Modes 
Misalnya kita mendapatkan nilai dari register sebagai berikut. 
`%edx -> 0xf000`
`%ecx -> 0x0100`

Carilah hasil dari ekspresi berikut.
`0x8(%edx)`
`(%edx, %ecx)`
`(%edx, %ecx, 4)`
`0x80(, %edx, 2)`

Bagaimana cara mengerjakannya? Berikut beberapa formula pengerjaannya. 

- Bentuk-bentuk di atas sesuai dengan bentuk memory addressing yang paling umum: 
![[Pasted image 20250713131146.png]]
	- **D (Displacement)**: Konstanta _displacement_ (offset) berukuran 1, 2, atau 4 _byte_.
	- **Rb (Base Register)**: Register dasar, bisa salah satu dari 8 register _integer_.
	- **Ri (Index Register)**: Register indeks, bisa register apa pun kecuali `%esp` (dan jarang `%ebp`).
	- **S (Scale)**: Faktor skala, bisa 1, 2, 4, atau 8. Ini digunakan untuk mengakses elemen dalam _array_ di mana setiap elemen memiliki ukuran tertentu (misalnya, _integer_ 4 _byte_, _double_ 8 _byte_).
		- **Kasus Khusus**: Terdapat juga kasus khusus seperti `(Rb,Ri)`, `D(Rb,Ri)`, dan `(Rb,Ri,S)`.

Nah, berarti, solusi dari ekspresi-ekspresi di atas adalah sebagai berikut. 
`0x8(%edx) -> 0x8 + 0xf000 -> 0xf0008` 
`(%edx, %ecx) -> 0xf000 + 0x0100 -> 0xf100`
`(%edx, %ecx, 4) -> 0xf000 + 0x0100 * 4`
`0x80(, %edx, 2) -> 0x80 + 0xf000 * 2`
*Jikalau kalian bingung, saya juga dulu bingung, jadi coba hubungkan formula umum dengan contoh-contoh perhitungan di atas*. 

# Instruksi `lea` (Load Effective Address)
Instruksi `leal Src,Dest` menghitung alamat yang ditentukan oleh ekspresi **Src** **dan menyimpannya ke** **Dest** **tanpa melakukan akses memori**. Berbeda dengan [[Assembly - Dasar#Move]] yang akan mengakses memori hasil komputasi [[Assembly - Control#Complete Memory Addressing Modes]] lalu memindahkannya ke `Dest`. 

## `mov vs lea`
Contoh: 
sebuah array `my_array dd 100, 200, 300, 400` dengan layout memori: 
- Alamat `0x402000` berisi nilai `100`.
- Alamat `0x402004` berisi nilai `200`.
- Alamat `0x402008` berisi nilai `300`.
- Alamat `0x40200C` berisi nilai `400`.

`mov my_array, ebx`
`mov [ebx + 8], eax` -> eax akan bernilai 300
`lea [ebx+8], ecx` -> ecx akan berisi **alamat 0x402008**


# Operasi Aritmatika 
## Instruksi Dua Operan 
- addl Src,Dest`: `Dest = Dest + Src`.
- `subl Src,Dest`: `Dest = Dest - Src`.
- `imull Src,Dest`: `Dest = Dest * Src` (perhatikan urutan argumen!).
- `sall Src,Dest` (atau `shll`): `Dest = Dest << Src` (shift kiri logis).
- `sarl Src,Dest`: `Dest = Dest >> Src` (shift kanan aritmatika).
- `shrl Src,Dest`: `Dest = Dest >> Src` (shift kanan logis).
- `xorl Src,Dest`: `Dest = Dest ^ Src`.
- `andl Src,Dest`: `Dest = Dest & Src`.
- `orl Src,Dest`: `Dest = Dest | Src`.

## Instruksi Satu Operan
- `incl Dest`: `Dest = Dest + 1`.
- `decl Dest`: `Dest = Dest - 1`.
- `negl Dest`: `Dest = -Dest`.
- `notl Dest`: `Dest = ~Dest`.

### Contoh Penggunaan Operasi Aritmatika
![[Pasted image 20250713132451.png]]

# Conditional Codes 
## Register Bit Tunggal 
Prosesor memiliki register bit tunggal yang menyimpan informasi status dari operasi aritmatika terakhir
    ◦ **CF (Carry Flag)**: Set jika ada _carry_ keluar dari bit paling signifikan (untuk _overflow unsigned_).
    ◦ **ZF (Zero Flag)**: Set jika hasil operasi sama dengan 0.
    ◦ **SF (Sign Flag)**: Set jika hasil operasi kurang dari 0 (untuk _signed_).
    ◦ **OF (Overflow Flag)**: Set jika terjadi _overflow_ _two's-complement_ (untuk _signed_).


- Pengaturan Implisit: Kode kondisi ini secara implisit diatur oleh sebagian besar operasi aritmatika (misalnya, `addl`/`addq`), tetapi **tidak diatur oleh instruksi** **lea**.
- Pengaturan Eksplisit
	- `cmpl/cmpq src2, src1`: Mirip dengan menghitung `Src1 - Src2` tetapi tidak menyimpan hasilnya. Mengatur kode kondisi berdasarkan perbandingan.
	- `testl/testq src2, src1`: Mirip dengan menghitung `Src1 & Src2` tetapi tidak menyimpan hasilnya. Berguna untuk memeriksa bitmask.
## Membaca Kode Kondisi 
![[Pasted image 20250713132754.png]]
Contoh: 
![[Pasted image 20250713132852.png]]

## Jumping 
Ini adalah *core* dari *conditional codes*. Umumnya, pada assembly, apabila sebuah comparison (`cmp/test`) terpenuhi, akan dilanjutkan dengan sebuah instruksi `jmp` pada sebuah alamat. 

### Jump Instructions
Gambar di bawah mungkin terkesan membingungkan dan memang membingungkan. Secara praktis, sebenarnya kita hanya perlu menggunakan logika untuk *comparison to jump instructions*.
![[Pasted image 20250713133019.png]]
Perhatikan contoh berikut. Coba analisis bagaimana `jmp` bekerja. Namun, apabila kalian lihat di *debugger* seperti `gdb`, baris seperti .L6 dan .L7 akan menjadi offset fungsi yang memproses *conditional cases*-nya. 
![[Pasted image 20250713133129.png]]

# Loop 
Mirip dengan conditionals, *core* dari loop adalah memenuhi sebuah kondisi dan `jmp` ke sebuah proses sebelum parameter *conditional*-nya terpenuhi. Perhatikan contoh berikut. 

![[Pasted image 20250713133452.png]]
