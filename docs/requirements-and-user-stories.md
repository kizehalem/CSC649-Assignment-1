# Part B: Requirements and User Stories

## B1. Functional Requirements
- **FR1:** The system shall parse and ingest raw Continuous Glucose Monitoring (CGM) data in standard CSV or JSON formats.
- **FR2:** The system shall calculate clinical glycemic metrics including Time-in-Range (TIR %), Time-Below-Range (TBR %), and Coefficient of Variation (CV %).
- **FR3:** The system shall generate visual alerts when nocturnal hypoglycemia patterns (blood glucose < 3.9 mmol/L between 00:00 and 06:00) are detected.
- **FR4:** The system shall suggest clinical adjustments for Insulin-to-Carbohydrate Ratios (ICR) and Insulin Sensitivity Factors (ISF) based on postprandial glucose trends.
- **FR5:** The system shall display a real-time risk score for Diabetic Ketoacidosis (DKA) when persistent hyperglycemia (>13.9 mmol/L) coincides with elevated blood ketones.
- **FR6:** The system shall export clinical decision summary reports into standard PDF format for medical record archiving.

## B2. Non-Functional Requirements
- **NFR1 (Performance):** The system shall process 14 days of high-density CGM data and render calculated metrics within 3 seconds.
- **NFR2 (Security):** The system shall encrypt all stored patient health information (PHI) at rest using AES-256 encryption.
- **NFR3 (Usability):** The system interface shall allow clinicians to review and accept/reject insulin suggestions within 3 button clicks.
- **NFR4 (Reliability):** The system rule engine shall achieve 99.9% operational uptime during standard hospital operating hours.

## B3. User Stories
1. **US1:** As an endocrinologist, I want the system to flag nocturnal hypoglycemia patterns automatically, so that I can reduce basal insulin doses to protect patient safety during sleep.
   - **Linked Requirement:** FR3
   - **Acceptance Criteria:**
     1. Highlight glucose timestamps below 3.9 mmol/L occurring between 00:00 and 06:00.
     2. Display a red visual warning banner on the main clinician dashboard.
2. **US2:** As a primary care doctor, I want suggested adjustments for ICR and ISF parameters, so that I can optimize post-meal insulin dosing without manual mathematical calculations.
   - **Linked Requirement:** FR4
   - **Acceptance Criteria:**
     1. Display recommended ICR/ISF values alongside current patient settings.
     2. Provide a single-click action to accept or modify the recommended dosage.
3. **US3:** As a diabetes nurse educator, I want automated Time-in-Range (TIR) metric summaries, so that I can quickly evaluate therapy progress during follow-up visits.
   - **Linked Requirement:** FR2
   - **Acceptance Criteria:**
     1. Display target percentage breakdown (TIR, TBR, TAR) in visual charts.
     2. Generate an exportable summary report.
