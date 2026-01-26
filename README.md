# Urban Heat Berlin
This project analyses the Urban Heat Island (UHI) effect across Berlin’s 12 Bezirke using Python and GIS tools.

Completed so far:
- Created a Berlin Bezirke base map from OpenStreetMap using OSMnx and GeoPandas
- Cleaned geometries and dissolved them into 12 districts
- Exported the final district boundaries as GeoJSON and pushed to GitHub

## Air temperature (DWD) pipeline (reproducible)

### Data source
Hourly air temperature observations (2m) from Deutscher Wetterdienst (DWD) Climate Data Center (CDC), dataset “hourly air temperature (TT_TU)”. Raw downloads are cached locally in `data/raw/` and are not committed.

### What the notebook does
Notebook: `code/urban_heat_berlin.ipynb`

1. Loads Berlin Bezirke boundaries from `data/processed/berlin_bezirke.geojson`.
2. Downloads DWD station metadata and selects stations within a buffer around Berlin.
3. Downloads hourly station temperature archives (TT_TU) and filters to the analysis period.
4. Computes station-level heat indicators:
   - `mean_tt` (mean hourly temperature)
   - `mean_daily_max` (mean of daily maxima)
   - `hot_hours_30` (count of hours ≥ 30°C)
   - `hot_days_30` (count of days with Tmax ≥ 30°C)
5. Aggregates indicators to Bezirke using a nearest-station baseline (v1).
6. Exports processed datasets, maps, and a short written summary.

### Outputs
- `data/processed/berlin_bezirke_airtemp_indicators.geojson`
- `data/processed/berlin_bezirke_airtemp_indicators.csv`
- `maps/berlin_airtemp_mean_daily_max.png`
- `maps/berlin_airtemp_hot_days_30.png`
- `report/air_temperature_summary.md`

### How to reproduce
1. Open `code/urban_heat_berlin.ipynb`.
2. Restart the kernel.
3. Run all cells.