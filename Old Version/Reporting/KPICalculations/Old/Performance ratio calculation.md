# Performance Ratio Calculation

Perfrormance ratio us in general ratio between incomming solar energy and energy delivered to grid. Some different variation applies in system:

* PR Contractual LD:  PR from contract for a given plant.
* PR Net:  PR basic calculation. Only looking at irradiance and production. Does not adjust for the module degradation in the nominal power.
* PR Gross:  Uses PR net as basis. Divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced.
* PR Gross Production Loss: Uses PR net as basis, but production is using measured production + estimated production losses due to Plant and Grid downtime.

__1. Performance ratio contractual LD:__

Basic formula as below, but might be overridden by plant specific formulas.

Parameters vary from plant to plant.

* PR Contractual = MCF * ( EAdj * Is ) / ( Pnom * Iacc )
    * EAdj: Measured energy production, manually adjusted if necessary
    * Is: Irradiance at standard test conditions, 1000 W/m2
    * Pnom: nominal DC power of plant
    * IAcc: accumulated irradiation
    * MCF: monthly correction factor

__2. Performance ratio net__

This formula only looks on energy produced in relation to the measured accumulated irradiation.

* PR net = EAdj * Is / Pnom / Iacc
    * EAdj: Measured energy production, manually adjusted if necessary
    * Is: Irradiation at standard test conditions, 1000 W/m2
    * Pnom: nominal DC power of plant
    * Iacc: accumulated irradiation

__3. Performance ratio gross__

This formula adjust the Performance ratio net by plant and grid availability

* PR Gross = PR Net / PAd / GAdg
    * PR Net: performance ratio net
    * PAd: Plant availability daylight.
    * GAdg: Grid availability daylight gross.

__4. Performance ratio gross production loss__

Uses PR net as basis, but production is using measured production + production losses due to downtime.

* PR Gross Prod Lost = EAdjGross * Is / Pnom / Iacc
    * EAdjGross: Measured energy production, manually adjusted if necessary + production lost due to inverters and grid downtime
    * EAdjGross = EAdj + Production Lost Inverters + Production Lost Grid
    * Is: Irradiance at standard test conditions, 1000 W/m2
    * Pnom: nominal DC power of plant
    * Iacc: accumulated irradiation in the module plane.
        * If no irradiation exists for period, use following algorithm:
            * Try to use horizontal irradiation measurement with Transposition Factor (TF) from external weather source (SolarGIS)
            * Try to use incline irradiation data from external weather source (SolarGIS)
            * Use irradiation for same time previous days. 30 days back is checked. Average for first 5 days with measurments is used.
            