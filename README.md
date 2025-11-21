# 🛡️ DDoS Attack Classification (12-Class) with Hierarchical Model & Federated Learning

This project focuses on detecting and classifying **12 different classes of DDoS attacks** using a combination of advanced preprocessing techniques, hierarchical modeling, and federated learning.
The full pipeline includes **data preprocessing → balancing → hierarchical classification → advanced ML models → federated training → evaluation**.

---

## 🔧 **Key Features**

* ✔ Balanced dataset using **SMOTE**
* ✔ Full preprocessing pipeline
* ✔ **Hierarchical Classification Model**
* ✔ Specialized handling for **SYN Flood & Synonymous Flood** attacks
* ✔ **Federated Learning** implementation
* ✔ Achieved **98% accuracy**
* ✔ Robust performance across all 12 classes

---

## 🔍 **Data Preprocessing Pipeline**

### **1. Duplicate Removal**

Ensures the dataset contains only unique samples and eliminates redundancy.

### **2. Null Value Removal**

All rows with missing values were removed for clean training.

### **3. Label Encoding**

Converts categorical attack names into numeric classes.

### **4. StandardScaler**

Standardizes all numerical features to boost model stability.

### **5. SMOTE (Synthetic Minority Oversampling Technique)**

Balances all 12 attack classes, ensuring equal representation.

---

## 🧩 **Hierarchical Classification Model**

A **two-level hybrid model** was designed:

---

### 🔹 **Level 1 — Specialized Binary Classification for SYN-Related Attacks**

The following two classes show very similar traffic patterns and often get misclassified:

* **SYN Flood**
* **Synonymous Flood**

To accurately separate them, a **Random Forest classifier** is trained **only on these two classes**.

📌 **Why Random Forest?**

* Excellent for handling noisy cybersecurity datasets
* Works well for binary and multi-class problems
* Reduces overfitting through ensemble learning
* Automatically captures nonlinear relations
* Robust performance and easy to tune

---

### 🔹 **Level 2 — General Classification for All 12 Classes**

For full multiclass classification, an **XGBoost model** is used on the entire dataset after preprocessing.

📌 **Why XGBoost?**

* Exceptional performance on tabular network traffic data
* Handles class imbalance (especially after SMOTE)
* Resistant to overfitting
* Fast training and high accuracy
* Feature importance plots provide interpretability

---

## 🌐 **Federated Learning Implementation**

To support privacy-preserving cybersecurity analytics, this project includes a simulated **Federated Learning** setup.

### **Federated Setup**

* Multiple clients train on different data partitions
* Only model weights/gradients are shared
* No raw packet or flow data is exposed
* Aggregation is done via **Federated Averaging (FedAvg)**

📌 **Why Federated Learning?**

* Ideal for sensitive and distributed network datasets
* Protects user or organization data
* Allows collaboration across multiple nodes securely

---

## 📊 **Results**

### 🎯 **Final Accuracy: *98%***

* The hierarchical design significantly improves the accuracy of **SYN Flood** vs **Synonymous Flood** predictions.
* XGBoost delivers strong multiclass classification across all 12 attack types.
* Federated learning retains model quality while preserving privacy.

---

## 📈 **Performance Highlights**

* ✔ Superior SYN-related attack separation via Random Forest
* ✔ Balanced dataset using SMOTE leads to stable predictions
* ✔ High generalization from federated setup
* ✔ Lower false positives and false negatives across classes

---

## 📁 **Recommended Project Structure**

```
└── ddos-hierarchical-classification/
    ├── data/
    ├── preprocessing/
    ├── federated/
    ├── models/
    ├── notebooks/
    ├── README.md
    └── requirements.txt
```

---

## ⚙️ **Technologies Used**

* Python
* Pandas, NumPy
* Scikit-Learn
* Imbalanced-Learn (SMOTE)
* Random Forest (Binary Classification)
* XGBoost (Multiclass Classification)
* Federated Learning (FedAvg Simulation)
* Matplotlib, Seaborn


