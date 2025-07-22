# Open-Meteo Air Quality API

The Open-Meteo Air Quality API provides comprehensive air quality forecasting capabilities for pollutants, pollen, and air quality indices worldwide. This service delivers detailed air quality data at 11 km resolution using CAMS (Copernicus Atmosphere Monitoring Service) models for both European and global coverage.

## Core Capabilities

### **Air Quality Forecasting**

- **Forecast Range**: Up to 7 days of detailed air quality predictions
- **Update Frequency**: Real-time updates from CAMS European and Global models
- **Coverage**: Global coverage with high-resolution European data
- **Accuracy**: Multi-model ensemble approach for improved reliability
- **Resolution**: 11 km resolution for detailed air quality data

### **Data Granularity**

- **Hourly Forecasts**: Detailed hourly air quality conditions
- **Current Conditions**: Real-time current air quality data
- **Historical Data**: Access to historical air quality archives
- **Pollen Forecasts**: Seasonal pollen predictions for Europe

### **Selective Data Extraction**

- **Efficient Queries**: Extract only the air quality variables you need
- **Reduced Payload**: Smaller responses for faster processing
- **Focused Analysis**: LLM gets targeted data instead of overwhelming JSON
- **Flexible Selection**: Choose single fields or multiple variables

**Examples:**

- Get just PM data: `"select": ["current.pm10", "hourly.pm2_5"]`
- Get air quality indices: `"select": ["daily.european_aqi", "daily.us_aqi"]`
- Get current conditions: `"select": ["current.pm10", "current.ozone", "current.nitrogen_dioxide"]`

## Available Air Quality Variables

### **Particulate Matter**

- `pm10`: Particulate matter with diameter smaller than 10 µm
- `pm2_5`: Particulate matter with diameter smaller than 2.5 µm

### **Atmospheric Gases**

- `carbon_monoxide`: Carbon monoxide concentration
- `nitrogen_dioxide`: Nitrogen dioxide concentration
- `sulphur_dioxide`: Sulphur dioxide concentration
- `ozone`: Ozone concentration
- `carbon_dioxide`: Carbon dioxide concentration (ppm)
- `ammonia`: Ammonia concentration (Europe only)
- `methane`: Methane concentration

### **Air Quality Indices**

- `european_aqi`: European Air Quality Index (0-100+)
- `european_aqi_pm2_5`: European AQI for PM2.5
- `european_aqi_pm10`: European AQI for PM10
- `european_aqi_nitrogen_dioxide`: European AQI for NO2
- `european_aqi_ozone`: European AQI for O3
- `european_aqi_sulphur_dioxide`: European AQI for SO2
- `us_aqi`: United States Air Quality Index (0-500)
- `us_aqi_pm2_5`: US AQI for PM2.5
- `us_aqi_pm10`: US AQI for PM10
- `us_aqi_nitrogen_dioxide`: US AQI for NO2
- `us_aqi_ozone`: US AQI for O3
- `us_aqi_sulphur_dioxide`: US AQI for SO2
- `us_aqi_carbon_monoxide`: US AQI for CO

### **Additional Variables**

- `aerosol_optical_depth`: Aerosol optical depth at 550 nm
- `dust`: Saharan dust particles
- `uv_index`: UV index considering clouds
- `uv_index_clear_sky`: UV index for clear sky

### **Pollen Variables (Europe Only)**

- `alder_pollen`: Alder pollen concentration
- `birch_pollen`: Birch pollen concentration
- `grass_pollen`: Grass pollen concentration
- `mugwort_pollen`: Mugwort pollen concentration
- `olive_pollen`: Olive pollen concentration
- `ragweed_pollen`: Ragweed pollen concentration

## Use Cases

### **Public Health**

- Air quality monitoring for vulnerable populations
- Health advisories and warnings
- Respiratory condition management
- Outdoor activity planning

### **Environmental Monitoring**

- Pollution tracking and analysis
- Industrial emission monitoring
- Urban air quality assessment
- Environmental compliance reporting

### **Personal Health**

- Daily air quality planning
- Exercise and outdoor activity timing
- Travel planning for air quality
- Home ventilation decisions

### **Research and Analysis**

- Air quality trend analysis
- Pollution source identification
- Climate change impact studies
- Academic research projects

## Technical Features

### **Multi-Model Support**

- **CAMS European Air Quality Forecast**: Europe, 0.1° resolution (~11 km)
- **CAMS European Air Quality Reanalysis**: Europe, 0.1° resolution (~11 km)
- **CAMS Global Atmospheric Composition**: Global, 0.25° resolution (~25 km)
- **CAMS Global Greenhouse Gas Forecast**: Global, 0.1° resolution (~11 km)

### **Geographic Coverage**

- **European Domain**: High-resolution coverage with detailed pollutants and pollen
- **Global Domain**: Worldwide coverage for major air quality parameters
- **Auto Domain**: Automatic combination of European and global data
- **Regional Focus**: Enhanced resolution for European air quality monitoring

### **Data Quality**

- **Update Frequency**: European (24 hours), Global (12 hours)
- **Forecast Duration**: Up to 7 days
- **Historical Data**: Available from 2013 onwards for Europe
- **Pollen Season**: Seasonal availability for European pollen forecasts

## Air Quality Index Scales

### **European AQI**

- **0-20**: Good
- **20-40**: Fair
- **40-60**: Moderate
- **60-80**: Poor
- **80-100**: Very Poor
- **100+**: Extremely Poor

### **US AQI**

- **0-50**: Good
- **51-100**: Moderate
- **101-150**: Unhealthy for Sensitive Groups
- **151-200**: Unhealthy
- **201-300**: Very Unhealthy
- **301-500**: Hazardous

## Global Coverage

The service provides air quality forecasts for:

- **All continents** and major landmasses
- **Urban areas** with enhanced monitoring
- **European regions** with high-resolution data
- **Remote locations** with global coverage
- **Coastal areas** and island nations

## Integration

### **API Endpoints**

- **Air Quality Forecast**: `/v1/air-quality` - Main air quality service
- **Geocoding**: `/v1/search` - Location coordinate lookup
- **Elevation**: `/v1/elevation` - Terrain data

### **Data Formats**

- **JSON**: Structured air quality data
- **CSV**: Tabular data export
- **GeoJSON**: Geospatial air quality data
- **Time Series**: Temporal data analysis

### **Forecast Durations**

- **Current**: Real-time air quality conditions
- **Hourly**: Up to 168 hours (7 days)
- **Historical**: Up to 92 days in the past
- **Pollen**: 4-day forecasts during season

## Important Notes

### **Regional Availability**

- **Pollen Data**: Only available in Europe during pollen season
- **Ammonia**: European coverage only
- **High Resolution**: Enhanced detail for European domain
- **Global Coverage**: Coarser resolution for worldwide data

### **Data Limitations**

- **Pollen Season**: Limited to specific seasons and regions
- **Model Updates**: Different update frequencies for different domains
- **Resolution**: Varies by geographic region and data type
- **Historical Data**: Limited availability for some parameters

This service enables users to access professional-grade air quality forecasting capabilities for any location worldwide, supporting both personal health decisions and environmental monitoring applications.
