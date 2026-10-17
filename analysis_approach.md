# Analysis Approach
**Author**: Ruth Evans
**Project**: International students in university
**Datasets**: 
- timesData.csv
- cwurData.csv


## 1. Objective
The objective of this analysis is to conduct an exploratory data analysis of universities worldwide, with a focus on identifying patterns related to university details and international student populations.


## 2. Dataset Overview
- **Source File:** timesData.csv
- **Records:**
2603
- **Time Period:**
todo
- **Key Variables:**
todo

## 3. Analysis Workflow
### Step 1:  Data load ###
The data was loaded into Microsoft Excel

### Step 2: Initial Data Exploration ###
- Examined the first few rows in Excel to identify the data.
- Imported the data into PowerQuery to identify the range of the Year column and analyse how many columns had missing data.

### Step 3: Eliminating data ###
Removed extraneous columns: world_rank, teaching, research, citations, income, student_staff_Ratio, female_male_ratio.

### Step 4: Data type conversion ###
Converted the international percentage column from text to decimal number then removed rows that were non compliant.

### Step 4: Missing Value Handling ###
- 2% of num_students rows were empty, these were filtered out.
- Some values in the total_score column were filled in with "-" instead of a number value, these rows were removed.

### Step 5: Analyse clean data ###
- Created pivot chart to explore data
- Noticed a possible correlation between university scores and the percentage of international students, Used the PEARSON function to generate an R value for the two columns of 0.652719057, proving a moderate but not strong correlation.

