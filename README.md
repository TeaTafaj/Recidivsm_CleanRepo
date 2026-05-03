# Recidivism and Prison Education

This project studies whether prison education programs reduce recidivism using individual-level prison release data from the National Corrections Reporting Program (NCRP). The analysis covers 34 states between 2005 and 2018.

Two questions are examined:
- Did the 2016 Second Chance Pell expansion reduce two-year recidivism in participating states?
- Are states with stronger prison education policies associated with lower recidivism?

---

## Project Structure

```
data_processing/
    01_data_preprocessing.ipynb       cleans and prepares the raw NCRP data
    99_eda.ipynb                     explores the cleaned dataset
regression/
    02_pell_did_regression.ipynb     difference-in-differences analysis
    03_policy_presence_regression.ipynb  policy strength analysis
memo/
    04_ds_memo.ipynb                 policy memo summarizing findings
data/
    raw/          place raw NCRP files here
    processed/    cleaned output is saved here
plots/            output figures
```

---

## Data

The raw data comes from the Bureau of Justice Statistics NCRP. It is not included in this repository due to size and access restrictions.

To request access, visit the ICPSR archive and search for "National Corrections Reporting Program." Place the raw tab-separated file in `data/raw/` before running notebook 01.

---

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

---

## Running the Analysis

Run notebooks in order:

1. `01_data_preprocessing.ipynb`
2. `99_eda.ipynb`
3. `02_pell_did_regression.ipynb`
4. `03_policy_presence_regression.ipynb`
5. `04_ds_memo.ipynb`

Each step depends on the previous one. If preprocessing changes, rerun from step 1.

---

## Key Variables (Codebook-Based)

The dataset follows NCRP (ICPSR 38492) coding conventions. Missing values are encoded numerically and converted to `NaN` during preprocessing.

**ADMTYPE**
- 1 = New court commitment  
- 2 = Parole return / revocation  
- 3 = Other admission  
- 9 = Missing  

**RELTYPE**
- 1 = Conditional release  
- 2 = Unconditional release  
- 3 = Other  
- 9 = Missing  

**RACE**
- 1 = White  
- 2 = Black  
- 3 = Hispanic  
- 4 = Other  
- 9 = Missing  

**AGEADMIT / AGERELEASE**
- 1 = 18–24  
- 2 = 25–34  
- 3 = 35–44  
- 4 = 45–54  
- 5 = 55+  
- 9 = Missing  

**OFFGENERAL**
- 1 = Violent  
- 2 = Property  
- 3 = Drugs  
- 4 = Public order  
- 5 = Other  
- 9 = Missing  

**OFFDETAIL**
- 1–14 = Offense categories  
- 99 = Missing  

**SENTLGTH**
- 0–6 = Sentence categories  
- 9 = Missing  

**TIMESRVD**
- 0–4 = Time served categories  
- 9 = Missing  

**Year variables (ADMITYR, RELEASEYR, etc.)**
- 9999 = Missing  

**Recidivism variable**
- `within_2_yrs = 1` if re-admitted within 2 years of release  
- `within_2_yrs = 0` otherwise  

---

## Findings

The preferred model estimates reduction in recidivism for Pell states after 2016. While this estimate is not statistically significant (p = 0.25), its direction is consistent with existing research suggesting that access to education reduces recidivism.

State policy strength scores as a Total do not show a statistically significant relationship with recidivism across specifications. However, "Incentives" as related to reduction of sentences showed significant results in reduction of recidivism with the highest amongst policies in statistical significance.

---

## Sources

(1) https://crimesolutions.ojp.gov/ratedpractices/corrections-based-vocational-training-programs#7-0  
Evidence on vocational training and recidivism  

(2) https://blackstone.edu/the-history-of-inmate-education/  
Historical background on prison education  

(3) https://www.rand.org/content/dam/rand/pubs/notes/2009/N3454.pdf  
Foundational research linking education to reduced recidivism  

(4) https://www.mackinac.org/s2024-02#central-administration  
Centralized administration of prison education systems  

(5) https://www.jstor.org/stable/23282743?seq=10  
Supporting academic evidence  

(6) https://www.mackinac.org/s2024-05#appendix-a-full-state-scores  
Source for state-level policy scoring  
