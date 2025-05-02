# 🏋️‍♀️ Calories Burnt Prediction – XGBoost Regression

## 📌 Problem Definition

Tujuan dari proyek ini adalah memprediksi **jumlah kalori yang dibakar seseorang setelah melakukan olahraga**, berdasarkan fitur-fitur seperti:
- Gender (`Sex`)
- Usia (`Age`)
- Tinggi badan (`Height`)
- Berat badan (`Weight`)
- Durasi olahraga (`Duration`)
- Detak jantung (`Heart_Rate`)
- Suhu tubuh (`Body_Temp`)

Jenis tugas machine learning: **Regresi (Supervised Learning)**  
Metode evaluasi: **Root Mean Squared Logarithmic Error (RMSLE)**

---

## 📊 Dataset

Dataset yang digunakan berasal dari:  
📁 `Calories Burnt Prediction - ruchikakumbhar`  
File:
- `train.csv`: data pelatihan
- `test.csv`: data pengujian
- `sample_submission.csv`: format pengumpulan hasil prediksi

---

## 🧪 Evaluation Metric

Metode evaluasi yang digunakan adalah **RMSLE**, karena:
- Cocok untuk target numerik positif seperti kalori
- Lebih toleran terhadap prediksi yang underestimasi
- Formula:

```
RMSLE = sqrt( (1/n) * Σ (log(1 + y_pred) - log(1 + y_true))^2 )
```

---

## 🔍 Exploratory Data Analysis

### ✅ Observasi Awal
- Total data: **7.5 juta baris**, tanpa missing values atau duplikat.
- Kolom: 7 numerik + 1 kategorikal (`sex`)
- Kolom `id` dibuang karena tidak relevan.

### ✅ Feature Engineering
- Kolom `sex` di-*map*: `'male' = 0`, `'female' = 1`
- `Height` dikonversi dari **cm ke meter**
- Menambahkan kolom **BMI**, namun dibuang setelah terbukti tidak berkorelasi tinggi terhadap target

### ✅ Korelasi Penting:
- `Duration` vs `Calories`: **0.95**
- `Heart_Rate` vs `Calories`: **0.90**
- `Body_Temp` vs `Calories`: **0.83**

---

## 📈 Visualisasi

- Histogram semua kolom numerik
- Heatmap matriks korelasi

---

## 🧹 Data Preparation

- Fitur: `Sex`, `Age`, `Height`, `Weight`, `Duration`, `Heart_Rate`, `Body_Temp`
- Target: `Calories`
- Split: `80% training`, `20% validation`

---

## 🤖 Modeling: XGBoost Regressor

Parameter:
```python
XGBRegressor(
    subsample=1.0,
    reg_lambda=5,
    reg_alpha=0.01,
    n_estimators=1000,
    max_depth=9,
    learning_rate=0.03,
    gamma=0,
    colsample_bytree=0.9,
    random_state=42
)
```

### ✅ Hasil Validasi:
- RMSLE (validation): **ditampilkan di console setelah training**

---

## 📤 Submission

Setelah model dilatih, prediksi dilakukan pada data `test.csv` dan hasilnya disimpan ke:

📄 `submission_xgb_regression.csv`

Format:
```csv
id,Calories
123456,123.45
...
```

---

## 🧠 Catatan Penting

- **Scaling eksplisit tidak dilakukan** karena XGBoost tidak sensitif terhadap skala.
- Kolom `BMI` dibuang karena kontribusinya rendah berdasarkan korelasi.

---

## 📚 Dependencies

- `pandas`
- `numpy`
- `matplotlib`, `seaborn`
- `xgboost`
- `scikit-learn`
