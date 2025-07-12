### ADT Set
- Definisi: Kumpulan objek **unik** dengan tipe sama, dan gak ada urutan.
- Operasi:
    - add: Nambahin elemen (kalo belum ada).
    - remove: Ngapus elemen.
    - isIn: Ngecek keanggotaan elemen.
    - union, intersection, setDifference: Operasi himpunan biasa.
    - Dll [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWzumlZLdeoacFVHPXoEs))
    
![[Screenshot 2025-07-12 at 19.22.44.png]]
### ADT Map (Associative Array)
- **Definisi**: Kumpulan pasangan **(key, value)**, di mana **key** harus unik. 
- **Operasi**:
    - set: Nambah atau modif pasangan (key, value).
    - unset: Ngapus pasangan berdasarkan key.
    - find: Nyari value berdasarkan key.
    - Dll [DRIVE ACADS ACATRIX](https://drive.google.com/drive/u/1/folders/1LgD6Far17EFWzumlZLdeoacFVHPXoEs))
![[Screenshot 2025-07-12 at 19.27.33.png]]

## Hash
- Fungsi Hash: Fungsi yang memetakan data dengan ukuran bebas ke nilai dengan ukuran tetap (disebut hash atau digest).
- Collision: Terjadi kalo dua key yang beda ngasilin hash yang sama.
- Hash Table: Struktur data yang manfaatin fungsi hash buat nentuin indeks penyimpanan data.
- Penanganan Collision:
    - Hash Chaining: Tiap sel di hash table nyimpen association list kecil.
    - Open Addressing: Kalo ada collision, data disimpen di slot kosong berikutnya (bisa pake linear probing, quadratic probing, atau double hashing).
- Load Factor: Rasio antara slot terisi dan total slot.