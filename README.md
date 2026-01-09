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
8. [Skills Demonstrated](#skills-demonstrated)

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

📸 **Screenshot:** Initial Power Query load & applied steps pane

---

### 5.2 Salary Extraction & Transformation

The Salary Estimate column contained salary ranges in text format.

**Steps taken:**
- Used **Column from Examples** to extract:
  - Minimum Salary
  - Maximum Salary
- Converted salary fields to Currency
- Multiplied values by 1,000 to reflect actual salaries

📸 **Screenshot:** Column from Examples extracting Min & Max Salary

---

### 5.3 Role Type Classification

Job titles were standardized into broader role categories using a custom column.

**Role Groups:**
- Data Scientist
- Data Analyst
- Data Engineer
- Machine Learning Engineer
- Other

📸 **Screenshot:** Custom column IF/ELSE logic for Role Type

---

### 5.4 Location Standardization

- Extracted State names and abbreviations from Location
- Resolved inconsistencies (e.g., “Anne Arundel, MD”)
- Applied TRIM to remove trailing spaces
- Merged with a state-mapping table to retrieve full state names

📸 **Screenshots:**  
- Text extraction before delimiter  
- TRIM operation  
- Merge Queries window  

---

### 5.5 Company Name & Rating Separation

Company name and rating were stored in a single column.

**Steps performed:**
1. Calculated the average company rating (3.9)
2. Replaced missing ratings with the average
3. Split the column using **Line Feed (#(lf))**
4. Created separate Company Name and Company Rating columns

📸 **Screenshot:** Split Column by Special Character (Line Feed)

---

### 5.6 Company Size Standardization

Company size was stored as text ranges.

**Steps taken:**
- Standardized text values (e.g., “501 to 1000” → “501-1000”)
- Split size into Min and Max employee counts
- Created a custom column to compute average employee count per company

**Custom Logic:**

If Max = null then Min
Else (Min + Max) / 2

📸 **Screenshot to include:**
- [cite_start]Size split & employee count average calculation [cite: 136]

---

### 5.7 Revenue Column Transformation
[cite_start]The Revenue column contained highly inconsistent text-based ranges[cite: 138].

[cite_start]**Step 1: Clean Text Noise** [cite: 139]
- [cite_start]Removed $, USD, and irrelevant text [cite: 140]
- [cite_start]Replaced "Unknown/Non-Applicable" with null [cite: 143]
- [cite_start]Replaced "Less than 1 million" → 0 to 1 million [cite: 144]
- [cite_start]Replaced "10+ billion" → 10 to 11 billion [cite: 146]

[cite_start]**Step 2: Split Revenue Ranges** [cite: 147]
- [cite_start]Split column by delimiter " to " [cite: 148]
- [cite_start]Created lower and upper revenue bounds [cite: 149]

[cite_start]**Step 3: Normalize Units** [cite: 150]
- [cite_start]Converted millions and billions into numeric multipliers (1,000,000 and 1,000,000,000) [cite: 151-155]

[cite_start]**Step 4: Final Revenue Calculation** [cite: 156]
- [cite_start]Used custom columns to compute numeric revenue values [cite: 157]
- [cite_start]Standardized all revenue figures into comparable numeric form [cite: 158]

[cite_start]📸 **Screenshots to include:** - Revenue value replacements [cite: 160]
- [cite_start]Revenue range split [cite: 161]
- [cite_start]Custom column calculations [cite: 162]

---

## Exploratory Data Analysis (EDA)

### 6.1 Salary by Role Type
- [cite_start]Grouped by Role Type [cite: 165]
- [cite_start]Calculated count, average minimum salary, and average maximum salary [cite: 166]
- [cite_start]Sorted by average maximum salary (DESC) [cite: 167]

[cite_start]📸 **Screenshot to include:** - Salary by Role Type output [cite: 168]

### 6.2 Salary by Company Size
- [cite_start]Grouped salaries by company size [cite: 170]
- [cite_start]Compared compensation trends across firm sizes [cite: 171]

[cite_start]📸 **Screenshot to include:** - Salary by Company Size output [cite: 172]

### 6.3 Salary by State
- [cite_start]Grouped by full state name [cite: 174]
- [cite_start]Identified top-paying locations [cite: 175]

[cite_start]📸 **Screenshot to include:** - Salary by State output [cite: 176]

### 6.4 Salary by Role Type & Company Size
- [cite_start]Multi-dimensional grouping [cite: 178]
- [cite_start]Revealed how compensation scales by role and organization size [cite: 179]

[cite_start]📸 **Screenshot to include:** - Role Type vs Company Size output [cite: 180]

---

## Key Insights
- [cite_start]**Machine Learning and Data Engineering** roles command the highest salaries[cite: 182].
- [cite_start]**Larger firms** tend to offer higher compensation[cite: 183].
- [cite_start]**Location** plays a significant role in salary variation[cite: 184].
- [cite_start]Robust data cleaning **materially improves insight quality**[cite: 185].

---

## Skills Demonstrated
- [cite_start]Advanced Excel Power Query [cite: 187]
- [cite_start]Data cleaning & transformation [cite: 188]
- [cite_start]Feature engineering [cite: 189]
- [cite_start]Conditional logic & custom columns [cite: 190]
- [cite_start]Salary analytics & EDA [cite: 191]
- [cite_start]Business-focused data storytelling [cite: 192]

---

## How to Reproduce This Project
1. [cite_start]Download the raw dataset from **Kaggle.com**[cite: 34].
2. [cite_start]Load the data into **Microsoft Excel**[cite: 38].
3. [cite_start]Open **Power Query Editor** and apply the transformation steps detailed in Section 5[cite: 77].
4. [cite_start]Use the engineered columns to generate the EDA outputs shown in Section 6[cite: 163].
