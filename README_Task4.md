# Task 4: Risk Logic

This directory contains the implementation for **Task 4: Risk Logic** of the Maternal Health Tracker project.

## Implementation Details
The `Task4_Risk_Logic.ipynb` notebook implements the core medical logic used to dynamically score each patient's pregnancy risk.

The primary function `assess_risk(row)` consumes a dictionary mapping of a single patient's physical records and strictly checks them against the provided clinician thresholds:
1. **Pregnancy Number**: High Risk (>= 5 pregnancies)
2. **Blood Pressure**:
   - Low Risk: Below 90 / 60
   - Normal: 90-119 / 60-79
   - High Risk: 130+ / 90+
   - Severe High Risk: 160+ / 110+
3. **Blood Glucose (Fasting)**:
   - Low: Below 3.9
   - Normal: 3.9 to 5.0
   - High Risk (Gestational diabetes): 5.1 to 6.9
   - Severe (Overt diabetes): 7.0+
4. **Haemoglobin**:
   - Severe Anemia: Below 7.0
   - Moderate Anemia (High Risk): 7.0 to 9.9
   - Normal: 10 to 13
   - Elevated Risk: 13+
5. **Antenatal Visits**:
   - Inadequate: Under 4
   - Suboptimal: 4 to 7
   - Normal: 8 to 14
   - High Risk: 15+

The aggregated result is seamlessly cast into a `Low`, `Medium`, or `High` risk classification, and returned as a tuple alongside the math components.

## Usage
The `assess_risk(row)` function relies solely on native Python mechanisms without enforcing Pandas requirements within its own signature. This standalone format natively interacts with the dictionaries fetched row-by-row during loop evaluations. It can act as a central validation unit to be imported into the Patient Classes logic.
