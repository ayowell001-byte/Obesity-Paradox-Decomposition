# Causal Decomposition of the Obesity Paradox in ICU Admissions

[![Status](https://img.shields.io/badge/Status-Complete-success)]()
[![Course](https://img.shields.io/badge/Course-STATS%20C160%20(UCLA)-blue)]()
[![Methodology](https://img.shields.io/badge/Methodology-Causal%20Inference%20%7C%20AIPW-orange)]()

An advanced causal inference project investigating the counterintuitive **"Obesity Paradox"**—the observed survival advantage of overweight patients in Intensive Care Units (ICUs)—using electronic health record data from the MIMIC-IV clinical registry. 

By **Asher Yowell** as the Final Project for STATS C160 (Winter 2026) at the University of California, Los Angele.

---

## Executive Summary & Actuarial Relevance
In risk management, actuarial science, and critical care epidemiology, understanding the true drivers of mortality risk versus spurious confounding is paramount for accurate risk stratification and pricing. While obesity is a well-documented risk factor for chronic conditions in the general population, retrospective ICU studies frequently exhibit a paradoxical survival benefit for overweight individuals ($25 \le \text{BMI} < 35$). 

This project goes beyond standard observational association by deploying **Structural Causal Models (SCMs)** and **Double-Robust Estimation** to decompose Total Variation (TV) into distinct pathways:
1. **Direct Variation ($\delta$-DE):** The isolated biological effect of BMI on 30-day mortality.
2. **Indirect Variation ($\delta$-IE):** Mediation through acute physiological ICU complications ($W$).
3. **Spurious/Confounded Variation ($\delta$-SE):** Confounding bias driven by pre-admission baseline characteristics ($Z$) such as age, sex, and comorbidity indices.

---

## Key Methodological & Technical Highlights

* **Structural Causal Models (SCMs) & DAGs:** Constructed a Directed Acyclic Graph (DAG) establishing backdoor admissibility and conditional independence assumptions (Sequential Ignorability for mediation).
* **Augmented Inverse Propensity Weighting (AIPW):** Implemented double-robust estimators combining propensity score modeling ($\pi(z))$ and outcome regression ($\mu_x(z)$) to handle high-dimensional covariate spaces and severe missing data structures without incurring specification bias.
* **Mediation & Heterogeneity Analysis:** Decomposed acute physiological pathways (electrolyte/fluid derangements, cardiac arrhythmias, hepatic dysfunction, coagulopathy, and neurological conditions) and evaluated effect heterogeneity across age brackets and Charlson Comorbidity Index stratification.
* **Rigorous Data Handling & Limitations Analysis:** Addressed real-world data challenges, including substantial missingness (e.g., ~46.4% in ICU mediators, ~61.9% in Charlson scores, ~46.9% in BMI) and selection bias considerations.

---

## Key Findings

* **Survival Advantage Confirmed, but Nuanced:** The total variation analysis confirmed a small net survival disadvantage/paradox, but decomposition revealed that the *Direct Effect* accounts for the primary survival variation, while indirect physiological pathways and spurious confounding nearly offset each other.
* **Mediator Counterbalance:** Certain acute conditions (e.g., Arrhythmia and Liver dysfunction) exhibited higher frequencies in normal-weight patients, counteracting expected survival trajectories and dampening the overall negative direct effect.
* **Risk Stratification Implications:** Findings indicate that standard clinical risk models must account for causal mediation and selection biases rather than taking observational risk ratios at face value, offering direct parallels to actuarial underwriting and mortality table adjustments.

---

## Repository Structure

```text
├── data/                    # Processed MIMIC-IV extracts and schema mappings
├── notebooks/               # R & Python scripts for AIPW estimation and DAG modeling
├── figures/                 # Causal decomposition plots and heterogeneity heatmaps
├── STATS_C160_Report.pdf    # Full comprehensive 9-page technical report
└── README.md
