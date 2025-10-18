# Research Problem Formulation  
**Bagian:** Bab I – Perumusan Masalah Penelitian  
**Fokus:** Evolusi pemikiran dari tantangan operasional di industri F&B menuju solusi berbasis *Hybrid Forecasting Model (ARIMA–XGBoost)*

---

## 1. Identify Broad Field (Identifikasi Bidang Luas)
Ide penelitian ini berakar dari dua tren besar yang membentuk arah penelitian modern di bidang **Data Science & Artificial Intelligence (AI)** dan **Operational Efficiency** dalam industri F&B.

### 1.1 Revolusi Data Science & AI
Transformasi besar dalam pengambilan keputusan bisnis kini tidak lagi berbasis intuisi, tetapi **berdasarkan data dan algoritma cerdas**.  
AI dan *machine learning* mampu mengubah keputusan operasional menjadi lebih terukur, adaptif, dan prediktif.

### 1.2 Efisiensi Operasi (Operational Efficiency)
Industri ritel dan F&B menghadapi tekanan tinggi untuk:
- Mengoptimalkan **biaya operasional**,
- Meningkatkan **kecepatan layanan**, dan  
- Memastikan **konsistensi produk** melalui *supply chain optimization*.

**Pemikiran Awal:**  
> “Bagaimana cara mengaplikasikan kecerdasan buatan untuk menyelesaikan masalah operasional di sekitar kita?”

---

## 2. Dissect the Subareas (Membedah Sub-Area)
Dari bidang luas tersebut, fokus penelitian mulai menyempit. Tantangan utama di industri F&B modern adalah **volatilitas permintaan** akibat:
- Tren media sosial (*FYP TikTok, Instagram Reels*),  
- Cuaca yang memengaruhi perilaku konsumen,  
- Event musiman dan tren viral produk tertentu.

### Sub-Area 1 — *Time Series Forecasting*
Alat utama untuk **memprediksi masa depan berdasarkan data transaksi historis.**

### Sub-Area 2 — *F&B Analytics*
Fokus pada data **granular per kategori menu**, sangat dinamis dan dipengaruhi faktor non-tradisional seperti tren sosial.

### Sub-Area 3 — *Hybrid Modeling*
Pengamatan bahwa data F&B **mengandung sinyal ganda** — pola reguler (musiman) dan anomali mendadak (viral).  
Artinya, **model tunggal tidak cukup** untuk menggambarkan dinamika kompleks tersebut.

**Transisi Pemikiran:**  
> “Masalah utama bukan sekadar *memprediksi masa depan*, tetapi *memprediksi dua jenis sinyal berbeda — reguler dan sporadis — dalam satu dataset*.”

---

## 3. Select Interested Sub-Area (Area yang Diminati)
Titik fokus penelitian berada pada perpotongan antara:
> **Advanced Time Series Forecasting** dan **Hybrid Modeling**

### Kebutuhan Aktual
Diperlukan model yang:
- Tidak hanya memprediksi total penjualan,  
- Tetapi juga **memberikan forecast pada level kategori menu** untuk mendukung:
  - *Just-in-Time Production*  
  - *Quality Assurance* dan pengendalian stok harian  

### Pemilihan Metode
Dipilih kombinasi dua pendekatan yang saling melengkapi:
- **ARIMA** → unggul untuk pola *linier* dan musiman  
- **XGBoost** → unggul untuk hubungan *non-linier* dan fitur eksternal (proxy tren)

### Arah Akhir
Mengembangkan **Model Hibrida Additive (ARIMA + XGBoost)**  
yang memisahkan sinyal permintaan:
- Bagian linier → diurus ARIMA  
- Residual (sinyal non-linier) → diurus XGBoost  

---

## 4. Raise Research Question (Pertanyaan Penelitian)
Setelah metode dan masalah ditetapkan, penelitian dirancang untuk bersifat **komparatif**, dengan tiga pertanyaan utama:

1. **ARIMA Baseline:** Seberapa akurat model ARIMA tunggal dalam meramalkan permintaan kategori menu?  
2. **XGBoost Baseline:** Seberapa akurat model XGBoost tunggal dengan *feature engineering* komprehensif?  
3. **Hipotesis Inti:** Apakah **Model Hibrida ARIMA–XGBoost** dapat menghasilkan akurasi (RMSE dan MAPE) yang lebih tinggi dibandingkan kedua model tunggal tersebut?

**Tujuan dari pertanyaan ini:**  
Menguji hipotesis bahwa pendekatan **Hybrid Additive** lebih efektif daripada model tunggal untuk menangani volatilitas permintaan F&B.

---

## 5. Formulate Objective (Merumuskan Tujuan Penelitian)
Tujuan penelitian disusun sebagai respons langsung terhadap rumusan masalah di atas:

| No | Tujuan Penelitian |
|----|--------------------|
| 1 | Menganalisis kinerja peramalan menggunakan **Model ARIMA Tunggal**. |
| 2 | Menganalisis kinerja peramalan menggunakan **Model XGBoost Tunggal**. |
| 3 | Membandingkan hasil dan menguji **efektivitas Model Hibrida (ARIMA–XGBoost)** terhadap model tunggal. |

---

## 6. Assess Objective (Penilaian Tujuan)
Evaluasi awal dilakukan untuk memastikan penelitian **layak (feasible)** dan **relevan (relevant)** terhadap konteks riset informatika.

| Aspek | Status | Keterangan |
|--------|---------|------------|
| **Feasible** | ✅ | Dataset transaksi tersedia di Kaggle; library seperti *Pandas*, *Statsmodels*, dan *XGBoost* dapat diakses di Google Colab. |
| **Relevant** | ✅ | Sejalan dengan tantangan operasional F&B dan standar *Advanced Time Series Forecasting*. |
| **Significant** | ✅ | Menyediakan bukti akademik dan pendekatan presisi untuk mendukung *Just-in-Time Production* dan peningkatan *Quality of Service*. |

---

## 7. Double Check (Pengecekan Ulang)
Langkah validasi dilakukan untuk memastikan keselarasan seluruh elemen proposal.

| Elemen | Status | Keterangan |
|---------|----------|------------|
| **Judul Akhir** | ✅ | *Analisis Komparatif Model ARIMA, XGBoost, dan Model Hibrida ARIMA–XGBoost untuk Peramalan Permintaan Kategori Menu pada Data Transaksi Kedai Kopi* |
| **Konsistensi** | ✅ | Judul, pertanyaan, dan tujuan semuanya terfokus pada perbandingan kinerja tiga model (linier, non-linier, dan hibrida). |
| **Arah Riset** | ✅ | Bertujuan mengatasi **volatilitas permintaan F&B** menggunakan kombinasi dua paradigma prediksi. |

---

## Ringkasan Bab I
| Tahap | Fokus | Output Utama |
|--------|--------|---------------|
| **Identify Broad Field** | Data Science, AI, Supply Chain | Area riset utama: peramalan permintaan |
| **Dissect Sub-Area** | F&B Analytics, Hybrid Forecasting | Masalah: volatilitas permintaan |
| **Select Sub-Area** | Advanced Hybrid Time Series | Solusi: Model ARIMA–XGBoost |
| **Raise Question** | Validasi metodologi | Hipotesis: model hibrida unggul |
| **Formulate Objective** | Menetapkan arah eksperimen | Tiga tujuan penelitian |
| **Assess Objective** | Menilai kelayakan riset | Feasible, relevan, signifikan |
| **Double Check** | Sinkronisasi keseluruhan | Proposal siap ke tahap Gap Analysis |

---

## Arah Lanjutan
Bab berikutnya (**Bab II – Gap Research Analysis**) akan:
- Mengidentifikasi **keterbatasan model tunggal (ARIMA & XGBoost)** dari literatur ilmiah,  
- Menunjukkan **mengapa model hibrida dibutuhkan**, dan  
- Menyusun **mind map konseptual** hubungan antar komponen metodologi.

---

>  **Dokumen ini merupakan bagian dari Tugas Riset Informatika**
> **Penulis:** *Syahrial Rizky*  
> **Program Studi:** Informatika – UPN “Veteran” Jawa Timur  
> **Mata Kuliah:** Riset Informatika  
> **Tahun Akademik:** 2025
