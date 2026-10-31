# Part B: Requirements and User Stories

## B1. Functional Requirements

| Req ID | Requirement Description ("The system shall...") | Testability Method |
| :--- | :--- | :--- |
| **FR1** | The system shall parse standardized CGM export files (CSV/JSON) and extract 14-day AGP metrics including Time-in-Range (TIR 3.9–10.0 mmol/L), Time-Below-Range (TBR < 3.9 mmol/L), and Coefficient of Variation (CV%). | Automated unit test with sample CGM datasets containing known AGP values. |
| **FR2** | The system shall trigger a high-priority nocturnal hypoglycemia alert whenever two or more readings < 3.9 mmol/L occur between 00:00 and 06:00 within a 14-day window. | Integration testing with simulated midnight glucose drops. |
| **FR3** | The system shall calculate and suggest Insulin-to-Carbohydrate Ratio (ICR) adjustments when postprandial glucose excursions exceed 10.0 mmol/L for 3 consecutive days at a specific mealtime. | Boundary value analysis comparing calculated suggestions against expert rule baseline. |
| **FR4** | The system shall display a prominent visual warning indicator on the clinical dashboard whenever patient Glucose Variability (CV%) exceeds 36%. | UI visual verification test under high CV% input conditions. |
| **FR5** | The system shall generate evidence-based Insulin Sensitivity Factor (ISF) correction advice when persistent post-correction hyperglycemia is detected. | Rule engine verification test using post-correction glucose logs. |
| **FR6** | The system shall log all clinician interactions (Accept, Modify, Reject) with associated justification reason codes into an immutable clinical audit table. | Database audit trail inspection following simulated clinician decision entry. |

## B2. Non-Functional Requirements

| NFR ID | NFR Type | Measurable Standard / Condition | Verification Method |
| :--- | :--- | :--- | :--- |
| **NFR1** | **Performance** | The system shall parse a 14-day CGM dataset (2,016 data points) and render the summary screen within 2.0 seconds of patient record selection. | Automated performance benchmarking tool. |
| **NFR2** | **Usability** | The clinical interface shall allow clinicians to review AGP summary alerts and finalize insulin parameter changes in 3 or fewer user clicks. | Usability testing with 5 clinicians measuring click-paths. |
| **NFR3** | **Security & Privacy** | The system shall encrypt all patient data at rest using AES-256 and in transit using TLS 1.3 protocol, complying with healthcare data protection standards. | Penetration testing and security audit verification. |
| **NFR4** | **Reliability** | The decision engine rule evaluator shall maintain 99.9% service availability during scheduled operational clinic hours (08:00–18:00, Mon–Fri). | System uptime telemetry monitoring. |

## B3. User Stories & Acceptance Criteria

| ID | User Story Description | Linked Req | Testable Acceptance Criteria |
| :--- | :--- | :--- | :--- |
| **US1** | **As an** Endocrinologist,<br>**I want** an automated summary of CGM Time-in-Range and glucose variability metrics,<br>**So that** I can rapidly identify unstable T1DM patients during consultations. | FR1, FR4 | **1.** Selecting a patient displays TIR, TBR, TAR, and CV% metrics formatted according to international AGP presentation guidelines within 2 seconds.<br>**2.** If TBR > 4% or CV > 36%, a red alert badge is rendered on the header navigation bar. |
| **US2** | **As a** Diabetes Nurse Educator,<br>**I want** the system to recommend Insulin-to-Carbohydrate Ratio (ICR) adjustments based on postprandial glucose spikes,<br>**So that** I can guide patients on dietary insulin matching. | FR3 | **1.** The decision module displays current vs. proposed ICR values alongside a breakdown of mealtime glucose trends.<br>**2.** The system forces a mandatory clinician action selection (Accept, Modify, or Override) with reason entry before saving. |
| **US3** | **As an** Outpatient Clinician,<br>**I want** automated alerts for recurring nocturnal hypoglycemia,<br>**So that** I can reduce bedtime basal rates and prevent night-time hypoglycemic events. | FR2, FR5 | **1.** The system highlights any 14-day log containing ≥2 nocturnal low readings (< 3.9 mmol/L between 00:00–06:00).<br>**2.** Clicking the alert opens an expanded overnight glucose plot with a specific basal rate reduction recommendation (e.g., reduce 01:00–04:00 basal by 10%).
