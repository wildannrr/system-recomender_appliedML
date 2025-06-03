# Laporan Proyek Machine Learning - M Wildan Nurohman

## Project Overview
### Latar Belakang

<img src="https://github.com/wildannrr/system-recomender_appliedML/blob/main/assets/bg.jpg" alt="Contoh Gambar" style="width:100%; height:auto;">

Perkembangan teknologi digital telah mengubah cara masyarakat mengakses informasi dan memperoleh pengetahuan. Salah satu dampak signifikan dari perubahan ini adalah meningkatnya popularitas kursus daring (online courses) sebagai alternatif pembelajaran formal dan informal. Platform seperti Udemy, Coursera, dan edX menyediakan ribuan kursus dari berbagai kategori, mulai dari pengembangan diri hingga kecerdasan buatan. Hal ini membuka peluang besar bagi siapa pun untuk belajar kapan saja dan di mana saja, tanpa batasan geografis maupun waktu [[1](https://www.sciencedirect.com/science/article/abs/pii/S0360131519302775?via%3Dihub)].

Namun, seiring dengan pertumbuhan jumlah kursus yang tersedia secara daring, muncul tantangan baru bagi pengguna, yaitu kesulitan dalam memilih kursus yang paling relevan dengan kebutuhan, tingkat kemampuan, dan preferensi pribadi mereka. Banyaknya pilihan sering kali menimbulkan kebingungan atau bahkan membuat pengguna merasa kewalahan [[2](https://www.solaresearch.org/wp-content/uploads/2017/05/chapter18.pdf)]. Oleh karena itu, dibutuhkan suatu sistem yang mampu merekomendasikan kursus secara personal berdasarkan data preferensi pengguna dan karakteristik kursus itu sendiri.

Sistem rekomendasi telah terbukti efektif dalam meningkatkan pengalaman pengguna dan mendorong keterlibatan yang lebih tinggi di berbagai platform digital seperti e-commerce dan media sosial. Dengan mengadopsi pendekatan yang serupa, sistem rekomendasi kursus daring dapat membantu pengguna menemukan materi pembelajaran yang sesuai dan relevan, sehingga proses belajar menjadi lebih efisien dan terarah [[3](https://www.learntechlib.org/primary/p/5822/)].

## Business Understanding
Industri e-learning global mengalami pertumbuhan pesat dalam beberapa tahun terakhir, terutama didorong oleh meningkatnya kebutuhan masyarakat untuk belajar secara fleksibel dan mandiri. Salah satu platform terbesar, Udemy, menawarkan ribuan kursus daring yang mencakup berbagai bidang keahlian. Namun, seiring bertambahnya jumlah kursus, pengguna semakin kesulitan menemukan materi yang sesuai dengan minat, tingkat kemampuan, dan tujuan belajarnya. Jika tidak ditangani, permasalahan ini dapat menurunkan keterlibatan pengguna, memperbesar risiko churn, dan menghambat efektivitas pembelajaran (Kizilcec & Brooks, 2017). Oleh karena itu, dibutuhkan sistem rekomendasi berbasis data yang mampu menyajikan pilihan kursus secara personal dan relevan. Sistem ini dapat dibangun dengan pendekatan seperti content-based filtering maupun collaborative filtering, untuk memberikan saran kursus berdasarkan karakteristik kursus dan perilaku pengguna sebelumnya. Implementasi solusi ini diyakini dapat meningkatkan kepuasan pengguna, mempercepat pengambilan keputusan belajar, serta memberikan keunggulan kompetitif bagi penyedia platform e-learning (Tang & McCalla, 2005).


### Problem Statements
- Pengguna kesulitan menemukan kursus yang sesuai dengan minat, tingkat keterampilan, dan tujuan belajar mereka karena jumlah kursus yang sangat banyak
- Tidak semua kursus yang populer atau berperingkat tinggi relevan dengan kebutuhan spesifik setiap individu.
- Kurangnya sistem personalisasi menyebabkan pengalaman belajar yang kurang optimal dan meningkatkan kemungkinan pengguna meninggalkan platform.


### Goals
- Membangun sistem rekomendasi kursus berbasis kemiripan konten (content-based) dengan memanfaatkan fitur deskriptif dari kursus seperti judul, subjek, tingkat kesulitan, dan harga.
- Menyediakan daftar kursus alternatif yang mirip secara konten dengan kursus yang telah dipilih pengguna.
- Memberikan solusi yang dapat bekerja tanpa data interaksi pengguna, sehingga tetap relevan untuk kasus cold-start.

   

### **Solution Statements**

Untuk mencapai tujuan utama membangun sistem rekomendasi kursus yang relevan dan personal bagi pengguna, dua pendekatan utama akan diimplementasikan: **Content-Based Filtering**. Pendekatan akan dikembangkan untuk mengevaluasi efektivitasnya dalam konteks rekomendasi kursus berbasis data dari platform seperti Udemy.

#### **1. Content-Based Filtering**

Pendekatan Content-Based Filtering (CBF) mengandalkan informasi deskriptif dari kursus yang tersedia untuk menentukan kemiripan antar kursus. Sistem akan merekomendasikan kursus yang memiliki kemiripan fitur dengan kursus yang sebelumnya telah diikuti atau disukai oleh pengguna.

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

> Referensi: Lops, P., de Gemmis, M., & Semeraro, G. (2011). Content-based recommender systems: State of the art and trends. *Recommender Systems Handbook*, 73–105. [https://doi.org/10.1007/978-0-387-85820-3\_3](https://doi.org/10.1007/978-0-387-85820-3_3)

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
Content-based filtering adalah metode yang digunakan dalam sistem rekomendasi dan analisis data yang berfokus pada karakteristik atau konten dari item-item yang ingin direkomendasikan atau dianalisis. Pendekatan ini menggunakan atribut-atribut atau fitur-fitur item untuk menentukan kesamaan antara item yang ada dan preferensi pengguna. Dalam konteks rekomendasi, content-based filtering berusaha untuk merekomendasikan item yang mirip dengan item yang telah disukai oleh pengguna berdasarkan karakteristik konten [[4](https://dqlab.id/content-based-filtering-dalam-algoritma-data-science)].

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

   `indices = pd.Series(df.index, index=df['course_title']).drop_duplicates()` :
   Membuat pemetaan dari nama course ke posisi index dalam DataFrame, dan melakukan drop jika ada course title yang sama

   `def recommend_courses(title, cosine_sim=cosine_sim, df=df, indices=indices):` :
   Membuat fungsi modular agar bisa memanggil rekomendasi berdasarkan input nama kursus, tanpa menulis ulang semua proses.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
