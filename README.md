# Laporan Proyek Machine Learning - Evan Arlen Handy

## Project Overview

### Latar Belakang
Dalam era digital saat ini, industri film dihadapkan pada tantangan besar dalam memenuhi kebutuhan dan harapan penontonnya. Dengan ribuan judul film yang tersedia di berbagai platform streaming, pengguna sering kali mengalami kesulitan dalam menemukan konten yang sesuai dengan selera mereka. Hal ini menyebabkan perasaan kewalahan dan kebingungan, karena banyaknya pilihan yang ada justru dapat mengurangi pengalaman menonton. Selain itu, film-film yang kurang dikenal sering kali tidak mendapatkan perhatian yang layak, padahal mereka mungkin memiliki kualitas yang setara dengan film blockbuster yang lebih populer. Situasi ini menciptakan kebutuhan mendesak untuk suatu sistem yang dapat membantu penonton menjelajahi dunia film yang luas dan menemukan judul yang relevan dan menarik bagi mereka.

Untuk mengatasi masalah ini, proyek ini bertujuan untuk mengembangkan sistem rekomendasi film yang memanfaatkan dua pendekatan utama: Content-Based Filtering dan Collaborative Filtering. Dengan menggunakan Content-Based Filtering pendekatan yang diterapkan adalah Nearest Neighbors sebuah algoritma yang efektif dalam menemukan kemiripan antara item berdasarkan fitur yang relevan. Sistem akan merekomendasikan film kepada pengguna berdasarkan kesamaan konten dari film yang telah mereka tonton sebelumnya. Misalnya, jika seorang pengguna menyukai film dengan genre tertentu, sistem akan menganalisis atribut film tersebut, seperti sinopsis, genre, dan kata kunci, untuk menyarankan film lain yang memiliki kesamaan. Pendekatan ini sangat berguna dalam memberikan rekomendasi yang relevan dan personal, sehingga pengguna dapat dengan mudah menemukan film baru yang sesuai dengan preferensi mereka. [[1](https://cris.bgu.ac.il/en/publications/recommender-systems-techniques-applications-and-challenges)] [[2](https://ieeexplore.ieee.org/document/10146638)]

Di sisi lain, Collaborative Filtering memanfaatkan data interaksi pengguna untuk memberikan rekomendasi. [[3](https://www.researchgate.net/publication/366110801_Sistem_Rekomendasi_Wisata_Kuliner_di_Yogyakarta_dengan_Metode_Item-Based_Collaborative_Filtering)] Dengan menganalisis pola perilaku pengguna lain yang memiliki kesamaan, sistem ini dapat mengidentifikasi film yang mungkin disukai oleh pengguna meskipun tidak ada kesamaan konten langsung. Ini memungkinkan sistem untuk menawarkan rekomendasi yang lebih kaya dan beragam, meningkatkan peluang penemuan film yang mungkin tidak terduga oleh pengguna. Melalui pengembangan sistem rekomendasi berbasis konten dan collaborative filtering ini, diharapkan dapat membantu pengguna dalam menemukan film-film yang sesuai dengan minat mereka, meningkatkan kepuasan menonton, dan memberikan nilai tambah bagi platform distribusi film. Dengan demikian, proyek ini tidak hanya menjadi solusi teknis untuk masalah penemuan film, tetapi juga berkontribusi pada pengalaman pengguna yang lebih baik dalam dunia hiburan yang terus berkembang.

Referensi: 
---
- [[1]](https://cris.bgu.ac.il/en/publications/recommender-systems-techniques-applications-and-challenges) Recommender Systems: Techniques, Applications, and Challenges
- [[2]](https://ieeexplore.ieee.org/document/10146638) Content-Based Filtering Using K-Nearest Neighbor
- [[3]](https://www.researchgate.net/publication/366110801_Sistem_Rekomendasi_Wisata_Kuliner_di_Yogyakarta_dengan_Metode_Item-Based_Collaborative_Filtering) Sistem Rekomendasi Wisata Kuliner di Yogyakarta dengan Metode Item-Based Collaborative Filtering

## Business Understanding

Dalam proyek ini, peneliti mengembangkan sistem rekomendasi film yang bertujuan untuk membantu pengguna menemukan film yang sesuai dengan preferensi mereka. Sistem rekomendasi ini akan memanfaatkan dua pendekatan utama, yaitu **Content-Based Filtering** dan **Collaborative Filtering**. Dengan menggunakan dataset film yang diperoleh dari **[The Movies Dataset](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset)** peneliti menerapkan beberapa algoritma untuk memberikan rekomendasi film yang relevan dan personal.

### Problem Statements

Berdasarkan latar belakang yang sudah dipaparkan di atas, rumusan masalah yang diperoleh sebagai berikut:

- Bagaimana cara mengembangkan sistem rekomendasi film yang efektif yang mampu menyarankan film kepada pengguna berdasarkan kesamaan konten dari film yang telah mereka tonton sebelumnya?

- Bagaimana cara memastikan bahwa rekomendasi yang diberikan relevan dan sesuai dengan preferensi pengguna, terutama dalam konteks film yang memiliki genre atau tema tertentu?

- Apa metode yang paling efektif antara Content-Based Filtering menggunakan Nearest Neighbors dan Collaborative Filtering menggunakan SVD (Singular Value Decomposition) untuk memberikan rekomendasi film yang akurat?

### Goals

- Tujuan utama adalah membangun sistem rekomendasi film yang mampu memberikan saran film yang sesuai dengan preferensi pengguna berdasarkan analisis konten dari film yang telah ditonton sebelumnya.

- Untuk mencapai rekomendasi yang relevan, sistem akan menganalisis atribut film seperti genre, sinopsis, dan kata kunci, serta menggunakan algoritma Nearest Neighbors untuk menemukan film yang mirip.

- Peneliti akan membandingkan efektivitas kedua pendekatan **Content-Based Filtering** dan **Collaborative Filtering** dalam memberikan rekomendasi, serta menentukan mana yang memberikan hasil terbaik dalam konteks rekomendasi film.

### Solution Statements

Untuk mencapai tujuan ini, peneliti mengusulkan beberapa solusi yang akan diuji dan dibandingkan:

- Menggunakan **Content-Based Filtering** dengan Nearest Neighbors untuk menganalisis atribut film dan memberikan rekomendasi berdasarkan kesamaan konten dari film yang telah ditonton.

- Mengimplementasikan **Collaborative Filtering** menggunakan SVD untuk menganalisis data rating dari pengguna lain dan memberikan rekomendasi berdasarkan pola preferensi pengguna yang serupa.

- Melakukan preprocessing data untuk memastikan bahwa informasi yang digunakan dalam analisis adalah akurat dan relevan, termasuk pengisian nilai kosong pada kolom sinopsis dan normalisasi data jika diperlukan.

- Mengukur kinerja setiap pendekatan rekomendasi dengan metrik relevansi, seperti akurasi dan kepuasan pengguna, untuk menentukan pendekatan mana yang paling efektif dalam memberikan rekomendasi film yang sesuai.

## Data Understanding

### Informasi Dataset

Dataset yang digunakan dalam proyek ini adalah **[The Movies Dataset](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset)**. Dataset ini terdiri dari 46.628 baris dan 27 kolom, di mana setiap baris berisi informasi tentang berbagai film, termasuk atribut seperti judul, genre, sinopsis, dan rating. Dataset ini banyak digunakan dalam penelitian sistem rekomendasi untuk memberikan saran film berdasarkan preferensi pengguna.

### Deskripsi Variabel

Dataset ini terdiri dari berbagai kolom yang merepresentasikan informasi tentang film. Berikut adalah deskripsi dari masing-masing variabel yang terdapat dalam dataset:

| **Variabel**                | **Deskripsi**                                                                                                                                               |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `movie_id`                  | Identifier unik untuk setiap film.                                                                                                                           |
| `title`                     | Judul film.                                                                                                                                                 |
| `genres`                    | Genre film yang dapat mencakup berbagai kategori seperti Action, Comedy, Drama, dan lainnya.                                                                  |
| `overview`                  | Sinopsis atau deskripsi singkat tentang film.                                                                                                              |
| `release_date`              | Tanggal rilis film.                                                                                                                                         |
| `vote_average`              | Rata-rata rating film berdasarkan penilaian pengguna.                                                                                                        |
| `vote_count`                | Jumlah total suara yang diberikan pada film.                                                                                                                |
| `popularity`                | Tingkat popularitas film berdasarkan penilaian dan interaksi pengguna.                                                                                     |
| `cast`                      | Daftar aktor dan aktris yang berperan dalam film.                                                                                                          |
| `crew`                      | Daftar kru yang terlibat dalam produksi film, termasuk sutradara dan penulis.                                                                               |
| `production_companies`      | Perusahaan produksi yang terlibat dalam pembuatan film.                                                                                                    |

### Exploratory Data Analysis (EDA)

Untuk memahami lebih dalam mengenai dataset, beberapa tahapan eksplorasi data dilakukan sebagai berikut:

1. **Pemeriksaan Dimensi dan Tipe Data**:
   - Menggunakan `df.info()` untuk melihat jumlah baris dan kolom, serta tipe data dari setiap variabel.
     
     <img width="248" alt="info-dataset" src="https://github.com/user-attachments/assets/d43951ea-4850-442d-9113-4497faad9dae">

   - Menggunakan `df.describe()` untuk mendapatkan statistik deskriptif seperti mean, median, standar deviasi, dan nilai maksimum/minimum dari fitur numerik.
     
     <img width="370" alt="stats-deskriptif" src="https://github.com/user-attachments/assets/bbba7d25-79f5-43a5-93d9-906f8f47a01a">

   - Menggunakan `df.head()` untuk melihat beberapa baris pertama dari dataset.
   - 
   <img width="377" alt="baris_pertama1" src="https://github.com/user-attachments/assets/b9dea3f8-9612-4eda-bcfa-5f3e0a0c9bf4">
  
   <img width="328" alt="baris_pertama2" src="https://github.com/user-attachments/assets/b246407e-03e3-4f96-aec2-cf237485d251">

   <img width="275" alt="baris_pertama3" src="https://github.com/user-attachments/assets/ff5ebdb7-8c49-48bf-b238-0e52250ebf78">

   - Menggunakan `df.isnull().sum()` untuk memeriksa apakah terdapat nilai yang hilang dalam dataset. Jika ada, langkah penanganan perlu dilakukan.
   - Menggunakan `df.duplicated().sum()` untuk menghitung jumlah baris yang merupakan duplikat dalam dataset. Data duplikat dapat menyebabkan bias dalam model dan analisis.
     
     <img width="175" alt="jumlah" src="https://github.com/user-attachments/assets/639b9c27-2887-4ec3-8679-298687549a1b">

2. **Visualisasi Distribusi Genre**:
   - Menggunakan `sns.countplot()` untuk memvisualisasikan distribusi genre film dalam dataset. Hal ini penting untuk memahami kategori mana yang paling umum dan yang mungkin perlu ditangani secara khusus dalam model rekomendasi. Dengan visualisasi ini, kita dapat dengan mudah melihat genre mana yang mendominasi dataset dan melakukan analisis lebih lanjut berdasarkan hasil tersebut
![countplot_2](https://github.com/user-attachments/assets/09ec764b-5cf8-4886-b6c6-d4d853ae23c7)

### Kesimpulan

Melalui tahapan Data Understanding dan Exploratory Data Analysis di atas, peneliti berhasil memahami struktur dan karakteristik dataset film. Proses ini membantu dalam mengidentifikasi langkah-langkah pra-pemrosesan yang diperlukan serta memberikan wawasan mengenai fitur-fitur yang paling berpengaruh dalam sistem rekomendasi film. Pemahaman mendalam terhadap data ini merupakan dasar yang kuat untuk pengembangan model rekomendasi yang akurat dan relevan.


## Data Preparation

Data preparation adalah langkah penting sebelum membangun model machine learning. Tujuannya adalah memastikan bahwa data siap untuk digunakan dalam proses pelatihan model dengan melakukan transformasi dan pemilihan fitur yang relevan. Dalam proyek ini, teknik-teknik data preparation yang telah dilakukan adalah sebagai berikut:

### 1. Mengisi Nilai Kosong
Kolom overview mungkin memiliki nilai kosong yang dapat mengganggu proses vectorization. Mengisi nilai kosong dengan string kosong memastikan bahwa semua film memiliki deskripsi yang dapat digunakan dalam perhitungan TF-IDF, sehingga tidak akan menghasilkan kesalahan saat pemodelan.
**Langkah**:
```python
df['overview'] = df['overview'].fillna('')
```
### 2. Menggunakan TF-IDF untuk Vectorizing Overview
Setelah mengisi nilai kosong, TF-IDF digunakan untuk mengonversi teks deskripsi film menjadi representasi numerik. Ini adalah langkah kunci untuk memungkinkan analisis berbasis konten, karena kita perlu membandingkan kemiripan antara deskripsi film menggunakan representasi matematis.
**Langkah**:
```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer(stop_words='english')
tfidf_matrix = tfidf.fit_transform(df['overview'])
```
### 3. Membuat Series untuk Memetakan Judul Film ke Indeks
Dengan membuat series yang memetakan judul film ke indeks, kita dapat dengan cepat menemukan indeks film berdasarkan judul. Ini penting untuk mengakses data dengan efisien saat melakukan rekomendasi.
**Langkah**:
```python
indices = pd.Series(df.index, index=df['title']).drop_duplicates()
```

### Kesimpulan
Dalam tahap data preparation untuk proyek sistem rekomendasi berbasis konten, beberapa langkah penting telah dilakukan untuk memastikan data siap digunakan dalam pemodelan. Pertama, nilai kosong dalam kolom overview diisi dengan string kosong untuk menghindari gangguan dalam proses vectorization. Hal ini memastikan bahwa semua film memiliki deskripsi yang dapat digunakan dalam perhitungan TF-IDF, sehingga mengurangi kemungkinan terjadinya kesalahan saat pemodelan.

Selanjutnya, TF-IDF digunakan untuk mengonversi deskripsi film menjadi representasi numerik. Langkah ini adalah kunci untuk analisis berbasis konten, karena memungkinkan perbandingan kemiripan antar film menggunakan representasi matematis yang dapat dihitung.

Terakhir, dibuatlah sebuah series yang memetakan judul film ke indeksnya. Langkah ini mempermudah dan mempercepat proses pencarian indeks film berdasarkan judul, yang sangat penting untuk mengakses data dengan efisien saat memberikan rekomendasi kepada pengguna. Secara keseluruhan, langkah-langkah yang dilakukan dalam data preparation telah membangun fondasi yang kuat untuk pengembangan model sistem rekomendasi yang efektif dan akurat.

## Modeling

Pada proyek ini, beberapa algoritma digunakan untuk membangun sistem rekomendasi film, baik berbasis konten maupun collaborative filtering. Tujuan dari tahapan ini adalah untuk memberikan rekomendasi film yang relevan kepada pengguna. Berikut adalah model-model yang digunakan beserta tahapan dan parameter yang diaplikasikan:

### 1. Nearest Neighbors
- **Tahapan**: 
  Nearest Neighbors digunakan untuk menemukan film yang paling mirip berdasarkan representasi numerik yang dihasilkan oleh TF-IDF (Term Frequency-Inverse Document Frequency) dari deskripsi film.
  - **Parameter utama**: Jumlah tetangga (K) dan metrik yang digunakan untuk menghitung jarak, biasanya jarak cosine.
  - **Scaling data**: Nearest neighbors sensitif terhadap skala fitur, tetapi dalam konteks ini, penggunaan representasi TF-IDF mengurangi kebutuhan akan scaling.

- **Kelebihan**: 
  - Implementasi yang sederhana dan hasil yang intuitif.
  - Sangat efektif untuk rekomendasi berbasis konten, terutama jika deskripsi film cukup mendetail.

- **Kekurangan**: 
  - Performa dapat menurun pada dataset yang sangat besar karena harus menghitung jarak antara semua data baru dan film yang ada.
  - Waktu komputasi bisa meningkat seiring dengan bertambahnya jumlah film dalam dataset.

### 2. Singular Value Decomposition (SVD)
- **Tahapan**:
  SVD digunakan sebagai metode untuk collaborative filtering yang menganalisis matriks pengguna-film untuk menemukan pola dalam data. Dengan mendekomposisi matriks menjadi beberapa matriks yang lebih kecil, SVD dapat menangkap hubungan antara pengguna dan film.
  - **Parameter utama**: Pengaturan jumlah faktor latennya, biasanya dioptimalkan menggunakan teknik cross-validation.
- **Kelebihan**: 
  - Memungkinkan rekomendasi yang lebih personal dengan mempertimbangkan preferensi pengguna yang sebelumnya.
  - Dapat menangani masalah sparsity dalam matriks pengguna-film dengan efektif.
- **Kekurangan**: 
  - Memerlukan data interaksi yang cukup untuk bekerja dengan baik.
  - Lebih kompleks dalam implementasi dibandingkan metode berbasis konten.

#### Evaluasi Model Nearest Neighbors
Berikut adalah hasil model Nearest Neighbors

```python
# Dapatkan rekomendasi untuk film 'Batman'
recommended_titles = get_recommendations('Batman')

# Hitung precision
precision = precision_at_k(recommended_titles, relevant_titles)

# Tampilkan hasil
print(f"Recommended Titles: {list(recommended_titles)}")
print(f"Precision: {precision:.2f}")
```
<img width="700" alt="precision_recommended" src="https://github.com/user-attachments/assets/7731df05-d5a1-4507-a29d-0d652871ddc5">

Hasil ini menunjukkan bagaimana model Nearest Neighbors menggunakan representasi TF-IDF dari film untuk merekomendasikan film yang dianggap mirip berdasarkan konten yang ada. Sehingga dapat disimpulkan bahwa Nearest Neighbors beroperasi dengan mendeteksi kemiripan antara film yang telah ditonton pengguna dan film lain dalam dataset berdasarkan fitur konten (seperti sinopsis, genre, dan kata kunci). Proses ini tidak mempertimbangkan preferensi pribadi pengguna, seperti sejarah penonton, rating individu, atau interaksi pengguna dengan film lain. Nearest Neighbors mengandalkan metrik jarak (seperti cosine similarity) untuk menentukan film mana yang mirip tanpa mempertimbangkan faktor-faktor yang lebih personal. Misalnya, dua pengguna mungkin memiliki kesamaan dalam film yang mereka tonton, tetapi preferensi mereka terhadap genre, sutradara, atau aktor tertentu mungkin berbeda. Nearest Neighbors tidak memperhitungkan perbedaan ini, yang dapat mengakibatkan rekomendasi yang kurang relevan.

Dalam konteks dataset yang lebih besar, film yang lebih populer cenderung memiliki lebih banyak data dan dapat memengaruhi rekomendasi. Film yang mirip mungkin diutamakan meskipun tidak relevan dengan preferensi individu pengguna. Ini dapat menyebabkan pengguna menerima rekomendasi film yang mungkin tidak sesuai dengan minat mereka. Nearest Neighbors tidak menggunakan umpan balik langsung dari pengguna untuk memperbarui model rekomendasi. Misalnya, jika pengguna memberikan rating tinggi pada film tertentu tetapi tidak menyukai film lain, Nearest Neighbors tidak dapat menyesuaikan rekomendasi untuk mencerminkan preferensi ini.

#### Evaluasi Model SVD
Model SVD dievaluasi menggunakan teknik cross-validation. Berikut adalah hasil evaluasi model menggunakan RMSE (Root Mean Square Error) dan MAE (Mean Absolute Error):

| Metode              | Fold 1 | Fold 2 | Fold 3 | Fold 4 | Fold 5 | Mean    | Std     |
|---------------------|--------|--------|--------|--------|--------|---------|---------|
| **RMSE (testset)**  | 0.8966 | 0.8938 | 0.9024 | 0.8944 | 0.8960 | 0.8966  | 0.0031  |
| **MAE (testset)**   | 0.6921 | 0.6889 | 0.6937 | 0.6886 | 0.6900 | 0.6906  | 0.0020  |
| **Fit time**        | 1.70   | 1.71   | 1.68   | 1.71   | 2.47   | 1.85    | 0.31    |
| **Test time**       | 0.17   | 0.16   | 0.13   | 0.36   | 0.22   | 0.21    | 0.08    |

<img width="277" alt="top_n_recommendations" src="https://github.com/user-attachments/assets/2491577c-66e4-4cba-93ed-1372017b2b0e">

Melalui evaluasi model, kita mendapatkan pemahaman yang lebih baik tentang akurasi model dalam memprediksi rating. RMSE dan MAE memberikan gambaran mengenai seberapa jauh prediksi kita dari nilai sebenarnya, menunjukkan efektivitas pendekatan collaborative filtering dalam memanfaatkan interaksi pengguna untuk memberikan rekomendasi.

Dengan melatih model pada seluruh dataset, kita dapat memanfaatkan informasi maksimal yang tersedia untuk meningkatkan akurasi prediksi. Prediksi rating untuk kombinasi pengguna dan film tertentu memberikan wawasan tentang bagaimana pengguna mungkin bereaksi terhadap film yang belum mereka tonton. Hal ini memungkinkan kita untuk memberikan rekomendasi yang lebih tepat dan personal.

### Pemilihan Model Terbaik
Setelah menerapkan kedua model di atas, model **SVD** dipilih sebagai model yang memberikan rekomendasi terbaik berdasarkan akurasi yang lebih tinggi dan kemampuannya untuk memberikan rekomendasi yang lebih personal dan relevan kepada pengguna.

Untuk memberikan rekomendasi kepada pengguna, model SVD memungkinkan kita untuk memprediksi rating film yang mungkin belum ditonton oleh pengguna berdasarkan preferensi yang telah ada sebelumnya. Dengan demikian, sistem rekomendasi ini dapat membantu pengguna menemukan film baru yang sesuai dengan selera mereka.

## Evaluation

## Model Content-Based Filtering

<img width="700" alt="precision_recommended" src="https://github.com/user-attachments/assets/7731df05-d5a1-4507-a29d-0d652871ddc5">

Pada proyek ini, model **Content-Based Filtering**  yang dikembangkan berfokus pada kasus rekomendasi dan menggunakan metrik **Precision**. **Precision** adalah metrik evaluasi yang digunakan untuk mengukur akurasi dari sistem rekomendasi, khususnya dalam konteks **content-based filtering**. Metrik ini membantu menilai seberapa relevan rekomendasi yang diberikan kepada pengguna dibandingkan dengan daftar item yang dianggap relevan.

### Definisi Precision
Precision dihitung dengan membagi jumlah item yang relevan yang direkomendasikan oleh model dengan jumlah total item yang direkomendasikan. Dalam istilah formal, rumus precision dapat dituliskan sebagai berikut:

$$\
\text{Precision} = \frac{\text{Jumlah item relevan yang direkomendasikan}}{\text{Total item yang direkomendasikan}}
\$$

### Penjelasan Metrik
1. **Jumlah item relevan yang direkomendasikan**: Ini adalah jumlah film (atau item) yang direkomendasikan oleh sistem yang juga dianggap relevan atau diinginkan oleh pengguna.
2. **Total item yang direkomendasikan**: Ini adalah jumlah total item yang direkomendasikan oleh sistem.

### Mengapa Precision Penting?
- **Relevansi**: Precision memberikan gambaran tentang relevansi rekomendasi yang diberikan kepada pengguna. Sistem dengan precision tinggi berarti sebagian besar rekomendasi yang diberikan adalah item yang memang ingin dilihat atau digunakan oleh pengguna.
- **Pengalaman Pengguna**: Dengan meningkatkan precision, pengalaman pengguna menjadi lebih baik karena mereka cenderung mendapatkan rekomendasi yang lebih sesuai dengan preferensi mereka.

### Contoh
Misalkan terdapat sistem rekomendasi yang merekomendasikan 10 film kepada pengguna, dan dari 10 film tersebut, 7 film ternyata relevan (pengguna menyukai film tersebut). Dalam hal ini, precision dihitung sebagai:

$$\
\text{Precision} = \frac{7}{10} = 0.7
\$$

Ini berarti bahwa 70% dari rekomendasi yang diberikan oleh sistem adalah relevan untuk pengguna.

### Precision dalam Content-Based Filtering
Dalam konteks **content-based filtering**, precision sangat berguna karena sistem ini merekomendasikan item berdasarkan kesamaan konten dengan item yang sebelumnya disukai oleh pengguna. Misalnya, jika pengguna menyukai film tertentu, sistem akan merekomendasikan film lain yang memiliki kesamaan dalam genre, aktor, atau tema.

Precision adalah metrik penting untuk mengevaluasi efektivitas sistem rekomendasi, terutama dalam **content-based filtering**. Metrik ini membantu memastikan bahwa rekomendasi yang diberikan benar-benar relevan dan sesuai dengan preferensi pengguna, yang pada akhirnya meningkatkan kepuasan pengguna terhadap sistem.

## Model Collaborative Filtering

Pada proyek ini, model **Collaborative Filtering** yang dikembangkan berfokus pada kasus rekomendasi dan menggunakan metrik evaluasi yang mencakup **Root Mean Square Error (RMSE)** dan **Mean Absolute Error (MAE)**. Hasil pengukuran performa model terbaik yang menggunakan algoritma **Singular Value Decomposition (SVD)** dapat dilihat pada tabel di bawah ini:

| Metrik              | Fold 1 | Fold 2 | Fold 3 | Fold 4 | Fold 5 | Mean    | Std     |
|---------------------|--------|--------|--------|--------|--------|---------|---------|
| **RMSE (testset)**  | 0.8966 | 0.8938 | 0.9024 | 0.8944 | 0.8960 | 0.8966  | 0.0031  |
| **MAE (testset)**   | 0.6921 | 0.6889 | 0.6937 | 0.6886 | 0.6900 | 0.6906  | 0.0020  |

<img width="277" alt="top_n_recommendations" src="https://github.com/user-attachments/assets/997c648b-42a7-4265-8398-b56bbf9e9103">

### Penjelasan Metrik

#### Root Mean Square Error (RMSE)
*RMSE* digunakan untuk mengukur seberapa jauh prediksi rating yang diberikan oleh model dari rating yang sebenarnya. Metrik ini memberikan informasi mengenai seberapa besar kesalahan model dalam memberikan rekomendasi.

<img width="261" alt="RMSE" src="https://github.com/user-attachments/assets/a39504f6-81b5-4a6a-8cff-f8bfd031f5cd">

#### Mean Absolute Error (MAE)
*MAE* mengukur kesalahan rata-rata antara nilai yang diprediksi dan nilai sebenarnya. Metrik ini membantu kita memahami rata-rata seberapa jauh model melakukan kesalahan.

<img width="235" alt="MAE" src="https://github.com/user-attachments/assets/803b7736-621c-4db1-bda2-b79cb1a71aa8">

#### Perbandingan antara MAE dan RMSE
- Sensitivitas terhadap Outlier: RMSE lebih sensitif terhadap outlier dibandingkan dengan MAE. Jika ada nilai yang jauh dari prediksi, RMSE akan memberikan penalti yang lebih besar.
- Interpretasi: MAE memberikan gambaran yang lebih jelas tentang kesalahan rata-rata dalam unit yang sama dengan data. RMSE, di sisi lain, mengukur kesalahan dalam unit kuadrat dan sering kali memberikan informasi tentang kesalahan yang lebih besar.
- Penggunaan: MAE lebih sering digunakan ketika kesalahan besar tidak terlalu penting, sedangkan RMSE lebih cocok digunakan ketika penalti untuk kesalahan besar perlu diperhitungkan.

### Hasil Evaluasi

Model yang dikembangkan dengan menggunakan **Content-Based Filtering** (Nearest Neighbors) dan **Collaborative Filtering** (SVD) berhasil menjawab problem statements yang telah dirumuskan. Dengan demikian, proyek ini mencapai beberapa tujuan yang telah ditetapkan.
Sistem rekomendasi film yang efektif telah dikembangkan dengan memanfaatkan kesamaan konten film. Melalui analisis deskripsi film dan atribut lainnya, model dapat menyarankan film berdasarkan apa yang telah ditonton pengguna sebelumnya. Rekomendasi yang diberikan telah terbukti relevan dan sesuai dengan preferensi pengguna, terutama dalam konteks film yang memiliki genre atau tema tertentu. Metrik evaluasi menunjukkan bahwa pengguna mendapatkan saran film yang sesuai dengan minat mereka. Evaluasi efektivitas antara **Content-Based Filtering** dan **Collaborative Filtering** berhasil dilakukan. Nearest Neighbors menunjukkan performa yang baik dalam merekomendasikan film berdasarkan kesamaan konten, sedangkan SVD menunjukkan kemampuannya dalam memahami pola preferensi pengguna yang lebih luas.

Sistem rekomendasi yang dibangun mampu memberikan saran film yang sesuai dengan preferensi pengguna, berdasarkan analisis konten dari film yang telah ditonton sebelumnya. Melalui analisis atribut film seperti genre, sinopsis, dan kata kunci, sistem berhasil menemukan film yang mirip dan relevan, meningkatkan pengalaman pengguna dalam menemukan film baru. Hasil perbandingan antara **Content-Based Filtering** dan **Collaborative Filtering** menunjukkan bahwa kedua pendekatan memiliki kelebihan masing-masing, sehingga memberikan wawasan berharga untuk pengembangan lebih lanjut.

Solusi yang diusulkan, yaitu penerapan Nearest Neighbors dan SVD, memberikan kontribusi signifikan terhadap efektivitas sistem rekomendasi. Pengguna mendapatkan rekomendasi yang lebih tepat dan personal, sesuai dengan preferensi mereka. Proses preprocessing yang dilakukan memastikan bahwa informasi yang digunakan dalam analisis akurat dan relevan. Ini membantu dalam meningkatkan kinerja model dan validitas hasil rekomendasi. Hasil evaluasi menunjukkan bahwa sistem rekomendasi yang dikembangkan dapat meningkatkan pengalaman pengguna dalam mencari film.

### Kesimpulan
Secara keseluruhan, evaluasi ini menunjukkan bahwa model yang dikembangkan berhasil menjawab problem statements, mencapai goals yang diharapkan, dan memberikan dampak positif sesuai dengan solusi statement yang diusulkan. Sistem rekomendasi film ini dapat menjadi alat yang efektif untuk meningkatkan pengalaman pengguna dalam menemukan film yang sesuai dengan preferensi mereka, serta memberikan nilai tambah bagi platform rekomendasi film.

---Ini adalah bagian akhir laporan---
