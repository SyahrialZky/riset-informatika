# ☕ Implementasi Model Hibrida ARIMA-XGBOOST untuk Peramalan Permintaan Kategori Menu pada Data Transaksi Kedai Kopi

## 📘 Deskripsi Proyek
Repositori ini berisi konsep awal proposal skripsi dengan fokus pada **implementasi model hibrida ARIMA–XGBoost** untuk **peramalan permintaan (demand forecasting)** pada **data transaksi kedai kopi (F&B Industry)**.  
Proyek ini merupakan bagian dari mata kuliah **Riset Informatika**, dengan topik utama **Perumusan Masalah Penelitian (Research Problem Formulation)**.

---

## 🧩 1. Pembedahan Perumusan Masalah

Proses perumusan masalah mengikuti tujuh langkah logis agar fondasi penelitian kokoh dan terukur.

### 1.1 Identify Broad Field
| Bidang Luas | Fokus |
|--------------|--------|
| **Data Science & AI** | Penerapan teknik Machine Learning untuk prediksi bisnis |
| **Operation Research** | Optimalisasi manajemen rantai pasok dan inventaris |

---

### 1.2 Dissect the Subareas
Bidang penelitian dibagi menjadi tiga area yang saling beririsan:

- **Time Series Forecasting** → menggunakan data historis transaksi penjualan.  
- **Hybrid Modeling** → menggabungkan kekuatan model statistik dan machine learning.  
- **F&B Analytics** → analisis permintaan yang *volatile* dan sensitif terhadap tren sosial.

---

### 1.3 Select Interested Sub-Area
Fokus penelitian pada:
> **Advanced Time Series Forecasting** dengan model **Hibrida (ARIMA–XGBoost)**  
> untuk mengatasi data F&B yang memiliki komponen linier dan non-linier secara simultan.

---

## 🎯 2. Rumusan Masalah dan Tujuan Penelitian

### 2.1 Pertanyaan Penelitian (Research Questions)
1. Bagaimana akurasi peramalan permintaan kategori menu jika menggunakan **model ARIMA tunggal** (linier baseline)?
2. Bagaimana akurasi peramalan permintaan kategori menu jika menggunakan **model XGBoost tunggal** (non-linier dengan feature engineering)?
3. Apakah **model hibrida ARIMA–XGBoost** mampu mencapai akurasi yang lebih tinggi (diukur dengan RMSE dan MAPE) dibandingkan kedua model tunggal?

---

### 2.2 Tujuan Penelitian (Research Objectives)
- Menganalisis dan menghitung akurasi peramalan menggunakan **ARIMA tunggal**.  
- Menganalisis dan menghitung akurasi peramalan menggunakan **XGBoost tunggal**.  
- Membandingkan **kinerja ARIMA, XGBoost, dan model Hibrida** untuk menguji efektivitas pendekatan hybrid forecasting.

---

## ✅ 3. Assessment & Double Check

### 3.1 Assessment of Objectives
| Kriteria | Status | Catatan |
|-----------|---------|----------|
| **Feasible** | ✅ | Algoritma dan dataset tersedia (Python / Google Colab) |
| **Relevant** | ✅ | Relevan dengan manajemen inventori dan riset informatika |
| **Significant** | ✅ | Membuktikan efektivitas metode hibrida untuk data permintaan yang volatil |

---

### 3.2 Double Check
Konsistensi antara **judul, pertanyaan, dan tujuan** sudah terverifikasi.  
Metode Hibrida dipilih karena paling sesuai untuk menangani karakteristik **volatilitas permintaan pada sektor F&B**.

---

## 🛣️ 4. Langkah Konseptual Selanjutnya
Tahapan berikutnya berfokus pada:

### 🔹 Gap Research Analysis (Bab II)
- Mengidentifikasi dan mengutip jurnal yang menunjukkan **kelemahan model tunggal** (ARIMA / XGBoost).  
- Membuktikan kebutuhan pendekatan **Hybrid Forecasting** pada domain F&B.

### 🔹 Methodology (Bab III)
- Menjabarkan **langkah teknis implementasi**:
  - Data preprocessing
  - Feature engineering
  - Pembentukan **model aditif hibrida (ARIMA + XGBoost)**

---

## ⚙️ Tools & Dataset
- **Dataset:** Simulasi *Coffee Shop Sales* (Kaggle)
- **Platform:** Google Colab / Jupyter Notebook
- **Libraries:** `pandas`, `numpy`, `scikit-learn`, `statsmodels`, `xgboost`, `matplotlib`

---

## 📚 Mata Kuliah
> **Riset Informatika – Universitas Pembangunan Nasional “Veteran” Jawa Timur**

---

## 👨‍💻 Penulis
**Nama:** *Syahrial Rizky*  
**Topik:** *Hybrid Forecasting in F&B Demand Prediction*  
**Status:** *Konsep Awal Proposal Skripsi / UTS Simulasi Bab 1–3*

---

## 🧾 Lisensi
Repositori ini bersifat akademik dan hanya digunakan untuk kepentingan pembelajaran dan penelitian.  
Lisensi mengikuti kebijakan institusi dan etika penelitian UPN Veteran Jawa Timur.

---
