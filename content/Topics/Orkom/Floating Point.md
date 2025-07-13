# Floating Point 

## Representasi Dasar 
Selayaknya integer pada [[Representasi Integer dan String#Representasi Integer]], sebuah bilangan desimal juga dapat direpresentasikan secara biner. 

![[Pasted image 20250713123136.png]]

- Bits dari titik ke kanan merepresentasikan pecahan dengan 2 pangkat bilangan negatif. 
![[Pasted image 20250713123233.png]]
## IEEE Floating Point Format
Bentuk dasar *floating* point adalah **(–1)^s M 2^E**.

• **s (sign bit)**: Bit tanda yang menentukan apakah bilangan tersebut positif atau negatif.
• **M (Significand)**: Nilai pecahan, biasanya dalam rentang [1.0, 2.0).
• **E (Exponent)**: Bobot nilai berdasarkan pangkat dua.

## Encoding 
• Bit paling signifikan (MSB) adalah bit tanda `s`.
• Bidang `exp` mengkodekan `E` (nilai `exp` tidak sama dengan `E`).
• Bidang `frac` mengkodekan `M` (nilai `frac` tidak sama dengan `M`).
![[Pasted image 20250713122253.png]]

## Opsi Presisi
- Single Precision: 32 bits .
![[Pasted image 20250713122333.png]]
- Double Precision: 64 bits.
![[Pasted image 20250713122344.png]]
- Extended Precision: 80 bits.
![[Pasted image 20250713122357.png]]


## Normalized vs Denormalized 
![[Pasted image 20250713122527.png]]
- **"Normalized"**: Terjadi ketika `exp` bukan `000…0` dan bukan `111…1`
	- Eksponen `E` dihitung sebagai `Exp – Bias`, di mana `Bias = 2^(k-1) - 1` (k adalah jumlah bit eksponen). Untuk _single precision_, `Bias` adalah 127.
	- Signifikand `M` memiliki `1` implisit di depan (`1.xxx…x` biner), sehingga tidak perlu disimpan dan "gratis".
- **Denormalized**: Terjadi ketika `exp = 000…0`.
	- Nilai eksponen `E` adalah `–Bias + 1`.
	- Signifikand `M` memiliki `0` implisit di depan (`0.xxx…x` biner).
	- Mencakup **nol** (yang unik: +0 dan -0). Nilai-nilai ini adalah yang paling dekat dengan nol dan berjarak sama.
- Special Values: Terjadi ketika `exp = 111…1`.
	- Jika `frac = 000…0`, itu mewakili **tak terhingga** (`∞`), baik positif maupun negatif. Ini digunakan untuk operasi yang menghasilkan _overflow_ (misalnya, `1.0/0.0`).
	- Jika `frac ≠ 000…0`, itu mewakili **Not-a-Number (NaN)**. Ini digunakan ketika nilai numerik tidak dapat ditentukan (misalnya, `sqrt(-1)`, `∞ - ∞`).

## Type-Casting
- `double/float` ke `int`: Akan memotong bagian pecahan (mirip dengan pembulatan ke arah nol). Tidak terdefinisi jika di luar jangkauan atau NaN (umumnya akan diatur ke TMin).
- `int` ke `double`:  Konversi yang tepat, selama _int_ memiliki ukuran kata <= 53 bit.