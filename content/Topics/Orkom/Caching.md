Pada rangkuman ini, saya hanya membahas materi-materi yang sering keluar pada UAS, apabila kalian penasaran tentang materinya secara keseluruhan, baca Powerpoint Mata Kuliah atau tonton https://www.youtube.com/watch?v=zF4VMombo7U&list=PL38NNHQLqJqYnNrTenxBvGJSPCkV9EOWk.


# Cache Organization
![[Pasted image 20250713134908.png]]
Organisasi cache ditentukan oleh tiga parameter utama:
- **S (Jumlah Set)**: `S = 2s` set.
- **E (Jumlah Baris per Set)**: `E = 2e` baris per set.
- **B (Jumlah Byte per Blok)**: Ukuran blok data adalah `B` byte.
**Ukuran cache (C)** dihitung dengan formula: `C = S x E x B` byte data. Setiap baris (line) dalam cache memiliki **valid bit** (v) dan **tag**. 

Alamat memori dibagi menjadi tiga bagian untuk akses cache:
- **t bits (tag)**: Untuk identifikasi blok.
- **s bits (set index)**: Untuk menemukan set yang benar.
- **b bits (block offset)**: Untuk menemukan data di dalam blok.
Contohnya, 
![[Pasted image 20250713135008.png]]
Langkah mencari data dalam cache: 
1. **Menemukan set** menggunakan `set index` dari alamat.
2. Memeriksa apakah ada baris dalam set tersebut yang memiliki tag yang cocok.
3. Jika **cocok dan baris valid (hit)**, data ditemukan di cache.
4. **Menemukan data** yang dimulai pada `block offset` yang ditentukan.

## Cache Hit and Miss
- **Cache Hit**: Data yang diminta ditemukan di cache.
- **Cache Miss**: Data yang diminta tidak ditemukan di cache. Dalam kasus ini, baris lama diusir (evicted) dan diganti dengan baris baru dari memori utama. Kebijakan penempatan (placement policy) menentukan di mana blok baru ditempatkan, dan kebijakan penggantian (replacement policy) menentukan blok mana yang akan diusir (misalnya, _random_, _least recently used/LRU_).

## Jenis - jenis Cache 
- **Direct-Mapped Cache (E = 1)**: Hanya ada satu baris per set. Blok dari memori utama hanya dapat dipetakan ke satu lokasi set spesifik di cache. Jika beberapa objek data memetakan ke lokasi blok cache yang sama, ini dapat menyebabkan _conflict miss_.
- **E-way Set Associative Cache (E > 1)**: Ada `E` baris per set. Ini memungkinkan blok data dari memori utama untuk ditempatkan di salah satu dari `E` baris dalam set yang ditentukan. Ini mengurangi _conflict miss_ dibandingkan dengan _direct-mapped cache_.
- Biasanya, cache memilih jalan tengah antara kedua sistem tersebut, yaitu memiliki associativity yang tinggi dan baris yang banyak. 

# Write & Read Policies 
Lebih baik kalian menonton video di atas atau mencari sumber di *youtube* agar lebih jelas dengan visualisasinya. 
• **Write-through**: Data segera ditulis ke memori utama.
• **Write-back**: Penulisan data ke memori ditunda hingga baris cache tersebut diganti. Ini menggunakan _dirty bit_ untuk melacak apakah baris tersebut telah dimodifikasi.
• **Write-allocate**: Pada _write-miss_, baris data dimuat ke dalam cache terlebih dahulu sebelum diperbarui. Ini baik jika akan ada lebih banyak penulisan ke lokasi tersebut.
• **No-write-allocate**: Pada _write-miss_, data langsung ditulis ke memori tanpa memuat baris ke cache terlebih dahulu.