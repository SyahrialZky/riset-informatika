# ☕ Analisis Komparatif Model Hibrida untuk Peramalan Permintaan F&B

## 🧾 Informasi Umum
**Judul Penelitian:**  
Analisis Komparatif Model **ARIMA**, **XGBoost**, dan **Model Hibrida ARIMA–XGBoost** untuk Peramalan Permintaan Kategori Menu pada Data Transaksi Kedai Kopi  

**Status:** Draft Proposal (Riset Informatika)  
**Metode Utama:** Hybrid Additive Modeling (ARIMA + XGBoost)  
**Dataset:** Data Transaksi Kedai Kopi (Simulasi Kaggle)  

---

## 💡 Latar Belakang & Urgensi
Penelitian ini berangkat dari tantangan **volatilitas permintaan** pada sektor **Food & Beverage (F&B)** yang sangat dipengaruhi oleh tren media sosial dan perilaku konsumen digital.  

Kegagalan peramalan yang akurat dapat menyebabkan:
- ⚠️ **Penurunan Kualitas Layanan:** Waktu tunggu pelanggan meningkat, stok produk tidak konsisten.  
- ⚙️ **Inefisiensi Operasional:** Hambatan pada *just-in-time production* dan alokasi sumber daya.  

**Urgensi Metodologis:**  
Data permintaan F&B mengandung dua jenis komponen:
- **Linier** → Pola musiman dan tren dasar (*ditangani ARIMA*)  
- **Non-Linier** → Anomali akibat tren viral, event, cuaca (*ditangani XGBoost*)  

Model tunggal tidak mampu mengoptimalkan keduanya secara bersamaan, sehingga dibutuhkan pendekatan **Hibrida (Hybrid Model)** untuk meningkatkan akurasi prediksi dan mendukung keputusan bisnis yang adaptif.

---

## ❓ Rumusan Masalah & Tujuan Penelitian

### Rumusan Masalah
1. Bagaimana akurasi peramalan permintaan kategori menu jika menggunakan **Model ARIMA tunggal**?  
2. Bagaimana akurasi peramalan permintaan kategori menu jika menggunakan **Model XGBoost tunggal** (dengan *feature engineering* yang komprehensif)?  
3. Apakah **Model Hibrida ARIMA–XGBoost** dapat menghasilkan akurasi yang lebih tinggi (berdasarkan **RMSE** dan **MAPE**) dibandingkan model tunggal?

### Tujuan Penelitian
- Menganalisis akurasi peramalan permintaan kategori menu menggunakan **Model ARIMA Tunggal**.  
- Menganalisis akurasi peramalan permintaan kategori menu menggunakan **Model XGBoost Tunggal**.  
- Membandingkan hasil dan menguji efektivitas **Model Hibrida (ARIMA–XGBoost)** terhadap model tunggal.

---

## 🚧 Batasan Masalah (Scope)
Penelitian ini dibatasi oleh hal-hal berikut:

| Aspek | Batasan |
|-------|----------|
| **Sumber Data** | Menggunakan dataset simulasi dari Kaggle (transaksi kedai kopi). |
| **Variabel Target** | Kuantitas permintaan harian per kategori menu (mis. *Coffee*, *Bakery*). |
| **Metode Komparasi** | Hanya membandingkan tiga model: ARIMA, XGBoost, dan Hibrida ARIMA–XGBoost. |
| **Variabel Eksternal** | Menggunakan *proxy variables* simulatif (mis. promosi, tren sosial) sebagai faktor non-linier. |

---

## 📚 Tinjauan Pustaka & Gap Analysis

### Analisis Celah (The Research Gap)

| Model | Kelemahan | Solusi Hibrida |
|--------|------------|----------------|
| **ARIMA (Linier)** | Tidak dapat menangkap lonjakan permintaan mendadak atau anomali non-linier. | Mengisolasi komponen linier dan menyerahkan residual ke XGBoost. |
| **XGBoost (Non-Linier)** | Kurang optimal dalam menangkap *time dependence* jangka panjang. | Memodelkan komponen non-linier residual dan menggabungkan fitur waktu serta proxy tren. |

**Justifikasi:**  
Residual dari model ARIMA masih mengandung pola non-linier yang dapat dimodelkan ulang menggunakan algoritma *machine learning* (XGBoost). Model hibrida mampu mengekstraksi dua komponen — linier dan non-linier — secara simultan untuk meningkatkan akurasi.

---

## ⚙️ Metodologi Penelitian (Additive Hybrid Modeling)

Metodologi penelitian ini menggunakan **Analisis Kuantitatif Eksperimental** dengan pendekatan **Additive Hybrid Modeling**.

### Prosedur Eksperimen

**1. Pra-Pemodelan**
- Agregasi data menjadi **deret waktu harian** per kategori menu.  
- Uji **stasioneritas (ADF Test)** untuk menentukan kebutuhan differencing.  

**2. Feature Engineering**
- Pembuatan **fitur waktu** (hari, bulan, libur).  
- Pembuatan **lagged features** (H–1, H–7, dst.).  
- Penambahan **proxy variables** (mis. diskon, tren viral) jika tersedia.  

**3. Langkah Pemodelan**
- **Langkah ARIMA (Linier):** Melatih ARIMA → menghasilkan \( \hat{L_t} \) dan residual \( R_t \).  
- **Langkah XGBoost (Non-Linier):** Melatih XGBoost dengan \( R_t \) sebagai target → menghasilkan \( \hat{N_t} \).  
- **Prediksi Final (Additive Hybrid):**  
  \[
  \hat{Y_t} = \hat{L_t} + \hat{N_t}
  \]

### Evaluasi Kinerja
Evaluasi dilakukan dengan dua metrik utama:

| Metrik | Keterangan |
|---------|------------|
| **RMSE (Root Mean Squared Error)** | Mengukur besar rata-rata kesalahan kuadrat (semakin kecil semakin baik). |
| **MAPE (Mean Absolute Percentage Error)** | Mengukur tingkat akurasi dalam bentuk persentase. |

---

## 📌 Daftar Pustaka (Referensi Kunci)

| No | Referensi | Kontribusi |
|----|------------|-------------|
| [1] | Al Ghozali, M. W., Swasti, Y. K., & W. K., B. S. D. (2023). *Analisis Komparatif Model ARIMA, XGBOOST Dan Pendekatan Hybrid ARIMA-XGBOOST Untuk Prediksi Permintaan Proyek IT.* Jurnal Inovasi dan Teknologi Komputer, 8(3), 15848. | Studi komparatif lokal, referensi utama pendekatan hibrida. |
| [2] | Box, G. E. P., & Jenkins, G. M. (1970). *Time Series Analysis: Forecasting and Control.* San Francisco: Holden-Day. | Fondasi teoretis model ARIMA. |
| [3] | Chen, T., & Guestrin, C. (2016). *XGBoost: A Scalable Tree Boosting System.* ACM SIGKDD Conference. | Konsep utama algoritma XGBoost. |
| [4] | Zhang, G. P. (2003). *Time Series Forecasting Using a Hybrid ARIMA and Artificial Neural Network Model.* Int. Journal of Forecasting, 18(1), 123–146. | Dasar teori model hibrida residual. |
| [5] | Wang, H., Zhao, X., & Cheng, Y. (2020). *Short-term Load Forecasting for Industrial Parks Using a Hybrid Model of ARIMA and XGBoost.* Energy, 208, 118360. | Implementasi hybrid ARIMA–XGBoost. |
| [6] | Li, J., & Wang, Q. (2024). *Optimizing Retail Inventory and Sales Through Advanced Time Series Forecasting Using Fine-Tuned PrGB Regressor.* IEEE Access, 12, 1–10. | Aplikasi forecasting lanjutan pada retail. |
| [7] | Gunasekaran, A., Rai, B. K., & Sharma, V. (2020). *E-commerce and Supply Chain Management: Current Status and Future Directions.* Int. Journal of Logistics Management. | Relevansi bisnis e-commerce & F&B. |
| [8] | Kotler, P., & Keller, K. L. (2021). *Marketing Management.* Harlow: Pearson Education. | Landasan perilaku konsumen & pemasaran F&B. |

---



