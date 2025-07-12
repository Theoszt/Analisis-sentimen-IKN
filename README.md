# Analisis Respon Masyarakat terhadap Pembangunan IKN

## Deskripsi Proyek

[cite_start]Proyek ini bertujuan untuk menganalisis sentimen masyarakat terhadap pembangunan Ibu Kota Nusantara (IKN)[cite: 37]. [cite_start]Analisis dilakukan berdasarkan data cuitan dari platform X (sebelumnya Twitter) yang dikumpulkan selama periode tahun 2022, 2023, dan 2024, dengan total 2086 cuitan yang digunakan dalam dataset ini[cite: 109, 110].

[cite_start]Pembangunan IKN merupakan proyek besar pemerintah yang bertujuan untuk menciptakan pusat pemerintahan yang lebih efektif, mengurangi kepadatan Jakarta, dan mendukung pemerataan pembangunan di luar Pulau Jawa[cite: 10]. [cite_start]Oleh karena itu, memahami respon masyarakat terhadap rencana ini sangat penting untuk mencerminkan keberhasilan komunikasi pemerintah dan persepsi publik terhadap perubahan besar yang akan terjadi[cite: 34, 35].

[cite_start]Hasil analisis sentimen ini diharapkan dapat membantu pemerintah dalam merancang kebijakan dan strategi komunikasi yang lebih baik, serta memberikan pemahaman mendalam tentang harapan dan kekhawatiran masyarakat terkait pembangunan IKN[cite: 40].

## Metodologi

### Pengumpulan Data
[cite_start]Data sentimen dikumpulkan dengan *scraping* cuitan dari aplikasi X (Twitter) dari tahun 2022, 2023, dan 2024[cite: 109, 110].

### Pelabelan Data
[cite_start]Data yang digunakan dalam analisis ini dilabeli secara manual menjadi kategori "positif", "negatif", dan "netral"[cite: 127]. [cite_start]Metode pelabelan manual dipilih karena menghasilkan distribusi label yang lebih seimbang dibandingkan metode otomatis seperti TextBlob dan Vader[cite: 112, 113, 114, 127].

[cite_start]Distribusi label data sampel (586 data sentimen) adalah sebagai berikut[cite: 160, 163]:
* [cite_start]Netral: 209 [cite: 160, 163]
* [cite_start]Negatif: 190 [cite: 160, 163]
* [cite_start]Positif: 187 [cite: 160, 163]

### Pra-pemrosesan Data
[cite_start]Langkah-langkah pra-pemrosesan data meliputi[cite: 128]:
* [cite_start]**Case Folding (Lowering):** Mengubah semua teks menjadi huruf kecil[cite: 129, 130].
* [cite_start]**Cleaning Teks:** Menghapus angka, URL, emoji, tanda baca, karakter yang tidak relevan, normalisasi, dan simbol[cite: 131, 132, 133, 134, 136, 137, 138, 139].
* [cite_start]**Slang to Formal Word:** Mengubah kata-kata tidak formal menjadi bentuk formalnya[cite: 140].
* [cite_start]**Tokenisasi:** Memecah teks menjadi unit-unit kata atau token[cite: 141].
* [cite_start]**Stemming:** Mengubah kata-kata ke bentuk dasarnya[cite: 143].
* [cite_start]**Stopword Removal:** Menghapus kata-kata umum yang tidak memberikan makna signifikan (stopword)[cite: 144].

### Feature Engineering
Dalam proyek ini, digunakan dua metode *feature engineering*:

1.  [cite_start]**TF-IDF (Term Frequency-Inverse Document Frequency):** [cite: 146]
    * [cite_start]Metode ini digunakan untuk mengekstrak informasi penting dari teks dengan mengidentifikasi kata-kata yang memiliki bobot besar dalam menentukan sentimen[cite: 147, 148].
    * [cite_start]TF-IDF dipilih karena menghasilkan akurasi yang lebih baik dibandingkan Word2Vec dalam implementasi ini[cite: 150].

2.  [cite_start]**Word2Vec:** [cite: 152]
    * [cite_start]Metode ini mengubah kata-kata menjadi vektor numerik berdasarkan konteksnya, membantu menangkap hubungan semantik antar kata[cite: 153, 154].
    * [cite_start]Meskipun demikian, dalam pengujian model, TF-IDF menunjukkan performa yang lebih unggul[cite: 150].

### Modeling
Beberapa model *machine learning* diuji menggunakan fitur Word2Vec dan TF-IDF.

[cite_start]**Akurasi Model dengan Word2Vec (data sampel 586 sentimen)[cite: 157, 159]:**
* [cite_start]Naive Bayes Gauss: 46.61% [cite: 159]
* [cite_start]Random Forest Classifier: 60.17% [cite: 159]
* [cite_start]KNN: 65.25% [cite: 159]
* [cite_start]SVM: 66.10% [cite: 159]
* [cite_start]Decision Tree: 55.93% [cite: 159]

[cite_start]**Akurasi Model dengan TF-IDF (data sampel 586 sentimen)[cite: 162, 164, 166]:**
* [cite_start]Naive Bayes Multinomial: 73.73% [cite: 164]
* [cite_start]Naive Bayes Gauss: 61.86% [cite: 164]
* [cite_start]Random Forest Classifier: 79.66% [cite: 164]
* [cite_start]High Gradient Boosting: 72.88% [cite: 164]
* [cite_start]XGBoost: 79.66% [cite: 164]
* [cite_start]SVM: 73.73% [cite: 166]
* [cite_start]Decision Tree: 72.03% [cite: 166]
* [cite_start]CatBoost: 74.58% [cite: 166]
* [cite_start]LightGBM: 74.58% [cite: 166]
* [cite_start]KNN: 83.90% [cite: 166]

**Model Terbaik:**
[cite_start]Model **KNN (K-Nearest Neighbors)** dengan *feature engineering* TF-IDF didapati sebagai model terbaik untuk analisis sentimen IKN, dengan akurasi total 93.86%[cite: 168, 191]. [cite_start]Evaluasi model KNN menunjukkan[cite: 191, 202, 203]:
* [cite_start]**Akurasi prediksi *train*:** 96.37% [cite: 169]
* [cite_start]**Akurasi prediksi *test*:** 83.90% [cite: 202]
* [cite_start]**Jumlah data *training*:** 468 [cite: 236]
* [cite_start]**Jumlah data *testing*:** 118 [cite: 237]
* [cite_start]Data yang belum terlabel sebanyak 1500 sentimen akan di-*train* menggunakan model KNN[cite: 262].

## Hasil dan Pembahasan

### Distribusi Sentimen Keseluruhan
[cite_start]Analisis menunjukkan bahwa pandangan masyarakat terhadap pembangunan IKN terus berubah seiring waktu[cite: 394].
* [cite_start]**Sebelum Pembangunan IKN (sebelum 2022-08-15):** Dari 289 responden, 50.9% sentimen negatif (147 responden), 10.0% sentimen positif (29 responden), dan 39.1% sentimen netral (113 responden)[cite: 315]. [cite_start]Ini menunjukkan 5 dari 10 orang merasa tidak setuju atau kurang mendukung[cite: 316].
* [cite_start]**Pas Awal Pembangunan IKN (2022-08-15 s.d. 2023-08-17):** Dari 340 responden, 87.1% sentimen negatif (296 responden), 2.9% sentimen positif (10 responden), dan 10.0% sentimen netral (34 responden)[cite: 323, 324, 325]. [cite_start]Ini mengindikasikan 9 dari 10 orang khawatir terhadap pembangunan IKN[cite: 341].
* [cite_start]**Pas Pembangunan Akhir IKN (2023-08-17 s.d. 2024-08-17):** Dari 1119 responden, 35.5% sentimen negatif (397 responden), 56.7% sentimen positif (635 responden), dan 7.8% sentimen netral (87 responden)[cite: 351, 352, 353]. [cite_start]Hal ini menunjukkan 6 dari 10 orang merasa positif terhadap pembangunan akhir IKN[cite: 354].
* [cite_start]**Setelah Pembangunan IKN (setelah 2024-08-17):** Dari 306 responden, 32.4% sentimen negatif (99 responden), 18.0% sentimen positif (55 responden), dan 49.7% sentimen netral (152 responden)[cite: 369]. [cite_start]Ini berarti 5 dari 10 orang merasa netral atau tidak memiliki pendapat tegas[cite: 392].

[cite_start]Secara keseluruhan, di awal pembangunan didominasi sentimen negatif, namun seiring berjalannya proyek, sentimen positif meningkat di akhir pembangunan[cite: 394, 396]. [cite_start]Setelah proyek selesai, banyak yang bersikap netral, kemungkinan menunggu hasil nyata[cite: 397, 398, 399].

## Kesimpulan

[cite_start]Pandangan masyarakat terhadap pembangunan IKN menunjukkan dinamika perubahan seiring waktu[cite: 394]. [cite_start]Awalnya didominasi oleh keraguan dan kekhawatiran (sentimen negatif), namun kemudian beralih ke peningkatan dukungan (sentimen positif) seiring dengan kemajuan proyek[cite: 394, 396]. [cite_start]Setelah proyek selesai, banyak masyarakat yang bersikap netral, menunjukkan sikap menunggu dan melihat hasil nyata dari pembangunan[cite: 397, 398, 399].

## Saran

[cite_start]Untuk meningkatkan dukungan publik, pemerintah disarankan untuk memperkuat komunikasi terkait manfaat pembangunan IKN serta memperlihatkan dampak positifnya secara lebih transparan kepada masyarakat[cite: 401].
