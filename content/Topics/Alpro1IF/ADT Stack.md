- Definisi: Stack itu kumpulan elemen yang operasinya cuma bisa dilakuin di satu ujung, yaitu **Top**. Prinsipnya **LIFO** (_Last In First Out_), yang terakhir masuk, pertama keluar.
- Analogi: Bayangin tumpukan piring, kita cuma bisa nambah atau ngambil piring dari paling atas.
![[Screenshot 2025-07-12 at 18.43.23.png]]
- Operasi:
    - CreateStack: Bikin stack kosong.
    - isEmpty/isFull: Ngecek stack kosong atau penuh.
    - push: Nambahin elemen ke Top.
    - pop: Ngambil elemen dari Top.
    - top: Liat elemen di Top tanpa ngambil.
    - Dll : [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs))
- Implementasi:
    - Bisa pake **array statik**, di mana idxTop nandain posisi elemen teratas. Kalo kosong,
        idxTop diset ke -1 (atau IDX_UNDEF).
        
- Note = Push itu Insert, Pop itu Delete.
![[Screenshot 2025-07-12 at 18.39.50.png]]

Contoh, operasi2 itu ada di [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWz_umlZLdeoacFVHPXoEs)), atau kalo mau liat C nya (karena praknya implementasiin si operasi2nya) itu ada di [githubnya nicholaswisee aja\(shoutout to wise)](https://github.com/nicholaswisee)

```
//contoh operasi di C nya
void Push(Stack * S, infotype X){
	Top(*S)++;
	InfoTop(*S) = X;
}
```