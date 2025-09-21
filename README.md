# 📊 Prediksi Penjualan & Sistem Rekomendasi Menu pada Kedai Kopitiam

---

##  Formulasi Problem Riset

1. **Identify Broad Field**  
   Komputasi Cerdas untuk sektor Food & Beverage (F&B) / Smart Retail.

2. **Dissect the Subareas**  
   - Time-series forecasting penjualan.  
   - Recommender system (CF, content-based, hybrid).  
   - Context-aware recommendation (jam, cuaca, promo).  
   - Integrasi stok dan prediksi penjualan.  
   - Explainability & metrik bisnis.

3. **Select Interested Sub-area**  
   Integrasi **peramalan penjualan item-level** dengan **sistem rekomendasi menu hybrid** yang sadar konteks dan stok.

4. **Raise Research Questions (RQ)**  
   - RQ1: Seberapa akurat model forecasting dalam memprediksi penjualan item harian/jam?  
   - RQ2: Apakah rekomendasi hybrid berbasis prediksi stok lebih efektif dibanding baseline populer/terbaru?  
   - RQ3: Bagaimana pengaruh variabel eksternal (cuaca, hari libur, promo) terhadap hasil prediksi & rekomendasi?  
   - RQ4: Bagaimana dampak explainability terhadap penerimaan pemilik kedai?

5. **Formulate Objectives**  
   - **Umum**: Merancang sistem terpadu forecasting + rekomendasi.  
   - **Khusus**:  
     - MAPE ≤ 20% pada prediksi penjualan per item.  
     - Peningkatan NDCG@5 ≥ 10% dibanding baseline.  
     - Penurunan stockout ≥ 20% atau waste ≥ 15% (simulasi).  
     - Menyediakan penjelasan rekomendasi dalam dashboard.

6. **Assess Objective**  
   - Data: transaksi, menu, stok (opsional), variabel eksternal (cuaca, libur, promo).  
   - Model: ARIMA/SARIMA, XGBoost/LSTM/GRU untuk forecasting; Item-CF + Content-based + Context-aware untuk rekomendasi.  
   - Evaluasi: MAE, RMSE, MAPE, Precision@K, NDCG@K, simulasi bisnis (stockout, waste, AOV).  
   - Etika: privasi pelanggan, anonimisasi data.

7. **Double Check**  
   - Kebaruan: forecast-aware + stock-aware + context-aware recsys untuk UMKM kedai lokal.  
   - Ketersediaan data ≥ 3–6 bulan transaksi.  
   - Baseline jelas (ARIMA, Popular).  
   - Target & metrik realistis.  
   - Risiko: data tipis, cold-start, minim variabel eksternal → sudah ada strategi mitigasi.

---

##  Metodologi

1. **Data Collection**: transaksi kedai kopi (menu, waktu, qty, harga).  
2. **Preprocessing**: agregasi, fitur waktu, cuaca, promo.  
3. **Forecasting Models**: ARIMA, XGBoost, LSTM.  
4. **Recommendation Models**: Popular, Item-CF, Content-based, Hybrid Context-aware.  
5. **Integration**: rekomendasi menu dipengaruhi stok & prediksi permintaan.  
6. **Evaluation**:  
   - Forecast → MAE, RMSE, MAPE.  
   - Recsys → Precision@K, Recall@K, NDCG@K.  
   - Bisnis → simulasi stockout, waste, AOV.  

---
## 👤 Author
Nama: **[Syahrial Rizky]**  
NPM: **[22081010020]**  
Prodi: Informatika, Universitas Pembangunan Nasional “Veteran” Jawa Timur  

---

