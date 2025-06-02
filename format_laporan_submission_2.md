# Laporan Proyek Machine Learning - Nama Anda

## Project Overview
### Latar Belakan

<img src="" alt="Contoh Gambar" style="width:100%; height:auto;">

Perkembangan teknologi digital telah mengubah cara masyarakat mengakses informasi dan memperoleh pengetahuan. Salah satu dampak signifikan dari perubahan ini adalah meningkatnya popularitas kursus daring (online courses) sebagai alternatif pembelajaran formal dan informal. Platform seperti Udemy, Coursera, dan edX menyediakan ribuan kursus dari berbagai kategori, mulai dari pengembangan diri hingga kecerdasan buatan. Hal ini membuka peluang besar bagi siapa pun untuk belajar kapan saja dan di mana saja, tanpa batasan geografis maupun waktu (Hew, Hu, Qiao, & Tang, 2020).

Namun, seiring dengan pertumbuhan jumlah kursus yang tersedia secara daring, muncul tantangan baru bagi pengguna, yaitu kesulitan dalam memilih kursus yang paling relevan dengan kebutuhan, tingkat kemampuan, dan preferensi pribadi mereka. Banyaknya pilihan sering kali menimbulkan kebingungan atau bahkan membuat pengguna merasa kewalahan (Kizilcec & Brooks, 2017). Oleh karena itu, dibutuhkan suatu sistem yang mampu merekomendasikan kursus secara personal berdasarkan data preferensi pengguna dan karakteristik kursus itu sendiri.

Sistem rekomendasi telah terbukti efektif dalam meningkatkan pengalaman pengguna dan mendorong keterlibatan yang lebih tinggi di berbagai platform digital seperti e-commerce dan media sosial. Dengan mengadopsi pendekatan yang serupa, sistem rekomendasi kursus daring dapat membantu pengguna menemukan materi pembelajaran yang sesuai dan relevan, sehingga proses belajar menjadi lebih efisien dan terarah (Tang & McCalla, 2005).

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa dan bagaimana masalah tersebut harus diselesaikan
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
- Format Referensi dapat mengacu pada penulisan sitasi [IEEE](https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf), [APA](https://www.mendeley.com/guides/apa-citation-guide/) atau secara umum seperti [di sini](https://penerbitdeepublish.com/menulis-buku-membuat-sitasi-dengan-mudah/)
- Sumber yang bisa digunakan [Scholar](https://scholar.google.com/)

## Business Understanding

Industri e-learning seperti Udemy mengalami pertumbuhan pesat dengan menawarkan ribuan kursus daring dari berbagai bidang. Namun, tantangan utama yang dihadapi adalah bagaimana membantu pengguna menemukan kursus yang paling relevan dengan kebutuhan, minat, dan tingkat keahlian mereka. Tanpa sistem rekomendasi yang efektif, pengguna dapat merasa kewalahan oleh banyaknya pilihan yang tersedia, yang berdampak pada rendahnya kepuasan dan retensi pengguna. Proyek ini bertujuan untuk membangun sistem rekomendasi berbasis data guna meningkatkan relevansi saran kursus, mendorong keterlibatan pengguna, mempercepat proses pengambilan keputusan pembelajaran, serta memberikan nilai tambah bisnis berupa peningkatan konversi dan loyalitas pengguna terhadap platform.
Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pengguna kesulitan menemukan kursus yang sesuai dengan minat, tingkat keterampilan, dan tujuan belajar mereka karena jumlah kursus yang sangat banyak
- Tidak semua kursus yang populer atau berperingkat tinggi relevan dengan kebutuhan spesifik setiap individu.
- Kurangnya sistem personalisasi menyebabkan pengalaman belajar yang kurang optimal dan meningkatkan kemungkinan pengguna meninggalkan platform.


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
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

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
