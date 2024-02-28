# Dim Tables

## DimDateAndHour

Schema name: dbo

Description: Dimension table having time dimension on hour resolution. Used by fact tables together with minute.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|DateAndHourKey|int(4)||Auto increment key|
|StartTime|datetime(8)||Start time, local time|
|EndTime|datetime(8)||End time, local time|
|Date|date(3)||Date, local time|
|Hour|int(4)||Hour of day, local time|
|WeekNo|int(4)||Week number, local time|
|MonthNo|int(4)||Month number, local time|
|MonthName|nvarchar(128)||Month name, local time|
|MonthNameShort|nvarchar(6)||Month name short, local time|
|Quarter|nvarchar(128)||Quarter, local time|
|Year|int(4)||Year, local time|
|ShiftName|nvarchar(128)||Shift name|
|YearWeek|nvarchar(128)||Year of week, local time|
|YearMonth|nvarchar(128)||Year of month, local time|
|DateShift|nvarchar(128)||Date of shift, local time|
|Day|nvarchar(128)||Day number, local time|
|UTCStartTime|datetime(8)||UTC Start Time|
|UTCEndTime|datetime(8)||UTC End Time|
|UTCYear|int(4)||UTC Year Number|
|UTCQuarter|int(4)||UTC Quarter Number|
|UTCMonth|int(4)||UTC Month Number|
|UTCDayInMonth|int(4)||UTC Day in Month|
|UTCHourOfDay|int(4)||UTC Hour of day|
|UTCISOWeekYear|int(4)||UTC ISO Week of Year|
|UTCISOWeekNo|int(4)||UTC Week No|
|UTCISOWeekDay|int(4)||UTC Day of Week|
|UTCEnglishMonthNameLong|nvarchar(128)||UTC English Month Name Long|
|UTCEnglishMonthNameShort|nvarchar(20)||UTC English Month Name Short|
|UTCEnglishWeekDayNameLong|nvarchar(128)||UTC English Week Day Long|
|UTCEnglishWeekDayNameShort|nvarchar(20)||UTC English Week Day Short|
|DayHour|nvarchar(128)|X|UTC Hour of day|


## DimDeliveryPoint

Schema name: dbo

Description: Dimension table defining the grid delivering point for a facility. Used by FactDeliverypoint for fact data. Link to facility.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|DeliveryPointKey|int(4)||Primary key column|
|DeliveryPointName|nvarchar(510)||Name of deliverypoint|
|DeliveryPointDescription|nvarchar(510)||Description of deliverypoint|
|FacilityKey|int(4)||Forreign key to DimFacility table|


## DimExtForecastType

Schema name: dbo

Description: Dimension table defining external forecast types. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ExtForecastTypeKey|int(4)||Primary key column|
|ExtForecastTypeName|nvarchar(128)||Name of external forecast|
|AutoExtractEnabled|bit(1)|X|1 if autoextracted from service provider, 0 if not (manual updated)|
|Description|nvarchar(510)||Description of external forecast|
|TagPrefix|nvarchar(128)|X|Prefix of tags in time series DB|
|Supplier|nvarchar(510)|X|Supplier of forecast service (e.g. SolarGIS)|
|FirstHourTrig|int(4)|X|First hour of day to trig forecast load|
|PowerForecastMethod|nvarchar(510)|X|Method of power forecast, dependent on provider|
|Percentiles|nvarchar(510)|X|Forecast percentile|
|GranularityMinutes|int(4)|X|Forecast time granularity|
|ExtractPeriodMinutes|int(4)|X|Minutes between each download from external service|
|ForecastStartMinute|int(4)|X||
|ForecastMinutesPeriod|int(4)|X|Length of forecast|
|RoundingStrategy|nvarchar(128)|X||
|Active|bit(1)|X|1 if active|


## DimExtForecastTypeWeights

Schema name: dbo

Description: Dimension table having setup for weighted forecast types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|TargetExtForecastTypeKey|int(4)||Forreign key to DimExtForecast table. Ext forecast type containing the new weighted forecast|
|SourceExtForecastTypeKey|int(4)||Forreign key to DimExtForecast table. Ext forecast type containing one of the forecast source|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|WeightFactor|float(8)||Weighting factor to multiply the energy forecast in source forecast|
|LastUpdated|datetime(8)|X||
|LastChangedTime|datetime(8)|X|Last time setup was updated/changed|
|LastChangedBy|nvarchar(128)|X|Last user changing the setup|
|ChangedComment|nvarchar(max)|X|Comment from user changing the setup|
|Active|bit(1)|X|1 if forecast setup is active|


## DimExtWeatherType

Schema name: dbo

Description: Dimension table having setup for external weather data integrations


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ExtWeatherTypeKey|int(4)||Primary key column|
|ExtWeatherTypeName|nvarchar(128)||Name of external weather|
|Description|nvarchar(510)||Description of external weather|
|TagPrefix|nvarchar(128)|X|Prefix of tags in time series DB|
|Supplier|nvarchar(510)|X|Supplier of external weather service (e.g. SolarGIS)|
|FirstHourTrig|int(4)|X|First hour of day to trig weather data upload|
|ForceUpdate|bit(1)|||
|UpdateType|nvarchar(128)|X|NewData or PreviousMonth|
|MaxHistoryDays|int(4)|X|Max number of days in history|
|FirstDayOfMonthTrig|int(4)|X|If monthly updates, which day in month to trig|
|MaxDaysInRequest|int(4)|X|Max number of days in history request|


## DimFacility

Schema name: dbo

Description: Dimension table having main setup for facility/plant


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)||Primary key column|
|FacilityName|nvarchar(510)||Name of facility|
|FacilityDescription|nvarchar(510)||Description of facility|
|FacilityLocation|nvarchar(510)|X|Location of facility|
|Entity|nvarchar(510)||Entity of facility, e.g. asset owner company name|
|Continent|nvarchar(510)||Continent of facility location|
|Country|nvarchar(510)||Country of facility location|
|PowerNominal|float(8)|X|Nominal DC power of plant (WDCp)|
|GridName|nvarchar(510)|X|Name of grid connected|
|PowerNominalACGrid|float(8)|X|Nominal AC output power of plant (W)|
|IPP_Gen_ID|nvarchar(128)|X|Generator ID of plant as seen from utility |
|Unit_ID|nvarchar(128)|X|Unit ID of plant as seen from utility|
|IPPID|nvarchar(40)|X|IPP ID of plant as seen from utility|
|GridConnectionVoltage|float(8)|X|Voltage at point of connection (V)|
|RegionKey|int(4)|X|Forreign key to DimRegion table|
|RegionScreenNo|int(4)|||
|SiteOrder|int(4)|X||
|NumConnectionPoints|int(4)|X|Number of grid connetion points|
|BreakersPerConnectionPoint|int(4)|X|Number of breakers per grid connection point|
|ViewAreaKey|int(4)|X|Forreign key to DimViewArea table|
|ViewAreaOrder|int(4)|X|Order number in view area|
|CountryCode|nvarchar(20)|X|3 digit country code|
|UID|uniqueidentifier(16)|X|GUID of facility used for identification in reports|


## DimFeeder

Schema name: dbo

Description: Dimension table having definition for PV feeders for facility/plant. Link to facility.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FeederKey|int(4)||Primary key column|
|FeederName|nvarchar(128)||Name of feeder|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|ZoneName|nvarchar(128)|X|Name of zone linked to feeder|
|SubFacilityKey|int(4)|X|Forreign key to DimSubfacility table|


## DimForecast

Schema name: dbo

Description: Dimension table having definition for different forecast/budgets per facility. Link to facility and forecasttype


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ForecastKey|int(4)||Primary key column|
|FacilityKey|int(4)|X|Forreign key to DimFacility table|
|ForecastPeriod_Minutes|int(4)|X|Interval in minutes for budget/forecast|
|LastExtract_UTC|datetime(8)|X||
|NextUpdateForecastStartTime|datetime(8)|X||
|ForecastTypeKey|int(4)||Forreign key to DimForecastType table|
|SubFacilityKey|int(4)|X|Forreign key to DimSubfacility table|


## DimForecastType

Schema name: dbo

Description: Dimension table having definition for different forecast/budget types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ForecastTypeKey|int(4)||Primary key column|
|ForecastTypeName|nvarchar(510)|X|Name of forecast/budget type|
|Description|nvarchar(510)|X|Description of forecast/budget type|
|IsEditable|bit(1)|X|If it is editable or not. 0 if not to be changed by user.|


## DimGridConnectionPoint

Schema name: dbo

Description: Dimension table having defintion for grid connection points for a facility. Link to facility.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|GridConnectionPointKey|int(4)||Primary key column|
|FacilityKey|int(4)|X|Forreign key to DimFacility table|
|GridConnectionPointName|nvarchar(128)|X|Name of grid connection point|
|Description|nvarchar(510)|X|Description of grid connection point|
|GridName|nvarchar(128)|X|Name of grid connected|
|GridOwner|nvarchar(128)|X|Owner of grid connected|
|SubFacilityKey|int(4)|X|Forreign key to DimSubfacility table|
|PPCKey|int(4)|X|Forreign key to DimPPC table. PPC controlling the grid connection point|


## DimInverter

Schema name: dbo

Description: Dimension table having defintion for inverters for a facility. Link to facility and invertertype. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|InverterKey|int(4)||Primary key column|
|InverterTypeKey|int(4)|X|Forreign key to DimInverterType table|
|InverterName|nvarchar(510)||Full name of inverter, e.g EG-AS-TS01-I01|
|InverterShortName|nvarchar(128)|X|Short name of inverter, e.g. I01|
|InverterNo|nvarchar(64)|X|Number of inverter, e.g. 01|
|TrafoNo|nvarchar(64)|X|Number of transforemer station connection to inverter, e.g. 01|
|InverterDescription|nvarchar(510)||Description of inverter|
|Supplier|nvarchar(510)||Supplier of inverter|
|Model|nvarchar(510)||Model of inverter|
|PowerNominal|float(8)|X|Nominal max AC output power of inverter from specification sheet (W)|
|PowerNominalDC|float(8)|X|Nominal DC power connected to inverter, som of PV panels (WDCp)|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|Inverter_SerialNo|nvarchar(128)||Serial number of inverter|
|SMC_SerialNo|nvarchar(128)|X||
|SM1_SerialNo|nvarchar(128)|X||
|SM2_SerialNo|nvarchar(128)|X||
|SM3_SerialNo|nvarchar(128)|X||
|SM4_SerialNo|nvarchar(128)|X||
|SM5_SerialNo|nvarchar(128)|X||
|SM6_SerialNo|nvarchar(128)|X||
|SM7_SerialNo|nvarchar(128)|X||
|SM8_SerialNo|nvarchar(128)|X||
|SM9_SerialNo|nvarchar(128)|X||
|SM10_SerialNo|nvarchar(128)|X||
|Sensor_SerialNo|nvarchar(128)|X||
|HasOnlyDCPower|bit(1)|X|1 if inverter only has DC power and not AC power measurement|
|SM11_SerialNo|nvarchar(128)|X||
|SM12_SerialNo|nvarchar(128)|X||
|ZoneName|nvarchar(32)|X|Name of zone hosting inverter|
|ClosestWeatherKey|int(4)|X|Closest weather station, forreign key to DimWeater table|
|ValueScale|float(8)|X|Value to scale input power and energy values from source. Values are divided by this to get the value in k|
|SubFacilityKey|int(4)|X|If linked to SubFacility, forreign key to DimSubFacility table|
|GPSLatitude|float(8)|X|GPS location of inverter|
|GPSLongitude|float(8)|X|GPS location of inverter|
|RelativeXPosition|float(8)|X|Relative position to inverter in plant relative to 0 point (m)|
|RelativeYPosition|float(8)|X|Relative position to inverter in plant relative to 0 point (m)|
|IsEast|bit(1)|X|If inverter is east oriented|
|IsWest|bit(1)|X|If inverter is west oriented|
|ProcessUnitID|int(4)|X|Link to state database PDSdb|
|LastLoadEndTime|datetime(8)|X|Last time loaded data for inverter|
|InverterRow|int(4)|X|Row position of inverter in logical plant grid. For vizualization|
|InverterColumn|int(4)|X|Column position of inverter in logical plant grid. For vizualization|
|IsReference|bit(1)|X|If estimated production for curtailment is calculation from reference inverters. |


## DimInverterType

Schema name: dbo

Description: Dimension table having setup for inverter types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|InverterTypeKey|int(4)||Primary key column|
|InverterTypeName|nvarchar(128)|X|Name of inverter type|
|Description|nvarchar(510)|X|Description of inverter type|
|IsStringInverter|bit(1)||1 if string inverter, 0 if central inverter|
|NominalACPower|float(8)|X|Nominal max AC output power of inverter type from specification sheet (W)|
|MaxEfficiency|float(8)|X|Max efficiency of inverter type from specification sheet (%)|
|MaxDCPower|float(8)|X|Nominal max DC input power of inverter type from specification sheet (W)|


## DimKpiParameters

Schema name: dbo

Description: Dimension table having properties for a facility used for data extraction and KPI calculations.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|FirstInstallationDate|datetime(8)|X|First date of PV module installation. |
|LastInstallationDate|datetime(8)|X|Last date of PV module installation. |
|AvailabilityNominalBonus|float(8)|X|Nominal plant availability number, bonus version (%)|
|YearlyModuleDegradationBonus|float(8)|X|Yearly module degradation for PR calculation, bonus version (%)|
|InitialModuleDegradationBonus|float(8)|X|Initial module degradation for PR calculation, bonus version (%)|
|AvailabilityNominalLD|float(8)|X|Nominal plant availability number, LD version (%)|
|YearlyModuleDegradationLD|float(8)|X|Yearly module degradation for PR calculation, LD version (%)|
|InitialModuleDegradationLD|float(8)|X|Initial module degradation for PR calculation, LD version (%)|
|PerformanceRatioNominal|float(8)|X|Nominal PR (%) for reporting|
|PerformanceRatioEPC_Bonus|float(8)|X|Nominal PR (%) for reporting|
|PerformanceRatioOM_Bonus|float(8)|X|Nominal PR (%) for reporting|
|PerformanceRatioOM_LD|float(8)|X|Nominal PR (%) for reporting|
|PerformanceRatioOM_P50|float(8)|X|Nominal PR (%) for reporting|
|PerformanceRatioEstimated|float(8)|X|Nominal PR (%) for reporting|
|SoilingTarget|float(8)|X|Target for soiling (%) for reporting|
|IrradiationStandardTestCondition|float(8)|X|Irradiation and STC (W/m2), normally 1000|
|InverterType|nvarchar(510)|X|Name of main inverter type used on plant|
|ModuleType|nvarchar(510)|X|Name of main PV module type used on plant|
|ModuleTypeKey|int(4)|X|Forreign key to DimModuleType table|
|NominalCellTemperature|float(8)|X|Nominal cell temperature for PV modules used, from data sheet (°C)|
|ModulePowerTemperatureCoefficient|float(8)|X|Module power temperature coefficient for PV modules used, from data sheet (%/°C)|
|ModuleEfficiency|float(8)|X|Module efficiency for PV modules used, from data sheet (%)|
|ModuleTempAdjustmentLimit|float(8)|X|Adjustment limit for module efficiency temp degradation (°C)|
|InverterDCLosses|float(8)|X|Estimated DC losses (0-1)|
|InverterMiscLosses|float(8)|X|Estimated misc. losses inverter (0-1)|
|PlantMiscLosses|float(8)|X|Estimated misc. Plant losses (0-1)|
|FlashTestPeakPower|float(8)|X|Flash test peak power of inverter (W)|
|UseTrackers|bit(1)|X|1 if plant has trackers|
|TrackerType|nvarchar(510)|X|Tracker type if in use|
|StartProductionDate|datetime(8)|X|Start date of production|
|FinancialCloseDate|date(3)|X|Date of financial close of project|
|ConstructionStartDate|date(3)|X|Date of construction start|
|ConstructionFinishDate|date(3)|X|Date of construction finish|
|CommercialOperationDate|date(3)|X|Date of start commercial production|
|NumberOfInstalledModules|int(4)|X|Number of installed PV modules in plant|
|PlaneOfArrayModuleArea|float(8)|X|Total panel area (m2)|
|NumberOfInverters|int(4)|X|Number of inverters in plant|
|NumberOfMVBreakers|int(4)|X|Number of MV breakers in plant|
|NumberOfHVBreakers|int(4)|X|Number of HV breakers in plant|
|Location|nvarchar(510)|X|Textual description of location|
|DrivingInstructions|nvarchar(max)|X|Driving instructions to plant|
|Coordinates|nvarchar(510)|X||
|CoordinateLongitude|float(8)|X|GPS location of plant|
|CoordinateLatitude|float(8)|X|GPS location of plant|
|Altitude|float(8)|X|Altitude of plant location (m)|
|ContactPerson|nvarchar(510)|X|Name of plant main contact person|
|EmailAddress|nvarchar(510)|X|Email of plant contact|
|PhoneNumber|nvarchar(510)|X|Phone number of plant contact|
|AreaUnderPanels|float(8)|X|Area under PV panels (ha)|
|LocalCurrency|nvarchar(128)|X|Local currency used |
|NominalHouseholdCapacity|float(8)|X|Number of househoulds|
|AnnualYieldEstimate|float(8)|X|Annual yield estimate for plant production (MWh)|
|GlobalEmmisionFactor|float(8)|X|Global emmision factor for plant (tons/MWh)|
|WarrantyStartDate_EPC|date(3)|X|Start date of warranty period|
|WarrantyEndDate_EPC|date(3)|X|End date of warranty period|
|FirstLD_Bonus_StartDate_OM|date(3)|X|First date of bonus|
|WarrantyIntervalMonths_OM|int(4)|X|Waranty interval (months)|
|PlantManagerEmail|nvarchar(510)|X|Mail to plant manager|
|DaylightInclineIrradiationLevel|float(8)||Irradiation level to trigger day (W/m2)|
|SitePortalURL|nvarchar(510)|X|Link to site SCADA portal|
|NumZones|int(4)|X|Number of zones in plant|
|ProjectTakeOverDate|datetime(8)|X|Date of take over from EPC|
|UseSoilingStation|bit(1)|X|If soiling stations is used in plant|
|UseSoilingRefCell|bit(1)|X|If soiling reference cells is used in plant|
|ModuleWidth|float(8)|X|Width of modules|
|ModuleRowDistance|float(8)|X|Row distance of modules|
|Slope|float(8)|X|Slope of modules|
|ClippingDetectingFactor|float(8)|X|Detection fafctor for clipping in percentage. Default 98,5 %|
|SoilingRateEstimate|float(8)|X|Fixed soiling rate estimate|
|ModuleCategory|nvarchar(40)|X|Category of PV modules|
|AutoGenerateDimStringMonitor|bit(1)|X||
|IsEastWest|bit(1)|X|If plant is east/west oriented|
|PowerNominalDC_East|float(8)|X|Nominal DC power for east oriented modules|
|PowerNominalDC_West|float(8)|X|Nominal DC power for west oriented modules|
|ShadingFactor|float(8)|X|Shading factor, fixed estimated value for the whole plant|
|ReportStringLosses|bit(1)|X|1 if string losses to be calculated |
|DefaultExportExtForecastKey|int(4)|X|Forreign key to DimExternalForecast, used as the default forecast to export in API|
|OnlyExtWeatherSource|bit(1)|X|If plant has now weather sensors, but only use external data|
|TrackerAvailabilityNominal|float(8)|X|Nominal tracker availability value, for reporting|
|UseSnowLosses|bit(1)|X|If plant should have snow losses calculated|
|ContractDuration|int(4)|X|Duration of PPA contract, for reporting|
|CalculateStringLossesPerChannel|bit(1)|X|1 if string losses to be calculated per channel|
|CalculateTrackerLossesPerTracker|bit(1)|X|1 if tracker losses to be calculated per tracker|
|IncludeCurtailmentLossesInPR|bit(1)|X|1 if curtailment losses should be included in energy based PR formula|
|TrackerLossesUseOutOfPos|bit(1)|X|1 if "out of pos" algorithm should result in losses|
|TrackerLossesUseOutOfPosStateSubClass|nvarchar(128)|X|Sub class to use as out of pos|
|StringSet_UnderPerformanceWarningLevel|float(8)|X|Level for detection string underperformance warning. 0-1, where 1 means no detection and 0 means always detected. Default value means 4 %|
|StringSet_UnderPerformanceErrorLevel|float(8)|X|Level for detection string underperformance error. 0-1, where 1 means no detection and 0 means always detected. Default value means 8 %|
|StringSet_DisconnectedLevel|float(8)|X|Level for detection string disconneted. 0-1, where 1 means no detection and 0 means always detected. Default value means 40 %|
|StringSet_IrradiationCheckLevel|float(8)|X|Irradiation level to detect underpeformance on strings.|
|Tracker_OutOfPosLimit|float(8)|X|Degrees deviation in tracker angles to detect out of pos alarm|
|Tracker_OutOfPosAlarmTime|float(8)|X|Number of seconds to set tracker out of pos alarm|
|Inverter_UnderPerformanceWarningLevel|float(8)|X|Under performance alarm level on inverter. 90 means alarm when relative performance below 90 %|
|StringCombiner_TemperatureAlarmLimit|float(8)|X|Limit to generate temperature alarm|
|Inverter_StartupLevelIrradiation|float(8)|X|Startup level for irradiation on the inverters|
|StringCombiner_TemperatureOffsetLimit|float(8)|X|Limit when checking temperature alarm on string combiner. Check applies to offset for transformer station median check|
|SubstationTransformer_TemperatureHighAlarmLimit|float(8)|X|Temperature alarm limit on transformer temperature alarm|
|DayIrradiationLevelDeadBand|float(8)|X|Deadband factor when going from day to night. E.g. Deault means night when irr<5-2=3|
|Weather_LowPassFilterSeconds|float(8)|X|Low pass filter time constant for weather data like irradiation in low pass filtered value use for is day etc.|
|StringSet_LowPassFilterSeconds|float(8)|X|Low pass filter time constant for filtering string data for performance functions|
|StringSet_PerformanceAlarms_StartHour|float(8)|X|Start hour of day for calculating string set performance alarms|
|StringSet_PerformanceAlarms_EndHour|float(8)|X|End hour of day for calculating string set performance alarms|
|StringSet_PerformanceAlarms_DeadbandFactor|float(8)|X|Deadband factor for turning off string performance state again|
|Inverter_PerformanceAlarms_StartHour|float(8)|X|Start hour of day for calculating inverter performance alarms|
|Inverter_PerformanceAlarms_EndHour|float(8)|X|End hour of day for calculating inverter performance alarms|
|Inverter_PerformanceAlarms_DeadbandFactor|float(8)|X|Deadband factor for turning off inverter performance alarm again|
|Inverter_LowPassFilterSeconds|float(8)|X|Low pass filter time constant for filtering inverter data for performance functions|


## DimMeter

Schema name: dbo

Description: Dimension table having defintion for power and energy meters for a facility. Link to facility and invertertype. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|MeterKey|int(4)||Primary key column|
|MeterName|nvarchar(510)||Meter name|
|MeterDescription|nvarchar(510)||Meter description|
|MeterType|nvarchar(510)||Meter type, e.g. "Energy meter"|
|SerialNumber|nvarchar(128)|X|Serial number of meter|
|DeliveryPointKey|int(4)||Forreign key to DimDeliveryPoint table|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|IsBackupMeter|nvarchar(20)||1 if this meter is a backup meter for plant. MeterType "Energy meter" and IsbackupMeter=0 is summarized as plant production|
|ValueScale|float(8)|X|Value to scale input power and energy values from source. Values are divided by this to get the value in k|
|Max_FeedInEnergy_Acc_kWh|float(8)|X|Max energy counter for meter, for calculating reset value|
|Active|bit(1)|X|1 if meter is active|
|Model|nvarchar(510)|X|Model of meter|
|Supplier|nvarchar(510)|X|Supplier of meter|
|GridConnectionPointKey|int(4)|X|Foreign key to DimGridConnectionPoint table|
|FeederKey|int(4)|X|Foreign key to DimFeeder table|
|SubFacilityKey|int(4)|X|Foreign key to DimSubfacility table|
|MeterGroup|nvarchar(128)|X|Meter group, used for data quality calculations |
|IsSubFacilityBackupMeter|nvarchar(20)|X|1 if this meter is a backup meter for sub facility. MeterType "Energy meter" and IsbackupMeter=0 is summarized as sub plant production|


## DimMinute

Schema name: dbo

Description: Dimension table having time dimension on minute resolution. Used by fact tables together with dateandhour.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|MinuteKey|int(4)||Primary key column|
|Minute|smallint(2)||Minute in hour|


## DimModuleType

Schema name: dbo

Description: Dimension table having setup for module types. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ModuleTypeKey|int(4)||Primary key column|
|ModuleTypeName|nvarchar(128)|X|Name of module type|
|Description|nvarchar(510)|X|Description of module type|
|MaximumPower|float(8)|X|Maximum DC power of PV panel|
|ModuleEfficiencySTC|float(8)|X|Module efficiency at STC (%) from data sheet|
|TemperatureCoefficients|float(8)|X|Module temperature coefficient, from data sheet  (%/°C)|


## DimPPC

Schema name: dbo

Description: Dimension table having defintion for power plant controllers for a facility. Link to facility. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|PPCKey|int(4)||Primary key column|
|FacilityKey|int(4)|X|Forreign key to DimFacility table|
|PPCName|nvarchar(128)||Name of PPC|
|Description|nvarchar(510)||Description of PPC|
|GridConnectionPointKey|int(4)|X|Forreign key to DimGridConnectionPoint table|
|Supplier|nvarchar(510)|X|Supplier of PPC|
|Model|nvarchar(510)|X|Model of PPC|
|SerialNo|nvarchar(510)|X|Serial number of PPC|
|CurtailmentFactorLimit|float(8)|X|Factor to detect power curtailment (measured vs setpoint), defult 0,95 (95%).|
|SubFacilityKey|int(4)|X|Forreign key to DimSubfacility table|
|UseForCurtailmentDetection|bit(1)|X|If PPC only is to be used to detect plant curtailment|


## DimRegion

Schema name: dbo

Description: Dimension table having setup for regions


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|RegionKey|int(4)||Primary key column|
|RegionName|nvarchar(510)||Region name|
|Description|nvarchar(510)||Region description|
|RegionTitle|nvarchar(510)||Region title (used in user interface)|
|CoordinateLongitude|float(8)||GPS coordinate of visualization|
|CoordinateLatitude|float(8)||GPS coordinate of visualization|


## DimSection

Schema name: dbo

Description: Dimension table having defintion for sections for a facility. Link to facility. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|SectionKey|int(4)||Primary key column|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|SectionName|nvarchar(510)||Section name|
|SectionDescription|nvarchar(510)||Section description|
|PowerNominal|float(8)||Nominal DC power for section (sum of PV modules) in (W)|
|UseTrackers|nvarchar(40)||If section is using trackers|
|SubFacilityKey|int(4)|X|Forreign key to DimSubfacility table|


## DimStateCodes

Schema name: dbo

Description: Dimension table having state code definitions for equipment


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|StateType|nvarchar(128)||State type (Tracker, Inverter, Grid)|
|StateCode|int(4)||Numeric state code if used|
|StateName|nvarchar(128)||State name|
|StateClass|nvarchar(128)||State class defining if downtime or not|
|StateSubClass|nvarchar(128)|X|State sub class|


## DimString

Schema name: dbo

Description: Dimension table having defintion for strings for a facility. Link to string monitor. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|StringKey|int(4)||Primary key column|
|StringMonitorKey|int(4)||Forreign key to DimStringMonitor|
|TrackerKey|int(4)|X|Forreign key to DimTracker. What tracker is moving string|
|StringName|nvarchar(128)|X|Name of string, unique|
|StringID|nvarchar(128)|X|ID of string (e.g. from plant design)|
|NumberOfModules|int(4)|X|Number of modules on string|
|NominalPower|float(8)|X|Nominal DC power on string (W)|
|GPSLatitude|float(8)|X|GPS coordinate|
|GPSLongitude|float(8)|X|GPS coordinate|


## DimStringMonitor

Schema name: dbo

Description: Dimension table having defintion for string channels for a facility. Link to inverter. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|StringMonitorKey|int(4)||Primary key column|
|InverterKey|int(4)||Forreign key to DimInverter table. Connected inverter|
|TrackerKey|int(4)|X|Forreign key to DimTracker table. What tracker is moving string|
|StringMonitorName|nvarchar(128)||Name of string monitor channel|
|StringMonitorGroupName|nvarchar(128)|X|Name of string monitor group / string combiner. Can also be string inverter name|
|StringMonitorNo|nvarchar(20)|X|String monitor number|
|ChannelNo|nvarchar(20)|X|String monitor channel number|
|NominalPower|float(8)||Nominal DC power of string channel (sum of connected PV modules)|
|NumStrings|int(4)||Number of strings on channel|
|Active|bit(1)||If string channel is active and used|
|StringColumn|int(4)|X|Logical string column position, for visualization|
|StringRow|int(4)|X|Logical string row position, for visualization|
|RelXPos|float(8)|X|Relative string position, for visualization (m)|
|RelYPos|float(8)|X|Relative string position, for visualization (m)|
|GPSLatitude|float(8)|X|GPS coordinates|
|GPSLongitude|float(8)|X|GPS coordinates|
|NumModules|int(4)|X|Number of PV modules on string channel|
|IsEast|bit(1)|X|If channel is east oriented|
|IsWest|bit(1)|X|If channel is west oriented|
|RowDistance|float(8)|X|Distance between string rows|
|TiltAngle|float(8)|X|Tilt angle if fixed tilt|
|AzimuthAngle|float(8)|X|Azimuth angle of panels|


## DimSubFacility

Schema name: dbo

Description: Dimension table having main setup for sub facility. Link to facility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|SubFacilityKey|int(4)||Primary key column|
|SubFacilityName|nvarchar(510)||Name of sub facility|
|SubFacilityDescription|nvarchar(510)||Description of sub facility|
|FacilityKey|int(4)|X|Forreign key to DimFacility table|
|PowerNominalDC|float(8)|X|Nominal DC power on sub facility (W). Sum of PV panels|
|IPP_Gen_ID|nvarchar(128)|X|Generator ID of sub plant as seen from utility |
|PowerNominalAC|float(8)|X|Nominal AC output power on sub facility (W). |
|EnableSubFacilityReporting|bit(1)|X|If reporting on sub facility is enable for this|
|CoordinateLongitude|float(8)|X|GPS coordinates|
|CoordinateLatitude|float(8)|X|GPS coordinates|


## DimTracker

Schema name: dbo

Description: Dimension table having defintion for trackers for a facility. Link to facility and trackertype. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|TrackerKey|int(4)||Primary key column|
|TrackerTypeKey|int(4)|X|Forreign key to DimTrackerType table|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|TrackerName|nvarchar(510)||Name of tracker|
|TrackerDescription|nvarchar(510)||Description of tracker|
|Supplier|nvarchar(510)|X|Supplier of tracker|
|Model|nvarchar(510)|X|Model of tracker|
|ConnectedInverterKey|int(4)|X|Forreign key to DimInverter table. Inverter supplying power to tracker |
|AngleOffset|float(8)|X|Offset of angle measurements|
|Active|bit(1)|X|If tracker is active or not |
|IsReferenceTracker|bit(1)|X|If this is a reference tracker, used for reporting|
|SubFacilityKey|int(4)|X|Forreign key to DimSubfacility table|
|GPSLatitude|float(8)|X|GPS coordinate|
|GPSLongitude|float(8)|X|GPS coordinate|
|RelativeXPosition|float(8)|X|Relative tracker position, for visualization (m)|
|RelativeYPosition|float(8)|X|Relative tracker position, for visualization (m)|
|SerialNo|float(8)|X|Serial number of tracker|
|TrackerGroup|nvarchar(510)|X|Tracker group, for visualization. E.g. Common tracker control unit|
|TrackerRow|int(4)|X|Logical tracker position, for visualization|
|TrackerColumn|int(4)|X|Logical tracker position, for visualization|
|MinAngle|float(8)|X|Minimum angle of tracker|
|MaxAngle|float(8)|X|Maximum angle of tracker|
|TrackerShortName|nvarchar(128)|X|Short name of tracker, for visualization|
|StructureRow|int(4)|X|Logical position of tracker group, for visualization|
|StructureColumn|int(4)|X|Logical position of tracker group, for visualization |


## DimTrackerType

Schema name: dbo

Description: Dimension table having setup for tracker types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|TrackerTypeKey|int(4)||Primary key column|
|TrackerTypeName|nvarchar(128)||Name of tracker type|
|Description|nvarchar(510)||Description of tracker type|
|SupplierName|nvarchar(510)||Supplier of tracker type|
|Category|nvarchar(128)|X|Category of tracker type (Single Axis NS)|
|Model|nvarchar(128)|X|Model of tracker type|


## DimViewArea

Schema name: dbo

Description: Dimension table for view areas used in old CMC views


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ViewAreaKey|int(4)||Primary key column|
|ViewAreaName|nvarchar(128)||View area name|
|ViewAreaTitle|nvarchar(510)||View area description|


## DimWeather

Schema name: dbo

Description: Dimension table having defintion for weather stations for a facility. Link to facility. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|WeatherKey|int(4)||Primary key column|
|FacilityKey|int(4)||Forreign key to DimFacility table|
|WeatherStationName|nvarchar(510)|X|Name of weather station|
|WeatherStationDescription|nvarchar(510)|X|Description of weather station|
|TrackerName|nvarchar(510)|X|Forreign key to DimTracker table. What tracker is moving incline pyranometer|
|OverruleBadTracker|bit(1)|X|Overrule bad tracker signal for pyranometer valicdation|
|DefaultDataQuality|int(4)||Default data quality for weather station. Bit wise status word |
|UseRefCellsForSoiling|bit(1)||If station is used for reference cell soiling calculation|
|HasReversedRefCells|bit(1)||If reference cells are swapped|
|RefCellCalibrationDate|date(3)|X|Last calibration date for reference cells|
|RefCellDirtyCleanOffset|float(8)||Calibration offset for clean and dirty reference cells|
|RefCellDirtyCleanScale|float(8)||Calibration scale for clean and dirty reference cells|
|SubFacilityKey|int(4)|X|Forreign key to DimSubfacility table|
|GPSLatitude|float(8)|X|GPS coordinate|
|GPSLongitude|float(8)|X|GPS coordinate|
|RelativeXPosition|float(8)|X|Relative weather station position, for visualization (m)|
|RelativeYPosition|float(8)|X|Relative weather station position, for visualization (m)|
|Model|nvarchar(510)|X|Model name of weather station|
|SerialNo|nvarchar(510)|X|Serial number of weather station|
|Supplier|nvarchar(510)|X|Supplier of weather station|
|WeatherStationCategory|nvarchar(40)|X|Field or site station.|
|IsEast|bit(1)|X|If station is east oriented|
|IsWest|bit(1)|X|If station is west oriented|
|StationNo|int(4)|X|Weather station number|
|Active|bit(1)|X|If weather station is active and in use|
|SoilingIndexOffset|float(8)|X|Calibration offset for soiling station index value|
|SoilingIndexScale|float(8)|X|Calibration scale for soiling station index value|
|SoilingReversedPolarity|bit(1)|X|If soiling station has reversed values|
|LastSoilingCalibrationDate|datetime(8)|X|Last date of calibrating the soiling index sensor|


