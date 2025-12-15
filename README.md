# Predicting Restaurant Ratings Using Yelp Business Metadata and Engagement  
**Course:** BDA 602 – Fall 2025  
**Institution:** San Diego State University – College of Arts and Letters, Big Data Analytics  
**Project Link:** [Link](https://aichutan.github.io/BDA602_final_yelp_analysis/)
---

## 🧠 Team Members  
- **Pilar de Haro** – Group Leader  
  *Dataset cleaning, model training/validation, results analysis, and report compilation*  
  📧 pdeharo0898@sdsu.edu  
- **Aichu Tan** – Modeling & Machine Learning  
  *Feature engineering, MLflow experiment tracking, and model optimization*  
  📧 dtan3697@sdsu.edu  
- **Swikriti Joshi** – Data Preparation & Visualization  
  *Data cleaning, formatting, and visual dashboard creation*  
  📧 sjoshi2639@sdsu.edu  
- **Eduardo Rosas** – Data Analysis & Visualization  
  *Model development, data preparation, and visualization design*  
  📧 erosas9172@sdsu.edu  

📂 **GitHub Repository:** [AichuTan/BDA602_final_yelp_analysis](https://github.com/AichuTan/BDA602_final_yelp_analysis)  
🎥 **Video Presentation:** [YouTube Link](https://www.youtube.com/watch?feature=shared&v=70_A0i9r2HI)  

---

## 📋 Abstract  
Online reviews heavily influence consumer choices, and Yelp ratings directly affect restaurant visibility and success.  
This project investigates whether **structured metadata**—price range, amenities, hours, and location—can predict restaurant ratings *without* text reviews.  

Using the **2024 Yelp Open Dataset**, we analyzed **36,261 restaurants** with **61 engineered features**, framing prediction as a **binary classification problem** (≥4★ vs. <4★).  
Models: Logistic Regression, Elastic Net, Random Forest, and XGBoost (Scikit-learn pipeline, 5-fold CV, MLflow tracking).  

**Key Results:**
- **XGBoost:** Highest Accuracy (0.733) and ROC-AUC (0.79)  
- **Random Forest:** Best F1-score (0.659)  
- **Top Predictors:** Review count, price range, operating hours, and accessibility/amenities (wheelchair access, table service)  
- **Clustering (K-Prototypes, k=3):** Identified family-casual, mid-range social, and quick-service archetypes  

**Conclusion:** Structured business metadata effectively predicts Yelp ratings and offers actionable insights for small restaurants to enhance service quality, accessibility, and customer satisfaction.  

---

## 📊 Data Sources  
**Dataset:** [Yelp Open Dataset 2024](https://www.yelp.com/dataset)  

- **Files Used:**  
  - `business.json` – metadata (categories, ratings, price range, amenities)  
  - `review.json` – subset of reviews (2019–2022)  

- **Final Sample:**  
  36,261 restaurants, 61 engineered features  

### 🧹 Data Cleaning & Feature Engineering  
- Log-transformed review counts (`log1p`)  
- Extracted weekly/average hours, weekend hours, and open days  
- Expanded nested attributes → 22 engineered features  
- Encoded categorical fields: Wi-Fi, Alcohol, Attire, Noise Level, Price Range  
- Removed label leakage (e.g., name, postal_code, stars)  
- Top 20 cuisine categories represented with tri-state indicators  
- Aggregated reviews (mean stars, word length, short-review ratio)

---

## ⚙️ Methods  
Supervised Learning Algorithms:  
- **Logistic Regression**  
- **Elastic Net**  
- **Random Forest**  
- **XGBoost**

Unsupervised Clustering:  
- **K-Prototypes** (handles mixed data types; Euclidean + dissimilarity matching)

**Pipeline:**  
- Scikit-learn `ColumnTransformer` with imputation, scaling, and encoding  
- Hyperparameter tuning via Randomized Search (5-fold stratified CV)  
- Metrics: Accuracy, F1, ROC-AUC  
- MLflow for experiment logging & comparison  

---

## 📈 Results  

| Model | Accuracy | F1 Score | ROC-AUC |
|--------|-----------|----------|----------|
| Logistic Regression | 0.690 | 0.648 | 0.760 |
| Elastic Net | 0.677 | 0.638 | 0.760 |
| Random Forest | 0.723 | **0.659** | 0.787 |
| XGBoost | **0.733** | 0.638 | **0.787** |

**Interpretation:**
- Ensemble models outperform linear ones  
- Nonlinear feature interactions drive satisfaction prediction  
- Metadata alone provides strong predictive signal  

### 🔍 Feature Importance  
Top predictors (Random Forest & Logistic Regression):  
- Review Count (log)  
- Average Review Word Length  
- Share of Short Reviews  
- Wheelchair Accessibility  
- Table Service  
- Dog-Friendly  
- Price Range  
- Drive-Thru / Delivery (negative impact)  

**Positive Predictors:** Accessibility, comfort, café or dessert types  
**Negative Predictors:** Fast Food, Burgers, long hours, high noise  

---

## 🧭 Clustering Insights (K-Prototypes, k=3)  

| Cluster | Profile | Avg Rating |
|----------|----------|-------------|
| **1** | Value-oriented, accessible, family-casual | ⭐ **3.61** |
| **0** | Social, mid-priced casual dining | ⭐ **3.43** |
| **2** | Mid-to-upscale dine-in, premium pricing | ⭐ **3.24** |

**Takeaway:** Comfort, Wi-Fi, consistent hours, and moderate pricing predict higher satisfaction. Upscale restaurants underperform when expectations exceed experience.  

---

## 💡 Discussion & Conclusion  
Structured business metadata can **predict Yelp restaurant ratings** without text analysis.  
Tree-based models capture non-linear interactions across price, amenities, and operational patterns.  
Clustering reveals clear **restaurant archetypes** linked to satisfaction and accessibility.

**Practical Implications:**
- Small businesses can enhance ratings via small operational upgrades (Wi-Fi, accessibility, clearer hours).  
- Metadata models offer interpretable, cost-effective tools for marketing and decision-support.  

### 🔮 Future Work  
- Incorporate **text embeddings** from reviews  
- Integrate **temporal** and **geospatial** context (competition, neighborhood trends)  
- Expand clustering to include dynamic sentiment or image data  

---

## 👩‍💻 References (APA)  
- Guo, Y., Lu, A., & Wang, Z. (2017). *Predicting restaurants’ rating and popularity based on Yelp dataset (CS229 Project).* Stanford University.  
- Luo, Y., & Xu, X. (2019). *Predicting the helpfulness of online restaurant reviews using different machine learning algorithms: A case study of Yelp.* *Sustainability*, 11(19), 5254.  
- Starakiewicz, T., & Wójcik, P. (2025). *Predicting restaurant survival using nationwide Google Maps data.* *Knowledge-Based Systems, 313*, 113198.  
- Yu, M. (2015). *Restaurant review star prediction for Yelp dataset (CSE 258 Project).* UC San Diego.  

---

## 📎 Appendices  
- **Appendix A:** Metadata Report (61 engineered features)  
- **Appendix B:** MLflow Dashboard (experiment tracking & model comparison)  
- **Appendix C:** Correlation Heatmap (low multicollinearity)  
- **Appendix D:** Random Forest Tuning (optimal n_estimators ≈ 600, max_features = log2)  
- **Appendix E–G:** K-Prototypes Cluster Profiles (operational archetypes)

---

> 🏁 *“Structured metadata alone can predict Yelp restaurant success.”*  
> This project highlights how data-driven insights can guide smarter, fairer, and more efficient decision-making in the restaurant industry.
