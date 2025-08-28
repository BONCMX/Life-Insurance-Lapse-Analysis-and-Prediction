# Life Insurance Lapse Analysis and Prediction

## ⚡ Executive Summary
- **Top Drivers**: Auto-debit status, sourcing channel (Online), first payment method, customer profile (income, education, city tier), premium size.  
- **Best Model**: HistGradientBoosting — ROC AUC **0.84**, Recall (lapse) **0.88**.  
- **Key Finding**: Policies without auto-debit are at **95% higher lapse risk**.  
- **Business Action**: Target High-Risk customers with proactive outreach & auto-debit promotion.  
- **Impact**: Improve persistency → +5% retention = up to **+25% profit uplift**.  

---

## 🌍 Why This Project Matter

In life insurance, **persistency is one of the most critical health indicators** of a portfolio.  
High lapse rates create operational inefficiencies, erode customer trust, and complicate long-term financial planning.  

Yet, insurers often struggle to answer two essential questions:
1. **What are the key drivers behind policy lapses?** – Are lapses driven more by payment methods, distribution channels, customer demographics, or product design?  
2. **Which customers are most at risk of lapsing?** – Can we anticipate lapse behavior early enough to intervene?

This project addresses both questions by combining **advanced analytics techniques** with **deep domain knowledge in life insurance**, offering a structured way to uncover hidden patterns and build predictive risk models that are interpretable and actionable.


---

## 🎯 Objectives
1. **Uncover Drivers of Lapse** → Understand key behavioral, demographic, and product factors.  
2. **Build Predictive Models** → Score customers by lapse probability.  
3. **Enable Business Action** → Segment into High/Medium/Low risk for targeted retention.  

---

## 📂 Data
- **Source**: Anonymized life insurance dataset (100k+ policies).  
- **Target**: `lapse_inforce` (1 = Lapse, 0 = Inforce).  
- **Key Variables**:
  - Payment behavior (auto-debit, method, frequency)  
  - Channel (sourcing, sub-channel)  
  - Customer profile (income, education, age, city tier)  
  - Policy attributes (premium, product type)  
  - Agent experience  

---

## 🛠 Methodology
1. **EDA**: lapse rate distribution, CI analysis, bivariate comparisons.  
2. **Feature Importance**: Logistic L1 (signed coef), Tree Ensembles (RF, ET, HGB), Permutation Importance.  
3. **Predictive Modeling**: HGB, RF, ET, Logistic L1.  
4. **Evaluation Metrics**: ROC AUC, Accuracy, Balanced Accuracy, Precision, Recall, F1.  

---

## 📊 Results

### 🔑 Top 10 Drivers of Lapse
![Feature Importance](images/feature_importance.png)  
**Insight**: Auto-debit, sourcing channel, and payment method dominate risk factors.  

### 🏆 Model Performance
| Model                | ROC AUC | Accuracy | BalancedAcc | F1  | Precision | Recall |
|----------------------|---------|----------|-------------|-----|-----------|--------|
| HistGradientBoosting | **0.84** | 0.80     | 0.70        | 0.87 | 0.86      | **0.88** |
| Logistic L1          | 0.82    | 0.74     | 0.78        | 0.81 | **0.94**  | 0.70   |
| Random Forest        | 0.81    | 0.76     | 0.76        | 0.83 | 0.91      | 0.76   |
| Extra Trees          | 0.79    | 0.78     | 0.70        | 0.86 | 0.86      | 0.86   |

### ROC Curve (Model Comparison)
![ROC Curve](images/roc_curves.png)  
**Insight**: HGB clearly dominates in distinguishing lapse vs. inforce.  

### Precision–Recall Curve (Best Model: HGB)
![PR Curve](images/pr_curve.png)  
**Insight**: At threshold ~0.5, Precision=0.86, Recall=0.88. Business can tune threshold:  
- Lower threshold → higher recall, catch more lapse risk.  
- Higher threshold → higher precision, fewer false alarms.  

### Confusion Matrix (HGB – Threshold=0.5)
![Confusion Matrix](images/confusion_matrix.png)  
**Insight**:  
- True Lapse caught: **13.5k** (88%).  
- False Alarms: ~2.2k inforce contracts flagged incorrectly.  

---

## 🚀 Business Implications
- **Auto Debit**: Policies without auto-debit → **95% more likely to lapse**.  
- **Digital/Online channels**: Higher lapse → need stronger onboarding & follow-up.  
- **Socio-demographic factors**: Income, education, city tier strongly linked to persistency.  
- **Agent Experience**: Inexperienced agents’ policies show higher lapse → need coaching.  

**Retention Strategy**:  
- **High Risk (p ≥ 0.70)**: intensive outreach, auto-debit enrollment.  
- **Medium Risk (0.50–0.70)**: early reminders, tailored communication.  
- **Low Risk (<0.50)**: standard retention campaign.  

---

## ⚠️ Limitations & Next Steps
- Data from one insurer; may not generalize across markets.  
- External macroeconomic effects (COVID, recession) not included.  
- Next steps:  
  - Deploy scoring into CRM system.  
  - Monitor model drift quarterly.  
  - Add external features (macro factors, competitor data).  

---

## 🛠 Tech Stack
- **Python**: pandas, numpy, scikit-learn, xgboost  
- **Visualization**: matplotlib, seaborn, plotly  
- **ML Models**: Logistic Regression, Random Forest, Extra Trees, Gradient Boosting  

---

## 📌 Takeaway
This project demonstrates that **data-driven lapse prediction is actionable**:  
- It uncovers *why* policies lapse.  
- It predicts *who* is at risk.  
- It empowers insurers to act *before* customers lapse.  

👉 **Outcome**: boost persistency, reduce acquisition costs, and strengthen long-term customer trust.  
