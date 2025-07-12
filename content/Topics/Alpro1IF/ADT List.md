Intinya sih kayak sebuah array, tapi kayak dipecah2 gitu loh. Misal
- fungsi isEmpty = buat ngecek list kosong apa ga
- indexOf = buat search sebuah nilai ada di index ke berapa
- length = berapa banyak elemen di list
- getElmt = buat liat nilai di index tertentu
- setElmt = buat ubah nilai di index tertentu
- concat = gabung 2 list
- dll

## Implementasi ADT List dengan Array
Ada beberapa versi
Note = Index Fisik tuh kayak rilnya, lojik tuh ya anggepannya padahal aslinya mah kaga disitu![[Screenshot 2025-07-12 at 05.14.11.png]]
- Implisit (alt 1) = Yang kosong diisi mark dan gaboleh ada mark diantara nilai yang terisi
	- Rata kiri (alt 1a) = Index fisik mulai dari 0
	- Tidak rata kiri (alt 1b) = Index fisik ga mulai dari 0
- Eksplisit (alt 2) = ditentuin dari Neff dan gaboleh ada mark diantara nilai yang terisi
	-  Rata kiri (alt 2a) = Index fisik mulai dari 0
	- Tidak rata kiri (alt 2b) = Index fisik ga mulai dari 0
	
- Tersebar (alt 3) = Ya intinya nyebar aja sih (jadi antara nilai bisa ada mark). Jadi kalo mau ke elemen selanjutnya gabisa cuma index + 1 tapi harus cek jg mark apa kaga.![[Screenshot 2025-07-12 at 05.17.18.png]]
Operasi2nya liat di PPT aja di [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs)


### Array Dinamis
![[Screenshot 2025-07-12 at 05.18.31.png]]
Kayak penjelasan sebelumnya aja, intinya ukurannya bisa berubah2 lah.
Operasi2nya liat di PPT aja di [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs)