# Urban Heat Berlin — Air temperature + green space + population density

## Period
2024-06-01 to 2024-08-31

## Goal
Analyze the spatial distribution of an Urban Heat Island proxy in Berlin (Bezirk-level air-temperature indicators) and examine how green space and population density relate to local temperature patterns.

## Data sources
- Air temperature: DWD weather station observations (hourly), aggregated to Bezirk-level indicators.
- Administrative boundaries: Berlin Bezirke polygons.
- Green space: Berlin open geodata “Grünanlagen” (parks/green facilities layer; proxy for vegetation/greenspace).
- Population density: Berlin open geodata “Einwohnerdichte 2022”.

## Method (high level)
1) Compute Bezirk-level heat indicators from DWD station data (e.g., mean daily max temperature, hot days ≥ 30°C).
2) Assign station-derived temperature indicators to Bezirke (baseline: nearest-station assignment).
3) Compute green share per Bezirk as area(Grünanlagen ∩ Bezirk) / area(Bezirk).
4) Compute Bezirk-level population density (residents per km²) from the density layer.
5) Compare relationships descriptively (scatter plots + Pearson correlation).

## Outputs (files)
- Processed dataset: `data/processed/berlin_bezirke_uhi_features.csv`
- Processed geodata: `data/processed/berlin_bezirke_uhi_features.geojson`
- Maps:
  - `maps/berlin_airtemp_mean_daily_max.png`
  - `maps/berlin_airtemp_hot_days_30.png`
  - `maps/berlin_green_share_pct.png`
  - `maps/berlin_pop_density_ew_km2.png`
  - `maps/scatter_tmax_vs_green.png`
  - `maps/scatter_tmax_vs_density.png`

## Key results (Bezirk-level; UHI proxy)
- Pearson corr(mean_daily_max, green_share_pct) = 0.597
- Pearson corr(mean_daily_max, pop_density_ew_km2) = 0.598

## Interpretation note (important for presentation)
The positive correlation with green_share_pct is counterintuitive if “greener → cooler”.
In this project, green_share_pct is a *proxy* derived from the “Grünanlagen” layer (parks/green facilities) and may not represent total vegetation cover (e.g., forests, tree canopy, water-adjacent cooling, private greenery). Additionally, the air-temperature indicator is assigned using a nearest-station baseline, which can blur microclimate differences at Bezirk scale. With only 12 Bezirke, a few districts can strongly influence correlations.
Therefore, interpret the green-space relationship cautiously as “association under this proxy + baseline method,” not as a causal statement.

## Limitations
- Nearest-station assignment is a conservative baseline; it can miss microclimate variation within Bezirke.
- Grünanlagen layer represents a specific subset of green space (not NDVI/canopy/total vegetation).
- Aggregation to 12 Bezirke limits statistical power.

## Suggested upgrade (optional, strong for portfolio)
- Add satellite-derived vegetation (NDVI from Sentinel-2) and/or Land Surface Temperature (Landsat/Sentinel-3) to better represent surface UHI patterns.
- Replace nearest-station assignment with multi-station interpolation (e.g., inverse-distance weighting).
