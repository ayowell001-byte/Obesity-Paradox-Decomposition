# Causal Decomposition of the Obesity Paradox in ICU Admissions

[![Status](https://img.shields.io/badge/Status-Complete-success)]()
[![Course](https://img.shields.io/badge/Course-STATS%20C160%20(UCLA)-blue)]()
[![Methodology](https://img.shields.io/badge/Methodology-Causal%20Inference%20%7C%20AIPW-orange)]()

A causal inference project investigating the **"Obesity Paradox"**. The observed survival advantage of overweight patients in Intensive Care Units (ICUs) using electronic health record data from the MIMIC-IV clinical registry. 

By **Asher Yowell** as the Final Project for STATS C160 (Winter 2026) at the University of California, Los Angeles.

---

## Summary
Understanding the true drivers of mortality risk versus spurious confounding is important for accurate risk stratification and pricing. Obesity is a well documented risk factor for chronic conditions in the general population, ICU studies frequently exhibit a paradoxical survival benefit for overweight individuals ($25 \le \text{BMI} < 35$). 

This project goes beyond standard observational association by deploying **Structural Causal Models (SCMs)** and **Double-Robust Estimation** to decompose the Total Variation (TV) into 3 different pathways:
1. **Direct Variation ($\delta$-DE):** The isolated biological effect of BMI on 30-day mortality.
2. **Indirect Variation ($\delta$-IE):** Mediation because of acute physiological ICU complications ($W$).
3. **Spurious/Confounded Variation ($\delta$-SE):** Confounding bias driven by pre-admission baseline characteristics ($Z$) such as age, sex, and comorbidity indices.

---

## Key Technical Highlights

* **Structural Causal Models (SCMs) & DAGs:** Constructed a Directed Acyclic Graph (DAG) for backdoor admissibility and conditional independence assumptions.
* **Augmented Inverse Propensity Weighting (AIPW):** Implemented double estimators by combining propensity score modeling ($\pi(z))$ and outcome regression ($\mu(z)$) to handle the high dimensional covariate spaces and missing data structures without incurring specification bias.
* **Mediation and Heterogeneity Analysis:** Decomposed physiological pathways and evaluated effect heterogeneity across age brackets and Charlson Comorbidity Index.
* **Data Handling & Limitations Analysis:** Addressed real-world data challenges such as substantial missingness and selection bias considerations.

---

## Key Findings

* **Survival Advantage Confirmed, but Nuanced:** The total variation analysis confirmed a small net survival disadvantage. The decomposition revealed that the *Direct Effect* accounts for the primary survival variation, while indirect physiological pathways and spurious confounding nearly offset each other.
* **Mediator Counterbalance:** Certain acute conditions exhibited higher frequencies in normal weight patients, counteracting expected survival trajectories and dampening the overall negative direct effect.
* **Risk Stratification Implications:** The findings indicate that standard clinical risk models must account for causal mediation and selection biases rather than taking observational risk ratios at face value.

