# 📈 IDX Stock Forecaster: Multivariate LSTM

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0%2B-orange)
![Status](https://img.shields.io/badge/Status-Active-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

## 📋 Deskripsi Project

**IDX Stock Forecaster** adalah sistem prediksi harga saham berbasis *Deep Learning* yang dirancang khusus untuk menangani volatilitas pasar saham Indonesia (IDX/BEI).

Berbeda dengan model prediksi konvensional yang hanya melihat riwayat harga (*Univariate*), sistem ini menggunakan pendekatan **Multivariate Time Series**. Model ini tidak hanya "melihat" harga masa lalu, tetapi juga "merasakan" momentum dan tren pasar dengan mengintegrasikan indikator teknikal:
* **RSI (Relative Strength Index):** Mendeteksi kondisi jenuh beli (*overbought*) atau jenuh jual (*oversold*).
* **MACD (Moving Average Convergence Divergence):** Mendeteksi arah dan kekuatan tren.

## ✨ Fitur Utama

🚀 **Arsitektur Deep Learning Canggih**
Menggunakan **Stacked LSTM** (Long Short-Term Memory) dengan mekanisme **Dropout** untuk mencegah *overfitting* dan mampu menangkap pola jangka panjang yang kompleks pada data saham.

🧠 **Smart Feature Engineering**
Menggabungkan data harga historis (`Close`) dengan analisis sentimen teknikal (`RSI`, `MACD`, `Signal Line`) sebagai fitur input (4 Dimensi), membuat prediksi lebih responsif terhadap perubahan pasar.

⏱️ **Optimasi Training Otomatis**
Menerapkan **Early Stopping** untuk memantau proses pelatihan. Sistem akan berhenti secara otomatis di titik optimal (saat *loss* terendah), menghasilkan efisiensi waktu dan akurasi tinggi (RMSE rendah).

🏭 **Automated End-to-End Pipeline**
Sistem "Pabrik Model" yang mampu memproses, melatih, dan menyimpan model serta *scaler* untuk berbagai saham (contoh: BBRI, TLKM, ASII, ANTM, ICBP) secara otomatis dalam satu kali eksekusi.

📅 **Smart Inference**
Skrip prediksi universal yang cerdas dalam menangani kalender. Jika prediksi jatuh pada hari libur bursa (Sabtu/Minggu), sistem otomatis menggeser target prediksi ke hari kerja berikutnya (Senin).

## 🛠️ Teknologi yang Digunakan

* **Python**: Bahasa pemrograman utama.
* **TensorFlow / Keras**: Membangun dan melatih model LSTM.
* **YFinance**: Mengambil data saham *real-time* dari Yahoo Finance.
* **Pandas & NumPy**: Manipulasi data dan perhitungan indikator teknikal.
* **Scikit-Learn**: Normalisasi data (`MinMaxScaler`).
* **Matplotlib**: Visualisasi grafik perbandingan harga asli vs prediksi.

## 📂 Struktur Project

```bash
├── models/                 # Folder penyimpanan Model (.keras) & Scaler (.pkl)
│   ├── model_BBRI.keras
│   ├── scaler_X_BBRI.pkl
│   └── ...
├── notebooks/              # Jupyter Notebook untuk eksperimen / training
│   └── Analisis_Saham_Final.ipynb
├── src/                    # Source code utama
│   └── analisis_saham.py  # Script untuk melatih semua saham dan prediksi harian
│   
├── requirements.txt        # Daftar library yang dibutuhkan
└── README.md               # Dokumentasi project
