# PR Net	

This is the PR basic calculation only considering production and irradiation. 
This formula is only taking into account irradiance and production measurements. It does not take into account the module degradation in the nominal power.

PR net = E_Meas * Is / Pnom / Iacc
- E_Meas: Measured energy production, manually adjusted if necessary
- Is: Irradiation at standard test conditions, constant 1000 W/m2
- Pnom: nominal DC power of plant. Sum of installed modules.
- Iacc: accumulated incline irradiation in kWh/m2.

