# Submission - Dicoding - ML - Terapan 2

# Laporan Proyek Machine Learning - Ridwan Abdiansah

## Project Overview
Teknologi informasi dan telekomunikasi semakin berkembang dan mengalami peningkatan yang sangat tinggi, dalam  hal  ini  dapat  diketahui  banyak  sekali  kegiatan  manusia  yang  membutuhkan  teknologi  informasi  dan komunikasi untuk saat ini, tidak terkecuali dalam bidang musik maupun film. Film merupakan audio visual yang memiliki banyak genre, seperti genre komedi, drama, horor, action, dan masih banyak lagi. Negara-negara maju sudah melebarkan sayap industri dalam bidang perfilman baik di negaranya sendiri maupun di mancanegara. Salah satu negara di Asia yang dikenal dengan industri filmnya di bidang animasi, yaitu Jepang. Film  Animasi  Jepang  atau  yang  dikenaldengan  sebutan animetersebut  memiliki  banyak  kategori  diantaranya genre,  jumlah  episode,  media  tayang  (layar  lebar,  TV,  OVA,  dan  ONA),  sumber  cerita  (Manga,  Light  Novel, Original), studio, musim rilis (Spring, Summer, Winter, dan Fall) serta komunitas. Berdasarkan   kategori   yang   telah   disebutkan,   memunculkan   masalah baru   bagi   penikmat animeuntuk menemukan animemana  yang  selanjutnya  akan  ditonton,  khususnya animeyang  masih  berstatus ongoingdan upcoming. Masalah ini dapat diatasi dengan menyampaikan informasi berupa daftar-daftar animeyang menjadi rekomendasi  kepada  penikmat animetersebut  berdasarkan  preferensinya  sendiri  (user).  Maka  dari  itu,  perlu adanya sebuah sistem yang dapat memberikan rekomendasi daftar animekepada user [1].

Sistem rekomendasi telah menjadi lazim dalam beberapa tahun terakhir karena mereka menangani masalah kelebihan informasi dengan menyarankan pengguna produk yang paling relevan dari sejumlah besar data. Untuk produk media, rekomendasi film kolaboratif online berupaya membantu pengguna mengakses film pilihan mereka dengan menangkap tetangga yang persis sama di antara pengguna atau film dari peringkat umum historis mereka. Namun, karena data yang jarang, pemilihan tetangga menjadi lebih sulit dengan meningkatnya film dan pengguna dengan cepat [2].

## Business Understanding

### Problem Statement

Bagaimana cara merekomendasikan movie yang disukai pengguna lain dapat direkomendasikan kepada pengguna lainnya dengan metode content based filtering ?

### Goals

Membangun sistem rekomendasi yang baik dengan metode content based filtering yang berguna bagi penikmat film anime dan menaikan nilai market ke pada perusahaan.

### Solution Statements

Menawarkan solusi sistem rekomendasi dengan metode content based filtering. Untuk mendapatkan rekomendasi terbaik, akan digunakan dua model yang berbeda yaitu Eucliden Distance dan Cosine Similarity  Selain itu, untuk mengukur kinerja model digunakan Komparasi Metrik Precision.

## Data Understanding

Berdasarkan sumber dataset: [Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database) diperoleh informasi:

Kumpulan data ini berisi informasi data preferensi pengguna dari 73.516 pengguna di 12.294 anime. Setiap pengguna dapat menambahkan anime ke daftar lengkap mereka dan memberikannya peringkat dan kumpulan data ini adalah kompilasi dari peringkat tersebut. 

Informasi Dataset / Deskripsi Varibel

* anime_id - id unik myanimelist.net yang mengidentifikasi anime.
* nama - nama lengkap anime.
* genre - daftar genre yang dipisahkan koma untuk anime ini.
* jenis - film, TV, OVA, dll.
* episode - berapa banyak episode dalam acara ini. (1 jika film). rating – rating rata-rata dari 10 untuk anime ini.
* anggota - jumlah anggota komunitas yang ada di anime ini "kelompok".

## Data Preparation

### Menangani Missing Value

Untuk mendeteksi missing value digunakan fungsi isnull().sum(). Namun sebelum itu kita cek fitur anime_id dan name apakah ada file yang terduplikat.

### Fitur anime_id
Tabel 1.
Jumlah Data | Jumlah Data Anime_id
----------- | --------------------
12294 | 12294

Terlihat pada fitur anime_id tidak terindikasi adanya file yang terduplikat.

### Fitur name
Tabel 2.
Jumlah Data | Jumlah Data Name
----------- | ----------------
12294 | 12292

Terlihat pada fitur name terindikasi adanya file duplikat karena adanya perbedaan data.

### Fitur Genre

Fitur genre ditemukan 43 Jenis dengan cara callback handler.

### Hasil Missing Value 

Tabel 3.
Fitur | Jumlah Value
----- | ------------
anime_id | 0
name | 0
genre | 0

Karena dari hasil output di atas menunjukkan bahwa tidak ada missing value pada dataset, maka kita akan melanjutkan ke tahap berikutnya.

## Modeling

### Rekomendasi dengan Cosine Similarity

Tabel 4.
No | anime_id | name | genre
-- | -------- | ---- | -----
477 | 14353 | Death Billiards | Drama

Tabel 4. merupakan contoh film yang di tonton pengguna di masa lalu.

Tabel 5.
No | name |	genre
-- | ---- | -----
0 |	Kurumiwari Ningyou	Drama
1	Momoko, Kaeru no Uta ga Kikoeru yo.	Drama
2	Soukyuu no Fafner: Dead Aggressor	Drama
3	Karasu Tengu Kabuto	Drama
4	Kyoushoku Soukou Guyver II	Drama
5	Plastic Memories	Drama
6	Koe wo Kikasete	Drama
7	Mobile Suit Gundam ZZ	Drama
8	Perrine Monogatari Movie	Drama
9	Futatsu no Kurumi	Drama

## Evaluation

## Referensi

[1] Billah, M., Artesya, M.A., Komalasari, D., S.Kom., M.Kom. (2021) . Penerapan CollaborativeFiltering, PCA dan K-Meansdalam Pembangunan Sistem Rekomendasi Ongoingdan UpcomingFilm Animasi Jepang. Seminar Nasional Mahasiswa Ilmu Komputer dan Aplikasinya (SENAMIKA) Jakarta-Indonesia.

[2] Zan Wang, Xue Yu, Nan Feng, Zhenhua Wang. (2014). Journal of Visual Languages & ComputingVolume 25, Issue 6, Pages 667-675. 
