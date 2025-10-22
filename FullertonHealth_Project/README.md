# <img width="40" height="40" alt="image" src="https://github.com/user-attachments/assets/dceb37ea-2ace-4d95-9b64-20590be3aaaa" /> The Complete Power BI Reporting System Project.

## Overview:

This is one of my projects I did at Fullerton Health as a Data Analyst.

**Note: All data used in this project is not real**

In this project, I built the system from scratch, including:

- Centralized data from multiple sources through ETL process.
- Designed OLAP data model for analysis.
- Created DAX measures for KPIs and business metrics.
- Designed Interactive Dashboard for management teams.
- Managed Power BI Service for report publishing and access control.

![process.png](https://github.com/thanhluan13062000/DA_Project_Document/blob/main/FullertonHealth_Project/Pictures/process.png)

## Data source

- Company Databases
- Company Sharepoint

## Tech stack

- MariaDB
- Python
- Power BI

## Implementation process

### Centralized data from multiple sources through ETL process.

Imported data from 5 different sources — one from the company database and four Excel files stored on SharePoint.

![import_source.png](https://github.com/thanhluan13062000/DA_Project_Document/blob/main/FullertonHealth_Project/Pictures/import_source.png)

You can find all the SQL scripts used to extract data from the database in the folder here: [SQL_Scripts Folder](https://github.com/thanhluan13062000/DA_Project_Document/tree/main/FullertonHealth_Project/SQL_Scripts)

Below is one of the tables I imported into Power BI. Normally, I would perform several data transformation steps based on specific business requirements. However, in this project, the data provided was already clean and well-structured, so I only needed to promoted headers and changed column data types.

![imported_data.png](https://github.com/thanhluan13062000/DA_Project_Document/blob/main/FullertonHealth_Project/Pictures/imported_data.png)

Load all tables to Power BI

![afterETL.png](https://github.com/thanhluan13062000/DA_Project_Document/blob/main/FullertonHealth_Project/Pictures/afterETL.png)

### Designed OLAP data model for analysis.

After the ETL process was completed and I had enough tables for data modeling.

![datamodeling.png](https://github.com/thanhluan13062000/DA_Project_Document/blob/main/FullertonHealth_Project/Pictures/datamodeling.png)

In this case, the data model includes two business processes:
the Claim process, and the Customer Enrollment and Group Change (CEGC) process.
The Claim process has two fact tables — Claim and Claim Detail — while the CEGC process has one fact table, Situation.

### Created DAX measures for KPIs and business metrics.

1. Claim Processing Indicators.

- Total number of claims received, settled and pending.
- Turnaround time indicators for claims, including the number and percentage of claims processed on time.
- Classification of pending claims by time delay zone to identify and prioritize overdue cases for processing.

2. Claim Adjuster Productivity

- Measures the number of claims handled by each Claim Adjuster, along with the number and percentage of claims processed on time.

3. Customer Lives

- Tracks the total number of active customers (lives) covered under insurance policies over time.
- Enables time-based analysis (month, quarter, or year) to monitor customer growth trends and retention performance

**Total number of claims**

<pre>
Claims_Count_Measure = 
  DISTINCTCOUNT('Claim detail'[Claim number])
</pre>

**Total claims settled and pending**

Claims_Count_Filter = 
VAR Settled_Claims =
    CALCULATE(
        [Claims_Count_Measure],
        Claim[Status] = "Settled"
    )
VAR Pending_Claims =
    CALCULATE(
        [Claims_Count_Measure],
        ALLEXCEPT(Claim,Claim[Beneficiary type]),
        Claim[Status] = "Pending"
    )
VAR Selected_Status  =
    SELECTEDVALUE(Claim[Status])

RETURN
    SWITCH(
        TRUE(),
        Selected_Status  = "Settled",Settled_Claims,
        Selected_Status  = "Pending",Pending_Claims,
        [Claims_Count_Measure]
    )
