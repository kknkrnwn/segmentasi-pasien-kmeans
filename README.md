# 🏥 Patient Segmentation Using K-Means Clustering

## 📖 Project Overview

This project applies the K-Means Clustering algorithm to segment hospital patients based on demographic and healthcare service characteristics. The clustering process aims to identify groups of patients with similar patterns in age, length of stay, and satisfaction level, enabling healthcare providers to better understand patient behavior and improve service quality.

The project includes data preprocessing, feature engineering, cluster optimization, model evaluation, cluster profiling, and visualization.

---

## 🎯 Objectives

- Perform patient segmentation using K-Means Clustering.
- Identify meaningful patient groups based on healthcare characteristics.
- Evaluate clustering performance using multiple validation metrics.
- Generate insights that can support healthcare management and decision-making.

---

## 🗂 Dataset Description

The dataset contains hospital patient information including demographic, hospitalization, and satisfaction attributes.

| Feature | Description |
|----------|-------------|
| patient_id | Unique patient identifier |
| age | Patient age |
| arrival_date | Hospital admission date |
| departure_date | Hospital discharge date |
| service | Type of healthcare service |
| satisfaction | Patient satisfaction score |
| Lama_Rawat_Inap | Length of stay (days) |
| Cluster | Assigned cluster label |

---

## ⚙️ Methodology

### 1. Data Collection

Patient records are collected and prepared for clustering analysis.

### 2. Feature Engineering

Length of Stay (LOS) is calculated from admission and discharge dates:

```python
df["Lama_Rawat_Inap"] = (
    df["departure_date"] - df["arrival_date"]
).dt.days
```

### 3. Data Preprocessing

The following preprocessing steps are performed:

- Missing value handling
- Data cleaning
- Outlier treatment using IQR capping
- Feature scaling using StandardScaler

### 4. Feature Selection

The clustering model uses:

```python
features = [
    "age",
    "Lama_Rawat_Inap",
    "satisfaction"
]
```

### 5. Cluster Optimization

Several evaluation techniques are used to determine the optimal number of clusters:

- Elbow Method
- Silhouette Score
- Davies-Bouldin Index

### 6. K-Means Clustering

The final model is trained using:

```python
KMeans(
    n_clusters=6,
    random_state=42,
    n_init=10
)
```

---

## 🔄 Project Workflow

```text
Raw Dataset
     │
     ▼
Data Understanding
     │
     ▼
Feature Engineering
(Length of Stay)
     │
     ▼
Data Cleaning
     │
     ▼
Outlier Treatment
(IQR Capping)
     │
     ▼
Feature Scaling
(StandardScaler)
     │
     ▼
Optimal K Determination
 ├─ Elbow Method
 ├─ Silhouette Score
 └─ Davies-Bouldin Index
     │
     ▼
K-Means Clustering
(K = 6)
     │
     ▼
Cluster Evaluation
     │
     ▼
Cluster Profiling
     │
     ▼
Business Insight Generation
```

---

# 📊 Exploratory Data Analysis

## Correlation Analysis

Understanding relationships among variables used in clustering.

<img width="650" alt="korelasi" src="https://github.com/user-attachments/assets/d6c34507-4cb5-4a5f-803c-bd7b9710d3cc" />

---

## Feature Distributions

Distribution analysis for:

- Age
- Length of Stay
- Satisfaction Score

<img width="650" alt="distribusi" src="https://github.com/user-attachments/assets/60822777-798b-4e17-bfea-fa8d3d817bc9" />

These visualizations help identify skewness, spread, and potential anomalies in the dataset.

---

# 📈 Cluster Optimization

## Elbow Method

The Elbow Method evaluates the Within-Cluster Sum of Squares (WCSS) across different K values.
The optimal K is identified at the point where adding additional clusters produces diminishing returns.

---
## Silhouette Score

The Silhouette Score measures cluster cohesion and separation.

<img width="1584" height="394" alt="perbandingan cluster" src="https://github.com/user-attachments/assets/f66eb897-a92e-419e-8c47-ecd049dab306" />


Interpretation:

| Score Range | Interpretation |
|-------------|---------------|
| > 0.50 | Strong clustering |
| 0.25 - 0.50 | Moderate clustering |
| < 0.25 | Weak clustering |

---

## Davies-Bouldin Index

The Davies-Bouldin Index evaluates cluster compactness and separation.

Interpretation:

| Score | Interpretation |
|--------|--------------|
| < 1.0 | Good clustering |
| > 1.0 | Poor clustering |

---

# 🤖 Clustering Results

## Final Model

```python
kmeans = KMeans(
    n_clusters=6,
    random_state=42,
    n_init=10
)
```

Selected Number of Clusters:

```text
K = 6
```

---

## Cluster Distribution

The proportion of patients within each cluster.

<img width="1484" height="492" alt="distribusi karakteristik" src="https://github.com/user-attachments/assets/31144f22-647b-4c38-b46d-6a475bddfe54" />


This visualization helps identify dominant patient groups.

---

## Cluster Profiles

Average characteristics for each cluster.

| Cluster | Average Age | Average LOS | Average Satisfaction |
|----------|------------|-------------|---------------------|
| 0 | ... | ... | ... |
| 1 | ... | ... | ... |
| 2 | ... | ... | ... |
| 3 | ... | ... | ... |
| 4 | ... | ... | ... |
| 5 | ... | ... | ... |

---

## Cluster Comparison

Boxplots are used to compare variable distributions across clusters.

![Cluster Boxplots](images/cluster_boxplots.png)

These plots reveal:

- Variability
- Cluster differences
- Outliers
- Behavioral patterns

---

## 3D Cluster Visualization

Clusters are visualized in three-dimensional feature space.

- X-axis → Age
- Y-axis → Length of Stay
- Z-axis → Satisfaction

<img width="650" alt="3D" src="https://github.com/user-attachments/assets/afd7aac1-1f7f-487b-b648-a863f9e6554d" />


This plot provides a visual assessment of cluster separation.

---

# 🏥 Healthcare Insights

The clustering process identifies distinct patient segments that may require different healthcare strategies.

Examples include:

### Cluster Type A
**Older Patients – Short Stay – Low Satisfaction**

Characteristics:

- Elderly patients
- Short hospitalization duration
- Lower satisfaction scores

Potential actions:

- Improve elderly-friendly services
- Enhance communication quality
- Increase post-treatment support

---

### Cluster Type B
**Younger Patients – High Satisfaction**

Characteristics:

- Younger age group
- Positive service experience
- Moderate length of stay

Potential actions:

- Maintain service quality
- Promote patient engagement programs

---

# 🔥 Service Distribution Analysis

Healthcare service categories are analyzed after clustering.

<img width="650" alt="heatmap" src="https://github.com/user-attachments/assets/fb115bb2-cc01-40db-a44f-b3c912d6479b" />

Purpose:

- Identify dominant services within each cluster.
- Support hospital resource planning.
- Improve operational efficiency.

---

# 📦 Output

The final dataset is exported as:

```text
hasil_clustering_pasien.csv
```

Contents:

- Original patient data
- Engineered features
- Cluster labels
- Cluster assignments

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Google Colab

---

# 📌 Key Findings

- K-Means successfully segments patients into six meaningful groups.
- Age, Length of Stay, and Satisfaction contribute significantly to cluster formation.
- Multiple validation metrics improve clustering reliability.
- Cluster profiling provides actionable healthcare insights.
- Service distribution analysis helps support hospital operational decisions.

---

# 🚀 Future Improvements

- Compare K-Means with Hierarchical Clustering.
- Compare K-Means with DBSCAN.
- Include diagnosis and treatment-related features.
- Build an interactive dashboard using Power BI or Streamlit.
- Deploy as a healthcare decision-support system.

---

## 👨‍💻 Author

Patient Segmentation and Healthcare Analytics Project using K-Means Clustering.

Developed for educational, research, and healthcare data analysis purposes.
