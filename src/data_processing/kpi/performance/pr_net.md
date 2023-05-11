# Performance Ratio Net (PR Net)

The most basic PR calculation. It is only looking at irradiance and production and __*does not adjust*__ for the module degradation in the nominal power.

## Formula

> PR net = E_Meas * Is / Pnom / Incline Irradiation

### Variables
- `E_Meas`: [Actual Production](../yield_and_weather/actual_production.md)
- `Is`: Irradiation at standard test conditions, constant 1000 W/m2
- `Pnom`: Nominal DC power of the plant, as in the sum of all installed modules.
- `Incline Irradiation`: [`Incline Irradiation`](../yield_and_weather/incline_irradiation.md)
