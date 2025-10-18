# BAB II: GAP RESEARCH ANALYSIS (Analisis Celah Penelitian)

Bab ini bertujuan untuk menjustifikasi pemilihan **Model Hibrida ARIMA–XGBoost** dengan menganalisis secara kritis kekuatan dan kelemahan model tunggal yang ditemukan dalam literatur ilmiah.

---

## 2.1 Analisis Status Quo: Kekuatan dan Kelemahan Model Tunggal
Penelitian terdahulu menunjukkan bahwa tidak ada satu model pun yang sepenuhnya ideal untuk menangani data deret waktu dengan karakteristik ganda — yaitu memiliki komponen **linier dan non-linier** secara bersamaan.

### 2.1.1 Model Linier Klasik: ARIMA
Model **ARIMA** (*AutoRegressive Integrated Moving Average*) adalah model statistik klasik yang menjadi dasar teori *time series forecasting* [4].

| Aspek | Penjelasan | Celah Penelitian (Gap) |
| :--- | :--- | :--- |
| **Kekuatan** | Fondasi teori yang kuat, mampu memodelkan *autocorrelation* dan pola musiman dasar (misalnya, pola permintaan mingguan). | |
| **Kelemahan** | Secara fundamental bersifat **linier** dan tidak dapat menangkap hubungan non-linier atau *outlier* kompleks yang timbul dari faktor eksternal. | **Gagal memprediksi anomali** yang disebabkan oleh tren media sosial atau *event* mendadak yang umum pada sektor F&B kekinian. |

---

### 2.1.2 Model Non-Linier Modern: XGBoost
Model **XGBoost** (*Extreme Gradient Boosting*) mewakili pendekatan *Machine Learning* yang unggul untuk regresi non-linier [5].

| Aspek | Penjelasan | Celah Penelitian (Gap) |
| :--- | :--- | :--- |
| **Kekuatan** | Robust terhadap data yang *volatile*, memiliki akurasi tinggi, dan dapat mengintegrasikan **variabel eksternal** (*proxy variables* seperti cuaca, event, atau sinyal tren). | |
| **Kelemahan** | Tidak secara eksplisit dirancang untuk memodelkan struktur deret waktu murni (*time dependence*). | **Berisiko kehilangan *long-term memory*** atau pola *autocorrelation* yang secara tradisional dimodelkan dengan baik oleh ARIMA. |

---

## 2.2 Identifikasi Celah Penelitian (The Research Gap)
Celah utama dalam penelitian ini terletak pada **residual** atau sisa pola yang tidak dapat dijelaskan oleh model linier.

**Argumen Kunci:**  
Data permintaan kategori menu dalam konteks F&B memiliki dua komponen terpisah:

1. **Komponen Linier** ($L_t$): Pola permintaan stabil, siklus musiman harian/mingguan.  
2. **Komponen Non-Linier** ($N_t$): Lonjakan permintaan mendadak akibat tren sosial atau faktor eksternal.

**Bukti Metodologis:**  
Zhang (2003) [8] membuktikan bahwa **residual dari model linier (ARIMA)** masih mengandung **struktur non-linier tersembunyi**.  
Model tunggal yang hanya fokus pada salah satu komponen — ARIMA pada $L_t$ dan XGBoost pada $N_t$ — akan selalu menghasilkan akurasi yang tidak optimal.

> **Celah yang Diisi:**  
> Penelitian ini menjembatani celah metodologis tersebut dengan mengimplementasikan **Model Hibrida ARIMA–XGBoost** yang memproses kedua komponen secara simultan, memastikan tidak ada sinyal informasi yang terbuang.

---

## 2.3 Justifikasi Pemilihan Model Hibrida
Pemilihan **Model Hibrida ARIMA–XGBoost** didasarkan pada landasan teoritis dan empiris berikut:

1. **Struktur Additive Decomposition**  
   Model hibrida mengadopsi pendekatan dekomposisi aditif:  
   \[
   \hat{Y}_t = \hat{L}_t + \hat{N}_t
   \]
   di mana:
   - $\hat{L}_t$ → diprediksi oleh ARIMA (komponen linier)  
   - $\hat{N}_t$ → dimodelkan oleh XGBoost (komponen non-linier/residual)

2. **Validasi Empiris di Sektor Ritel**  
   Penelitian terbaru [6] dalam konteks ritel menunjukkan bahwa pendekatan berbasis *boosting* diperlukan untuk meningkatkan akurasi prediksi dan efisiensi inventaris.

3. **Bukti Aplikasi di Domain Lain**  
   Pendekatan hibrida **ARIMA–XGBoost** telah terbukti menghasilkan performa superior pada data *volatile* seperti peramalan **energi** dan **traffic flow** [7], [9].

---

## 2.4 Kebaruan (Novelty) Penelitian
Meskipun model hibrida telah digunakan pada penelitian sebelumnya, penelitian ini menawarkan kebaruan pada aspek **terapan dan metodologis** sebagai berikut:

| Aspek | Kebaruan yang Diajukan |
| :--- | :--- |
| **Metode Hibrida Terstruktur** | Implementasi struktur *Additive Decomposition* yang eksplisit dan sistematis. |
| **Resolusi Data Tinggi** | Fokus pada **kuantitas permintaan per kategori menu**, bukan total penjualan — meningkatkan nilai praktis untuk *just-in-time production*. |
| **Integrasi Variabel Kontemporer** | Penggunaan **simulasi *proxy variables*** yang merepresentasikan pengaruh **tren sosial dan faktor cuaca** sebagai *input* non-linier utama untuk model XGBoost. |

---

## Ringkasan Bab II
| Bagian | Fokus | Output Utama |
|:---|:---|:---|
| **Analisis Status Quo** | Menilai kekuatan dan kelemahan model tunggal (ARIMA & XGBoost). | Mengidentifikasi keterbatasan model linier & non-linier. |
| **Identifikasi Celah Penelitian** | Menggambarkan gap metodologis antara $L_t$ dan $N_t$. | Menunjukkan perlunya pendekatan hybrid. |
| **Justifikasi Pemilihan Model** | Memperkuat alasan pemilihan ARIMA–XGBoost. | Validasi empiris dan teoritis pendekatan hybrid. |
| **Kebaruan Penelitian** | Menunjukkan nilai tambah penelitian ini. | Kebaruan metode, resolusi data, dan integrasi variabel kontekstual. |

---

> 📄 **Status:** Bab II – Gap Research Analysis  
> **Penulis:** *Syahrial Rizky*  
> **Program Studi:** Informatika – UPN “Veteran” Jawa Timur  
> **Mata Kuliah:** Riset Informatika  
> **Tahun Akademik:** 2025
