# Nigeria Health Facilities Analysis
## Focus: Akwa Ibom State
**Author:** Utibeobong Utin  
**Tools:** Python (pandas, matplotlib, seaborn)  
**Dataset:** Nigeria Health Facilities - Humanitarian Data Exchange (HDX)  
**Dataset Size:** 46,146 facilities | 15 columns | Nationwide coverage  

---

## Project Overview

This project analyses the distribution, functionality, and category breakdown 
of health facilities across Nigeria, with a deep-dive focus on Akwa Ibom State. 
The goal is to identify gaps in health facility coverage and flag data quality 
issues, and surface insights that could inform resource allocation decisions 
at the state and LGA level.

---

## Data Source

- **Provider:** Humanitarian Data Exchange (HDX)
- **Dataset:** Nigeria Health Facilities Registry
- **Format:** CSV
- **Last Updated:** 2020
- **URL:** https://data.humdata.org

---

## Data Cleaning Steps

The raw dataset contained several quality issues that were addressed before analysis:

1. **Dropped irrelevant columns** : global_id, ward_code, lga_code, 
   state_code, FID, timestamp, and accessibility were removed. 
   The accessibility column was dropped entirely — 46,129 out of 
   46,146 values were missing (99.9% null).

2. **Standardised text fields** : state_name, lga_name, functional_status, 
   category, and type were stripped of whitespace and converted to 
   consistent title case to eliminate formatting inconsistencies.

3. **Replaced ambiguous values** : "Unknown" strings in functional_status 
   and accessibility were converted to NaN to treat them correctly 
   as missing data rather than a valid category.

4. **Filled remaining nulls** : functional_status nulls were filled 
   with "Unknown" and category nulls (34 rows) were filled 
   with "Unspecified" to preserve all 46,146 facility records.

**Final clean dataset:** 46,146 rows | 7 columns | Zero missing values.

---

## National Findings

### 1. Facility Distribution by State
The top 10 states by facility count account for a disproportionate share 
of Nigeria's total health infrastructure. States in the north-east and 
north-west show both the highest facility counts and the highest rates 
of non-functionality : suggesting quantity without quality of service delivery.

### 2. Functional Status - National Picture
Across all 46,146 facilities nationally:
- A significant proportion are either **Partially Functional** or 
  **Not Functional**
- A large number are recorded as **Unknown** - meaning their operational 
  status was never verified during data collection
- Unknown status is not the same as functional - it represents 
  a **reporting and verification gap** that understates the true 
  burden of non-functional facilities

### 3. Facility Categories
Primary Health Centres dominate Nigeria's health facility landscape, 
consistent with the national primary healthcare policy. However, the 
ratio of PHCs to higher-level facilities (General Hospitals, Specialist 
Hospitals, Teaching Hospitals) raises questions about referral capacity 
and specialist care access across many states.

---

## Akwa Ibom State : Deep Dive

### Overview
- **Total facilities:** 870
- **LGAs covered:** 31
- **Most common facility type:** Primary Health Centre (552 facilities - 63%)

### Finding 1 : Primary care is the backbone, tertiary care is thin
63% of Akwa Ibom's facilities are Primary Health Centres. This aligns 
with national policy but masks a critical gap at the top of the 
referral pyramid:

| Facility Type | Count |
|---|---|
| Primary Health Centre | 552 |
| Dispensary | 144 |
| General Hospital | 17 |
| Specialist Hospital | 23 |
| Teaching Hospital | 1 |

With only **1 Teaching Hospital** and **17 General Hospitals** serving 
a state population of over 5 million, access to specialist and tertiary 
care remains a significant challenge.

### Finding 2 : Functional status looks strong but hides a data gap
- **790 facilities (91%)** are recorded as Functional
- **80 facilities (9%)** are recorded as Unknown

At face value, 91% functionality appears strong. However, the 80 
facilities with Unknown status represent an unverified gap. In health 
data reporting, Unknown does not mean functional : it means no one 
confirmed either way. These facilities require follow-up verification 
before being counted as operational.

**Recommendation:** State health authorities should prioritise 
verification visits to the 80 facilities with Unknown status to 
establish their true operational condition.

### Finding 3 : Significant LGA-level inequality in facility distribution
Facility distribution across Akwa Ibom's 31 LGAs is uneven:

| LGA | Facilities |
|---|---|
| Uyo | 74 |
| Eket | 47 |
| Ikot Ekpene | 41 |
| Eastern Obolo | 15 |
| Udung Uko | 12 |

Uyo - the state capital - has nearly **5 times more facilities** than 
Udung Uko and Eastern Obolo. This gap likely reflects historical 
infrastructure investment patterns favouring urban centres over 
rural and riverine communities.

**Recommendation:** LGAs with fewer than 20 facilities - particularly 
Eastern Obolo, Udung Uko, and Nsit Atai - should be prioritised in 
future facility expansion and rehabilitation planning.

---

## Key Takeaways

1. Nigeria's health facility data has significant quality gaps - 
   particularly in functional status verification - that limit 
   the reliability of national health system assessments.

2. Akwa Ibom performs relatively well on facility functionality 
   but faces structural challenges in tertiary care access and 
   equitable LGA-level distribution.

3. Data-driven decision making at LGA level requires not just 
   counting facilities but verifying their operational status - 
   a gap this analysis highlights clearly.

---

## Tools and Libraries Used

```python
import pandas as pd        # data loading, cleaning, analysis
import numpy as np         # numerical operations
import matplotlib.pyplot   # data visualisation
import seaborn as sns      # statistical visualisation
```

---

## How to Reproduce This Analysis

1. Download the Nigeria Health Facilities dataset from HDX:
   https://data.humdata.org
2. Clone this repository
3. Open `nigeria_health_facilities_analysis.ipynb` in Jupyter Notebook
4. Run all cells in order

---

## Author

**Utibeobong Utin**  
Data Analyst | Health Data | Operations  
[utibeutin.com](https://utibeutin.com)
