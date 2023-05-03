# Planned Power Reduction

Planned reduced availability can be registered in two ways as shown below:
- Planned Power Reduction
- Planned Outages 
    - Is used to import planned power reduction


## Planned Power Reduction

Planned power reduction is registered in a plant portal page to reduce the planned nominal power in the forecast. Data is normally transferred to the data warehouse and used for adjusted forecasting if used.

Procedure to operate screen is:

- Select time period to edit data
- Press "Get data" button to refresh data table
- Press the "edit" button to edit a date
- Enter reduced power in kW for each hour
- Press the "v" button to store data or the "x" button to cancel operation
- Press the "Update from planned outages" to update all data for period based on registration of planned outages
    - NB: all data is overwritten with the planned outages data, removing the previous entered values

Zero values are not shown in the read mode of the list.

Total nominal availability is calculated based on the Nominal AC grid power registered for the plant under plant parameters.

Planned power reduction will be used to calculate adjusted forecast

## Planned Outages

Planned outages are registered in portal page to report power ouatges for the plant. 

Procedure to operate screen is:

- Edit data
    - Select time period to see old outage registrations
    - Press "Get data" button to refresh data table
    - Press the "Edit" button  to edit an existing outage registration
    - Enter start time, end time, power reduction and comment
    - Press the "v" button to store data or the "x" button to cancel operation
- Add new data
    - To add new outage registration, press "+" button
    - Enter data and press the  button to store data or the "x" button to cancel operation
- Delete data
    - Press "-" button for the row to be deleted
    - Confirm or Cancel deletion

If you register an outage outside the time interval of your time filter, it will not show in table. Then change period filter to see the new outage.
