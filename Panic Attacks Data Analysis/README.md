
# 🏥 Panic Attack Data Analysis - NGO Project Power BI Dashboard

📌 Problem Statement



Analysis of panic attack patterns among different demographics to help NGO develop targeted mental health interventions.

🛠️ Tools Used: 
Snowflake, 
Power BI

🔑Key Learnings:

 -Snowflake database management

 -SQL queries for data extraction and transformation

 -Power BI visualization techniques (Bar Charts, Slicers, Line Charts, Area Charts, Clustered Bar Charts)

 -Data transformation using Power BI, Excel and SQL

 -Data modeling concepts

 -DAX Measures implementation



🧾 Steps Followed 🧠 Advanced Calculations

- Step 1
-Data Source: NGO CSV file

-Data Extraction & Preparation

-Extracted raw data from NGO website in CSV format

-Performed initial data cleaning in Excel:

-Standardized column headers

-Handled missing values

-Validated data ranges

- Step 1
Snowflake Setup
Created Snowflake account and configured workspace
Created database using SQL:
CREATE DATABASE PowerBIProject;
Created table structure:

<img width="263" alt="Image" src="https://github.com/user-attachments/assets/77bc5556-b1c3-4957-b14c-f6be27ef399c" />


Data Profiling & Transformation
Data validation queries:

-- Check for null IDs
SELECT * FROM panic_attack_data WHERE id IS NULL;

-- Check for duplicates
SELECT id, COUNT(id) FROM panic_attack_data 
GROUP BY id ORDER BY COUNT(id) DESC;

Created analysis dataset copy:

CREATE TABLE analysis_dataset AS SELECT * FROM panic_attack_data;

Data corrections:

UPDATE analysis_dataset 
SET gender = "male" 
WHERE panic_attack_frequency = 9;

Power BI Transformation
In Power Query Editor:

Converted boolean values to 0/1

Created conditional column for Panic Score:

<img width="1207" alt="Image" src="https://github.com/user-attachments/assets/251456df-c89a-4d8a-86ee-6af8cf792e1f" />


Adjusted heart rate values by -1 using Transform > Reduce Value


Visualizations
Main Dashboard:

Bar charts showing panic attack frequency by demographic

Slicers for gender, age groups
*(Space for PBI screenshot 4 - Main Dashboard)*

Age Group Analysis Page:

Created calculated columns:

// IF version
Age Group = IF('dataset'[Age]<=17,"Child",
             IF('dataset'[Age]<=24,"Adolescent",
               IF('dataset'[Age]<=64,"Adult","Senior")))

// SWITCH version
Age Group = SWITCH(TRUE(),
                  'dataset'[Age]<=17,"Child",
                  'dataset'[Age]<=24,"Adolescent",
                  'dataset'[Age]<=64,"Adult",
                  "Senior")




Key Metrics:
% with Dizziness = 
DIVIDE(
    COUNTROWS(FILTER('dataset', 'dataset'[Dizziness]=1)),
    COUNTROWS('dataset'),
0)*100


📸 Snapshots

Data Source:

<img width="1423" alt="Image" src="https://github.com/user-attachments/assets/e6e80fbd-45d1-49ce-b527-4bcba37a3822" />

Number of patient by symptons:

![Image](https://github.com/user-attachments/assets/bb0c6256-20e9-4248-b12d-87fcd73a7b37)


other Analysis:

![Image](https://github.com/user-attachments/assets/a2d42f77-5a53-4b0c-b73d-a411dc7504b1)



age group analysis using clustered bar chart:

![Image](https://github.com/user-attachments/assets/c409579b-5215-4ef2-b9ad-494ebbf3f0f6)





📊 Data Dictionary

<img width="290" alt="Image" src="https://github.com/user-attachments/assets/541a0e2d-e460-488a-9c3e-60906fb8a163" />



