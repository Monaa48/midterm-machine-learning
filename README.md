# Midterm Exam: Machine Learning Portfolio

**Nama:** ANOM NUR MAULID
**NIM:** 1103223193
**Kelas:** TK-46-01

## 📋 Overview
Repository ini merupakan submisi resmi untuk Ujian Tengah Semester (UTS) mata kuliah **Machine Learning**. Proyek ini mendemonstrasikan penerapan pipeline *End-to-End Machine Learning* pada tiga domain masalah yang berbeda:
1.  **Supervised Learning (Classification):** Deteksi Transaksi Penipuan (*Fraud Detection*).
2.  **Supervised Learning (Regression):** Prediksi Tahun Rilis Lagu.
3.  **Unsupervised Learning (Clustering):** Segmentasi Pelanggan Kartu Kredit.

Setiap proyek mencakup tahapan *Data Loading*, *Preprocessing*, *Feature Engineering*, *Model Training*, *Hyperparameter Tuning*, hingga *Evaluation*.

---

## 🚀 Project 1: Fraud Detection (Classification)

### 1. Objective
Tujuan utama proyek ini adalah membangun model Machine Learning yang mampu mendeteksi probabilitas transaksi penipuan (*fraud*) dengan akurasi tinggi, meskipun data memiliki ketimpangan kelas yang ekstrem (*imbalanced data*).

### 2. Dataset
* **Sumber Data:** IEEE-CIS Fraud Detection Dataset.
* **File:** `train_transaction.csv` dan `train_identity.csv`.
* **Fitur:** Informasi transaksi (jumlah, kartu, alamat) dan identitas digital (device info, email).

### 3. Methodology & Pipeline
* **Data Handling:**
    * **Merging:** Menggabungkan tabel `transaction` dan `identity` menggunakan `left join` untuk memperkaya fitur (total 780+ kolom).
    * **Optimization:** Menggunakan library **Polars** untuk pembacaan data cepat dan teknik **Sampling (100k baris)** untuk efisiensi memori (RAM) di Google Colab.
* **Preprocessing:**
    * *Feature Selection:* Menghapus kolom ID (`TransactionID`) dan Waktu (`TransactionDT`).
    * *Encoding:* Mengubah fitur kategorikal (string) menjadi numerik menggunakan Label Encoding.
    * *Handling Missing Values:* Mengisi nilai *null* dengan konstanta `-1`.
* **Modeling:**
    * **Algoritma:** Random Forest Classifier.
    * **Imbalance Handling:** Menggunakan parameter `class_weight='balanced'` agar model memberikan bobot lebih pada kelas minoritas (Fraud).
    * **Hyperparameter Tuning:** Mengatur `n_estimators=100` dan `max_depth=15` untuk mencegah *overfitting*.

### 4. Results
* **Metric Utama:** AUC-ROC Score.
* **Performance:** Model berhasil mencapai **AUC Score ~0.87** pada data validasi.
* **Kesimpulan:** Random Forest efektif menangani data *tabular* yang kompleks dan *high-dimensional* tanpa memerlukan scaling yang rumit.

---

## 🎵 Project 2: Song Year Prediction (Regression)

### 1. Objective
Memprediksi tahun rilis sebuah lagu secara kontinu (nilai numerik) berdasarkan 90 fitur audio (*timbre features*) yang diekstraksi dari sinyal musik.

### 2. Dataset
* **Sumber Data:** `midterm-regresi-dataset.csv` (Million Song Dataset subset).
* **Struktur:** Kolom pertama adalah Target (Tahun), kolom 2-91 adalah Fitur Audio.

### 3. Methodology & Pipeline
* **Preprocessing:**
    * Melakukan standarisasi fitur menggunakan **StandardScaler** untuk menyamakan rentang nilai data audio.
    * Membagi data menjadi Training Set (80%) dan Test Set (20%).
* **Modeling & Tuning:**
    * **Baseline Model:** Linear Regression (Model sederhana sebagai tolak ukur).
    * **Tuned Model:** Random Forest Regressor dengan tuning:
        * `n_estimators=100` (Jumlah pohon keputusan).
        * `max_depth=20` (Membatasi kedalaman pohon).
        * `n_jobs=-1` (Parallel processing).

### 4. Results
* **Metric Utama:** Mean Absolute Error (MAE) - Rata-rata selisih tahun prediksi dengan tahun asli.
* **Linear Regression:** MAE ~6.78 Tahun.
* **Random Forest (Tuned):** MAE ~6.45 Tahun.
* **Kesimpulan:** Hyperparameter tuning pada Random Forest berhasil menurunkan tingkat kesalahan prediksi, membuktikan bahwa hubungan antara fitur audio dan tahun rilis bersifat non-linear.

---

## 👥 Project 3: Customer Segmentation (Clustering)

### 1. Objective
Mengidentifikasi kelompok (*cluster*) pelanggan kartu kredit yang memiliki pola perilaku serupa untuk membantu strategi pemasaran dan manajemen risiko.

### 2. Dataset
* **Sumber Data:** `clusteringmidterm.csv`.
* **Fitur Kunci:** `BALANCE` (Saldo), `PURCHASES` (Pembelian), `CASH_ADVANCE` (Tarik Tunai), `CREDIT_LIMIT`.

### 3. Methodology & Pipeline
* **Preprocessing:**
    * Mengisi *missing values* pada `MINIMUM_PAYMENTS` dan `CREDIT_LIMIT` dengan nilai rata-rata (mean).
    * Melakukan normalisasi data menggunakan **StandardScaler** agar fitur dengan nilai besar (ribuan) tidak mendominasi fitur nilai kecil (desimal).
* **Modeling:**
    * **Algoritma:** K-Means Clustering.
    * **Optimasi K:** Menggunakan **Elbow Method** untuk mencari jumlah cluster optimal berdasarkan penurunan nilai *Inertia*.

### 4. Results
* **Jumlah Cluster Optimal (K):** 4.
* **Interpretasi Segmen:**
    1.  **Cluster 0 (High Cash Advance):** Nasabah dengan saldo tinggi yang sering melakukan tarik tunai (berisiko tinggi).
    2.  **Cluster 1 (Low Activity):** Nasabah pasif, transaksi dan saldo rendah.
    3.  **Cluster 2 (Big Spenders):** Nasabah yang aktif berbelanja retail/cicilan dengan limit tinggi (target promo belanja).
    4.  **Cluster 3 (Average Users):** Nasabah pengguna rata-rata dengan aktivitas moderat.

---

## 🛠️ How to Run
1.  Buka file notebook (`.ipynb`) yang tersedia di repository ini menggunakan **Google Colab**.
2.  Pastikan Runtime diatur ke **T4 GPU** (Opsional untuk ML, tapi disarankan untuk kecepatan).
3.  Jalankan sel kode secara berurutan (*Run All*).
4.  **Catatan:** Dataset akan diunduh secara otomatis di dalam notebook menggunakan perintah `!gdown`.

---
*Created for Midterm Exam - Machine Learning & Deep Learning Classes - Telkom University*