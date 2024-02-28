# Fact Tables

## FactAvailability

Schema name: dbo

Description: Fact table with aggregated equipment availability numbers for a facility in 10 min intervals


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactAvailabilityID|int(4)||Primary key column|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|DateAndHourKey|int(4)||Forreign key to DimDateAndHour table|
|MinuteKey|int(4)||Forreign key to DimMinute table|
|PeriodStartTime|datetime(8)||Start time internal|
|PeriodEndTime|datetime(8)||End time internal|
|InverterSecondsTotal|float(8)||Total number of seconds for inverters in interval|
|InverterSecondsDaylight|float(8)||Daylights seconds for inverters in interval|
|InverterSecondsWeighted_Idle|float(8)||Idle seconds for inverters in interval|
|InverterSecondsWeighted_Operation|float(8)||Operation seconds for inverters in interval|
|InverterSecondsWeighted_Failure|float(8)||Failure seconds for inverters in interval|
|InverterSecondsWeighted_LineRestraint|float(8)||Line restraint seconds for inverters in interval|
|InverterSecondsWeighted_NotScheduled|float(8)||Not scheduled seconds for inverters in interval|
|InverterSecondsWeighted_DownTimeNight|float(8)||Down time seconds for inverters in interval|
|GridSecondsTotal|float(8)|||
|GridSecondsDaylight|float(8)|||
|GridSeconds_Idle|float(8)|||
|GridSeconds_Operation|float(8)|||
|GridSeconds_Failure|float(8)|||
|GridSeconds_LineRestraint|float(8)|||
|GridSeconds_NotScheduled|float(8)|||
|GridSeconds_DownTimeNight|float(8)|||
|TrackerSecondsTotal|float(8)|||
|TrackerSecondsDaylight|float(8)|||
|TrackerSecondsWeighted_Idle|float(8)|||
|TrackerSecondsWeighted_Operation|float(8)|||
|TrackerSecondsWeighted_Failure|float(8)|||
|TrackerSecondsWeighted_LineRestraint|float(8)|||
|TrackerSecondsWeighted_NotScheduled|float(8)|||
|TrackerSecondsWeighted_DownTimeNight|float(8)|||
|TrackerSecondsWeighted_DownTimeForLosses|float(8)|X||


## FactCleaning

Schema name: dbo

Description: Fact table with cleaning estimations


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|Date|date(3)|||
|NumberOfDaysToCleanFacility|int(4)|X||
|CleaningCostFacility|float(8)|X||
|EstimatedSoilingRate|float(8)|X||
|DailyIncomeLossPerSoilingPercent|float(8)|X||
|NumDaysBeforeRainWash|int(4)|X||
|SoilingIndex|float(8)|X||
|CleaningCycle|int(4)|X||
|SoilingLimit|float(8)|X||
|RecommendedWaitForRain|bit(1)|X||
|RecommendedDaysUntilCleaning|int(4)|X||
|ForecastedDaysUntilRainWash|int(4)|X||
|IdealCleaningCycle|int(4)|X||
|IdealSoilingLimit|float(8)|X||


## FactDailyPlantReport

Schema name: dbo

Description: Fact table with daily plant comments from plant database


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactDailyPlantReportID|int(4)|||
|FacilityKey|int(4)|||
|ReportDate|date(3)|||
|DateAndHourKey|int(4)|||
|SiteComment|nvarchar(max)|X||
|CentralComment|nvarchar(max)|X||
|Weather|nvarchar(510)|X||
|LastChangedTime|datetime(8)|X||
|ReportUser|nvarchar(510)|X||


## FactDataQuality

Schema name: dbo

Description: Fact table with aggregated data quality KPI data per facility and day


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|X||
|Date|date(3)|X||
|DataQualityKPI|float(8)|X||
|MeterConsistency|float(8)|X||
|InverterACOutputConsistency|float(8)|X||
|DCLevelConsistency|float(8)|X||
|TrackerDataAvailability|float(8)|X||
|GHIConsistency|float(8)|X||
|GHIDataAvailability|float(8)|X||
|GIIConsistency|float(8)|X||
|GIIDataAvailability|float(8)|X||
|ModuleTempConsistency|float(8)|X||
|ModuleTempDataAvailability|float(8)|X||
|SoilingDataAvailability|float(8)|X||
|AmbientTempConsistency|float(8)|X||
|AmbientTempDataAvailability|float(8)|X||
|WindSpeedConsistency|float(8)|X||
|WindSpeedDataAvailability|float(8)|X||
|MeterConsistency_Factor|float(8)|X||
|InverterACOutputConsistency_Factor|float(8)|X||
|DCLevelConsistency_Factor|float(8)|X||
|TrackerDataAvailability_Factor|float(8)|X||
|GHIConsistency_Factor|float(8)|X||
|GHIDataAvailability_Factor|float(8)|X||
|GIIConsistency_Factor|float(8)|X||
|GIIDataAvailability_Factor|float(8)|X||
|ModuleTempConsistency_Factor|float(8)|X||
|ModuleTempDataAvailability_Factor|float(8)|X||
|SoilingDataAvailability_Factor|float(8)|X||
|AmbientTempConsistency_Factor|float(8)|X||
|AmbientTempDataAvailability_Factor|float(8)|X||
|WindSpeedConsistency_Factor|float(8)|X||
|WindSpeedDataAvailability_Factor|float(8)|X||
|MeterConsistency_Deviation|float(8)|X||
|InverterACOutputConsistency_Deviation|float(8)|X||
|DCLevelConsistency_Deviation|float(8)|X||
|TrackerDataAvailability_Deviation|float(8)|X||
|GHIConsistency_Deviation|float(8)|X||
|GHIDataAvailability_Deviation|float(8)|X||
|GIIConsistency_Deviation|float(8)|X||
|GIIDataAvailability_Deviation|float(8)|X||
|ModuleTempConsistency_Deviation|float(8)|X||
|ModuleTempDataAvailability_Deviation|float(8)|X||
|SoilingDataAvailability_Deviation|float(8)|X||
|AmbientTempConsistency_Deviation|float(8)|X||
|AmbientTempDataAvailability_Deviation|float(8)|X||
|WindSpeedConsistency_Deviation|float(8)|X||
|WindSpeedDataAvailability_Deviation|float(8)|X||


## FactDataQualityDetails

Schema name: dbo

Description: Fact table with detailed data quality KPI data per facility and day


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|X||
|Date|date(3)|X||
|DataQualitySubFactor|nvarchar(128)|X||
|EquipmentName|nvarchar(510)|X||
|EquipmentGroup|nvarchar(510)|X||
|ValueName|nvarchar(510)|X||
|Value|float(8)|X||
|Diff|float(8)|X||
|DiffUnit|nvarchar(20)|X||
|RowOrder|int(4)|X||


## FactDeliveryPoint

Schema name: dbo

Description: Fact table with aggregated data for a deliverypoint/facility in 10 min intervals


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactDeliveryPointID|int(4)|||
|DeliveryPointKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|FeedInPower_kW|float(8)|X||
|FeedInEnergy_kWh|float(8)|X||
|FeedInEnergy_Acc_kWh|float(8)|X||
|FeedInReactivePower_kVAr|float(8)|X||
|FeedInReactiveEnergy_kVArh|float(8)|X||
|FeedInReactiveEnergy_Acc_kVArh|float(8)|X||
|ConsumptionPower_kW|float(8)|X||
|ConsumptionEnergy_kWh|float(8)|X||
|ConsumptionEnergy_Acc_kWh|float(8)|X||
|ConsumptionReactivePower_kVAr|float(8)|X||
|ConsumptionReactiveEnergy_kVArh|float(8)|X||
|ConsumptionReactiveEnergy_Acc_kVArh|float(8)|X||
|Frequency_Hz|float(8)|X||
|Voltage_V|float(8)|X||
|Current_A|float(8)|X||
|PowerFactor|float(8)|X||
|Availability|float(8)|X||
|PeriodDuration_s|float(8)|X||
|Irradiation_acc|float(8)|X||
|Irradiation_acc_horizontal|float(8)|X||
|EnvironmentTemperature|float(8)|X||
|ModuleTemperature|float(8)|X||
|CellTemperatureEstimated|float(8)|X||
|WindSpeed|float(8)|X||
|HorizontalIrradiation_Pyranometer|float(8)|X||
|InClineIrradiation_Pyranometer|float(8)|X||
|RefCellIrradiation_1_Dirty|float(8)|X||
|RefCellIrradiation_2_Cleaned|float(8)|X||
|AirPressure|float(8)|X||
|RainIntensity|float(8)|X||
|WindDirection|float(8)|X||
|Humidity|float(8)|X||
|RainAmount|float(8)|X||
|DataQuality|int(4)|X||
|ProductionManuallyAdjusted|float(8)|X||
|ProcessedStatus|int(4)|X||
|InClineIrradiation_Pyranometer_Modified|float(8)|X||
|GridDownTimeSeconds|float(8)|X||
|GridDownTimeEstimatedProductionLoss|float(8)|X||
|InverterDownTimeSeconds|float(8)|X||
|InverterDownTimeEstimatedProductionLoss|float(8)|X||
|TrackerDownTimeSeconds|float(8)|X||
|TrackerDownTimeEstimatedProductionLoss|float(8)|X||
|Soiling|float(8)|X||
|SoilingWeighted|float(8)|X||
|InclineIrradianceForProductionLoss|float(8)|X||
|SoilingIndex|float(8)|X||
|ExtWeatherSource|int(4)|X||
|ManualWeatherSource|int(4)|X||
|InClineIrradiation_Pyranometer_East|float(8)|X||
|InClineIrradiation_Pyranometer_West|float(8)|X||
|Irradiation_acc_East|float(8)|X||
|Irradiation_acc_West|float(8)|X||
|ModuleTemperature_East|float(8)|X||
|ModuleTemperature_West|float(8)|X||
|EstimatedProduction|float(8)|X||
|EstimatedProductionForCurtailmentAndClipping|float(8)|X||
|CurtailmentEstimatedProductionLoss|float(8)|X||
|ClippingEstimatedProductionLoss|float(8)|X||
|CurtailmentSeconds|float(8)|X||
|SoilingEstimatedProductionLoss|float(8)|X||
|StringDownTimeEstimatedProductionLoss|float(8)|X||
|StringAvailability|float(8)|X||
|InverterDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|TrackerDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|CurtailmentEstimatedProductionLossNonFiltered|float(8)|X||
|ClippingEstimatedProductionLossNonFiltered|float(8)|X||
|SoilingEstimatedProductionLossNonFiltered|float(8)|X||
|StringDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|StringDownTimeSeconds|float(8)|X||
|GridDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|ClippingSeconds|float(8)|X||
|SnowDepth|float(8)|X||
|SnowEstimatedProductionLossNonFiltered|float(8)|X||
|SnowEstimatedProductionLoss|float(8)|X||
|HasSnowLoss|bit(1)|X||
|ExtWeather_InclineIrradiation|float(8)|X||
|ProductionManualCorrectionFactor|float(8)|X||
|SoilingIndexDailyFiltered|float(8)|X||
|SnowLossPR|float(8)|X||
|EstimatedProductionForSnowLoss|float(8)|X||
|HasSnowLoss_ManualOverride|bit(1)|X||
|GlobalEmissionFactor|float(8)|X||
|HasDeemedEnergy|bit(1)|X||
|EstimatedProductionForDeemedEnergy|float(8)|X||
|DeemedEnergy|float(8)|X||
|EstimatedProductionFromReferenceInverters|float(8)|X||
|CurtailmentEstimatedProductionLossFromReferenceInverters|float(8)|X||
|ProductionReferenceInverters|float(8)|X||
|ConsumptionEnergyAUX|float(8)|X||
|ConsumptionEnergyTotal|float(8)|X||
|NoSoilingOverride|bit(1)|X||
|NoStringLossesOverride|bit(1)|X||
|TrackerProductionLosses_Total|float(8)|X||
|TrackerProductionLosses_Total2|float(8)|X||
|TrackerProductionLosses_Failure|float(8)|X||
|TrackerProductionLosses_ManualParked|float(8)|X||
|TrackerProductionLosses_WindStow|float(8)|X||
|TrackerProductionLosses_OutOfPosition|float(8)|X||
|EstimatedProductionForGridDownTime|float(8)|X||
|TrackerMeasuredAngle50Percentile|float(8)|X||
|TrackerMeasuredAngle10Percentile|float(8)|X||
|TrackerMeasuredAngle90Percentile|float(8)|X||
|TrackerSetpointAngle50Percentile|float(8)|X||


## FactDeliveryPointDailyData

Schema name: dbo

Description: Fact table with aggregated data for a deliverypoint/facility in daily intervals. Aggregated from FactDeliveryPoint


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactDeliveryPointDailyDataID|int(4)|||
|FacilityKey|int(4)|||
|Date|date(3)|||
|FeedInPower_kW|float(8)|X||
|FeedInEnergy_kWh|float(8)|X||
|FeedInReactivePower_kVAr|float(8)|X||
|FeedInReactiveEnergy_kVArh|float(8)|X||
|ConsumptionPower_kW|float(8)|X||
|ConsumptionEnergy_kWh|float(8)|X||
|ConsumptionReactivePower_kVAr|float(8)|X||
|ConsumptionReactiveEnergy_kVArh|float(8)|X||
|Frequency_Hz|float(8)|X||
|Voltage_V|float(8)|X||
|Current_A|float(8)|X||
|PowerFactor|float(8)|X||
|Irradiation_acc|float(8)|X||
|Irradiation_acc_horizontal|float(8)|X||
|EnvironmentTemperature|float(8)|X||
|ModuleTemperature|float(8)|X||
|CellTemperatureEstimated|float(8)|X||
|WindSpeed|float(8)|X||
|HorizontalIrradiation_Pyranometer|float(8)|X||
|InClineIrradiation_Pyranometer|float(8)|X||
|RefCellIrradiation_1_Dirty|float(8)|X||
|RefCellIrradiation_2_Cleaned|float(8)|X||
|AirPressure|float(8)|X||
|RainIntensity|float(8)|X||
|WindDirection|float(8)|X||
|Humidity|float(8)|X||
|RainAmount|float(8)|X||
|ProductionManuallyAdjusted|float(8)|X||
|InclineIrradianceForProductionLoss|float(8)|X||
|InClineIrradiation_Pyranometer_East|float(8)|X||
|InClineIrradiation_Pyranometer_West|float(8)|X||
|Irradiation_acc_East|float(8)|X||
|Irradiation_acc_West|float(8)|X||
|ModuleTemperature_East|float(8)|X||
|ModuleTemperature_West|float(8)|X||
|EstimatedProduction|float(8)|X||
|EstimatedProductionForCurtailmentAndClipping|float(8)|X||
|EstimatedProductionForSnowLoss|float(8)|X||
|EstimatedProductionForDeemedEnergy|float(8)|X||
|GridDownTimeSeconds|float(8)|X||
|GridDownTimeEstimatedProductionLoss|float(8)|X||
|GridDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|InverterDownTimeSeconds|float(8)|X||
|InverterDownTimeEstimatedProductionLoss|float(8)|X||
|InverterDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|TrackerDownTimeSeconds|float(8)|X||
|TrackerDownTimeEstimatedProductionLoss|float(8)|X||
|TrackerDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|CurtailmentSeconds|float(8)|X||
|CurtailmentEstimatedProductionLoss|float(8)|X||
|CurtailmentEstimatedProductionLossNonFiltered|float(8)|X||
|ClippingSeconds|float(8)|X||
|ClippingEstimatedProductionLoss|float(8)|X||
|ClippingEstimatedProductionLossNonFiltered|float(8)|X||
|Soiling|float(8)|X||
|SoilingIndex|float(8)|X||
|SoilingIndexDailyFiltered|float(8)|X||
|SoilingEstimatedProductionLoss|float(8)|X||
|SoilingEstimatedProductionLossNonFiltered|float(8)|X||
|StringDownTimeSeconds|float(8)|X||
|StringAvailability|float(8)|X||
|StringDownTimeEstimatedProductionLoss|float(8)|X||
|StringDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|SnowDepth|float(8)|X||
|SnowLossPR|float(8)|X||
|SnowEstimatedProductionLoss|float(8)|X||
|SnowEstimatedProductionLossNonFiltered|float(8)|X||
|ExtWeather_InclineIrradiation|float(8)|X||
|DeemedEnergy|float(8)|X||
|ProductionManualCorrectionFactor|float(8)|X||
|GlobalEmissionFactor|float(8)|X||


## FactEnercastLiveMeterData

Schema name: dbo

Description: Fact table with data for feeding Enercast forecasting service with live data


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactEnercastLiveMeterDataID|int(4)|||
|FacilityKey|int(4)|||
|SubFacilityKey|int(4)|X||
|PeriodStartTimeUTC|datetime(8)|||
|PeriodEndTimeUTC|datetime(8)|||
|Power_Average_kW|float(8)|X||
|Available_Capacity_kW|float(8)|X||
|Power_Output_Limit_kW|float(8)|X||


## FactEnercastParameters

Schema name: dbo

Description: Fact table parameters for facility to configure Enercast forecast download


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|SubFacilityKey|int(4)|X||
|AssetId|nvarchar(128)|||
|AssetName|nvarchar(128)|||
|Percentile|float(8)|X||


## FactExtForecast

Schema name: dbo

Description: Fact table external forecast data. Data down to 10 min level based on provider resolution


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactExtForecastID|bigint(8)|||
|ExtForecastTypeKey|int(4)|||
|FacilityKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|HorizontalIrradiation|float(8)|X||
|InclineIrradiation|float(8)|X||
|DiffuseIrradiation|float(8)|X||
|EnvironmentTemperature|float(8)|X||
|ModuleTemperature|float(8)|X||
|WindSpeed|float(8)|X||
|WindDirection|float(8)|X||
|Power_kW|float(8)|X||
|EnergyProduction_kWh|float(8)|X||
|Humidity|float(8)|X||
|AirPressure|float(8)|X||
|RainAmount|float(8)|X||
|InClineIrradiation_East|float(8)|X||
|InClineIrradiation_West|float(8)|X||
|ModuleTemperature_East|float(8)|X||
|ModuleTemperature_West|float(8)|X||
|SnowDepth|float(8)|X||
|LocalTimeForecastLoad|datetime(8)|X||
|SubFacilityKey|int(4)|X||
|SolarZenith|float(8)|X||
|SolarAzimuth|float(8)|X||
|CloudOpacity|float(8)|X||
|LastUpdateTime|datetime(8)|X||
|Availability|float(8)|X||


## FactExtWeather

Schema name: dbo

Description: Fact table external weather data. Data down to 10 min level based on provider resolution


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactExtWeatherID|bigint(8)|||
|ExtWeatherTypeKey|int(4)|||
|FacilityKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|HorizontalIrradiation|float(8)|X||
|InclineIrradiation|float(8)|X||
|DiffuseIrradiation|float(8)|X||
|EnvironmentTemperature|float(8)|X||
|ModuleTemperature|float(8)|X||
|WindSpeed|float(8)|X||
|WindDirection|float(8)|X||
|Power_kW|float(8)|X||
|EnergyProduction_kWh|float(8)|X||
|Humidity|float(8)|X||
|RainAmount|float(8)|X||
|AirPressure|float(8)|X||
|InClineIrradiation_East|float(8)|X||
|InClineIrradiation_West|float(8)|X||
|ModuleTemperature_East|float(8)|X||
|ModuleTemperature_West|float(8)|X||
|SnowDepth|float(8)|X||
|SubFacilityKey|int(4)|X||
|SolarZenith|float(8)|X||
|SolarAzimuth|float(8)|X||
|CloudOpacity|float(8)|X||
|LastUpdateTime|datetime(8)|X||


## FactFacilityStatus

Schema name: dbo

Description: Fact table for facility/plant state results.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactFacilityStatusID|int(4)|||
|FacilityKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|StateStartTime|datetime(8)|||
|StateEndTime|datetime(8)|X||
|StateDuration|float(8)|X||
|StateCode|int(4)|X||
|StateName|nvarchar(510)|||
|StateClass|nvarchar(510)|||
|Comment|nvarchar(2048)|||
|IsOperation|bit(1)|||
|IsFailure|bit(1)|||
|IsIdle|bit(1)|||
|IsLineRestraint|bit(1)|||
|IsNotScheduled|bit(1)|||
|DataQuality|int(4)|X||
|Processed|bit(1)|||
|Updated|bit(1)|X||


## FactForecast

Schema name: dbo

Description: Fact table for forecast/budget data


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactForecastID|int(4)|||
|FacilityKey|int(4)|X||
|ForecastKey|int(4)|||
|DateAndHourKey|int(4)|||
|ForecastStartTime|datetime(8)|||
|ForecastEndTime|datetime(8)|||
|ForecastDuration|float(8)|||
|HorizontalIrradiation|float(8)|X||
|HorizontalIrradiation_acc|float(8)|X||
|InClineIrradiation|float(8)|X||
|InClineIrradiation_acc|float(8)|X||
|EnvironmentTemperature|float(8)|X||
|ModuleTemperatureDaylight|float(8)|X||
|EnergyProduction|float(8)|X||
|PerformanceRatio|float(8)|X||
|MaxAvailableGridPower|float(8)|X||
|NominalDCPower|float(8)|X||
|PlantAvailability|float(8)|X||
|ModifiedPlantAvailability|float(8)|X||
|ModifiedGridAvailability|float(8)|X||
|NetTariff|float(8)|X||
|ChangedTime|datetime(8)|X||
|ChangedBy|nvarchar(510)|X||
|DataQuality|int(4)|X||
|UseDataInApp|bit(1)|X||
|ActualNetTariff|float(8)|X||
|SpecialCompensation|float(8)|X||
|GlobalEmissionFactor|float(8)|X||
|ActualNetTariff2|float(8)|X||
|SubFacilityKey|int(4)|X||
|ClippingPercentage|float(8)|X||


## FactForecastAdjusted

Schema name: dbo

Description: Fact table for adjusted forecast/budget data


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactForecastAdjustedID|bigint(8)|||
|FacilityKey|int(4)|||
|ForecastType|nvarchar(40)|||
|ForecastStartTime|datetime(8)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|HoursAhead|int(4)|||
|PreviousPeriodEnergyForecast|float(8)|X||
|PreviousPeriodEnergyProduction|float(8)|X||
|PreviousPeriodProductionForecastRatio|float(8)|X||
|PreviousPeriodAvailability|float(8)|X||
|PreviousPeriodAvailabilityForecast|float(8)|X||
|AvailabilityRatio|float(8)|X||
|PreviousPeriodPowerFactor|float(8)|X||
|ForecastAvailability|float(8)|X||
|ForecastEnergyInitial|float(8)|X||
|ForecastEnergyAdjusted|float(8)|X||
|ForecastMinActivePower|float(8)|X||
|ForecastMaxActivePower|float(8)|X||
|ForecastMinReactivePower|float(8)|X||
|ForecastMaxReactivePower|float(8)|X||
|MeasuredAvailability|float(8)|X||
|MeasuredEnergy|float(8)|X||
|MeasuredMinActivePower|float(8)|X||
|MeasuredMaxActivePower|float(8)|X||
|MeasuredMinReactivePower|float(8)|X||
|MeasuredMaxReactivePower|float(8)|X||


## FactInverter

Schema name: dbo

Description: Fact table inverter data, 10 min periods. Data from timeseries database and aggregated/augmented data from states.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactInverterID|int(4)|||
|InverterKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|Energy_kWh|float(8)|X||
|Power_kW|float(8)|X||
|Energy_kWh_Acc|float(8)|X||
|PowerReactive_kVAr|float(8)|X||
|DataQuality|int(4)|X||
|EstimatedProductionLoss_Wh|float(8)|X||
|DownTimeSeconds|float(8)|X||
|DCPower_kW|float(8)|X||
|AC_DC_PowerRatio|float(8)|X||
|DCVoltage|float(8)|X||
|DCCurrent|float(8)|X||
|EstimatedProductionLoss_Wh_NonFiltered|float(8)|X||
|PowerEstimateFirstPrinciples|float(8)|X||
|PowerEstimateML|float(8)|X||
|Avg_Degradation|float(8)|X||
|Low_Degradation|float(8)|X||
|High_Degradation|float(8)|X||


## FactInverterDailyData

Schema name: dbo

Description: Fact table inverter data, daily values. Aggregated from FactInverter.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactInverterDailyDataID|int(4)|||
|InverterKey|int(4)|||
|FacilityKey|int(4)|||
|Date|date(3)|||
|Energy_kWh|float(8)|X||
|DownTimeSeconds|float(8)|X||
|EstimatedProductionLoss_Wh|float(8)|X||
|EstimatedProductionLoss_Wh_NonFiltered|float(8)|X||
|Power_kW|float(8)|X||
|PowerReactive_kVAr|float(8)|X||
|AC_DC_PowerRatio|float(8)|X||
|DCPower_kW|float(8)|X||
|DCVoltage|float(8)|X||
|DCCurrent|float(8)|X||
|RelativeEnergy_kWh_kWp|float(8)|X||
|RelativeEnergy_kWh_kWp_Median|float(8)|X||
|AC_DC_PowerRatio_Median|float(8)|X||
|PR_gross_STC|float(8)|X||


## FactInverterSoiling

Schema name: dbo

Description: Fact table for estimated soiling values, daily level per inverter


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactInverterSoilingID|int(4)|||
|InverterKey|int(4)|||
|Date|date(3)|||
|CPR_Soiling|float(8)|X||
|SoilingRatio|float(8)|X||
|SoilingIndex|float(8)|X||
|SoilingRate|float(8)|X||
|Avg_Degradation|float(8)|X||
|Low_Degradation|float(8)|X||
|High_Degradation|float(8)|X||


## FactInverterStatus

Schema name: dbo

Description: Fact table for inverter state information. State logging based on signals from inverter, with start time, end time and state codes.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactInverterStatusID|bigint(8)|||
|FacilityKey|int(4)|||
|InverterKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|StateCode|int(4)|X||
|StateStartTime|datetime(8)|||
|StateEndTime|datetime(8)|X||
|StateDuration|float(8)|X||
|StateName|nvarchar(510)|||
|StateClass|nvarchar(510)|||
|Comment|nvarchar(2048)|||
|IsOperation|bit(1)|||
|IsFailure|bit(1)|||
|IsIdle|bit(1)|||
|IsLineRestraint|bit(1)|||
|IsNotScheduled|bit(1)|||
|DataQuality|int(4)|X||
|Processed|bit(1)|||
|Updated|bit(1)|X||


## FactInverterTypeEfficiency

Schema name: dbo

Description: Fact table with efficiency curve data per inverter type


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|InverterTypeKey|int(4)|||
|PowerDCMin|float(8)|||
|PowerDCMax|float(8)|X||
|InverterEfficiency|float(8)|X||


## FactLogBook

Schema name: dbo

Description: Fact table with log book data from plant operators.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|FactLogBookID|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|DateAndHourKey|int(4)|X||
|MinuteKey|int(4)|X||
|LogBookType|nvarchar(510)|||
|LogComment|nvarchar(max)|||
|LogLastChangedTime|datetime(8)|X||
|LogUser|nvarchar(128)|X||


## FactMeteologicaParameters

Schema name: dbo

Description: Fact table with Meteologica forecast setup per facility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|UseHistoricalData|bit(1)|||
|UseExternalForecast|bit(1)|||
|SendObservationData|bit(1)|X||
|LastObservationData|datetime(8)|X||
|UpdateIntervalMinutesObservationData|int(4)|X||
|SubFacilityKey|int(4)|X||


## FactMeter

Schema name: dbo

Description: Fact table metering data, 10 min periods. Data from timeseries database and aggregated/augmented data from states.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactMeterID|int(4)|||
|MeterKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|FeedInPower_kW|float(8)|X||
|FeedInEnergy_kWh|float(8)|X||
|FeedInEnergy_Acc_kWh|float(8)|X||
|FeedInReactivePower_kVAr|float(8)|X||
|FeedInReactiveEnergy_kVArh|float(8)|X||
|FeedInReactiveEnergy_Acc_kVArh|float(8)|X||
|ConsumptionPower_kW|float(8)|X||
|ConsumptionEnergy_kWh|float(8)|X||
|ConsumptionEnergy_Acc_kWh|float(8)|X||
|ConsumptionReactivePower_kVAr|float(8)|X||
|ConsumptionReactiveEnergy_kVArh|float(8)|X||
|ConsumptionReactiveEnergy_Acc_kVArh|float(8)|X||
|Frequency_Hz|float(8)|X||
|Voltage_V|float(8)|X||
|Current_A|float(8)|X||
|PowerFactor|float(8)|X||
|DataQuality|int(4)|X||
|DataQualityMessage|nvarchar(max)|X||
|MeterReset|bit(1)|X||


## FactModuleTypeEfficiency

Schema name: dbo

Description: Fact table with efficiency curve data per module type


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ModuleTypeKey|int(4)|||
|InclineIrradiationMin|float(8)|||
|InclineIrradiationMax|float(8)|X||
|ModuleEfficiency|float(8)|X||


## FactOperationStatus

Schema name: dbo

Description: Fact table with operation status text comment per facility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|PlantComment|nvarchar(max)|X||
|CentralComment|nvarchar(max)|X||
|ChangeTime|datetime(8)|X||


## FactOptimalTrackerAngles

Schema name: dbo

Description: Fact table optimal tracker angle per facility and 10 minute periode. Calculated and stored from using PVLib and plant location


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|DateAndHourKey|int(4)|X||
|MinuteKey|int(4)|X||
|SolarAzimuth|float(8)|X||
|SolarZenith|float(8)|X||
|OptimalAngle|float(8)|X||
|OptimalAngleLimited|float(8)|X||


## FactPlannedAvailability

Schema name: dbo

Description: Fact table with planned availability per time period and facility. Data from manually entered operator information on planned downtime.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactPlannedAvailabilityID|int(4)|||
|FacilityKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|NominalPowerAvailability|float(8)|X||
|PlannedPowerUnavailability|float(8)|X||
|PlannedPowerAvailability|float(8)|X||


## FactPlannedOutages

Schema name: dbo

Description: Fact table with planned outages. With start time, end time and reason.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactPlannedOutagesID|int(4)|||
|FacilityKey|int(4)|||
|StartTime|datetime(8)|||
|EndTime|datetime(8)|||
|PowerReduction|float(8)|||
|IsPlanned|bit(1)|||
|Comment|nvarchar(2048)|X||


## FactPPC

Schema name: dbo

Description: Fact table PPC data, 10 min periods. Data from timeseries database and aggregated/augmented data from states.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactPPCID|int(4)|||
|PPCKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|ActivePowerSetpointAverage|float(8)|X||
|ActivePowerSetpointMax|float(8)|X||
|ActivePowerSetpointMin|float(8)|X||
|ActivePowerMeasureAverage|float(8)|X||
|ActivePowerMeasureMax|float(8)|X||
|ActivePowerMeasureMin|float(8)|X||
|CurtailmentFactorAverage|float(8)|X||
|CurtailmentFactorMax|float(8)|X||
|IsCurtailment|bit(1)|X||
|IsClipping|bit(1)|X||


## FactProductionCorrection

Schema name: dbo

Description: Fact table for production correction factors used for performance reporting. Manually entered data.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|Date|date(3)|||
|NumInvertersDown|float(8)|X||
|NumTrackersDown|float(8)|X||
|InclineIrradiation|float(8)|X||
|HorizontalIrradiation|float(8)|X||
|TF|float(8)|X||
|IrrLossInverter|float(8)|X||
|IrrLossTracker|float(8)|X||
|IrrLossTotal|float(8)|X||
|ProductionManualCorrectionFactor|float(8)|X||
|Comment|nvarchar(max)|X||
|NotificationDone|bit(1)|X||


## FactSolarGISParameters

Schema name: dbo

Description: Fact table with SolarGIS forecast setup per facility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|Longitude|float(8)|X||
|Lattitude|float(8)|X||
|UseExternalForecast|bit(1)|X||
|UseHistoricalData|bit(1)|X||
|TerrainShading|bit(1)|X||
|TerrainElevation|float(8)|X||
|TerrainAzimuth|float(8)|X||
|TerrainTilt|float(8)|X||
|Horizon|nvarchar(510)|X||
|GeometryType|nvarchar(510)|X||
|GeometryAzimuth|float(8)|X||
|GeometryTilt|float(8)|X||
|GeometryRotationLimitEast|float(8)|X||
|GeometryRotationLimitWest|float(8)|X||
|GeometryBackTracking|bit(1)|X||
|SystemInstallationType|nvarchar(510)|X||
|SystemSelfShading|bit(1)|X||
|ModuleType|nvarchar(510)|X||
|ModuleSurfaceReflectance|float(8)|X||
|ModulePowerToleranceLow|float(8)|X||
|ModulePowerToleranceHigh|float(8)|X||
|ModuleNominalOperatingCellTemp|float(8)|X||
|ModuleOpenCircuitVoltageCoeff|float(8)|X||
|ModuleShortCircuitCurrentCoeff|float(8)|X||
|ModulePmaxCoeff|float(8)|X||
|InverterInterconnection|nvarchar(510)|X||
|InverterEfficiencyConstantPercent|float(8)|X||
|InverterStartPower|float(8)|X||
|InverterLimitationACPower|float(8)|X||
|InverterNominalDCPower|float(8)|X||
|LossesACLossesCables|float(8)|X||
|LossesACLossesTransformer|float(8)|X||
|LossesDCLossesCables|float(8)|X||
|LossesDCLossesMismatch|float(8)|X||
|LossesDCLossesSnowPollution|float(8)|X||
|LossesDCLossesMonthlySnowPollution|nvarchar(510)|X||
|TopologyXSIType|nvarchar(510)|X||
|TopologyType|nvarchar(510)|X||
|TopologyRelativeSpacing|float(8)|X||
|ForecastAPIKey|nvarchar(128)|X||
|HistoricalAPIKey|nvarchar(128)|X||
|GeometryAzimuthEast|float(8)|X||
|GeometryAzimuthWest|float(8)|X||
|SubFacilityKey|int(4)|X||
|Degradation|float(8)|X||
|DegradationFirstYear|float(8)|X||


## FactSolCastParameters

Schema name: dbo

Description: Fact table with SolCast forecast setup per facility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|SubFacilityKey|int(4)|X||
|ResourceId|nvarchar(128)|||
|Api_key|nvarchar(128)|||


## FactStringIRScan

Schema name: dbo

Description: Fact table for string IR scan data. To be manually uploaded


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|StringKey|int(4)|||
|ModuleNo|int(4)|X||
|GPSLatitudeSupplier|float(8)|X||
|GPSLongitudeSupplier|float(8)|X||
|ReportID|nvarchar(128)|X||
|DefectID|nvarchar(128)|X||
|ImageCaptureTime|datetime(8)|X||
|Severity|nvarchar(20)|X||
|DefectCategory|nvarchar(128)|X||
|SignatureTemperature|float(8)|X||
|ReferenceTemperature|float(8)|X||
|DeltaTemperature|float(8)|X||
|Url_IR|nvarchar(1024)|X||
|Url_VIS|nvarchar(1024)|X||
|SeveritySupplier|nvarchar(20)|X||
|DefectCategorySupplier|nvarchar(128)|X||
|Comments|nvarchar(max)|X||


## FactStringMonitor

Schema name: dbo

Description: Fact table with string channel measuement data. Data per date, split into morning, midday and afternoon data. Aggregated and augmented data.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactStringMonitorID|bigint(8)|||
|StringMonitorKey|int(4)|||
|Date|date(3)|||
|DateAndHourKey|int(4)|X||
|AmpereAverageMorning|float(8)|X||
|AmpereHoursMorning|float(8)|X||
|VoltageMorning|float(8)|X||
|PowerMorning|float(8)|X||
|EnergyMorning|float(8)|X||
|EnergyGroupAverageMorning|float(8)|X||
|EnergyPlantAverageMorning|float(8)|X||
|AmpereAverageMidDay|float(8)|X||
|AmpereHoursMidDay|float(8)|X||
|VoltageMidDay|float(8)|X||
|PowerMidDay|float(8)|X||
|EnergyMidDay|float(8)|X||
|EnergyGroupAverageMidDay|float(8)|X||
|EnergyPlantAverageMidDay|float(8)|X||
|AmpereAverageAfterNoon|float(8)|X||
|AmpereHoursAfterNoon|float(8)|X||
|VoltageAfterNoon|float(8)|X||
|PowerAfterNoon|float(8)|X||
|EnergyAfterNoon|float(8)|X||
|EnergyGroupAverageAfterNoon|float(8)|X||
|EnergyPlantAverageAfterNoon|float(8)|X||
|HasWarning1Morning|bit(1)|X||
|HasWarning2Morning|bit(1)|X||
|HasWarning3Morning|bit(1)|X||
|QualityOK|bit(1)|||
|HasWarning1MidDay|bit(1)|X||
|HasWarning2MidDay|bit(1)|X||
|HasWarning3MidDay|bit(1)|X||
|HasWarning1AfterNoon|bit(1)|X||
|HasWarning2AfterNoon|bit(1)|X||
|HasWarning3AfterNoon|bit(1)|X||
|QualityMorning|int(4)|X||
|QualityMidDay|int(4)|X||
|QualityAfterNoon|int(4)|X||
|EnergyGroupMedianMorning|float(8)|X||
|EnergyPlantMedianMorning|float(8)|X||
|EnergyGroupMedianMidDay|float(8)|X||
|EnergyPlantMedianMidDay|float(8)|X||
|EnergyGroupMedianAfterNoon|float(8)|X||
|EnergyPlantMedianAfterNoon|float(8)|X||
|SpecificEnergyMorning|float(8)|X||
|SpecificEnergyMidDay|float(8)|X||
|SpecificEnergyAfterNoon|float(8)|X||
|SpecificEnergyGroupMedianMorning|float(8)|X||
|SpecificEnergyGroupMedianMidDay|float(8)|X||
|SpecificEnergyGroupMedianAfterNoon|float(8)|X||
|SpecificEnergyPlantMedianMorning|float(8)|X||
|SpecificEnergyPlantMedianMidDay|float(8)|X||
|SpecificEnergyPlantMedianAfterNoon|float(8)|X||
|NominalPower|float(8)|X||
|VoltagePlantAvgMorning|float(8)|X||
|VoltagePlantAvgMidDay|float(8)|X||
|VoltagePlantAvgAfterNoon|float(8)|X||
|PerfIndMorningGroup|float(8)|X||
|PerfIndMidDayGroup|float(8)|X||
|PerfIndAfternoonGroup|float(8)|X||
|PerfIndMorningPlant|float(8)|X||
|PerfIndMidDayPlant|float(8)|X||
|PerfIndAfternoonPlant|float(8)|X||
|CPR|float(8)|X||
|AvailabilityMorning|float(8)|X||
|AvailabilityMidDay|float(8)|X||
|AvailabilityAfterNoon|float(8)|X||
|CPR_PeakPerformance|float(8)|X||
|FaultCode|int(4)|X||
|Soiling|float(8)|X||
|CPR_Soiling|float(8)|X||
|TrackerDownPercentageMorning|float(8)|X||
|TrackerDownPercentageMidDay|float(8)|X||
|TrackerDownPercentageAfterNoon|float(8)|X||
|EstimatedEnergyLossesMorning|float(8)|X||
|EstimatedEnergyLossesMidDay|float(8)|X||
|EstimatedEnergyLossesAfterNoon|float(8)|X||


## FactSubFacility

Schema name: dbo

Description: Fact table with aggregated data for a sub-facility in 10 min intervals


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactSubFacilityID|int(4)|||
|FacilityKey|int(4)|||
|SubFacilityKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|FeedInPower_kW|float(8)|X||
|FeedInEnergy_kWh|float(8)|X||
|FeedInEnergy_Acc_kWh|float(8)|X||
|FeedInReactivePower_kVAr|float(8)|X||
|FeedInReactiveEnergy_kVArh|float(8)|X||
|FeedInReactiveEnergy_Acc_kVArh|float(8)|X||
|ConsumptionPower_kW|float(8)|X||
|ConsumptionEnergy_kWh|float(8)|X||
|ConsumptionEnergy_Acc_kWh|float(8)|X||
|ConsumptionReactivePower_kVAr|float(8)|X||
|ConsumptionReactiveEnergy_kVArh|float(8)|X||
|ConsumptionReactiveEnergy_Acc_kVArh|float(8)|X||
|Frequency_Hz|float(8)|X||
|Voltage_V|float(8)|X||
|Current_A|float(8)|X||
|PowerFactor|float(8)|X||
|Availability|float(8)|X||
|PeriodDuration_s|float(8)|X||
|Irradiation_acc|float(8)|X||
|Irradiation_acc_horizontal|float(8)|X||
|EnvironmentTemperature|float(8)|X||
|ModuleTemperature|float(8)|X||
|CellTemperatureEstimated|float(8)|X||
|WindSpeed|float(8)|X||
|HorizontalIrradiation_Pyranometer|float(8)|X||
|InClineIrradiation_Pyranometer|float(8)|X||
|RefCellIrradiation_1_Dirty|float(8)|X||
|RefCellIrradiation_2_Cleaned|float(8)|X||
|AirPressure|float(8)|X||
|RainIntensity|float(8)|X||
|WindDirection|float(8)|X||
|Humidity|float(8)|X||
|RainAmount|float(8)|X||
|DataQuality|int(4)|X||
|ProductionManuallyAdjusted|float(8)|X||
|ProcessedStatus|int(4)|X||
|InClineIrradiation_Pyranometer_Modified|float(8)|X||
|GridDownTimeSeconds|float(8)|X||
|GridDownTimeEstimatedProductionLoss|float(8)|X||
|InverterDownTimeSeconds|float(8)|X||
|InverterDownTimeEstimatedProductionLoss|float(8)|X||
|TrackerDownTimeSeconds|float(8)|X||
|TrackerDownTimeEstimatedProductionLoss|float(8)|X||
|Soiling|float(8)|X||
|SoilingWeighted|float(8)|X||
|InclineIrradianceForProductionLoss|float(8)|X||
|SoilingIndex|float(8)|X||
|InClineIrradiation_Pyranometer_East|float(8)|X||
|InClineIrradiation_Pyranometer_West|float(8)|X||
|Irradiation_acc_East|float(8)|X||
|Irradiation_acc_West|float(8)|X||
|ModuleTemperature_East|float(8)|X||
|ModuleTemperature_West|float(8)|X||
|EstimatedProduction|float(8)|X||
|EstimatedProductionForCurtailmentAndClipping|float(8)|X||
|CurtailmentEstimatedProductionLoss|float(8)|X||
|ClippingEstimatedProductionLoss|float(8)|X||
|CurtailmentSeconds|float(8)|X||
|SoilingEstimatedProductionLoss|float(8)|X||
|StringDownTimeEstimatedProductionLoss|float(8)|X||
|StringAvailability|float(8)|X||
|InverterDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|TrackerDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|CurtailmentEstimatedProductionLossNonFiltered|float(8)|X||
|ClippingEstimatedProductionLossNonFiltered|float(8)|X||
|SoilingEstimatedProductionLossNonFiltered|float(8)|X||
|StringDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|StringDownTimeSeconds|float(8)|X||
|GridDownTimeEstimatedProductionLossNonFiltered|float(8)|X||
|ClippingSeconds|float(8)|X||
|SnowEstimatedProductionLossNonFiltered|float(8)|X||
|SnowEstimatedProductionLoss|float(8)|X||
|SnowDepth|float(8)|X||
|HasSnowLoss|bit(1)|X||
|ExtWeather_InclineIrradiation|float(8)|X||
|ProductionManualCorrectionFactor|float(8)|X||
|SoilingIndexDailyFiltered|float(8)|X||
|NoSoilingOverride|bit(1)|X||


## FactTracker

Schema name: dbo

Description: Fact table tracker data, 10 min periods. Data from timeseries database and aggregated/augmented data from states.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactTrackerID|bigint(8)|||
|TrackerKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|MeasuredAngle|float(8)|X||
|SetpointAngle|float(8)|X||
|DeviationAngle|float(8)|X||
|TrackingQuality|int(4)|X||
|EstimatedProductionLoss_Wh|float(8)|X||
|DownTimeSeconds|float(8)|X||
|IsLast|bit(1)|||
|PlantAverageMeasuredAngle|float(8)|X||
|PlantMedianMeasuredAngle|float(8)|X||
|ProductionAvailability|float(8)|X||
|TrackerProductionLosses_Total|float(8)|X||
|TrackerProductionLosses_Total2|float(8)|X||
|DownTimeStateName|nvarchar(510)|X||


## FactTrackerDailyData

Schema name: dbo

Description: Fact table tracker data, daily values. Aggregated from FactTracker


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactTrackerDailyDataID|int(4)|||
|TrackerKey|int(4)|||
|FacilityKey|int(4)|||
|Date|date(3)|||
|LossesSemiParkedTrackers|float(8)|X||
|LossesFullyParkedTrackers|float(8)|X||
|MiddayDeviationFromMedian|float(8)|X||
|MiddayDeviationFromOptimal|float(8)|X||
|ProductionLosses_Total|float(8)|X||
|ProductionLosses_Failure|float(8)|X||
|ProductionLosses_ManualParked|float(8)|X||
|ProductionLosses_WindStow|float(8)|X||
|ProductionLosses_OutOfPosition|float(8)|X||
|DownTimeSeconds|float(8)|X||


## FactTrackerStatus

Schema name: dbo

Description: Fact table for tracker state information. State logging based on signals from tracker, with start time, end time and state codes.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactTrackerStatusID|int(4)|||
|FacilityKey|int(4)|||
|TrackerKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|StateStartTime|datetime(8)|||
|StateEndTime|datetime(8)|X||
|StateDuration|float(8)|X||
|StateName|nvarchar(510)|||
|StateClass|nvarchar(510)|||
|Comment|nvarchar(2048)|||
|IsOperation|bit(1)|||
|IsFailure|bit(1)|||
|IsIdle|bit(1)|||
|IsLineRestraint|bit(1)|||
|IsNotScheduled|bit(1)|||
|DataQuality|int(4)|X||
|Processed|bit(1)|||
|Updated|bit(1)|X||
|StateCode|int(4)|X||


## FactWeather

Schema name: dbo

Description: Fact table weather data, 10 min periods. Data from timeseries database and aggregated/augmented data from states.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FactWeatherID|int(4)|||
|FacilityKey|int(4)|||
|WeatherKey|int(4)|||
|DateAndHourKey|int(4)|||
|MinuteKey|int(4)|||
|PeriodStartTime|datetime(8)|||
|PeriodEndTime|datetime(8)|||
|EnvironmentTemperature|float(8)|X||
|ModuleTemperature|float(8)|X||
|WindSpeed|float(8)|X||
|HorizontalIrradiation_Pyranometer|float(8)|X||
|InClineIrradiation_Pyranometer|float(8)|X||
|RefCellIrradiation_1_Dirty|float(8)|X||
|RefCellIrradiation_2_Cleaned|float(8)|X||
|AirPressure|float(8)|X||
|RainIntensity|float(8)|X||
|WindDirection|float(8)|X||
|Humidity|float(8)|X||
|DataQuality|int(4)|X||
|Soiling|float(8)|X||
|RefCellTemp|float(8)|X||
|SoilingRatio|float(8)|X||
|DataQualityNew|int(4)|X||
|SoilingIndex|float(8)|X||
|SensorOutOfOrderMask|smallint(2)|X||
|SensorMedianFilterMask|smallint(2)|X||
|SensorLimitFilterMask|smallint(2)|X||
|SensorTrackerFilterMask|smallint(2)|X||
|SoilingIndexDailyFiltered|float(8)|X||
|RainAmountCounter|float(8)|X||
|RainAmount|float(8)|X||
|SoilingIndexDailyFiltered_NonOffset|float(8)|X||
|SoilingIndex_NonFiltered|float(8)|X||
|SoilingIndexDailyFilteredRollingMedian|float(8)|X||


