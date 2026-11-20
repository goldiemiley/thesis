# Literature review: sources

Annotated sources for my IMQF master's thesis. The thesis compares generalised linear models (GLMs) with gradient boosting for motor-insurance claim frequency and severity, checks the calibration of both, and assesses what the differences mean for premium adequacy.

## Overview

| Theme | Sources |
|---|---|
| [GLMs versus machine learning for frequency–severity pricing](#1-glms-versus-machine-learning-for-frequencyseverity-pricing) | 1–5 |
| [Calibration](#2-calibration) | 6–8 |
| [Financial consequences of pricing errors](#3-financial-consequences-of-pricing-errors) | 9 |
| [Datasets](#4-datasets) | 10–11 |
| [Interpretability](#5-interpretability) | 12–13 |
| [Discrimination and fairness](#6-discrimination-and-fairness) | 14–15 |
| [Reviews and textbooks](#7-reviews-and-textbooks) | 16–17 |

---

## 1. GLMs versus machine learning for frequency–severity pricing

### 1. Clemente, Guerreiro & Bravo (2023)
**Modelling Motor Insurance Claim Frequency and Severity Using Gradient Boosting.** *Risks*, 11(9), 163. [doi:10.3390/risks11090163](https://doi.org/10.3390/risks11090163)

- **Examines:** whether gradient boosting improves both components of expected claim cost.
- **Method:** separate frequency and severity models; GLM versus gradient-boosted decision trees; out-of-sample comparison.
- **Data:** a proprietary motor portfolio from a European insurer operating in European and non-European markets.
- **Findings:** boosting performed better for claim frequency, but the GLM performed better for severity. Non-linear relationships do not automatically make boosting the best model for every target.
- **For this thesis:** one of the strongest methodological references. It supports choosing the frequency and severity models independently instead of assuming one algorithm must win both.

### 2. Wilson, Nehme, Dhyani & Mahbub (2024)
**A Comparison of Generalised Linear Modelling with Machine Learning Approaches for Predicting Loss Cost in Motor Insurance.** *Risks*, 12(4), 62. [doi:10.3390/risks12040062](https://doi.org/10.3390/risks12040062)

- **Examines:** how alternative frequency–severity models perform when combined into loss-cost predictions.
- **Method:** GLM, gradient boosting, neural networks and a hybrid GLM–neural-network model, evaluated on combined frequency–severity predictions.
- **Data:** French freMTPL2freq and freMTPL2sev.
- **Findings:** the hybrid model performed best, with the standalone neural network close behind.
- **For this thesis:** a direct comparison study to build on. The thesis extends it by examining calibration and alignment with actual premiums on a different portfolio, not only by repeating its model ranking.

### 3. Henckaerts, Côté, Antonio & Verbelen (2021)
**Boosting Insights in Insurance Tariff Plans with Tree-Based Machine Learning Methods.** *North American Actuarial Journal*, 25(2), 255–285. [doi:10.1080/10920277.2020.1745656](https://doi.org/10.1080/10920277.2020.1745656)

- **Examines:** building complete insurance tariffs with tree-based methods and assessing their economic value.
- **Method:** regression trees, random forests and boosted trees; insurance-specific loss functions; extensive cross-validation; interpretation tools and economic evaluation.
- **Data:** motor-insurance frequency and severity portfolio data.
- **Findings:** boosted trees outperformed classical GLMs; the resulting risk differentiation helped form profitable simulated portfolios and guard against adverse selection.
- **For this thesis:** connects model performance to tariff construction and selection risk. Especially useful for the financial-implications chapter.

### 4. Holvoet, Antonio & Henckaerts (2025)
**Neural Networks for Insurance Pricing with Frequency and Severity Data: A Benchmark Study from Data Preprocessing to Technical Tariff.** *North American Actuarial Journal*, 29(3), 519–562. [doi:10.1080/10920277.2025.2451860](https://doi.org/10.1080/10920277.2025.2451860)

- **Examines:** the full workflow from preprocessing through prediction and calibration to a deployable tariff.
- **Method:** GLM, boosted trees, feed-forward networks and combined actuarial neural networks; cross-validation, deviance, calibration, statistical comparisons and surrogate GLMs.
- **Data:** Australian, Belgian, French and Norwegian motor-insurance datasets.
- **Findings:** results varied by dataset and criterion. A boosting-based hybrid tariff was preferred by their Gini selection criterion for three datasets, while the GLM was preferred for Norway.
- **For this thesis:** probably the best end-to-end methodological guide. It shows why a single accuracy number is not enough and why results need not carry over between portfolios.

### 5. Su & Bai (2020)
**Stochastic Gradient Boosting Frequency-Severity Model of Insurance Claims.** *PLOS ONE*, 15(8), e0238000. [doi:10.1371/journal.pone.0238000](https://doi.org/10.1371/journal.pone.0238000)

- **Examines:** whether modelling the dependence between claim frequency and severity improves loss modelling.
- **Method:** dependent frequency–severity boosting with profile likelihood; frequency enters the severity model as a predictor; simulations.
- **Data:** simulated datasets and French motor-insurance claims data.
- **Findings:** the dependent model outperformed the competing methods in the reported experiments.
- **For this thesis:** frames the discussion of the independence assumption behind a simple frequency × severity approach. A possible extension, not part of the core design.

---

## 2. Calibration

### 6. Denuit, Charpentier & Trufin (2021)
**Autocalibration and Tweedie-Dominance for Insurance Pricing with Machine Learning.** *Insurance: Mathematics and Economics*, 101, 485–497. [doi:10.1016/j.insmatheco.2021.09.001](https://doi.org/10.1016/j.insmatheco.2021.09.001)

- **Examines:** why flexible models can predict aggregate losses incorrectly even when trained to minimise deviance.
- **Method:** mathematical analysis of Tweedie losses; local GLM recalibration; comparisons involving GLM, GAM, boosting and neural networks.
- **Data:** French freMTPL2 frequency and severity data, alongside theoretical analysis.
- **Findings:** minimising deviance does not by itself guarantee balanced predictions. Local recalibration corrects bias at the level of price groups, not only across the whole portfolio.
- **For this thesis:** the main justification for comparing observed and predicted losses by risk group, and for checking calibration before interpreting premium adequacy.

### 7. Wüthrich & Ziegel (2024)
**Isotonic Recalibration under a Low Signal-to-Noise Ratio.** *Scandinavian Actuarial Journal*, 2024(3), 279–299. [doi:10.1080/03461238.2023.2246743](https://doi.org/10.1080/03461238.2023.2246743)

- **Examines:** how to recalibrate noisy insurance predictions while keeping an understandable pricing structure.
- **Method:** isotonic regression applied to existing predictions; theoretical analysis and a neural-network application.
- **Data:** French MTPL claim-frequency data and mathematical examples.
- **Findings:** under the paper's conditions, a low signal-to-noise ratio leads to a simple, stepwise recalibrated pricing structure.
- **For this thesis:** a practical optional improvement: compare GLM and boosting before and after recalibration. Recalibration must still be evaluated out of sample.

### 8. Denuit, Huyghe, Trufin & Verdebout (2024)
**Testing for Auto-Calibration with Lorenz and Concentration Curves.** *Insurance: Mathematics and Economics*, 117, 130–139. [doi:10.1016/j.insmatheco.2024.04.003](https://doi.org/10.1016/j.insmatheco.2024.04.003)

- **Examines:** whether calibration can be tested statistically instead of judged only from charts.
- **Method:** a characterisation of auto-calibration using Lorenz and concentration curves; a statistical test; simulation study.
- **Data:** simulated data and a Swiss motor-insurance database.
- **Findings:** develops a calibration test and demonstrates it on insurance predictions.
- **For this thesis:** supports a more rigorous validation chapter, and explains the limits of judging calibration from decile plots alone.

---

## 3. Financial consequences of pricing errors

### 9. Finger, Albrecher & Wilhelmy (2024)
**On the Cost of Risk Misspecification in Insurance Pricing.** *Japanese Journal of Statistics and Data Science*, 7(2), 1111–1153. [doi:10.1007/s42081-024-00256-z](https://doi.org/10.1007/s42081-024-00256-z)

- **Examines:** the financial consequences of assigning policyholders to the wrong risk class.
- **Method:** a two-risk-type economic model; premium optimisation; mean–variance analysis; numerical examples and Monte Carlo extensions.
- **Data:** stylised portfolios and simulated losses, not an observed motor portfolio.
- **Findings:** classification errors can change which customers accept cover and reduce premium income. Whether finer risk differentiation pays off depends on its costs, its errors and the insurer's objectives.
- **For this thesis:** a key quantitative-finance reference on why model errors matter commercially. It is also a reminder that policy data alone cannot reveal how customers would respond to price changes.

---

## 4. Datasets

### 10. Espinosa, Lledó & Atance (2026)
**A Detailed Dataset of Motor Insurance Policies with Coverage-Specific Financial Information.** *Data in Brief*, 66. [doi:10.1016/j.dib.2026.112883](https://doi.org/10.1016/j.dib.2026.112883) · Data: [Mendeley Data, doi:10.17632/sw4jmdb2sm.1](https://doi.org/10.17632/sw4jmdb2sm.1)

- **Examines:** documents a new Spanish motor-insurance dataset.
- **Method:** anonymisation, duplicate removal, variable standardisation, range checks and consistency validation.
- **Data:** 354,140 policy-year observations and 47 variables, 2022–2024: premiums, exposure, claims, and incurred losses by coverage.
- **Findings:** a dataset release. It does not establish a best pricing model or show that premiums are inadequate.
- **For this thesis:** the primary data source. Its definitions and preprocessing decisions guide the data chapter and the limitations.

### 11. Segura-Gisbert, Lledó & Pavía (2025)
**Dataset of an Actual Motor Vehicle Insurance Portfolio.** *European Actuarial Journal*, 15, 241–253 (online 2024). [doi:10.1007/s13385-024-00398-0](https://doi.org/10.1007/s13385-024-00398-0)

- **Examines:** an earlier public Spanish motor-insurance portfolio.
- **Method:** dataset construction, anonymisation and descriptive documentation.
- **Data:** 105,555 records and 30 variables, November 2015 – December 2018: policy dates, premiums, claims and vehicle characteristics.
- **Findings:** a dataset contribution, not a comparative modelling study.
- **For this thesis:** a possible second dataset for replication. It is a separate portfolio and cannot be linked to the 2022–2024 data.

---

## 5. Interpretability

### 12. Richman & Wüthrich (2023)
**LocalGLMnet: Interpretable Deep Learning for Tabular Data.** *Scandinavian Actuarial Journal*, 2023(1), 71–95. [doi:10.1080/03461238.2022.2081816](https://doi.org/10.1080/03461238.2022.2081816)

- **Examines:** combining flexible prediction with a GLM-like interpretation of each variable.
- **Method:** a neural architecture with input-dependent regression coefficients; variable selection and interaction analysis.
- **Data:** synthetic examples and French motor-insurance claim-frequency data.
- **Findings:** achieves flexible non-linear prediction while exposing variable contributions and interactions.
- **For this thesis:** helps separate inherently interpretable models from post-hoc explanations, and supports interpreting the boosting model alongside its performance metrics.

### 13. Kuo & Lupton (2023)
**Towards Explainability of Machine Learning Models in Insurance Pricing.** *Variance*, 16(1). [Article](https://variancejournal.org/article/68374-towards-explainability-of-machine-learning-models-in-insurance-pricing) · [Preprint: arXiv:2003.10674](https://doi.org/10.48550/arXiv.2003.10674)

- **Examines:** why machine-learning models have been slow to be adopted in a regulated pricing practice, and how actuaries can explain them.
- **Method:** a framework for explaining pricing models, built around actuarial standards on communicating results, illustrated with a case study.
- **Findings:** frames model validation around two questions: how the model affects individual policyholders, and how the predictors relate to expected losses.
- **For this thesis:** a practitioner-focused reference for the interpretability section. It explains what a regulator or pricing committee would need to see before a boosting model could replace a GLM.

---

## 6. Discrimination and fairness

### 14. Lindholm, Richman, Tsanakas & Wüthrich (2022)
**Discrimination-Free Insurance Pricing.** *ASTIN Bulletin*, 52(1), 55–89. [doi:10.1017/asb.2021.23](https://doi.org/10.1017/asb.2021.23)

- **Examines:** the difference between predicting risk accurately and setting prices that avoid direct and proxy discrimination.
- **Method:** a probabilistic pricing framework; averaging over protected characteristics; correction for portfolio bias.
- **Data:** theoretical analysis and a synthetic health-insurance portfolio, not motor-insurance evidence.
- **Findings:** simply leaving out a protected characteristic does not remove its indirect influence through correlated variables.
- **For this thesis:** supports a careful discussion of price differences between customer groups. Model-based risk differentiation should not automatically be called "fair pricing".

### 15. Lindholm, Richman, Tsanakas & Wüthrich (2024)
**A Multi-Task Network Approach for Calculating Discrimination-Free Insurance Prices.** *European Actuarial Journal*, 14(2), 329–369 (online 2023). [doi:10.1007/s13385-023-00367-z](https://doi.org/10.1007/s13385-023-00367-z)

- **Examines:** whether discrimination-free prices can be estimated when protected information is incomplete.
- **Method:** multi-task neural networks compared with conventional feed-forward networks at different levels of missing information.
- **Data:** synthetic data and a real motor-claims dataset.
- **Findings:** performance was comparable when protected information was available for at least half of the policies, and better when it was available for fewer than half.
- **For this thesis:** explains the data requirements and limits of a fairness extension. Relevant to the limitations section, not to the core GLM–boosting comparison.

---

## 7. Reviews and textbooks

### 16. Blier-Wong, Cossette, Lamontagne & Marceau (2021)
**Machine Learning in P&C Insurance: A Review for Pricing and Reserving.** *Risks*, 9(1), 4. [doi:10.3390/risks9010004](https://doi.org/10.3390/risks9010004)

- **Examines:** applications of machine learning in property and casualty insurance.
- **Method:** structured literature review and methodological overview, including neural networks.
- **Data:** previously published studies.
- **Findings:** organises the literature on pricing and reserving and identifies directions for further work. It does not name a single best algorithm.
- **For this thesis:** a starting point for the literature review, and for placing the thesis within actuarial analytics rather than generic "AI".

### 17. Wüthrich & Merz (2023)
**Statistical Foundations of Actuarial Learning and its Applications.** Springer Actuarial, Cham. Open access. [doi:10.1007/978-3-031-12409-9](https://doi.org/10.1007/978-3-031-12409-9)

- **Covers:** statistical learning for actuarial work: regression, model evaluation and modern predictive methods.
- **Method:** mathematical development supported by worked actuarial applications on public datasets. A textbook, not a single empirical study.
- **Contribution:** connects practical modelling to the assumptions and statistical principles needed to interpret results correctly.
- **For this thesis:** the reference for exposure treatment, loss functions, validation and actuarial terminology.
