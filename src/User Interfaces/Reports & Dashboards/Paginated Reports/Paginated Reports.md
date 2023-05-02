# Paginated Reports

Paginated reports are made from data in data warehouse database using <a href="https://learn.microsoft.com/en-us/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports?view=sql-server-ver16" target="_blank">SQL Server Reporting Services</a> or <a href="https://www.boldreports.com/" target="_blank">Bold Reports</a> reporting tools. 
The reports are opened from the web portal on the central server. 

Each report has a header. The header contains a set of report parameters for filtering the report content, and these are different from report to report. The example below shows one only having Month as input. When all parameters are filled in, one can get the report by pressing the "View report" button. The parameter field can be hidden pressing the ![](../../../Images/SSRS_HideMenu.png) button.

The row below the parameter field, contains functions for operating the generated report. Here is a list of options:

- Use the arrow buttons to switch pages when multiple pages in result, or enter page number in the page number input field and press enter
- Zoom the report using the zoom field 
- Find text in the report using the search tool 
- Export data to other format using the export menu 
- Refresh report content using the refresh button 
- Print report using the print button 


