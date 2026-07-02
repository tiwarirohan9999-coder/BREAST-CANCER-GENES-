#  Heart Attack Risk Prediction

A machine learning project that predicts whether a patient is at risk of a heart attack using clinical parameters like age, cholesterol, blood pressure, chest pain type, and more.

Built as a first-year portfolio project to practice the end-to-end ML workflow: data cleaning, class balancing, model training, and evaluation.

---

## 📊 Dataset

- **File:** `cleaned_merged_heart_dataset.csv` / `.xlsx`
- **Records:** 1,888 patients
- **Source:** Merged from 5 publicly available heart disease datasets (Kaggle)
- **Target column:** `target` → `1` = heart disease risk, `0` = no heart disease risk

### Features
| Column | Description |
|---|---|
| age | Patient age |
| sex | 1 = male, 0 = female |
| cp | Chest pain type (0–3) |
| trestbps | Resting blood pressure |
| chol | Serum cholesterol (mg/dl) |
| fbs | Fasting blood sugar > 120 mg/dl (1 = true) |
| restecg | Resting ECG results |
| thalachh | Maximum heart rate achieved |
| exang | Exercise-induced angina (1 = yes) |
| oldpeak | ST depression induced by exercise |
| slope | Slope of peak exercise ST segment |
| ca | Number of major vessels colored by fluoroscopy |
| thal | Thalassemia (0–3) |
| target | 1 = heart disease risk, 0 = no risk |

---

## ⚙️ Workflow

1. **Load & prepare data** — read CSV/Excel, split features/target
2. **Train/test split** — 80/20 (or 70/30), stratified on target
3. **Scale features** — `StandardScaler`
4. **Balance classes** — `SMOTE` on training data only
5. **Train 3 models:**
   - Logistic Regression
   - K-Nearest Neighbors (KNN)
   - Naive Bayes
6. **Evaluate** — Accuracy, Recall, Precision, F1-score, Confusion Matrix
7. **Visualize** — target distribution pie chart, accuracy comparison, recall comparison, confusion matrix

---

## 📈 Results

| Model | Accuracy | Recall |
|---|---|---|
| Logistic Regression | ~75% | ~80% |
| KNN (K=5) | ~92% | ~92% |
| Naive Bayes | ~71% | ~81% |

> **Note:** Recall is especially important here — missing a real heart disease case (false negative) is more costly than a false alarm. KNN performed best on both accuracy and recall in this dataset.

### Visualizations
- `target_distribution_pie.png` — class balance in the dataset
- `model_comparison.png` — accuracy across all 3 models
- `model_comparison_recall.png` — recall across all 3 models
- `confusion_matrix.png` — confusion matrix for the best model

---

## 🗂️ Project Structure

```
heart-attack-prediction/
├── data/
│   ├── cleaned_merged_heart_dataset.csv
│   └── raw_merged_heart_dataset.csv
├── heart_model_training.py
├── requirements.txt
├── README.md
└── .gitignore
```

---

## 🚀 Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/<your-username>/heart-attack-prediction.git
cd heart-attack-prediction
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the script
```bash
python heart_model_training.py
```

Make sure `cleaned_merged_heart_dataset.csv` is in the same folder as the script.

---

## 🛠️ Tech Stack

- Python
- pandas
- scikit-learn
- imbalanced-learn (SMOTE)
- matplotlib

---

## 🔮 Future Improvements

- Add more models (Random Forest, SVM, XGBoost)
- Hyperparameter tuning (GridSearchCV)
- Deploy as a web app (Streamlit / Flask)
- Add feature importance analysis
- Cross-validation instead of single train/test split

---

## 🙋 Author

**Rohan Tiwari**
Researcher, TIET-UQ, CoE-DSAI
