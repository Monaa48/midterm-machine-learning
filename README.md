# Midterm Exam: Machine Learning (Clustering Task)

**Nama: ANOM NUR MAULID** 
**NIM: 1103223193** 
**Kelas: TK-46-01** 

## 1. Project Overview
Repository ini berisi penyelesaian tugas UTS mata kuliah Machine Learning. Tugas utama adalah melakukan **Customer Segmentation** (Clustering) menggunakan dataset penggunaan kartu kredit untuk mengelompokkan nasabah berdasarkan perilaku transaksi mereka.

## 2. Dataset Description
Dataset yang digunakan adalah `clusteringmidterm.csv`. Dataset ini memiliki fitur seperti:
- **BALANCE**: Saldo tagihan nasabah.
- **PURCHASES**: Total pembelanjaan.
- **CASH_ADVANCE**: Total penarikan tunai.
- **CREDIT_LIMIT**: Batas kredit.
- Dan fitur perilaku lainnya.

## 3. Methodology & Model
Pengerjaan dilakukan secara End-to-End Pipeline:
1.  **Data Preprocessing:**
    - Menghapus kolom `CUST_ID`.
    - Mengisi missing values (`NaN`) pada kolom `MINIMUM_PAYMENTS` dan `CREDIT_LIMIT` menggunakan rata-rata (mean).
    - Melakukan **StandardScaler** untuk menyamakan skala data.
2.  **Determination of K (Elbow Method):**
    - Menggunakan metode Elbow untuk mencari jumlah cluster optimal.
    - Ditemukan titik siku (elbow) pada **K = 4**.
3.  **Modeling:**
    - Menggunakan algoritma **K-Means Clustering** dengan `n_clusters=4`.

## 4. Analysis Results
Nasabah berhasil dikelompokkan menjadi 4 tipe karakteristik:
- **Cluster 0 (High Cash Advance):** Nasabah yang sering melakukan tarik tunai tapi jarang belanja barang.
- **Cluster 1 (Low Activity):** Nasabah pasif dengan transaksi dan saldo terendah.
- **Cluster 2 (Big Spenders):** Nasabah yang aktif berbelanja barang (retail) namun jarang tarik tunai.
- **Cluster 3 (Average Users):** Nasabah dengan penggunaan menengah.

## 5. How to Run
1.  Buka file notebook `.ipynb` di repository ini menggunakan Google Colab atau Jupyter Notebook.
2.  Pastikan dataset `clusteringmidterm.csv` tersedia.
3.  Jalankan setiap cell secara berurutan (Run All).

---