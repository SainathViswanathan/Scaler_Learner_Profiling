# Scaler — Learner Profiling (Clustering Case Study)

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python)
![Machine Learning](https://img.shields.io/badge/Type-Unsupervised%20Learning-green)
![Clustering](https://img.shields.io/badge/Focus-Clustering%20%7C%20EDA-yellow)
![Libraries](https://img.shields.io/badge/Libraries-pandas%2C%20scikit--learn%2C%20seaborn-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)


## 🚀 About Scaler
Scaler is a cutting-edge online tech university (tech-versity) designed to upskill software and data science professionals.  
It offers rigorous, live-learning programs delivered by seasoned industry experts, focusing on modern curricula aligned with current technological trends.  
Scaler empowers learners to bridge skill gaps, advance their careers, and gain real-world exposure through personalized mentorship and structured, data-driven education.

---

## 🧩 Issue at Hand
Scaler caters to a diverse learner base across varying job roles, industries, and experience levels.  
This diversity creates challenges in profiling learners effectively to deliver truly **personalized learning experiences**.  
Without a structured, data-backed approach, Scaler risks offering generalized content that may not address individual learner needs or motivations.

---

## 🎯 Project Objective
Leverage **unsupervised learning and clustering techniques** to categorize Scaler’s learners into meaningful profiles based on:
- Job roles and positions  
- Company and industry affiliation  
- Years of experience  
- Compensation (CTC) and salary progression  

These profiles are then analyzed to uncover actionable insights that can help Scaler:
- Tailor its curriculum and mentorship programs  
- Design better learner journeys  
- Improve satisfaction and retention  
- Strengthen its position as a leader in learner-centric, personalized education

---

## 🔑 Key Goals
- Develop a **data-driven, personalized approach** to enhance learner experience and outcomes.  
- Enable Scaler to refine **course offerings**, **mentorship models**, and **marketing strategies** through understanding distinct learner segments.  
- Support Scaler in becoming a **benchmark for learner-centric education** by addressing unique skill gaps and aligning learning paths with real-world demand.

---

## 📚 Dataset
The dataset `scaler_clustering.csv` consists of anonymized learner data, including:

| Feature | Description |
|----------|-------------|
| `company_hash` | Anonymized employer identifier |
| `email_hash` | Unique anonymized learner ID |
| `orgyear` | Year the learner joined current company |
| `ctc` | Current compensation (CTC) |
| `job_position` | Job title or role |
| `ctc_updated_year` | Year of last salary update |

**Rows:** ~205,800  
**Columns:** 7  

---

## 🧠 Methodology Overview

### 1. **Exploratory Data Analysis (EDA)**
- Analyzed data shape, types, distributions, and missing values.  
- Identified over 52,000 missing `job_position` entries, duplicate rows, and anomalies in `ctc` and `orgyear`.  
- Detected outliers (e.g., unrealistic years or salary values) and assessed data quality before modeling.

### 2. **Data Cleaning & Preprocessing**
- Removed 34 duplicate records and standardized `job_position` text fields.  
- Corrected invalid `orgyear` values using logical replacements based on `ctc_updated_year`.  
- Adjusted abnormally small `ctc` values (e.g., 2 → 200,000) identified as data-entry errors.  
- Imputed missing job roles using the most frequent `job_position` within the same `company_hash`.

### 3. **Feature Engineering**
- Derived new variables:
  - `yoe` (Years of Experience)
  - `num_jobs` and `growth` (% salary growth)
  - `ctc_yoe_ratio`
  - Binary flags (`is_developer`, `is_management`, `is_sales`, `is_tech`, `is_non_coder`)
  - `ctc_bin` — salary tier labels (`low`, `medium`, `high`)

### 4. **Encoding & Scaling**
- Applied frequency encoding for categorical job roles.  
- Scaled numeric features with `StandardScaler` to normalize input for clustering.

### 5. **Cluster Analysis**
- **Hopkins Statistic:** 0.9999 (high cluster tendency — verified via resampling).  
- **Dimensionality Reduction:** PCA retained 95% variance in 10 components.  
- **K-Means:** Elbow & silhouette suggested *k = 6* clusters.  
- **Hierarchical Clustering:** Run on 20% random sample (Ward linkage), optimal *k = 8*.

---

## 🧭 Learner Profiles (K-Means: k = 6)

| Cluster | Profile | Insights & Actions |
|----------|----------|--------------------|
| **1. Underpaid Switchers** | Developers with high experience and frequent job changes but low pay. | Offer targeted upskilling to bridge skill gaps. |
| **2. Ambitious Movers** | Developers showing consistent growth and frequent transitions. | Provide guidance for long-term career planning. |
| **3. Stagnant Movers** | Frequent job switchers without salary progression. | Focus mentorship on market readiness and skill diversification. |
| **4. Professionally Stuck** | Non-coders or other roles with low mobility and no recent hikes. | Design re-skilling programs to revive career momentum. |
| **5. Elite Achievers** | High-performing individuals with high CTC, growth, and stability. | Leverage as success stories and mentors. |
| **6. Underpaid Veterans** | Experienced managers/sales professionals with low compensation. | Create hybrid technical-management transition tracks. |

---

## 📈 Key Recommendations
1. **Targeted Upskilling:** Create specialized programs for stagnant and stuck clusters.  
2. **High-Value Courses:** Introduce niche offerings like “AI + Business” for transitioning professionals.  
3. **Smart Marketing:** Use cluster insights for targeted acquisition campaigns.  
4. **Corporate Partnerships:** Align with companies hosting “Elite Achievers” for placement; offer upskilling where underpaid clusters dominate.  
5. **Data Quality:** Standardize data collection (especially job titles) to improve future analytics accuracy.

---

## 🧰 Tools & Libraries
| Category | Tools |
|-----------|--------|
| **Data Manipulation** | pandas, numpy |
| **Visualization** | matplotlib, seaborn |
| **Machine Learning** | scikit-learn (KMeans, AgglomerativeClustering, StandardScaler, PCA) |
| **Clustering Utilities** | fastcluster, scipy |
| **Evaluation Metrics** | silhouette score, elbow method, Hopkins test |

---

## 🧪 How to Run
1. Clone the repository.  
2. Place `scaler_clustering.csv` inside the `/data` folder.  
3. Open and execute the notebook `Scaler_Clustering_Case_Study.ipynb` step-by-step.  
4. Review cluster outputs and profile visualizations.

---

## 📌 Project Impact
This project enables Scaler to:
- Understand learner patterns at scale.  
- Deliver **personalized mentorship and learning paths**.  
- Strengthen **curriculum design and career services**.  
- Build data-backed strategies for learner engagement and retention.

---

## 🧭 Authors & Acknowledgments
Developed by **Sainath Viswanathan** as part of Scaler’s Data Science & ML learning journey.  
Guided by Scaler’s project framework and case study design.
