# Manual Data Correction

Data is corrected manually in web pages in plant portal and central portal.
This chapter describes the functionality.
## Central Web Portal
### Production correction
Production number is read from energy meters and summarized and stored as plant data per 10 minute. This plant data can be manually corrected. Meter data as input to the plant data is not corrected in this process.
User enter 10 minute data to be changed. Values can be positive or negative. Reason for change is added as text. Production values are updated and used in KPI calculations.
See also 2.1.1.
### Production adjustment factor
The production adjustment factor is used to calculate the Kd factor in contractual PR. The screen enters a adjustment factor from 0-1 per plant and day, and factor is used to calculate other losses for the Kd factor (see 2.4.7)
### Irradiation adjustment
Irradiation number are read from pyranometers and summarized and stored as plant data per 10 minute (see 2.1.3 and 2.1.4). Plant values can be updated using a web screen in portal. Only irradiation energy data used for PR calculation is updated.
### Budget updates
Budgets are updated in budget screen.
### Edit plant comments
Plant comment screen is used to update daily textual comments used in reporting
### Update Facility Weather Data
This function is used to update weather data for a facility. User can update the data on a facility in 3 ways:
- Update from sensors values. E.g. when one or more sensors are set out of order.
- Update from historical SolarGIS data
- Update from forecast SolarGIS data
## Plant web portals
### Equipment Down Times
Registered states for each equipment is corrected in the plant web portal.
See also 3.1.