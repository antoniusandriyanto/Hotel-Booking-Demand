# Hotel-Booking-Demand

# <center>**Analisis RFM terhadap Dataset Hotel Booking Demand**

![image](https://github.com/user-attachments/assets/f94da422-be25-4134-ba62-f9c941ff12d8)

<hr>

## <center>**Business Understanding**

<hr>

***Stakeholder***: ***Revenue Manager*** dari Manajemen Hotel Tuvoli


> ### **Context**

Manajemen Hotel `Tuvoli` yang menjalankan *`City Hotel`* di Lisbon, Portugal dan *`Resort Hotel`* di Algrave, Portugal tengah mengalami tantangan signifikan dalam mengoptimalkan strategi pemesanan hotel mereka. Manajemen hotel tersebut berupaya untuk memaksimalkan tingkat hunian dan pendapatan sambil meminimalkan pembatalan pemesanan hotel mereka. Hal ini mendorong pihak manajemen Hotel `Tuvoli` meminta bantuan kepada konsultan data `BetaMachineLearning` untuk menganalisis data-data pemesanan kamar hotel yang mereka miliki dan menarik *insight* yang berguna untuk meningkatkan profitabilitas mereka. Analisis segmentasi tamu yang efektif dan analisis prediktif sangat penting untuk mencapai tujuan ini. 

Adanya analisis segmentasi tamu memungkinkan pihak manajamen hotel untuk mengelompokkan Tamu berdasarkan sejumlah karakteristik mereka. Informasi ini nantinya berkontribusi untuk memberikan *insight* mendalam tentang nilai Tamu berdasarkan perilaku mereka. Sementara itu, analisis prediktif menggunakan *machine learning* dalam memprediksi pembatalan pemesanan hotel berperan penting bagi pihak hotel karena memungkinkan mereka untuk secara proaktif mengelola risiko pembatalan pemesanan. Kedua analisis ini jika diintegrasikan secara bersamaan diharapkan mampu memaksimalkan pendapatan hotel.

> ### **Problem Statement**

Bagaimana pemanfaatan analisis segmentasi tamu dan pemanfaatan *Machine Learning* dalam memprediksi pembatalan pemesanan hotel secara efektif dapat mengoptimalkan strategi pemesanan hotel dan strategi manajemen profit secara keseluruhan?

> ### **Goals**

1. Analisis segmentasi tamu menggunakan metrik RFM bertujuan untuk:
    - mengidentifikasi dan menyegmentasi tamu berdasarkan perilaku pemesanan mereka menggunakan metrik RFM.
    - menentukan segmen tamu bernilai tinggi yang memberikan kontribusi signifikan terhadap pendapatan hotel.
    - mengembangkan strategi pemasaran yang ditargetkan untuk berbagai segmen tamu.

2. Analisis prediktif pembatalan pemesanan hotel bertujuan untuk:
    - membangun model prediktif untuk mengidentifikasi kemungkinan pembatalan pemesanan.
    - menerapkan langkah-langkah proaktif untuk mengurangi dampak pembatalan berdasarkan prediksi model.

> ### **Analytic Approach**

1. Analisis RFM:
   - mengidentifikasi prilaku tamu berdasarkan terakhir kali melakukan transaksi (Recency), seberapa sering melakukan transaksi (Frequency) dan berapa banyak uang yang dihabiskan (Monetary).
   - Menyegmentasi tamu ke dalam berbagai kategori RFM (misalnya, bernilai tinggi, sering, baru, dan berisiko).

2. Analisis prediktif menggunakan *Machine Learning*:
   - Memilih fitur yang terkait dengan pembatalan pemesanan.
   - Melatih model *Machine Learning* dengan algoritma yang paling efektif untuk memprediksi pembatalan pemesanan.
   - Mengevaluasi kinerja model menggunakan metrik evaluasi yang telah ditentukan.

3. Integrasi dan Pengembangan Strategi:
   - Menggabungkan wawasan dari analisis RFM dan prediksi pembatalan.
   - Mengembangkan strategi untuk melibatkan tamu bernilai tinggi dan mengurangi pembatalan.
   - Menerapkan kampanye pemasaran yang ditargetkan dan memantau efektivitasnya.

> ### **Metric Evaluation**
![image](https://github.com/user-attachments/assets/a01e4579-b204-4635-968c-58ed4b36d37a)

- *(TP) True Positive*: Tamu diprediksi (predict) cancel dan kenyataannya (actual) benar-benar cancel.
- *(FP) False Positive*: Tamu diprediksi (predict) cancel, tapi kenyataannya (actual) tidak cancel.
- *(TN) True Negative*: Tamu diprediksi (predict) tidak cancel dan kenyataannya (actual) tidak cancel.
- *(FN) False Negative*: Tamu diprediksi (predict) tidak cancel, tapi kenyataannya (actual) cancel.

**Error Types:**

1. Type 1 error : False Positive

Konsekuensi : tamu yang seharusnya tidak *cancel* akan dianggap *cancel* tentunya ini akan membuat kekecewaan dari tamu terhadap pelayanan hotel apabila kamar tidak tersedia akibat *overbook*.

2. Type 2 error : False Negative

Konsekuensi : tamu yang seharusnya *cancel* akan dianggap tidak *cancel* tentunya ini akan membuat kerugian bagi perusahaan di bidang hotel tersebut.

Berdasarkan *problem statement* dan *goals* dari analisis ini, maka prioritas utamanya adalah memastikan bahwa model *machine learning* dapat memprediksi setiap pembatalan yang mungkin terjadi  dengan ketepatan yang tinggi. Dengan keperluan untuk mempertimbangkan keharmonisan prediksi seperti F1-score tetapi lebih menekankan pada pengurangan Type I error (false positive) atau lebih fokus pada recall, **maka F2-score menjadi pilihan yang baik**.

F2-score merupakan varian dari F1 score yang memberikan bobot lebih pada recall daripada precision.Penggunaan F2-score dalam konteks prediksi pembatalan pemesanan hotel mencerminkan strategi bisnis yang memprioritaskan meminimalkan Type 2 error (false negative)—yang berarti memastikan bahwa Anda memprediksi sebanyak mungkin pembatalan yang sebenarnya.


<hr>

## <center> Random Forest

<hr>

![image](https://github.com/user-attachments/assets/c07c3a7e-246f-495b-ad09-0d08b08adda7)

Pada kedua alat prediksi untuk City Hotel dan Resort Hotel menggunakan Random Forest. Random Forest merupakan suatu algoritma yang menggunakan decision tree untuk melangsungkan proses seleksi, di mana pohon decision tree akan dibagi secara rekursif berdasarkan data pada kelas yang sama. Oleh karena itu dengan menggunakan tree yang semakin banyak maka akan berpengaruh terhadap akurasi yang didapatkan menjadi lebih baik. Untuk prediksi klasifikasi pada Random Forest sendiri nantinya setiap pohon akan memberikan prediksi kelas. Prediksi akhir dari Random Forest dihasilkan dengan mengambil suara mayoritas dari semua pohon.

Pada Random Forest dapat dilakukan hyperparameter tuning dengan parameter :

- n_estimators: Jumlah pohon dalam hutan.
- max_depth: Kedalaman maksimum dari pohon keputusan.
- min_samples_split: Jumlah minimum sampel yang diperlukan untuk membagi sebuah node.
- min_samples_leaf: Jumlah minimum sampel yang diperlukan untuk menjadi leaf node (simpul daun).
- model_bootstrap: Apakah sampel bootstrap digunakan saat membuat pohon. Jika Salah, seluruh kumpulan data digunakan untuk membangun setiap pohon.

link Tableau:

Hotel Booking Dashboard : https://public.tableau.com/shared/T5586WRSY?:display_count=n&:origin=viz_share_link

RFM Hotel Booking Dashboard : https://public.tableau.com/views/RFMHotelBookingDashboard/RFMHotelBookingDashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link 
