# Deeper_Analysis_of_Data-related_Jobs
This project was created in order to improve my Excel and data analysis skills.  
The main goal of this project was to perform several analyses on a dataset containing various information about data-related jobs.

I created analyses answering the following questions:

- What are the top skills of Data Professionals?
- Do more skills equal more money for Data Specialists?
- What’s the salary for data jobs in different countries?
- What’s the pay of top 10 data skills?

---

## Excel Skills Used

- Pivot Tables  
- ETL  
- Power Query  
- Pivot Charts  
- DAX
- Power Pivot 

---

## Dataset Used

The dataset used in this project covers the period from **January 2023 to June 2025** and is available through Luke Barousse’s Excel course:  
[Excel Dataset](https://lukeb.co/bonus_excel_file)

---

## 1. What are the top skills of Data Professionals?

**Skills & Tools:** Power Pivot

At the start, I created a **Data Model** by integrating the `data_jobs_all` and `data_jobs_skills` tables into one model.

<img width="1118" height="700" alt="data model diagram" src="https://github.com/user-attachments/assets/d5ac3dc2-3ed9-4c3f-9846-02b5e5d514fc" />


Since the dataset was already cleaned in Power Query, Power Pivot automatically created a relationship between these two tables based on the `job_id` column.

Then, I built a **Pivot Table** and a **Pivot Chart** with slicers.

<img width="1357" height="529" alt="pivot table and chart" src="https://github.com/user-attachments/assets/d5bae4e7-17e9-4d62-8239-174ba9692df3" />

### Final Analysis

The chart shows that **SQL**, **Excel**, and **Python** are the most used skills for Data Analysts in Poland, reflecting their fundamental role in data analysis.

---

## 2. Do more skills equal more money for Data Specialists?

**Skills & Tools:** Power Query / ETL

I started by extracting the original data in Power Query and created two queries:
- one containing all job information  
- another listing skills for each `job_id`

![Queries in Power Query](path/to/queries_preview.png)

Next, I transformed the data by:
- changing column types  
- cleaning text to remove specific words (skills)  
- removing unnecessary columns  

![Applied Steps in Power Query](path/to/applied_steps.png)

Afterwards, I loaded the transformed queries into the workbook.

![Loaded Data](path/to/loaded_data.png)

Finally, I created a **Pivot Table** and a **Pivot Chart** with a slicer.

![Pivot Chart Result](path/to/pivot_chart_skills_salary.png)

### Final Analysis

The chart reveals a correlation between the **number of skills** and **median salary**.  
Roles requiring fewer skills tend to offer lower salaries, while more specialized skill sets are associated with higher pay.

---

## 3. What’s the salary for data jobs in different countries?

**Skills & Tools:** Pivot Tables & DAX

Using the Data Model created with Power Pivot, I built a **Pivot Table** showing:
- Job Titles  
- Median Salary (US)  
- Median Salary (Non-US)

![Pivot Table by Country](path/to/pivot_table_country.png)

To calculate the **median salary** for jobs in the United States, I added a new DAX measure:

``DAX
=CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States"
) ``

### Final Analysis

Job roles such as **Senior Data Engineer** and **Data Scientist** have the highest median salaries both in the US and globally, showing the strong demand for advanced data skills worldwide.

![Pivot Table and Slicer](path/to/pivot_table_dax_result.png)

---

## 4. What’s the pay of top 10 data skills?

**Skills & Tools:** Advanced Charts

For this analysis, I used the previously cleaned and loaded data to create a **Combo Pivot Chart** that compares **Median Salary** and **Skill Likelihood (%)** from the Pivot Table.  
- On the **primary axis**, the chart shows Median Salary (as a Clustered Column).  
- On the **secondary axis**, it shows Skill Likelihood (as a Line with Markers).

To improve clarity, I added axis titles, removed unnecessary lines, and changed the markers to diamond shapes.

![Combo Chart of Top 10 Skills](path/to/top10_skills_chart.png)

### Final Analysis

The chart shows that learning key skills such as **Python** and **SQL** is closely connected with higher salaries, making them essential for anyone looking to increase their value in the data industry.
