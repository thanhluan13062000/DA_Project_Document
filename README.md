# Sales Report Project with Power BI
Why do we need to do this?
<br>Data is generated when a business starts its business process, synthesizing that data and creating reports showing the necessary indicators helps us clearly understand the operating status of the business.
<br>Indicators shown in this report include:
<br>•	Revenue
<br><pre>o Total revenue
<br>o Revenue by year
<br>o Revenue by customer
<br>o Revenue by each region/city
<br>o Rate of increase/decrease in revenue compared to the previous year </pre>
<br>•	Profit
<br><pre>o Total profit
<br>o Profit by year
<br>o Profit by business channel
<br>o Ratio of profit to revenue
<br>o Rate of profit increase/decrease compared to the previous year</pre>
<br>• Total goods sold
<br>
<br>From the information collected from the indicators in the report, I believe it can help us make decisions to optimize business operations.

## Data Sources
Sales Data: The primary dataset used for this report is the "Sales_Analysis_Report.xlsx" file, containing detailed information about each sale made by the company.
## Tools
- Power BI
## Implementation process
- Import data into power bi
<pre>
  - Download <b> Sales_Analysis_Report.xlsx </b> file
  - Import file into Power BI
</pre>
- Create date table with DAX language
<pre>
  Date = 
ADDCOLUMNS(
    CALENDARAUTO(),
    "Year",YEAR([Date]),
    "Quarter","Q"&FORMAT(CEILING(MONTH([Date])/3,1),"#"),
    "Quarter No",CEILING(MONTH([Date])/3,1),
    "Month No",MONTH([Date]),
    "Month Name", FORMAT([Date],"MMMM"),
    "Month Short Name", FORMAT([Date],"MMM"),
    "Month Short Name Plus Year", FORMAT([Date],"MMM,yy"),
    "DateSort",FORMAT([Date],"yyyyMMdd"),
    "DateName",FORMAT([Date],"dddd"),
    "Details",FORMAT([Date],"dddd-MMM-yyyy"),
    "DayNumber",DAY([Date]),
    "MonthSort",FORMAT([Date],"yyyyMM"
))
</pre>
![create_date_table](https://github.com/thanhluan13062000/DA_Project_Document/assets/160031050/4ad6c330-3f16-4806-933f-63703529ace6)
- Modeling data
- Create measure
- Create Report
