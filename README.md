# Salary Survey Analysis
### Dataset Source: [**kaggle**](https://www.kaggle.com/datasets/masoomaalghawas/ask-a-manager-salary-survey-2021)
### Original Dataset Author/s: Masooma Alghawas, Hind Janahi, Sara Janahi


## Overview
  The main goal of the project is to clean and prepare a dataset survey published by Alison Green on [www.askamanager.org](https://www.askamanager.org/2021/04/how-much-money-do-you-make-4.html). The author of the survey aims to gather real-world information about what different job salaries are in the market. As per Green, the goal of the survey is to remove unreliable and inaccurate data that are often seen on online salary websites.

The dataset was prepared and cleaned using Excel - Power Query, followed by Power BI to visualize the data.


## Data Import
The dataset was imported in Excel for data cleaning using Power Query tools.


## Understanding the Dataset
  Understanding the dataset's structure is crucial, as it guides how we approach data cleaning, missing entries, duplicates, inconsistent data types, and messy values.


1. **Column Count:** 18 columns.
2. **Row/Records Count:** 27,941 rows/records.
3. **Column Names and Data Types:**
   - Timestamp: General
   - How old are you?: General
   - What industry do you work in?: General
   - Job title: General
   - If your job title needs additional context, please clarify here: General
   - What is your annual salary? (You'll indicate the currency in a later question. If you are part-time or hourly, please enter an annualized equivalent -- what you would earn if you worked the job 40 hours a week, 52 weeks a - year.): Number
   - How much additional monetary compensation do you get, if any (for example, bonuses or overtime in an average year)? Please only include monetary compensation here, not the value of benefits: General
   - Please indicate the currency: General
   - If "Other," please indicate the currency here: General 
   - If your income needs additional context, please provide it here: General
   - What country do you work in?: General
   - If you're in the U.S., what state do you work in?: General
   - What city do you work in?: General
   - How many years of professional work experience do you have overall?: General
   - How many years of professional work experience do you have in your field?: General
   - What is your highest level of education completed?: General
   - What is your gender?: General
   - What is your race? (Choose all that apply.): General

    **Data types identified:** 17 General and 1 Number

4. Categorical Column Values (Sourced from [askamanager](https://www.askamanager.org/2021/04/how-much-money-do-you-make-4.html) website):  

    - How old are you?: **7 Unique Values Identified.**
        - under 18  
        - 18-24  
        - 25-34  
        - 35-44  
        - 45-54  
        - 55-64  
        - 65 or over  

    - What industry do you work in?: **27 Unique Values Identified.**
        - Accounting, Banking & Finance
        - Agriculture or Forestry
        - Art & Design
        - Business or Consulting
        - Computing or Tech
        - Education (Primary/Secondary)
        - Education (Higher Education)
        - Engineering or Manufacturing
        - Entertainment
        - Government and Public Administration
        - Health care
        - Hospitality & Events
        - Insurance
        - Law
        - Law Enforcement & Security
        - Leisure, Sport & Tourism
        - Marketing, Advertising & PR
        - Media & Digital
        - Nonprofits
        - Property or Construction
        - Recruitment or HR
        - Retail
        - Sales
        - Social Work
        - Transport or Logistics
        - Utilities & Telecommunications   
        - Other     

    - If you're in the U.S., what state do you work in?: **51 Unique Values Identified**

    - How many years of professional work experience do you have overall?: **8 Unique Values Identified**
        - 1 year or less
        - 2 - 4 years
        - 5-7 years
        - 8 - 10 years
        - 11 - 20 years
        - 21 - 30 years
        - 31 - 40 years
        - 41 years or more

    - How many years of professional work experience do you have in your field?: **8 Unique Values Identified**
        - 1 year or less
        - 2 - 4 years
        - 5 - 7 years
        - 8 - 10 years
        - 11 - 20 years
        - 21 - 30 years
        - 31 - 40 years
        - 41 years or more

    - What is your highest level of education completed? **6 Unique Values Identified**
        - High School
        - Some College
        - College Degree
        - Master's Degree
        - PhD
        - Professional Degree (MD, JD, etc.)

    - What is your gender?: **4 Unique Values Identified**
        - Man
        - Woman
        - Non-binary
        - Other or prefer not to answer

    - What is your race?: **7 Unique Values Identified**
        - Asian or Asian American
        - Black or African American
        - Hispanic, Latino, or Spanish origin
        - Middle Eastern or Northern African
        - Native American or Alaska Native
        - White
        - Another option not listed here or prefer not to answer


### Data Cleaning and Transformation
  To improve data quality and analysis accuracy, various cleaning steps were taken such as handling missing values, standardizing inconsistent entries, formatting issues, column names, and dropping unneeded tables.

1. Removed Duplicates
    - Tool Used: Data Tab - Remove Duplicates.
    - Result: No Duplicates Found.
2. Dropped Columns
    - A total of 7 columns were dropped since these columns either provide redundant information or have minimal impact on key insights. 11 columns remained (e.g., column "How much additional monetary compensation do you get, if any" dropped since not all same jobs have will have an additional compensation and can lead to unreliable expectations and inconsistent insights).
2. Renamed Columns
    - Almost all columns were renamed for readability (e.g., "what is your annual salary" vs. "salary", "Job title" vs. "job_title", "timestamp" vs. "date_recorded", etc.).
3. Changed Data Type 
    - Data type format of columns were changed for standardization and accuracy (timestamp date/time vs. date, salary general vs. number, etc.).
4. Trimmed and standardized text columns.
    - Tool used: Power Query - Transform
    - Columns Affected: industry, job_title, country, education_level
5. Data Validation
    - A helper column was used to validate "under 18" and "18-24" categories in age_group column that has "8 - 10 years" and above in experience_years_field and experience_years_overall column. 
    - Tool used: Power Query - Add Column - Custom Column
    - Columns Affected: age_group
    - Script used: [under 18](https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/scripts/under%2018), [18-24](https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/scripts/18-24)
6. Records Count
    - Raw: 27941
    - Cleaned: 26842
    - Records removed: 1099


### Data Analysis
  Conducted exploratory analysis with visualizations to reveal patterns and insights across multiple categories, including distributions and average salaries.
  
  **Note:** Since most of the population of the data are from the United States, the analysis was done using the top 5 country with the most respondents and its respective currency, in this way, we are to ensure consistency and transparency of the data.


#### Gender Distribution and Salary
  - There’s a notable imbalance in the gender distribution: women make up 78% of the total population, while men account for 19% and non-binary genders for 2–3%.  
  - Men report the highest average salary, slightly above the 100k mark, followed by women and non-binary individuals, both in the 70–80k range.
  This difference may be influenced by the relatively small number of men in the dataset, which could be skewing their average salary upward.

<p align="center">
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/gender_distribution.png" width="45%" />
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/gender_salary.png" width="45%" />
</p>


#### Age Group Distribution and Salary
  - Most of the population resides in 25-34 and 35-44 age group, this is a normal observation since these groups are the primary workforce of most organizations. 
  - Age group 45-54 shows the highest average salary, followed closely by 35-44 and 55-64 groups. This can be due to pay grade or salaries having a correlation with age or work experience.

<p align="center">
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/agegroup_distribution.png" width="45%" />
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/agegroup_salary.png" width="45%" />
</p>


#### Education Level Distribution and Salary
  - The majority of respondents hold either a college degree or a master’s degree. An expected result, as this is a common requirement in today's professional roles in organizations. 
  - In terms of average salary, respondents with Professional Degrees (MD, JD, etc.) stand out, earning well above 100k on average compared to the other groups. This may be linked to the specialized nature of these degrees, where advanced expertise offer a higher pay grade in roles requiring specific knowledge or skill sets. 

<p align="center">
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/educationlevel_distribution.png" width="45%" />
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/educationlevel_salary.png" width="45%" />
</p>


#### Country Distribution and Salary
  - The dataset is heavily skewed toward the United States, which accounts for over 20,000 respondents (more than 70% of the total population). The remaining respondents are primarily from Canada, the United Kingdom, Australia, and Germany.
  - In terms of average salary, Australia reports the highest figures, exceeding the 100k mark, while the United Kingdom shows the lowest, around 50k. These results may be influenced by the relatively small sample sizes outside the United States, which can skew averages and limit broader generalization.

<p align="center">
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/country_distribution.png" width="45%" />
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/country_salary.png" width="45%" />
</p>


#### Work and Role Tenure Distribution and Salary
  - Work Tenure (overall years of experience): The top three groups are 2–4 years, 5–7 years, and 11–20 years, each with a closely even share of respondents. This aligns with the two most populated age brackets (25–34 and 35–44), which represent mid to advanced career professionals.
  - Role Tenure (years of experience in current field/role): A significant proportion of respondents fall within the 11–20 years category, while the remaining groups generally have 5k respondents or fewer.
  - In terms of salary, both work and role tenure show that respondents with 21–30 years of experience earn the highest average salaries, followed by those with 11–20 years and 41 years and more. This pattern suggests that career longevity and accumulated expertise are positively correlated with higher pay grades, often reflecting senior or executive-level positions.
  
<p align="center">
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/worktenure_distribution.png" width="45%" />
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/worktenure_salary.png" width="45%" />
</p>

<p align="center">
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/roletenure_distribution.png" width="45%" />
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/roletenure_salary.png" width="45%" />
</p>


#### Industry Distribution and Salary
  - The Information Technology (IT) industry represents the largest share of respondents with over 4,000 participants, followed by Nonprofits and Higher Education, each with more than 2,000 respondents. The remaining industries generally report 1,000 or fewer respondents.
  - In terms of average salary, Information Technology leads with an average of $120k, followed closely by the Law industry. The remaining industries cluster within the $65k–$100k range, indicating relatively balanced compensation levels across most sectors.

<p align="center">
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/industry_distribution.png" width="49%" />
  <img src="https://github.com/Stinrb/Salary-Survey-Analysis/blob/main/visualizations/industry_salary.png" width="49%" />
</p>
