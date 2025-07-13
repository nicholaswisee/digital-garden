# CPU-Memory Speed and Locality of Reference 

Terdapat kesenjangan kecepatan yang terus melebar antara kecepatan CPU, memori utama (DRAM), dan penyimpanan massal (disk).
- **SRAM (Static RAM)** lebih cepat dan lebih mahal daripada DRAM, menggunakan 4 atau 6 transistor per bit, serta mempertahankan nilainya selama daya tersambung dan tidak memerlukan penyegaran. SRAM umumnya digunakan untuk **memori cache**.
- **DRAM (Dynamic RAM)** lebih lambat dan lebih murah, menyimpan bit dengan kapasitor tunggal, dan nilainya harus disegarkan setiap 10-100 ms. DRAM digunakan untuk **memori utama** dan _frame buffer_. Akses SRAM sekitar 4 ns/doubleword, DRAM sekitar 60 ns, sementara disk sekitar 40.000 kali lebih lambat dari SRAM dan 2.500 kali lebih lambat dari DRAM.
- TL;DR, SRAM faster than DRAM lol. 

Karena adanya kesenjangan kecepatan, dibutuhkan sebuah prinsip lokalitas atau *Locality of Reference*, yaitu sebuah prinsip yang menyebabkan program cenderung menggunakan data dan instruksi dengan alamat yang berdekatan atau sama dengan yang baru saja digunakan.
- **Lokalitas Temporal (Temporal Locality)**: Item yang baru saja diakses kemungkinan besar akan diakses lagi dalam waktu dekat.
- **Lokalitas Spasial (Spatial Locality)**: Item dengan alamat yang berdekatan cenderung diakses bersamaan dalam waktu.


# Memory Hierarchy 
Intinya ini adalah general knowledge tentang bagaimana data diproses dalam sebuah komputer. Untuk penjelasan lebih spesifik, *watch* https://www.youtube.com/watch?v=lQcU4WwVALI&t=12s.
![[Pasted image 20250713134443.png]]
