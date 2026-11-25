---
title: "Implementation of a Federated Learning Platform for Glucose Prediction in Type 1 Diabetes"
collection: publications
category: conferences
permalink: /publication/2025-06-18-federated-learning-platform-glucose-prediction-t1d
excerpt: 'First application of federated learning to glucose prediction in Type 1 Diabetes: an LSTM trained across simulated hospital and patient clients with Flower matched, and in several metrics beat, centralized training. Best Student Paper Award.'
date: 2025-06-18
venue: '2025 IEEE 38th International Symposium on Computer-Based Medical Systems (CBMS)'
paperurl: 'https://ieeexplore.ieee.org/document/11058766'
citation: '<b>Fuertes, C.</b>, Gallardo, C., Subias, D., Hernando, M. E., Rigla, M., &amp; García-Sáez, G. (2025). &quot;Implementation of a Federated Learning Platform for Glucose Prediction in Type 1 Diabetes.&quot; <i>2025 IEEE 38th International Symposium on Computer-Based Medical Systems (CBMS)</i>. 311-316.'
---
 
**Best Student Paper Award**, IEEE CBMS 2025 (Madrid, 18-20 June 2025). I am the first author of this paper.
 
## Why this work
 
Deep learning can improve glucose forecasting for people with Type 1 Diabetes, but it needs large and diverse datasets, and clinical data is sensitive and hard to share. Federated learning (FL) trains a shared model without moving the raw data: only model updates leave each participant. At the time of the study, I found no earlier application of FL to glucose time-series prediction in diabetes.
 
## What we did
 
- **Data:** insulin pump and continuous glucose monitoring records from 12 anonymized patients, provided by Parc Taulí Hospital (about three months each).
- **Model:** an LSTM network (TensorFlow/Keras) that forecasts glucose 30 minutes ahead from four inputs: glucose, bolus insulin, basal insulin and carbohydrate intake, on a common 5-minute grid. Hyperparameters were tuned with Bayesian optimization.
- **Federated platform:** built with the [Flower](https://flower.ai/) framework and its Simulation Engine, with a central server coordinating the clients.
- **Experiments:** 8 in total, comparing centralized training with FL in two scenarios, **cross-silo** (4 clients, each representing an institution) and **cross-device** (11 clients, one per patient), using the aggregation strategies FedAvg, FedMedian, FedTrimmedAvg and FedAdam. I extended the Flower strategies with real-time metric tracking and RMSE-based model checkpointing.
- **Evaluation:** RMSE, Pearson correlation and the Clarke Error Grid, which measures clinical safety.
## Key results
 
| Metric | Centralized | Federated (average) |
|---|---|---|
| RMSE (mg/dL) | 22.98 | 20.70 ± 0.17 |
| Pearson correlation | 0.927 | 0.936 |
| Clarke zone D errors | 2.72 % | 1.88 % |
 
- The federated models matched or improved on the centralized model, and reduced the most dangerous prediction errors (Clarke zone D).
- Three aggregation strategies (FedAvg, FedMedian, FedTrimmedAvg) worked well, with no clear winner. FedAdam did not converge, because its extra hyperparameters could not be tuned within the computational budget.
- FL training took about 8 times longer than centralized training.
## Limitations and next steps
 
The federation was simulated on a single machine, and the data partitions necessarily differed from the centralized setup. The next steps are a real multi-institution deployment, larger datasets, and privacy-enhancing techniques such as differential privacy and secure aggregation for non-trusted environments.
 
## Funding
 
Spanish research grant PROPHECY (PI21/01028, PI21/00154), co-funded by the European Union.
 
[Read the paper on IEEE Xplore](https://ieeexplore.ieee.org/document/11058766) | DOI: [10.1109/CBMS65348.2025.00069](https://doi.org/10.1109/CBMS65348.2025.00069)
