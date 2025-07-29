# Logika
Logika adalah ilmu yang membantu kita dalam berpikir dan mencapai kesimpulan dari berbagai pernyataan (*reasoning*). Logika digunakan sebagai alat bantu untuk memahami dan menjawab sebuah argumen. 

## 1. Proposisi
Logika didasarkan pada hubungan antara kalimat atau pernyataan. Proposisi adalah pernyataan yang bernilai benar (*true*) atau salah (*false*), tetapi tidak keduanya. Contoh-contoh proposisi : 
- Bumi lebih besar daripada bulan (benar)
- -999 < 999 (benar)
- Sekarang tahun 1977 atau tahun 888 (salah)
- $x - y = y - x$ untuk semua  $x,y$ ∈ $R$ 
Contoh kalimat yang bukan proposisi : 
- Hari ini mau makan apa? (kalimat tanya)
- Bukan jendela itu sekarang! (kalimat perintah)
- $a + b < 81$ (kalmat terbuka)
Jadi, kesimpulannya adalah prosisi haruslah berupa kalimat berita. Pernyataan yang melibatkan variabel disebut predikat, kalimat terbuka. Contoh : 
- $x > 3$ 
	Notasi : $P(x) : x < 3$
- $∀x P(x)$
	Contoh predikat dengan *quantifier*
Proposisi dilambangkan dengan huruf kecil *p*, *q*, *r*, .... Contoh : 
- *p* : 513414 adalah bilangan ganjil.
- *q* : $7 - 3 + 4$.
- *r* : Indonesia terletak di benua Asia.
Proposisi dapat dinyatakan dalam 4 bentuk : 
1. Proposisi atomik
2. Proposisi majemuk
3. Implikasi
4. Bi-implikasi

### 1.1. Proposisi Atomik
Proposisi atomik adalah proposisi tunggal, contohnya seperti berikut : 
- Teknik Informatika ITB dibentuk tahun 2025
- $2n$ selalu genap untuk semua $n = 0, 1, 2, ...$
- Nama saya berhuruf depan R, tetapi saya tidak bisa memrogram menggunakan bahasa pemrograman R
- Ibukota Jawa Barat adalah Bandung

### 1.2. Proposisi Majemuk
Misalkan *p* dan *q* adalah proposisi atomik. Ada 4 macam proposisi majemuk : 
1. Konjungsi (*conjunction*) : *p* dan *q*
	Notasi *p* ∧ *q*
2. Disjungsi (*disjunction*) : *p* atau *q*
	Notasi *p* ∨ *q*
3. Ingkaran (*negation*) : tidak *p*
	Notasi ~*p*
4. Disjungsi eksklusif : *p* atau *q* tapi bukan keduanya
	Notasi *p* ⊕ *q* 
Nilai kebenaran dalam proposisi majemuk dapat ditentukan dengan menggunakan "tabel kebenaran". Contoh : 
- Proposisi majemuk : (*p* ∧ *q*) ∨ (~*q* ∧ *r*)
	Tabel kebenaran : 

| *p* | *q* | *r* | *p* ∧ *q* | ~*q* | ~*q* ∧ *r* | (*p* ∧ *q*) ∨ (~*q* ∧ *r*) |
| :-: | :-: | :-: | :-------: | :--: | :--------: | :------------------------: |
|  T  |  T  |  T  |     T     |  F   |     F      |             T              |
|  T  |  T  |  F  |     T     |  F   |     F      |             T              |
|  T  |  F  |  T  |     F     |  T   |     T      |             T              |
|  T  |  F  |  F  |     F     |  T   |     F      |             F              |
|  F  |  T  |  T  |     F     |  F   |     F      |             F              |
|  F  |  T  |  F  |     F     |  F   |     F      |             F              |
|  F  |  F  |  T  |     F     |  T   |     T      |             T              |
|  F  |  F  |  F  |     F     |  T   |     F      |             F              |

Proposisi majemuk akan disebut tautologi jika ia benar untuk semua kemungkinan kasus, dan akan disebut kontradiksi jika ia salah untuk semua kemungkinan kasus. Dua buah proposisi majemuk, *P*(*p*, *q*, ..) dan *Q*(*p*, *q*, ..) disebut ekivalen secara logika jika keduanya mempunyai tabel kebenaran yang identik (notasi : *P*(*p*, *q*, ..) ⟺ *Q*(*p*, *q*, ..)). 
Hukum-hukum Logika disebut juga hukum-hukum aljabar proposisi, yang dapat dijabarkan sebagai berikut : 
1. Hukum identitas
	- *p* ∨ **F** ⟺ *p*
	- *p* ∧ **T** ⟺ *p*
2. Hukum *null*/dominasi
	- *p* ∧ **F** ⟺ **F**
	- *p* ∨ **T** ⟺ **T**
3. Hukum negasi
	- *p* ∨ ~*p* ⟺ **T**
	- *p* ∧ ~*p* ⟺ **F**
4. Hukum idempoten
	- *p* ∨ *p* ⟺ *p*
	- *p* ∧ *p* ⟺ *p*
5. Hukum involusi (negasi ganda)
	- ~(~*p*) ⟺ *p*
6. Hukum penyerapan (absorbsi)
	- *p* ∨ (*p* ∧ *q*) ⟺ *p*
	- *p* ∧ (*p* ∨ *q*) ⟺ *p*
7. Hukum komutatif
	- *p* ∧ *q* ⟺ *q* ∧ *p*
	- *p* ∨ *q* ⟺ *q* ∨ *p*
8. Hukum asosiatif
	- *p* ∧ (*q* ∧ *r*) ⟺ (*p* ∧ *q*) ∧ *r*
	- *p* ∨ (*q* ∨ *r*) ⟺ (*p* ∨ *q*) ∨ *r*
9. Hukum distributif
	- *p* ∨ (*q* ∧ *r*) ⟺ (*p* ∨ *q*) ∧ (*p* ∨ *r*)
	- *p* ∧ (*q* ∨ *r*) ⟺ (*p* ∧ *q*) ∨ (*p* ∧ *r*)
10. Hukum de Morgan
	- ~(*p* ∧ *q*) ⟺ ~*p* ∨ ~*q*
	- ~(*p* ∨ *q*) ⟺ ~*p* ∧ ~*q*

### 1.3. Implikasi
Implikasi biasa disebut proposisi bersyarat yang berbentuk "jika p, maka q" (notasi : *p* → *q*). *p* disebut hipotesis, antesenden, premis, atau kondisi, sedangkan *q* disebut konklusi atau konsekuen. Contohnya : 
- Jika nilai ujian saya lebih dari 85, maka ayah saya akan membelikan saya es krim.
- Jika kecepatan mobil melebihi 80 km/jam, maka alarm akan berbunyi.
Tabel kebenaran untuk implikasi :

| *p* | *q* | *p* → *q* |
| :-: | :-: | :-------: |
|  T  |  T  |     T     |
|  T  |  F  |     F     |
|  F  |  T  |     T     |
|  F  |  F  |     T     |

Perlu diperhatikan bahwa implikasi hanya memperhatikan nilai kebenaran premis dan konsekuen, bukan hubungan sebab akibat antara keduanya. Implikasi berikut ini valid meskipun secara bahasa tidak memiliki makna : 
- Jika 5 - 2 = 3, maka hujan akan terjadi di Bandung.
- Jika n merupakan pecahan, maka kipas angin akan mati. 
Berbagai sintaks kalimat yang mengekspresikan implikasi *p* → *q* : 
- Jika p, maka q (if p, then q)
- Jika p, q (if p, q)
- p mengakibatkan q (p implies q)
- q jika p (q if p)
- p hanya jika q (p only if q)
- p syarat cukup untuk q (p is sufficient condition for q)
- q syarat perlu bagi p (q is necessary condition for q)
- q bilamana p (q whenever p)
- q mengikuti dari p (q follows from p)
### 1.4. Biimplikasi
Biimplikasi dinyatakan dalam bentuk "p jika dan hanya jika q" (notasi : *p* ↔ *q*). Tabel kebenaran untuk Biimplikasi : 

| *p* | *q* | *p* ↔ *q* |
| :-: | :-: | :-------: |
|  T  |  T  |     T     |
|  T  |  F  |     F     |
|  F  |  T  |     F     |
|  F  |  F  |     F     |

Pernyataan "p jika dan hanya jika q" dapat dibaca "jika p maka q dan jika q maka p" (*p* ↔ *q* ⟺ (*p* → *q*) ∧ (*q* → *p*)). Contoh : 
- |x| < a jika dan hanya jika –a < x < a, yang dalam hal ini a > 0
Ada beberapa cara untuk menyatakan bikondisional *p* ↔ *q* : 
- p jika dan hanya jika q.
- p adalah syarat perlu dan cukup untuk q.
- Jika p maka q, dan sebaliknya.
- p iff q
Bila dua proposisi majemuk yang ekivalen di-bikondisionalkan maka hasilnya adalah tautologi. Dua buah proposisi majemuk, *P*(*p*, *q*, ..) dan *Q*(*p*, *q*, ..) disebut ekivalen secara logika, dilambangkan dengan *P*(*p*, *q*, …) ⟺ *Q*(*p*, *q*, …) jika *P* ↔ *Q* adalah tautologi.

## 2. Argumen 
Argmen adalah suatu deret proposisi yang ditulis sebagai 

*p1*

*p2*

⋮

*pn*

—

∴ *q*

yang dalam hal ini, *p1*, *p2*, …, *pn* disebut hipotesis (atau premis), dan *q* disebut konklusi. Konklusi biasanya ditandai dengan kata “Jadi”, “Oleh karen itu”,“Dengan demikian, “, dan lain-lain. Contoh dari argumen : 
- Jika anda mahasiswa Informatika maka anda tidak sulit belajar Bahasa Java. Jika anda tidak suka begadang maka anda bukan mahasiswa Informatika. Tetapi, anda sulit belajar Bahasa Java dan anda tidak suka begadang. Jadi, anda bukan mahasiswa Informatika.
Terdapat argumen yang sahih (valid) dan palsu (invalid). Sebuah argumen dikatakan sahih jika konklusi benar bilamana semua hipotesisnya benar; sebaliknya argumen dikatakan palsu (fallacy atau invalid). Jika argumen sahih, maka kadang-kadang kita mengatakan bahwa secara logika konklusi mengikuti hipotesis atau sama dengan memperlihatkan bahwa implikasi (*p1* ∧ *p2* ∧ ...  *pn*) → *q* adalah benar (yaitu, sebuah tautologi). Argumen yang palsu menunjukkan proses penalaran yang tidak benar. Beberapa argumen yang sudah dipastikan sahih : 
1. Modus ponen
	
	*p* → *q*
	
	*p*
	
	———
	
	∴ *q*
2. Modus tollen

	*p* → *q*
	
	~*q*
	
	———
	
	∴ *p*
3. Aturan transitif
	
	*p* → *q*
	
	*q* → *r*
	
	———
	
	∴ *p* → *r*
4. Silogisme disjungtif/kontrapositif
	
	*p* ∨ *q*
	
	~*p*
	
	———
	
	∴ *q*



	*p* ∨ *q*
	
	~*q*
	
	———
	
	∴ *p*
5. Simplifikasi Konjungtiif
	
	*p* ∧ *q*
	
	———
	
	∴ *p*


	*p* ∧ *q*
	
	———
	
	∴ *q*
6. Penjumlahan disjungtif
	
	*p*
	
	———
	
	∴ *p* ∨ *q*
7. Konjungsi
	
	*p*
	
	*q*
	
	———
	
	∴ *p* ∧ *q*

Selain menggunakan tabel kebenaran, sebuah argumen juga dapat dibuktikan kesahihannya dengan menggunakan campuran hukum-hukum logika dan metode penarikan kesimpulan yang sudah terbukti sahih (modus ponen, modus tollen, dsb). Contoh : 
- Buktikan bahwa argumen berikut benar: 
	~*p* ∨ *q* , *s* ∨ *p*, ~*q* ⇒ s
	Bukti : 
	
		(1) ~*p* ∨ *q* (Premis)
		
		(2) ~*q* (Premis)
		
		(3) ~*p* (Silogisme disjungtif (1) dan (2))
		
		(4) *s* ∨ *p* (Premis)
		
		(5) *s* (Silogisme disjungtif (3) dan (4))
		

## 3. Aksioma, Teorema, Lemma, Corollary
Aksioma adalah proposisi yang diasumsikan benar. Aksioma tidak memerlukan pembuktian kebenaran lagi. Contoh :
- Untuk semua bilangan real x dan y, berlaku x + y = y + x (hukum komutatif penjumlahan).
- Jika diberikan dua buah titik yang berbeda, maka hanya ada satu garis lurus yang melalui dua buah titik tersebut.
Teorema adalah proposisi yang sudah terbukti benar. Bentuk khusus dari teorema adalah lemma dan corollary. Lemma adalah teorema sederhana yang digunakan untuk pembuktian teorema lain, sedangkan corollary adalah teorema yang dapat dibentuk langsung dari teorema yang telah dibuktikan, atau dapat diartikan sebagai teorema yang mengikuti teorema lain.