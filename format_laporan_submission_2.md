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
| `num_reviews`         | Integer    | Jumlah ulasan pengguna terhadap kursus                               |
| `num_lectures`        | Integer    | Jumlah total video dalam kursus                                      |
| `level`               | String     | Tingkatan kursus (Beginner, Intermediate, Expert, All Levels)        |
| `content_duration`    | Float      | Durasi kursus dalam jam                                              |
| `published_timestamp` | Timestamp  | Tanggal kursus diterbitkan di platform                               |
| `subject`             | String     | Kategori utama/topik kursus (Business, Web Dev, Graphic Design, dll) |

## Exploratory Data Analysis (EDA)



## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

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
