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

<img width="329" height="196" alt="Queries" src="https://github.com/user-attachments/assets/fc585e45-abb1-417c-bfe5-fcebcab81cca" />



Next, I transformed the data by:

- changing column types  
- cleaning text to remove specific words (skills)  
- removing unnecessary columns  

<img width="1911" height="638" alt="Applied Steps in Power Query" src="https://github.com/user-attachments/assets/3050280e-3c85-4513-ae33-be245e00ddc9" />
<img width="1886" height="694" alt="Applied Steps in Power Query" src="https://github.com/user-attachments/assets/5f9c64fa-349c-49df-a7bb-58c415823b15" />

Afterwards, I loaded the transformed queries into the workbook.


Finally, I created a **Pivot Table** and a **Pivot Chart** with a slicer.


<img width="1463" height="499" alt="Pivot Chart Result" src="https://github.com/user-attachments/assets/c3b9d9f4-3674-4f12-8791-142b08a39ae7" />


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

<img width="674" height="330" alt="Pivot Table by Country" src="https://github.com/user-attachments/assets/0db249c9-b39a-46a6-88d8-80e38fcf162e" />


To calculate the **median salary** for jobs in the United States, I added a new DAX measure:

``DAX
=CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States"
) ``

### Final Analysis

Job roles such as **Senior Data Engineer** and **Data Scientist** have the highest median salaries both in the US and globally, showing the strong demand for advanced data skills worldwide.


<img width="964" height="416" alt="Pivot Table and Slicer" src="https://github.com/user-attachments/assets/8a6baded-7e52-4d56-abda-c0a25d6590ae" />


---

## 4. What’s the pay of top 10 data skills?

**Skills & Tools:** Advanced Charts

For this analysis, I used the previously cleaned and loaded data to create a **Combo Pivot Chart** that compares **Median Salary** and **Skill Likelihood (%)** from the Pivot Table.  
- On the **primary axis**, the chart shows Median Salary (as a Clustered Column).  
- On the **secondary axis**, it shows Skill Likelihood (as a Line with Markers).

To improve clarity, I added axis titles, removed unnecessary lines, and changed the markers to diamond shapes.


<img width="1534" height="447" alt="Combo Chart of Top 10 Skills" src="https://github.com/user-attachments/assets/deafab7a-d799-4845-8894-97c2333ebd48" />


### Final Analysis

The chart shows that learning key skills such as **Python** and **SQL** is closely connected with higher salaries, making them essential for anyone looking to increase their value in the data industry.
