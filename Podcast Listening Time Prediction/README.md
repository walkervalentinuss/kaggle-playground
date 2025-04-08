# 🎧 Kaggle Playground S5E4 - Podcast Listening Time Prediction

This project is part of the Kaggle Playground Series - Season 5, Episode 4.  
The goal is to predict **podcast listening time (in minutes)** based on episode metadata, genre, sentiment, and other features.
The evaluation metric is **Root Mean Squared Error (RMSE)**.

## 📦 Dataset

The dataset can be downloaded from the official competition page:

```bash
kaggle competitions download -c playground-series-s5e4
```

---

## 📊 Exploratory Data Analysis (EDA)

Several visualizations were used to understand patterns in listening behavior:
- Distribution of listening time by genre
- Boxplots by sentiment and genre
- ANOVA test to assess statistical significance of sentiment on listening time
- Analysis of listening time by day of the week

**Key Insights:**
- Listening time varies significantly across genres and sentiment (p-value < 0.05).
- Weekdays tend to have longer listening time than weekends.

---

## 🧠 Modeling

Two baseline models were used for regression:

### ✅ LightGBM
- Model: `LGBMRegressor`
- RMSE: **13.75**

### ✅ Random Forest
- Model: `RandomForestRegressor`
- RMSE: **13.36** (best so far)

---

## 📁 Folder Structure

```
├── dataset/            # Dataset files
├── code.ipynb          # Jupyter notebooks for EDA and modeling
├── submissions/        # Submission CSVs
├── README.md           # Project overview
```

---

## 🏁 Submission

The predictions are submitted as `.csv` with format:
```
id, listening_time
```

---

## ✨ Author

Created by walker
For Kaggle Playground Series S5E4  
