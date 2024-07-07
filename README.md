# Final Project: Insurance Upselling Intelligence 
## Stage: Data Preprocessing
## Group: Data Wizard
* Dzulfikar Hanif Maulana (Ketua)
* Abdul Hardia Amin
* Haerunnisa
* Muhammad Fadhil Pasaribu
* Nisrina Widya Nur Farhani

## Summary:
>Pada tahap ini kami berada di tahap 2 Final Project yaitu Data Preprocessing. Kami melakukan data cleaning dan feature engineering terhadap dataset, berikut ini rangkuman atas apa yang telah kami kerjakan pada tahap ini:
1. Data Cleaning:
- Handle Missing Values, cek apakah ada null values kemudian menghapus row yang mengandung null values.
- Handle Duplicated Data, cek apakah ada duplicated values kemudian menghapus row yang mengandung nilai duplikat.
- Handle Outliers, cek apakah ada outlier menggunakan boxplot dalam hal ini adalah kolom Annual_Premium, kemudian membuat variable dataset baru tanpa outlier.
- Feature Transformation, melakukan transformasi pada kolom yang skalanya jauh berbeda. Dalam hal ini adalah kolom Annual_Premium, kemudian kami menggunakan metode Log Transformation untuk mentransformasinya. 
- Feature Encoding, mengubah kolom kategorikal menjadi numerik. Pertama menggunakan Label encoding pada kolom Gender(Male[1], Female[0]; kolom baru 'Gender_Label'), kolom Vehicle_Damage(Yes[1], No[0]; kolom baru 'Vehicle_Damage_Label'), dan Response_Class (True[1], False[0]). Kedua menggunakan One Hot Encoding pada kolom Vehicle_Age mengubahnya menjadi beberapa kolom terpisah sesuai kategori valuenya ('Vehicle_Age_1-2 Year', 'Vehicle_Age_< 1 Year', 'Vehicle_Age_> 2 Years').
- Handle Class Imbalance, melakukan balancing pada data yang tidak balance yaitu kolom Response menggunakan metode SMOTE.

2. Feature Engineering:
- Feature Selection
    - Menghapus kolom ‘id’, karena berisi value yang tidak relevan untuk digunakan saat proses pemodelan Machine Learning.
    - Membuang fitur yang telah melewati proses encoding kedalam data numerik baik menggunakan label encode maupun One Hot Encoding. kolom yang di maksud yaitu 'Gender’, ’Vehicle_Age’, 'Vehicle_Damage', dan‘Response'.
    - Menghapus kolom Driving_License karena menunjukkan nilai p-value >0.05 setelah melalui metode chi square.
    - menghapus kolom ‘Annual_Premium’ setelah dilakukan transformasi fitur menggunakan Log Transform dan membuat kolom baru denga nama ‘Annual_Premium_Log’.
    - Hasil feature selection = ['Age', 'Region_Code','Previously_Insured', 'Annual_Premium', 'Policy_Sales_Channel', 'Vintage', 'Response_Class', 'Gender_Label',
       'Vehicle_Damage_Label', 'Vehicle_Age_1-2 Year', 'Vehicle_Age_< 1 Year','Vehicle_Age_> 2 Years', 'Annual_Premium_Log']
- Feature Extraction
    - Berdasarkan kolom yang telah ada, kami menambahkan 4 kolom baru sebagai fitur baru yang dihasilkan dari gabungan beberapa fitur terkait, yaitu:
        1. Previous_Claim_Count, memanfaatkan fitur ‘Previously_Insured’ dan ‘Vehicle_Damage_Label’
        2. Ownership_Duration, memanfaatkan fitur ‘Vintage’, ‘Vehicle_Age_1-2 Year’, ‘Vehicle_Age_<1 Year’ dan ‘Vehicle_Age_>2 Years’.
        3. Sales_Channel_Frequency, memanfaatkan fitur ‘Policy_Sales_Channel’.
        4. Customer_Engagement_Index, memanfaatkan fitur ‘Vintage’ dan ‘Annual_Premium’.
- 4 ide tambahan:
  - Claim History: Informasi tentang riwayat klaim asuransi sebelumnya. 
  - Credit Score: Skor kredit dari pemegang asuransi. 
  - Employment Status: Status pekerjaan pemegang asuransi, seperti apakah mereka bekerja penuh waktu, paruh waktu, wiraswasta, atau pengangguran. 
  - Marital Status: Status pernikahan pemegang asuransi. 
