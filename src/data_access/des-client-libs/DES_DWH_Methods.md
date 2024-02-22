# PView DWH DES functions

•	[DES].[GetDailyKPIValues]: get KPI data from the 
o	Parametere
	"FacilityNames":["EG-AS", "EG-DA"]
	"KPIDefinitions":["PerformanceRatioProductionLoss", "AmbientTemperatureMeasure"]
	"FromDate":["2020-01-01"]
	"ToDate":["2020-04-01"]
o	Result set:
	“FacilityName"
	"KPI_DefinitionName"
	“Unit”
	"Date"
	"Value"
o	Gyldige KPIDefinitions:
	RainMeasure
	ReactiveEnergyMeasure
	ReactivePowerMeasure
	AmbientTemperatureMeasure
	ModuleTemperatureMeasure
	WindDirectionMeasure
	InclineIrradiationEnergyMeasure
	InclineIrradiationEnergyForecast
	PerformanceRatioProductionLoss
	PlantAvailabilityProductionLoss
	GridAvailabilityProductionLoss
	TrackerAvailability
	EnergyPerformanceIndex
	CurtailmentLosses
	SoilingIndex
	PlantDownTimeLosses
	GridDownTimeLosses
	TrackerDownTimeLosses
	PerformanceRatioProductionLossForecast
	SoilingLosses
	ClippingLosses
	StringLosses
	ModuleTemperatureDaylightMeasure
	ModuleTemperatureCorrected
 
•	[DES].[GetInverterAlarms]: get alarms for inverters
o	Parametere
	"Inverters": ["EG-AS-TS02-I04", "EG-AS-TS01-I01"]
	"FromTime":["2020-01-01T00:00:00"]   local time
	"ToTime":["2020-04-01T10:00:00"]    local time
o	Result set:
	"InverterName
	"AlarmSource"
	"AlarmMessage"
	"AlarmAcknowledged" true/false
	"AlarmSeverity"   1-1000
	"ActiveTimeUTC"
	"ActiveTimeLocal"
o	Example
	@JsonDataSet='{"Inverters":["EG-AS-TS02-I04", "EG-AS-TS01-I01"],"FromTime":["2020-01-01T12:00:00"],"ToTime":["2020-04-01T12:00:00"]}'
 
•	[DES].[GetInverterKPIs]:  get KPI calculations for inverters 
o	Parametere
	"Inverters": ["EG-AS-TS02-I04", "EG-AS-TS01-I01"]
	"FromTime":["2020-01-01T00:00:00"]   local time
	"ToTime":["2020-04-01T10:00:00"]    local time
o	Result set:
	"InverterName
	"DownTimeSeconds": number of seconds in period with downtime
	"EstimatedProductionLoss": estimated losses for downtime in periode, Wh
	"PerformanceRatio": calculated PR net for inverter in period
o	Example
	@JsonDataSet='{"Inverters":["EG-AS-TS02-I04", "EG-AS-TS01-I01"],"FromTime":["2020-01-01T12:00:00"],"ToTime":["2020-04-01T12:00:00"]}


