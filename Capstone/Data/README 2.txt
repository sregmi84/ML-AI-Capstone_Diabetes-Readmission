https://www.kaggle.com/competitions/1056lab-diabetes-readmission-prediction/data

Context
This dataset is 10-years (from 1999 to 2008) of clinical care at 130 US hospitals and integrated delivery networks.

Can we forecast whether a diabetes patient will be readmitted in the future or not?

Content
The original data came from the UCI Machine Learning Repository via Kaggle datasets.

It contains 101,766 instances (patients) that are classified into three classes: 0 means no readmission, 1 means readmission in less than 30 days, and 2 means readmission in more than 30 days.

Training Data and Test Data
The training data is randomly selected 71,236 instances.
The test data is the remaining 30,530 instances.

License
The original dataset in Kaggle datasets licensed by the CC0: Public Domain.

Notice
This is a private competition in 1056Lab, a data mining laboratory at Chubu University.

References
Beata Strack, Jonathan P. DeShazo, Chris Gennings, Juan L. Olmo, Sebastian Ventura, Krzysztof J. Cios, and John N. Clore, “Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records,” BioMed Research International, vol. 2014, Article ID 781670, 11 pages, 2014.
Humberto Brandão: Diabetes 130 US hospitals for years 1999-2008 - Kaggle datasets
Diabetes 130-US hospitals for years 1999-2008 Data Set - UCI Machine Learning Repository


Files Descriptions
train.csv - the training set that includes the readmitted
test.csv - the test set that does not include the readmitted
sampleSubmission.csv - a sample submission file in the correct format.
Data Fields
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

