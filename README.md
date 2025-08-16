# Donor Behavior Forecasting: Predicting First-Time Donor Retention Within 35 Days

## Abstract
This project investigates whether the early behavior of first-time donors can predict their likelihood of returning to give again within **35 days**. Using signals from a donor’s first 24 hours of activity, we developed and validated a machine learning model. The best-performing model, **calibrated XGBoost**, achieved strong predictive performance (ROC AUC = 0.75, Accuracy = 68%, Recall for returners = 67%).  

Our findings suggest that early donor engagement patterns carry significant predictive power. The methodology and insights shared here can inform broader donor retention strategies.

---

## Introduction
Donor retention is a critical challenge in sustaining charitable giving. While welcoming first-time donors is important, organizations often lack tools to anticipate who will remain engaged.  

**Research Question**:  
*Can we predict, on Day 1, whether a first-time donor will return to give within 35 days?*

The 35-day cutoff serves as a proxy for “one month,” accommodating variations in calendar length.

---

## Methods

### Data & Features
We extracted donor behaviors and contextual variables from the first 24 hours after a donor’s initial gift. Features were grouped into five categories:  
1. **Platform relationship** (e.g., onboarding completeness, sign-up device)  
2. **Donor properties** (generalized demographics, location type)  
3. **Gift properties** (first gift amount, recurrence, tithe indicator)  
4. **Giving partner context** (partner profile completeness, co-donor activity)  
5. **Engagement signals** (personal notes, acknowledgment timing)  

### Models Tested
- **Logistic Regression**: offered interpretability but was limited to linear assumptions.  
- **XGBoost**: better at capturing non-linear interactions across behavioral and contextual features.  

### Model Choice
A **calibrated XGBoost classifier** was selected. Calibration ensured predicted probabilities aligned with observed outcomes, enabling donor segmentation into *low, medium, and high return likelihood tiers*.

---

## Results

- **ROC AUC**: 0.75  
- **Accuracy**: 68%  
- **Recall (Returners)**: 67%  

### Key Predictors
- **Profile completeness** strongly correlated with donor retention (though potentially affected by data leakage).  
- **Recurring gift setup** and **signup device type** were significant predictors.  
- **Memo engagement** (donors leaving notes) emerged as an important emotional signal.  
- **Calendar features** (day of month, month-end) had minimal predictive value.  

---

## Discussion

### Challenges
- **Data Leakage**: Profile completion data reflected the current state, not necessarily the first-24-hour state.  
- **Class Imbalance**: More donors did not return than those who did. Weighted training was applied to mitigate this.  

### Implications
- Early donor activity offers actionable signals for retention.  
- Behavioral features (e.g., leaving notes, tithe indicators) are as important as transaction size.  
- Predictive models can guide targeted engagement strategies.  

---

## Future Work
- **Eliminate Data Leakage**: Use point-in-time snapshots of donor profiles.  
- **Expand Feature Set**: Incorporate app session data, support interactions, or communication engagement.  
- **Donor–Partner Specific Models**: Extend predictions to determine whether donors return to the *same* giving partner.  
- **Deployment**: Package the model into a donor analytics tool.  

---

## Key Takeaways
- First 24-hour behavior is a strong predictor of donor retention.  
- Machine learning models outperform linear baselines for this task.  
- Addressing data leakage and imbalance is essential for reliable results.  

---
