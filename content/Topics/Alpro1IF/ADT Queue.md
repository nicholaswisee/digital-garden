- Definisi: Queue itu sederetan elemen dengan prinsip **FIFO** (_First In First Out_). Elemen ditambahin di belakang (**TAIL**) dan dikeluarin dari depan (**HEAD**).
- Analogi: Persis kayak antrian di dunia nyata, siapa yang dateng duluan, dia yang dilayanin duluan.
- **Operasi**:
    - CreateQueue: Bikin antrian kosong.
    - enqueue: Nambahin elemen ke `TAIL`.
    - dequeue: Ngapus elemen dari `HEAD`.
    - head: Liat elemen di `HEAD` tanpa ngapus.
    - isEmpty/isFull: Ngecek antrian kosong atau penuh. 
- **Implementasi dengan Array**:
    - **alt-1**: idxHead selalu 0. Pas `dequeue`, semua elemen digeser ke kiri.
	    Kalo nambahin elemen =
		- Kalo maish ada tempat = TAIL geser ke kanan
		- Kalo queue kosong, idxHead = idxTail = 0
		Kalo ngapus elemen =
		- Kalo ga kosong = Ambil HEAD dan geser semua elemen dari idxHead+1 -- idxTail dan geser ke kiri.
		- Kalo elemennya cuma 1, idxHead = idxTail = IDX=UNDEF
		![[Screenshot 2025-07-12 at 18.05.37.png]]
    - **alt-2**: idxHead bisa geser ke kanan (ga mesti dari 0). Pas enqueue dan idxTail mentok, baru semua elemen digeser ke kiri.
	    Kalo nambahin elemen = kayak alt-1 tadi, tapi kalo idxTail = idxMax padahal sebelah head masih kosong, maka harus digeser dulu
		Kalo ngapus elemen =
		- Kalo ga kosong = ambil HEAD kemudian HEAD geser ke kanan (idxHeadnya aja)
		- Kalo elemennya cuma 1 kayak alt-1 tadi.
		![[Screenshot 2025-07-12 at 18.10.13.png]]
    - **alt-3 (Circular Buffer)**: idxHead dan idxTail "muter" di array. Gak perlu ada pergeseran elemen sama sekali. Paling ruwet tapi codingnya aowkoakwo
	    Kalo nambahin elemen =
	    - Kalo idxTail < idxMax maka kayak alt-1 & 2 tadi
	    - idxTail = idxMax  maka idxTail baru jadi 0 (asumsi masih ada tempat)
	    - Kalo kosong maka idxHead = idxTail = 0
	    Kalo ngapus elemen =
	    - Ambil HEAD terus HEAD geser kanan
	    - Kalo idxHead = idxMax maka idxHead baru jadi 0
	    - Kalo elemen nya 1 maka idxHead = idxTail = IDX_UNDEF
	    NOTE = PAKE **mod** buat insert ataupun delete, sumpah ngaruh bat karena kayak misalkan CAPACITY = 9 (idxMax = 8) dan idxTail = 8, terus mau insert kan berarti idxTail+1 = 9, nah 9 mod 9 = 0, maka idxTailnya jadi 0. Kalo idxTailnya misal = 5, maka 5+1 mod 9 = 6, maka idxTailnya jadi 6. Paham kan?
	    ![[Screenshot 2025-07-12 at 18.16.49.png]]
	    
        


Kalo mau belajar C nya baca [githubnya nicholaswisee aja\(shoutout to wise)](https://github.com/nicholaswisee)
```
//contoh enqueue queue alt-3
void enqueue(Queue *q, ElType val){
	if (isFull(*q))
	{
		return;
	} else
	{
		if (isEmpty(*q))
		{
			IDX_HEAD(*q) = 0;
			IDX_TAIL(*q) = 0;
		} else
		{
			IDX_TAIL(*q) = (IDX_TAIL(*q)+1)%CAPACITY;
		}
			TAIL(*q) = val;

}

}
```