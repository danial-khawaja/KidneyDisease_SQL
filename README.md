# Exploring Chronic Kidney Disease through Statistical Analysis


Objective:

Chronic kidney disease (CKD) is a serious medical condition that affects a significant proportion of the population. The dataset was compiled over a 2-month period in India for patients in one hospital. I will analyze the clincal data to identify trends and statistics in CKD patients. My findings can be used to improve early diagnosis and treatment of chronic kidney disease, and to develop preventive measures to reduce its incidence.

This table contains 398 rows of patients and includes information on medical attributes such as blood test levels, and comorbidities associated with chronic kidney disease. The table has two values in the classification column: "ckd" and "notckd". The target is to highlight the differences in medical attributes in relation to patients that have CKD and Non-CKD patients. This will give insight into how chronic kidney disease affects our metabolic numbers and what are the most common comorbidities that increase the progression of CKD.

Dataset:

- Link: https://www.kaggle.com/datasets/mansoordaku/ckdisease

Table Name: KidneyDisease

Column Names and their values:

id = patient id - (there are 398 total patients and values range from 0-397 and are arranged in ascending order to specify patient id)

age = age of the patient

blood_pressure = patient's blood pressure level

specific_gravity = patient's specific gravity level

albumin = patient's albumin level

sugar = patient's sugar level

red_blood_cells = values are "normal" or "abnormal". "normal" refers to the patient having red blood cells in the normal range. "abnormal" refers to the patient having red blood cells in the abnormal range

pus_cell = values are "normal" or "abnormal". "normal" refers to the patient having red blood cells in the normal range. "abnormal" refers to the patient having red blood cells in the abnormal range

pus_cell_clumps = values are "present" or "notpresent"

bacteria = values are "present" or "notpresent". "present" refers to patient having bacteria in the kidneys. "notpresent" refers to patient not having bacteria in the kidneys

blood_glucose_random = patient's random glucose testing level

blood_urea = measures the amount of urea nitrogen in the blood

serum_creatinine = patient’s creatinine levels

sodium = patient’s sodium level

potassium = patient’s potassium level

hemoglobin = patient’s hemoglobin level

packed_cell_volume = patient’s red blood cell mass

white_blood_cell_count = patient’s white blood cell count

red_blood_cell_count = patient’s red blood cell count

hypertension = values are "yes" or "no". "yes" refers to the patient having hypertension (high blood pressure). "no" refers to the patient not having hypertension

diabetes_mellitus = values are "yes" or "no". "yes" refers to the patient having diabetes mellitus. "no" refers to the patient not having diabetes mellitus

coronary_artery_disease = values are "yes" or "no". "yes" refers to the patient having coronary artery disease. "no" refers to the patient not having coronary artery disease

appetite = values are "good" or "bad". "good" refers to the patient having a healthy diet in relation to kidney disease. "bad" refers to the patient having an unhealthy diet in relation to kidney disease

pedal_edema = values are "yes" or "no". "yes" refers to the patient having pedal edema. "no" refers to the patient not having pedal edema

anemia = values are "yes" or "no". "yes" refers to the patient having anemia. "no" refers to the patient not having anemia

classification = refers to whether the patient has chronic kidney disease or not. Values are “ckd” or “notckd”. “ckd” refers to the patient having chronic kidney disease. “notckd” refers to the patient not having chronic kidney disease
       
_______________________________________________________________________________________________________________________________________________________________________

### SQL Queries to identify totals, averages, and percentages of CKD risk factors

--Number of patients with chronic kidney disease and without chronic kidney disease:

       SELECT classification, COUNT(*) as total_patients
       FROM KidneyDisease
       GROUP BY classification;

--Average age of patients with chronic kidney disease and without chronic kidney disease:

       SELECT classification, AVG(age) as average_age
       FROM KidneyDisease
       GROUP BY classification;
       
--Average levels of serum creatinine among patients with and without chronic kidney disease:

      SELECT classification, AVG(serum_creatinine) as average_serum_creatinine
      FROM KidneyDisease
      GROUP BY classification;
      
--Average blood pressure among patients with and without chronic kidney disease:

      SELECT classification, AVG(blood_pressure) as average_blood_pressure
      FROM KidneyDisease
      GROUP BY classification;

--Average levels of blood glucose random among patients with and without chronic kidney disease:

       SELECT classification, AVG(blood_glucose_random) as average_blood_glucose_random
       FROM KidneyDisease
       GROUP BY classification;
       
--Average levels of hemoglobin among patients with and without chronic kidney disease:

       SELECT classification, AVG(hemoglobin) as average_hemoglobin
       FROM KidneyDisease
       GROUP BY classification;       

--Average levels of blood urea among patients with and without chronic kidney disease:

       SELECT classification, AVG(blood_urea) as average_blood_urea
       FROM KidneyDisease
       GROUP BY classification;

--Average levels of sodium among patients with and without chronic kidney disease:

       SELECT classification, AVG(sodium) as average_sodium
       FROM KidneyDisease
       GROUP BY classification;

--Average levels of potassium among patients with and without chronic kidney disease:

       SELECT classification, AVG(potassium) as average_potassium
       FROM KidneyDisease
       GROUP BY classification;
       
--Count the number of patients with each comorbidity, grouped by their classification (CKD or notCKD)

       SELECT classification, 
          COUNT(CASE WHEN hypertension = 'yes' THEN 1 END) AS hypertension_count,
          COUNT(CASE WHEN diabetes_mellitus = 'yes' THEN 1 END) AS diabetes_mellitus_count,
          COUNT(CASE WHEN coronary_artery_disease = 'yes' THEN 1 END) AS coronary_artery_disease_count,
          COUNT(CASE WHEN pedal_edema = 'yes' THEN 1 END) AS pedal_edema_count,
          COUNT(CASE WHEN anemia = 'yes' THEN 1 END) AS anemia_count
       FROM KidneyDisease
       GROUP BY classification;
       
--Calculate the percentage of CKD patients grouped by each comorbidity

      SELECT 
         COUNT(CASE WHEN hypertension = 'yes' THEN 1 END) * 100.0 / COUNT(*) AS percentage_hypertension_ckd_patients,
         COUNT(CASE WHEN diabetes_mellitus = 'yes' THEN 1 END) * 100.0 / COUNT(*) AS percentage_diabetes_mellitus_ckd_patients,
         COUNT(CASE WHEN coronary_artery_disease = 'yes' THEN 1 END) * 100.0 / COUNT(*) AS percentage_coronary_artery_disease_ckd_patients,
         COUNT(CASE WHEN anemia = 'yes' THEN 1 END) * 100.0 / COUNT(*) AS percentage_anemia_ckd_patients,
         COUNT(CASE WHEN pedal_edema = 'yes' THEN 1 END) * 100.0 / COUNT(*) AS percentage_pedal_edema_ckd_patients
      FROM KidneyDisease
      WHERE classification = 'ckd';


____________________________________________________________________________________________________________________________________________________________________

# Data Report: CKD vs. Non-CKD Patients



Number of CKD Patients = 248

Number of Non-CKD Patients = 150

Average Age of CKD Patients = 54

Average Age of Non-CKD Patients = 46

Average Serum Creatinine of CKD Patients = 4.43

Average Serum Creatinine of Non-CKD Patients = 0.87

Average Blood Pressure of CKD Patients = 79

Average Blood Pressure of Non-CKD Patients = 71

Average Blood Glucose Random level of CKD Patients = 175

Average Blood Glucose Random level of Non-CKD Patients = 107

Average Hemoglobin of CKD Patients = 10.6

Average Hemoglobin of Non-CKD Patients = 15.2

Average Blood Urea of CKD Patients = 72.7

Average Blood Urea of Non-CKD Patients = 32.8

Average Sodium level of CKD Patients = 133.9

Average Sodium level of Non-CKD Patients = 141.7

Average Potassium level of CKD Patients = 4.9

Average Potassium level of CKD Patients = 4.3

Number of CKD Patients with Hypertension = 145

Percentage of CKD Patients with Hypertension = 58.5%

Number of CKD Patients with Diabetes Mellitus = 133

Percentage of CKD Patients with Diabetes Mellitus = 53.6%

Number of CKD Patients with Coronary Artery Disease = 34

Percentage of CKD Patients with Coronary Artery Disease = 13.7%

Number of CKD Patients with Anemia = 59

Percentage of CKD Patients with Anemia = 23.8%

Number of CKD Patients with Pedal Edema = 76

Percentage of CKD Patients with Pedal Edema = 30.6%



### Data Analysis:

- Patient Demographics - Out of the 398 patients, 248 were diagnosed with CKD while 150 patients did not have CKD. The average age of CKD patients was 54 years, while the average age of Non-CKD patients was 46.

- Serum Creatinine - The average serum creatinine level of patients with CKD was 4.43 mg/dL, while the average serum creatinine level of Non-CKD patients was: 0.87 mg/dL.

- Hypertension - The average blood pressure of CKD patients was 79, while the average blood pressure of Non-CKD patients was 71. 145 patients out of 248 with CKD had hypertension (58.5%).

- Diabetes Mellitus - The average blood glucose random level of CKD patients was 175, while the average Blood Glucose Random level of Non-CKD patients was 107. 133 patients out of 248 with CKD had diabetes mellitus (53.6%)

- Hemoglobin & Anemia - The average hemoglobin level of CKD patients was 10.6 g/dL, while the average hemoglobin level of Non-CKD patients was 15.2. 59 patients out of 248 with CKD had anemia (23.8%).

____________________________________________________________________________________________________________________________________________________________________

### Insights:

This data analysis has identified several important trends in the characteristics of patients with chronic kidney disease (CKD). Patients with CKD tend to be older, with a statistically significant difference of 6 years compared to those without CKD. This highlights the importance of regular monitoring of kidney function in elderly patients, especially those with known risk factors for CKD.

Additionally, patients with CKD tend to have higher levels of serum creatinine, hypertension, and diabetes mellitus, all of which are established risk factors for the development and progression of CKD. These findings underscore the importance of early detection and management of these risk factors to prevent the onset and progression of CKD.

Furthermore, the data analysis revealed that patients with CKD have lower levels of hemoglobin, packed cell volume, and red blood cell count, indicating a high prevalence of anemia. Anemia is a common complication of CKD and is associated with increased morbidity and mortality. Healthcare providers should routinely screen patients with CKD for anemia and initiate appropriate treatment to improve patient outcomes.

Finally, this analysis highlights the importance of regular monitoring of symptoms and comorbidities in patients with CKD. Pedal edema was the most commonly reported symptom, while hypertension, diabetes mellitus, and coronary artery disease were the most commonly reported comorbidities. Healthcare providers should routinely assess and manage these conditions to improve patient outcomes.

### Action Items:

Healthcare Providers

- Monitor Kidney Function: for early detection and management of risk factors for CKD in patients, especially in those with hypertension, diabetes, and cardiovascular disease

- Order Routine Blood Tests: and check blood pressure for patients to evaluate medical attributes associated with kidney function including creatinine, high blood pressure, hemoglobin, sodium & potassium levels
 
- Encourage Lifestyle Changes: including maintaining a healthy weight and diet as well as engaging in regular physical activity to reduce the risk of CKD

Researchers

- Conduct Clinical Trials: for further research to understand the complex interconnected relationships between age, hypertension, diabetes, and cardiovascular disease and their contribution to the progression of CKD
 
- Investigate Genetics: and the potential role of racial and genetic differences in the development and progression of CKD including studying unique characteristics of CKD in different racial groups and ensuring medical equality in care for all patients

- Improve Data Collection / Analysis: Clinical Data Analysts can work on standardizing protocols for data collection, using advanced statistical methods, and using electronic health records to track patient outcomes over time

Policy Makers 

- Promote Innovative Payment Models: which incentivize quality care and improve patient outcomes, such as value-based payment models

- Address Social Determinants of Health: that contribute to CKD disparities, such as poverty and lack of access to healthcare in addition to developing plans that ensure equitable access to quality care for all CKD patients, regardless of race, ethnicity, or socioeconomic status

- Launch Awareness Campaigns: to educate high-risk populations of the factors that contribute to CKD and how they can take practical steps to prevent its development

### Conclusion: 

Overall, this data analysis highlights the significant impact of the risk factors and comorbidities on the development and progression of CKD. Early detection and management of these risk factors, coupled with regular monitoring of kidney function, can help to prevent or slow down its progression. Through concerted efforts from healthcare providers, researchers, and policy makers, we can work together to improve the lives of those affected by CKD.
