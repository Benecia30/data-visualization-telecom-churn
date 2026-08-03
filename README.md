# Data Visualisation — Customer Behaviour in Telecom

Group project for the *Data Visualisation* course, analyzing customer churn patterns in a telecom dataset using R and ggplot2.

**Team (Our Data Vision):** Benecia Dsouza, Greeshma Vishnu, Garima Goel, Alina Batool, Ali Hussnain

## Overview

We explore the [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) dataset (7,043 customers, 21 variables) to understand which demographic, contract, and service factors are associated with customers leaving the company. The project pairs exploratory visualization (bar plots, histograms, box/violin/density plots, heatmaps, faceted grids) with two modeling techniques — logistic regression and K-means clustering with PCA — to answer five research questions.

## Research Questions

1. How do customer demographics and contract types influence spending, and does this vary by churn behavior?
2. How does customer loyalty (tenure) vary across contract and internet service types, and how does this relate to churn?
3. Does having OnlineSecurity and TechSupport affect how long customers stay and how much they spend — and does this change by contract type?
4. Which service combinations contribute most to high Monthly Charges, and how do these "premium" segments behave in terms of tenure and churn?
5. Can we identify distinct customer segments based on service usage patterns (via clustering), and how do these segments differ in churn, loyalty, and spending?

## Key Findings

- **Contract type is the dominant driver** of both tenure and total spending — month-to-month customers churn far more (32–55% depending on internet service) than one- or two-year contract holders (1–9%).
- **Support services help, but mainly on short contracts.** OnlineSecurity and TechSupport are associated with longer tenure and higher spend, but the effect is small once contract length is controlled for.
- **Fiber optic + month-to-month is the highest-risk combination** (55% churn), while two-year contracts are low-risk across all internet service types.
- **"Premium" customers** (avg. charge > $90, 5+ services) generate the most revenue but also show meaningfully higher churn — high revenue correlates with high risk.
- **K-means clustering (k=4)** on service-usage patterns reveals distinct segments: loyal high-spenders, low-cost/low-churn basics, moderate mid-tier users, and a high-churn, low-tenure "new customer" segment (~40% churn).
- A logistic regression (`Churn ~ tenure + Contract + InternetService`) confirms all effects are statistically significant (p < 0.001): longer tenure and longer contracts reduce churn odds, Fiber optic increases them.

## Repository Structure

```
├── data/
│   └── cleaned_customer_data.csv     # Cleaned dataset (11 rows with missing TotalCharges removed)
├── report/
│   ├── Data_Visualization_Telecom.Rmd   # Full R Markdown analysis (reproducible)
│   └── Data_Visualization_Telecom.html  # Rendered report
├── presentation/
│   └── Telecom_Data.pdf              # Project slide deck
└── README.md
```

## Reproducing the Analysis

1. Clone the repo and open `report/Data_Visualization_Telecom.Rmd` in RStudio.
2. Install required packages:
   ```r
   install.packages(c("ggplot2", "dplyr", "stringr", "plotly", "scales", "cluster", "caret", "tidyr"))
   ```
3. Knit the document — it reads `cleaned_customer_data.csv` from the working directory (update the path if you keep the folder structure above, e.g. `read.csv("../data/cleaned_customer_data.csv")`).

## Data Source & References

- Kaggle. (n.d.). *Telco Customer Churn*. https://www.kaggle.com/datasets/blastchar/telco-customer-churn
- Soetewey, A. (2020). *Graphics in R with ggplot2*. https://statsandr.com/blog/graphics-in-r-with-ggplot2/
