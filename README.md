
# data-512-Final-Project: Wildfire Impact Assessment for Boulder, CO

This repository contains the code, data, and analysis for assessing the impact of wildfires on air quality in Boulder, CO. The primary focus is to analyze historical wildfire data, calculate smoke exposure estimates, and correlate these estimates with AQI (Air Quality Index) values over time. Additionally, we employ time series models to forecast future smoke exposure trends up to 2050.

### Repository Structure

```
data-512-Final-Project
├── data
│   ├── GeoJSON Exports                # Wildfire data files obtained from ScienceBase.gov
│   │   ├── boulder_fires_final.json
│   │   ├── USGS_Wildland_Fire_Combined_Dataset.json
│   │   ├── USGS_Wildland_Fire_Merged_Dataset.json
│   │   ├── Wildland_Fire_Polygon_Metadata.xml
│   ├── aqi_gaseous.csv                # AQI data for gaseous pollutants
│   ├── aqi_particulate.csv            # AQI data for particulate pollutants
│   ├── aqi_yoy.csv                    # Year-over-year AQI data
│   ├── boulder_1800fires_final.json   # Filtered data for fires within 1800 miles of Boulder
│   ├── boulder_fires_final.json       # Filtered data for fires within 650 miles of Boulder
│   ├── gaseous_data.json              # AQI data processed for gaseous pollutants
│   ├── particulate_data.json          # AQI data processed for particulate pollutants
│   ├── Smoke_Estimate_Annual.csv      # Annual smoke estimates based on fire data
├── scripts
│   ├── data-extraction-analysis.ipynb # Main notebook for data extraction, analysis, and modeling
│   ├── epa_air_quality_history_example.ipynb   # EPA air quality example notebook from professor
│   ├── wildfire_geo_proximity_example.ipynb    # Wildfire geographic proximity example notebook from professor
├── wildfire
│   ├── Reader.py                      # Provided reader for handling wildfire data
│   ├── Wildfire_short_sample_2024.json # Sample JSON file for testing
├── .gitignore                         # Git ignore file for excluding unnecessary files
├── LICENSE                            # License file for the project
└── README.md                          # Project README file (you are here)
```

### Folder and File Explanations

- **`data/GeoJSON Exports/`**: Contains wildfire data files sourced from the link provided by the professor ([ScienceBase.gov](https://www.sciencebase.gov/catalog/item/61707c2ad34ea36449a6b066)). These files include comprehensive wildfire metadata and datasets.
  
- **`data/`**: Includes both raw and processed data files used in this analysis:
  - `aqi_gaseous.csv`, `aqi_particulate.csv`, and `aqi_yoy.csv`: CSV files containing AQI data for various pollutants, processed for analysis.
  - `boulder_1800fires_final.json` and `boulder_fires_final.json`: Filtered JSON files that include only the fires within specific radii (650 miles and 1800 miles) around Boulder.
  - `Smoke_Estimate_Annual.csv`: Contains yearly aggregated smoke estimates calculated from wildfire data, used in modeling and forecasting.

- **`scripts/`**: Houses Jupyter notebooks for data analysis, model building, and example notebooks provided by the professor:
  - `data-extraction-analysis.ipynb`: Main analysis notebook where data is processed, visualizations are generated, and SARIMA modeling is applied.
  - `epa_air_quality_history_example.ipynb` and `wildfire_geo_proximity_example.ipynb`: Example notebooks from the professor that demonstrate accessing AQI data and calculating wildfire proximity.

- **`wildfire/`**: Contains helper files provided by the professor, such as `Reader.py` for parsing wildfire data and a sample JSON file for testing.

### Project Overview

The main objectives of this project are:
1. **Quantify Smoke Impact**: Calculate annual smoke exposure estimates based on proximity and size of wildfires around Boulder, CO.
2. **Forecast Future Smoke Exposure**: Use SARIMA time series models to forecast smoke estimates for the next 25 years.
3. **Correlate Wildfire Activity with AQI**: Analyze how smoke exposure estimates align with historical AQI data to understand potential impacts on air quality.

### Key Methods and Techniques

1. **Data Processing**:
   - **Filtering Fires by Distance**: Using provided wildfire data, fires within specific distance thresholds (650 miles and 1800 miles) of Boulder are selected. This allows us to focus on fires that are most likely to impact Boulder’s air quality.
   - **Annual Aggregation of Smoke Estimates**: Each fire’s smoke impact is calculated using its size and distance from Boulder, and then summed annually to get yearly smoke estimates.

2. **Calculating Smoke Impact**:
   - **Formula**:
     ```
     Smoke Impact = (Fire Size in Acres) / (Distance from Boulder)^2
     ```
     This formula helps in weighting the impact of fires based on their proximity and size, giving more weight to closer, larger fires.

3. **Time Series Modeling**:
   - **SARIMA**: Seasonal ARIMA (SARIMA) is applied to forecast smoke exposure from wildfires up to 2050. The model accounts for both trend and seasonality in the historical smoke estimate data.
   - **Validation and Forecasting**: The model is trained on historical data, validated on a holdout set, and used to generate future forecasts with 95% confidence intervals.

### Visualizations

1. **Histogram of Fire Distances**: A histogram showing the distribution of fires by their distance from Boulder, with a cutoff at 650 miles. This visualization helps in understanding the spatial spread of fires impacting Boulder.
   
2. **Total Acres Burned per Year**: A line plot showing annual variation in total burned acres within 650 miles of Boulder. This highlights temporal patterns and any trends in fire severity over time.
   
3. **Comparison of Smoke Estimates and AQI**: A line plot that overlays smoke exposure estimates and AQI values for Boulder. This visualization aims to reveal correlations between wildfire activity and air quality changes.
   
4. **SARIMA Model Predictions on Original Data**: This plot shows the SARIMA model's predictions for smoke estimates over the validation set, providing insight into model accuracy.

5. **SARIMA Model Predictions on Smoothed Data**: For improved readability, the SARIMA predictions are plotted on smoothed data, which reduces noise and better illustrates trend patterns.

6. **Normality Test on Residuals**: A Q-Q plot to assess the normality of residuals from the SARIMA model. Three statistical tests (Shapiro-Wilk, Anderson-Darling, and D’Agostino's K-squared) confirm the residuals follow a normal distribution, validating model assumptions.

7. **Forecast with 95% Confidence Intervals**: A final plot showing the SARIMA model's forecasted smoke estimates up to 2050 with confidence intervals. This is crucial for understanding the uncertainty in predictions.

### Installation and Usage

#### Requirements

- Python 3.x
- Required packages: `pandas`, `numpy`, `matplotlib`, `statsmodels`, `pmdarima`, `geopy`, `fiona`, `shapely`

#### Running the Analysis

Clone the repository:
```bash
git clone https://github.com/radhikasethi2011/data-512-Final-Project.git
```

1. Navigate to the project directory and open `data-extraction-analysis.ipynb` in Jupyter Notebook or Jupyter Lab.
2. Run each cell sequentially to reproduce the analysis, visualizations, and model predictions.

### Reflection

This project required collaboration on key steps like accessing AQI data, wildfire filtering, and model validation. Working with example notebooks from the professor, such as the EPA air quality history example and wildfire proximity example, significantly accelerated the process and provided a strong foundation. Collaborating with peers helped refine the approach and ensured a comprehensive analysis. 

### Acknowledgments

- **Professor’s Resources**: The AQI and wildfire data examples were instrumental in setting up data processing pipelines.
- **Libraries and Tools**: Python libraries such as `pandas`, `statsmodels`, and `matplotlib` were essential for data handling, model building, and visualization.

### License
This project is licensed under the MIT License. See the LICENSE file for details.

