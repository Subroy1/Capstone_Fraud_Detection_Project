📄 **[VIEW FULL CAPSTONE PROJECT REPORT (PDF)](./Capstone%20Project-%20Credit%20Card%20Fraud%20Detection.pdf)**

> **📌 Note:** Click the link above to open the PDF report. Please continue clicking **"More pages"** to view all contents.

---

🎯# **Project overview**

**Fraud Detection in Credit Card Payments Based on Transaction Behaviour using Data Analysis, Machine Learning and Artificial Neural Network**

---

📋## **Executive Summary**

Credit card fraud continues to be one of the most significant challenges faced by financial institutions, payment processors and merchants. Fraudulent transactions result in direct financial losses.

This project investigates the effectiveness of multiple supervised and unsupervised techniques for identifying fraudulent credit card transactions in a highly imbalanced dataset where fraud instances comprise only 0.2% of all transactions.

🔍Key findings include:

* Model selection should ultimately be guided by business objectives, fraud risk tolerance and operational investigation capacity rather than model metrics alone.

* Logistic Regression and XGBoost consistently achieved the strongest fraud detection performance in traditional models.

* Neural Network (MLP) achieved the best F1 score balancing Precision and Recall .

* Ensemble techniques such as weighted soft voting outsmarted individual models  with tuned weightage.

* Isolation Forest provided a viable alternative when labelled fraud examples are unavailable.

* Lift Curve analysis demonstrated substantial operational advantages and prioritization of addressing fraud cases.

---

❓## **Problem Statement**

Credit card issuers process millions of transactions daily. Detecting fraudulent transactions quickly is essential to:

* Minimize financial losses

* Protect customers from identity theft

* Maintain customer trust and loyalty

* Meet regulatory obligations

* Reduce operational costs associated with fraud investigations

* Reduce False positives causing customer mistrust .

The primary objective is to identify among supervised, unsupervised and deep learning techniques, which models provide the most effective balance between fraud detection performance and operational feasibility.

---

### Hypothesis

**Null Hypothesis (H₀):** The model performs no better than random chance in detecting fraudulent transactions.

**Alternative Hypothesis (H₁):** The model reliably distinguishes fraudulent transactions from legitimate transactions and provides measurable improvements over random selection.

---

🔄## **Project Workflow**

### 1. Problem Definition

Defined fraud detection as an imbalanced binary classification problem.

### 2. ## **Dataset Overview**

The dataset was sourced from OpenML and contains historical credit card transactions labelled as fraudulent or legitimate (https://api.openml.org/data/download/22121069/dataset)

### Dataset Characteristics

* Target Variable: Class

  * 0 = Legitimate Transaction

  * 1 = Fraudulent Transaction

* Highly Imbalanced Dataset

* PCA-transformed anonymized features (V1–V28)

* Additional Features:

  * Time

  * Amount

### Challenges

* Extreme class imbalance (only around 0.2 % fraud transactions)

* Limited interpretability due to PCA transformations and anonymized features 

* Absence of customer, device and location attributes

* Lack of sequential transaction history limiting any inference drawn from ordered transactions . 

### 3. Exploratory Data Analysis

Performed:

* Class distribution analysis

* Correlation analysis

* Temporal and Transaction amount analysis

* Temporal transaction analysis

* Feature importance exploration

### 4. Data Preparation

* Missing value validation (no missing values)

* Feature scaling (for normalization into ML models)

* Train/Test split (using scikit learn library)

* Cross-validation (using grid search parameters)

* SMOTE oversampling (training folds only, model finally generalizable on unseen data)

  ![][image1]

### 5. Feature Engineering

* Time-based feature analysis

* Transaction amount normalization

* Feature scaling for distance-based algorithms

* Engineered trigonometric features for capturing cyclical time in a 24 hour period. 

* Class balancing through SMOTE

  ![][image2]

### 6. Model Development

Developed and evaluated:

* Logistic Regression

* Decision Tree

* Random Forest

* SVM

* XGBoost

* Isolation Forest

* Voting Ensemble

* Neural Network (MLP)

### 7. Hyperparameter Optimization

GridSearchCV and Stratified Cross Validation were used to identify optimal model parameters and have full representation of the training data used in both validation and training sets.

### 8. Model Evaluation

Performance was measured using multiple business-relevant metrics.

---

📊## **Evaluation Metrics**

Given the severe class imbalance, Accuracy alone is not an appropriate measure of performance.

The following metrics were used:

### Recall

Measures the proportion of frauds successfully detected.

A high Recall reduces missed fraudulent transactions (False Negatives).

### Precision

Measures the proportion of flagged transactions that are genuinely fraudulent.

A high Precision reduces unnecessary customer interventions.

### F1 Score

Balances Precision and Recall.

### Anomaly- recall Score

Converting anomaly scores into appropriate format for isolation forest.

### ROC-AUC

Measures overall class separation ability.

### Precision-Recall AUC (PR-AUC)

Primary evaluation metric for this project because it focuses on minority class performance.

### Lift Curve

Measures operational effectiveness by comparing model performance against random transaction selection.

---

📈## **Supervised Learning Results**

**![][image3]**

### Key Findings (Individual models- supervised)

![][image4]

* Logistic Regression achieved the highest Recall of its own.

* XGBoost produced the strongest overall balance between Recall and Precision.

* Decision Trees exhibited signs of overfitting.

* SVM produced strong Precision but incurred extremely high training times.

* Random Forest achieved strong Precision but lower Recall than XGBoost.


---

🧠## **Artificial Neural Network Results**

**![][image5]**

![][image6]

The Multilayer Perceptron(MLP) successfully identified complex nonlinear relationships within the data and produced:

* High Recall

* Strong F1 Score

* Excellent classification accuracy

The model achieved only 16 False Negatives while maintaining a competitive balance between fraud detection and operational overhead.Its F1- score is the highest amongst all models evaluated . 

---

🌲## **Unsupervised Learning Test Results**

### ![][image7]

### ![][image8] Why Unsupervised Learning Matters

Isolation Forest provides a useful solution when:

* Fraud labels are unavailable, such as new CC organizations.

* Historical transaction patterns are limited with no prediction power. 

* New credit card products are launched for existing issuers . 

* Emerging fraud patterns are being observed and considered anomalies by training completely on existing normal data.

---

🤝## **Ensemble Learning Experiment**

### Weighted Voting Classifier

Participating Models:

* Logistic Regression (50%)

* XGBoost (40%)

* SVM (10%)

### Design Rationale

* Logistic Regression contributed a strong Recall hence given the highest weight.

* XGBoost contributed balanced classification performance with low training time.  
  (In real time systems , model times are significant for risk mitigation). 

* SVM contributed high Precision and helped reduce False Positives.

Careful selection of constituent estimators is essential when balancing Recall and Precision in highly imbalanced datasets.

![][image9]

**Future experiments combining MLP and XGBoost may provide further improvements.**

---

📈## **Lift Curve Analysis and Business Value**

Lift Curves evaluate how effectively a model prioritizes high-risk transactions compared with random guessing.

The business question answered is:

"If I investigate the highest-risk transactions first, how much better am I performing than random selection?"

![][image10]

The above table (sorted descending gives greatest lift for top 1% and 10% deciles and tied at 5%/). 

![][image11]

### Business approach to investigation 

* Lift@10% ≈ 9.05x

* Lift@1% ≈ 86.39x

This indicates that by reviewing only the highest-risk transactions for a weighted ensemble, fraud investigators can identify significantly more fraudulent transactions than random review strategies.

Lift analysis would always be supplemented with:

* Investigation costs

* Operational staffing

* Customer impact

* Regulatory requirements

In real scenarios , decisions are made based on costs incurred in compensating customers , fraud investigation costs , regulatory costs and also following a cost-based-on-amount of individual frauds.

### Business benefits 

* Improved resource allocation

* Reduced investigation costs

* Better customer outreach prioritization

* Enhanced fraud prevention efficiency

---

💡## **Technical Insights**

* ANN MLP provided the best scores across all the metrics in its ability to unravel complex patterns within its latent space . 

* PR-AUC proved more informative than ROC-AUC for this imbalanced dataset.

* Accuracy in absolute terms is not the right indicator for fraud classification. 

* XGBoost consistently delivered strong and stable performance.

* Logistic Regression remained surprisingly competitive despite its simplicity.

* SMOTE occasionally introduced synthetic noise and degraded model performance.

* Ensemble performance depends heavily on tuned constituent model selection and provided the biggest lift for prioritizing fraud investigations and alerting .

* Training time should be considered alongside predictive performance.

---

🏦## **Business Insights**

The best model is not necessarily the model with the highest metric score.

Real-world deployment decisions depend upon:

* Customer base characteristics

* Fraud risk appetite

* Investigation capacity

* Cost of False Negatives

* Cost of False Positives

The metrics provide the strongest signal based on high Recall, F1-score and AUPRC but a model with marginally lower Recall may be preferable if it substantially reduces operational costs (Cost of False Positives).

---

⚠️## **Limitations**

* PCA-transformed features reduce interpretability.

* Original customer and transaction context is unavailable.

* Computational limitations restricted some large-scale experiments such as SVMs and Random Forests .

* Location and device-level information were unavailable.

* Deep sequence models such as LSTMs could not be evaluated due to lack of customer specific information on sequential history.

---

📌## **Final Recommendation(s)**

### Recommended Supervised Model

**XGBoost or Ensemble including XGB** 

* Strong Recall and Lift **(@10%- 9.37- XGB and 9.05 Ensemble)**

* High Precision-Recall tradeoff **(AUPRC - XGB- 0.71, Ensemble - 0.67)**

* Strong class separation capability (**XGB ROC 0.98 , Ensemble-0.97**)

* Highest business applicability

### MLP Neural Network

* Strong Recall (83%)

* High F1 Score (0.46)

* Few False positives compared to XGB

* Ability to learn nonlinear fraud patterns

* Quicker to train than other supervised models .


### Recommended Unsupervised Model

**Isolation Forest**

* Effective when labelled fraud data is unavailable

* Useful for new issuers and emerging fraud patterns

Ultimately, model selection should be driven by business objectives, operational constraints and fraud risk tolerance rather than raw evaluation metrics alone.

---

🚀## **Future Work**

Potential future enhancements include:

* ANN + XGBoost hybrid ensembles

* Further Threshold optimization experiments on XGB 

* One-Class SVM anomaly detection as an additional alternative to unsupervised learning for novelty detection considering only majority class samples 

* Location-based fraud indicators (if available GPS location)

* Multiclass fraud categorization (payment channel, identity theft , mobile device)

* 2-step multi factor authentication as an additional layer 

👤## **Author**

Subhojit Roy

📞## **Contact and Further Information**

**(https://www.linkedin.com/in/subhojitroy/)**

Project repository layout ![][image12]

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAREAAADdCAIAAAATq9GiAAAabklEQVR4Xu2dC1xU1b7HEXkIKi8hFUT0PFpKcjx19dyrXryVmfjKjidC8x1WPCRUXtIwDAYqKGo+CvOt3TzqPZkGFmlmPsjHDU1F08yTHkvNBF8hKs[...]

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAREAAADYCAIAAABDZkARAAAZs0lEQVR4Xu2dCXQVVZqAE7KxhCQsARMgUREZhAHSB2hBAoNimAOYTDMKokK0zwSDKDJiENQQtWVRaNAmQWCQRWgWmZmQZoKBZgk7kUyCnNMgNoRGDJ[...]

[image3]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAnAAAABRCAYAAABSfJsZAAAjSElEQVR4Xu1dTY7cRtLVRQyoLvHtvDHU0D28FaAGhLmE14YWmj7BHECAFz3N5RzB0K7Vd9B26qvIiJf5Mpisn26WVKV5DwiRlUxmxn8E2Yb5aisIgi[...]

[image4]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAApUAANCCAYAAAAXHTOtAAA0qUlEQVR4Xu2dB5gUVfbFyUmEGUTJoIiggAIqICrKCgoYwIwoQVGCgLgiUSUZQJE1A2JAXEQws64g6CKL7oKu/BUTGNFdRMAAsypJwvtz3vhqq+59A1[...]

[image5]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAdYAAAA7CAYAAADGt6uyAAANhElEQVR4Xu2bC27byBJFsxUtxshyBHg3hrbigbcSeCN8apJNVt261fyo5Rnl3QMQE/6q619NJfNrEEIIIYQQQpxHg1UIIYToiAarEEII0R[...]

[image6]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQ4AAADrCAYAAACYT3ggAAAfhUlEQVR4Xu2dC3gN19rHWw7bpW5VB6UcbX36aU9R5VRRPXUrdWi1VepUqm1c6lqXoBWpu96iSlxKUTRBaUIrqLsSQURSkRASl4hE0LhFErf15V39Zp[...]

[image7]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAnAAAAAtCAYAAAAunFajAAAOuklEQVR4Xu2biW3kPAyFt5UpZpByBkg3i7SSH24lSCP+Rwcl8pHyMUcSZ98HGJt4bImieDx7sn9mQgghhBByKP7gCUIIIYQQ8rOhgCOEEEIIORi/WM[...]

[image8]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQwAAADoCAYAAAAaLtqzAAAhzElEQVR4Xu2dCXhN19rHDcShRVqqah6qeltfDUVRqoPpq146D/feUoqaiiIpVVKt4tJL0WhVa665ElMk5jFiSkwREkkQGcSQGCKJ4P3yrvvt/Zyscx[...]

[image9]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQQAAADgCAYAAADlqhgqAAAh+klEQVR4Xu2dB3gUVduGCSGJ0lEMTUAghSagCFIFJIIoBpEuCCQUpSggRsCAFCMECVEEQlG6kCAiIvoBIlXB8MFHEYKA9N6DWBBBz5/3+M84e3bPZu[...]

[image10]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAUcAAAD8CAYAAADkM2ZpAAAfZElEQVR4Xu2dTW7kuhWFs5EA9kIyMdp4+8jUQBfQu8jY8KCfV5AFNOCBEw+zhIZnnd6Dp1GKlEhe3ntIUSq5xLLPBxzklX4o/n5FlV/w/jIQQsiOX[...]

[image11]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgkAAAFRCAYAAAD+Vz7/AAA/iUlEQVR4Xu3dB7wU1dnHcSnSBUFABRQ72E3EFuxd0ahYSETFEt9YomISO4hKBGPB+tqS2IMajaK+ajQFTewKtmhUUMCCmgAaEaXe887/rGfu2XN37[...]

[image12]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAjUAAAEUCAYAAADTDceWAAAh5ElEQVR4Xu2dS47jSJZFcwO+lZi4EA30MnKSUwE+ym30pEcO7cUBDXvYe8hGDHoDPavKqooqVKll/L537SOap1whPj8XOMgQKfu8R9Ls0qh0/nRGC[...]
