# Urban Heat Berlin — Air temperature + green space + density
Period: 2024-06-01 to 2024-08-31

## Outputs
- data/processed/berlin_bezirke_uhi_features.geojson
- data/processed/berlin_bezirke_uhi_features.csv
- maps/berlin_airtemp_mean_daily_max.png
- maps/berlin_airtemp_hot_days_30.png
- maps/berlin_green_share_pct.png
- maps/berlin_pop_density_ew_km2.png

## Key results (Bezirk-level; nearest-station baseline for air temperature)
- Mean daily max (°C) range: 24.74 to 25.18
- Hot days (Tmax ≥ 30°C) range: 9 to 12
- Warmest Bezirke by mean daily max: Friedrichshain-Kreuzberg, Lichtenberg, Mitte
- Coolest Bezirke by mean daily max: Charlottenburg-Wilmersdorf, Spandau, Steglitz-Zehlendorf
- Most hot days (Tmax ≥ 30°C): Treptow-Köpenick, Friedrichshain-Kreuzberg, Lichtenberg

## Relationship to green space & density (descriptive)
- Corr(mean_daily_max, green_share_pct): 0.60 (expected negative if greener → cooler)
- Corr(mean_daily_max, pop_density_ew_km2): 0.60 (expected positive if denser → hotter)

## Notes / limitations
- Air temperature is derived from DWD stations and assigned to Bezirke using a nearest-station baseline (conservative; may miss microclimate differences).
- Green space and density are aggregated from Berlin open geodata layers; results depend on layer definitions and spatial resolution.
- With 12 Bezirke, predictive ML is mainly illustrative; interpretation should focus on descriptive patterns + uncertainty.

## Suggested next upgrade (optional)
- Add satellite-derived NDVI (Sentinel-2) and/or Land Surface Temperature (Sentinel-3 / Landsat) to better represent surface UHI.