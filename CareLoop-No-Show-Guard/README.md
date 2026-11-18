# CareLoop Clinics — No-Show Guard

**Project:** Appointment No-Show Prediction and Analysis  
**Repository:** [https://github.com/kharshithkumar99/MyFirstProject.git]

## 1. Project Overview

CareLoop Clinics — No-Show Guard is a data analytics and machine-learning project designed to analyse and predict patient appointment no-shows.

The project uses appointment records, clinic information and patient follow-up notes to identify factors associated with missed appointments. It combines Python, SQL, machine learning and Generative AI to help clinics improve appointment attendance.

## 2. Project Objectives

- Clean and validate appointment data.
- Analyse clinic-wise and monthly no-show trends using SQL.
- Build machine-learning models to predict appointment no-shows.
- Analyse patient follow-up notes using Gemini API.
- Recommend practical actions to reduce missed appointments.

## 3. Implementation and Results

### Part 1 — Data Ingestion and Cleaning

- Original appointment records: 1,020.
- Rejected invalid records: 32.
- Final cleaned appointment records: 990.
- Removed 20 duplicate records.
- Handled missing values and outliers.
- Enriched clinic information using weather data.

### Part 2 — SQL Analysis

- Analysed 990 appointments across 8 clinics.
- Overall no-show rate: 22.02%.
- Highest clinic no-show rate: 33.3% at Gomti Nagar Care Point.
- The 31+ day booking lead-time group had a 60.5% no-show rate.
- Used JOIN, GROUP BY, HAVING, CTEs, window functions, RANK and LAG.

### Part 3 — Machine Learning

Models developed:
- Logistic Regression
- Decision Tree
- Random Forest
- Tuned Random Forest

**Selected model:** Logistic Regression.

- Cross-validation ROC-AUC: 0.774.
- Classification threshold: 0.35.
- Test ROC-AUC: 0.789.
- Test accuracy: 0.788.
- Test precision: 0.571.
- Test recall: 0.571.

Logistic Regression was selected because it achieved the highest cross-validation ROC-AUC among the evaluated models.

### Part 4 — Generative AI Analysis

- Used Gemini API to analyse patient follow-up notes.
- Processed the first 10 notes.
- Successfully validated 9 nonblank notes.
- Skipped 1 blank note without making an API call.
- Compared a simple prompt (V1) against a CRAFT-based prompt (V2).
- Used Pydantic for response validation.
- Total Gemini API calls: 14 out of the permitted 25.

## 4. Business Recommendation

Clinics should prioritise appointments with longer booking lead times because the 31+ day group showed a 60.5% no-show rate. The selected Logistic Regression model achieved a cross-validation ROC-AUC of 0.774 and uses a 0.35 threshold to flag potentially missed appointments. Clinics can use these flags to prioritise reminder calls and investigate barriers such as transport difficulties, forgotten reminders and scheduling conflicts. The project analysed 990 cleaned appointments and 10 follow-up notes, with an overall no-show rate of 22.02%. These findings should be tested through a controlled operational trial before wider deployment.

## 5. Model Selection

Logistic Regression was selected based on its cross-validation ROC-AUC of 0.774, the highest among the evaluated models.

A threshold of 0.35 was selected to improve recall and identify more potentially missed appointments. The threshold reflects the operational trade-off between missed high-risk appointments and the additional effort of reminder calls.

## 6. Limitations

1. Only 10 follow-up notes were analysed, so the findings may not represent the complete patient population.
2. Data cleaning and outlier statistics were calculated before the train/test split, which may introduce data leakage.
3. The random train/test split may place appointments belonging to the same patient in both sets, potentially affecting the evaluation.

## 7. Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- MySQL
- Google Gemini API
- Pydantic
- Open-Meteo API
- Google Colab
- GitHub

## 8. Project Files

| File | Description |
|---|---|
| `data/appointments.csv` | Original appointment dataset |
| `data/clinics.csv` | Original clinic dataset |
| `data/followup_notes.csv` | Original patient follow-up notes |
| `01_ingest_clean.ipynb` | Data validation and cleaning |
| `02_queries.sql` | SQL analysis queries |
| `03_model.ipynb` | Machine-learning models and evaluation |
| `04_genai.ipynb` | Gemini API analysis, Pydantic validation, prompt comparison, and Part 4 analysis |
| `appointments_clean.csv` | Cleaned appointment data |
| `clinics_enriched.csv` | Clinic data enriched with weather |
| `rejected_rows.json` | Rejected records |
| `load_data.sql` | SQL table creation and data loading |
| `test_risk_scores.csv` | Test-set risk predictions |
| `notes_analysed.csv` | Gemini analysis of follow-up notes |
| `notes_appointments_merged.csv` | Merged note and appointment data |
| `root_cause_reminder_crosstab.csv` | Root-cause and reminder analysis |


## 9. API Security

The Gemini API key is entered at runtime and is not included in this repository.

## 10. Conclusion

This project demonstrates how data cleaning, SQL analytics, machine learning and Generative AI can be combined to understand and predict appointment no-shows. The results provide a starting point for clinics to prioritise follow-up efforts and improve appointment attendance.
