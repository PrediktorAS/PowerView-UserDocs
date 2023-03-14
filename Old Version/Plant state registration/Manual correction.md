# Manual Correction

The equipment/plant state can be corrected in a user screen in the plant portal. See Equipment downtime general .

Look for state descriptions for each equipment group before changing. In general, state class "Failure time" and "Idle time" is considered down time and will result in reduced availability.

Down time states should in general not be registered during night. Then codes like "Error, no power production" for inverter should be used.

For grid down time, the states "Downtime due to Utility" and "Downtime due to Force Majeure" is treated special. These codes will result in calculated deemed energy in the deemed energy reports in central portal.