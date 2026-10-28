# trials-of-triage

**Using pattern recognition to detect implicit bias in hospital triaging.**
Whether a patient is admitted or discharged, predicted from the attributes
recorded at triage, and then taken apart with Shapley values to ask which
attribute actually carried the decision.

Attributes considered: Emergency Severity Index, gender, employment status,
insurance status, race, ethnicity, age and language.

## What we found

- Patients on federally run insurance programs — Medicaid, Medicare — fared
  measurably worse than patients on private plans **at the same severity index**.
- Ethnicity weighed more heavily on treatment for patients under forty, at any
  given ESI level.
- Language, against expectation, was not a barrier.

Importance is not uniform across attributes, and the ranking is the result: a
single accuracy number would have hidden every one of these.

**Paper** · [Annals of Biomedical Science and Engineering, 2023](https://doi.org/10.29328/journal.abse.1001022)
**Presented** · 2022 Southern California Conferences for Undergraduate Research, Pepperdine University

## Method

Two halves. The classification task trains a neural network and a balanced random
forest to separate *Admitted* from *Discharged* on the attributes above. The
analysis then computes SHAP values over the fitted model to recover each
attribute's contribution to an individual decision, and aggregates those into the
findings above.

| Path | What it is |
|---|---|
| `Models/Network_Model.ipynb` | The neural classifier |
| `Models/RdataShapVal.ipynb` | SHAP attribution over the fitted model |
| `Models/Rdata_Analysis-Fixed.ipynb` | The analysis the paper reports |
| `Models/balanced_random_forest_classifier_params.conf` | Random-forest configuration |
| `Data/` | Train, validation and test splits |
| `5v_cleandf.rdata` | The cleaned record set the splits are drawn from |

## Future work

Aggregating patient records from more hospitals, to ask whether the same
demographics receive different care in different parts of the United States.
