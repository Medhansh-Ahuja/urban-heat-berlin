# Urban Heat Berlin — Air temperature + green space + density

## Step 6 FINAL outputs
- /Users/medhanshahuja/Projects/Urban Technology/Urban_Heat_Berlin_Project/maps/scatter_tmax_vs_green.png
- /Users/medhanshahuja/Projects/Urban Technology/Urban_Heat_Berlin_Project/maps/scatter_tmax_vs_density.png

## Relationships (descriptive)
- Corr(mean_daily_max, green_share_pct_fixed): 0.597
- Corr(mean_daily_max, pop_density_ew_km2): 0.598

## Interpretation note (important for presentation)
- If green correlation is counterintuitive, emphasize: (1) small sample (12 Bezirke),
  (2) air temperature is based on nearest-station assignment (can bias),
  (3) the 'Gruenanlage' layer is *not* full vegetation (it may exclude forests/water),
  so 'green_share' here is a proxy and should be interpreted cautiously.