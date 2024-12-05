# Wildfire Impact Assessment on Boulder, Colorado: Data-512 Final Project

## Overview

This project investigates the impact of wildfire smoke on air quality and public health in Boulder, Colorado, by analyzing historical wildfire data, mortality rates, and air quality trends. Using data from the US Geological Survey (USGS), the CDC Wonder API, and the EPA Air Quality System (AQS) API, this study calculates smoke exposure estimates and correlates them with respiratory mortality trends. It also employs time series modeling to predict future smoke impacts up to 2050, offering actionable insights for policymakers and stakeholders.

The study aligns with human-centered data science principles, ensuring ethical handling of health and environmental data while communicating findings effectively to inform decision-making.

---

## Repository Structure

```
data-512-Final-Project/
│
├── data/
│   ├── GeoJSON Exports/
│   │   ├── boulder_fires_final.json
│   │   ├── boulder_1800fires_final.json
│   │   ├── USGS_Wildland_Fire_Combined_Dataset.json
│   │   ├── Wildland_Fire_Polygon_Metadata.xml
│   ├── cleaned_Smoke_Estimate_Annual.csv
│   ├── Refined_Underlying_Cause_of_Death.txt
│   ├── AQI Data (aqi_gaseous.csv, aqi_particulate.csv, etc.)
│   └── Wildfire.zip
│
├── scripts/
│   ├── data-extraction-analysis.ipynb
│   ├── part-2-analysis.ipynb
│   ├── epa_air_quality_history_example.ipynb
│   └── wildfire_geo_proximity_example.ipynb
│
├── wildfire/
│   ├── Reader.py
│   ├── Wildfire_short_sample_2024.json
│
├── LICENSE
├── README.md
└── Final Reports (PDFs of analyses, PechaKucha presentation, etc.)
```

---

## Data Sources and Descriptions

### Wildfire Data
- **Source**: US Geological Survey (USGS)
- **Description**: Combined wildland fire polygons dataset spanning 1961–2021, filtered to include fires within a 650-mile radius of Boulder.
- **Usage**: Used to calculate annual smoke impacts based on fire size and distance.

### Mortality Data
- **Source**: CDC Wonder API
- **Description**: Mortality rates and population data for Boulder, focusing on respiratory-related causes of death (1999–2020).
- **Usage**: Correlated with smoke estimates to analyze health impacts.

### Air Quality Data
- **Source**: EPA Air Quality System (AQS) API
- **Description**: Historical AQI data for Boulder, including trends in particulate and gaseous pollutants.
- **Usage**: Validated smoke estimates and provided additional insights into air quality impacts.

---

## Methodology

### 1. Smoke Impact Calculation
**Formula**:  
\[
\text{Smoke Impact} = \frac{\text{Fire Size in Acres} \times \alpha}{\text{Distance from Boulder}^2}
\]  
where \( \alpha = 15.625 \) is a scaling factor to standardize the smoke impact.

**Steps**:
- Filter fires occurring between May and October (wildfire season).
- Aggregate smoke impact values annually.

---

### 2. Mortality Rate Analysis
- Calculated annual respiratory-related mortality rates per 100,000 population.
- Focused on causes like chronic lower respiratory diseases and pneumonia.

---

### 3. Data Integration
- Merged wildfire, mortality, and AQI data on a yearly basis.
- Addressed missing data and ensured alignment across datasets.

---

### 4. Predictive Modeling
- **Model**: Seasonal ARIMA (SARIMA) to forecast smoke exposure up to 2050.
- **Validation**: Model predictions validated using historical data and residual normality tests.

---

## Visualizations

1. **Histogram of Fires by Distance**: Distribution of wildfires by their proximity to Boulder, with a cutoff at 650 miles.
2. **Total Acres Burned per Year**: Temporal variation in burned acres within 650 miles of Boulder.
3. **Trends in Smoke Impact and Mortality Rates**: Correlation between smoke exposure and respiratory mortality rates.
4. **Correlation Heatmaps**: Relationships between variables like population, smoke impact, and mortality.
5. **SARIMA Predictions**: Forecasts for smoke impacts with confidence intervals.
6. **Cause-Specific Mortality Trends**: Focused on specific respiratory diseases like pneumonia.

---

## Key Findings

### Trends in Smoke Impact and Mortality Rates
- Positive correlation observed between smoke impact and respiratory mortality rates.
- Significant peaks in smoke impact coincided with wildfire seasons.

---

### Cause-Specific Mortality Analysis
- Chronic lower respiratory diseases and pneumonia were the most impacted causes.
- Highlights the need for targeted interventions during wildfire seasons.

---

### Predictive Insights
- SARIMA forecasts indicate increasing smoke exposure in Boulder.
- Suggests proactive wildfire mitigation and public health preparedness.

---

### Air Quality Validation
- AQI trends corroborate smoke impact estimates, highlighting wildfire smoke's role in deteriorating air quality.

---

## Limitations

1. **Data Granularity**: Lack of fine-grained spatial or temporal resolution in some datasets.
2. **Simplified Assumptions**: Smoke impact formula does not account for wind patterns or fire duration.
3. **Confounding Factors**: Socioeconomic variables and healthcare access were not included.

---

## Conclusion

This project underscores the significant public health impacts of wildfire smoke in Boulder. Findings advocate for enhanced wildfire mitigation strategies and healthcare interventions to protect vulnerable populations. Future research should incorporate more granular data and explore socioeconomic factors to provide a holistic understanding of wildfire impacts.

---

## Installation and Usage

### Requirements
- **Python 3.8+**
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `geopandas`, `statsmodels`, `fiona`, `shapely`, `scikit-learn`

### Steps to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/radhikasethi2011/data-512-Final-Project.git
   ```
2. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn geopandas statsmodels scikit-learn
   ```
3. Open and run `data-extraction-analysis.ipynb` for initial data processing.
4. Use `part-2-analysis.ipynb` for extended analysis and modeling.

---

## Acknowledgments

- **Professor’s Resources**: Example notebooks and datasets provided a strong foundation for this project.
- **Open-Source Tools**: Python libraries like `statsmodels` and `matplotlib` were instrumental in analysis and visualization.

---

## References

1. **USGS Wildfire Data**: [ScienceBase.gov](https://www.sciencebase.gov/catalog/item/61707c2ad34ea36449a6b066)
2. **CDC Wonder API**: [CDC Wonder](https://wonder.cdc.gov/)
3. **EPA Air Quality System**: [EPA AQS API](https://www.epa.gov/aqs)

