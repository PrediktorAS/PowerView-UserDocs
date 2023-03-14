# Data Warehouse Reports

The data warehouse reports are made as custom reports from the data warehouse database using MS Reporting Services reporting tool. The reports are opened from the web portal on the central server. 

Each report has a header. The header contains a set of report parameters for filtering the report content, and these are different from report to report. The example below shows one only having Month as input. When all parameters are filled in, one can get the report by pressing the "View report" button. The parameter field can be hidden pressing the  button.

The row below the parameter field, contains functions for operating the generated report. Here is a list of options:

* Use the arrow buttons ![Arrow buttons](../Images/SSRS%20arrow%20paging.png) to switch pages when multiple pages in result, or enter page number in the page number input field and press enter
* Zoom the report using the zoom field ![Zoom](../Images/SSRS%20zoom.png)
* Find text in the report using the search tool ![Search](../Images/SSRS%20search.png)
* Export data to other format using the export menu ![Export](../Images/SSRS%20Export.png)
* Refresh report content using the refresh button ![Refresh](../Images/SSRS%20refresh.png)
* Print report using the print button ![Print](../Images/SSRS%20print.png)
 
![header](../Images/SSRS%20header.png)

PS: some reports has a period selection as well as a "Period free" selection, added start and end date/time. Example is shown below. When using the free period, un-check both start and end check-boxes to the right of the date input fields and enter dates and time. When this is done, the period selection is overruled, even though it is still visible (not possible to hide on the fly).

![Period picker](../Images/period%20start%20free.png)
