# 📩 SMS Spam Filtering Using Naïve Bayes

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge\&logo=googlecolab\&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Naïve%20Bayes-success?style=for-the-badge)
![NLP](https://img.shields.io/badge/NLP-TF--IDF-orange?style=for-the-badge)

## 📌 Project Overview

Projek ini bertujuan membangun sistem **SMS Spam Filtering** menggunakan algoritma **Naïve Bayes** untuk mengklasifikasikan pesan SMS berbahasa Indonesia ke dalam kategori **Spam** dan **Ham (Non-Spam)**. Sistem ini dikembangkan untuk membantu mendeteksi pesan promosi, phishing, maupun penipuan secara otomatis sehingga dapat meningkatkan keamanan pengguna.

---

## 🚀 Key Results

| Metric           | Score    |
| ---------------- | -------- |
| Accuracy         | **96%**  |
| Precision (Ham)  | **1.00** |
| Precision (Spam) | **0.93** |
| Recall (Ham)     | **0.91** |
| Recall (Spam)    | **1.00** |
| F1-Score         | **0.96** |

> [!IMPORTANT]
> Model berhasil mengklasifikasikan SMS spam dan non-spam dengan tingkat akurasi 96% serta mampu mendeteksi seluruh SMS spam pada data uji.

---

## 📂 Dataset

| Keterangan  | Informasi         |
| ----------- | ----------------- |
| Jumlah Data | 1.000 SMS         |
| SMS Spam    | 534               |
| SMS Ham     | 466               |
| Bahasa      | Indonesia         |
| Format      | CSV               |
| Sumber Data | Perangkat Android |

---

## 🎯 Problem Statement

Beberapa permasalahan yang menjadi latar belakang proyek ini:

* SMS promosi yang mengganggu pengguna.
* SMS phishing dan penipuan (smishing).
* Penyalahgunaan OTP palsu.
* Sulitnya melakukan identifikasi manual terhadap SMS dalam jumlah besar.

---

## 🔄 Workflow

```text
Input Dataset
      ↓
Text Preprocessing
      ↓
TF-IDF Vectorization
      ↓
Train-Test Split
      ↓
Naïve Bayes Classification
      ↓
Model Evaluation
      ↓
Prediction on New Messages
```

---

## 🧹 Text Preprocessing

Tahap preprocessing dilakukan untuk membersihkan dan menyiapkan data teks sebelum digunakan dalam proses klasifikasi.

### Cleaning

<img width="984" height="429" alt="image" src="https://github.com/user-attachments/assets/92cfd9f6-8b1c-4708-96b5-1a84ca2da283" />

Menghapus karakter yang tidak diperlukan seperti tanda baca, simbol, dan karakter khusus.

### Case Folding

<img width="647" height="316" alt="image" src="https://github.com/user-attachments/assets/ed0773b5-72a9-4644-944c-b12e3a934df0" />

Mengubah seluruh huruf menjadi huruf kecil (lowercase) agar konsisten.

### Tokenization

<img width="652" height="262" alt="image" src="https://github.com/user-attachments/assets/d6053c8a-6842-48e7-ba7e-debc148df536" />

Memecah kalimat menjadi token atau kata-kata individual.

### Stopword Removal

<img width="654" height="302" alt="image" src="https://github.com/user-attachments/assets/2b460c54-65fc-47d7-b00e-64783d680e0d" />

Menghapus kata-kata umum yang tidak memiliki informasi penting.

### Stemming
<img width="384" height="78" alt="image" src="https://github.com/user-attachments/assets/9cc0e942-e1c6-432e-9958-45dfad8084bf" />

Mengubah kata menjadi bentuk dasar menggunakan Sastrawi 

### Sebelum Preprocessing

<img width="498" height="250" alt="image" src="https://github.com/user-attachments/assets/8c947664-897e-4dfb-974f-eb69b0abb265" />

### Setelah Preprocessing

<img width="434" height="247" alt="image" src="https://github.com/user-attachments/assets/4f4ca5bf-aa14-40e9-affc-6889b37c9309" />

## 🔠 TF-IDF Vectorization

<img width="622" height="114" alt="image" src="https://github.com/user-attachments/assets/eda62caf-9dd8-46dc-b23c-e0eda73d7a16" />

<img width="544" height="459" alt="image" src="https://github.com/user-attachments/assets/3b343491-6069-4615-9c93-40ceb58686fc" />

TF-IDF digunakan untuk mengubah data teks menjadi representasi numerik yang dapat diproses oleh algoritma machine learning.

Kata yang sering muncul pada suatu dokumen namun jarang muncul pada dokumen lain akan memperoleh bobot lebih tinggi karena dianggap memiliki informasi yang lebih relevan dalam proses klasifikasi.

Output dari tahap ini berupa matriks fitur numerik yang digunakan sebagai input model Naïve Bayes.

---

## 🤖 Naïve Bayes Classification

<img width="576" height="165" alt="image" src="https://github.com/user-attachments/assets/5e960f81-fe95-4e04-81f6-c9cb7d0a2093" />

Model dibangun menggunakan algoritma **Multinomial Naïve Bayes** yang dilatih menggunakan fitur hasil pembobotan TF-IDF.

Model mempelajari pola kata-kata yang sering muncul pada SMS spam maupun ham, kemudian menggunakan pola tersebut untuk memprediksi kategori SMS baru yang belum pernah dilihat sebelumnya.

---

## 📊 Model Evaluation

### Confusion Matrix

<img width="683" height="142" alt="image" src="https://github.com/user-attachments/assets/35df2eb0-e8fe-4ae2-aec4-50688b15c0ca" />

<img width="368" height="242" alt="image" src="https://github.com/user-attachments/assets/5e48d439-5b19-4022-b0fc-19f99e062b6c" />

Hasil klasifikasi:

| Actual / Predicted | Ham | Spam |
| ------------------ | --- | ---- |
| Ham                | 85  | 8    |
| Spam               | 0   | 107  |

### Classification Report

| Class | Precision | Recall | F1-Score |
| ----- | --------- | ------ | -------- |
| Ham   | 1.00      | 0.91   | 0.96     |
| Spam  | 0.93      | 1.00   | 0.96     |

### Accuracy

```text
Accuracy = 96%
```

> [!NOTE]
> Model mampu mendeteksi seluruh SMS spam pada data uji (Recall Spam = 1.00), menunjukkan performa yang sangat baik dalam proses spam filtering.

---

## 🧪 Testing on New Messages

<img width="663" height="271" alt="image" src="https://github.com/user-attachments/assets/975935cd-d456-4359-889c-5bfd11313c89" />

Pengujian terhadap pesan baru menunjukkan bahwa model mampu mengklasifikasikan SMS sebagai spam maupun ham secara tepat, sehingga membuktikan kemampuan generalisasi model terhadap data yang belum pernah dilihat sebelumnya.

---

## 🎯 Key Findings

✅ Dataset berhasil diproses menggunakan tahapan NLP standar.

✅ TF-IDF efektif dalam merepresentasikan teks menjadi fitur numerik.

✅ Naïve Bayes mampu mengidentifikasi pola SMS spam dan ham dengan baik.

✅ Model mencapai akurasi 96% pada data uji.

✅ Sistem mampu mendeteksi SMS spam secara efektif dan dapat digunakan sebagai solusi spam filtering sederhana.

---

## 🛠️ Technologies Used

* Python
* Google Colab
* Pandas
* NumPy
* Scikit-Learn
* Sastrawi
* Matplotlib
* Seaborn

---
atau data uji.
