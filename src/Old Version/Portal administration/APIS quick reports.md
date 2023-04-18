# APIS Quick Reports

APIS Quick reports, are a set of reports to define reports for data in the ACT plant databases and APIS Honeystore time series database. One can define process reports, with tabular and graph presentation elements. Typically equipment state and alarm&events data can be configured in this solution.

The main elements to creating a new report type are:

* Select type report. The selection is done from a defined selection of report types.
* The report is configured through selection which heading, data fields and curve/graphs as in the report.
* Configure the option in the portal menu for direct access to the report.

The very first thing is to click the menu option __Portal admin->Report config__. This brings up a list of all configured reports.

The following are the functions to the buttons and links in the screen:

* __Edits__: Amend the report
* __Copy__: Create a Linde the report. The report gets the same name, with the word copy prefixing it.
* __ID/Name/Description...__: Sort the table through clicking on these
* __Add new__: Create a new report

Through clicking the button __Add new__ a new page is opened to add new data elements.

The parameters in this screen that are common to all report types are explained below. The selected report type is Multiplematerial report. Other report types selected will give different fields to fill in on the screen. This is shown under the detailed description of the different report types.

Parameter

__Description__

|Name|Report name|
|---|---|
|Description|Freeform description of the report|
|Type|Allows selection of the type of report. You can select between 12 different types:<br><li> Single carrier report. Report for a given carrier (material carrier).<br><li> Multiple carrier report. As above, but for multiple carriers (material carriers).<br><li> Equipment report. Gives data for equipment.<br><li> Single material report.This is a report that gives data for a unit of a produced material. A unit could be a produced part or batch or a semi-product.<br><li> Multiple material report. As above, but for multiple material units.<br><li> Period report. Aggregated data for a selected period and with a given interval.<br><li> Single process run report. Report with data for a run.<br><li> Multiple process run report. As above, but for multiple runs.<br><li> Process unit, multiple. Fetch data for one or more process units.<br><li> Process unit, report periodical. Fetch data for a process unit split into intervals.<br><li> Multiple registration report. Fetch data for multiple registration.<br><li> Single registration report. Fetch data for a registration<br><br>Each of these types is handled in a separate chapter|
|Number of frozen rows|Scrolling in the table will be fixed and not allowed.|
|Show the column name|Identifiers and selected aggregated data (for example ”mean”) namely in the different columns in 1st row, if this box is crossed.|
|Number of line graphs|Gives how many line graphs will be shown in the report.|
|Number of bar graphs|Gives how many bar graphs will be shown in the report.
|Table type|Determines whether the table will be shown column-wise, row-wise or no table at all.|
|Dynamic graph|Whether you will be able to redefine the report retrieval. A graph is defined within it for selection of which rows will be included.|
|Data elements|Shows a line for each data element defined as one data element per line. Definition of data will be described in more depth under the different report types. In the example above the is no data defined (zero lines for the data definition)|

The following are the functions of the buttons and links in the screen:

* __OK__: Saves and quits the configuration   
* __Cancel__: Quits the configuration without saving
* __Save__: Saves without quiting the configuration
* __Delete__: Delete the report
* __Add new__: Add a new report element

__Data elements__

Data elements are added to the table bottommost in the report configuration page. Through clicking Add new, a new window is opened. What will be configured depends on the report type and selected data type. 

The table below displays the fields that are joint for all report elements. Special fields are explained in more detail for each report type.

Parameter

__Description__

|||
|---|---|
|Data label|Text that is shown in report tables and graphs for this data element.|
|Tag name|Given here is a tag name of the element if you will use the element for further calculation. In an arithmetic expression in the spreadsheet function, use the tag name.|
|Order|This givens which placing the data element will have in relation to the other data elements in the report|
|Data type|Selects what kind of data will be fetched. The choice here is independent to the report type.|
|Link to report|This allows creation of a ”hyperlink” in the report table to another report. Eg. You can link an identifier value in a multiple material report versus a single material report.|
|Show in graph|You can select a line graph or a bar graph here for presentation of the data element. This is only applicable for numeric elements.|
|Show in table|Determines if a data element will be shown in a table or not be shown.|
|Data aggregation|This is shown for numeric data elements. It aggregates the values shown in there own column (row) at the end of the report table. Use “Show column name" to see the name of the aggregation in the table.|
