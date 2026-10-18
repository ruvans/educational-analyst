# Analysis Approach
**Author**: Ruth Evans
**Project**: International students in university
**Dataset**: timesData.csv from https://www.kaggle.com/code/mylesoneill/australian-university-comparison/input



## 1. Objective
The objective of this analysis is to conduct an exploratory data analysis of universities worldwide, with a focus on identifying patterns related to university details and international student populations.


## 2. Dataset Overview
- **Source File:** timesData.csv
- **Records:**
2603
- **Time Period:**
2011-2016
- **Key Variables:**
    - university_name
    - country
    - international
    - total_score
    - num_students 
    - international_students
    - year

## 3. Analysis Workflow
### Step 1:  Data load ###
The CSV data was imported into Microsoft Excel.

### Step 2: Initial Data Exploration ###
- Examined the first few rows in Excel to identify the data.
- Imported the data into PowerQuery to identify the range of the Year column and analyse how many columns had missing data.

### Step 3: Eliminating data ###
Removed extraneous columns: world_rank, teaching, research, citations, income, student_staff_Ratio, female_male_ratio, international.

### Step 4: Renaming ###
Renamed international_students to international_students_percentage

### Step 4: Data type conversion ###
- Converted the international percentage column from text to decimal number then removed rows that were non compliant.
- Converted international_students_percentage from decimal to percentage data type

### Step 5: Missing Value Handling ###
- 2% of num_students rows were empty, these were filtered out.
- Some values in the total_score column were filled in with "-" instead of a number value, these rows were removed.

### Step 6: Generate new columns ###
- num_international_students column created using the following m-code, then rounded to the nearest integer and data type set to whole number.
> [num_students]*[international_students_percentage]


Full Power Query m-code saved in Docs\data_cleaning_m_code.txt

## Data Exploration ## 
Created pivot table to explore data and find patterns.

**Key findings:**
- Amount of international students increases each year
- Amount of total students does not change much each year
- Top three countries for international students are USA, UK, and Germany.
- Noticed a possible correlation between university scores and the percentage of international students, Used the PEARSON excel function to generate an R value for the two columns of 0.652719057, proving a moderate but not strong correlation.
