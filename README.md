# Chronic Kidney Disease Data Analysis


Introduction:

Chronic kidney disease is a serious medical condition that affects a significant proportion of the population. Through my data analysis and usage of statistical techniques, I will investigate the medical data to identify trends, and patterns in CKD patients. My findings can be used to improve early diagnosis and treatment of chronic kidney disease, and to develop preventive measures to reduce its incidence.

- Dataset link: https://www.kaggle.com/datasets/mansoordaku/ckdisease

Table Name: KidneyDisease

Column Names and their values:

id = patient id - (there are 400 total patients and values range from 0-399 and are arranged in ascending order to specify patient id)

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

blood _urea = measures the amount of urea nitrogen in the blood

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

____________________________________________________________________________________________________________________________________________________________________

(CKD Analysis - These queries will help to analyze the trends in chronic kidney disease and provide insights into the common characteristics and conditions associated with the disease.)

1. Count the number of patients who have chronic kidney disease:

              SELECT COUNT(*) AS "Number of Patients with CKD" 
              FROM KidneyDisease
              WHERE classification = 'ckd';

2. Count the number of patients who do not have chronic kidney disease:

              SELECT COUNT(*) AS "Number of Patients without CKD" 
              FROM KidneyDisease
              WHERE classification = 'notckd';

3. Calculate the average age of patients with chronic kidney disease:

              SELECT AVG(age) AS "Average Age of Patients with CKD" 
              FROM KidneyDisease
              WHERE classification = 'ckd';

4. Calculate the average age of patients without chronic kidney disease:

              SELECT AVG(age) AS "Average Age of Patients without CKD"
              FROM KidneyDisease
              WHERE classification = 'notckd';

5. Calculate the average blood pressure of patients with chronic kidney disease:

              SELECT AVG(blood_pressure) AS "Average Blood Pressure of Patients with CKD"
              FROM KidneyDisease
              WHERE classification = 'ckd';

6. Calculate the average blood pressure of patients without chronic kidney disease:

              SELECT AVG(blood_pressure) AS "Average Blood Pressure of Patients without CKD"
              FROM KidneyDisease
              WHERE classification = 'notckd';

7. Calculate the average serum creatinine level of patients with chronic kidney disease:

              SELECT AVG(serum_creatinine) AS "Average Serum Creatinine of Patients with CKD"
              FROM KidneyDisease
              WHERE classification = 'ckd';

8. Calculate the average serum creatinine level of patients without chronic kidney disease:

              SELECT AVG(serum_creatinine) AS "Average Serum Creatinine of Patients without CKD"
              FROM KidneyDisease
              WHERE classification = 'notckd';
             
9. Calculate the average hemoglobin level of patients with chronic kidney disease:

              SELECT AVG(hemoglobin) AS "Average Hemoglobin of Patients with CKD"
              FROM KidneyDisease
              WHERE classification = 'ckd';

10. Calculate the average hemoglobin level of patients without chronic kidney disease:

              SELECT AVG(hemoglobin) AS "Average Hemoglobin of Patients without CKD"
              FROM KidneyDisease
              WHERE classification = 'notckd';

11. Calculate the average blood urea level of patients with chronic kidney disease:

              SELECT AVG(blood_urea) AS "Average Blood Urea of Patients with CKD"
              FROM KidneyDisease
              WHERE classification = 'ckd';

12. Calculate the average blood urea level of patients without chronic kidney disease:

              SELECT AVG(blood_urea) AS "Average Blood Urea of Patients without CKD"
              FROM KidneyDisease
              WHERE classification = 'notckd';

13. Calculate the average white blood cell count of patients with chronic kidney disease:

              SELECT AVG(white_blood_cell_count) AS "Average White Blood Cell Count of Patients with CKD"
              FROM KidneyDisease
              WHERE classification = 'ckd';

14. Calculate the average white blood cell count of patients without chronic kidney disease:

              SELECT AVG(white_blood_cell_count) AS "Average White Blood Cell Count of Patients without CKD"
              FROM KidneyDisease
              WHERE classification = 'notckd';

15. Calculate the average red blood cell count of patients with chronic kidney disease:

              SELECT AVG(red_blood_cell_count) AS "Average Red Blood Cell Count of Patients with CKD"
              FROM KidneyDisease
              WHERE classification = 'ckd';

16. Calculate the average red blood cell count of patients without chronic kidney disease:
 
              SELECT AVG(red_blood_cell_count) AS "Average Red Blood Cell Count of Patients without CKD"
              FROM KidneyDisease
              WHERE classification = 'notckd';

17. Count the number of patients with hypertension who have chronic kidney disease:

              SELECT COUNT(*) AS "Number of Patients with CKD who have Hypertension"
              FROM KidneyDisease
              WHERE classification = 'ckd' AND hypertension = 'yes';

18. Calculate the percentage of patients with hypertension and chronic kidney disease:

              SELECT COUNT(*) * 100.0 / (SELECT COUNT(*) FROM KidneyDisease WHERE classification = 'ckd') 
              AS percentage_hypertension_ckd_patients
              FROM KidneyDisease
              WHERE hypertension = 'yes' AND classification = 'ckd';

19. Count the number of patients with diabetes mellitus who have chronic kidney disease:

              SELECT COUNT(*) AS "Number of Patients with CKD who have Diabetes Mellitus"
              FROM KidneyDisease
              WHERE classification = 'ckd' AND diabetes_mellitus = 'yes';

20. Calculate the percentage of patients with diabetes mellitus and chronic kidney disease:

              SELECT COUNT(*) * 100.0 / (SELECT COUNT(*) FROM KidneyDisease WHERE classification = 'ckd') 
              AS percentage_diabets_mellitus_ckd_patients
              FROM KidneyDisease
              WHERE diabetes_mellitus = 'yes' AND classification = 'ckd';

21. Count the number of patients with anemia who have chronic kidney disease:

              SELECT COUNT(*) AS "Number of Patients with CKD who have Anemia"
              FROM KidneyDisease
              WHERE classification = 'ckd' AND anemia = 'yes';

22. Calculate the percentage of patients with anemia and chronic kidney disease:

              SELECT COUNT(*) * 100.0 / (SELECT COUNT(*) FROM KidneyDisease WHERE classification = 'ckd') 
              AS percentage_anemia_ckd_patients
              FROM KidneyDisease
              WHERE anemia = 'yes' AND classification = 'ckd';

23. Count the number of patients with pedal edema who have chronic kidney disease:

              SELECT COUNT(*) AS "Number of Patients with CKD who have Pedal Edema"
              FROM KidneyDisease
              WHERE classification = 'ckd' AND pedal_edema = 'yes';

24. Calculate the percentage of patients with pedal edema and chronic kidney disease:

              SELECT COUNT(*) * 100.0 / (SELECT COUNT(*) FROM KidneyDisease WHERE classification = 'ckd') 
              AS percentage_pedal_edema_ckd_patients
              FROM KidneyDisease
              WHERE pedal_edema = 'yes' AND classification = 'ckd';
       
_______________________________________________________________________________________________________________________________________________________________________
       
       
(GROUP BY Queries for CKD Table Views)


--Number of patients with chronic kidney disease and without chronic kidney disease:

       SELECT classification, COUNT(*) as total_patients
       FROM KidneyDisease
       GROUP BY classification;

--Average age of patients with chronic kidney disease and without chronic kidney disease:

       SELECT classification, AVG(age) as average_age
       FROM KidneyDisease
       GROUP BY classification;

--Proportion of patients with hypertension among those with and without chronic kidney disease:

       SELECT classification, COUNT(*) as total_patients,
              ROUND(AVG(CASE WHEN hypertension = 'yes' THEN 1 ELSE 0 END)*100, 2) AS proportion_with_hypertension 
       FROM KidneyDisease
       GROUP BY classification;

--Proportion of patients with diabetes mellitus among those with and without chronic kidney disease:

       SELECT classification, COUNT(*) as total_patients,
              ROUND(AVG(CASE WHEN diabetes_mellitus = 'yes' THEN 1 ELSE 0 END)*100, 2) AS proportion_with_diabetes_mellitus  
       FROM KidneyDisease
       GROUP BY classification;

--Average levels of blood glucose random among patients with and without chronic kidney disease:

       SELECT classification, AVG(blood_glucose_random) as average_blood_glucose_random
       FROM KidneyDisease
       GROUP BY classification;

--Average levels of blood urea among patients with and without chronic kidney disease:

       SELECT classification, AVG(blood_urea) as average_blood_urea
       FROM KidneyDisease
       GROUP BY classification;

--Average levels of serum creatinine among patients with and without chronic kidney disease:

       SELECT classification, AVG(serum_creatinine) as average_serum_creatinine
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

--Average levels of hemoglobin among patients with and without chronic kidney disease:

       SELECT classification, AVG(hemoglobin) as average_hemoglobin
       FROM KidneyDisease
       GROUP BY classification;

____________________________________________________________________________________________________________________________________________________________________

Dataset Report: Summary & Insights


Data Exploration:

The dataset consists of 25 columns (patient attributes) and 400 rows (# of patients) which describe the medical conditions of patients with chronic kidney disease. The columns include age, blood pressure, specific gravity, albumin, sugar, red blood cells, pus cell, pus cell clumps, bacteria, blood glucose random, blood urea, serum creatinine, sodium, potassium, hemoglobin, packed cell volume, white blood cell count, red blood cell count, hypertension, diabetes mellitus, coronary artery disease, appetite, pedal edema, anemia, and classification (ckd or notckd).

Data Cleaning:

The original Excel file was imported into SQL server and missing values were allowed to remain NULL in order to maintain the accuracy of the statistics from this specific clinical dataset. The inconsistent data types were converted to their respective data types. The column 'classification' was transformed into a binary variable (bit) where 1 represents ckd and 0 represents notckd.

Data Analysis - The following trends were identified in the data:

Patient Demographics: Out of the 400 patients, 250 were diagnosed with chronic kidney disease (ckd) while 150 patients did not have ckd. The average age of patients with CKD was 54 years, with a minimum age of 2 and a maximum age of 90 years.

Serum Creatinine: The average serum creatinine level of patients with CKD was 3.07 mg/dL, with a minimum level of 0.5 mg/dL and a maximum level of 9.6 mg/dL.

Hypertension: 183 patients out of 250 with CKD had hypertension (73.2%), while only 15 patients out of 150 without CKD had hypertension (10%).

Diabetes Mellitus: 108 patients out of 250 with CKD had diabetes mellitus (43.2%), while only 15 patients out of 150 without CKD had diabetes mellitus (10%).

Hemoglobin & Anemia: The average hemoglobin level of patients with CKD was 9.6 g/dL, with a minimum level of 3.1 g/dL and a maximum level of 17.8 g/dL. 179 patients out of 250 with ckd had anemia (71.6%), while only 41 patients out of 150 without ckd had anemia (27.3%).

Pedal Edema: 141 patients out of 250 with ckd had pedal edema (56.4%), while only 15 patients out of 150 without ckd had pedal edema (10%).

Insights:

This data analysis has identified several important trends in the characteristics of patients with chronic kidney disease (CKD). Patients with CKD tend to be older, with a statistically significant difference of 6 years compared to those without CKD. This highlights the importance of regular monitoring of kidney function in elderly patients, especially those with known risk factors for CKD.

Additionally, patients with CKD tend to have higher levels of serum creatinine, hypertension, and diabetes mellitus, all of which are established risk factors for the development and progression of CKD. These findings underscore the importance of early detection and management of these risk factors to prevent the onset and progression of CKD.

Furthermore, the data analysis revealed that patients with CKD have lower levels of hemoglobin, packed cell volume, and red blood cell count, indicating a high prevalence of anemia. Anemia is a common complication of CKD and is associated with increased morbidity and mortality. Healthcare providers should routinely screen patients with CKD for anemia and initiate appropriate treatment to improve patient outcomes.

Finally, this analysis highlights the importance of regular monitoring of symptoms and comorbidities in patients with CKD. Pedal edema was the most commonly reported symptom, while hypertension, diabetes mellitus, and coronary artery disease were the most commonly reported comorbidities. Healthcare providers should routinely assess and manage these conditions to improve patient outcomes.

Action Items:

Healthcare Providers: Regular monitoring of kidney function and early detection and management of risk factors for CKD in patients, especially in those with hypertension and diabetes mellitus.
Awareness and management of anemia in CKD patients, which is associated with lower levels of hemoglobin, packed cell volume, and red blood cell count.
Encourage lifestyle changes, such as reducing salt and sugar intake, maintaining a healthy weight, and engaging in regular physical activity to reduce the risk of CKD.

Researchers: Further research to understand the complex relationships between age, hypertension, diabetes mellitus, and anemia and their contribution to the development and progression of CKD.
Conduct studies to evaluate the effectiveness of different interventions in managing anemia in CKD patients.
Investigate the potential of biomarkers, such as serum creatinine and blood urea, in predicting and monitoring CKD.

Policy Makers: Develop policies and guidelines to improve the prevention, detection, and management of CKD.
Increase access to healthcare services and resources, especially for underserved communities who are at a higher risk of CKD.
Encourage education and awareness campaigns to increase knowledge and understanding of the risk factors and prevention of CKD.

Conclusion: 

Overall, this data analysis highlights the significant impact of age, hypertension, diabetes mellitus, and anemia on the development and progression of CKD. Early detection and management of these risk factors, coupled with regular monitoring of kidney function, can help to prevent or slow down the progression of CKD. Through concerted efforts from healthcare providers, researchers, and policy makers, we can work together to improve the lives of those affected by CKD.


























