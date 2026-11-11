# MEMO

**To:** Mr. Habimana, Head of Planning and Data, MCSU
**From:** Student 1 name and Student 2 name, Junior Data Analysts (Group XX)
**Date:** 11 November 2026
**Subject:** Maize yield data: ready for modelling?

**1. What we received.** The file had 1,426 farm records and 20 columns, covering 2015 to 2024, 5 provinces, 30 districts and the three seasons. After cleaning, all 1,426 records can be used.

**2. Main problems found.**
- *The file is not the one that was described to us.* It has no cooperative code, no planting date and no harvest weight. This matters because we cannot report results for each cooperative. We worked with the file as it is and did not invent the missing columns.
- *Some forms were incomplete.* 14 records had no rainfall, soil acidity or pest value. Leaving them empty would stop the forecast for those farms. We filled them with the middle value of similar records (for rainfall, records of the same season).
- *Season C and irrigated plots have few records* (226 Season C records, 128 irrigated plots). Forecasts for them will be less reliable. We made sure they are present in the same share in every part of the data.

**3. Data removed or changed.** No record was removed. No duplicate, impossible value or mixed spelling was found. Unusual values (large farms, cool highland farms, yields above 4 t/ha) were checked and kept because they are realistic. The record code and the district name are not given to the model. We found no column that is known only after harvest, so nothing had to be removed to avoid leakage; the yield itself is kept only as the value to predict.

**4. New features.** We created 10 new pieces of information, for example total fertiliser per hectare, an improved-seed marker, altitude zone, a marker for good soil acidity and temperature, pest level, and rainfall on irrigated plots. After checking which ones add information, 5 are kept in the final data (total_fert_kg_ha, improved_seed, manure_and_fert, altitude_zone, ph_optimal); the others repeated information already present or showed a weak link with yield. They help with Questions B (inputs), C (weather and location) and E (risk). In the raw data, improved varieties average 2.77 t/ha against 1.80 t/ha for local seed, and Season A averages 2.86 t/ha against 1.99 t/ha in Season C. These are simple averages, not yet proof of cause.

**5. Limits and risks.** The data cannot tell us anything about individual cooperatives, planting dates or farmers. 21 rainfall values sit exactly at 150 mm, which suggests the weather data has a lower limit. The task sheet states that the data is synthetic, so conclusions must be confirmed with real field data.

**6. Recommendation.** The data is ready for the modelling team: 998 records for training, 214 for validation and 214 for the final test, with 32 features. It can support Questions A, B, C and E now, and Question D for provinces and seasons. Next season, please ask field officers to record the cooperative code, the planting date and the actual rainfall for every farm, and to visit more Season C and irrigated plots.
