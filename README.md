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
- Size split & employee count average calculation

---

### 5.7 Revenue Column Transformation
The Revenue column contained highly inconsistent text-based ranges.

**Step 1: Clean Text Noise**
- Removed $, USD, and irrelevant text
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

📸 **Screenshots to include:** - Revenue value replacements 
- Revenue range split
- Custom column calculations

---

## Exploratory Data Analysis (EDA)

### 6.1 Salary by Role Type
- Grouped by Role Type
- Calculated count, average minimum salary, and average maximum salary
- Sorted by average maximum salary (DESC)

📸 **Screenshot to include:** - Salary by Role Type output

### 6.2 Salary by Company Size
- Grouped salaries by company size
- Compared compensation trends across firm sizes

📸 **Screenshot to include:** - Salary by Company Size output

### 6.3 Salary by State
- Grouped by full state name
- Identified top-paying locations

📸 **Screenshot to include:** - Salary by State output

### 6.4 Salary by Role Type & Company Size
- Multi-dimensional grouping
- Revealed how compensation scales by role and organization size 

📸 **Screenshot to include:** - Role Type vs Company Size output

---

## Key Insights
- **Machine Learning and Data Engineering** roles command the highest salaries.
- **Larger firms** tend to offer higher compensation.
- **Location** plays a significant role in salary variation.
- Robust data cleaning **materially improves insight quality**.

---

## Skills Demonstrated
- Advanced Excel Power Query
- Data cleaning & transformation
- Feature engineering
- Conditional logic & custom columns
- Salary analytics & EDA
- Business-focused data storytelling

---

## How to Reproduce This Project
1. Download the raw dataset from **Kaggle.com**.
2. Load the data into **Microsoft Excel**.
3. Open **Power Query Editor** and apply the transformation steps detailed in Section 5
4. Use the engineered columns to generate the EDA outputs shown in Section 6.
