# ML-AI-Capstone_Diabetes-Readmission
Classification to predict hospital readmission of patients with diabetes using pateint encounter data

## Data
Data comes from UCI ML Repository. It can found under Capstone/Data/diabetic_data.csv

Data can be downloaded from here:
https://archive.ics.uci.edu/ml/datasets/Diabetes+130-US+hospitals+for+years+1999-2008#

This dataset is 10-years (from 1999 to 2008) of clinical care at 130 US hospitals and integrated delivery networks.
It contains 101,766 instances (patients) that are classified into three classes: 0 means no readmission, 1 means readmission in less than 30 days, and 2 means readmission in more than 30 days. Missing values are identified by "?" in the data.

In the process of our model design, we classify output into two classes (0 no readmission and 1 means readmitted)

## Data Fields

race Values: Caucasian, Asian, African American, Hispanic, and other
gender Values: male, female, and unknown/invalid
age Grouped in 10-year intervals: 0, 10), 10, 20), …, 90, 100)
weight Weight in pounds.
admission_type_id Integer identifier corresponding to 9 distinct values, for example, emergency, urgent, elective, newborn, and not available
discharge_disposition_id Integer identifier corresponding to 29 distinct values, for example, discharged to home, expired, and not available
admission_source_id Integer identifier corresponding to 21 distinct values, for example, physician referral, emergency room, and transfer from a hospital
time_in_hospital Integer number of days between admission and discharge
payer_code Integer identifier corresponding to 23 distinct values, for example, Blue Cross/Blue Shield, Medicare, and self-pay
medical_specialty Integer identifier of a specialty of the admitting physician, corresponding to 84 distinct values, for example, cardiology, internal medicine, family/general practice, and surgeon
num_lab_procedures Number of lab tests performed during the encounter
num_procedures Number of procedures (other than lab tests) performed during the encounter
num_medications Number of distinct generic names administered during the encounter
number_outpatient visits Number of outpatient visits of the patient in the year preceding the encounter
number_emergency visits Number of emergency visits of the patient in the year preceding the encounter
number_inpatient visits Number of inpatient visits of the patient in the year preceding the encounter
diag_1 The primary diagnosis (coded as first three digits of ICD9); 848 distinct values
diag_2 Secondary diagnosis (coded as first three digits of ICD9); 923 distinct values
diag_3 Additional secondary diagnosis (coded as first three digits of ICD9); 954 distinct values
number_diagnoses Number of diagnoses entered to the system
max_glu_serum Indicates the range of the result or if the test was not taken. Values: “>200,” “>300,” “normal,” and “none” if not measured
A1Cresult Indicates the range of the result or if the test was not taken. Values: “>8” if the result was greater than 8%, “>7” if the result was greater than 7% but less than 8%, “normal” if the result was less than 7%, and “none” if not measured.
For the generic names: metformin, repaglinide, nateglinide, chlorpropamide, glimepiride, acetohexamide, glipizide, glyburide, tolbutamide, pioglitazone, rosiglitazone, acarbose, miglitol, troglitazone, tolazamide, examide, citoglipton, insulin, glyburide-metformin, glipizide-metformin, glimepiride-pioglitazone, metformin-rosiglitazone, and metformin-pioglitazone, the feature indicates whether the drug was prescribed or there was a change in the dosage. Values: “up” if the dosage was increased during the encounter, “down” if the dosage was decreased, “steady” if the dosage did not change, and “no” if the drug was not prescribed
change Indicates if there was a change in diabetic medications (either dosage or generic name). Values: “change” and “no change”
diabetesMed Indicates if there was any diabetic medication prescribed. Values: “yes” and “no”
readmitted Days to inpatient readmission. Values: “2” if the patient was readmitted in less than 30 days, “1” if the patient was readmitted in more than 30 days, and “0” for no record of readmission.

## Data Cleanup
We dropped columns that had close to 50% missing data ('weight', 'payer_code', 'medical_specialty'). Also dropped encounter id and patient number. We also excluded individual medication prescribed field and used the overall diabetesMed field. This was also done to imrpove performance because of processing limitations of the machine. We also dropped the 3 diagnoses fields but retained the number of diagnoses field.

In the process of our model design, we classify output into two classes (0 no readmission and 1 means readmitted). The output class is balanced.

## Plots
Plots are not saved separately in this repository because of file size.

## Script to run the code
Script can be found under Capstone/Capstone - Diabetes Readmission.ipynb

## Model
Models tested are limited to the ones learned so far in the program. Current models come from Sci-kit learn package. Future enhancement using more advanced models (such as RandomForest, XGBoost etc.) recommended. If run in better machine with resource capability, the SVM can also be tuned using Grid Search CV (not done here)

We used the dummy classifier with most frequent strategy as the baseline model. All fields were converted to numeric during cleanup and no furtehr encoding was required. We used Standard Scaling transformation before running our classification models.
Then compared Logistic Regression, Decision Tree, KNN Classisifier and Support Vector models. We used permutation importance to identify important features and Grid Search CV to fine tune the models. We used roc_auc scoring as the output class is balanced.

## Finding based on model evaluation and validation
Using roc_auc score in Grid Search CV we found the logistic regression with c=100 and ridge (L2) penalty to be the best model in terms of both test accuracy(0.65) and time. Since it is Logistic Regression, we can also get the probablity that a patient will likely fall into one of the two output classes.

Also, it would nice to have socio-economic data such as income which determines eating/exercise habits or access to better resources and healthcare services.

