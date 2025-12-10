** DRAFT **
# Is healthcare more expensive for men vs women?

## 1. Project Overview

Cisgender men and women interact with the NHS in different ways due to biological, social and behavioural factors. These differences drive distinct healthcare needs, utilisation patterns and overall costs. This project investigates whether men or women incur higher NHS healthcare costs, and explores which conditions and age groups drive these differences.

Using NHS and ONS datasets, we have built a data-driven narrative supported by clear visualisations and analysis in Jupyter Notebook.

### Why this problem matters? 

Analysing cisgender-based cost differences helps to illuminate:
- Differences in healthcare utilisation (including use of private healthcare referrals. providers)
- Variations in risk factors (location, lifestyle, age)
- Potential inequities or unmet needs (help-seeking behavioural patterns in data)
- Areas where one sex faces a greater medical or financial burden.

Understanding these patterns supports better NHS resource planning and service design.

## 2. Research Questions

Do cisgender men or women incur higher overall NHS healthcare costs?

Which conditions, services or procedure categories contribute most to the difference?


## 3. Datasets Used

Our analysis draws on a combination of NHS and ONS datasets, supplemented with additional secondary sources.

### Primary datasets

Hospital Admitted Patient Care Activity 2023–24
Source: NHS Digital
Used for: FCE counts by sex, diagnosis & procedure groups
https://digital.nhs.uk/data-and-information/publications/statistical/hospital-admitted-patient-care-activity/2023-24

General Health by Age, Sex and Deprivation (Census 2021)
Source: ONS
Used for: SES & gender interplay
https://www.ons.gov.uk/.../generalhealthbyagesexanddeprivationenglandandwales/census2021

Patient Level Activity & Costing (2021–22)
Source: NHS England
Used for: cost comparisons across services
https://www.gov.uk/government/statistics/patient-level-activity-and-costing-2021-22

### Secondary datasets

Used as needed to support or contextualise findings:

Prescription Costs — NHS Scotland: https://www.opendata.nhs.scot/dataset/prescriptions-in-the-community

A&E Activity — NHS Scotland: https://www.opendata.nhs.scot/dataset/weekly-accident-and-emergency-activity-and-waiting-times

GP Payments — NHS Scotland: https://www.opendata.nhs.scot/dataset/nhsscotland-payments-to-general-practice/resource/db3455ae-913e-4110-8439-d6a49164f7d9

Healthcare Expenditure — UK Health Accounts (ONS): https://www.ons.gov.uk/peoplepopulationandcommunity/healthandsocialcare/healthcaresystem/bulletins/ukhealthaccounts/2021

Gender & Age breakdown — Acute Patient Activity & Costing: https://digital.nhs.uk/data-and-information/publications/statistical/acute-patient-level-activity-and-costing/2018-19/age-and-gender

## 4. Data Cleaning & Handling of anomalies

Cleaning steps included:

...............

   
## 5.Exploratory Analysis & Visualisation

Click [here](notebooks/Images) for the link to view our visual analysis

## 6. Key findings

.................

## 7. Challenges
### **Challenges Encountered During Data Collection & Preparation**

**Census Health Dataset (ONS – General Health by Sex)** 

The Census dataset presented several formatting and structure challenges:
- The dataset did not begin at row one, requiring manual row-skipping to extract proper headers.
Multiple supplementary sheets (notes, definitions, contents) made it unclear which table to analyse.
- Column naming was inconsistent between sheets and required standardisation.
- Some metadata (e.g. confidence intervals and notes) was included within the data tables, which required filtering.
- The dataset included combined (“Persons”) values which had to be removed to isolate male vs female comparisons.
- Decisions had to be made about whether to include further breakdowns (age, region, deprivation), which were intentionally excluded to keep scope manageable.

 **Fingertips API Dataset (Emergency Hospital Admissions)**

Working with the API presented several technical and structural challenges:
- Direct URL-based API calls frequently return server errors.
- Documentation did not always match the behaviour of the live API.
- Indicator categories were not labelled in an intuitive way, requiring trial-and-error searching.
- Metadata structure required exploration using dir(), help(), and test queries
- Expected categories such as “Healthcare” did not exist in data fields.
- The indicator discovery process involved manual filtering by name keywords.
- Time was not stored as a traditional year and required decoding from sortable values.
- National values were duplicated across geographic levels, requiring de-duplication.



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

_**Supports:** “Women use primary care services more; men under-consult / delay
seeking care.”_

**Ballering et al., 2023 – “Sex and gender differences in primary care help-seeking behaviour”
(Family Practice)** 
https://pmc.ncbi.nlm.nih.gov/articles/PMC10193899
-  Showed that biological sex (being female), more than gender identity/expression,
is associated with higher help-seeking for physical symptoms.

_**Supports:** the idea that sex itself is a strong predictor of using primary care more
often._ 

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

_**Supports:** “Cost burden patterns differ by gender and across the life course.”_ 
Out-of-pocket spending (personal expenses)

**Deloitte Health Equity Institute / YouGov survey – “The women’s health spending gap in the
UK”(2024)** 
https://www.deloitte.com/uk/en/blogs/thoughts-from-the-centre/the-womens-health-spending-gap-in-the-uk.html

- Survey of over 2,500 working adults in the UK.
- Women spent about £100 more per year out of pocket than men (≈50% more).
- Average spend: £305 for women vs £210 for men.
**Women spent:**
- 10% more on diagnostics/wearables
- 25% more on general healthcare & private counselling
- 250% more on fertility/menopause/menstrual health

_**Supports:** “Women bear a higher personal financial burden for health than men.”_

## 10. Contributors (_In no particular order_) 
_Fola Kareem_

_Heather Moorehouse_

_May Agboola_

_Sherelle Garwood_

_Selena Ellis_

_Rhea Strachan_

_Katarzyna Jagiello_






