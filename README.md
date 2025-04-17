Binary Network Intrusion Detection using Machine Learning

This project focuses on detecting network intrusions using a supervised machine learning approach. The dataset CICIDS2017 contains traffic labeled as either "BENIGN" or various types of attacks. We convert this into a binary classification problem: **Normal vs Attack**.

---

 Dataset Overview

The dataset (merged from multiple CSVs) contains features extracted from network traffic. Each row represents a network connection, with attributes like:

- Protocol type
- Duration
- Source/Destination bytes
- Flags
- Packet size features
- Flow stats

And includes a label (`Label`) such as `"BENIGN"`, `"DDoS"`, `"PortScan"` etc.

---

 Preprocessing & Feature Engineering

1. Binary Classification Mapping**:
   - Created a new column `Binary_class`:
     - `"BENIGN"` → `"Normal"`
     - Any other label → `"Attack"`

2. Feature Cleanup**:
   - Dropped the original `Label` and `Binary_class` from the feature set `X`
   - Encoded categorical columns using `LabelEncoder`

3. Missing/Invalid Values**:
   - Replaced `inf` and `-inf` with `NaN`
   - Dropped rows with `NaN`

---

Model Training

We used a **Random Forest Classifier** trained on a 20% subset of the data for faster performance. The model was trained and tested using an internal 80-20 split from this subset.

Evaluation Metrics:

- Accuracy
- Precision, Recall, F1-score
- Confusion Matrix (visualized)
