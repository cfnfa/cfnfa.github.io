---
title: "A personalized hybrid federated learning framework for glucose prediction in type 1 diabetes"
collection: publications
category: manuscripts
permalink: /publication/2026-10-26-personalized-hybrid-federated-learning-glucose-prediction
excerpt: 'A federated Temporal Fusion Transformer trained across clinically defined silos and then personalized for each patient, evaluated on 497 adults and externally validated on a second cohort.'
date: 2026-10-26
venue: 'Artificial Intelligence in Medicine'
paperurl: 'https://www.sciencedirect.com/science/article/pii/S0933365726002137'
citation: 'Gallardo-García, C., <b>Fuertes, C.</b>, Hernando, M. E., Subías, D., Rigla, M., &amp; García-Sáez, G. (2027). &quot;A personalized hybrid federated learning framework for glucose prediction in type 1 diabetes.&quot; <i>Artificial Intelligence in Medicine</i>. 183, 103561.'
---
 
Open access journal article, published in the special issue "AIIM for IEEE CBMS 2025" of *Artificial Intelligence in Medicine*. This paper builds on our award-winning CBMS 2025 work, and I am a co-author (methodology and data curation).
 
## Why this work
 
Glucose prediction models trained in one place often fail to generalize to other clinical settings, because patients differ in treatment modality and insulin type (non-IID data). Federated learning can combine knowledge across institutions without sharing patient data, but it must cope with this heterogeneity, and patients also need models adapted to them.
 
## What we did
 
- **Hybrid design:** cross-silo federated training followed by patient-level personalization.
- **Clinically defined silos:** instead of random client partitions, the clients were built from the T1-DEXI dataset by treatment modality (closed-loop, insulin pump, multiple daily injections) and insulin type, which gives realistic treatment-related heterogeneity.
- **Model:** a Temporal Fusion Transformer for multi-horizon prediction (30, 60 and 90 minutes), trained with FedProx aggregation. It uses the clinician-prescribed basal insulin profile as a known future input.
- **Data:** T1-DEXI (497 adults, 487 after exclusions) for training and testing, and OhioT1DM (12 adults) for external validation and personalization.
- **Baselines:** centralized training and local-only models trained in isolation per silo.
## Key results
 
- **Collaboration helps:** federated training reduced RMSE by 5.4 to 6.5 mg/dL compared with local-only models on the T1-DEXI test set, depending on the prediction horizon.
- **Cost of privacy in-distribution:** the centralized model was slightly more accurate on T1-DEXI, by about 0.9 to 1.3 mg/dL.
- **Better under distribution shift:** on the external OhioT1DM cohort, the federated global model had significantly lower error than the centralized one at 60 and 90 minutes (by 2.8 and 4.5 mg/dL).
- **Personalization:** after patient-level fine-tuning, centralized models kept a small advantage (0.8 to 1.0 mg/dL), and the gap between global and personalized models was smaller for the federated model.
- **Clinically meaningful inputs matter:** adding the scheduled basal insulin profile improved in-distribution accuracy.
## Limitations
 
The silos were built from a single cohort rather than from independent institutions, the external cohort was small, and federated learning alone gives no formal privacy guarantee. Secure aggregation and differential privacy were out of scope and are needed for real-world use.
 
[Read the paper on ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0933365726002137) | DOI: [10.1016/j.artmed.2026.103561](https://doi.org/10.1016/j.artmed.2026.103561)
