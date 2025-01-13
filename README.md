# Laporan Proyek Machine Learning - Raihan Khairul Rochman
# Sistem Rekomendasi Ponsel

## Project Overview

Sistem rekomendasi telah menjadi salah satu alat penting untuk mempermudah pengambilan keputusan, khususnya dalam dunia digital yang dipenuhi dengan informasi dan pilihan. Dalam sebuah artikel oleh Robin Burke, dkk (2011), sistem rekomendasi dijelaskan sebagai "sebuah sistem yang menyajikan rekomendasi yang dipersonalisasi sebagai output atau mempunyai efek untuk mengarahkan pengguna secara dipersonalisasi kepada objek yang menarik atau berguna dalam posibilitas opsi yang luas."¹

Dalam bidang pemasaran, sistem rekomendasi digunakan untuk merekomendasikan produk yang mungkin menarik atau berguna untuk pengguna dari sekian banyak opsi produk yang ada. Dewasa ini, produk ponsel menjadi salah satu jenis produk dengan opsi yang paling banyak seiring dengan berkembangnya teknologi. Dalam hal ini, kebutuhan akan sistem rekomendasi menjadi semakin meningkat untuk dapat menyajikan pilihan produk ponsel yang menarik bagi pengguna.

Dalam projek ini saya akan membuat sebuah sistem rekomendasi untuk produk ponsel. Dataset yang digunakan bernama "Cellphones Recommendations" yang diambil dari situs Kaggle. Dataset berisi data spesifikasi produk ponsel paling populer Amerika pada tahun 2022 dan data penilaian berdasarkan survei beserta data pengguna atau partisipan pada survei tersebut.

¹ [Burke, Robin, Alexander Felfernig, and Mehmet H. Göker. "Recommender systems: An overview." Ai Magazine 32.3 (2011): 13-18.](https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/2361/2231)
²

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa proyek ini penting untuk diselesaikan.
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
  
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 

## Business Understanding

Melimpahnya opsi produk ponsel dalam pasar khususnya *e-commerce* seringkali menimbulkan keraguan dan kebingungan di antara pelanggan. Opsi yang melimpah membuat pelanggan sulit untuk mempertimbangkan produk mana yang lebih cocok dengan preferensi dan kebutuhan mereka. Untuk mengatasi hal ini, sistem rekomendasi hadir untuk memberikan saran kepada pengguna terkait produk-produk yang mungkin mereka sukai secara mudah. Sistem rekomendasi membantu pengguna menemukan produk yang relevan dengan mereka berdasarkan pola yang dipelajari pada data aktivitas dan penilaian pengguna, atau mencari kesamaan antara satu produk dengan produk lainnya.

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana 
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding

Dataset yang saya gunakan adalah dataset *Cellphones Recommendation* yang diunduh dari situs Kaggle. Dataset ini berisi data tentang ponsel paling populer di Amerika Serikat pada tahun 2022. Dataset ini mengandung 3 file csv yang terdiri dari data ponsel, data pengguna, dan data penilaian pengguna.

Data ponsel yang terdapat pada berkas `cellphones data.csv` berisi 33 jenis ponsel berbeda dengan 13 fitur yang mencakup spesifikasi ponsel seperti performa berdasarkan nilai AnTuTu, kapasitas memori, kapasitas baterai, resolusi kamera, ukuran layar, tanggal rilis, dan lain-lain. Harga dari setiap ponsel diambil dari Amazon dan Best-Buy pada bulan Agustus 2022.

Data pengguna dan penilaiannya terdapat pada berkas `cellphones users.csv` dan `cellphones ratings.csv`. Penilaian diambil berdasarkan survei di Mechanical Turk. Setiap partisipan diberikan 10 jenis ponsel secara acak dan diminta untuk menilai seberapa mungkin partisipan untuk membeli ponsel tersebut dengan harga yang ditentukan dalam skala 1 (sangat tidak setuju) hingga 10 (sangat setuju). Partisipan juga diminta untuk mengisi beberapa informasi pribadi yaitu umur, jenis kelamin, dan pekerjaan.

* [Kaggle. "Cellphones Recommendations"](https://www.kaggle.com/datasets/meirnizri/cellphones-recommendations)

Variabel-variabel yang terdapat pada Cellphones Recommendations dataset adalah sebagai berikut:

### Data Ponsel (`cellphones data.csv`)
1. `cellphone_id`: Nomor pengenal unik yang diberikan untuk setiap ponsel.
2. `brand`: Merek dari ponsel.
3. `model`: Model dari ponsel.
4. `operating system`: Sistem operasi ponsel.
5. `internal memory`: Kapasitas penyimpanan internal ponsel dalam gigabita (GB).
6. `RAM`: Kapasitas RAM (*Random Memory Access*) ponsel dalam gigabita (GB).
7. `performance`: Nilai performa ponsel berdasarkan penilaian AnTuTu.
8. `main camera`: Resolusi kamera utama (belakang) dalam megapiksel (MP).
9. `selfie camera`: Resolusi kamera swafoto (depan) dalam megapiksel (MP).
10. `battery size`: Kapasitas baterai ponsel dalam miliampere-jam (mAh).
11. `screen size`: Ukuran layar ponsel dalam inci.
12. `weight`: Berat ponsel dalam gram.
13. `price`: Harga ponsel dalam Dolar Amerika Serikat (USD). Diambil dari Amazon dan Best-Buy pada Agustus 2022.
14. `release date`: Tanggal rilis ponsel dalam format hari/tanggal/tahun.

### Data Penilaian (`cellphones ratings.csv`)
1. `user_id`: Nomor identitas pengguna diambil dari dataset pengguna.
2. `cellphone_id`: Nomor identitas ponsel diambil dari dataset ponsel.
3. `rating`: Penilaian yang diberikan dalam skala 1 (sangat tidak setuju) hingga 10 (sangat setuju) untuk seberapa mungkin pengguna membeli ponsel tersebut dengan harga yang ditentukan.

### Data Pengguna (`cellphones users.csv`)
1. `user_id`: Nomor pengenal unik yang diberikan untuk setiap pengguna.
2. `age`: Usia pengguna dalam tahun.
3. `gender`: Jenis kelamin pengguna.
4. `occupation`: Pekerjaan pengguna.

Untuk memberikan gambaran terkait informasi dan analis tentang dataset lebih lanjut, saya menampilkan beberapa tangkapan layaran yang merupakan keluaran dari kode-kode yang menampilkan informasi tentang dataset pada *notebook* berikut.

### Univariate Analysis Data Ponsel

![image](https://github.com/user-attachments/assets/785d09ae-e161-48f6-a311-099231f13b4f)
![image](https://github.com/user-attachments/assets/39b1f40f-756c-497a-8315-d1e11cb5cd95)

Hasil keluaran di atas menunjukkan bahwa dataset ponsel memiliki 33 entri atau 33 produk ponsel yang berbeda dengan total 14 kolom yang 13 diantaranya merupakan kolom fitur yang terdiri dari 9 fitur numerik (tidak termasuk `cellphone_id`) dengan tipe data `int64` dan `float64` dan 4 fitur kategorikal dengan tipe data `object`. Kolom fitur menjelaskan tentang spesifikasi ponsel.

Terdapat total 10 merek yang berbeda dari 33 produk ponsel yang terdata. Delapan produk di antaranya merupakan produk merek Samsung, enam dari merek Apple, dan sisanya merupakan produk dari merek yang beragam mulai dari OnePlus, Xiaomi, hingga Sony.

### Univariate Analysis Data Penilaian

![image](https://github.com/user-attachments/assets/503a0cb5-5aff-4d56-8e3c-5c28e45fbec1)
![image](https://github.com/user-attachments/assets/39647208-03ea-4d46-a0d4-f4b0900c489b)  
![image](https://github.com/user-attachments/assets/2ab73291-7fc1-4374-a188-c63a04e50ee2)  
![image](https://github.com/user-attachments/assets/e3e404e8-aeb1-461d-aed2-664f03c25cfe)

Berdasarkan hasil keluaran di atas, terdapat 990 entri penilaian yang diambil dari 99 pengguna yang berbeda. Hal ini sesuai dengan ketentuan survei bahwa setiap pengguna menilai 10 produk ponsel secara acak. Dalam dataset ditunjukkan bahwa terdapat entri penilaian untuk 33 jenis produk ponsel yang berbeda, yang artinya seluruh entri atau produk pada dataset ponsel memiliki penilaian penggunanya masing-masing.

Analisis nilai rating menunjukkan bahwa rata-rata penilaian pengguna adalah 6,7. Penilaian terendah adalah 1 dan penilaian tertinggi adalah 18 melebihi skala maksimum penilaian, yaitu 10, yang artinya terdapat nilai yang tidak valid pada dataset. Selanjutnya diketahui bahwa terdapat hanya satu buah entri dengan nilai 18. Nilai ini akan dikonversi menjadi 10 sebagai nilai maksimum untuk mencegah bias pada model.

### Univariate Analysis Data Pengguna

![image](https://github.com/user-attachments/assets/e9625413-81e7-4400-9915-b49cbb980926)
![image](https://github.com/user-attachments/assets/31de8d8b-9527-4c7f-8106-07aa40795e11)

Data pengguna memiliki 99 entri seperti ditunjukkan di atas, dengan 50 di antaranya merupakan laki-laki dan 46 di antaranya merupakan perempuan. Sementara itu, terdapat 3 pengguna dengan data `gender` yang tidak valid. Namun, data `gender` yang tidak valid tidak akan diproses karena fitur `gender` tidak digunakan untuk pelatihan. Rata-rata usia pengguna yang terdaftar adalah sekitar 36 tahun. Para pengguna juga memiliki jenis pekerjaan yang bervariasi ditunjukkan dengan terdapatnya setidaknya 46 jenis pekerjaan yang berbeda pada dataset.

## Data Preparation

### Menangani *Outlier*

Pada tahap *univariate analysis* data penilaian, ditemukan sebuah penilaian yang melebihi batas maksimum skala yaitu 10. Pada tahap ini saya akan mengonversi penilaian tersebut menjadi pada batas maksimum yaitu 10. Hal ini bertujuan untuk menjaga konsistensi pada skala data.

## Mengekstraksi Tahun Rilis menjadi Fitur Baru

![image](https://github.com/user-attachments/assets/1472671a-5fe9-4d7f-b421-975f7d0b011b)

Pada tahap ini saya mengekstraksi nilai tahun dari tanggal rilis untuk mempermudah model mengklasifikasikan ponsel berdasarkan tahun rilis untuk skema *content-based filtering*.

![image](https://github.com/user-attachments/assets/2b94c8a1-2ab9-4467-bf94-6e8d129e2e2d)


## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
