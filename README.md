# Bank-Marketing
The core task is to predict whether a client will subscribe to a term deposit (a type of savings account) after being targeted by a bank's telemarketing campaign.

# Project Title: Term Deposit Subscription Prediction using Explainable AI (XAI)
Status: Analysis Complete | Final Model: Random Forest | F1-Score: 0.46
 

## 1. Problem Statement
This project addresses the core challenge of bank marketing: efficiently identifying which contacts are most likely to subscribe to a term deposit. The goal was to move beyond high-cost, blanket campaigns by developing a machine learning model that minimizes wasted marketing expenditure and maximizes the conversion rate, especially given the significant class imbalance (only 11.7% of clients subscribe).
## 2. Methodology & Key Findings
We systematically compared three model types, focusing on advanced techniques to handle the highly imbalanced dataset and the non-linear relationship between features.
📈 Model Performance Summary
Model                             Success Rate (F1-Score)     Hits Rate (Recall)       Business Impact Assessment
Baseline (Logistic Regression)    $18\%$                      $17.7\%$                 Unsuitable; missed over 82% of actual customers.
Deep Learning (PyTorch MLP)       $47\%$                      $50\%$                   Highest F1, but marginal gain vs. complexity.
Advanced (Random Forest)          $46\%$                      $49\%$                   Optimal choice. Best balance of performance, stability, and interpretability.

### Key Technique: We found that Threshold Optimization was crucial. By tuning the prediction threshold from the default 0.5 to 0.37 for the Random Forest, we achieved a $\mathbf{48\%}$ increase in the F1-Score, demonstrating that the cost of missing a subscriber outweighs the cost of a false contact.

## 3. Critical Insights from Explainable AI (SHAP)
We used SHAP (SHapley Additive exPlanations) on the final Random Forest model to move beyond prediction and diagnose why the model was failing to identify the remaining False Negatives. This diagnosis provides an actionable roadmap for marketing strategy and future feature engineering.
Positive Drivers (The Success Profile): 
The strongest indicators of a 'Yes' prediction were features related to Age, previous campaign success, and account balance.

Negative Drivers (The Failure Profile): 
The model penalized potential subscribers who displayed characteristics of historical resistance. The primary factors pushing predictions down were:

  Failed Contact History: High number of previous failed contacts.

  Stale Leads: Long duration since the last contact (high pdays value).

  Financial Strain: Indicators like unemployment or existing loan obligations.

Actionable Strategy: This analysis proves that the model's limitations are due to feature quality, not model architecture. Future work must focus on engineering better features to capture the nuances of "previously unreceptive" clients.

## 4. Final Recommendation and Next Steps
The Tuned Random Forest Model is the recommended solution for immediate deployment.

Deployment: Deploy the Random Forest model using the 0.37 optimized threshold.
Strategic Segmentation: Implement a tiered marketing approach based on SHAP insights:
  Prioritize leads with the highest positive feature contributions.
  Segment leads with high negative contributions into a lower-cost "nurture" track, saving resources.
Future Feature Engineering: The model is capped at 46% F1 until features are engineered to better represent the quality of historical client engagement.
