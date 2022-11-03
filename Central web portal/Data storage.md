# Data Storage

The central reporting server contains the 10 minute average data store per plant, the forecast database per plant and the data warehouse. The data warehouse database is named SSO_DWH.

The 10 minute time series database has the following naming conversion:

*COUNTRY-SITE-Log10Min*

E.g.: *NO-OS-Log10Min*

* NO: Norway
* OS: Oslo

The forecast time series database has the following naming conversion:

*COUNTRY-SITE-Forecast*

*E.g.: NO-OS-Forecast*

* NO: Norway
* OS: Oslo

The central SCADA server contains the 1 minute data store per plant. The database has the following naming conversion:

*COUNTRY-SITE-Log1Min*

E.g.: *NO-OS-Log1Min*

* NO: Norway
* OS: Oslo           
