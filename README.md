
# Is healthcare more expensive for men vs women?

## 1. Project Overview

Cisgender men and women interact with the NHS in different ways due to biological, social and behavioural factors. These differences drive distinct healthcare needs, utilisation patterns and overall costs. This project investigates whether men or women incur higher NHS healthcare costs, and explores which conditions and age groups drive these differences.

This project presents a data-driven comparison of sex-based healthcare costs in the UK, combining multiple NHS and ONS datasets. Using Python and Jupyter Notebook, we explored how healthcare usage and costs differ between men and women, and which conditions and services drive these differences.


> **Important note:**  
> Due to data availability, this project focuses solely on male and female categories as recorded in NHS and ONS datasets.  
> Trans and non-binary identities are not represented, and this limitation is explicitly acknowledged.


### Why this problem matters? 

Analysing cisgender-based cost differences helps to illuminate:
- Differences in healthcare utilisation (including use of private healthcare referrals. providers)
- Variations in risk factors (location, lifestyle, age)
- Potential inequities or unmet needs (help-seeking behavioural patterns in data)
- Areas where one sex faces a greater medical or financial burden.

Understanding these patterns supports better NHS resource planning and service design.

## 2. Research Questions

1. Do cisgender men or women incur higher overall NHS Healthcare costs?
2. Which conditions, services, or age bands contribute most to these differences?
3. How do utilisation patterns differ (e.g. preventative vs emergency care)?


## 3. Datasets Used

Our analysis draws on a combination of NHS and ONS datasets, supplemented with additional secondary sources.

### <ins>Primary datasets</ins>

*Hospital Admitted Patient Care Activity 2023–24*
Source: NHS Digital
Used for: FCE counts by sex, diagnosis & procedure groups
https://digital.nhs.uk/data-and-information/publications/statistical/hospital-admitted-patient-care-activity/2023-24

*General Health by Age, Sex and Deprivation (Census 2021)*
Source: ONS
Used for: SES & gender interplay
https://www.ons.gov.uk/.../generalhealthbyagesexanddeprivationenglandandwales/census2021

*Patient Level Activity & Costing (2021–22)*
Source: NHS England
Used for: cost comparisons across services
https://www.gov.uk/government/statistics/patient-level-activity-and-costing-2021-22

### <ins>Secondary datasets</ins>

*UK health accounts*
https://www.ons.gov.uk/peoplepopulationandcommunity/healthandsocialcare/healthcaresystem/datasets/healthaccountsreferencetables


*Acute Patient Level Activity and Costing, 2019-20* 

https://digital.nhs.uk/data-and-information/publications/statistical/acute-patient-level-activity-and-costing/2019-20

### API data

*NHS Fingertips API*

https://fingertips.phe.org.uk/profile/guidance/supporting-information/api

## 4. Data Cleaning & Handling of anomalies

Cleaning steps included:

- Removed structural rows that did not represent real observations (e.g. subheadings, section headers, subtotals, and grand total rows) to avoid double-counting.
- Standardised column names, data types, and formats across datasets.
- Converted numeric fields from strings to appropriate numeric types, handling commas, missing values, and formatting inconsistencies.
- Addressed embedded metadata and non-data rows commonly present in public NHS and ONS spreadsheets.
- Created datasets ready for analysis and focused on comparable units.



   
## 5.Exploratory Analysis & Visualisation

Visualisations were created using Matplotlib and Seaborn, focusing on clarity and narrative insight. These include:

- Total estimated healthcare costs by sex
- Diagnosis counts by sex
- Procedure volumes by sex
- Comparisons across service categories

Click [here](notebooks/Images) for the link to view our visuals produced during analysis

### Development and Coding tools
- Python
- Jupyter Notebooks

### Libraries Used
The following libraries and modules require installation
- Pandas `!pip install pandas`
- Numpy `!pip install numpy`
- Matplotlib `!pip install matplotlib`
- Seaborn `!pip install seaborn`
- Fingertips `!pip install fingertips_py`

## 6. Key findings

The evidence appeared to have consistently indicated that:
- Women utilised hospital services more than men
- Women received higher diagnosis counts in most categories
- Estimated hospital expenditure calculated using sex proportions suggested women incur greater total cost. Population size alone did not explain the difference
- Overall healthcare costs are rising, which may increase the cost disparity

## 7. Challenges
### **Challenges Encountered During Data Collection & Preparation**

The datasets presented several formatting and structural issues:

- NHS dataset contained non-data rows
- Multiple sections included subtotal rows (not labelled “Total”), which inflated male/female counts when summed.
- The datasets often included a grand total row which needed to be isolated.
- Mixed formatting in numeric fields. Some columns like included: commas, decimals stored as strings, NaN values.
- Structural inconsistencies in Excel formatting
- Missing values and inconsistencies
- Datasets covering the same themes from different years had different formatting in headers and columns, as well as not including data from all the same healthcare areas.
- Data was categorical and already aggregated. 


 **Fingertips API Dataset (Emergency Hospital Admissions)**

Working with the API presented several technical and structural challenges:
- Direct URL queries often returned server errors.
- Documentation did not consistently match live API behaviour.
- Poorly labelled indicator categories required trial-and-error exploration.
- Metadata structure needed investigation using dir(), help(), and test queries.
- Expected fields (e.g., “Healthcare”) were not present.
- Indicator discovery relied on manual keyword filtering.
- Time values were encoded rather than conventional years and needed decoding.
- National data was duplicated across geographic levels, requiring de-duplication.



## 8. Conclusion
Overall, our findings indicate that women contribute a disproportionately higher share of NHS healthcare costs compared to men. This appears largely driven by gender-specific health needs, particularly those associated with reproductive health, maternity, and age-related conditions such as menopause. These results are consistent with the diagnostic data, which shows significantly higher treatment volumes for gynaecological and maternity-related issues among women.

In contrast, men tend to incur higher costs in diagnostic categories typically associated with male-dominant health risks, such as cardiovascular diseases. Furthermore, our analysis of diagnosis frequency by gender reveals that women seek medical support more often than men, leading to a higher number of recorded diagnoses. This aligns with existing literature suggesting that women are generally more proactive in seeking healthcare intervention, while men may delay medical consultation.

Taken together, these findings highlight notable gender differences in both healthcare utilisation and the resulting cost implications across the NHS.
## 9. References
###  Who uses healthcare more – men or women?
**Wang et al., 2013 – “Do men consult less than women?” (BMJ Open)** 
https://bmjopen.bmj.com/content/3/8/e003320?
- Used routinely collected UK GP data.
- Found that men’s consultation rates were about 32% lower than women’s
overall, even after adjusting for some health needs.


**Ballering et al., 2023 – “Sex and gender differences in primary care help-seeking behaviour”
(Family Practice)** 
https://pmc.ncbi.nlm.nih.gov/articles/PMC10193899
-  Showed that biological sex (being female), more than gender identity/expression,
is associated with higher help-seeking for physical symptoms.



### Costs & economic side (who pays more / costs more?)
NHS hospital costs by sex and age
NHS Digital, “Acute patient level activity and costing 2018–19: Age and gender” 
https://digital.nhs.uk/data-and-information/publications/statistical/acute-patient-level-activity-and-costing/2018-19/age-and-gender
- Breaks down NHS A&E and inpatient costs by age and gender.
Shows that:
- Under 15: higher costs for males

- Ages 15–39 and 80+: higher costs for females
-  Overall, women account for a slightly greater share of admitted-patient costs,
partly due to maternity-related care.




## 10. Contributors (_In no particular order_) 
_Fola Kareem_

_Heather Moorhouse_

_May Agboola_

_Sherelle Garwood_

_Selena Ellis_

_Rhea Strachan_

_Katarzyna Jagiello_






