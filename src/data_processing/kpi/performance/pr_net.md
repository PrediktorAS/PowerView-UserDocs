# PR Net	

This is the PR basic calculation only considering production and irradiation. 

This formula is only taking into account irradiance and production measurements. It does not take into account the module degradation in the nominal power.

PR net = [Actual Production](../yield_and_weather/actual_production.md) * Is / Pnom / [Incline Irradiation](../yield_and_weather/incline_irradiation.md)
- Is: Irradiation at standard test conditions, constant 1000 W/m2
- Pnom: nominal DC power of plant. Sum of installed modules.


