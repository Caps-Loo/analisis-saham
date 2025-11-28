# 📈 IDX Stock Forecaster: Multivariate LSTM

## 📋 Deskripsi Project

**IDX Stock Forecaster** adalah sistem prediksi harga saham berbasis Deep Learning yang dirancang khusus untuk memodelkan dinamika pasar saham Indonesia (IDX/BEI).  
Proyek ini memanfaatkan pendekatan **Multivariate Time Series**, sehingga model mampu memahami lebih banyak konteks dibanding pendekatan univariate tradisional.

Tidak hanya mengamati pergerakan harga historis, model juga menggabungkan indikator teknikal penting yang dapat menghasilkan prediksi yang lebih stabil dan akurat:

- **RSI (Relative Strength Index):** Mengukur momentum beli/jual.
- **MACD (Moving Average Convergence Divergence):** Menangkap kekuatan dan arah tren.
- **Signal Line MACD:** Memberikan gambaran momentum jangka pendek.

Dengan kombinasi fitur ini, model memperoleh perspektif yang lebih kaya terhadap kondisi pasar dan mampu menghasilkan prediksi yang lebih realistis.

---

## ✨ Fitur Utama

### 🚀 Arsitektur LSTM Bertingkat

- Menggunakan Stacked LSTM Layers untuk menangkap pola jangka panjang yang sulit ditangani model biasa.
- Ditambah Dropout Regularization untuk mengurangi risiko overfitting.

### 🧠 Feature Engineering Kaya Informasi

Data input mencakup 4 fitur utama:
- Harga penutupan (Close)
- RSI
- MACD
- MACD Signal

Pendekatan ini membuat model lebih sensitif terhadap perubahan struktur tren pasar.

### ⏱ Optimasi Training Otomatis

Menerapkan:
- **Early Stopping:** Menghentikan pelatihan ketika performa optimal tercapai.
- **Model Checkpointing:** Menyimpan model terbaik otomatis.
- **Batch Training Multisaham:** Melatih banyak saham dalam satu kali eksekusi.

Hasilnya: proses efisien dan stabil dengan nilai RMSE yang rendah.

### 🏭 End-to-End Pipeline Otomatis

Pipeline mencakup:
- Pengambilan data historis otomatis (via Yahoo Finance)
- Preprocessing & Scaler Management
- Pelatihan LSTM untuk tiap saham
- Penyimpanan artefak model (.keras) & scaler (.pkl)
- Prediksi harian otomatis
- Penanganan hari libur dan akhir pekan

Cukup jalankan satu skrip — seluruh model akan diperbarui otomatis.

### 📅 Smart Inference (Prediksi Hari Kerja)

Sistem prediksi otomatis mendeteksi apakah prediksi berikutnya jatuh pada:
- Sabtu
- Minggu
- Hari non-trading

Jika ya, target prediksi digeser ke hari kerja terdekat — biasanya Senin.  
Sehingga prediksi tidak kosong atau "bocor".

---

## 🛠 Teknologi yang Digunakan

- **Python 3.8+** – Bahasa utama project
- **TensorFlow / Keras** – Model LSTM multivariate
- **YFinance** – Mengambil data pasar real-time
- **NumPy & Pandas** – Manipulasi data dan perhitungan indikator teknikal
- **Scikit-Learn** – Normalisasi (MinMaxScaler) dan alat preprocessing
- **Matplotlib** – Visualisasi prediksi vs harga asli
- **Pickle / Joblib** – Penyimpanan Scaler

---

## 📂 Struktur Project

Struktur ini dirancang untuk memisahkan model, eksperimen, pipeline utama, dan dokumentasi secara bersih.

```
├── models/                      # Penyimpanan artefak model & scaler
│   ├── model_BBRI.keras         # Model LSTM saham BBRI
│   ├── scaler_X_BBRI.pkl        # Scaler input untuk BBRI
│   └── ...                      # Model dan scaler untuk saham lain
│
├── notebooks/                   # Notebook eksperimen
│   └── Analisis_Saham_Final.ipynb
│       # EDA, feature engineering, dan eksperimen training
│
├── src/                         # Central pipeline & kode produksi
│   └── analisis_saham.py        # Script training & prediksi otomatis multisaham
│
├── requirements.txt             # Daftar dependensi Python
│
└── README.md                    # Dokumentasi lengkap project
```
