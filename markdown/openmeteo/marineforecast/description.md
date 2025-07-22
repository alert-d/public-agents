# Open-Meteo Marine Weather API

The Open-Meteo Marine Weather API provides comprehensive marine weather forecasting capabilities for ocean and coastal areas worldwide. This service delivers detailed wave forecasts, sea surface temperatures, ocean currents, and marine conditions at high resolution for maritime operations, coastal activities, and marine research.

## Core Capabilities

### **Marine Weather Forecasting**

- **Forecast Range**: Up to 16 days of detailed marine weather predictions
- **Update Frequency**: Real-time updates from multiple marine weather models
- **Coverage**: Global ocean coverage with high-resolution regional data
- **Accuracy**: Multi-model ensemble approach for improved reliability
- **Resolution**: 5 km resolution for detailed coastal and offshore data

### **Data Granularity**

- **Hourly Forecasts**: Detailed hourly marine conditions
- **Daily Summaries**: Daily marine weather summaries and extremes
- **Current Conditions**: Real-time current marine data
- **Historical Data**: Access to historical marine weather archives

### **Selective Data Extraction**

- **Efficient Queries**: Extract only the marine variables you need
- **Reduced Payload**: Smaller responses for faster processing
- **Focused Analysis**: LLM gets targeted data instead of overwhelming JSON
- **Flexible Selection**: Choose single fields or multiple variables

**Examples:**

- Get just wave data: `"select": ["current.wave_height", "hourly.wave_height"]`
- Get sea temperature trends: `"select": ["daily.sea_surface_temperature"]`
- Get current marine conditions: `"select": ["current.wave_height", "current.wave_direction", "current.sea_surface_temperature"]`

## Available Marine Variables

### **Wave Data**

- `wave_height`: Significant wave height (mean)
- `wind_wave_height`: Wind-generated wave height
- `swell_wave_height`: Swell wave height
- `secondary_swell_wave_height`: Secondary swell component
- `tertiary_swell_wave_height`: Tertiary swell component

### **Wave Direction**

- `wave_direction`: Mean wave direction
- `wind_wave_direction`: Wind wave direction
- `swell_wave_direction`: Swell wave direction
- `secondary_swell_wave_direction`: Secondary swell direction
- `tertiary_swell_wave_direction`: Tertiary swell direction

### **Wave Period**

- `wave_period`: Mean wave period
- `wind_wave_period`: Wind wave period
- `swell_wave_period`: Swell wave period
- `secondary_swell_wave_period`: Secondary swell period
- `tertiary_swell_wave_period`: Tertiary swell period
- `wind_wave_peak_period`: Wind wave peak period
- `swell_wave_peak_period`: Swell wave peak period

### **Ocean Conditions**

- `sea_surface_temperature`: Sea surface temperature (SST)
- `ocean_current_velocity`: Ocean current speed
- `ocean_current_direction`: Ocean current direction
- `sea_level_height_msl`: Sea level height including tides
- `invert_barometer_height`: Inverted barometer effect height

## Use Cases

### **Maritime Operations**

- Commercial shipping and navigation
- Fishing operations and marine aquaculture
- Offshore oil and gas operations
- Marine construction and engineering
- Search and rescue operations

### **Recreational Marine**

- Sailing and boating activities
- Surfing and water sports
- Coastal tourism and beach activities
- Marine wildlife observation
- Recreational fishing

### **Coastal Management**

- Coastal erosion monitoring
- Port operations and management
- Marine safety and emergency response
- Environmental monitoring
- Coastal infrastructure planning

### **Scientific Research**

- Oceanographic studies
- Marine ecosystem research
- Climate change impact assessment
- Marine renewable energy planning
- Academic research projects

## Technical Features

### **Multi-Model Support**

- **MeteoFrance MFWAM**: Global wave model (0.08° resolution)
- **MeteoFrance SMOC**: Currents, tides & SST (0.08° resolution)
- **ECMWF WAM**: Global wave model (0.25° resolution)
- **NCEP GFS Wave**: Global wave model (0.25° resolution)
- **DWD EWAM**: European wave model (0.05° resolution)
- **DWD GWAM**: Global wave model (0.25° resolution)
- **ERA5-Ocean**: Historical ocean data (0.5° resolution)

### **Flexible Units**

- Length: Metric (meters), Imperial (feet)
- Velocity: km/h, mph, m/s, knots
- Temperature: Celsius, Fahrenheit
- Direction: Degrees (0° = North, 90° = East)

### **Geographic Coverage**

- **Global Oceans**: Worldwide marine coverage
- **High-Resolution**: Regional models for enhanced accuracy
- **Coastal Areas**: Detailed coastal and nearshore data
- **Deep Ocean**: Open ocean conditions
- **Polar Regions**: Arctic and Antarctic marine conditions

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

### **Model Update Frequency**

- **MeteoFrance MFWAM**: Every 12 hours
- **MeteoFrance SMOC**: Every 24 hours
- **ECMWF WAM**: Every 6 hours
- **NCEP GFS Wave**: Every 6 hours
- **DWD EWAM**: Twice daily
- **DWD GWAM**: Twice daily
- **ERA5-Ocean**: Daily with 5 days delay

## Global Coverage

The service provides marine weather forecasts for:

- **All major oceans** and seas worldwide
- **Coastal regions** with enhanced resolution
- **Polar regions** including Arctic and Antarctic waters
- **Island nations** and remote marine areas
- **Major shipping lanes** and maritime routes

## Integration

### **API Endpoints**

- **Marine Forecast**: `/v1/marine` - Main marine forecasting service
- **Historical Marine**: `/v1/archive` - Past marine weather data
- **Geocoding**: `/v1/search` - Location coordinate lookup
- **Elevation**: `/v1/elevation` - Terrain and bathymetry data

### **Data Formats**

- **JSON**: Structured marine weather data
- **CSV**: Tabular data export
- **GeoJSON**: Geospatial marine data
- **Time Series**: Temporal data analysis

### **Forecast Durations**

- **Current**: Real-time marine conditions
- **Hourly**: Up to 168 hours (7 days)
- **Daily**: Up to 8 days
- **15-minutely**: Short-term detailed forecasts
- **Historical**: Up to 92 days in the past

## Important Notes

### **Coastal Navigation**

- **Limited Accuracy**: Coastal area accuracy is limited
- **Not for Navigation**: Not suitable for coastal navigation
- **Nautical Almanac**: Does not replace nautical almanac
- **Use with Caution**: Exercise caution in coastal areas

### **Data Limitations**

- **Tides**: Computed at 0.08° (~8 km) resolution
- **Ocean Currents**: Limited accuracy in coastal areas
- **Secondary Swell**: Only available for some models
- **Tertiary Swell**: Only available for GFS wave models

This service enables users to access professional-grade marine weather forecasting capabilities for any ocean location worldwide, supporting both commercial and recreational marine activities while providing essential data for marine safety and environmental monitoring.
