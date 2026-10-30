# trials-of-triage

**Which attribute actually decides whether a patient is admitted?**

Hospital triage dispositions, admitted or discharged, predicted from what is recorded at
intake, then taken apart with Shapley values to ask what carried each decision.

Attributes: Emergency Severity Index, insurance status, race, ethnicity, employment,
age, gender, language.

## Findings

- At the same severity index, patients on federally run insurance programs (Medicaid,
  Medicare) were admitted less often than patients on private plans.
- Ethnicity weighed more heavily on patients under forty, at any given severity index.
- Language, against expectation, was not a barrier.

Attribute importance is not uniform, and the ranking is the result. A single accuracy
number would have hidden every one of these.

**Paper** · [Annals of Biomedical Science and Engineering, 2023](https://doi.org/10.29328/journal.abse.1001022)
**Presented** · Southern California Conferences for Undergraduate Research, Pepperdine, 2022

## Method

Two halves. A neural classifier and a balanced random forest separate *Admitted* from
*Discharged* on the attributes above. Shapley values over the fitted model then recover
each attribute's contribution to an individual decision, and those are aggregated into
the findings.

| Path | |
|---|---|
| `Models/Network_Model.ipynb` | The neural classifier |
| `Models/RdataShapVal.ipynb` | Shapley attribution over the fitted model |
| `Models/Rdata_Analysis-Fixed.ipynb` | The analysis the paper reports |
| `Models/balanced_random_forest_classifier_params.conf` | Random-forest configuration |
| `Data/` | Train, validation and test splits |
| `5v_cleandf.rdata` | The cleaned record set the splits are drawn from |

## Future work

Aggregating records from more hospitals, to ask whether the same demographics receive
different care in different parts of the United States.
