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

Proses modeling yang saya lakukan pada data ini adalah dengan membuat algoritma machine learning, yaitu content based filtering untuk algoritma content based filtering saya buat dengan apa yang disukai pengguna pada masa lalu.
Proses algoritma content based filtering yaitu :
1. Melakukan TF-IDF Vectorizer. TF-IDF Vectorizer akan digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap genre anime. Kita akan menggunakan fungsi tfidfvectorizer() dari library sklearn.
2. Melakukan perhitungan idf pada data genre
3. Mapping array dari fitur index integer ke fitur name
4. Melakukan fit lalu ditransformasikan ke bentuk matrix
5. Mengubah vektor tf-idf dalam bentuk matriks dengan fungsi todense()
6. Membuat dataframe untuk melihat tf-idf matrix
7. Kolom diisi dengan genre, Baris diisi dengan nama anime
8. Pada dataset dibuat dibagian fitur genre menjadi satu jenis genre untuk satu judul film karena akan membuat rekomendasi akan maksimal.

Tabel 4.
|name|fi|space|shounen|power|psychological|shoujo|josei|drama|mystery|mecha|
|---|---|---|---|---|---|---|---|---|---|---|
|Cleopatra D\.C\.|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Meiken Jolie|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Keroro Gunsou|0\.0|0\.0|1\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Tonari no Tamageta-kun|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|RPG Densetsu Hepoi|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Mo Jing Lieren 3rd Season|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Chibi Kero: Kerobouru no Himitsu\!?|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Vampire Hunter D|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|
|Kiss Dum: Engage Planet|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|1\.0|
|Doraemon \(2005\)|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|0\.0|

Tabel 4. merupakan hasil algoritma content based filtering

## Result
### Rekomendasi dengan Cosine Similarity

Tabel 5.
No | anime_id | name | genre
-- | -------- | ---- | -----
477 | 14353 | Death Billiards | Psychological

Tabel 5. merupakan contoh film yang di tonton pengguna di masa lalu.

Tabel 6.
|index|name|genre|
|---|---|---|
|0|DRAMAtical Murder|Psychological|
|1|Himitsu: The Revelation|Psychological|
|2|Mind Game|Psychological|
|3|Eikyuu Kazoku|Psychological|
|4|Born by Myself|Psychological|
|5|Paradise|Psychological|
|6|Fujimi 2-choume Koukyougakudan|Psychological|
|7|Kakari|Psychological|
|8|Chikotan|Psychological|
|9|Great Rabbit|Psychological|

Tabel 6. merupakan hasil rekomendasi dari cosine similarity.

### Rekomendasi dengan Euclidean Similarity

Tabel 7.
No | anime_id | name | genre
-- | -------- | ---- | -----
2727 | 2369 | Rental Magica | Mystery

Tabel 8.
|index|name|genre|
|---|---|---|
|0|GetBackers|Mystery|
|1|Mezzo DSA|Mystery|
|2|Cowboy Bebop: Tengoku no Tobira|Mystery|
|3|Gyakuten Saiban: Sono &quot;Shinjitsu&quot;, Igi Ari\!|Mystery|
|4|Tiger &amp; Bunny Recaps|Mystery|
|5|Higurashi no Naku Koro ni Kai|Mystery|
|6|Kuroshitsuji: Book of Murder|Mystery|
|7|Agatha Christie no Meitantei Poirot to Marple|Mystery|
|8|Kono Naka ni Hitori, Imouto ga Iru\!|Mystery|
|9|Kindaichi Shounen no Jikenbo: Shinigami Byouin Satsujin Jiken|Mystery|

Tabel 8. merupakan hasil rekomendasi dari euclidean similarity.

## Evaluation

## Komparasi  Waktu Eksekusi
Tabel 9.
No|Cosine Similarity|Euclidean Similarity|
--|-----------------|--------------------|
Time (Seconds)|1.136652|3.268346

Tabel 9. merupakan hasil dari komparasi waktu eksekusi. dilihat dari output yang dihasilkan untuk menghitung kecepatan komparasi waktu eksekusi didapat cosine similarity dengan nilai 1.136652 detik sedangkan euclidean similarity mendapatkan waktu 3.268346

## Kesimpulan

dataset harus di proses terlebih dahulu dengan menggunakan TF-IDF Vectorizer yang berguna untuk menentukan nilai frekuensi suatu kata di dalam sebuah dataset. kemudian dilanjutkan dengan Melakukan perhitungan idf pada fitur genre dan Mapping array dari fitur index integer ke fitur nama. lalu Melakukan fit lalu ditransformasikan ke bentuk matrix. selanjutnya Mengubah vektor tf-idf dalam bentuk matriks dengan fungsi todense(). Dari hasil proses sebelumnya dijalankan diketahui bahwa teknik cosine similarity dan teknik Euclidean Similarity sama-sama mendapatkan presisi yang akurat 100% dari percobaan hasil 9 output namun pada hal kecepatan waktu komparasi eksekusi teknik cosine similarity lebih unggul dari teknik Euclidean similarity.

## Referensi

[1] Billah, M., Artesya, M.A., Komalasari, D., S.Kom., M.Kom. (2021) . Penerapan CollaborativeFiltering, PCA dan K-Meansdalam Pembangunan Sistem Rekomendasi Ongoingdan UpcomingFilm Animasi Jepang. Seminar Nasional Mahasiswa Ilmu Komputer dan Aplikasinya (SENAMIKA) Jakarta-Indonesia.

[2] Zan Wang, Xue Yu, Nan Feng, Zhenhua Wang. (2014). Journal of Visual Languages & ComputingVolume 25, Issue 6, Pages 667-675. 
