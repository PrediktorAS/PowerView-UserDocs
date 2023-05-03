# Soiling Index

Soiling index for a plant is calculated as average soiling index calculated from soiling stations or reference cells.
If plant is configured to use soiling stations, these measurements are used and reference cells are ignored. (configured in plant parameters)

## Reference cell calculations
All working reference cells are used to calculate the plant average value. °
Soiling index for a 10 minute period is calculated as relation between clean and dirty reference cells.
Reference cells are calibrated/normalized with the “cleaning date” as configured in the “Setup weather station” page (Last ref. cell cleaning date (dd.mm.yyyy). 

Normalization factor is calculated for that day, assuming both reference cells should be equal day after cleaning.
- Soiling Index = 100 * (RefCellIrradiation_Cleaned - RefCellIrradiation_Dirty / RefCellDirtyCleanScale) / RefCellIrradiation_Cleaned
    - RefCellIrradiation_Cleaned: measured irradiation on clean reference cell
    - RefCellIrradiation_Dirty: measured irradiation on clean reference cell
    - RefCellDirtyCleanScale: normalization factor calculated based on cleaned date
    - Filter: calculated when RefCellIrradiation_Cleaned > 200 W/m2

##	Soiling Index calculations
Plant average soiling index is calculated from all working soiling index measurements. (no filtering on deviation from median etc.)
