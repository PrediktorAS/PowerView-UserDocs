# GAMESA Inverter v2

State logging is set up for all inverter. Each section within the inverter is considered a process unit. Naming is set to:

\<Country\>-\<Site\>-TSXX-IYY.Z:

* Country is two characters code.
* Site is two characters code.
* XX is TS number
* YY is inverter number
* Z is section number in inverter, 1 or 2

Example:

* NO-OS-TS01-I01.1
* NO-OS-TS01-I01.2

Section boolean states and some external states are used for determine process time allocation. The external states are

* GridDown
* NoIrradiation (default incline irradiation < 5)
* AboveInverterStartupLevel (default incline irradiation > 120)

Following codes are used:

|Code|Name|Class|
|---|---|---|
|309|Operation|Production time|
|310|Operation with warning|Production time|
|311|Operation with failure|Production time|
|401|Warning|Idle time|
|402|Stopped|Idle time|
|403|Not started|Idle time|
|404|Waiting for PV|Idle time|
|1500|No power production|Not scheduled|
|1501|Grid down|Line restraint time|
|1502|Grounded|Idle time|
|1800|Emergency|Failure time|
|10200|Night failure|Not scheduled|
|10201|Night warning|Not scheduled|
|10202|Night grounded|Not scheduled|
|2000|Preventive Maintenance|Unscheduled|
|2001|Corrective Maintenance|Failure time|
|2002|Downtime due to utility|Line restraint time|
|2003|Downtime due to Force Majeure|Line restraint time|

Algorithm:

```
If (GridCalc.GridDown)
{
    Code=1501 (Grid down – Line restraint time)
}

Else If (WeatherCalc.NoIrradiation)
{             
    // Night time mode

    If (IsGrounded)
        Code=10202 (night failure – Not Scheduled)
    Else If (HasFailure)
        Code=10201 (night warning – Not Scheduled)
    Else If (HasWarning)
        Code=10200(night grounded – Not Scheduled)
    Else
        Code=1500 (No power production - Not Scheduled)
}

Else If (IsProducing)
{
    If (HasFailure)
        Code=311 (Operation with failure – ProductionTime)
    else If (HasWarning)
        Code=310 (Operation with warning – ProductionTime)
    else
        Code=309 (Operation – Production time)                                           
}  

Else If (IsStatCom)

{             
    Code=1503 (statcom – line restraint time)
}             

Else If (IsGrounded)
{             
    Code=1502 (grounded – Idle time)
}             

Else If (HasFailure)
{             
    Code=2000 + FailureCode (Inverter specific codes – Failure time)
}             

Else if (HasWarning)
{             
    Code=401 ( warning – Idle time)
}             

Else if (IsStopped)
{             
    Code=402 ( stopped – Idle time)
}             

Else if (WeatherCalc.AboveInverterStartupLevel)
{            
    Code=403   ( NotStarted  – Idle time)
}             

Else
{             
    Code=404  ( WaitingForPV – Line restraint)             
}      
```