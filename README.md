#  Implementasi Model Hibrida ARIMA–XGBOOST untuk Peramalan Permintaan Kategori Menu pada Data Transaksi Kedai Kopi

##  Deskripsi Umum
Repositori ini merupakan bagian dari **penyusunan Proposal Skripsi** untuk mata kuliah **Riset Informatika**.  
Penelitian ini berfokus pada penerapan **model hibrida ARIMA–XGBoost** dalam **peramalan permintaan (demand forecasting)** pada **kategori menu kedai kopi (F&B Industry)**, yang bersifat *volatile* dan sensitif terhadap tren musiman maupun sosial.

Struktur penyusunan proposal mengikuti tiga bab utama:
1. **Bab I – Research Problem Formulation (Perumusan Masalah Penelitian)**
2. **Bab II – Gap Research Analysis & Mind Map**
3. **Bab III – Methodology**

---

##  Bab I — Research Problem Formulation

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

##  Bab II — Gap Research Analysis (Analisis Celah Penelitian)

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

##  Bab III — Methodology (Rencana Pengembangan)

Bab ini menjelaskan **prosedur rinci dan justifikasi ilmiah (metodologi)** yang digunakan untuk mencapai tujuan penelitian, yaitu membuktikan efektivitas model **Hybrid ARIMA–XGBoost** pada data permintaan kategori menu kedai kopi.

---

### 3.1 Metodologi Penelitian (Methodology)

Metodologi penelitian yang digunakan adalah **Analisis Kuantitatif Eksperimental** dengan pendekatan **Additive Hybrid Modeling Approach (Pendekatan Model Hibrida Aditif)**.

#### 3.1.1 Pendekatan Hibrida Additive (Metodologi Kunci)
Pendekatan ini didasarkan pada asumsi bahwa sinyal permintaan \( Y_t \) dapat dipisahkan menjadi dua komponen utama:

\[
Y_t = L_t + N_t
\]

di mana:
- \( L_t \): komponen **linier** (dimodelkan dengan ARIMA)
- \( N_t \): komponen **non-linier** (dimodelkan dengan XGBoost)
- \( e_t \): residual dari model ARIMA yang berperan sebagai perwakilan komponen non-linier.

Dengan demikian, model XGBoost akan mempelajari pola dari residual \( e_t \) untuk memperbaiki prediksi akhir.

#### 3.1.2 Desain Eksperimen
Penelitian ini akan membandingkan **tiga model peramalan** secara paralel pada dataset yang sama untuk membuktikan superioritas pendekatan hibrida:

| Jenis Model | Deskripsi | Tujuan |
|--------------|------------|---------|
| **Model Baseline** | ARIMA tunggal (model linier klasik) | Menjadi pembanding utama |
| **Model Pesaing** | XGBoost tunggal dengan fitur waktu dan lag | Menangkap hubungan non-linier |
| **Model Usulan** | Hibrida ARIMA–XGBoost | Kombinasi linier + non-linier untuk prediksi lebih akurat |

---

### 3.2 Metode Penelitian (Method)

Bagian ini menjelaskan **langkah-langkah teknis** yang digunakan dalam pelaksanaan eksperimen sesuai dengan kerangka berpikir yang dirancang pada Bab I dan II.

---

#### 3.2.1 Sumber Data
- **Dataset:** Coffee Shop Sales (Simulasi Kaggle)
- **Variabel Target:** Kuantitas permintaan harian (\( Q_t \)) per **kategori menu (\( C_i \))**
- **Pembagian Data:** Time-based splitting (80% data latih, 20% data uji)

---

#### 3.2.2 Tahap Pra-Pemrosesan (Data Preprocessing)
1. **Agregasi Data:**  
   Mengubah transaksi mentah menjadi **deret waktu harian** untuk setiap kategori menu (mis. `Permintaan_Kopi`, `Permintaan_Pastry`).
2. **Penanganan Missing Value:**  
   Mengisi nilai kosong dengan **0** untuk hari tanpa transaksi.
3. **Uji Stasioneritas (ADF Test):**  
   Menentukan parameter \( d \) (differencing) pada model ARIMA agar data menjadi stasioner tanpa kehilangan tren penting.

---

#### 3.2.3 Tahap Rekayasa Fitur (Feature Engineering)
Tahapan ini sangat penting untuk meningkatkan kinerja model **XGBoost** baik dalam mode tunggal maupun hibrida.

| Jenis Fitur | Deskripsi |
|--------------|------------|
| **Fitur Waktu** | Variabel dummy seperti `Hari_dalam_Minggu`, `Bulan`, `Hari_Libur` |
| **Lagged Features** | `Permintaan_H-1`, `Permintaan_H-7` untuk menangkap pola musiman |
| **Fitur Proxy Eksternal (Opsional)** | Representasi faktor eksternal seperti `diskon besar`, `event`, atau `tren viral` (jika tersedia di dataset) |

---

#### 3.2.4 Prosedur Pemodelan Hibrida ARIMA–XGBoost

##### Langkah 1: Pemodelan Linier (ARIMA)
- Menentukan parameter \( p, d, q \) menggunakan **ACF/PACF Plot** atau `auto_arima()`.  
- Melatih model ARIMA pada data latih \( Y_{train} \).  
- Menghasilkan prediksi linier \( \hat{L_t} \) dan menghitung **residual \( e_t = Y_t - \hat{L_t} \)**.

##### Langkah 2: Pemodelan Non-Linier (XGBoost)
- Menetapkan **residual \( e_t \)** sebagai target baru.  
- Melatih **XGBoost Regressor** menggunakan residual \( e_t \) dan fitur tambahan dari tahap *feature engineering*.  
- Menghasilkan prediksi non-linier \( \hat{N_t} \).

##### Langkah 3: Final Forecast
Menggabungkan hasil prediksi kedua model:
\[
\hat{Y_t} = \hat{L_t} + \hat{N_t}
\]

Sehingga hasil akhir mengandung kontribusi dari **komponen linier (ARIMA)** dan **non-linier (XGBoost)** secara aditif.

---

#### 3.2.5 Evaluasi Kinerja (Performance Metrics)

Dua metrik utama digunakan untuk mengevaluasi performa tiap model:

| Metrik | Formula | Interpretasi |
|---------|----------|---------------|
| **Root Mean Squared Error (RMSE)** | \(\sqrt{\frac{1}{n}\sum{(y_t - \hat{y_t})^2}}\) | Mengukur rata-rata kesalahan absolut kuadrat (sensitif terhadap outlier) |
| **Mean Absolute Percentage Error (MAPE)** | \(\frac{100\%}{n}\sum\left|\frac{y_t - \hat{y_t}}{y_t}\right|\) | Mengukur akurasi dalam persen, sangat relevan untuk analisis bisnis |

Model dengan nilai **RMSE & MAPE terendah** dianggap memberikan hasil prediksi paling akurat.

---

### 3.3 Ringkasan Alur Eksperimen

1. Import dan pra-pemrosesan data.  
2. Uji stasioneritas dan transformasi deret waktu.  
3. Bangun model baseline (ARIMA) → hasilkan residual.  
4. Lakukan feature engineering → bangun model XGBoost.  
5. Kombinasikan hasil ARIMA + XGBoost menjadi model hibrida.  
6. Evaluasi ketiga model menggunakan RMSE dan MAPE.  
7. Interpretasikan hasil dan validasi keunggulan model hibrida.

---


### 3.4 Visualisasi Rencana Proses (Konseptual)

<pre><code>
```mermaid
flowchart TD
A[Raw Data Transaksi] --> B[Data Preprocessing]
B --> C[ARIMA Model (Linier Component)]
C --> D[Residual Extraction]
D --> E[XGBoost Model (Non-Linier Component)]
E --> F[Hybrid Model (L + N)]
F --> G[Evaluation (RMSE, MAPE)]

</code></pre>
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
- **Status:** *Draft - Proposal *

---

## 📂 Struktur Folder (Rencana)
