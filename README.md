# ☕ Implementasi Model Hibrida ARIMA–XGBOOST untuk Peramalan Permintaan Kategori Menu pada Data Transaksi Kedai Kopi

## 📘 Deskripsi Umum
Repositori ini merupakan bagian dari **penyusunan Proposal Skripsi** untuk mata kuliah **Riset Informatika**.  
Penelitian ini berfokus pada penerapan **model hibrida ARIMA–XGBoost** dalam **peramalan permintaan (demand forecasting)** pada **kategori menu kedai kopi (F&B Industry)**, yang bersifat *volatile* dan sensitif terhadap tren musiman maupun sosial.

Struktur penyusunan proposal mengikuti tiga bab utama:
1. **Bab I – Research Problem Formulation (Perumusan Masalah Penelitian)**
2. **Bab II – Gap Research Analysis & Mind Map**
3. **Bab III – Methodology**

---

## 🧩 Bab I — Research Problem Formulation

Bab ini membedah proses konseptual awal penelitian menggunakan tujuh langkah logis yang menjadi dasar formulasi masalah penelitian.

### 1.1 Identify Broad Field
| Bidang Luas | Fokus |
|--------------|--------|
| **Data Science & Artificial Intelligence** | Penerapan Machine Learning untuk prediksi bisnis |
| **Operation Research** | Optimalisasi manajemen rantai pasok dan inventaris |

---

### 1.2 Dissect the Subareas
Bidang penelitian dibagi menjadi tiga area utama yang saling beririsan:

- **Time Series Forecasting** – menggunakan data historis transaksi penjualan untuk analisis pola waktu.  
- **Hybrid Modeling** – menggabungkan kekuatan model statistik dan machine learning dalam satu pendekatan terpadu.  
- **F&B Analytics** – analisis permintaan yang *volatile* dan dinamis akibat faktor eksternal seperti tren sosial atau musim.

---

### 1.3 Select Interested Sub-Area
Penelitian difokuskan pada:
> **Advanced Time Series Forecasting dengan Model Hibrida (ARIMA–XGBoost)**  
> untuk menangani data penjualan F&B yang mengandung komponen **linier dan non-linier** secara simultan.

---

### 1.4 Raise Research Question
1. Bagaimana akurasi peramalan permintaan kategori menu jika menggunakan **Model ARIMA tunggal** (baseline linier)?  
2. Bagaimana akurasi peramalan permintaan kategori menu jika menggunakan **Model XGBoost tunggal** (non-linier dengan feature engineering)?  
3. Apakah **Model Hibrida ARIMA–XGBoost** dapat menghasilkan akurasi (RMSE, MAPE) yang lebih tinggi dibandingkan kedua model tunggal tersebut?

---

### 1.5 Formulate Objective
- Menganalisis akurasi peramalan permintaan kategori menu menggunakan **Model ARIMA tunggal**.  
- Menganalisis akurasi peramalan permintaan kategori menu menggunakan **Model XGBoost tunggal**.  
- Membandingkan hasil dan menguji efektivitas **Model Hibrida (ARIMA–XGBoost)** terhadap model tunggal.

---

### 1.6 Assessment of Objectives
| Kriteria | Status | Catatan |
|-----------|---------|----------|
| **Feasible** | ✅ | Algoritma dan dataset tersedia (Python/Google Colab) |
| **Relevant** | ✅ | Relevan dengan masalah inventory management dan forecasting F&B |
| **Significant** | ✅ | Kontribusi riset dalam pembuktian efektivitas metode hibrida pada data yang volatil |

---

### 1.7 Double Check
Konsistensi antara **judul, pertanyaan penelitian, dan tujuan** telah terverifikasi.  
Pemilihan metode hibrida menjadi solusi ideal untuk mengatasi permasalahan **volatilitas dan non-linearitas** permintaan menu pada bisnis F&B.

---

## 🌉 Bab II — Gap Research Analysis (Analisis Celah Penelitian)

Bab ini berfungsi untuk menjustifikasi **pemilihan Model Hibrida ARIMA–XGBoost** sebagai solusi terbaik dengan membandingkan kekuatan dan kelemahan model tunggal yang ada dalam literatur ilmiah.

---

### 2.1 Status Quo: Kekuatan dan Kelemahan Model Tunggal

#### 🔹 A. Model Linier (ARIMA)
| Aspek | Penjelasan |
|-------|-------------|
| **Kekuatan** ([3]) | - Koefisien model mudah dijelaskan (*interpretable*).<br>- Fondasi teori kuat untuk memodelkan autocorrelation dan pola musiman dasar. |
| **Kelemahan** ([5]) | - Asumsi linieritas tidak dapat menangkap hubungan non-linier dan *outlier* kompleks.<br>- Sensitif terhadap stasioneritas; proses differencing dapat menghilangkan tren penting. |
| **Celah Penelitian** | Gagal memproses lonjakan permintaan akibat **viral marketing** atau **event mendadak** yang umum terjadi di F&B. |

---

#### 🔹 B. Model Non-Linier (XGBoost / ML Lain)
| Aspek | Penjelasan |
|-------|-------------|
| **Kekuatan** ([4]) | - Akurasi tinggi & robust terhadap data non-linier.<br>- Dapat mengintegrasikan variabel eksternal seperti cuaca, promosi, atau aktivitas media sosial. |
| **Kelemahan** ([5], [7]) | - Sangat bergantung pada *feature engineering* yang tepat.<br>- Tidak secara eksplisit memodelkan struktur deret waktu (kurang optimal untuk *time dependence*). |
| **Celah Penelitian** | Kehilangan **long-term memory** yang dapat ditangkap oleh ARIMA. |

---

### 2.2 Celah Penelitian (The Research Gap)

Dari hasil tinjauan, **tidak ada model tunggal** yang mampu mengelola **komponen linier dan non-linier secara bersamaan** dalam data transaksi F&B yang sangat dinamis.  

| Komponen | Karakteristik | Tantangan |
|-----------|----------------|------------|
| **Linier** | Pola permintaan stabil, jam sibuk, musiman harian/mingguan | Dapat dimodelkan dengan ARIMA |
| **Non-Linier** | Lonjakan mendadak akibat tren sosial, cuaca, atau event | Dapat dimodelkan dengan XGBoost |

**Justifikasi Metodologis:**  
Model Hibrida hadir untuk menjembatani celah ini.  
Menurut Zhang (2003) [5], residual dari model linier (ARIMA) masih mengandung struktur non-linier yang dapat dimodelkan ulang menggunakan *Machine Learning* (XGBoost). Dengan memanfaatkan residual tersebut, kombinasi **ARIMA + XGBoost** mampu mengekstraksi kedua komponen dengan optimal.

---

### 2.3 Novelty Penelitian (Kebaruan)
Penelitian ini memberikan nilai tambah dengan tiga aspek utama:

1. **Metode:**  
   Implementasi **Hybrid Model ARIMA–XGBoost dengan struktur Additive Decomposition (Linier + Non-Linier)** sebagai strategi peramalan yang lebih adaptif.

2. **Objek Data:**  
   Fokus pada **peramalan kategori menu** (bukan total penjualan), sehingga menghasilkan *forecast* yang lebih detail dan relevan untuk manajemen stok.

3. **Variabel Kontekstual:**  
   Mengintegrasikan variabel eksternal (*proxy variable*) yang mencerminkan pengaruh **tren sosial, promosi, dan cuaca** dalam model XGBoost.

---

### 2.4 Referensi Kunci (Format IEEE)
| No | Referensi | Dukungan |
|----|------------|-----------|
| [3] | Box & Jenkins, *Time Series Analysis: Forecasting and Control*, 1970 | Fondasi teori ARIMA (model linier) |
| [4] | Chen & Guestrin, *XGBoost: A Scalable Tree Boosting System*, 2016 | Keunggulan XGBoost dalam data non-linier |
| [5] | Zhang, *Time Series Forecasting Using a Hybrid ARIMA and Neural Network Model*, 2003 | Teori dasar model hibrida (residual mengandung struktur non-linier) |
| [6] | Wang et al., 2020 | Aplikasi Hibrida ARIMA–XGBoost pada data energi |
| [7] | Kim & Lee, 2021 | Aplikasi Hibrida ARIMA–XGBoost pada data transportasi & volatilitas |

> Catatan: Referensi [6]–[7] menunjukkan bahwa metode hibrida telah teruji di domain lain, memperkuat validitas pemilihannya untuk sektor F&B.

---

## 🧭 Bab III — Methodology (Rencana Pengembangan)

Bab III akan menjelaskan **kerangka metodologi teknis**, mencakup:
- **Dataset:** Coffee Shop Sales (Kaggle) atau data transaksi kedai kopi aktual.  
- **Preprocessing:** pembersihan data, normalisasi, dan transformasi log.  
- **Feature Engineering:** pembuatan fitur waktu (hari, bulan, musim, promosi, tren).  
- **Modeling Steps:**  
  1. Penerapan ARIMA untuk menangkap pola linier.  
  2. Penerapan XGBoost terhadap residual ARIMA untuk pola non-linier.  
  3. Evaluasi gabungan menggunakan metrik RMSE & MAPE.  
- **Tools:** Python, Google Colab, `pandas`, `numpy`, `statsmodels`, `xgboost`, `scikit-learn`, `matplotlib`.

---

## ⚙️ Tools & Dataset
- **Dataset:** [Coffee Shop Sales – Kaggle (Simulasi)](https://www.kaggle.com/code/ahmedabbas757/coffee-shop-sales)  
- **Platform:** Google Colab / Jupyter Notebook  
- **Libraries:** `pandas`, `numpy`, `statsmodels`, `xgboost`, `sklearn`, `matplotlib`

---

## 🧾 Informasi Akademik
- **Mata Kuliah:** Riset Informatika  
- **Program Studi:** Informatika, UPN Veteran Jawa Timur  
- **Penulis:** *Syahrial Rizky*  
- **Status:** *Proposal Skripsi – Bab I & Bab II (Research Problem + Gap Analysis)*

---

## 📂 Struktur Folder (Rencana)
