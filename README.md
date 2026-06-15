# Is Healthcare More Expensive for Men vs Women? 🏥

A data-driven analysis of sex-based NHS healthcare costs in England, combining multiple NHS and ONS datasets with REST API integration and a full ETL pipeline built in Python.

---

## Project Notes 🗒️ ‼️

- All datasets are **real, publicly available NHS and ONS data** — no mock data was used.
- **_Raw source files arrived with embedded metadata rows, merged cell headers, subtotals, and mixed-type numeric fields; a significant portion of this project was engineering those into analysis-ready datasets before any insight could be extracted._**
- This project demonstrates: **multi-source ETL**, **raw Excel parsing** with `openpyxl`, **structural data repair** (stripping non-data rows, reconstructing offset headers, handling merged cells), **wide-to-long reshaping** with `pd.melt`, **ICD-10 code categorisation**, **REST API integration** via the NHS Fingertips API, and **data visualisation** with `matplotlib` and `seaborn`.

---

## Project Notebooks 📓

| Notebook | Purpose |
|---------|---------|
| `01-cleaning-reprocessing-notebook.ipynb` | Cleans raw NHS/ONS datasets and saves outputs into the `data/clean/` directory |
| `02-fingertips-api-notebook.ipynb` | Retrieves, filters, and processes API data via the NHS Fingertips API |
| `03-analysis-visualisation-notebook.ipynb` | Runs the final analysis, merges datasets, and generates all visualisations |

---

## Overview 🔍

Cisgender men and women interact with the NHS in different ways due to biological, social, and behavioural factors. This project investigates whether men or women incur higher NHS healthcare costs, and explores which conditions and age groups drive these differences.

> **Important note:** Due to data availability, this project focuses solely on male and female categories as recorded in NHS and ONS datasets. Trans and non-binary identities are not represented in the source data, and this limitation is explicitly acknowledged.

### Research Questions ❓

1. Do cisgender men or women incur higher overall NHS healthcare costs?
2. Which conditions, services, or age bands contribute most to these differences?
3. How do utilisation patterns differ (e.g. preventative vs emergency care)?

---

## Datasets Used 📊

### Primary Datasets

| Dataset | Source | Used For |
|--------|--------|---------|
| Hospital Admitted Patient Care Activity 2023–24 | NHS Digital | FCE counts by sex, diagnosis & procedure groups |
| General Health by Age, Sex and Deprivation (Census 2021) | ONS | SES & gender interplay |
| Patient Level Activity & Costing 2021–22 | NHS England | Cost comparisons across services |

### Secondary Datasets

- UK Health Accounts — ONS
- Acute Patient Level Activity and Costing 2019–20 — NHS Digital

### API Data 📊

- NHS Fingertips API — emergency hospital admissions by sex and geography

---

## Data Cleaning & Engineering

Each source arrived in a different state of messiness. Key engineering work included:

- **Identifying and skipping non-data rows embedded** in NHS Excel files — section headers, subheadings, subtotal rows, and grand totals all had to be stripped without losing real records
- **Manually reconstructing** column headers from merged cells and offset header rows (true headers living at row index 8 or 9 rather than row 0)
- **Standardising** column names across all datasets to consistent `snake_case`
- **Converting** numeric fields stored as comma-formatted strings or mixed types using `pd.to_numeric` with `errors='coerce'`
- **Replacing** embedded metadata tokens (e.g. `[x]`, `[note_10]`) with `NaN` for safe downstream handling
- **Reshaping** wide-format NHS tables into tidy long format using `pd.melt`
- **Mapping** ICD-10 diagnosis codes to standardised clinical categories via a manually constructed lookup dictionary, handling the `D` code range ambiguity (which spans two distinct disease groups depending on the second character)
- **Decoding** non-standard sortable time values from the Fingertips API into calendar years
- **De-duplicating national-level records** repeated across geographic levels in the API response

---

## Key Findings 🧐

The evidence consistently indicated that:

- **_Women utilised hospital services more than men_**
- **_Women received higher diagnosis counts in most categories_**
- Estimated hospital expenditure (calculated using sex proportions) suggested **_women incur greater total cost_** — _population size alone did not explain the differences_
- **_Overall_** _healthcare costs are rising_, which **may increase the cost disparity over time**

**_Women's higher utilisation appears largely driven by reproductive health, maternity, and age-related conditions_**. Men, by contrast, incur higher relative costs in categories associated with cardiovascular disease. Women also sought medical support more frequently than men, resulting in a higher number of recorded diagnoses — consistent with existing literature on gender differences in help-seeking behaviour.

---

## Visualisations 📊

Charts were produced using Matplotlib and Seaborn in JupyterNotebook including:

- Total estimated healthcare costs by sex
- Diagnosis counts and procedure volumes by sex
- Self-rated health distribution by sex (2011 vs 2021)
- Emergency admissions trend over time by sex
- Female share of FCEs by ethnic group

---

## How to Run 🛠️

1. Clone the repository
2. Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn openpyxl fingertips_py
```

3. Run notebooks in order: `01` → `02` → `03`

Raw data files should be placed in `data/raw/`. Cleaned outputs are written to `data/clean/`.

---

## References

- Wang et al., 2013 — "Do men consult less than women?" (BMJ Open) https://bmjopen.bmj.com/content/3/8/e003320
- Ballering et al., 2023 — "Sex and gender differences in primary care help-seeking behaviour" (Family Practice) https://pmc.ncbi.nlm.nih.gov/articles/PMC10193899
- NHS Digital — Acute patient level activity and costing 2018–19: Age and gender https://digital.nhs.uk/data-and-information/publications/statistical/acute-patient-level-activity-and-costing/2018-19/age-and-gender

---

## Contributors _(in no particular order)_

Fola Kareem · Heather Moorhouse · May Agboola · Sherelle Garwood · Selena Ellis · Rhea Strachan · Katarzyna Jagiello
