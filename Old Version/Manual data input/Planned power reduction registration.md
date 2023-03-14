# Planned Power Reduction Registration

Planned power reduction is registered in a plant portal page to reduce the planned nominal power in the forecast. Data is normally transferred to the data warehouse and used for adjusted forecasting if used.

Procedure to operate screen is:

* Select time period to edit data
* Press "Get data" button to refresh data table
* Press the edit button ![Edit button](../Images/edit.png) to edit a date
* Enter reduced power in kW for each hour
* Press the ![Apply button](../Images/store.png) button to store data or the ![Cancel button](../Images/cancel.png) button to cancel operation
* Press the "Update from planned outages" to update all data for period based on registration of planned outages
    * NB: all data is overwritten with the planned outages data, removing the previous entered values

Zero values are not shown in the read mode of the list.

Total nominal availability is calculated based on the Nominal AC grid power registered for the plant under plant parameters.