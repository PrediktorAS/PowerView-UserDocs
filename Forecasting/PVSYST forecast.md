# PVSYST Forecast

Initial hourly forecast on plant system is based on PVSYST simulation. Following data is stored per hour:

* EnergyForecast
* IrradiationHorizontal
* IrradiationInCline
* TemperatureAmbient

The PVSYST initial data are averaged per month, having same values for each time of day through out the months (implemented from Jordan plants). This removes the unatural statistical variations.
