# Cambridge Analytica: Analyzing Online Public Reaction and Meta Stock Movements

DSA 210 – Introduction to Data Science (Spring 2025–2026)  
Student: Dicle Ezgi İlhan

---

# Motivation

The Cambridge Analytica scandal became one of the most widely discussed privacy controversies involving Facebook (Meta). After the scandal became public in 2018, online discussions about data privacy, Facebook usage, and digital ethics increased significantly. Many users reacted through searches, discussions, and information-seeking behavior on digital platforms.

I became interested in understanding how these public reactions were reflected in online activity and whether they were associated with Meta’s stock movements during the same period. This project analyzes online behavior indicators such as Google Trends searches and Wikipedia pageviews together with Meta stock price data.

Rather than trying to establish direct causality, the analysis focuses on identifying patterns and associations between public attention indicators and financial market behavior during a major technological controversy.

---

# Data Sources

The analysis combines three publicly available datasets covering the period between 2015 and 2021.

## 1. Google Trends Data

Keywords:
- “delete facebook”
- “facebook privacy”
- “cambridge analytica”

Source: Google Trends  
Collection Tool: pytrends

Methodology:
- Data collected in multiple time windows
- Combined into a single continuous dataset
- Weekly aggregation applied for consistency

Purpose:
Google Trends data was used to represent public attention and behavioral reactions during the scandal period.

---

## 2. Wikipedia Pageview Data

Pages:
- Cambridge_Analytica
- Facebook

Source: Wikimedia REST API  
Frequency: Daily

Collection Method:
- Python requests library
- Wikimedia pageview API

Purpose:
Wikipedia pageviews were used as indicators of public information-seeking behavior.

---

## 3. Meta Stock Price Data

Ticker:
- META

Source: Yahoo Finance  
Collection Tool: yfinance

Frequency:
- Daily closing prices aggregated weekly

Purpose:
Meta stock prices were used to analyze financial market behavior during the scandal timeline.

---

# Data Organization

```text
data/raw/          # Original collected datasets
data/processed/    # Cleaned and merged datasets
notebooks/         # Jupyter notebooks for analysis
figures/           # Generated visualizations
```

---

# Data Analysis Pipeline

## 1. Data Preparation

Several preprocessing steps were applied before analysis:

- Date formats standardized across datasets
- Daily data aggregated into weekly averages
- Missing values checked and handled appropriately
- Multiple datasets merged using the date variable
- Numerical variables normalized using MinMaxScaler

The final merged dataset included:
- Google Trends variables
- Wikipedia pageviews
- Meta weekly stock prices

---

## 2. Exploratory Data Analysis (EDA)

EDA focused on identifying temporal trends and relationships between variables.

The following visualizations were generated:
- Time-series plots
- Correlation heatmaps
- Scatter plots
- Trend comparisons around the scandal timeline

EDA findings showed:
- Significant spikes in Google search activity during 2018
- Increased Wikipedia activity during the scandal period
- Observable fluctuations in Meta stock prices around the same timeline

The analysis suggested that online behavior indicators may contain meaningful signals associated with Meta stock movements.

---

# Hypothesis Testing

Several correlation-based hypotheses were evaluated using Pearson correlation tests.

| Hypothesis | Description |
|---|---|
| H1 | “delete facebook” search interest is associated with Cambridge Analytica Wikipedia activity |
| H2 | “delete facebook” search interest is associated with Facebook Wikipedia activity |
| H3 | “facebook privacy” search interest is associated with Cambridge Analytica Wikipedia activity |
| H4 | “facebook privacy” search interest is associated with Facebook Wikipedia activity |
| H5 | “cambridge analytica” search interest is associated with Cambridge Analytica Wikipedia activity |
| H6 | “delete facebook” search interest is associated with Meta stock price movements |

The tests showed statistically significant relationships between several variables, although correlation strengths varied from weak to moderate.

These findings suggest that online public attention indicators may be associated with financial market reactions during the scandal period.

---

# Machine Learning Models

Four regression models were implemented to predict Meta stock prices using online behavior indicators.

## Model Setup

Features:
- Google Trends variables
- Wikipedia pageview variables

Target Variable:
- Meta weekly stock price

Normalization:
- MinMaxScaler applied before modeling

Train-Test Split:
- 80% training
- 20% testing

Evaluation Metrics:
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

Scatter plots comparing actual and predicted values were also generated for Random Forest and KNN models to visually evaluate predictive performance.

---

# Results

| Model | RMSE | MAE | R² |
|---|---:|---:|---:|
| Linear Regression | 0.2069 | 0.1663 | 0.2799 |
| Random Forest | 0.0739 | 0.0504 | 0.9082 |
| KNN | 0.0812 | 0.0583 | 0.8890 |
| Decision Tree | 0.0676 | 0.0454 | 0.9232 |

Decision Tree achieved the highest R² score on the test set among the evaluated models, while Linear Regression showed weaker predictive performance. Non-linear models such as Random Forest, KNN, and Decision Tree captured relationships within the dataset more effectively than Linear Regression.

Feature importance analysis from the Random Forest model provided additional insight into which search terms and online behavior variables contributed most strongly to the predictions.

Although some models achieved relatively high R² values, predicting stock prices directly remains inherently difficult because financial markets are influenced by many external factors. Therefore, the primary purpose of this analysis is not to claim perfect stock price prediction, but rather to explore which online behavior indicators are most associated with Meta stock movements.

---

# Key Findings

1. **Public attention increased during the scandal**  
   Google Trends data showed clear spikes in searches such as “delete facebook,” “facebook privacy,” and “cambridge analytica” around the scandal period.

2. **Wikipedia activity reflected information-seeking behavior**  
   Wikipedia pageviews for Cambridge Analytica and Facebook increased during the scandal period, showing that users actively searched for more information after the controversy became public.

3. **Online behavior indicators were associated with Meta stock movements**  
   Correlation analysis suggested that some public attention indicators were associated with Meta stock price movements, but these relationships should be interpreted as associations rather than causal effects.

4. **Non-linear models outperformed Linear Regression**  
   Random Forest, KNN, and Decision Tree models performed better than Linear Regression, suggesting that the relationship between online behavior indicators and stock movements may be complex and non-linear.

5. **Stock price prediction remains difficult**  
   Although some models achieved relatively high R² values, predicting stock prices directly remains difficult because financial markets are influenced by many external factors.

---

# Limitations and Future Work

## Limitations

- Financial markets are influenced by many external factors not included in this analysis
- Publicly available datasets may contain limitations regarding granularity
- The project focuses only on one major technology controversy

## Future Improvements

Future work could include:
- sentiment analysis from social media platforms
- additional financial and macroeconomic indicators
- news-based datasets
- advanced time-series models such as LSTM networks
- analysis of additional technology companies and privacy controversies

---

# Setup and Reproducibility

## Requirements

- Python 3.11+
- Dependencies listed in requirements.txt

## Main Libraries Used

- pandas
- numpy
- matplotlib
- seaborn
- scipy
- scikit-learn
- pytrends
- yfinance
- requests

---

# Project Structure

```text
project/
├── data/
│   ├── raw/
│   └── processed/
├── requirements.txt
└── README.md
```

---

# AI Assistance Disclosure

AI tools were used during the project development process to assist with:
- debugging Python code
- explaining programming concepts
- refining interpretations
- improving report structure and wording

All data collection, analysis decisions, hypothesis formulation, and interpretations were reviewed and finalized independently by the student.

---

# Acknowledgments

Data Providers:
- Google Trends
- Wikimedia REST API
- Yahoo Finance

Course:
- DSA 210 – Introduction to Data Science
- Sabancı University
- Spring 2025–2026
