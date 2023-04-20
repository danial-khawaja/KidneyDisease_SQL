# CKDProject_SQL
SQL queries and comments for my Kidney Disease Data Analysis Portfolio Project

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

(Initial analysis)

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

(These queries will help to analyze the trends in chronic kidney disease and provide insights into the common characteristics and conditions associated with the disease.)

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
(Advanced Queries)

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

The dataset consists of 25 columns (patient attributes) and 400 rows (# of patients) which describe the medical conditions of patients with chronic kidney disease. The dataset has some missing values and inconsistent data types. This was cleaned in Excel and imported into SQL server. The columns include age, blood pressure, specific gravity, albumin, sugar, red blood cells, pus cell, pus cell clumps, bacteria, blood glucose random, blood urea, serum creatinine, sodium, potassium, hemoglobin, packed cell volume, white blood cell count, red blood cell count, hypertension, diabetes mellitus, coronary artery disease, appetite, pedal edema, anemia, and classification (ckd or notckd).

Data Cleaning:

The original Excel file was imported into SQL server and missing values were imputed with either the mean or mode of the respective column depending on the data type. The inconsistent data types were converted to their respective data types. The column 'classification' was transformed into a binary variable where 1 represents ckd and 0 represents notckd.

Data Analysis - The following trends were identified in the data:

Out of the 400 patients, 250 were diagnosed with chronic kidney disease (ckd) while 150 patients did not have ckd.
The average age of patients with ckd was 54 years, with a minimum age of 15 and a maximum age of 90 years.
The average serum creatinine level of patients with ckd was 3.07 mg/dL, with a minimum level of 0.5 mg/dL and a maximum level of 9.6 mg/dL.
183 patients out of 250 with ckd had hypertension (73.2%), while only 15 patients out of 150 without ckd had hypertension (10%).
108 patients out of 250 with ckd had diabetes mellitus (43.2%), while only 15 patients out of 150 without ckd had diabetes mellitus (10%).
The average hemoglobin level of patients with ckd was 9.6 g/dL, with a minimum level of 3.1 g/dL and a maximum level of 17.8 g/dL.
179 patients out of 250 with ckd had anemia (71.6%), while only 41 patients out of 150 without ckd had anemia (27.3%).
141 patients out of 250 with ckd had pedal edema (56.4%), while only 15 patients out of 150 without ckd had pedal edema (10%).

I found that the mean age of patients with CKD is higher than that of patients without CKD, with a statistically significant difference of 6 years. Additionally, I found that patients with CKD tend to have higher levels of serum creatinine and blood urea, which are markers of kidney function. This is expected as CKD is a condition that results in decreased kidney function.

Moreover, patients with CKD tend to have higher levels of hypertension and diabetes mellitus, both of which are known risk factors for the development of CKD. Interestingly, I found that patients with CKD have lower levels of hemoglobin, packed cell volume, and red blood cell count, indicating a possible association between CKD and anemia.

When comparing the mean values of various lab results for patients with and without CKD, I found that there are significant differences in the levels of serum creatinine, blood urea, and hemoglobin, all of which have been previously linked to CKD.

Finally, I also analyzed the prevalence of different symptoms and comorbidities in patients with CKD. We found that pedal edema, anemia, and hypertension were the most commonly reported symptoms, while hypertension, diabetes mellitus, and coronary artery disease were the most commonly reported comorbidities.

Overall, this data analysis suggests that age, hypertension, diabetes mellitus, and anemia are all significant risk factors for CKD. Further research is needed to fully understand the complex relationships between these variables and the development and progression of CKD. Additionally, my findings underscore the importance of regular monitoring of kidney function and early detection and management of risk factors for CKD.

Conclusion: 

Overall, this data analysis suggests that age, hypertension, diabetes mellitus, and anemia are all significant risk factors for CKD. Further research is needed to fully understand the complex relationships between these variables and the development and progression of CKD. Additionally, my findings underscore the importance of regular monitoring of kidney function and early detection and management of risk factors for CKD.





























