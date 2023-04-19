# CKDProject_SQL
SQL queries and comments for my Kidney Disease Data Analysis Portfolio Project

Code abbreviations for medical factors: 

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



































