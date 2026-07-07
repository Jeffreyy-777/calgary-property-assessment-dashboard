# Calgary Property Assessment Dashboard

An interactive Tableau dashboard exploring property assessment data across Calgary's communities, built using the City of Calgary's open data portal.

🔗 **[View Live Dashboard](https://public.tableau.com/app/profile/jeffrey.jackson6639/viz/Calgary_Property_Assessment_Dashboard/Dashboard1)**

## Dataset

**Source:** [City of Calgary Open Data – Current Year Property Assessments (Parcel)]([https://data.calgary.ca/](https://data.calgary.ca/Government/Current-Year-Property-Assessments-Parcel-/4bsw-nn7w/about_data)  
**Snapshot:** July 6, 2026 (dataset updates daily)  
**Records:** 604,479 properties across Calgary

| Column | Description |
|---|---|
| Assessed Value | Property assessed value in CAD |
| Comm Name | Community name |
| Assessment Class Description | Residential, Non-Residential, or Farm Land |
| Year of Construction | Year the property was built |
| Land Size Sf | Land size in square feet |
| Property Type | Improvement (Land + Building), Land Only, or Improvement Only |

## Dashboard Visuals

### 1. Property Value by Community (Bubble Chart)
Each bubble represents a Calgary community. Bubble size and colour both reflect the average assessed value — larger and warmer = more expensive. Quickly identifies Calgary's wealthiest and most affordable neighbourhoods at a glance.

### 2. Top Residential Communities by Value (Bar Chart)
Horizontal bar chart of the top 20 residential communities ranked by average assessed value, filtered to communities with 500+ properties to remove statistical outliers. Upper Mount Royal, Elbow Park, and University Heights lead the rankings.

### 3. Average Residential Property Value by Decade Built (Area Chart)
Shows how the average assessed value of residential properties varies by the decade they were constructed. Reveals that older inner-city properties (1920s) command premium values, while mid-century suburban builds are lower, with a recovery trend in recent decades.

### 4. Property Value Distribution (Histogram)
Distribution of all Calgary properties across $100K value bins, with an average reference line. Shows that the bulk of Calgary properties are valued between $400K–$700K, with a right-skewed tail of high-value properties.

### 5. Land Size vs Assessed Value (Scatter Plot)
Each dot represents a residential community, plotting average land size (sq ft) against average assessed value. A trend line reveals the relationship — or lack thereof — between lot size and property value in Calgary.

## Key Findings

- **Upper Mount Royal** has the highest average residential assessed value in Calgary
- **The most common property value range** is $500K–$600K
- **1920s-built properties** have the highest average assessed value — likely heritage inner-city homes in desirable neighbourhoods
- **Land size alone does not predict value** — location and community matter more
- **96% of Calgary properties** are classified as Land + Building improvements

## Data Cleaning

Before building the dashboard, the raw dataset was cleaned in Python:

- Stripped commas from `ASSESSED_VALUE` so Tableau could treat it as a number
- Removed `YEAR_OF_CONSTRUCTION` entries before 1900 (data entry errors)
- Mapped `PROPERTY_TYPE` codes to readable labels (`LI` → Improvement, etc.)
- Removed the `MULTIPOLYGON` geometry column to reduce file size
- Added a `DECADE_BUILT` column for the construction timeline visual

Cleaned data script: `clean_data.py`

## Tools

- **Python** (pandas) — data cleaning
- **Tableau Public** — dashboard and visualizations
- **City of Calgary Open Data Portal** — data source

## Files

| File | Description |
|---|---|
| `Calgary_Property_Assessments_Clean.csv` | Cleaned dataset used in Tableau |
| `clean_data.py` | Python script used to clean the raw data |
