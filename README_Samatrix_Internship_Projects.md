# Samatrix Consulting Internship — Data Analysis Projects

A collection of data analysis and statistical modelling projects completed during my **4-week Summer Internship at Samatrix Consulting Pvt. Ltd.**, from **23 June 2025 to 21 July 2025**.

The internship focused on cleaning, analyzing, and interpreting data using statistical techniques and Python tools to derive meaningful insights. This repository brings together five project notebooks covering clinical-trial survival analysis, IPL performance, call-center staffing, A/B testing, and portfolio risk assessment.

> **Important:** The findings below summarize the uploaded notebooks and their saved outputs. Some notebooks are exploratory and contain modelling assumptions or implementation issues; results should be revalidated before being used for operational, medical, or financial decisions.

## Table of Contents

- [Internship Overview](#internship-overview)
- [Project Collection](#project-collection)
  - [1. Clinical-Trial Survival Analysis](#1-clinical-trial-survival-analysis-for-treatment-efficacy)
  - [2. IPL Team Performance Analysis](#2-ipl-team-performance-trends-20082023)
  - [3. Call-Center Queue and Staffing Optimization](#3-call-center-queue-and-staffing-optimization)
  - [4. Website A/B Testing](#4-website-ab-testing-and-sequential-monitoring)
  - [5. Portfolio Risk Assessment and Value at Risk](#5-portfolio-risk-assessment-and-value-at-risk-var)
- [Combined Technology Stack](#combined-technology-stack)
- [Repository Structure](#suggested-repository-structure)
- [Setup and Run](#setup-and-run)
- [Key Learning Outcomes](#key-learning-outcomes)
- [Limitations and Reproducibility Notes](#limitations-and-reproducibility-notes)
- [Internship Verification](#internship-verification)

## Internship Overview

| Detail | Information |
|---|---|
| Organization | Samatrix Consulting Pvt. Ltd. |
| Internship | 4-week Summer Internship |
| Dates | 23 June 2025 – 21 July 2025 |
| Focus | Data analysis, statistical techniques, data cleaning, interpretation, and insight generation |
| Work format | Python Jupyter Notebook projects |

## Project Collection

### 1. Clinical-Trial Survival Analysis for Treatment Efficacy

**Notebook:** `PeeyushVerma_Clinical_Trial.ipynb`

#### Objective
Explore patient survival-time data to compare standard and test treatment groups and investigate how treatment and patient characteristics relate to survival outcomes.

#### What I did
- Inspected a clinical survival dataset containing **274 rows and 9 columns**.
- Examined fields including survival/follow-up time (`TIME`), event indicator (`Y`), treatment (`trt`), cell type, Karnofsky performance score (`karno`), diagnosis time, age, and prior therapy.
- Explored survival patterns using Kaplan–Meier survival curves.
- Applied log-rank tests to compare survival distributions between treatment groups.
- Fitted Cox proportional-hazards models to examine associations between covariates and survival.
- Explored a time-varying Cox model and prepared visualizations to support interpretation.

#### Results recorded in the notebook
- The Kaplan–Meier section reports median survival times of **95** for the standard group and **52** for the test group (time units follow the source dataset).
- A log-rank test output reports **p = 0.91423**, which does not provide evidence of a statistically significant difference between the compared survival curves at the conventional 0.05 threshold.
- Another comparison in the notebook reports **p = 0.9277**, also not statistically significant.

These are notebook outputs rather than a clinical conclusion. The notebook contains multiple analysis variants and some data-filtering warnings, so the treatment comparison and model specification should be checked before drawing a final efficacy conclusion.

#### Technology and methods
`Python`, `Pandas`, `NumPy`, `Matplotlib`, `lifelines`, Kaplan–Meier estimator, log-rank test, Cox proportional-hazards regression, time-varying Cox regression.

---

### 2. IPL Team Performance Trends (2008–2023)

**Notebook:** `PeeyushVerma_IPL_Analysis.ipynb`

#### Objective
Analyze Indian Premier League (IPL) match and innings data from 2008–2023 to explore scoring trends and test whether selected match contexts are associated with differences in team scoring.

#### What I did
- Loaded match-level and ball/innings-level data from CSV sources.
- Cleaned and transformed dates, standardized column names, and prepared run totals and run-rate features.
- Joined match information with aggregated team scoring data.
- Created a `Pre` / `Post` period split around 2018 for comparative analysis.
- Used descriptive statistics and visualizations to inspect distributions and trends.
- Checked normality with the Shapiro–Wilk test and used non-parametric Mann–Whitney U tests for selected comparisons.
- Compared scoring in playoffs versus league matches, explored team-level differences, and examined home-versus-away scoring.
- Used effect-size, confidence-interval, correlation, and OLS regression outputs for additional analysis.

#### Results recorded in the notebook
- The aggregated match/team dataset contains **2,045 rows and 10 columns** before later filtering.
- The notebook reports no statistically significant scoring difference between playoff and league matches in one comparison (**p ≈ 0.7669**).
- For Chennai Super Kings, the recorded Mann–Whitney U test reports **p ≈ 0.3327**, not statistically significant.
- A home-versus-away comparison reports a statistically significant difference (**p ≈ 1.24 × 10⁻⁵**).
- One later comparison reports a mean difference of approximately **11.94 runs**, a 95% confidence interval of approximately **[9.16, 14.70]**, and Cohen's *d* of approximately **0.39**. Interpret this alongside the exact groups and filtering used in that notebook section.

The notebook contains several analysis stages and filters; results depend on the selected seasons, teams, and comparison groups.

#### Technology and methods
`Python`, `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`, `SciPy` (`shapiro`, `mannwhitneyu`, skewness and kurtosis), `Statsmodels` (OLS regression), descriptive statistics, hypothesis testing, confidence intervals, effect size, correlation analysis, and feature engineering.

---

### 3. Call-Center Queue and Staffing Optimization

**Notebook:** `PeeyushVerma_CallCenter.ipynb`

#### Objective
Build a simulation-based exploration of call-center staffing, waiting times, queue size, customer abandonment, and staffing cost under changing call-arrival conditions.

#### What I did
- Modelled an 8-hour shift using simulated customer arrivals and service times.
- Used exponential inter-arrival and service-time distributions.
- Simulated queue behaviour for different agent counts, from 1 to 5.
- Compared average waiting time, 95th-percentile waiting time, and average system/queue size.
- Added exploratory scenarios for customer patience and abandonment, peak/off-peak arrival rates, agent breaks, and 30-day variability.
- Compared simulated behaviour with an M/M/1 queueing formula and explored a simple staffing-cost calculation.

#### Parameters and results recorded in the notebook
- Baseline arrival rate: **20 calls per hour**.
- Service rate: **5 calls per hour per agent**.
- Shift duration: **8 hours**.
- Waiting-time target used in the notebook: **95th-percentile wait of 5 minutes**.
- In one saved output, the time-varying arrival-rate scenario with 3 agents reports an average wait of **94.4 minutes**.
- A separate abandonment scenario with 4 agents reports an abandonment rate of **18.29%** and an average wait of **1.1 minutes among the calls included in the served-wait calculation**.
- The notebook's simple cost scenario reports its lowest computed cost at **1 agent**; this is not a reliable staffing recommendation without fixing the model assumptions and validating the cost calculation.

#### Technology and methods
`Python`, `NumPy`, `Pandas`, `Matplotlib`, discrete-event-style queue simulation, exponential random sampling, M/M/1 queueing concepts, staffing sensitivity analysis, abandonment modelling, time-varying arrivals, break scenarios, and cost trade-off analysis.

---

### 4. Website A/B Testing and Sequential Monitoring

**Notebook:** `PeeyushVerma_AB_Testing.ipynb`

#### Objective
Simulate an e-commerce checkout experiment to test whether a new checkout experience (Variant B) converts better than the existing experience (Variant A).

#### What I did
- Simulated visitors and purchase outcomes for two variants.
- Calculated conversion rates and 95% confidence intervals.
- Visualized conversion-rate estimates and uncertainty.
- Applied a two-proportion z-test to assess whether the difference was statistically significant.
- Built a batch-based monitoring simulation that tracks conversion rates, observed lift, and p-values as more visitors arrive.

#### Results recorded in the notebook
In the initial simulated experiment:
- Variant A: **973 conversions / 10,000 visitors = 9.73%**.
- Variant B: **1,134 conversions / 10,000 visitors = 11.34%**.
- Observed absolute difference: **1.61 percentage points**.
- Two-proportion z-test: **z ≈ 3.708**, **p ≈ 0.000104**.
- The notebook's test rejects the null hypothesis at the 0.05 level for this simulated sample.

In the saved sequential simulation's final batch:
- Variant A: **574 / 6,000 = 9.57%**.
- Variant B: **714 / 6,000 = 11.90%**.
- Observed absolute lift: approximately **2.33 percentage points**.
- The saved output reports a statistically significant result at the final batch.

These are simulated results, not results from a live production experiment. Repeatedly checking ordinary p-values during sequential monitoring can inflate the false-positive rate; a production experiment should use a pre-defined sample size or a valid sequential-testing method.

#### Technology and methods
`Python`, `NumPy`, `Pandas`, `Matplotlib`, `SciPy`, `Statsmodels` (`proportions_ztest`), conversion-rate analysis, confidence intervals, hypothesis testing, and batch/sequential monitoring simulation.

---

### 5. Portfolio Risk Assessment and Value at Risk (VaR)

**Notebook:** `VaR.ipynb`

#### Objective
Explore historical returns and portfolio risk for a five-stock portfolio using parametric and historical Value at Risk (VaR), Expected Shortfall (CVaR/ES), drawdown, diversification, and backtesting concepts.

#### What I did
- Retrieved historical prices for **AAPL, MSFT, AMZN, NVDA, and TSLA** using `yfinance`.
- Calculated daily log returns and summarized mean, variance, skewness, and kurtosis.
- Visualized return distributions and explored Normal and Student's *t*-distribution fits.
- Calculated 95% VaR using parametric and historical-percentile approaches.
- Explored Expected Shortfall, correlation, equal-weight portfolio returns, maximum drawdown, and recovery time.
- Ran a one-sample t-test on portfolio returns and a Jarque–Bera normality test.
- Checked historical VaR exceptions and plotted rolling 60-day historical VaR.

#### Results recorded in the notebook
- The downloaded price matrix contains **1,526 rows and 5 stock columns**.
- Equal portfolio weights of **20% per stock** were used in one portfolio analysis.
- A saved calculation reports a maximum drawdown of approximately **−55.49%**, from **19 November 2021** to **5 January 2023**, with a reported recovery date of **21 May 2024**.
- The notebook reports a historical 95% Expected Shortfall of **0.05112** in return units (about 5.11% under the notebook's calculation).
- VaR backtesting reports **77 exceptions out of 1,525 days (5.05%)**, close to the nominal 5% rate in that calculation.
- A Jarque–Bera test reports **p < 0.001**, rejecting normality for the tested return series.

**Reproducibility note:** The notebook contains exploratory calculations with inconsistent VaR sign conventions and variable reuse, and some results use simulated returns rather than the downloaded portfolio returns. Therefore, individual VaR figures in the notebook are not presented here as one definitive risk estimate. The calculations should be consolidated and rerun before using the results for financial decisions.

#### Technology and methods
`Python`, `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`, `yfinance`, `SciPy` (`stats`, Normal and Student's *t* distributions, Jarque–Bera and t-tests), `Joblib` (parallel bootstrap fitting), log returns, portfolio weighting, VaR, Expected Shortfall, drawdown, correlation, diversification analysis, and backtesting.

---

## Combined Technology Stack

| Category | Tools / techniques used |
|---|---|
| Language | Python |
| Notebook environment | Jupyter Notebook / IPython |
| Data manipulation | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Statistical analysis | SciPy, Statsmodels |
| Survival analysis | lifelines |
| Financial data retrieval | yfinance |
| Parallel computation | Joblib |
| Statistical methods | Descriptive statistics, confidence intervals, hypothesis testing, normality tests, Mann–Whitney U test, two-proportion z-test, log-rank test, Cox regression, OLS regression |
| Modelling and analysis | Feature engineering, survival analysis, queue simulation, A/B testing, portfolio risk, VaR, Expected Shortfall, drawdown, and backtesting |

## Suggested Repository Structure

```text
samatrix-internship-data-analysis/
├── README.md
├── notebooks/
│   ├── PeeyushVerma_Clinical_Trial.ipynb
│   ├── PeeyushVerma_IPL_Analysis.ipynb
│   ├── PeeyushVerma_CallCenter.ipynb
│   ├── PeeyushVerma_AB_Testing.ipynb
│   └── VaR.ipynb
└── docs/
    └── internship-certificate.pdf   # Optional; share only if you want it public
```

The structure above is a suggested GitHub layout. The uploaded files may currently be in a different folder arrangement.

## Setup and Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd samatrix-internship-data-analysis
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

Linux/macOS:

```bash
source .venv/bin/activate
```

Windows:

```powershell
.venv\Scripts\activate
```

### 3. Install the common dependencies

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels lifelines yfinance joblib jupyter
```

### 4. Start Jupyter

```bash
jupyter notebook
```

Open the notebook you want to explore and run its cells in order.

### Data notes
- The IPL notebook reads CSV data from remote URLs included in the notebook. Internet access may be required, and those URLs may change.
- The clinical-trial notebook uses a dataset whose loading steps are embedded in the notebook. Check the source cell and dataset terms before redistributing the data.
- The call-center and A/B-testing notebooks generate simulated data.
- The VaR notebook downloads market prices with `yfinance`, so its results can change when the data range or source data changes.

## Key Learning Outcomes

- Cleaning, transforming, and validating tabular data.
- Exploratory data analysis and communicating patterns with charts.
- Choosing statistical tests based on the question and data assumptions.
- Interpreting p-values, confidence intervals, and effect sizes.
- Applying survival-analysis methods to time-to-event data.
- Simulating queues and evaluating staffing trade-offs.
- Measuring conversion-rate differences in controlled experiments.
- Exploring portfolio risk using VaR, Expected Shortfall, drawdown, and backtesting.
- Translating analytical outputs into understandable findings while documenting assumptions and limitations.

## Limitations and Reproducibility Notes

- The notebooks are exploratory learning and analysis artifacts, not production-ready systems.
- Some notebooks depend on external datasets or current market data; results can change.
- Statistical significance does not by itself prove practical importance or causation.
- Survival-analysis results depend on correct event/censoring definitions and valid model assumptions.
- Sequential A/B monitoring requires appropriate statistical controls if used for real decisions.
- The call-center notebook contains assumptions and queueing calculations that need validation; its simple cost minimum should not be interpreted as a staffing recommendation.
- The VaR notebook has inconsistent sign conventions and mixes some simulated-return calculations with historical-price analysis. Reconcile these before reporting one final risk number.
- Always rerun notebooks from top to bottom in a clean environment before publishing final numbers.

## Internship Verification

The uploaded internship completion certificate states that Peeyush Verma, a student of JECRC University Jaipur, successfully completed a **4-week Summer Internship at Samatrix Consulting Pvt. Ltd. from 23 June 2025 to 21 July 2025**. It describes the work as data-analysis projects involving statistical techniques and tools, including cleaning, analyzing, and interpreting data to derive insights.

**Organization:** Samatrix Consulting Pvt. Ltd.  
**Website:** https://samatrix.io

---

## Author

**Peeyush Verma**  
B.Tech, Computer Science Engineering (AI & ML) — JECRC University, Jaipur

- GitHub: https://github.com/DevPeeyush
- LinkedIn: https://www.linkedin.com/in/peeyush-verma1

---

*This README consolidates the five uploaded project notebooks into one internship-project overview. Update the repository URL and verify the notebooks run successfully before publishing.*
