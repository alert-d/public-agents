# Open-Meteo Weather Forecast Service

The Open-Meteo Weather Forecast service provides comprehensive weather forecasting capabilities using multi-model data from global and regional weather services. This service delivers accurate, up-to-date weather information for any location worldwide.

## Core Capabilities

### **Weather Forecasting**

- **Forecast Range**: Up to 16 days of detailed weather predictions
- **Update Frequency**: Real-time updates from multiple weather models
- **Coverage**: Global coverage with high-resolution regional data
- **Accuracy**: Multi-model ensemble approach for improved reliability

### **Data Granularity**

- **Hourly Forecasts**: Detailed hourly weather conditions
- **Daily Summaries**: Daily weather summaries and extremes
- **Current Conditions**: Real-time current weather data
- **Historical Data**: Access to historical weather archives

### **Selective Data Extraction**

- **Efficient Queries**: Extract only the weather variables you need
- **Reduced Payload**: Smaller responses for faster processing
- **Focused Analysis**: LLM gets targeted data instead of overwhelming JSON
- **Flexible Selection**: Choose single fields or multiple variables

**Examples:**

- Get just rain data: `"select": ["current.precipitation", "hourly.precipitation"]`
- Get temperature trends: `"select": ["daily.temperature_2m_max", "daily.temperature_2m_min"]`
- Get current conditions: `"select": ["current.temperature_2m", "current.wind_speed_10m", "current.weather_code"]`

## Available Weather Variables

### **Temperature & Humidity**

- `temperature_2m`: 2-meter air temperature
- `temperature_2m_max/min`: Daily temperature extremes
- `apparent_temperature`: Feels-like temperature
- `relative_humidity_2m`: Relative humidity at 2 meters
- `dew_point_2m`: Dew point temperature

### **Precipitation**

- `precipitation`: Total precipitation (rain + snow)
- `precipitation_probability`: Probability of precipitation
- `rain`: Liquid precipitation
- `snowfall`: Snow accumulation
- `showers`: Showers intensity

### **Wind & Atmospheric**

- `wind_speed_10m`: Wind speed at 10 meters
- `wind_direction_10m`: Wind direction
- `wind_gusts_10m`: Wind gusts
- `pressure_msl`: Mean sea level pressure
- `surface_pressure`: Surface pressure

### **Solar & Radiation**

- `uv_index`: UV index
- `uv_index_max`: Maximum daily UV index
- `sunshine_duration`: Duration of sunshine
- `shortwave_radiation`: Solar radiation
- `direct_radiation`: Direct solar radiation

### **Visibility & Clouds**

- `cloud_cover`: Total cloud cover percentage
- `cloud_cover_low/mid/high`: Cloud cover by altitude
- `visibility`: Visibility range
- `weather_code`: Weather condition codes

## Use Cases

### **Personal Weather**

- Daily weather planning and preparation
- Outdoor activity scheduling
- Travel weather information
- Clothing and gear recommendations

### **Business Applications**

- Agriculture and farming decisions
- Construction and outdoor work planning
- Event planning and risk assessment
- Energy production optimization

### **Scientific Research**

- Climate studies and analysis
- Weather pattern research
- Environmental monitoring
- Academic research projects

## Technical Features

### **Multi-Model Support**

- **GFS**: Global Forecast System (NOAA)
- **ICON**: ICOsahedral Nonhydrostatic model (DWD)
- **IFS**: Integrated Forecasting System (ECMWF)
- **HRRR**: High-Resolution Rapid Refresh (NOAA)

### **Flexible Units**

- Temperature: Celsius, Fahrenheit
- Wind Speed: km/h, mph, m/s, knots
- Precipitation: mm, inch
- Pressure: hPa, mmHg, inHg

### **Geographic Coverage**

- **Global**: Worldwide coverage
- **High-Resolution**: Regional models for enhanced accuracy
- **Elevation Support**: Terrain-aware forecasting
- **Marine**: Ocean and coastal weather

## Data Quality

### **Accuracy Metrics**

- **Short-term**: 1-3 days with high accuracy
- **Medium-term**: 4-7 days with good reliability
- **Long-term**: 8-16 days with general trends
- **Ensemble**: Probabilistic forecasts for uncertainty

### **Update Schedule**

- **Real-time**: Continuous model updates
- **Hourly**: Fresh forecast data
- **Daily**: Model reanalysis
- **Seasonal**: Long-range outlooks

## Global Coverage

The service provides weather forecasts for:

- **All continents** and major landmasses
- **Ocean regions** and marine areas
- **Polar regions** including Arctic and Antarctic
- **Remote locations** and islands
- **Urban areas** with enhanced resolution

## Integration

### **API Endpoints**

- **Forecast**: `/v1/forecast` - Main forecasting service
- **Historical**: `/v1/archive` - Past weather data
- **Ensemble**: `/v1/ensemble` - Probabilistic forecasts
- **Marine**: `/v1/marine` - Ocean weather data

### **Data Formats**

- **JSON**: Structured weather data
- **CSV**: Tabular data export
- **GeoJSON**: Geospatial weather data
- **Time Series**: Temporal data analysis

### **Forecast Durations**

- **Current**: Real-time conditions
- **Hourly**: Up to 168 hours (7 days)
- **Daily**: Up to 16 days
- **15-minutely**: Short-term detailed forecasts
- **Historical**: Up to 92 days in the past

This service enables users to access professional-grade weather forecasting capabilities for any location worldwide, supporting both personal and professional weather-dependent decisions.
