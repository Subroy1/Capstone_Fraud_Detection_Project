🎯# CapstoneProject
Fraud Detection in Credit card payment ecosystem using predcitve Machine Learning and Deep Learning Classifier models . 

⭐### Project Title
Credit Card Fraud Detection Based on Transaction Behaviour using Data Analysis and Machine Learning 

📋#### Executive summary
In this digital era, monetary transactions are accelerating rapidly towards a cashless system along with which the risk of fraudulent transactions is also increasing.
Credit card fraud is the most common type of identity theft causing nightmare and distress to victims (customers) and businesses who have to compensate for the loss in addition to reputational loss[...]
Timely intervention on fraud alerts and customer reach is imperative for smooth running of business and retaining customer trust and loyalty to the financial institutions.
The model can serve as a real-world application of imbalanced classification and cost sensitive Machine Learning approaches.
In this exercice, we built and compared various Predictive machine learning models that can learn from preceding data and estimate high probabilities resulting infraudulent credit card transaction[...]
The real world implementaiton entails monitoring the activities of populations of users in order to estimate, perceive or avoid objectionable behaviour, which consist of fraud, intrusion, and defa[...]

🔍#### Rationale
Timely intervention of credit card companies in alerting customers for suspicious transactions is imperative due to various reasons - 

1. It causes identity theft and distress to victims (customers) and unimaginable financial losses. 
2. Businesses who have to compensate for the loss endured by the customer(s).
3. Financial institutions trust gets eroded for repeat offences causing irrecoverable damage to their reputation, added with penalties from regulatory authorities for compromised systems (Financia[...]
4. Quick identification of frauds cases without causing pain to customers upholds customer loyalty .

❓#### Research Question
In all of the classification machine learning algorithms available to us, which one would best work in detecting close to 100% of fradulent credit card transactions in upholding customer trust and[...]

Hypothesis task-

Goal: To determine if the model (e.g., Logistic Regression) significantly outperforms a baseline (e.g., random guessing or a simple rule-based model) in identifying fraudulent transactions.

Null Hypothesis (Ho): The model has no predictive power; observed fraud detection is due to chance.

Alternative Hypothesis (Ha): The model reliably distinguishes fraudulent from legitimate transactions.

📁#### Data Sources

The dataset is sourced from OpenML and contains historical financial transactions labeled for fraud detection. The target variable is Class, a binary indicator where 1 represents fraud and 0 repre[...]
Features include:

1. **V1–V28** : Anonymized variables derived using Principal Component Analysis to protect sensitive information

2. **Time**: Seconds elapsed since the first transaction (can be converted into time-of-day format)

3. **Amount**: Transaction value

Due to privacy constraints, original features (e.g., location, device type) are not available. While this limits interpretability and exploratory analysis, it does not impact the application of ma[...]

Note: The dataset is in .arff format and can be loaded using scipy.io.arff, then converted to CSV for easier processing.
<img width="569" height="461" alt="image" src="https://github.com/user-attachments/assets/5509cd8b-b4ef-4368-9ef9-8b5e60f1bcb5" />

🔧#### Methodology
From a statistical perspective, fraud cases are extremely rare compared to genuine transactions resulting in extreme class imbalance . 
**Data Cleaning and Preprocessing techniques**
1. Feature importance techniques and correlation analysis will be used for model performance. 
2. Feature scaling would be done where necessary(KNN and SVM which depend on distances of data points) for non-PCA transformed features such as time and amount upon inspection.
3. SMOTE (Synthetic Minority Oversampling Technique) would augment synthetic fraud cases for the model to have a more balanced split of 2 classes (fraud vs non-fraud) only on the training data . 

All preprocessing steps including SMOTE would be applied within a cross validation pipeline to prevent data leakage.
🤖 **Machine learning techniques**
**Machine Learning Techniques:**
- 🤖 Logistic Regression
- 🌳 Random Forest
- 🚀 XGBoost
- 🔍 Isolation Forest (unsupervised)
  
Supervised techniques such as Logistic Regression,KNN, Random Forest (bagging), SVM classifiers (with various kernels such as Polynomial, linear and RBF ) , XGBoost and Decision Trees would be use[...]

Some unsupervised techniques to automatically detect anomalies such as Isolation Forest would be explored. 

Since synthesized data can introduce noise and this is a classification problem, some algorithms may even perform poorly with sampling,we would run w/o sampling with class_weight='balanced' to cou[...]

Finally, GridSearchCV with stratification(consistent class proportions) would be run for identifying correct hyperparameters yielding best estimator results. Training and prediction times would al[...]

**Evaluation metrics**
In order to evaluate performance of different algorithms, confusion matrix , F1-score , precision and recall would be used. Specifically , aim would be for a high recall score to avoid any fraud t[...]

Precision would also need to be moderately high at an acceptable level to avoid declining transactions of too many customers. To keep a balance , F1-score would also be evaluated. Similarly, AUROC[...]

As such, the best model would be with a larger area under Precision-Recall-Curve  for an imbalanced test dataset like fraud detection. 

📈 #### Results
✅ For imbalanced datasets like fraud detection, PRC AUC is generally a more reliable and informative metric than ROC AUC because it focuses on the performance of the minority class, which is typical[...]

Noise Amplification: Most likely what happened is given that fraudulent data point is an outlier—an isolated transaction that doesn't share characteristics with other fraud, SMOTE created synthe[...]

⚠️ROC AUC (Receiver Operating Characteristic - Area Under the Curve): This metric plots the True Positive Rate (TPR) against the False Positive Rate (FPR) at various threshold settings. An ROC AUC o[...]

🔄#### Next steps
The primary purpose at this point is EDA on the given dataset with a simple baseline model to set the stage for more sophisticated model comparisons afterwards. In part II of the assignment , we w[...]

Model deployment and finding model by scalability and suitability to actual business,  millions of transactions happen across various online platofrms such as Mobile device , internet , payment ga[...]

Multinomial classification models need to be built to categorize type of frauds in order to optimize resource spend in improving transaction processes. 

📑#### Outline of project
https://github.com/Subroy1/CapstoneProject/blob/main/CreditCardFraudCapstone.ipynb

👤### Author
Subhojit Roy

📞##### Contact and Further Information
**NOTE ** EDA has been complemented by manual visual inspections (describe,info, exploration of PCA values and their relationships) plus a relative feature importance as revealed through L1 regula[...]
