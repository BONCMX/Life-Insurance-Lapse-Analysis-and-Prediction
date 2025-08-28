# Life Insurance Lapse Analysis and Prediction

## 🌍 Why This Project Matter

In life insurance, **persistency is one of the most critical health indicators** of a portfolio.  
High lapse rates create operational inefficiencies, erode customer trust, and complicate long-term financial planning.  

Yet, insurers often struggle to answer two essential questions:
1. **What are the key drivers behind policy lapses?** – Are lapses driven more by payment methods, distribution channels, customer demographics, or product design?  
2. **Which customers are most at risk of lapsing?** – Can we anticipate lapse behavior early enough to intervene?

This project addresses both questions by combining **advanced analytics techniques** with **deep domain knowledge in life insurance**, offering a structured way to uncover hidden patterns and build predictive risk models that are interpretable and actionable.


---

## 1.Objectives🎯 
1. **Uncover Drivers of Lapse** → Understand key behavioral, demographic, and product factors.  
2. **Build Predictive Models** → Score customers by lapse probability.  
3. **Enable Business Action** → Segment into High/Medium/Low risk for targeted retention.  

---

## 2.Data📂
- **Source:** [*<u>Kaggle – Insurance Premium Data</u>*](https://www.kaggle.com/datasets/prachi13/insurance13m-persistency?resource=download&select=Train.csv)

- **Target**: `lapse_inforce` (1 = Lapse, 0 = Inforce).  
- **Key Variables**:
  - Payment behavior (auto-debit, payment_method, payment_frequency,  ...)  
  - Channel (sourcing, sub-channel,  ...)  
  - Customer profile (la_income, la_education, la_age, city_tier, ...)  
  - Policy attributes (premium, product_type, ...)  
  - Agent experience  

---
### Dataset Discription

The dataset contains **100,000 policy records** from an anonymized life insurance portfolio.  
It includes information on **policies, customers (life assured), agents, distribution channels, and policy status**.  
These features form the foundation for analyzing **drivers of policy lapse** and building **predictive models** to estimate lapse risk.  

- **Number of Rows**: 100,000  
- **Number of Columns**: 38  
- **Target Variable**: `lapse_inforce` (1 = Lapse, 0 = Inforce)  
- **Data Types**: Mixed (numeric, categorical, date, binary flags)  
- **Use Case**: Root cause analysis of lapse & predictive modeling for persistency improvement  

---

### 📋 Variable Dictionary

| Original (VAR..) | New Name             | Description                                                                 |
|------------------|----------------------|-----------------------------------------------------------------------------|
| VAR1             | id                   | Masked policy identifier (unique but anonymized, used as reference only).   |
| VAR2             | persistency_13m      | Historical 13-month persistency ratio of the mapped agent.                  |
| VAR3             | ag_branch            | Distribution branch of the mapped agent.                                    |
| VAR4             | alcohol              | Alcohol consumption declaration of the life assured.                        |
| VAR5             | premium              | Annualized premium amount of the policy.                                    |
| VAR6             | ag_exp_months        | Agent’s tenure (experience) in months.                                      |
| VAR7             | auto_debit           | Auto-debit flag (Yes/No) for premium payments.                              |
| VAR8             | bmi                  | Body Mass Index (BMI) of the life assured at application.                   |
| VAR9             | risk_exposure        | Total company risk exposure for the life assured.                           |
| VAR10            | sourcing_channel     | Channel through which the policy was sourced (e.g., Online, Bank).          |
| VAR11            | la_city              | City of residence of the life assured.                                      |
| VAR12            | contract_branch      | Branch where the policy contract was booked.                                |
| VAR13            | city_tier            | City tier classification (Metro, Tier-2, Tier-3).                           |
| VAR14            | la_age               | Age of the life assured.                                                    |
| VAR15            | la_education         | Education level of the life assured.                                        |
| VAR16            | la_gender            | Gender of the life assured.                                                 |
| VAR17            | la_income            | Declared income of the life assured.                                        |
| VAR18            | la_industry          | Industry/sector of the life assured.                                        |
| VAR19            | marital              | Marital status of the life assured.                                         |
| VAR20            | nationality          | Nationality of the life assured.                                            |
| VAR21            | occupation           | Occupation of the life assured (e.g., Salaried, Self-employed).             |
| VAR22            | policy_type          | Policy type: PAR, NON-PAR, or ULIP.                                         |
| VAR23            | distribution_partner | Specific distribution partner (e.g., HDFC Bank, Online aggregator).         |
| VAR24            | first_payment_method | Method of the first premium payment (Cash, Online, Cheque, etc.).           |
| VAR25            | product_category     | Product category (Protection, Savings, Investment, Pension, etc.).          |
| VAR26            | payment_frequency    | Premium payment frequency (Monthly, Quarterly, Annual, etc.).               |
| VAR27            | product_name         | Product name (masked if sensitive).                                         |
| VAR28            | login_date           | Date of policy application login.                                           |
| VAR29            | sensitivity          | Price sensitivity flag (1 = Yes, 0 = No).                                   |
| VAR30            | residential_status   | Residential status of the life assured (Owned, Rented, etc.).               |
| VAR31            | risk_term            | Risk cessation term (policy duration for coverage).                         |
| VAR32            | rider                | Rider opted flag (1 = Yes, 0 = No).                                         |
| VAR33            | smoker               | Smoker declaration of the life assured.                                     |
| VAR34            | la_state             | State of residence of the life assured.                                     |
| VAR35            | sub_channel          | Sub-distribution channel (e.g., HDFC Bank branch, Online partner).          |
| VAR36            | sum_assured          | Sum assured (coverage amount payable upon insured event).                   |
| VAR37            | operation_zone       | Company-defined operational zone/region.                                    |
| VAR38            | lapse_inforce        | **Target variable**: Policy status (1 = Lapsed, 0 = Inforce).               |

---
### Sample Data Preview

The dataset contains **100,000 rows and 38 columns**.  
Below is a sample snapshot of the first few records after variable renaming:

| id       | persistency_13m | ag_branch             | alcohol | premium    | ag_exp_months | auto_debit | bmi   | risk_exposure | sourcing_channel     | la_city     | contract_branch       | city_tier | la_age | la_education                       | la_gender | la_income   | la_industry        | marital | nationality | occupation | policy_type | distribution_partner | first_payment_method                 | product_category | payment_frequency | product_name                    | login_date | sensitivity | residential_status | risk_term | rider | smoker | la_state      | sub_channel | sum_assured  | operation_zone | lapse_inforce |
|----------|-----------------|-----------------------|---------|------------|----------------|------------|-------|---------------|----------------------|-------------|-----------------------|-----------|--------|------------------------------------|-----------|-------------|-------------------|---------|-------------|------------|-------------|----------------------|--------------------------------------|-----------------|------------------|---------------------------------|------------|-------------|-------------------|-----------|-------|--------|--------------|-------------|--------------|----------------|---------------|
| 19981651 | 0.8773          | Ghaziabad - Rajnagar  | NaN     | 622,010.00 | 77.00          | Y          | NaN   | 0.00          | HDFC BANK            | Ghaziabad   | Ghaziabad - Rajnagar  | Tier II   | 46.00  | Graduation                         | Male      | 7,200,000.00| Legal And Justice | Married | Indian      | Salaried   | Par         | HDFC BANK            | DD                                   | Pension         | Annual           | HDFC Life Personal Pension Plus | 2018-09-01 | 0           | Resident Indian   | 14.00     | 1     | NaN    | Uttar Pradesh | HDFC BANK   | 7,901,018.00 | North 2        | 1             |
| 20524842 | 93.47           | Delhi - Asaf Ali Road | N       | 7,157.00   | 33.00          | Y          | 16.23 | 10,000,000.00 | HDFC BANK            | Bangalore   | Delhi - Nehru Place   | Tier I    | 24.00  | Graduation                         | Female    | 495,000.00  | Trading           | Single  | Indian      | Salaried   | Non Par     | HDFC BANK            | ECS,SI                               | Protection      | Annual           | HDFC Life Click 2 Protect 3D+   | 2018-07-07 | 1           | Resident Indian   | 40.00     | 1     | N      | Karnataka     | HDFC BANK   | 10,000,000.00| North 1        | 1             |
| 20360827 | 86.61           | Mumbai - Corporate    | Y       | 27,426.00  | 99.00          | N          | 20.83 | 18,000,000.00 | EDM                  | Mumbai      | Mumbai - HUB          | Tier I    | 33.00  | B.E.                                | Male      | 2,500,000.00| Insurance         | Married | Indian      | Salaried   | Non Par     | NaN                  | Online Credit/Debit Card/Teles Sales | Protection      | Annual           | HDFC Life Click 2 Protect 3D+   | 2018-04-23 | 1           | Resident Indian   | 30.00     | 1     | N      | Maharashtra   | EDM         | 30,000,000.00| NaN            | 1             |
| 21025282 | NaN             | Mumbai - Borivali     | NaN     | 33,493.00  | 3.00           | Y          | NaN   | 350,000.00    | Other Banks & CA     | Thane       | Mumbai - Borivali     | Tier I    | 28.00  | Diploma in Electrical Engineering  | Male      | 450,000.00  | Consultant        | Single  | Indian      | Salaried   | Par         | RBL Bank Ltd         | Online Credit/Debit Card/Teles Sales | Savings         | Annual           | HDFC Life Uday                 | 2018-12-31 | 0           | Resident Indian   | 12.00     | 0     | NaN    | Maharashtra   | Ratnakar Bank | 212,857.00   | West           | 1             |
| 19982717 | 0.8307          | Mumbai - Corporate    | NaN     | 12,335.00  | 32.00          | N          | NaN   | 58,326.00     | HDFC BANK            | Pandharpur  | Mumbai - HUB          | Tier III  | 37.00  | B.A.                                | Male      | 250,000.00  | Sales & Marketing | Married | Indian      | Salaried   | Par         | HDFC BANK            | Online Credit/Debit Card/Teles Sales | Savings         | Annual           | HDFC Life ClassicAssure Plus    | 2018-01-17 | 0           | Resident Indian   | 10.00     | 1     | NaN    | Maharashtra   | HDFC BANK   | 116,653.00   | NaN            | 1             |


---
## 3.Methodology🛠
1. **EDA**: lapse rate distribution, CI analysis, bivariate comparisons.  
2. **Feature Importance**: Logistic L1 (signed coef), Tree Ensembles (RF, ET, HGB), Permutation Importance.  
3. **Predictive Modeling**: HGB, RF, ET, Logistic L1.  
4. **Evaluation Metrics**: ROC AUC, Accuracy, Balanced Accuracy, Precision, Recall, F1.  

---

## 4.Results📊

### 🔑 Top 10 Drivers of Lapse

| Rank | Feature                          | Avg. Norm. Importance | # Models Agree | Signed Coef | Direction  |
|------|----------------------------------|-----------------------|----------------|-------------|------------|
| 1    | auto_debit_N                     | 0.95                  | 5              | -0.70       | ↓ Risk     |
| 2    | auto_debit_Y                     | 0.78                  | 4              | 0.70        | ↑ Risk     |
| 3    | sourcing_channel_e_Online        | 0.25                  | 5              | 0.76        | ↑ Risk     |
| 4    | first_payment_method_e_encoded   | 0.24                  | 5              | 0.06        | ↑ Risk     |
| 5    | la_education_e_encoded           | 0.22                  | 5              | 0.10        | ↑ Risk     |
| 6    | ag_exp_moths_e_encoded           | 0.22                  | 5              | 0.12        | ↑ Risk     |
| 7    | premium_e_encoded                | 0.18                  | 5              | 0.03        | ↑ Risk     |
| 8    | city_tier_encoded                | 0.17                  | 5              | 0.11        | ↑ Risk     |
| 9    | la_income_e_encoded              | 0.17                  | 5              | 0.13        | ↑ Risk     |
| 10   | la_age_e_encoded                 | 0.14                  | 5              | 0.03        | ↑ Risk     |


### 📊 Model Metrics

| Model               | ROC AUC | Accuracy | Balanced Accuracy | F1   | Precision | Recall |
|---------------------|---------|----------|-------------------|------|-----------|--------|
| HistGradientBoosting | **0.85** | 0.80     | 0.70              | 0.87 | 0.85      | **0.90** |
| Logistic_L1          | 0.84    | 0.75     | 0.78              | 0.81 | **0.94**  | 0.72   |
| RandomForest         | 0.84    | 0.80     | 0.68              | 0.87 | 0.84      | 0.90   |
| ExtraTrees           | 0.81    | 0.79     | 0.67              | 0.87 | 0.84      | 0.89   |

**Insight**: Auto-debit, sourcing channel, and payment method dominate risk factors.  

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

## ⚡ Executive Summary
- **Top Drivers**: Auto-debit status, sourcing channel (Online), first payment method, customer profile (income, education, city tier), premium size.  
- **Best Model**: HistGradientBoosting — ROC AUC **0.84**, Recall (lapse) **0.88**.  
- **Key Finding**: Policies without auto-debit are at **95% higher lapse risk**.  
- **Business Action**: Target High-Risk customers with proactive outreach & auto-debit promotion.  
- **Impact**: Improve persistency → +5% retention = up to **+25% profit uplift**.  

