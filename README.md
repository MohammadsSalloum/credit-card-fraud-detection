# credit-card-fraud-detection
This project applies **Anomaly Detection** techniques to detect fraudulent credit card transactions using the [Kaggle dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud).

---

## 📌 Project Motivation
Credit card fraud is a serious issue where fraudulent transactions are rare compared to normal ones.  
This dataset is highly **imbalanced** (only ~0.17% fraud cases), so I applied anomaly detection methods that are well-suited for such problems.

---

## 🔬 Steps I Followed

### 1. Data Understanding
- Used the **Kaggle credit card dataset** with 284,807 transactions.  
- Only 492 were frauds → dataset is highly imbalanced.  
- Features were already transformed (PCA components).

### 2. Preprocessing
- Scaled features using **StandardScaler**.  
- Split dataset into **training (normal only)** and **testing (normal + fraud)**.  

### 3. Models Used
#### 🔹 Isolation Forest
- Detects outliers by randomly partitioning the data.  
- Parameters I used:  
  - `n_estimators=100`: number of trees  
  - `contamination=0.0017`: fraction of anomalies expected (matches fraud rate)

#### 🔹 One-Class SVM
- Learns the boundary of normal data and detects points outside it.  
- Parameters I used:  
  - `kernel="rbf"`: radial basis function kernel  
  - `nu=0.0017`: expected proportion of outliers  
  - `gamma=0.01`: defines how far the influence of one data point reaches  

### 4. Evaluation
- Used **Confusion Matrix**, **Precision**, **Recall**, **F1-score**.  
- Because the dataset is imbalanced, **recall (ability to catch frauds)** was especially important.  

---

## 📊 Results

| Model            | Precision (Fraud) | Recall (Fraud) | F1-score |
|------------------|-------------------|----------------|----------|
| Isolation Forest | 0.26              | 0.25           | 0.26     |
| One-Class SVM    | 0.08              | 0.68           | 0.14     |

- **Isolation Forest** had better precision (fewer false alarms).  
- **One-Class SVM** caught more fraud cases (higher recall) but with low precision.  

---

## 🎯 Conclusion
- Fraud detection is extremely challenging due to class imbalance.  
- Anomaly detection methods can identify fraud, but there is a tradeoff between **precision** (false alarms) and **recall** (catching real frauds).  
- In real life, we would balance them depending on the business need (better to miss fewer frauds or reduce false alarms?).  

---

👨‍💻 Author: Mohammad Salloum  
