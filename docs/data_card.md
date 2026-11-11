# Data Card - Maize Yield, Rwanda (Question 1)

**Purpose.** Model-ready data to predict maize yield per hectare before harvest for the Maize Cooperative Support Unit (MCSU).

**Source.** `maize_yield_rwanda_rw.csv`, supplied with the practical task. The task sheet states that the data is synthetic. For this course only.

**Size.** Raw file: 1426 records, 20 columns. Usable after cleaning: 1426 records.
Split (seed 42, stratified by season): train 998, validation 214, test 214.

**Targets.** `yield_t_ha` (tonnes per hectare, regression). `low_yield_risk` (1 if yield is at or below 1.94 t/ha, the 20th percentile of the training set) for Question E. `low_yield_risk` is a target, not a feature.

**Columns in the final files (32 features).** year, altitude_m, rainfall_mm, avg_temp_c, soil_ph, urea_kg_ha, manure_t_ha, plant_density_per_ha, pest_incidence_index, total_fert_kg_ha, irrigation, improved_seed, manure_and_fert, altitude_zone, ph_optimal, season_A, season_B, season_C, province_Eastern, province_Kigali, province_Northern, province_Southern, province_Western, soil_type_Clay, soil_type_Loam, soil_type_Sandy loam, soil_type_Volcanic, seed_variety_PAN691, seed_variety_RHM104, seed_variety_WH505, seed_variety_ZM621, farming_practice_Traditional.

**Cleaning steps.** Text labels tidied; duplicates checked (none); irrigation changed to 1/0; impossible values checked (none); outliers checked and kept with reasons; leakage check (no after-harvest column); missing values in rainfall, soil pH and pest index filled with training-set medians (rainfall by season).

**Feature steps.** 10 new features created (5 kept after selection); log transformation of farm area; one-hot encoding; standardisation; selection by constant/duplicate/high-correlation filters and SelectKBest (F-test), all learned on the training set; irrigation, altitude, temperature and province kept by a business rule for Questions C and D.

**Known limitations and bias risks.**
- The file does not match the description in the task sheet: no cooperative, planting date, farmer age or harvest weight.
- Season C (226 records) and irrigated plots (128 records) are few, so results for them are less certain.
- 21 rainfall values sit exactly at 150.0 mm, which suggests a lower limit in the weather data.
- Altitude and pest groups use limits chosen by the analysts.
- `district` is not a model feature; it stays in `data/interim/` for reporting.

**How to reproduce.** Create the environment from `environment.yml`, put the raw file next to the notebook (or in `data/raw/`), then use Kernel > Restart & Run All. The fingerprints printed in section 6.3 must be the same on every run.
