# Comparing Effective Estimators of Large Wildfires in California Using the Pareto Distribution

## Overview

This project focuses on **predicting the occurrence and frequency of extremely large wildfires** in California, using fire data collected between 2017 and 2022. Due to the inherent rarity of these catastrophic events, traditional statistical methods often fail to accurately model the **heavy-tailed distribution** of fire areas.

To address this challenge, we utilized the **Pareto distribution** to model the upper tail of the wildfire size data (fires $\ge$ 50,000 acres) and estimate the expected rate of fires $\ge$ 300,000 acres. The core of our work involves a comparative simulation study of different estimators and confidence interval methods for the Pareto shape parameter, $\alpha$.

---

## Key Findings

Through extensive simulation and analysis, we determined the most statistically robust methods for estimating large wildfire rates:

1. **Optimal Estimator:** The **Maximum Likelihood Estimator (MLE)** for the Pareto shape parameter ($\hat{\alpha}_{MLE}$) consistently demonstrated a **lower Root Mean Squared Error (RMSE)** compared to the Method of Moments (MOM) estimator across all tested values of $\alpha$ and sample sizes ($n$).

2. **Optimal Confidence Interval:** The **Exact 95% Confidence Interval** method exhibited coverage rates closest to the nominal 95% target, regardless of $\alpha$ or sample size, making it the most reliable method.

3. **Asymptotic Efficiency:** While both MLE and MOM were asymptotically efficient, the **MLE converged faster** (intervals became narrower more quickly) at large sample sizes ($n>200$).

---

## Final Prediction

Using the optimal **MLE point estimator** and the **Exact 95% Confidence Interval** method on the real-world California wildfire data:

* **Estimated Pareto Shape Parameter ($\hat{\alpha}_{MLE}$):** $1.08$ (95% CI: $0.788, 1.41$)

* **Expected Number of Large Wildfires ($\ge 300,000$ acres) per Year:** **1.30 fires** (95% CI: $0.71, 2.19$)

We are 95% confident that the true number of extreme wildfires expected in California in a given year falls between 0.71 and 2.19.

---

## Methodology Details

### Data

* **Source:** California Department of Forestry and Fire Protection.

* **Timeframe:** 2017–2022.

* **Scope:** Wildfires with a minimum area of spread of **50,000 acres**.

### Statistical Framework

The area of spread ($Y$) for large wildfires is modeled by the two-parameter **Pareto Distribution** $Pareto(y_m, \alpha)$, with:

* $y_m$: Scale parameter (minimum area, set to 50,000 acres).

* $\alpha$: **Shape parameter** (the parameter of interest, which describes the heaviness of the distribution's tail).

### Estimators Compared

| Estimator | Formula | Key Benefit |
| :--- | :--- | :--- |
| **Maximum Likelihood Estimator ($\hat{\alpha}_{MLE}$)** | $\frac{1}{\frac{1}{n}\sum_{i=1}^{n}log(Y_{i}/y_{m})}$ | **Asymptotically efficient**; lower RMSE in simulations. |
| **Method of Moments Estimator ($\hat{\alpha}_{MOM}$)** | $\frac{\overline{Y}}{\overline{Y}-y_{m}}$ (assuming $\alpha>1$) | Simpler to calculate; provided competitive precision at small sample sizes but lacked coverage accuracy. |

---

## Repository Structure

The full code and detailed results are available in the linked GitHub repository:

* **`final_project/`**: Contains the core simulation code to compare the MLE and MOM estimators and calculate coverage rates/RMSE.

* **`wildfire_exploration/`**: Includes the code for applying the final, chosen estimator to the real-world data and generating the final expected value and QQ-plot.

* **`AdditionalExploration/`**: Code and visualization for comparing the asymptotic efficiency of the two estimators.

* **`STAT_250_Final_Project_...pdf`**: The complete final report detailing all derivations, simulation setup, and results.

---

## Authors

* Grace Hanson

* Simon Hempel-Costello

* Ammy Lin
