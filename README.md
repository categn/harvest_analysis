# harvest_analysis
This analysis examines agricultural yield data collected from a harvesting machine in Jolanda di Savoia. The goal is to clean, process, and analyze the yield distribution while correlating it with a vegetation vigor index. The key steps are:

- Data Cleaning

I used geopandas to handle geospatial data, then converted timestamps into a proper datetime format and checked for missing values and duplicates.
- Exploratory Data Analysis

I examined the distribution of key variables using histograms and checked for outliers using boxplots.
- Spatial Interpolation 

Since the dataset contained latitude and longitude coordinates in EPSG:4326, I reprojected them to UTM Zone 32N (EPSG:32632) to allow for spatial interpolation. Then I generated a spatial yield distribution map using Inverse Distance Weighting (IDW) interpolation. Since the harvester collects yield data only at specific locations, interpolation was necessary to estimate values in unobserved areas and create a continuous yield map. To do it, I created a 100×100 grid covering the study area and applied IDW, giving greater weight to near observations. The resulting yield map revealed spatial variations in productivity, highlighting both high-yield and low-yield zones.
- Creation of a vegetation vigor index 

To study the relationship between crop health and yield, I computed a vegetation index based on the available agronomic data. The index uses yield per unit area and humidity levels, which can influence crop productivity. Higher values indicate areas with higher productivity and sufficient moisture. Then I analyzed the correlation between the vegetation vigor index and yield to determine its predictive power. A scatter plot analysis showed a clear positive trend, and the correlation coefficient (0.65) confirmed a strong relationship. This result suggests that the vegetation index is an effective predictor of yield, providing a useful metric for future agricultural planning. 

## Files
- `resa_girasole_2022.gpkg` – dataset used for the analysis 
- `Test_Rurall.ipynb` – code for the implementation 

## Tools used
- **Programming**: Python, Jupyter Notebook
- **Libraries**: geopandas, pandas, NumPy, SciPy
- **Data Visualization**: Matplotlib, Seaborn
