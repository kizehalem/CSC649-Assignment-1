# Part A: Problem Formulation

## A1. Problem Statement
Managing Type 1 Diabetes Mellitus (T1DM) requires complex clinical decisions regarding multi-daily insulin dosing, basal rates, and carbohydrate ratios. Existing clinical software and Electronic Health Records (EHRs) display raw Continuous Glucose Monitoring (CGM) data without automated pattern recognition. Consequently, clinicians struggle during brief consultations to spot critical trends like nocturnal hypoglycemia or extreme glycemic variability, leading to delayed dosage adjustments and increased risks of severe hypoglycemia or Diabetic Ketoacidosis (DKA). This project adds a Clinical Decision Support System (CDSS) extension to clinic EHRs that analyzes CGM metrics to deliver real-time insulin dosage adjustments and early risk warnings at the point of care.

## A2. Users & Scope

### Primary Users & Stakeholders
- **Endocrinologists & General Practitioners:** Primary decision-makers adjusting insulin regimens during consultations.
- **Diabetes Nurse Educators:** Review continuous monitoring trends and track patient compliance.
- **T1DM Patients:** Direct beneficiaries receiving safer, personalized therapy adjustments.

### Project Scope
- **In-Scope:** CGM data ingestion (CSV/JSON), clinical metric calculations (Time-in-Range, CV%), rule-based insulin adjustment suggestions (ICR, ISF, basal rates), and DKA/hypoglycemia visual risk flags.
- **Out-of-Scope:** Direct hardware control of automated insulin pumps, closed-loop algorithm development, and patient-facing mobile apps.
