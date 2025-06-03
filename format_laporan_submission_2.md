# Laporan Proyek Machine Learning - M Wildan Nurohman

## Project Overview
### Latar Belakang

<img src="https://github.com/wildannrr/system-recomender_appliedML/blob/main/assets/bg.jpg" alt="Contoh Gambar" style="width:100%; height:auto;">

Perkembangan teknologi digital telah mengubah cara masyarakat mengakses informasi dan memperoleh pengetahuan. Salah satu dampak signifikan dari perubahan ini adalah meningkatnya popularitas kursus daring (online courses) sebagai alternatif pembelajaran formal dan informal. Platform seperti Udemy, Coursera, dan edX menyediakan ribuan kursus dari berbagai kategori, mulai dari pengembangan diri hingga kecerdasan buatan. Hal ini membuka peluang besar bagi siapa pun untuk belajar kapan saja dan di mana saja, tanpa batasan geografis maupun waktu [[1](https://www.sciencedirect.com/science/article/abs/pii/S0360131519302775?via%3Dihub)].

Namun, seiring dengan pertumbuhan jumlah kursus yang tersedia secara daring, muncul tantangan baru bagi pengguna, yaitu kesulitan dalam memilih kursus yang paling relevan dengan kebutuhan, tingkat kemampuan, dan preferensi pribadi mereka. Banyaknya pilihan sering kali menimbulkan kebingungan atau bahkan membuat pengguna merasa kewalahan [[2](https://www.solaresearch.org/wp-content/uploads/2017/05/chapter18.pdf)]. Oleh karena itu, dibutuhkan suatu sistem yang mampu merekomendasikan kursus secara personal berdasarkan data preferensi pengguna dan karakteristik kursus itu sendiri.

Sistem rekomendasi telah terbukti efektif dalam meningkatkan pengalaman pengguna dan mendorong keterlibatan yang lebih tinggi di berbagai platform digital seperti e-commerce dan media sosial. Dengan mengadopsi pendekatan yang serupa, sistem rekomendasi kursus daring dapat membantu pengguna menemukan materi pembelajaran yang sesuai dan relevan, sehingga proses belajar menjadi lebih efisien dan terarah [[3](https://www.learntechlib.org/primary/p/5822/)].

### Mengapa Proyek Ini Penting?
**1.Lonjakan Pertumbuhan Platform Pembelajaran Online**
Dalam beberapa tahun terakhir, platform kursus online seperti Dicoding, Coursera, Udemy, edX, dan lainnya mengalami pertumbuhan eksponensial. Ribuan kursus tersedia, menciptakan masalah information overload bagi pengguna yang kesulitan menemukan kursus yang paling relevan.

Menurut laporan Global Market Insights (2022) [[4](https://www.gminsights.com/industry-analysis/elearning-market-size)], pasar e-learning global diproyeksikan mencapai USD 1 triliun pada tahun 2028, menunjukkan besarnya kebutuhan akan sistem personalisasi yang efektif.

**2.Pentingnya Personalisasi dalam Pembelajaran**
Kurangnya personalisasi dalam sistem pembelajaran dapat menyebabkan rendahnya motivasi belajar, keterlibatan, dan retensi pengguna.

Penelitian oleh Li et al. (2010)[[5](https://icml.cc/Conferences/2009/papers/210.pdf)] menunjukkan bahwa sistem rekomendasi dapat meningkatkan kepuasan pengguna hingga 47% dan mempercepat proses pengambilan keputusan dalam memilih konten belajar.

**3. Mengatasi Masalah Cold-Start**
Sistem Content-Based Filtering tidak membutuhkan data historis dari pengguna seperti rating atau interaksi sebelumnya. Ini penting untuk mengatasi masalah cold-start, terutama untuk pengguna baru atau konten baru.

Menurut Aggarwal (2016)[[6](https://link.springer.com/book/10.1007/978-3-319-29659-3)], content-based filtering adalah salah satu solusi paling efektif untuk cold-start problem karena bergantung pada fitur eksplisit dari item, bukan perilaku pengguna.

### Hasil Riset dan Referensi Terkait
Terdapat 3 hasil riset dari berbagai studi dan platform, diantaranya : 
- Udemy Engineering Blog [[7](https://medium.com/udemy-engineering)]
- MOOCs Personalization Study [[8](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10597557)]
- Google Course Recommendation System [[9](https://developers.google.com/machine-learning/recommendation/overview?hl=id)]
  
| Studi / Platform                                    | Temuan                                                                                                                                      | Relevansi                                                                          |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Udemy Engineering Blog**                          | Menjelaskan bahwa mereka menggunakan model hibrida, tetapi CBF tetap krusial untuk cold-start dan filter awal berdasarkan deskripsi kursus. | Menunjukkan bahwa CBF digunakan di platform nyata.                                 |
| **MOOCs Personalization Study (Zhao et al., 2019)** | Rekomendasi personal meningkatkan engagement sebanyak **+20%** dibanding metode non-personalisasi.                                          | Mendukung pentingnya sistem rekomendasi untuk pengalaman pengguna yang lebih baik. |
| **Google Course Recommendation System**             | Menjelaskan penggunaan TF-IDF dan Cosine Similarity dalam pencocokan konten deskriptif kursus di awal interaksi.                            | Model yang digunakan dalam proyek ini mengikuti best practice industri.            |


## Business Understanding
Dalam beberapa tahun terakhir, industri e-learning telah mengalami pertumbuhan yang sangat pesat. Platform seperti Udemy menghadirkan ribuan kursus dari berbagai kategori, menjangkau jutaan pengguna di seluruh dunia. Namun, keberhasilan platform ini tidak hanya bergantung pada kuantitas kursus yang tersedia, tetapi juga pada kemampuan untuk menyajikan konten yang relevan dan tepat sasaran kepada pengguna.

Sebagian besar pengguna menghadapi tantangan dalam memilih kursus yang sesuai dengan minat, tujuan pembelajaran, dan tingkat keahlian mereka. Pengalaman pengguna yang buruk dalam proses pencarian kursus dapat menurunkan tingkat kepuasan, retensi, dan konversi. Di sisi lain, sistem rekomendasi yang baik dapat meningkatkan engagement, memperpanjang durasi kunjungan pengguna, bahkan mendorong pembelian lebih lanjut.

### Problem Statements
- Pengguna kesulitan menemukan kursus yang sesuai dengan minat, tingkat keterampilan, dan tujuan belajar mereka karena jumlah kursus yang sangat banyak
- Tidak semua kursus yang populer atau berperingkat tinggi relevan dengan kebutuhan spesifik setiap individu.
- Kurangnya sistem personalisasi menyebabkan pengalaman belajar yang kurang optimal dan meningkatkan kemungkinan pengguna meninggalkan platform.


### Goals
- Membangun sistem rekomendasi kursus berbasis kemiripan konten (content-based) dengan memanfaatkan fitur deskriptif dari kursus seperti judul, subjek, tingkat kesulitan, dan harga.
- Menyediakan daftar kursus alternatif yang mirip secara konten dengan kursus yang telah dipilih pengguna.
- Memberikan solusi yang dapat bekerja tanpa data interaksi pengguna, sehingga tetap relevan untuk kasus cold-start.

   

### **Solution Statements**

Untuk mencapai tujuan utama membangun sistem rekomendasi kursus yang relevan dan personal bagi pengguna, pendekatan utama akan diimplementasikan: **Content-Based Filtering**. Pendekatan akan dikembangkan untuk mengevaluasi efektivitasnya dalam konteks rekomendasi kursus berbasis data dari platform seperti Udemy.

#### **1. Content-Based Filtering**

Pendekatan Content-Based Filtering (CBF) mengandalkan informasi deskriptif dari kursus yang tersedia untuk menentukan kemiripan antar kursus. Sistem akan merekomendasikan kursus yang memiliki kemiripan fitur dengan kursus yang sebelumnya telah diikuti atau disukai oleh pengguna.[[10](https://link.springer.com/chapter/10.1007/978-0-387-85820-3_3)]

**Implementasi teknis:**

* Setiap kursus akan direpresentasikan dalam bentuk vektor fitur yang dibangun dari atribut seperti judul kursus, kategori, dan deskripsi.
* Representasi teks tersebut akan dikonversi menjadi vektor numerik menggunakan teknik **TF-IDF (Term Frequency–Inverse Document Frequency)**.
* Kemiripan antar kursus dihitung menggunakan **Cosine Similarity**, menghasilkan matriks kemiripan.
* Kursus yang memiliki skor kemiripan tinggi dengan kursus yang sudah diminati oleh pengguna akan direkomendasikan.

**Kelebihan:**

* Tidak bergantung pada data pengguna lain, sehingga cocok untuk sistem dengan jumlah pengguna terbatas.
* Dapat menjelaskan rekomendasi secara eksplisit berdasarkan fitur kursus.

**Keterbatasan:**

* Terjebak dalam "filter bubble", karena hanya merekomendasikan kursus yang mirip dengan preferensi sebelumnya.
* Kualitas rekomendasi sangat bergantung pada kelengkapan dan kejelasan deskripsi konten kursus.

---
#### **Keseluruhan** :

- Melakukan pembersihan dan eksplorasi data (EDA) untuk memahami distribusi dan kualitas data kursus.

- Menggabungkan fitur-fitur teks (course_title, subject, level, price) menjadi satu representasi string.

- Mengubah representasi teks menjadi vektor numerik menggunakan teknik TF-IDF Vectorization.

- Menghitung cosine similarity antar kursus berdasarkan vektor TF-IDF yang dihasilkan.

- Mengembangkan fungsi rekomendasi yang mengembalikan top-N kursus yang paling mirip dengan kursus tertentu berdasarkan skor kemiripan.

- Melakukan evaluasi kualitatif dan visualisasi untuk memahami relevansi hasil
---

## Data Understanding

Dataset yang digunakan dalam proyek ini merupakan kumpulan data kursus dari platform edukasi daring Udemy. Dataset ini berisi informasi seputar kursus online, termasuk topik, harga, tingkat kesulitan, serta jumlah peserta, Proses pengumpulan data dilakukan melalui tiga langkah utama:

- Mendownload dataset dari yang masih berupa zip di kaggle
- Mengekstrak isi file ZIP untuk mendapatkan file CSV secara lokal
- Mengupload file CSV ke google colab
- Membaca file CSV ke dalam bentuk DataFrame agar dapat dianalisis lebih lanjut.

#### Informasi Dataset : 
| Jenis       | Keterangan                                                                                                                                      |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| **Title**   | 👨‍🏫Udemy Courses✍🏻                                                                                                              |
| **Source**  | [Kaggle](https://www.kaggle.com/datasets/andrewmvd/udemy-courses)                                                              |
| **Maintainer** | [Andrewmvd](https://www.kaggle.com/andrewmvd)                                                                                     |                                 |
| **Visibility** | Publik                                                                                                                                       |
| **Tags**    | Education, Business, Online Comunitties, Tabular                                                                  |
| **Usability** | 10.00                                                                                                                                         |
  
Dataset ini berisi 3.678 entri dan 12 fitur, yang mereprentasikan : 

| Nama Kolom            | Tipe Data  | Deskripsi                                                            |
| --------------------- | ---------- | -------------------------------------------------------------------- |
| `course_id`           | Integer    | ID unik setiap kursus                                                |
| `title`               | String     | Judul kursus                                                         |
| `url`                 | String     | Tautan ke kursus di situs Udemy                                      |
| `is_paid`             | Boolean    | Status apakah kursus berbayar atau gratis                            |
| `price`               | String/Int | Harga kursus dalam USD                                               |
| `num_subscribers`     | Integer    | Jumlah pengguna yang mengikuti kursus                                |
| `num_reviews`         | Integer    | Jumlah ulasan pengguna terhadapkursus                               |
| `num_lectures`        | Integer    | Jumlah total video dalam kursus                                      |
| `level`               | String     | Tingkatan kursus (Beginner, Intermediate, Expert, All Levels)        |
| `content_duration`    | Float      | Durasi kursus dalam jam                                              |
| `published_timestamp` | Timestamp  | Tanggal kursus diterbitkan di platform                               |
| `subject`             | String     | Kategori utama/topik kursus (Business, Web Dev, Graphic Design, dll) |

## Exploratory Data Analysis (EDA)
Tahapan EDA telah dilakukan untuk mendapatkan wawasan mendalam tentang data:
1. **Distribusi Kategori Courses**
<p align="center">
  <img src="https://github.com/wildannrr/system-recomender_appliedML/blob/main/assets/distribusi%20berdasarkan%20kategori.png" alt="Gambar 1. Distribusi produk pada kategori utama" width="500"/>
</p>
<p align="center"><strong>Gambar 1.</strong> Distribusi Courses Berdasarkan Kategori</p>

- Web Development dan Business Finance adalah dua kategori dengan jumlah kursus terbanyak, masing-masing sekitar 1.200 kursus.

- Musical Instruments dan Graphic Design memiliki jumlah kursus yang jauh lebih sedikit, sekitar 600–700 kursus.

_Insight:_

Kategori Web Development dan Business Finance sangat dominan di platform ini, yang menunjukkan bahwa permintaan atau penawaran kursus dalam dua bidang ini sangat tinggi.

2. **Distribusi Tingkat Kesulitan Courses**
<p align="center">
  <img src="https://github.com/wildannrr/system-recomender_appliedML/blob/main/assets/distribusi%20berdsarkan%20tingkat%20kesulitan.png" alt="Gambar 2. Distribusi Courses berdasarkan Tingkat Kesulitan" width="500"/>
</p>
<p align="center"><strong>Gambar 2.</strong> Distribusi Courses Berdasarkan tingkat kesulitan</p>

- All Levels adalah tingkat kesulitan terbanyak, dengan hampir 2.000 kursus, menunjukkan bahwa banyak kursus dirancang untuk mencakup semua kalangan.

- Beginner Level berada di urutan kedua dengan sekitar 1.300 kursus.

- Intermediate Level cukup jauh lebih sedikit (~400 kursus).

- Expert Level sangat sedikit — hanya sekitar 50 kursus.

_Insight:_

Platform ini lebih fokus pada kursus untuk pemula atau yang mencakup semua level, sementara kursus dengan tingkat lanjut atau ahli sangat jarang. Ini bisa menunjukkan bahwa target audiens utama adalah pemula atau masyarakat umum.

3. **Distribusi Course Gratis vs Berbayar**
<p align="center">
  <img src="https://github.com/wildannrr/system-recomender_appliedML/blob/main/assets/berbayar%20vs%20gratis.png" alt="Gambar 3. Distribusi Course Gratis dan Berbayar" width="500"/>
</p>
<p align="center"><strong>Gambar 3.</strong> Distribusi Course Gratis dan Berbayar</p>

- Jumlah kursus berbayar (sekitar 3.500) jauh lebih banyak dibandingkan kursus gratis (sekitar 500).
- Kursus berbayar mendominasi, dengan rasio hampir 7:1 dibandingkan kursus gratis.
  
_Insight:_

Hal ini menunjukkan bahwa platform atau penyedia kursus lebih fokus pada model bisnis berbasis langganan atau pembayaran

4. **Distribusi Korelasi Antar Fitur Numerik**
<p align="center">
  <img src="https://github.com/wildannrr/system-recomender_appliedML/blob/main/assets/heatmap%20cor.png" alt="Gambar 4. Distribusi Korelasi Antar Fitur Numerik" width="500"/>
</p>
<p align="center"><strong>Gambar 4.</strong> Distribusi Korelasi Fitur Numerik</p>
Matriks korelasi ini menunjukkan hubungan antara variabel-variabel seperti jumlah subscribers, jumlah reviews, jumlah lectures, content, dan durasi pada "Heatmap Korelasi Fitur Numerik". Berikut beberapa insight berdasarkan matriks:

1. **Korelasi Tinggi**: 
   - Ada korelasi kuat (1.0) di diagonal utama, yang wajar karena setiap variabel memiliki korelasi sempurna dengan dirinya sendiri.
   - Korelasi tinggi (0.65) antara jumlah subscribers dan jumlah reviews menunjukkan bahwa semakin banyak subscribers, semakin banyak juga reviews yang diterima.

2. **Korelasi Sedang**:
   - Korelasi 0.8 antara jumlah lectures dan durasi menunjukkan hubungan positif yang cukup kuat, artinya semakin banyak lectures, semakin lama durasi keseluruhan.
   - Korelasi 0.65 antara jumlah lectures dan content juga menunjukkan hubungan positif, meskipun tidak sekuat dengan durasi.

3. **Korelasi Rendah**:
   - Korelasi antara content dan durasi (0.23) serta antara jumlah reviews dan jumlah lectures (0.24) menunjukkan hubungan yang lemah, menandakan bahwa variabel ini tidak terlalu saling bergantung.

4. **Korelasi Negatif atau Sangat Rendah**:
   - Nilai korelasi seperti 0.16 antara jumlah subscribers dan jumlah lectures atau durasi menunjukkan hubungan yang sangat lemah atau hampir tidak ada.

_Insight:_
Secara keseluruhan, matriks ini menunjukkan bahwa jumlah subscribers dan reviews memiliki hubungan yang lebih erat, sementara jumlah lectures lebih berkorelasi dengan durasi dan content.

## Data Preparation
Pada tahap ini, data disiapkan agar bisa digunakan dalam proses machine learning atau analisis lanjutan. Langkah-langkah yang dilakukan meliputi: data cleaning, seleksi fitur, penggabungan teks, dan vektorisasi teks menggunakan TF-IDF 

### Data Cleaning
Sebelum melakukan tahapan persiapan data yang lebih lanjut, beberapa langkah pembersihan data (data cleaning) telah dilakukan pada tahap Data Understanding untuk memastikan kualitas data. Tahapan ini meliputi:

1.  **Penanganan Missing Values:** Memeriksa dan menghapus data yg memiliki nilai NULL atau NAN, karena dataset ini tidak memiliki missing values, jadi tidak dilakukan proses pembersihan, hanya mengecek saja
2.  **Penanganan Data Duplikat:** Mengidentifikasi dan menghapus data yg memiliki duplikasi
3.  **Penanganan Data Tidak Relevan:** Terdapat beberapa data yang tidak relevan pada fitur `num_lecture` dan `num_subscriber`, yaitu nilainya 0. Keduanya tidak relevan karena tidak mungkin ada kursus tanpa konten dan tidak mungkin ada kursus berdurasi 0
   
1. Cek Missing Value :
   ```python
   df.isnull().sum()
   ```
   Output:
   
   ![image](https://github.com/user-attachments/assets/5794209a-6712-44a7-a02b-215908a288f3)

   _insight_ : Tidak terdapat missing value pada data ini

2. Penangan Data Duplikat :
   
   Identifikasi Data Duplikat, untuk menentukan proses penangan duplikasi data, apakah menghapusnya atau melakukan agregasi.

   ```python

   # Ambil semua baris yang dianggap duplikat
   duplikat = df[df.duplicated(keep=False)]
   
   # Cek apakah seluruh kolomnya identik
   identik = duplikat.groupby(list(df.columns)).size().reset_index(name='count')
   
   print(f"Jumlah grup baris duplikat unik (berdasarkan semua kolom): {len(identik)}")
   display(identik)
   ```
Ouput : 

![image](https://github.com/user-attachments/assets/377ab6b2-639d-4868-9cd2-429cc3e11df1)
_insight_: 
 Semua baris yang duplikat memiliki nilai yang sama persis di semua kolom (karena count: 2 pada setiap grup), artinya mereka duplikat secara penuh, dapat disimpulkan bahwa teknik lanjutan yg akan digunakan adalah .drop_duplicates()

Mengatasi Data Duplikat: 

```python
# Hapus baris duplikat
df = df.drop_duplicates()

# Cek data setelah penghapusan data duplikat
print("Jumlah baris setelah menghapus duplikat:", df.shape[0])
```
Output: 

Setelah proses penghapusan data duplikat dengan metode `.drop.duplicates()` , Jumlah data sekarang adalah 3672

3. Penangan Data Tidak Relevan :
   ```python
   # Hapus data yang tidak relevan
   df = df[df['content_duration'] > 0]
   df = df[df['num_lectures'] > 0]

   print("Jumlah baris dan kolom setelah pembersihan:", df.shape)
   ```
   Output :

   Setelah proses penghapusan data yang tidak relevan pada fitur `content_duration` dan `num_lectures`, Jumlah data sekarang adalah 3671
   
--- 

### Konversi published_timestamp menjadi datetime
```python
df['published_timestamp'] = pd.to_datetime(df['published_timestamp'])
```
**Mengapa diperlukan?**

- Format konsisten: Data timestamp dalam format string (object) yang tidak bisa diolah untuk analisis temporal

- Operasi waktu: Memungkinkan filtering berdasarkan tanggal, ekstraksi bulan/tahun, atau analisis tren waktu
  
### Penggabungan Fitur
Untuk model Content-Based Filtering yang akan menggunakan informasi tekstual produk, teks dari beberapa kolom yang relevan digabungkan menjadi satu kolom baru. Kolom yang digabungkan adalah `course_title`, `subject`, dan `level`. Hasil penggabungan disimpan dalam kolom `combined_features`. Selain itu, nilai-nilai yang mungkin hilang dalam kolom teks diisi dengan string kosong (`''`) untuk menghindari *error* saat pemrosesan teks.

```python
df['combined_features'] = df['course_title'] + ' ' + df['subject'] + ' ' + df['level']
```
**Mengapa diperlukan?**
*   Mengkonsolidasikan semua informasi tekstual yang relevan dari berbagai sumber ke dalam satu representasi.
*   Memudahkan proses vektorisasi teks selanjutnya menggunakan teknik seperti TF-IDF.

### Features Engineering : TF-IDF
```python
tfidf = TfidfVectorizer(stop_words='english')
tfidf_matrix = tfidf.fit_transform(df['combined_features'])
```
Penjelasan :


`stop_words='english'` : menghapus kata-kata umum seperti "the", "and", "of" dll , yang tidak memberi makna signifikan.

`fit_transform` : membangun dan mengaplikasikan model TF-IDF terhadap teks course_title.

**Mengapa Penting?**

- Mengubah data teks yang tidak terstruktur menjadi format numerik yang dapat diproses oleh algoritma machine learning.
- Menangkap pentingnya kata kunci dalam setiap produk, yang akan digunakan sebagai dasar untuk menghitung kemiripan konten antar produk.
  
## Modeling
### Content Based Filtering (CBF)
Content-based filtering adalah metode yang digunakan dalam sistem rekomendasi dan analisis data yang berfokus pada karakteristik atau konten dari item-item yang ingin direkomendasikan atau dianalisis. Pendekatan ini menggunakan atribut-atribut atau fitur-fitur item untuk menentukan kesamaan antara item yang ada dan preferensi pengguna. Dalam konteks rekomendasi, content-based filtering berusaha untuk merekomendasikan item yang mirip dengan item yang telah disukai oleh pengguna berdasarkan karakteristik konten [[11](https://dqlab.id/content-based-filtering-dalam-algoritma-data-science)].

Tahapan : 
1. Menghitung kemiripan menggunakan cosine_similiarity

     
```python
cosine_sim = cosine_similarity(tfidf_matrix, tfidf_matrix)
cosine_sim
```

   Alasan :
   Saya memilih cosine similarity karena metrik ini paling cocok untuk mengukur kemiripan antar dokumen berbasis vektor TF-IDF. Cosine similarity menilai kemiripan arah antar vektor,    bukan panjangnya, sehingga cocok untuk teks.


**_Bagaimana cara kerjanya?_**

   Setiap dokumen direpresentasikan sebagai vektor dalam ruang multidimensi (dimana setiap dimensi adalah kata unik). Cosine similarity menghitung kosine dari sudut antara dua vektor. Nilai cosine similarity berkisar antara -1 hingga 1:
   
   - 1: Menunjukkan bahwa kedua vektor (dokumen) sangat mirip atau identik. Sudut antara mereka adalah 0 derajat.
   
   - 0: Menunjukkan bahwa kedua vektor (dokumen) tidak terkait sama sekali atau ortogonal. Sudut antara mereka adalah 90 derajat.
   
   - -1: Menunjukkan bahwa kedua vektor (dokumen) sangat berlawanan. Sudut antara mereka adalah 180 derajat.

Output : 

![image](https://github.com/user-attachments/assets/c1b32d67-14d6-47aa-ad94-3961a216424b)

2. Buat Mapping dari Index ke Judul
   ```python
   indices = pd.Series(df.index, index=df['course_title']).drop_duplicates()

   def recommend_courses(title, cosine_sim=cosine_sim, df=df, indices=indices):
    if title not in indices:
        return f"Kursus '{title}' tidak ditemukan."

    idx = indices[title]
    sim_scores = list(enumerate(cosine_sim[idx]))
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)
    sim_scores = sim_scores[1:6]  # Ambil 5 teratas setelah dirinya sendiri
    course_indices = [i[0] for i in sim_scores]

    return df[['course_title', 'subject', 'level', 'price']].iloc[course_indices]
    
   ```

Penjelasan :

![image](https://github.com/user-attachments/assets/273ddc9a-6ba4-49d7-ac92-f8cee806e0d2)


Kode ini diperlukan untuk:

* Membangun sistem rekomendasi berbasis konten (content-based filtering).
* Menyediakan hasil yang cepat, relevan, dan bisa digunakan langsung oleh pengguna.
* Dibuat modular dan efisien untuk **penggunaan berulang**, integrasi ke produk nyata, dan skalabilitas.

### Model Testing
Test 1 : 

```python
course_title = "Introduction to Forex Trading Business For Beginners"

# Ambil indeksnya
idx = df[df['course_title'] == course_title].index[0]

# Ambil skor similarity terhadap semua kursus
sim_scores = list(enumerate(cosine_sim[idx]))

# Mengurutkan dari yang paling mirip
sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)

# Ambil top 10 (kecuali course itu sendiri)
top_courses = [i[0] for i in sim_scores[1:11]]
df[['course_title', 'subject', 'price']].iloc[top_courses]
```
Output : 

![image](https://github.com/user-attachments/assets/1c390607-d3c1-48fa-8957-355c2e1329e0)

Penjelasan : 



- **Konsistensi Subjek**

  - 100% course berada dalam kategori "Business Finance"
  - Menunjukkan sistem berhasil mengidentifikasi kesamaan topik
  Content-based filtering bekerja dengan baik

- **Fokus Tema Trading/Forex**

  Course diurutkan berdasarkan relevansi:

  - Forex Trading (5 course) - Tema paling dominan
  - General Trading (3 course) - Tema yang lebih luas
  - Cryptocurrency/Bitcoin (1 course) - Variasi dalam finance
  - Day Trading (1 course) - Spesialisasi trading

- **Level Pembelajaran**

  - 8 course mengandung kata "Beginners" atau "Introduction"
  - 1 course level "Intermediate"
  - 1 course lebih spesifik (Day Trading)

- **Distribusi Harga**

  - FREE (0):     40% (4 course)
  - Low (20-50):  40% (4 course)  
  - High (95-150): 20% (2 course)

  _Insight_: Mayoritas rekomendasi terjangkau untuk pemula.

**Kualitas Similarity Ranking**
  Urutan menunjukkan tingkat kesamaan:

  - Exact match: "Forex Trading For Beginners"
  - Very similar: "Forex for Beginners: Easy Forex Trading..."
  - Topic variation: "Forex Trading" (tanpa beginners)
  - Gradual expansion: Trading → Day Trading → Bitcoin

Test 2 : 

```python
# Ambil indeks kursus berdasarkan judul
course_title = "Introduction to Forex Trading Business For Beginners"
idx = df[df['course_title'] == course_title].index[0]

# Ambil semua skor cosine similarity terhadap kursus ini
sim_scores = list(enumerate(cosine_sim[idx]))

# Urutkan dari skor tertinggi ke rendah
sim_scores_sorted = sorted(sim_scores, key=lambda x: x[1], reverse=True)

# Konversi ke DataFrame untuk tampilan yang rapi
similarity_df = pd.DataFrame([
    {
        'Course': df.iloc[i]['course_title'],
        'Similarity Score': score
    }
    for i, score in sim_scores_sorted
])

# Tampilkan top 10 hasil (kecuali dirinya sendiri di baris pertama)
similarity_df.iloc[1:11]
```

Output : 

![image](https://github.com/user-attachments/assets/f9a2aa32-37e0-43b1-8163-8975ab1df42f)


Penjelasan : 

_**Interpretasi Similarity Scores:**_

  - Rentang Skor (0.61 - 0.85)
  - Skala: 0-1 (dimana 1 = identik sempurna)
  - Range: 0.6105 - 0.8514
  - Kualitas: Semua skor di atas 0.6 menunjukkan similarity - yang baik

_**Distribusi Tingkat Kesamaan:**_

🔴 Very High Similarity (0.80+)
  - Course #1: "Forex Trading For Beginners" - 0.851

    Hampir identik dengan input course



  🟡 High Similarity (0.70-0.79)

  - Course #2: "Forex for Beginners: Easy Forex Trading..." - 0.736

    Sangat mirip, variasi kata kunci



  🟢 Good Similarity (0.65-0.69)

  - Course #3: "Forex Trading" - 0.695
  - Course #4: "Forex Trading For Beginners: Technical..." - 0.692
  - Course #5: "Forex Trading for Beginners - Basics" - 0.672

🔵 Moderate Similarity (0.60-0.64)

  - Course #6-10: Skor 0.610-0.650

    Masih relevan tapi lebih general (trading vs forex spesifik)

**Menghitung akurasi kemiripan antar Courses dengan :**

```python
idx_A = df[df['course_title'] == "Forex Trading"].index[0]
idx_B = df[df['course_title'] == "Introduction to Bitcoin for Beginners"].index[0]

similarity_score = cosine_sim[idx_A][idx_B]
print(f"Similarity Score between Forex Trading and Introduction to Bitcoin for Beginners : {similarity_score}")

```
Penjelasan: 

- idx: Mendapatkan index baris dari kursus yang dicari.

- `enumerate(cosine_sim[idx])`: Mengambil skor kemiripan antara kursus tersebut dan seluruh kursus lainnya.
  
Output : 

![image](https://github.com/user-attachments/assets/e8618c6f-0367-4388-ae97-77e27c228103)

## Evaluasi dan Visualisasi

**Melihat Rekomendasi Kursus berdasarkan Kursus Tertentu**
```python
# Fungsi menampilkan rekomendasi
def show_recommendations(idx, top_n=5):
    course_title = df.iloc[idx]['course_title']
    print(f"\nKursus acuan: '{course_title}'\n")

    # Ambil indeks dan skor kemiripan tertinggi
    similarity_scores = cosine_sim[idx]
    top_indices = similarity_scores.argsort()[::-1][1:top_n+1]  # urutkan dan ambil top-n, skip index pertama

    print("Rekomendasi:")
    for i in top_indices:
        print(f"  - {df.iloc[i]['course_title']} (Score: {similarity_scores[i]:.4f})")

```
Penjelasan : 


- `def show_recommendations(idx, top_n=5):`
  - `idx`: Index course yang akan dicari rekomendasinya
  - `top_n`: Jumlah rekomendasi yang ingin ditampilkan (default 5)

- `course_title = df.iloc[idx]['course_title']` : Mengambil judul course berdasarkan index

- `print(f"\nKursus acuan: '{course_title}'\n")` : Menampilkan course yang dijadikan acuan untuk rekomendasi

- `similarity_scores = cosine_sim[idx]
top_indices = similarity_scores.argsort()[::-1][1:top_n+1]` :
  - `cosine_sim[idx]`: Mengambil baris similarity matrix untuk course ke-idx
  - `argsort()`: Mengurutkan index berdasarkan nilai similarity (ascending)
  - `[::-1]` : Membalik urutan jadi descending (tertinggi dulu)
  - `[1:top_n+1] `: Skip index pertama (course itu sendiri), ambil top_n selanjutnya

- `for i in top_indices:
    print(f"- {df.iloc[i]['course_title']} (Score: {similarity_scores[i]:.4f})")`
    - Loop untuk setiap course yang direkomendasikan
    - Menampilkan judul course dan similarity score dengan 4 desimal

**Tampilkan rekomendasi kursus index ke-3 dengan 5 rekomendasi kursus**
```python
show_recommendations(3, top_n=5)
```
Output : 

![image](https://github.com/user-attachments/assets/65143f1a-2aa3-48d4-8eb2-30e7af4abbf6)

Penjelasan : 

  - "Excel Crash Course: Master Excel for Financial Analysis" - Score: 0.6219

    - Relevansi Tinggi: Excel + Financial Analysis (exact match)
    Target: Lebih spesifik ke Excel mastery


  - "Beginner to Pro in Excel: Financial Modeling and Valuation" - Score: 0.6009

    - Relevansi Sangat Tinggi: "Beginner to Pro" + Excel + Financial
    - Progression: From same series, level lanjutan


  - "Stock Technical Analysis with Excel" - Score: 0.5088

    - Relevansi Sedang: Excel + Financial analysis (stocks)
    - Spesialisasi: Fokus ke technical analysis


  - "Stock Fundamental Analysis with Excel" - Score: 0.4808

    - Relevansi Sedang: Excel + Financial analysis (fundamental)
    - Complement: Pasangan dengan technical analysis


  - "Building Financial Statements in Excel" - Score: 0.4731

    - Relevansi Sedang: Excel + Financial statements
    - Foundational: Skill dasar untuk financial analysis

**Visualisasi kesamaan antar fitur berdasarkan cosine similiarity**
![image](https://github.com/user-attachments/assets/ee378ca2-98db-49f1-8a5b-42391c8aa041)

Penjelasan:

_**Cluster Analysis:**_

🔵 Finance/Investment Cluster:

  - "Beginner to Pro - Financial Analysis in Excel 2017" dengan "Financial Modeling for Business Analysts" → 0.18
  - "Ultimate Investment Banking Course" dengan "The Only Investment Strategy..." → 0.30
  Menunjukkan courses dengan topik serupa memiliki similarity lebih tinggi

🟢 Trading Cluster:

  - "How To Maximize Your Profits Trading Options" dengan "Options Trading 3: Advanced..." → 0.23
  - "Trading Penny Stocks" dengan "Trading Stock Chart Patterns" → 0.12
  Trading courses saling terkait tapi dengan specialization berbeda

_**Pola Similarity:**_


- Similarity Tinggi (>0.20):

  - Excel 2017 ↔ Trading Penny Stocks: 0.29 (karena analytical approach)
  - Ultimate Investment ↔ Investment Strategy: 0.30 (topik investasi serupa)
  - Options Trading courses: 0.23 (spesialisasi sama)

- Similarity Rendah (<0.10):

  - GST Course ↔ Most others: 0.03-0.07 (topik sangat berbeda - tax vs finance)
  -Banking ↔ Trading: 0.05-0.08 (domain berbeda dalam finance)

_**Course Positioning:**_

  Most Similar Courses:

- Investment-focused courses (0.30 max similarity)
- Options trading specialization (0.23)
- Excel-based analysis (0.29 with penny stocks)


## **KESIMPULAN**

Dalam proyek ini, telah dikembangkan sebuah sistem rekomendasi kursus berbasis Content-Based Filtering (CBF) menggunakan pendekatan cosine similarity terhadap fitur deskriptif dari kursus, khususnya course_title. Sistem ini dirancang untuk menjawab beberapa permasalahan utama yang dihadapi pengguna dalam menemukan kursus yang relevan di tengah banyaknya pilihan yang tersedia.

### **Pencapaian Terhadap Problem Statements**
**1. Kesulitan menemukan kursus sesuai minat dan kebutuhan**
→ Sistem CBF berhasil mengidentifikasi kursus-kursus yang memiliki kemiripan konten dengan kursus yang dipilih pengguna, sehingga mempermudah pencarian yang relevan dengan minat dan tujuan belajar individu.

**2. Kursus populer belum tentu relevan untuk semua orang**
→ Dengan menekankan kemiripan isi daripada popularitas, sistem ini merekomendasikan kursus berdasarkan konten yang serupa, bukan berdasarkan rating atau jumlah peserta, sehingga lebih personal.

**3. Kurangnya personalisasi dalam platform kursus**
→ Sistem ini menghadirkan pengalaman belajar yang lebih terpersonalisasi dengan memberikan daftar rekomendasi yang mirip secara semantik, meningkatkan relevansi dan kemungkinan keterlibatan pengguna.

### **Pencapaian Terhadap Goals**
**1.Pembangunan sistem berbasis konten**
→ Fitur seperti judul kursus digunakan untuk membentuk representasi vektor TF-IDF, yang kemudian dihitung kemiripannya dengan cosine similarity untuk membangun sistem rekomendasi.

**2.Menyediakan daftar kursus alternatif yang mirip**
→ Fungsi recommend_courses() berhasil menghasilkan rekomendasi top-5 yang kontennya paling mirip dengan kursus input pengguna.

**3.Solusi tanpa data interaksi pengguna (cold-start)**
→ Sistem ini tidak bergantung pada data user_id atau rating, sehingga sangat cocok untuk diterapkan dalam skenario cold-start ketika data interaksi pengguna masih terbatas atau belum tersedia.

### **Kesimpulan Visualisasi**
Visualisasi heatmap cosine similarity memberikan gambaran kuantitatif tentang hubungan antar kursus, membantu memverifikasi bahwa kursus dengan topik serupa memang memiliki skor kemiripan tinggi. Hal ini membuktikan bahwa metode yang digunakan telah bekerja secara logis dan sesuai dengan tujuan proyek.


## Referensi
[1] Hew, K. F., Hu, X., Qiao, C., & Tang, Y. (2020). What predicts student satisfaction with MOOCs: A gradient boosting trees supervised machine learning and sentiment analysis approach. Computers & Education, 145, 103724. https://doi.org/10.1016/j.compedu.2019.103724

[2] Kizilcec, R. F., & Brooks, C. (2017). Diverse Big Data and Randomized Field Experiments in MOOCs. In C. Lang, G. Siemens, A. Wise, & D. Gašević (Eds.), The Handbook of Learning Analytics (pp. 269–278). Society for Learning Analytics Research (SoLAR).

[3] Tang, T., & McCalla, G. (2005). Smart recommendation for an evolving e-learning system. International Journal on E-learning, 4(1), 105–129.

[4] Global Market Insights. (2023). Recommender system market size. Retrieved June 3, 2025, from https://www.gminsights.com/industry-analysis/elearning-market-size

[5] Li, Q., Yang, Q., & Xue, X. (2010). Transfer learning for collaborative filtering via a rating-matrix generative model. Proceedings of the 27th International Conference on Machine Learning (ICML-10), 617–624.

[6] Aggarwal, C. C. (2016). Recommender systems: The textbook. Springer.

[7] Udemy Engineering. (2021, July 15). How Udemy uses hybrid recommendation systems to personalize learning. Udemy Tech Blog from https://medium.com/udemy-engineering

[8] Zhao, Y., Xu, G., & Zhang, Y. (2019). Personalized recommendation in massive open online courses with probabilistic matrix factorization. IEEE Access, 7, 97499–97511.

[9] Google Developers. (n.d.). Recommending courses using text similarity. Google Developer Guides. https://developers.google.com/machine-learning/recommendation/overview

[10] Lops, P., de Gemmis, M., Semeraro, G. (2011). Content-based Recommender Systems: State of the Art and Trends. In: Ricci, F., Rokach, L., Shapira, B., Kantor, P. (eds) Recommender Systems Handbook. Springer, Boston, MA. https://doi.org/10.1007/978-0-387-85820-3_3

[11] DQLab, “Content-Based Filtering dalam Algoritma Data Science,” DQLab, [Online]. Available: https://dqlab.id/content-based-filtering-dalam-algoritma-data-science. [Accessed: 27-May-2025].
