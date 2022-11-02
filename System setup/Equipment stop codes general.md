# Equipment Stop Codes General

Available equipment stop codes, or equipment states, are configured in a user screen in the plant portals.

The following parameters are set for each code:

* Code: numeric state code
* Name: name of state showing in reports
* Class: class of state, used in availability and failure calculations
    * Production time
    * Failure time (causes downtime in availability calculation)
    * Idle time (causes downtime in availability calculation)
    * Line restraint time
    * Unscheduled
    * Not scheduled
* Description: textual description of code
* Label: text label
* Process unit class: which group of equipment using this code
    * Grid or Inverter to be normally used

Existing codes can be edited from the list. Press "Add new" button to add new code.

In general, code editing should be handled with care, and seen in relation to calculations and formulas.