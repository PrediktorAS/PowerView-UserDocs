# Forecasting Principles

There are three types of forecasts in the system:

* PVSYST simulation values
    * Hourly values from PVSYST simulation software
    * Monthy production diveded equally between each day
    * Loaded on plat system and available in plant reports
    * Available in Honeystore time series database and in Process Exporer under \<plant\>-Forecast database
    * Available in central reports under "PVSYST Forecast" forcast type (External forecast report)
* Owner budget values
    * Budget values loaded into data warehouse
    * Daily values
    * Available in central reports as forecast types (Measured vs forecast)
        * Internal original budget
        * Internal updated budget
        * External original budget
* SolarGIS forecast values
    * Forecast loaded from SolarGIS forecast service provider
    * Power and weather forecast loaded each day
    * 15 minute values
    * Two types:
        * RollingDaily: 9 days ahead, updated for all days every day at midnight. Data for next days overwritten and updated every day.
        * WeekAhead: updated day one week ahead. Data is not overwrittem
    * Available in central reports  (External forecast report)
