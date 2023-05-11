# Production Losses due to Tracker downtime

As explained in [Equipment States](../../../data_collection/equipment_states/) Tracker state is classified into the following classes, where only number two and three are considered as Tracker downtime and thus production loss:
- Production time
- __Failure time__
- __Idle time__
- Line restraint time
- Unscheduled

Tracker losses (*E_loss_tracker*) are calculated per tracker and summarized on plant. Losses are categorized into following sub categories in addition to total losses:
-	Failure
-	Manual parked
-	Wind Stow
-	Out of position

## Calculation
> E_loss_tracker  = E_ref  *  (1 – GII_tracker / GII_reference)

Negative tracker losses not allowed: when `E_loss_tracker < 0` then `E_loss_tracker = 0`

### Variables
- [`E_ref`](#e_ref-calculation): reference production for tracker
- [`GII_tracker`](#gii_tracker-calculation): incline irradiance for tracker calculated from GHI_measured and tracker angles
- [`GII_reference`](#e_ref-calculation): incline irradiance for reference trackers calculated from GHI_measured and tracker angles

#### E_ref calculation
> E_ref = E_plant * ( Pnom_tracker /  Pnom_plant )

- `E_plant`: plant production
    - [Actual Production](../yield_and_weather/actual_production.md) on plant
    - If E_measured_plant does not exist for 10 min period, use [Estimated Production](../yield_and_weather/estimated_production.md) 
- `Pnom_tracker`: nominal DC power connected to tracker
- `Pnom_plant`: nominial DC power for plant

#### GII_tracker calculation
Incline irradiance for tracker calculated from GHI_measured and tracker angles
> GII_tracker = diffuse_fraction * GHI_measured * 0.5 * (1 + cos(theta_tracker)) + (1 - diffuse_fraction) * DNI * cos(aoi_tracker)

#### GII_reference calculation
Incline irradiance for reference trackers calculated from GHI_measured and tracker angles
> GII_reference = diffuse_fraction * GHI_measured * 0.5 * (1 + cos(theta_reference)) + (1 - diffuse_fraction) * DNI * cos(aoi_reference)

#### GII Variables
- `GHI_measured` is measured [horizontal irradiation](../yield_and_weather/horizontal_irradiation.md)
- `GII_measured` is measured [incline irradiation](../yield_and_weather/incline_irradiation.md)
- `theta_tracker` and `theta_reference` are measured tracker angles for parked and working reference trackers respectively
    - Reference trackers: Using median angles for working trackers for plant
- `DNI`: DNI is direct normal irradiation
    - GHI * (1-diffuse_fraction) / cos(solar_zenith)
- `aoi_tracker` and `aoi_reference` are angle of incidence on parked and reference trackers and calculated as follows: 
    - `aoi` = arccos(projection)
        - Clip to {0,85}
    - `projection` =  (cos(surface_tilt) * cos(solar_zenith) +sin(surface_tilt) * sin(solar_zenith) *cos(solar_azimuth - surface_azimuth))
        - `surface_tilt` = abs(tracker_angle)
            - `tracker_angle`: theta_tracker for aoi_tracker and theta_reference for aoi_reference
        - `surface_azimuth` = 90 if tracker_angle < 0 else 270
        - `solar_zenith`: solar zenith angle clipped on 85 degrees
        - `solar_azimuth`: solar azimuth angle
        - Clip to {-1, 1}
- `diffuse_fraction`: Diffuse fraction is calculated as follows 
    - `diffuse_fraction` = ( TF_clearsky - TF_measured) / (TF_clearsky - TF_diffuse)
        - `TF_clearsky` = cos(aoi_reference) / cos(solar_zenith)
        - `TF_diffuse` = 0.5 * (1 + cos(theta_reference))
        - `TF_meas` = GII_measured / GHI_measured
        - Clip to {0.1, 1}
    - In center of day when tracker angles < 30 degrees
        - `diffuse_fraction` = mean(`diffuse_fraction`) where abs(`theta_reference`) > 30 degrees for that day
    - During backtracking, using `diffuse_fraction` as calculated, even when `theta` < 30 degrees