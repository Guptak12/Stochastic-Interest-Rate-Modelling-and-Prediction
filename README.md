## Finance Club, IIT Roorkee: Stochastic Interest Rate Modelling and Prediction

This README outlines the submission for the 2026 IIT Roorkee Finance Club Open Projects. The project tackles the implementation, calibration, and extension of the Cox-Ingersoll-Ross (CIR) short-rate model using real-world yield curve data. It is designed as a single-person project to be completed within a two-week duration.

---

### Project Overview

Interest rates drive bond pricing, derivative valuation, and portfolio risk management. This project utilizes advanced mathematical frameworks rooted in stochastic calculus to model the seemingly random evolution of short rates. By building the CIR framework from the ground up, the project estimates historical parameters, projects the yield curve, and critically analyzes the model's limitations.

---

### Core Objectives & Workflow

* **Data Engineering**: The raw dataset contains missing values, outliers, and formatting inconsistencies. The preprocessing pipeline utilizes column stripping, numeric coercion, linear interpolation, and robust outlier filtering via a rolling Median Absolute Deviation (MAD) window.


* **Base CIR Model Calibration**: The model parameters are estimated using three distinct approaches: Time-Series Ordinary Least Squares (OLS), Time-Series Maximum Likelihood Estimation (MLE), and Cross-Sectional (CS) Yield Curve Calibration.


* **Yield Curve Construction**: The core predictive test requires reconstructing the entire yield curve for out-of-sample test days using solely the 3-Month (3M) yield as a proxy for the instantaneous short rate.


* **Model Extension**: The base CIR model is extended into the CIR++ (Shifted CIR) framework to address the base model's limitations in fitting initial term structures.


* **Critical Analysis**: The project analyzes the sensitivity of the calibrated curves, the breakdown of the Feller condition, and the vulnerabilities of deterministic shift extensions during structural regime changes.



---

### Mathematical Framework

The fundamental basis of the CIR model is the evolution of the instantaneous short rate $r_{t}$ via the following stochastic differential equation:

$$dr_{t}=\kappa(\theta-r_{t})dt+\sigma\sqrt{r_{t}}dW_{t}$$

* $\kappa>0$ represents the speed of mean reversion.


* $\theta>0$ represents the long-run mean.


* $\sigma>0$ is the volatility coefficient.


* $W_{t}$ represents a standard Brownian motion.



The inclusion of the square-root diffusion process ensures that interest rates remain strictly positive, assuming the Feller condition $2\kappa\theta\ge\sigma^{2}$ is satisfied. In scenarios where the Feller condition breaks down, the project implementation relies on a full truncation scheme to handle boundary violations.

---

### Project Results & Insights

* **Predictive Accuracy**: The Cross-Sectional (CS) calibration significantly outperformed the time-series methods, achieving an out-of-sample pooled $R^{2}$ of 0.892873, successfully exceeding the project's verification threshold of 0.85.


* **Extension Underperformance**: The CIR++ extended model yielded a lower out-of-sample $R^{2}$ of 0.835044. This occurred because the deterministic shift was calibrated on training data and subsequently failed to adapt to a drastic interest rate regime shift during the testing period.


* **Mean-Reversion Dynamics**: Based on the CS calibration, the estimated mean-reversion speed implies that interest rate shocks possess a half-life of approximately 4.17 years, indicating high shock persistence.


* **Systematic Limitations**: The 2-Year maturity proved the most difficult to fit, as the single-factor nature of the base CIR model struggles to capture steeply rising yield curves during severe interest rate hikes.



---

### Deliverables and Formatting

The final submission is contained entirely within a single Google Colab Notebook.

| Requirement | Description |
| --- | --- |
| **Code Execution** | The notebook runs fully from top to bottom, handling data processing, model calibration, and metric output without errors. |
| **Markdown as Report** | Integrated markdown cells explain stochastic calculus concepts, justify choices, and outline limitations. |
| **Code Quality** | The codebase is Pythonic and modular, utilizing clear inline comments (written in Spanish per project configuration) to explain complex mathematical steps. |


 ### Submission
submitted by :- Kush
(guptak12)
