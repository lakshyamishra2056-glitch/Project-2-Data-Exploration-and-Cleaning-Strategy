# Project-2-Data-Exploration-and-Cleaning-Strategy
E-Commerce Business Analytics Project

Figuring out who an online store's best customers are, what's actually selling, and where deliveries are hurting its reputation, using Python.

Status: Planning and data-cleaning strategy complete (Weeks 1 and 2). Both documents are in the docs/ folder. Analysis notebooks will be added as each phase is finished.

Week 1: docs/Business_Analytics_Project_Strategy.docx (objectives, scope, timeline, risks)
Week 2: docs/Data_Exploration_and_Cleaning_Strategy.docx (detecting and fixing messy data, with pseudocode)
Why this project

Most small online stores have plenty of order data but only use a sliver of it. They know their monthly revenue, but they usually can't say which customers are slowly drifting away, which categories eat into margins, or why some orders end up with bad reviews.

This project takes public e-commerce data and turns it into answers a business owner could read in five minutes and act on the same week.

Business questions
Customers: Who brings in most of the revenue, and who is at risk of leaving? (RFM segmentation)
Sales trends: How do sales move over time, and are there seasonal patterns?
Products: Which categories drive growth, and which are just taking up space?
Delivery: How much do late deliveries hurt customer review scores?
Regions: Do customers in different states or cities behave differently?
Scope

In scope

Descriptive and diagnostic analysis of historical orders
RFM customer segmentation, with a K-Means check
Sales trend analysis and a simple forecast
Cohort-style retention analysis
Clear charts and a short written summary with recommendations

Out of scope

Real-time dashboards or live data pipelines
Deep learning models
Production deployment
Tech stack
Tool	Used for
Python 3.10+	Main language
Pandas, NumPy	Loading, cleaning, merging and aggregating data
Matplotlib, Seaborn, Plotly	Static and interactive charts
Scikit-learn	Scaling, K-Means clustering, silhouette scores
Statsmodels	Time-series decomposition and forecasting
Jupyter Notebook	Keeping code, output and notes together
Data

All data is public, so no private company records are needed.

Olist Brazilian E-Commerce dataset (Kaggle) is the main source: around 100,000 orders across linked tables for customers, items, payments, reviews, sellers and delivery dates.
UCI Online Retail II is the backup, mainly for cross-checking the RFM approach.
Public holiday calendars help explain seasonal spikes.

Raw data files are not committed to this repo. Download them from the sources above and place them in data/raw/ (see Getting started).

Approach
Understand each table: shapes, types, missing values.
Clean: fix dates, handle duplicates and missing values case by case, review outliers before removing anything, standardise text fields.
Transform: merge tables (checking row counts after every join), then build features such as delivery delay, order value, late-delivery flag and RFM scores.
Explore with no agenda first, so surprises show up early.
Analyse: RFM and clustering, cohort retention, trends and forecast.
Communicate: final charts and plain-language recommendations.
Data exploration and cleaning strategy (Week 2)

Good analysis depends on trustworthy data, so this project has a written plan for dealing with noisy and messy records before any modelling starts. The full detail is in the Week 2 document. In short:

Detecting problems

Missing values: count and percentage per column, a missingness heatmap, and a check for disguised nulls such as "N/A", "unknown" or 9999.
Outliers: IQR rule, z-scores, percentile checks, box plots and business rules (for example, negative quantities or delivery before purchase). Outliers are investigated, not deleted automatically.
Inconsistencies: duplicate rows and keys, near-duplicate category names, bad date formats, and broken links between tables.

Fixing them

Imputation: median for skewed numbers, mean for symmetric ones, mode or "Unknown" for categories, group-wise fills where it makes sense, and a flag column whenever an important field is imputed.
Scaling and transforms: standardisation, robust scaling, log transforms for skewed money columns, binning, and one-hot or frequency encoding.
Text and semi-structured fields: lower-casing, regex extraction, fuzzy matching for messy labels, JSON parsing, and simple tokenisation for reviews.

Working rules

Raw data stays untouched; cleaned data is saved separately.
Profile first, clean second, validate third.
Fit scalers and imputers on training data only, to avoid leakage.
Check row counts and totals after every merge.
Keep a cleaning log of what changed, how many rows were affected, and why.

The document also includes seven pseudocode samples (profiling, missing values, outlier detection, text cleaning, validation, scaling and a full pipeline) that will be turned into working code in the notebooks.

Timeline

About 50 working hours over four weeks.

Phase	Activity	Hours
1	Scoping and environment setup	4
2	Data collection and understanding	5
3	Data cleaning	8
4	Transformation and feature building	6
5	Exploratory data analysis	8
6	Core analysis (RFM, cohorts, trends, forecast)	10
7	Visualisation and insights	5
8	Documentation and review	4
	Total	50
Risks I'm watching
Bad joins can duplicate orders and inflate revenue, so I check totals before and after every merge.
Dataset bias: the data comes from one country and one period, so findings may not generalise. I'll say so clearly in the write-up.
Correlation vs causation: late delivery and bad reviews may share a hidden cause, so I'll word findings carefully.
Scope creep: new ideas go on a "future work" list instead of into the project.
Project structure
.
├── README.md
├── requirements.txt
├── data/
│   ├── raw/             # downloaded datasets (not committed)
│   └── processed/       # cleaned and merged tables
├── notebooks/
│   ├── 01_data_understanding.ipynb
│   ├── 02_cleaning.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_eda.ipynb
│   └── 05_analysis.ipynb
├── reports/
│   ├── figures/         # final charts
│   └── cleaning_log.csv # planned: record of every cleaning decision
└── docs/
    ├── Business_Analytics_Project_Strategy.docx
    └── Data_Exploration_and_Cleaning_Strategy.docx

The notebook files above are the planned layout and will appear as each phase is completed.

Getting started
bash
# 1. Clone the repo
git clone https://github.com/lakshyamishra2056-glitch/<repo-name>.git
cd <repo-name>

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # on Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Download the datasets into data/raw/ (see the Data section)

# 5. Launch Jupyter
jupyter notebook

Suggested requirements.txt:

pandas
numpy
matplotlib
seaborn
plotly
scikit-learn
statsmodels
jupyter
Expected deliverables
Project strategy document (done, Week 1)
Data exploration and cleaning strategy document (done, Week 2)
Well-commented Jupyter notebooks covering cleaning, exploration and analysis
Final visualisations
Short findings report with recommendations
Reproducibility

Random seeds are fixed wherever randomness is involved, and library versions will be recorded so anyone can re-run the notebooks and get the same results.
