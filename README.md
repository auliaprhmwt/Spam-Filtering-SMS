**SPAM FILTERING FOR SMS USING NAÏVE BAYES**

**Latar Belakang**

SMS masih digunakan untuk OTP, notifikasi, dan komunikasi penting. Namun, maraknya SMS spam dan phishing (smishing) dapat mengganggu pengguna dan mengancam keamanan data pribadi. Oleh karena itu diperlukan sistem klasifikasi otomatis untuk membedakan SMS spam dan SMS normal (ham).


**Dataset & Tujuan**

Informasi Dataset
- 1.000 SMS berbahasa Indonesia
- 534 SMS Spam
- 466 SMS Ham (Non-Spam)
- Data dikumpulkan dari SMS pada perangkat Android dan disimpan dalam format CSV.

**Tujuan**
Membangun model yang mampu mengidentifikasi SMS spam secara otomatis untuk meningkatkan keamanan pengguna.

**Rumusan Masalah**
- SMS promosi yang mengganggu
- SMS penipuan dan phishing
- Penyalahgunaan OTP palsu
- Sulit melakukan identifikasi secara manual dalam jumlah besar

**Objek**
- Mengklasifikasikan SMS menjadi Spam atau Ham
- Mengukur performa model klasifikasi
- Mengevaluasi efektivitas algoritma Naïve Bayes

**Fitur yang digunakan**
TF-IDF Vectorization

**Mengubah teks SMS menjadi representasi numerik menggunakan:**
TF (Term Frequency)
IDF (Inverse Document Frequency)

Tujuannya untuk memberikan bobot lebih tinggi pada kata-kata yang penting dalam proses klasifikasi.

**Langkah**

**1. INPUT DATA**
<img width="1195" height="621" alt="image" src="https://github.com/user-attachments/assets/bee38295-0890-4572-9931-a11b8ef2a7e6" />

Pada tahap ini dilakukan import library yang diperlukan untuk proses pengolahan data, preprocessing teks, pembobotan TF-IDF, pembangunan model Naïve Bayes, serta evaluasi performa model.


<img width="536" height="260" alt="image" src="https://github.com/user-attachments/assets/f9d78daa-9436-43fb-9be0-c8987c3f6d59" />

Mengimpor dan memuat dataset SMS ke dalam Google Colab agar data dapat diolah dan dianalisis pada tahap selanjutnya.


**2. PREPROCESSING**
   
- Cleaning
<img width="984" height="429" alt="image" src="https://github.com/user-attachments/assets/92cfd9f6-8b1c-4708-96b5-1a84ca2da283" />

Membersihkan teks SMS dari karakter yang tidak diperlukan, seperti tanda baca dan simbol, agar data menjadi lebih rapi dan siap untuk dianalisis.


- Case Folding
<img width="647" height="316" alt="image" src="https://github.com/user-attachments/assets/ed0773b5-72a9-4644-944c-b12e3a934df0" />

Mengubah seluruh huruf pada teks menjadi huruf kecil (lowercase) agar kata yang sama dengan penulisan berbeda (huruf besar dan kecil) dianggap sebagai satu kata yang sama.

- Tokenization
<img width="652" height="262" alt="image" src="https://github.com/user-attachments/assets/d6053c8a-6842-48e7-ba7e-debc148df536" />

Memecah teks menjadi token atau kata-kata individual sehingga dapat diolah dan dianalisis oleh algoritma machine learning.

- Stopword Removal
<img width="654" height="302" alt="image" src="https://github.com/user-attachments/assets/2b460c54-65fc-47d7-b00e-64783d680e0d" />

Menghapus kata umum yang tidak informatif

- Stemming
<img width="384" height="78" alt="image" src="https://github.com/user-attachments/assets/9cc0e942-e1c6-432e-9958-45dfad8084bf" />

Mengubah kata menjadi bentuk dasar menggunakan Sastrawi 


 **Sebelum Preprocessing**
 
<img width="498" height="250" alt="image" src="https://github.com/user-attachments/assets/8c947664-897e-4dfb-974f-eb69b0abb265" />

 **Setelah Preprocessing**
 
 <img width="434" height="247" alt="image" src="https://github.com/user-attachments/assets/4f4ca5bf-aa14-40e9-affc-6889b37c9309" />

**3. PEMBOBOTAN TF-IDF**
<img width="622" height="114" alt="image" src="https://github.com/user-attachments/assets/eda62caf-9dd8-46dc-b23c-e0eda73d7a16" />

<img width="544" height="459" alt="image" src="https://github.com/user-attachments/assets/3b343491-6069-4615-9c93-40ceb58686fc" />

Tujuan dari tahap ini adalah mengubah data teks yang masih berbentuk kata-kata menjadi representasi numerik yang dapat diproses oleh algoritma machine learning. Selain itu, TF-IDF digunakan untuk mengukur tingkat kepentingan suatu kata dalam sebuah dokumen relatif terhadap seluruh dokumen pada dataset.

Pada metode TF-IDF, kata yang sering muncul pada suatu dokumen tetapi jarang muncul pada dokumen lain akan memperoleh bobot yang tinggi karena dianggap memiliki informasi yang lebih spesifik dan relevan. Sebaliknya, kata yang muncul pada banyak dokumen akan memperoleh bobot yang rendah karena dianggap kurang mampu membedakan suatu dokumen dengan dokumen lainnya.

Hasil dari proses ini berupa matriks numerik yang berisi bobot TF-IDF untuk setiap kata atau n-gram pada setiap dokumen. Matriks tersebut kemudian digunakan sebagai fitur masukan (input) dalam proses klasifikasi menggunakan algoritma Naïve Bayes. Dengan adanya pembobotan TF-IDF, model dapat lebih fokus pada kata-kata yang memiliki informasi penting sehingga membantu meningkatkan akurasi dalam membedakan SMS spam dan SMS non-spam (ham).

**4. KLASIFIKASI NAÏVE BAYES**
<img width="576" height="165" alt="image" src="https://github.com/user-attachments/assets/5e960f81-fe95-4e04-81f6-c9cb7d0a2093" />

Pada tahap ini, model dibangun menggunakan fungsi MultinomialNB() dan kemudian dilatih menggunakan data latih yang telah diproses sebelumnya agar dapat mempelajari pola-pola yang membedakan SMS spam dan SMS ham.

Melalui proses pelatihan tersebut, model mempelajari hubungan antara kata-kata yang muncul pada pesan dengan kategori yang sesuai. Setelah model selesai dilatih, model dapat digunakan untuk memprediksi kategori SMS baru yang belum pernah dilihat sebelumnya. Hasil dari tahap ini adalah terbentuknya model klasifikasi yang mampu mengenali pola karakteristik pesan spam maupun non-spam. Selanjutnya, performa model dievaluasi menggunakan beberapa metrik seperti accuracy, precision, recall, dan f1-score untuk mengetahui seberapa baik kemampuan model dalam melakukan spam filtering.

**5. EVALUASI**

<img width="683" height="142" alt="image" src="https://github.com/user-attachments/assets/35df2eb0-e8fe-4ae2-aec4-50688b15c0ca" />

<img width="368" height="242" alt="image" src="https://github.com/user-attachments/assets/5e48d439-5b19-4022-b0fc-19f99e062b6c" />

Tahap evaluasi dilakukan untuk mengukur kinerja model dalam mengklasifikasikan SMS spam dan ham menggunakan confusion matrix, classification report, dan accuracy score. Berdasarkan confusion matrix, model menghasilkan 85 data ham yang berhasil diklasifikasikan dengan benar, 107 data spam yang berhasil diklasifikasikan dengan benar, serta hanya 8 kesalahan klasifikasi pada data ham yang diprediksi sebagai spam. Selain itu, tidak terdapat data spam yang salah diprediksi sebagai ham. Hasil tersebut menunjukkan bahwa model memiliki kemampuan yang sangat baik dalam membedakan pesan spam dan non-spam.

Berdasarkan classification report, model memperoleh nilai precision sebesar 1,00 untuk kelas ham dan 0,93 untuk kelas spam, sedangkan nilai recall masing-masing sebesar 0,91 dan 1,00. Nilai f1-score untuk kedua kelas mencapai 0,96 yang menunjukkan keseimbangan yang baik antara ketepatan dan kemampuan deteksi model. Secara keseluruhan, model memperoleh accuracy sebesar 96% pada 200 data uji, yang menunjukkan bahwa model Naïve Bayes yang dibangun mampu melakukan spam filtering secara efektif dan memberikan performa yang sangat baik dalam mendeteksi SMS spam.

**Uji Model**
<img width="663" height="271" alt="image" src="https://github.com/user-attachments/assets/975935cd-d456-4359-889c-5bfd11313c89" />

Berdasarkan hasil yang ditampilkan terlihat bahwa model dapat memprediksi pesan atau 
teks baru sebagai ham dan spam dengan sesuai. Hasil ini dengan kata lain menjadi validasi 
untuk performa model yang baik pada kasus baru yang mungkin tidak ada di dalam data latih 
atau data uji.
