# Excel Power Query Data Cleaning & Exploratory Data Analysis  
## Salary Insights from a Messy Kaggle Dataset

**Author:** Jonathan Apwoka  
**Tools:** Microsoft Excel, Power Query, DAX (Power Query Custom Columns)  
**Data Source:** Kaggle.com  
**Focus Areas:** Data Cleaning, Feature Engineering, Salary Analysis, EDA

---

## 📌 Table of Contents
1. [Project Context](#project-context)
2. [Problem Statement](#problem-statement)
3. [Dataset Overview](#dataset-overview)
4. [Project Objectives](#project-objectives)
5. [Data Cleaning & Transformation Workflow](#data-cleaning--transformation-workflow)
   - 5.1 [Initial Data Preparation](#51-initial-data-preparation)
   - 5.2 [Salary Extraction & Transformation](#52-salary-extraction--transformation)
   - 5.3 [Role Type Classification](#53-role-type-classification)
   - 5.4 [Location Standardization](#54-location-standardization)
   - 5.5 [Company Name & Rating Separation](#55-company-name--rating-separation)
   - 5.6 [Company Size Standardization](#56-company-size-standardization)
   - 5.7 [Revenue Column Transformation](#57-revenue-column-transformation)
6. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
   - 6.1 [Salary by Role Type](#61-salary-by-role-type)
   - 6.2 [Salary by Company Size](#62-salary-by-company-size)
   - 6.3 [Salary by State](#63-salary-by-state)
   - 6.4 [Salary by Role Type & Company Size](#64-salary-by-role-type--company-size)
7. [Key Insights](#key-insights)
8. [Strategic Business Recommendations](#strategic-business-recommendations)
9. [Skills Demonstrated](#skills-demonstrated)

---

## Project Context

Publicly available salary datasets are often highly unstructured, making direct analysis unreliable.  
This project demonstrates how **Excel Power Query** can be used as a **robust data transformation and analytics tool** to clean, standardize, and analyze messy real-world data.

The workflow mirrors real tasks performed in:
- Finance Operations
- Business Intelligence
- HR Analytics
- Data & Financial Analysis roles

---

## Problem Statement

The raw dataset sourced from Kaggle contained:
- Inconsistent salary formats stored as text
- Combined fields (company name and rating)
- Messy revenue ranges
- Non-standardized company sizes
- Inconsistent job titles and locations

**Objective:**  
Transform the unclean dataset into a structured, analysis-ready model and extract actionable salary insights using **Power Query only**.

---

## Dataset Overview

- **Source:** Kaggle.com  
- **Format:** Excel (.xlsx)  
- **Primary Columns Used:**
  - Job Title
  - Salary Estimate
  - Location
  - Company Size
  - Revenue
  - Company Name
  - Company Rating

The Job Description column was removed as it was not relevant to salary analysis.

---

## Project Objectives

- Clean and standardize text-based numeric fields
- Engineer new analytical features (salary bounds, role groups, employee counts)
- Normalize revenue and company size data
- Perform salary-focused EDA
- Demonstrate professional Power Query workflows

---

## Data Cleaning & Transformation Workflow

### 5.1 Initial Data Preparation

- Removed non-essential columns (Job Description)
- Checked for duplicate records (none found)
- Sorted index column for data traceability

---

### 5.2 Salary Extraction & Transformation

The Salary Estimate column contained salary ranges in text format.

**Steps taken:**
- Used **Column from Examples** to extract:
  - Minimum Salary
  - Maximum Salary
- Converted salary fields to Currency
- Multiplied values by 1,000 to reflect actual salaries

---

### 5.3 Role Type Classification

Job titles were standardized into broader role categories using a custom column.

**Role Groups:**
- Data Scientist
- Data Analyst
- Data Engineer
- Machine Learning Engineer
- Other

Custom column IF/ELSE logic for Role Type;

<img width="1920" height="1020" alt="Screenshot 2026-01-10 024352" src="https://github.com/user-attachments/assets/e7d08a56-c91c-4164-8c27-07a2a2fe6dbe" />


---

### 5.4 Location Standardization

- Extracted State names and abbreviations from Location using; text extraction before & after delimiter
- Resolved inconsistencies (e.g. “Anne Arundel, MD”)
- Applied TRIM to remove trailing spaces
- Merged with a state-mapping table to retrieve full state names

Merge Queries window;

<img width="877" height="790" alt="Screenshot 2026-01-09 213044" src="https://github.com/user-attachments/assets/8786f14d-b032-454c-8682-c0615b3ef946" />


---

### 5.5 Company Name & Rating Separation

Company name and rating were stored in a single column.

**Steps performed:**
1. Calculated the average company rating (3.9)
2. Replaced missing ratings with the average
3. Split the column using **Line Feed (#(lf))**
4. Created separate Company Name and Company Rating columns

Split Column by Special Character (Line Feed);

<img width="877" height="728" alt="Screenshot 2026-01-09 191537" src="https://github.com/user-attachments/assets/694d3f3d-9a38-43a3-a456-52737437f859" />

---

### 5.6 Company Size Standardization

Company size was stored as text ranges.

**Steps taken:**
- Standardized text values (e.g. “501 to 1000” → “501-1000”)
- Split size into Min and Max employee counts
- Created a custom column to compute average employee count per company

Custom Logic;

<img width="877" height="551" alt="image" src="https://github.com/user-attachments/assets/403c1baf-e985-482d-ba88-ec69e02d7f21" />

---

### 5.7 Revenue Column Transformation
The Revenue column contained highly inconsistent text-based ranges.

**Step 1: Clean Text Noise**
- Removed $, USD and irrelevant text
- Replaced "Unknown/Non-Applicable" with null
- Replaced "Less than 1 million" → 0 to 1 million
- Replaced "10+ billion" → 10 to 11 billion 

**Step 2: Split Revenue Ranges**
- Split column by delimiter " to "
- Created lower and upper revenue bounds

**Step 3: Normalize Units**
- Converted millions and billions into numeric multipliers (1,000,000 and 1,000,000,000)

**Step 4: Final Revenue Calculation**
- Used custom columns to compute numeric revenue values
- Standardized all revenue figures into comparable numeric form

Revenue range split & replacements;

<img width="1158" height="570" alt="Screenshot 2026-01-09 203631" src="https://github.com/user-attachments/assets/05bd56b7-34a7-460c-871e-5bdd52535363" />

Custom column calculations;

<img width="877" height="551" alt="Screenshot 2026-01-09 204100" src="https://github.com/user-attachments/assets/623e5324-1e4b-45b4-8c64-bad6264657e7" />

---

## Exploratory Data Analysis (EDA)

### 6.1 Salary by Role Type
- Grouped by Role Type
- Calculated count, average minimum salary and average maximum salary
- Sorted by average maximum salary (DESC)

Salary by Role Type Group By Step;

<img width="877" height="663" alt="Screenshot 2026-01-09 052605" src="https://github.com/user-attachments/assets/20442e0e-2a59-466c-8676-1fd3f02c0308" />

Salary by Role Type output;

<img width="1920" height="1020" alt="Screenshot 2026-01-09 211544" src="https://github.com/user-attachments/assets/d45300db-b1e9-4e47-bfb1-b1741e0559ea" />

### 6.2 Salary by Company Size
- Grouped salaries by company size
- Compared compensation trends across firm sizes

Salary by Company Size output;

<img width="1920" height="1020" alt="Screenshot 2026-01-09 212516" src="https://github.com/user-attachments/assets/b6da2bb2-71f4-4fb9-8393-fcfcb3cf921f" />

### 6.3 Salary by State
- Grouped by full state name
- Identified top-paying locations

Salary by State output;

<img width="1920" height="1020" alt="Screenshot 2026-01-09 213648" src="https://github.com/user-attachments/assets/25ae6cf5-7e40-421e-83cf-c0c920f1d3db" />

### 6.4 Salary by Role Type & Company Size
- Multi-dimensional grouping
- Revealed how compensation scales by role and organization size 

Role Type vs Company Size output;

<img width="1920" height="1020" alt="Screenshot 2026-01-09 214802" src="https://github.com/user-attachments/assets/df944d35-a2b0-4693-a57e-dfa5aa4c82df" />

---

## 8. Key Insights

* **High-Growth Domain Premiums:** Identified **Data Engineering** and **Machine Learning** as the highest-compensated roles, with average maximum salaries reaching **$150,791** and **$130,923** respectively, reflecting intense market demand for specialized technical talent.
* **Corporate Scale Correlation:** Established a direct link between firm size and compensation ceilings. Large-scale firms (100+ employees) offer a **7.2% salary premium** ($152,085 avg. max) compared to mid-sized firms with ~80 staff ($141,862 avg. max).
* **Geospatial Compensation Variance:** Discovered significant regional outliers; state-cities such as **Fort Sam Houston, Wilmington, and Pleasanton** command top-tier compensation packages with average maximums of **$331,000** and lower bounds starting at **$212,000**.
* **ETL Value Proposition:** Demonstrated that implementing a robust, automated cleaning pipeline in Power Query materially reduced data noise, improving the reliability of salary benchmarks by eliminating duplicate entries and standardized fragmented job titles.

---

## 9. Strategic Business Recommendations

* **Talent Acquisition Strategy:** Prioritize aggressive recruitment and retention budgets for **Machine Learning and Data Engineering** roles to remain competitive in a high-demand labor market.
* **Corporate Benchmarking:** Larger organizations should leverage these scale-based insights to calibrate their compensation tiers, ensuring they maintain their competitive edge against other 100+ employee firms.
* **Agile Incentives for SMEs:** Smaller firms can mitigate lower salary bands by differentiating their employer brand with non-monetary incentives such as remote flexibility and rapid career-growth pathways.
* **Regional Pay Modeling:** Implement localized salary structures that account for identified geospatial disparities (e.g., $331k peaks) to ensure regional fairness and prevent "talent flight" to higher-paying hubs.
* **ETL Automation:** Standardize the use of the developed **Power Query M-Language script** across HR departments to ensure that all future salary data ingestion is accurate, reproducible, and ready for immediate analysis.

---

## Skills Demonstrated
- Advanced Excel Power Query
- Data cleaning & transformation
- Feature engineering
- Conditional logic & custom columns
- Salary analytics & EDA
- Business-focused data storytelling
