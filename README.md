# ML-AI-Capstone_Diabetes-Readmission
Hospitals are constantly looking for ways to minimize costs and provide better patient care. Hospital stays require significant resources and it means added burden on hospitals, medical providers and patients alike. In this study, we find a way to identify diabetic patients who are likely to be readmitted based on their past utilization data using various classification techniques (Logistic Regression, Decision Tree, KNN Classifier and Support Vector). The result would allow hospitals to plan and manage resource allocation accordingly. It would also enable the hospitals to build early intervention programs for some of the patients identified as likely to be readmitted. This would prevent readmission and save costs for the hospital and patients alike.

## Data
Data comes from UCI ML Repository. It can found under Capstone/Data/diabetic_data.csv

Data can be downloaded from here:
https://archive.ics.uci.edu/ml/datasets/Diabetes+130-US+hospitals+for+years+1999-2008#

This dataset is 10-years (from 1999 to 2008) of clinical care at 130 US hospitals and integrated delivery networks.
It contains 101,766 instances (patients) that are classified into three classes: 0 means no readmission, 1 means readmission in less than 30 days, and 2 means readmission in more than 30 days. Missing values are identified by "?" in the data.

In the process of our model design, we classify output into two classes (0 no readmission and 1 means readmitted)

## Data Fields

- race Values: Caucasian, Asian, African American, Hispanic, and other
- gender Values: male, female, and unknown/invalid
- age Grouped in 10-year intervals: 0, 10), 10, 20), …, 90, 100)
- weight Weight in pounds.
- admission_type_id Integer identifier corresponding to 9 distinct values, for example, emergency, urgent, elective, newborn, and not available
- discharge_disposition_id Integer identifier corresponding to 29 distinct values, for example, discharged to home, expired, and not available
- admission_source_id Integer identifier corresponding to 21 distinct values, for example, physician referral, emergency room, and transfer from a hospital
- time_in_hospital Integer number of days between admission and discharge
- payer_code Integer identifier corresponding to 23 distinct values, for example, Blue Cross/Blue Shield, Medicare, and self-pay
- medical_specialty Integer identifier of a specialty of the admitting physician, corresponding to 84 distinct values, for example, cardiology, internal medicine, family/general practice, and surgeon
- num_lab_procedures Number of lab tests performed during the encounter
- num_procedures Number of procedures (other than lab tests) performed during the encounter
- num_medications Number of distinct generic names administered during the encounter
- number_outpatient visits Number of outpatient visits of the patient in the year preceding the encounter
- number_emergency visits Number of emergency visits of the patient in the year preceding the encounter
- number_inpatient visits Number of inpatient visits of the patient in the year preceding the encounter
- diag_1 The primary diagnosis (coded as first three digits of ICD9); 848 distinct values
- diag_2 Secondary diagnosis (coded as first three digits of ICD9); 923 distinct values
- diag_3 Additional secondary diagnosis (coded as first three digits of ICD9); 954 distinct values
- number_diagnoses Number of diagnoses entered to the system
- max_glu_serum Indicates the range of the result or if the test was not taken. Values: “>200,” “>300,” “normal,” and “none” if not measured
- A1Cresult Indicates the range of the result or if the test was not taken. Values: “>8” if the result was greater than 8%, “>7” if the result was greater than 7% but less than 8%, “normal” if the result was less than 7%, and “none” if not measured.
- For the generic names: metformin, repaglinide, nateglinide, chlorpropamide, glimepiride, acetohexamide, glipizide, glyburide, tolbutamide, pioglitazone, rosiglitazone, acarbose, miglitol, troglitazone, tolazamide, examide, citoglipton, insulin, glyburide-metformin, glipizide-metformin, glimepiride-pioglitazone, metformin-rosiglitazone, and metformin-pioglitazone, the feature indicates whether the drug was prescribed or there was a change in the dosage. Values: “up” if the dosage was increased during the encounter, “down” if the dosage was decreased, “steady” if the dosage did not change, and “no” if the drug was not prescribed
- change Indicates if there was a change in diabetic medications (either dosage or generic name). Values: “change” and “no change”
- diabetesMed Indicates if there was any diabetic medication prescribed. Values: “yes” and “no”
- readmitted Days to inpatient readmission. Values: “2” if the patient was readmitted in less than 30 days, “1” if the patient was readmitted in more than 30 days, and “0” for no record of readmission.

## Data Exploration

### Distributions

![Distribution by Gender](/Capstone/images/dist_gender.jpg)
![Distribution by Age](/Capstone/images/dist_age.jpg)

### Correlation
We examined correaltion betweeen numeric fields including encoded categorical ones. We found that there aren't very highly correalted features in the data.

![Correaltion](/Capstone/images/corr.jpg)

## Data Cleanup
The data contains missing values and those are filled with the most frequent values obtained by using the mode() function. We dropped columns that had close to 50% missing data ('weight', 'payer_code', 'medical_specialty'). Also dropped encounter id and patient number. We also excluded individual medication prescribed field and used the overall diabetesMed field. This was also done to improve performance because of processing capacity limitations of the machine we are using. We also dropped the 3 diagnoses fields but retained the number of diagnoses field.

In the process of our model design, we classify output into two classes (0 no readmission and 1 means readmitted) instead of the three that appear in the raw data. The output class is balanced.

### Check Output Class balance

![Class Balance](/Capstone/images/class_balance.jpg)

### Redefine Output Class balance

![Redefine Balance](/Capstone/images/redefine_class.jpg)

## Plots
Plots are not saved separately in this repository because of file size. But we have saved some screenshots that are used in this report. They can be found in the folder:  Capstone/images

## Script to run the code
Script can be found under Capstone/Capstone - Diabetes Readmission.ipynb

## Methodology (Model and Feature Selection)
Models tested are limited to the ones learned so far in the program. Current models come from Sci-kit learn package. Future enhancement using more advanced models (such as RandomForest, XGBoost etc.) recommended. If run in better machine with resource capability, the SVM can also be tuned using Grid Search CV (not done here)

We used the dummy classifier with most frequent strategy as the baseline model. All fields were converted to numeric during cleanup and no further encoding was required. We used Standard Scaling transformation before running our classification models.

### Simple Models (Logistic Regression, Decision Tree, KNN Classisifier and Support Vector models)
Then compared Logistic Regression, Decision Tree, KNN Classisifier and Support Vector models against the baseline dummy model and with each other.

Here is an example of one of the simple models (simple logistic regression with default parameters):
![Basic Logistic Regression](/Capstone/images/base_log_reg.jpg)

See comparision of results across the simple models, their ROC curves and confusion matrices.

**Results**
![Basic Model Results](/Capstone/images/base_models_results.jpg)

**ROC Curves**
![Basic Model ROC Curves](/Capstone/images/base_models_ROC_Curves.jpg)

**Confusion Matrices**
![Basic Model Confusion Matrices](/Capstone/images/base_models_Conf_Matrices.jpg)

#### Feature Importance
We used permutation importance to identify important features from the logistic regression model.
![Permutation Importance Logistic Regression](/Capstone/images/perm_imp_base_Log_reg.jpg)

Next we examined the impact of removing the least important feaatures
![Remove Least Important Features Logistic Regression](/Capstone/images/remove_less_imp_features_base_log_reg.jpg)
We retain all features for this the rest of this analysis.

Grid Search CV was used to fine tune the models. We used roc_auc scoring as the output class is balanced.

Here is an example of one of the models using Grid Search CV (Decision Tree):
![Grid Search Decision Tree](/Capstone/images/grid_cv_dcsn_tree.jpg)

**Results from Grid Search**
![Grid Search Model Results](/Capstone/images/grid_cv_best_models_results.jpg)

We plot the Precision-Recall curves, ROC curves and Confusion matrices for the logistic regression, decision tree and KNN classifier with the best parameters obtained from the Grid Search CV

**Precision Recall Curves - Grid Search**
![Grid Search Precision Recall Curves](/Capstone/images/best_Prec_Rec_Curves.jpg)

**ROC Curves - Grid Search**
![Grid Search ROC Curves](/Capstone/images/best_ROC_Curves.jpg)

**Confusion Matrices - Grid Search**
![Grid Search Confusion Matrices](/Capstone/images/best_Conf_Matrices.jpg)

## Finding based on model evaluation and validation
Using roc_auc score in Grid Search CV we found the logistic regression with c=100 and ridge (L2) penalty to be the best model in terms of both test accuracy(0.65) and time. Since it is Logistic Regression, we can also get the probablity that a patient will likely fall into one of the two output classes.

**Recommended Logistic Regression Model**
![Best Logistic Regression](/Capstone/images/best_log_reg.jpg)

## Conclusion
The model and technique provided in this study can be used as a preliminary approach by hospitals to predict future hospital readmission. The model can be scaled to incoporate additional chronic diagnoses that cause frequent inpatient visits but can also be managed without hospital stays. For example, a similar study and model can be built using the same framework to identify chances of readmission in patients admitted to the hospital with heart diseases. The model can further be expanded to include additional hospitals.

The recommended logistic regression model isn't very robust yet. We used some feature engineering techniques with Grid Search CV to improve our model. It can be improved further and we have provided some methods we feel will help in future studies.

## Further Recommendations

### Random Forest
One recommendation was to use Random Forest model to see if it improves test accuracy scores. Upon testing and tuning the Random Forest model using Grid Search CV, the result did not improve. In fact the, the test accuracy was 0.63, lower than that for the Logistic Regression model with c=100 and ridge (L2) penalty at 0.65. 

![Best Random Forest](/Capstone/images/best_random_forest.jpg)

Also, explored feature importance for this best random forest model.
![Best Random Forest Feature Importance](/Capstone/images/random_forest_features.jpg)

### Other Recommendations
Another factor, we feel is worth exploring given a machine with better computation powers, is to include additional factors to the model. Specially including the individual prescribed medication fields might have major impact on improving our model. As some drugs are key in diabetes management whereas others are less frequently used.

Gradient Boost might be worth considering too in future studies.

Also, it would nice to have socio-economic data such as income which determines eating/exercise habits or access to better resources and healthcare services.

