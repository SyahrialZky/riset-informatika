# BAB III: METHODOLOGY (Metodologi Penelitian)

Bab ini menyajikan desain eksperimen, prosedur teknis, dan alat evaluasi yang digunakan untuk mencapai tujuan penelitian, yaitu membandingkan efektivitas **Model Hibrida ARIMA–XGBoost** terhadap model tunggal.

---

## 3.1 Desain Penelitian
Penelitian ini menggunakan pendekatan **Analisis Kuantitatif Eksperimental** dengan desain **komparatif**, yang bertujuan untuk mengukur secara numerik kinerja tiga model peramalan pada dataset yang sama guna memvalidasi hipotesis bahwa **model hibrida memiliki akurasi superior**.

### 3.1.1 Pendekatan Hibrida Aditif (Additive Hybrid Modeling Approach)
Metodologi utama yang digunakan adalah **Additive Hybrid Modeling**, berdasarkan prinsip **dekomposisi sinyal** [8].  
Model ini mengasumsikan bahwa sinyal permintaan total ($Y_t$) dapat dipisahkan menjadi dua komponen utama:

\[
Y_t = L_t + N_t
\]

- $L_t$ → Komponen linier, dimodelkan oleh **ARIMA**.  
- $N_t$ → Komponen non-linier, dimodelkan oleh **XGBoost** dari residual ARIMA.  

Dalam implementasi:
1. ARIMA memodelkan $L_t$ dan menghasilkan residual ($e_t$).  
2. XGBoost memodelkan $N_t$ dari residual tersebut.  
3. Prediksi akhir dihitung sebagai:  
   \[
   \hat{Y}_t = \hat{L}_t + \hat{N}_t
   \]

---

### 3.1.2 Desain Eksperimen Komparatif
Penelitian ini membandingkan performa tiga desain model utama berikut:

| Jenis Model | Peran | Justifikasi |
|:---|:---|:---|
| **Model 1 – ARIMA Tunggal** | *Baseline* linier | Mengukur kemampuan model statistik klasik dalam menangkap pola *autocorrelation* dan musiman. |
| **Model 2 – XGBoost Tunggal** | *Baseline* non-linier | Mengukur kemampuan *machine learning* dalam memanfaatkan fitur eksternal dan menangkap anomali non-linier. |
| **Model 3 – Hibrida ARIMA–XGBoost** | **Model Usulan** | Menguji efektivitas kombinasi dua pendekatan (statistik dan *machine learning*) dalam satu sistem peramalan. |

---

## 3.2 Prosedur Implementasi Teknis (Method)
Langkah-langkah teknis penelitian mengikuti alur **kerangka berpikir metodologis** yang dirancang pada Bab I dan II.

### 3.2.1 Pengumpulan dan Pra-Pemrosesan Data
1. **Sumber Data:** Dataset transaksi kedai kopi dari **Kaggle (simulasi)**.  
2. **Agregasi Data:** Data transaksi dikonversi menjadi **deret waktu harian** untuk setiap **kategori menu** sebagai variabel target ($Q_t$).  
3. **Penanganan Nilai Kosong:** Hari tanpa transaksi diisi dengan nilai nol ($Q_t = 0$) agar deret waktu bersifat kontinu.  
4. **Pembagian Data:** Dataset dibagi menjadi **80% data latih** dan **20% data uji** secara **kronologis (time-based splitting)**.

---

### 3.2.2 Rekayasa Fitur (Feature Engineering)
Tahapan ini penting terutama untuk Model 2 (XGBoost Tunggal) dan Model 3 (Hibrida ARIMA–XGBoost), yang memerlukan fitur-fitur tambahan untuk menangkap pola kompleks.

| Jenis Fitur | Tujuan | Contoh Variabel |
|:---|:---|:---|
| **Temporal & Lagged Features** | Menangkap musiman dan ketergantungan waktu antar periode. | `Day_of_Week`, `Month`, `Permintaan_lag_7` |
| **Proxy Eksternal** | Menangkap lonjakan non-linier akibat faktor eksternal. | `Is_Holiday` (biner), `Avg_Temp_Day` (cuaca simulasi), `Is_Viral_Promo` (tren sosial) |

---

### 3.2.3 Pemodelan Linier (Langkah Hibrida 1)
1. **Uji Stasioneritas:** Dilakukan **ADF Test** (*Augmented Dickey-Fuller*) untuk memastikan data stasioner. Jika tidak, diterapkan *differencing* ($d$).  
2. **Pemilihan Parameter:** Parameter ARIMA ($p$, $q$) ditentukan menggunakan **ACF/PACF Plot** atau fungsi `auto_arima()`.  
3. **Residual Generation:** Setelah ARIMA dilatih, dihitung **residual ($e_t = Y_t - \hat{L}_t$)** yang menjadi **target baru** untuk model XGBoost.

---

### 3.2.4 Pemodelan Non-Linier (Langkah Hibrida 2)
1. **Penargetan Residual:** Residual $e_t$ digunakan sebagai variabel target untuk pelatihan model XGBoost.  
2. **Input Fitur:** Model XGBoost dilatih menggunakan seluruh fitur hasil *feature engineering* (temporal, lagged, dan proxy eksternal).  
3. **Output:** Model menghasilkan prediksi residual non-linier ($\hat{N}_t$).

---

### 3.2.5 Peramalan dan Kombinasi Akhir
Prediksi akhir dari Model Hibrida diperoleh dengan menjumlahkan hasil kedua model:

\[
\hat{Y}_t = \hat{L}_t \text{ (ARIMA)} + \hat{N}_t \text{ (XGBoost)}
\]

Nilai $\hat{Y}_t$ menjadi hasil akhir peramalan yang memadukan pola linier dan non-linier pada data permintaan.

---

## 3.3 Evaluasi Kinerja (Performance Metrics)
Evaluasi dilakukan terhadap ketiga model menggunakan dua metrik utama yang umum digunakan dalam *time series forecasting*:

| Metrik | Deskripsi | Relevansi |
|:---|:---|:---|
| **Root Mean Squared Error (RMSE)** | Mengukur rata-rata besar kesalahan prediksi (dalam satuan asli variabel target). | Sensitif terhadap *outlier*, penting untuk data F&B yang bersifat *volatile*. |
| **Mean Absolute Percentage Error (MAPE)** | Mengukur akurasi prediksi dalam bentuk persentase. | Mudah diinterpretasikan secara bisnis dan berguna untuk pengambilan keputusan operasional. |

### Kriteria Keberhasilan
Model Hibrida dinilai **berhasil** apabila:
- Nilai **RMSE dan MAPE** lebih rendah secara signifikan dibandingkan model ARIMA dan XGBoost tunggal.  
- Peningkatan akurasi terukur membuktikan bahwa kombinasi kedua model memberikan hasil peramalan yang lebih efektif dan stabil.

---

## Ringkasan Bab III
| Tahap | Fokus | Output Utama |
|:---|:---|:---|
| **Desain Penelitian** | Menentukan pendekatan eksperimen dan model yang dibandingkan. | Desain komparatif dengan tiga model utama. |
| **Pra-Pemrosesan Data** | Mempersiapkan dataset agar siap dipakai untuk peramalan. | Data bersih dan terstruktur dalam format deret waktu. |
| **Feature Engineering** | Membuat variabel tambahan untuk menangkap pola kompleks. | Fitur temporal, lag, dan proxy eksternal. |
| **Pemodelan Linier & Non-Linier** | Mengembangkan dua tahap hibrida: ARIMA → XGBoost. | Model Hibrida ARIMA–XGBoost. |
| **Evaluasi Kinerja** | Mengukur akurasi hasil peramalan. | Nilai RMSE dan MAPE untuk validasi hipotesis. |

---

> 📄 **Status:** Bab III – Methodology  
> **Penulis:** *Syahrial Rizky*  
> **Program Studi:** Informatika – UPN “Veteran” Jawa Timur  
> **Mata Kuliah:** Riset Informatika  
> **Tahun Akademik:** 2025
