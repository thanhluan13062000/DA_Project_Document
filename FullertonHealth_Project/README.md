# <img width="40" height="40" alt="image" src="https://github.com/user-attachments/assets/dceb37ea-2ace-4d95-9b64-20590be3aaaa" /> The Complete Power BI Reporting System Project.

## Overview:

This is one of my projects I did at Fullerton Health as a Data Analyst.

**Note: All data used in this project is not real**

In this project, I built the system from scratch, including:

- Centralized data from multiple sources through ETL process.
- Designed OLAP data model for analysis.
- Created DAX measure for KPIs and business metrics.
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

After the ETL process was done and I had enough tables for data modeling.

![datamodeling.png](https://github.com/thanhluan13062000/DA_Project_Document/blob/main/FullertonHealth_Project/Pictures/datamodeling.png)