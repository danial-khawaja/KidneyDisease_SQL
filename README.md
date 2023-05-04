# Chronic Kidney Disease Data Analysis


Introduction:

Chronic kidney disease is a serious medical condition that affects a significant proportion of the population. Through my data analysis and usage of statistical techniques, I will investigate the medical data to identify trends, and patterns in CKD patients. My findings can be used to improve early diagnosis and treatment of chronic kidney disease, and to develop preventive measures to reduce its incidence.

- Dataset link: https://www.kaggle.com/datasets/mansoordaku/ckdisease

Code abbreviations for patient attributes: 

age = age

bp = blood pressure

sg = specific gravity

al = albumin

su = sugar

rbc = red blood cells

pc = pus cell

pcc = pus cell clumps

ba = bacteria

bgr = blood glucose random

bu = blood urea

sc = serum creatinine

sod = sodium

pot = potassium

hemo = hemoglobin

pcv = packed cell volume

wc = white blood cell count

rc = red blood cell count

htn = hypertension

dm = diabetes mellitus

cad = coronary artery disease

appet = appetite

pe = pedal edema

ane = anemia

_______________________________________________________________________________________________________________________________________________________________________

(Initial analysis of patient attributes)

--Count the number of patients with hypertension:

       SELECT COUNT(*) 
       FROM Kidney_Disease 
       WHERE htn = 'yes';

--Calculate the average serum creatinine levels for patients with anemia:

       SELECT AVG(sc)
       FROM Kidney_Disease
       WHERE ane = 'yes';

--Count the number of patients with albumin levels greater than 3:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE al > 3;

--Calculate the average age of patients with a blood glucose random value greater than 140:

       SELECT AVG(age)
       FROM Kidney_Disease
       WHERE bgr > 140;

--Count the number of patients with diabetes mellitus who have pedal edema:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE dm = 'yes'
       AND pe = 'yes';

--Calculate the average hemoglobin levels of patients with hypertension and anemia:

       SELECT AVG(hemo)
       FROM Kidney_Disease
       WHERE htn = 'yes'
       AND ane = 'yes';

--Count the number of patients with a packed cell volume of less than 30:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE pcv < 30;

--Calculate the average white blood cell count for patients with pus cell clumps:

       SELECT AVG(wc)
       FROM Kidney_Disease
       WHERE pcc = 'present';

_______________________________________________________________________________________________________________________________________________________________________

(CKD Analysis - These queries will help to analyze the trends in chronic kidney disease and provide insights into the common characteristics and conditions associated with the disease.)

--Count the number of patients with chronic kidney disease:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE classification = 'ckd';

--Calculate the average age of patients with chronic kidney disease:

       SELECT AVG(age)
       FROM Kidney_Disease
       WHERE classification = 'ckd';

--Calculate the average serum creatinine level of patients with chronic kidney disease:

       SELECT AVG(sc)
       FROM Kidney_Disease
       WHERE classification = 'ckd';

--Count the number of patients with hypertension and chronic kidney disease:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE classification = 'ckd' AND htn = 'yes';

--Count the number of patients with diabetes mellitus and chronic kidney disease:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE classification = 'ckd' AND dm = 'yes';

--Calculate the average hemoglobin level of patients with chronic kidney disease:

       SELECT AVG(hemo)
       FROM Kidney_Disease
       WHERE classification = 'ckd';

--Count the number of patients with anemia and chronic kidney disease:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE classification = 'ckd' AND ane = 'yes';

--Count the number of patients with pedal edema and chronic kidney disease:

       SELECT COUNT(*)
       FROM Kidney_Disease
       WHERE classification = 'ckd' AND pe = 'yes';

_______________________________________________________________________________________________________________________________________________________________________
(Advanced Queries for Statistical Analysis)

--Number of patients with chronic kidney disease and without chronic kidney disease:

       SELECT classification, COUNT(*) as total_patients
       FROM Kidney_Disease
       GROUP BY classification;

--Average age of patients with chronic kidney disease and without chronic kidney disease:

       SELECT classification, AVG(age) as avg_age
       FROM Kidney_Disease
       GROUP BY classification;

--Proportion of patients with hypertension among those with and without chronic kidney disease:

       SELECT classification, COUNT(*) as total_patients,
              ROUND(AVG(CASE WHEN htn = 'yes' THEN 1 ELSE 0 END)*100, 2) AS proportion_with_htn 
       FROM Kidney_Disease
       GROUP BY classification;

--Proportion of patients with diabetes mellitus among those with and without chronic kidney disease:

       SELECT classification, COUNT(*) as total_patients,
              ROUND(AVG(CASE WHEN dm = 'yes' THEN 1 ELSE 0 END)*100, 2) AS proportion_with_dm  
       FROM Kidney_Disease
       GROUP BY classification;

--Average levels of blood glucose random among patients with and without chronic kidney disease:

       SELECT classification, AVG(bgr) as avg_bgr
       FROM Kidney_Disease
       GROUP BY classification;

--Average levels of blood urea among patients with and without chronic kidney disease:

       SELECT classification, AVG(bu) as avg_bu
       FROM Kidney_Disease
       GROUP BY classification;

--Average levels of serum creatinine among patients with and without chronic kidney disease:

       SELECT classification, AVG(sc) as avg_sc
       FROM Kidney_Disease
       GROUP BY classification;

--Average levels of sodium among patients with and without chronic kidney disease:

       SELECT classification, AVG(sod) as avg_sod
       FROM Kidney_Disease
       GROUP BY classification;

--Average levels of potassium among patients with and without chronic kidney disease:

       SELECT classification, AVG(pot) as avg_pot
       FROM Kidney_Disease
       GROUP BY classification;

--Average levels of hemoglobin among patients with and without chronic kidney disease:

       SELECT classification, AVG(hemo) as avg_hemo
       FROM Kidney_Disease
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


























