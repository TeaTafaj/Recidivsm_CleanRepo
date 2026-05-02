# Recidivism and Prison Education

This project studies whether prison education programs reduce recidivism. It uses individual-level prison release data from the National Corrections Reporting Program (NCRP) covering 34 states from 2005 to 2018.

Two questions are examined. Did the 2016 Second Chance Pell expansion reduce two-year recidivism in participating states? Are states with stronger prison education policies associated with lower recidivism?

## Project Structure

```
data_processing/
    01_data_preprocessing.ipynb       cleans and prepares the raw NCRP data
    99_eda.ipynb                       explores the cleaned dataset
regression/
    02_pell_did_regression.ipynb       difference-in-differences analysis
    03_policy_presence_regression.ipynb  policy strength analysis
memo/
    04_ds_memo.ipynb                   policy memo summarizing findings
data/
    raw/          place raw NCRP files here
    processed/    cleaned output is saved here
plots/            output figures
```

## Data

The raw data comes from the Bureau of Justice Statistics NCRP. It is not included in this repository because of its size and access restrictions.

To request access, visit the ICPSR data archive and search for "National Corrections Reporting Program." Place the raw tab-separated file in `data/raw/` before running notebook 01.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Running the Analysis

Run the notebooks in this order.

1. `01_data_preprocessing.ipynb` builds the cleaned dataset
2. `99_eda.ipynb` explores the cleaned data
3. `02_pell_did_regression.ipynb` runs the difference-in-differences analysis
4. `03_policy_presence_regression.ipynb` runs the policy strength analysis
5. `04_ds_memo.ipynb` contains the policy memo

Each notebook reads from the output of the previous step. If you change the preprocessing notebook, start from step 1.

## Findings

The preferred model estimates a 2.4 percentage point reduction in recidivism for Pell states after 2016. This estimate is not statistically significant (p = 0.25). State policy strength scores show no significant association with recidivism across any model specification.
