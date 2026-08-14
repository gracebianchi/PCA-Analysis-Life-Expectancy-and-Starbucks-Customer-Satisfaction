# Principal Component Analysis: Life Expectancy & Starbucks Customer Satisfaction

Two principal component analysis (PCA) case studies conducted in R. This project applies dimensionality reduction to datasets from two distinct domains—global health and customer satisfaction—to identify the smaller set of latent dimensions underlying correlated variables.

**[Read the full analysis (PDF)](./PCA_Analysis_Grace_Bianchi.pdf)** | **[View the R Markdown source](./PCA_Analysis_Grace_Bianchi.Rmd)**

## Project Overview

This project demonstrates how the same unsupervised learning technique can uncover interpretable patterns across different types of data.

| Case Study                      | Data                                                        | Objective                                                                                                     |
| ------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Life Expectancy                 | 183 countries observed in 2015 across 9 health indicators   | Summarize the primary dimensions of global health, mortality, disease, and healthcare expenditure             |
| Starbucks Customer Satisfaction | 113 survey respondents across 20 retained numeric variables | Identify the main dimensions underlying customer satisfaction, demographics, spending, and store-use behavior |

For each case study, I standardized the variables, performed PCA, evaluated component importance, interpreted variable loadings, and visualized the results using scree plots, biplots, correlation circles, representation-quality plots, and contribution charts.

## Key Findings

### Life Expectancy Analysis

The first three principal components explained approximately **76.1% of the total variance**:

* **PC1: Overall health outcomes (38.3%)**
  Contrasted life expectancy and immunization coverage with adult mortality, child mortality, and HIV/AIDS prevalence.

* **PC2: Childhood disease and mortality (26.7%)**
  Primarily reflected variation in measles cases, infant deaths, and under-five deaths.

* **PC3: Healthcare expenditure (11.1%)**
  Was driven primarily by percentage expenditure on healthcare, capturing financial variation not represented by the main health and mortality dimensions.

Overall, the analysis reduced nine correlated health indicators to three interpretable components representing general health outcomes, childhood disease burden, and healthcare spending.

### Starbucks Customer Satisfaction Analysis

The first three principal components explained approximately **41.2% of the total variance**, while the first six components explained approximately **61.4%**:

* **PC1: Overall customer satisfaction (18.8%)**
  Was driven by product quality, service, ambiance, price, and product-choice ratings, indicating that customers tended to evaluate these aspects together.

* **PC2: Demographics and spending behavior (13.6%)**
  Distinguished variation related to income, age, spending per purchase, and Wi-Fi ratings.

* **PC3: Customer context and store use (8.8%)**
  Reflected differences in employment status, purchasing method, and distance from the store.

The results separated the survey into three broad sources of variation: the core customer experience, demographic and spending characteristics, and situational engagement patterns.

## Analysis Workflow

1. Filtered the life expectancy dataset to observations from 2015.
2. Selected numeric variables and removed fields containing missing values or zero variance.
3. Standardized all retained variables to prevent differences in measurement scale from dominating the analysis.
4. Performed PCA using both `prcomp()` and `FactoMineR::PCA()`.
5. Evaluated eigenvalues and variance explained using scree plots and the Kaiser criterion.
6. Interpreted component loadings, variable contributions, and quality of representation (`cos²`).
7. Visualized observations and variables using PCA biplots, correlation circles, heatmaps, and contribution plots.
8. Compiled the methodology, visualizations, and interpretations into a reproducible R Markdown report.

## Tools and Skills

* **R:** data preparation, standardization, and statistical analysis
* **dplyr:** data filtering and variable selection
* **FactoMineR:** principal component analysis
* **factoextra:** scree plots, biplots, and component-interpretation visualizations
* **corrplot:** visualization of variable representation quality
* **ggplot2:** supporting data visualizations
* **R Markdown:** reproducible analysis and PDF reporting

## Repository Structure

| File                                                                                                                           | Description                                                            |
| ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| [`PCA_Analysis_Grace_Bianchi.Rmd`](./PCA_Analysis_Grace_Bianchi.Rmd)                                                           | R Markdown source containing both PCA case studies                     |
| [`PCA_Analysis_Grace_Bianchi.pdf`](./PCA_Analysis_Grace_Bianchi.pdf)                                                           | Rendered 23-page report with code, visualizations, and interpretations |
| [`Life Expectancy Data (1).csv`](./Life%20Expectancy%20Data%20%281%29.csv)                                                     | Global life expectancy and health-indicator dataset                    |
| [`Starbucks satisfactory survey encode cleaned (1).csv`](./Starbucks%20satisfactory%20survey%20encode%20cleaned%20%281%29.csv) | Encoded Starbucks customer survey dataset                              |

## Data Sources

* **Life Expectancy:** [Life Expectancy (WHO) dataset](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who), containing health and economic indicators collected from the World Health Organization and United Nations.
* **Starbucks Customer Survey:** [Starbucks Customer Survey dataset](https://www.kaggle.com/datasets/mahirahmzh/starbucks-customer-retention-malaysia-survey), containing encoded survey responses about customer demographics, purchasing behavior, and satisfaction.

Copies of both datasets used in the analysis are included in this repository for reproducibility.

## Limitations

* PCA identifies directions of maximum variance but does not establish causal relationships or directly measure predictive importance.
* Principal component signs are mathematically arbitrary; interpretation depends on the relationships among loadings rather than whether a component is labeled positive or negative.
* PCA is sensitive to outliers and assumes that the most important patterns can be represented through linear combinations of the original variables.
* Several Starbucks survey fields are encoded categorical or ordinal variables treated as numeric, so distances and component loadings should be interpreted cautiously.
* The Starbucks survey contains only 113 respondents and may not represent the broader Starbucks customer population.
