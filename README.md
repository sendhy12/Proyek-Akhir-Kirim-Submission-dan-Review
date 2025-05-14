# Laporan Proyek Machine Learning - Sendhy Maula Ammarulloh

## Project Overview

Pariwisata merupakan sektor strategis yang memiliki kontribusi signifikan terhadap pertumbuhan ekonomi nasional di Indonesia. Sebagai negara kepulauan dengan keanekaragaman budaya, alam, dan sejarah, Indonesia memiliki potensi wisata yang sangat besar untuk dikembangkan \[1]. Berdasarkan data dari Badan Pusat Statistik (BPS) Bali, pada bulan April 2023, jumlah kunjungan wisatawan ke Bali mencapai 411.510, meningkat sebesar 11,01% dibandingkan bulan sebelumnya \[2]. Peningkatan tersebut menegaskan pentingnya optimalisasi sektor pariwisata melalui pendekatan yang adaptif terhadap perkembangan teknologi digital.

Salah satu pendekatan yang relevan untuk mendukung pengembangan sektor ini adalah penerapan **sistem rekomendasi berbasis machine learning**. Sistem ini bertujuan untuk menyajikan rekomendasi destinasi wisata yang dipersonalisasi sesuai preferensi pengguna, baik lokal maupun mancanegara. Dalam hal ini, dua pendekatan utama digunakan, yaitu **Content-Based Filtering (CBF)** dan **Collaborative Filtering (CF)** \[2], \[3]. CBF merekomendasikan tempat wisata berdasarkan preferensi pengguna terhadap atribut tertentu seperti kategori dan lokasi, sedangkan CF memanfaatkan riwayat penilaian pengguna lain yang memiliki kemiripan perilaku atau preferensi.

Urgensi pengembangan proyek ini juga dilatarbelakangi oleh permasalahan **keterbatasan informasi dan overload pilihan** yang dialami oleh wisatawan dalam merencanakan perjalanan mereka. Dalam konteks ini, sistem rekomendasi mampu menjadi solusi yang efektif dalam membantu pengguna menavigasi banyaknya pilihan destinasi berdasarkan data historis, preferensi, dan karakteristik destinasi itu sendiri.

Selain memberikan manfaat bagi pengguna, sistem ini juga berdampak positif bagi **pemerataan promosi destinasi**, termasuk tempat wisata yang belum banyak dikenal. Implementasi teknologi ini dapat berperan sebagai sarana inovatif untuk memperkuat citra pariwisata Indonesia secara global serta **meningkatkan kontribusi ekonomi lokal** melalui pemerataan kunjungan ke berbagai lokasi wisata \[1].

Sebagai bagian dari upaya digitalisasi dan transformasi sektor pariwisata, proyek ini menjadi penting untuk diselesaikan karena mampu memberikan nilai tambah terhadap strategi promosi destinasi, pengambilan keputusan wisatawan, serta mendukung pertumbuhan ekosistem ekonomi kreatif dan UMKM pariwisata. Di sisi lain, proyek ini juga menjadi representasi dari sinergi antara pengembangan teknologi kecerdasan buatan dan kontribusinya terhadap sektor riil, seperti yang telah diinisiasi melalui program Bangkit Academy dengan proyek "DestiMate" \[3].

---

### Referensi

* \[1] Santo, “Peran Penting Pariwisata dalam Pengembangan Ekonomi Indonesia,” 21 Februari 2024.
* \[2] R. Faurina dan E. Sitanggang, “Implementasi Metode Content-Based Filtering dan Collaborative Filtering pada Sistem Rekomendasi Wisata di Bali,” *Techno.com*, vol. 22, no. 4, pp. 870–881, 2023.
* \[3] M. S. Negara dan A. Z. Mardiansyah, “Implementasi Machine Learning dengan Metode Collaborative Filtering dan Content-Based Filtering pada Aplikasi Mobile Travel (Bangkit Academy),” *Jurnal Begawe Teknologi Informasi (JBegaTI)*, vol. 5, no. 1, pp. 126–136, 2024.

## Business Understanding

### A. Problem Statements

Dalam konteks pariwisata Indonesia, terdapat beberapa tantangan yang menghambat optimalisasi pengalaman wisatawan dan pemerataan promosi destinasi wisata:

* **Pernyataan Masalah 1**: Wisatawan kesulitan dalam menemukan tempat wisata yang sesuai dengan preferensi pribadi mereka karena banyaknya pilihan destinasi yang tersedia dan keterbatasan informasi yang relevan serta terpersonalisasi.

* **Pernyataan Masalah 2**: Destinasi wisata yang kurang populer atau baru cenderung tidak terekspos secara optimal, karena sistem promosi tradisional tidak mampu menyesuaikan dengan karakteristik dan perilaku wisatawan secara dinamis.

* **Pernyataan Masalah 3**: Tidak adanya sistem digital yang mampu merekomendasikan tempat wisata secara otomatis dan adaptif berbasis data pengguna serta atribut destinasi.

### B. Goals

Tujuan dari proyek ini adalah untuk menjawab pernyataan masalah di atas dengan pendekatan berbasis data dan teknologi sistem rekomendasi:

* **Tujuan 1**: Membangun sistem rekomendasi destinasi wisata yang dapat memberikan saran tempat wisata secara personalisasi berdasarkan preferensi pengguna.

* **Tujuan 2**: Meningkatkan visibilitas tempat wisata yang kurang dikenal dengan cara memunculkannya dalam sistem rekomendasi berdasarkan kemiripan konten atau perilaku pengguna lain.

* **Tujuan 3**: Mengembangkan solusi teknologi berbasis machine learning untuk membantu pengambilan keputusan wisatawan dan sekaligus mendukung promosi destinasi pariwisata Indonesia secara efisien dan terukur.

### C. Solution Approach

Untuk mencapai tujuan yang telah ditetapkan, proyek ini menggunakan dua pendekatan utama dalam pengembangan sistem rekomendasi wisata, yaitu:

#### 1) Content-Based Filtering (CBF)
#### 2) Collaborative Filtering (CF)

Kombinasi kedua pendekatan ini diharapkan dapat menghasilkan sistem rekomendasi yang akurat, relevan, dan adaptif terhadap kebutuhan pengguna, sekaligus mendorong eksposur destinasi wisata secara lebih merata dan efisien.

##  Data Understanding

Pada tahap ini, dilakukan pemuatan dan pemahaman awal terhadap dataset yang digunakan dalam sistem rekomendasi tempat wisata. Dataset yang digunakan diperoleh dari [Kaggle: Indonesia Tourism Destination](https://www.kaggle.com/datasets/aprabowo/indonesia-tourism-destination), yang berisi data tempat wisata di Indonesia beserta rating pengguna dan informasi lainnya.

Dataset terdiri dari beberapa file utama:

* **`tourism_with_id.csv`**: berisi informasi detail tentang tempat wisata.
* **`tourism_rating.csv`**: berisi rating dari pengguna terhadap tempat wisata.
* **`package_tourism.csv`** *(opsional)*: berisi daftar paket wisata berdasarkan kota.
* **`user.csv`** *(opsional)*: berisi informasi pengguna seperti lokasi dan usia.

### 📌 Variabel pada `tourism_with_id.csv`:

| Kolom                       | Deskripsi                                                    |
| --------------------------- | ------------------------------------------------------------ |
| `Place_Id`                  | ID unik untuk setiap tempat wisata                           |
| `Place_Name`                | Nama tempat wisata                                           |
| `Description`               | Deskripsi singkat tempat wisata                              |
| `Category`                  | Kategori tempat wisata (contoh: Budaya, Taman Hiburan, dll.) |
| `City`                      | Kota lokasi tempat wisata                                    |
| `Price`                     | Harga tiket masuk                                            |
| `Rating`                    | Rating rata-rata dari pengguna                               |
| `Time_Minutes`              | Perkiraan waktu kunjungan (menit)                            |
| `Coordinate`, `Lat`, `Long` | Lokasi geografis dalam format koordinat                      |

* **Jumlah data**: 437 entri.

### 📌 Variabel pada `tourism_rating.csv`:

| Kolom           | Deskripsi                                         |
| --------------- | ------------------------------------------------- |
| `User_Id`       | ID pengguna yang memberikan rating                |
| `Place_Id`      | ID tempat wisata yang dinilai                     |
| `Place_Ratings` | Skor rating yang diberikan pengguna (rentang 1–5) |

* **Jumlah data**: 10.000 entri.

---

## 🔎 Exploratory Data Analysis (EDA)

Pada tahap ini dilakukan eksplorasi awal terhadap data untuk memahami karakteristik dasar yang dapat mendukung proses pemodelan sistem rekomendasi.

### 📌 Statistik Deskriptif Rating

> Rata-rata rating berada di kisaran 3, menunjukkan bahwa sebagian besar pengguna cenderung memberikan penilaian netral terhadap tempat wisata yang mereka kunjungi.

### 📊 Distribusi Rating

> Sebagian besar nilai rating berkisar antara 3,5 hingga 4, mengindikasikan preferensi pengguna yang dominan terhadap tempat-tempat yang mereka sukai atau anggap layak direkomendasikan.

### 👥 Statistik Pengguna dan Tempat Wisata

> Terdapat banyak pengguna dan tempat wisata unik, memungkinkan penerapan metode **collaborative filtering** karena adanya interaksi user-item yang cukup beragam.

### 🗺️ Informasi Kategori Tempat Wisata

> Tempat wisata diklasifikasikan ke dalam beberapa kategori seperti **Budaya**, **Taman Hiburan**, **Cagar Alam**, **Bahari**, **Pusat Perbelanjaan**, dan **Tempat Ibadah**, yang dapat dimanfaatkan dalam pendekatan **content-based filtering**.

### 📂 Distribusi Kategori Tempat Wisata

> Kategori tempat wisata paling dominan adalah kategori **Taman Hiburan**, yang menunjukkan tingginya ketertarikan atau jumlah tempat wisata bertema taman hiburan dalam dataset.

## **Data Preparation**

Pada tahap ini, dilakukan **pembersihan dan persiapan data** agar siap digunakan dalam proses pemodelan. Persiapan ini mencakup pengecekan terhadap data yang hilang (missing values), duplikat, serta melakukan encoding pada ID pengguna dan tempat wisata agar dapat digunakan dalam model Neural Network. Langkah-langkah ini penting untuk memastikan kualitas data yang optimal dalam proses **modeling**.

### 1. **Pengecekan Missing Value**

Proses pertama yang dilakukan adalah pengecekan terhadap **missing values** pada dataset. Hal ini penting untuk memastikan bahwa data yang hilang tidak memengaruhi kinerja model. Dari hasil pengecekan, tidak ditemukan missing value pada data rating, namun terdapat missing value pada data tempat wisata (`place`), yang kemudian dihapus menggunakan `dropna(axis=1)`.

**Alasan**: Menghilangkan missing values untuk menjaga kualitas data dan memastikan model menerima informasi yang lengkap.

---

### 2. **Pengecekan Duplikat**

Pengecekan data **duplikat** dilakukan untuk menghindari bias yang dapat memengaruhi model rekomendasi. Beberapa data duplikat ditemukan pada dataset rating, dan langkah selanjutnya adalah menghapusnya menggunakan `drop_duplicates()`. Dengan demikian, hanya data unik yang digunakan dalam model.

**Alasan**: Menghapus duplikat diperlukan agar data yang digunakan dalam model tidak bias dan mencerminkan preferensi pengguna yang sebenarnya.

---

### 3. **Konversi Data ke dalam Bentuk List**

Pada tahap ini, setiap kolom pada dataset **place** diubah menjadi list untuk memudahkan pengolahan data lebih lanjut. Data yang dikonversi adalah:

* **`place_id`**: Menyimpan ID tempat wisata dalam bentuk list.
* **`place_name`**: Menyimpan nama tempat wisata dalam bentuk list.
* **`place_category`**: Menyimpan kategori tempat wisata dalam bentuk list.

**Alasan**: Konversi data ke list membantu struktur data lebih mudah diakses dan digunakan dalam sistem rekomendasi.

---

### 4. **Membangun DataFrame untuk Rekomendasi**

Setelah data dikonversi, kita membuat **DataFrame** akhir, `tourism_df`, yang berisi informasi tentang tempat wisata, nama tempat, dan kategori tempat. DataFrame ini akan digunakan dalam proses rekomendasi tempat wisata yang sesuai dengan preferensi pengguna.

**Alasan**: Membuat DataFrame yang terstruktur memudahkan pencocokan tempat wisata dengan preferensi pengguna dan memberikan rekomendasi yang lebih relevan.

---

### 5. **Encoding User\_Id (ID Pengguna)**

Pada tahap ini, **User\_Id** dikonversi menjadi representasi numerik untuk memudahkan pemrosesan oleh model.

* **Proses**: Mengambil ID pengguna unik dengan `.unique()`, lalu membuat dictionary `user_to_user_encoded` untuk memetakan User\_Id ke ID numerik kecil, dan `user_encoded_to_user` untuk decoding kembali ke ID asli.
* **Alasan**: Encoding diperlukan agar model, terutama Neural Network, dapat memproses data numerik dengan efisien.

---

### 6. **Encoding Place\_Id (ID Tempat Wisata)**

Tahap berikutnya adalah mengonversi **Place\_Id** menjadi ID numerik yang lebih kecil.

* **Proses**: Mengambil ID tempat wisata unik dengan `.unique()`, lalu membuat dictionary `place_to_place_encoded` untuk memetakan Place\_Id ke ID numerik kecil, dan `place_encoded_to_place` untuk decoding.
* **Alasan**: Encoding ID tempat wisata mempermudah model dalam memproses data dan meningkatkan efisiensi komputasi.

---

### 7. **Penggabungan Data untuk Model**

Setelah proses encoding terhadap **ID pengguna** dan **ID tempat wisata** selesai, data `rating` yang telah diproses (termasuk hasil encoding) disiapkan untuk digunakan dalam model rekomendasi. Penggabungan data ini melibatkan pencocokan antara pengguna dan tempat wisata yang mereka rating, sehingga setiap pasangan pengguna-tempat wisata memiliki ID numerik yang dapat digunakan dalam model.

Data yang telah diproses ini siap digunakan untuk melatih model **Collaborative Filtering** berbasis **Neural Network**, yang bertujuan untuk memprediksi rating yang diberikan oleh pengguna terhadap tempat wisata yang belum mereka kunjungi.

**Alasan**: Penggabungan dan encoding data diperlukan agar informasi tentang pengguna dan tempat wisata dapat diproses dalam bentuk numerik yang sesuai dengan input untuk model rekomendasi.

## Modeling

Tahapan ini membahas mengenai model sistem rekomendasi yang dibuat untuk menyelesaikan permasalahan dalam menemukan tempat wisata yang sesuai dengan preferensi pengguna serta meningkatkan visibilitas destinasi yang kurang populer. Proyek ini menyajikan **dua solusi rekomendasi** menggunakan **dua pendekatan algoritma yang berbeda**, yaitu:

### 1. Content-Based Filtering (CBF)

Pendekatan ini merekomendasikan tempat wisata berdasarkan kemiripan **fitur konten**—dalam hal ini adalah **kategori tempat wisata**.

#### Algoritma:

* **TF-IDF Vectorizer** digunakan untuk mengubah data kategori ke dalam representasi numerik.
* **Cosine Similarity** digunakan untuk mengukur tingkat kemiripan antar tempat wisata berdasarkan hasil vektorisasi kategori.

#### Output:

Sistem memberikan **top-5 rekomendasi tempat wisata** yang paling mirip dengan input, contohnya: ketika input adalah *Gedung Sate*, sistem mengembalikan daftar tempat dengan kategori serupa yaitu **Budaya**.

| Index | Place Name                              | Category |
|-------|------------------------------------------|----------|
| 0     | Monumen Nasional                        | Budaya   |
| 1     | Candi Sewu                              | Budaya   |
| 2     | Museum Benteng Vredeburg Yogyakarta     | Budaya   |
| 3     | Museum Satria Mandala                   | Budaya   |
| 4     | Kyotoku Floating Market                 | Budaya   |

#### Kelebihan:

* Dapat bekerja meskipun tidak ada data pengguna (cocok untuk cold-start user).
* Menghasilkan rekomendasi yang konsisten dengan konten yang disukai pengguna.

#### Kekurangan:

* Rekomendasi terbatas pada fitur konten yang tersedia.
* Tidak mempertimbangkan perilaku pengguna lain.

---

### 2. Collaborative Filtering (CF)

Pendekatan ini memberikan rekomendasi berdasarkan **interaksi pengguna**, yaitu data rating tempat wisata. Model dibangun menggunakan pendekatan **Neural Network** dengan layer embedding untuk pengguna dan tempat wisata.

#### Algoritma:

* Model *Neural Collaborative Filtering* dibangun untuk mempelajari hubungan laten antara pengguna dan tempat wisata.
* Data rating dinormalisasi dan dibagi menjadi data latih dan validasi.
* Model dilatih menggunakan **Binary Crossentropy Loss** dan dioptimasi dengan **Adam Optimizer**.

#### Output:

Sistem menghasilkan **top-10 rekomendasi** berdasarkan prediksi rating tertinggi terhadap tempat wisata yang belum dikunjungi oleh pengguna tertentu.

### 🎯 User ID Terpilih: `69`

**Jumlah tempat yang telah dikunjungi:** 24

---

### 🌟 Tempat dengan **Rating Tinggi** oleh User:

| Nama Tempat                             | Kategori      |
| --------------------------------------- | ------------- |
| Rumah Sipitung                          | Budaya        |
| Curug Tilu Leuwi Opat                   | Cagar Alam    |
| Museum Barli                            | Budaya        |
| Gua Pawon                               | Cagar Alam    |
| GPIB Immanuel Semarang (Gereja Blenduk) | Tempat Ibadah |

---

### 🔮 **Top 10 Rekomendasi Tempat Wisata** untuk User 69:

| Rekomendasi Ke | Nama Tempat                                  | Kategori      |
| -------------- | -------------------------------------------- | ------------- |
| 1              | Kawasan Malioboro                            | Taman Hiburan |
| 2              | Bukit Bintang Yogyakarta                     | Taman Hiburan |
| 3              | The World Landmarks - Merapi Park Yogyakarta | Taman Hiburan |
| 4              | Alun-alun Utara Keraton Yogyakarta           | Budaya        |
| 5              | Gumuk Pasir Parangkusumo                     | Taman Hiburan |
| 6              | Air Terjun Kedung Pedut                      | Cagar Alam    |
| 7              | Desa Wisata Gamplong                         | Taman Hiburan |
| 8              | Obyek Wisata Goa Kreo                        | Cagar Alam    |
| 9              | Taman Pelangi                                | Taman Hiburan |
| 10             | Taman Keputran                               | Taman Hiburan |

#### Kelebihan:

* Rekomendasi lebih personal karena berdasarkan perilaku pengguna.
* Mampu menemukan preferensi tersembunyi yang tidak bisa diidentifikasi oleh fitur konten.

#### Kekurangan:

* Tidak cocok untuk pengguna baru tanpa data interaksi (cold-start problem).
* Membutuhkan data yang cukup besar dan proses pelatihan yang lebih kompleks.

## Evaluation

Evaluasi sistem rekomendasi dilakukan untuk menilai sejauh mana solusi yang dibangun berhasil menjawab permasalahan utama, yaitu memberikan rekomendasi destinasi wisata yang **relevan, personal, dan mendukung eksposur destinasi yang kurang populer**.

Evaluasi dibagi berdasarkan dua pendekatan yang digunakan:

### 1. Evaluasi Content-Based Filtering (CBF)

**Tujuan yang didukung**:

* *Tujuan 1*: Rekomendasi yang sesuai dengan preferensi pengguna
* *Tujuan 2*: Eksposur destinasi mirip secara konten, termasuk yang kurang populer

**Metrik Evaluasi: Precision\@K**

Metrik ini digunakan untuk mengevaluasi relevansi top-K hasil rekomendasi berdasarkan kemiripan kategori dengan tempat yang sedang diminati pengguna.

$$
\text{Precision@K} = \frac{\text{Jumlah item yang relevan dalam Top-K}}{\text{K}}
$$

**Interpretasi Hasil**:
Precision\@5 sebesar **1.00** menunjukkan bahwa **100% dari tempat wisata yang direkomendasikan memiliki kategori yang serupa**, yang berarti sistem cukup baik dalam mengenali preferensi berdasarkan konten.

Ini menunjukkan bahwa pendekatan CBF mampu:

* Memberikan saran yang relevan secara tematik/kategorikal.
* Menyisipkan tempat wisata lain yang sejenis, termasuk tempat kurang populer yang memiliki kategori serupa.

---

### 2. Evaluasi Collaborative Filtering (CF)

**Tujuan yang didukung**:

* *Tujuan 1*: Rekomendasi berbasis perilaku pengguna
* *Tujuan 3*: Solusi adaptif berbasis data interaksi

**Metrik Evaluasi: Root Mean Squared Error (RMSE)**

Digunakan untuk mengevaluasi akurasi prediksi rating antara yang diprediksi model dan data aktual.

$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (\hat{y}_i - y_i)^2}
$$

**Interpretasi Hasil**:

* RMSE pada data latih menurun secara konsisten.
* RMSE pada data validasi mulai meningkat setelah beberapa epoch → indikasi **overfitting**.

Hal ini mengindikasikan:

* Model sudah cukup memahami data pelatihan.
* Perlu dilakukan **regularisasi atau teknik validasi silang** agar model lebih general dan tidak overfit.

### Kesimpulan Evaluasi:

* Pendekatan **CBF** cukup efektif dalam memberikan rekomendasi awal terutama saat belum tersedia data interaksi pengguna (solusi untuk cold-start problem).
* Pendekatan **CF** mampu menangkap pola preferensi yang lebih kompleks dan personal dari perilaku pengguna, meskipun membutuhkan data interaksi dalam jumlah yang cukup.
* Keduanya berkontribusi dalam mendukung **pemerataan eksposur destinasi wisata**, baik berdasarkan konten (CBF) maupun perilaku pengguna lain (CF), sesuai dengan pernyataan masalah dan tujuan proyek.

**---Ini adalah bagian akhir laporan---**
