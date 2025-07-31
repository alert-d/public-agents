# Open-Meteo Historical Weather Service

The Open-Meteo Historical Weather service provides access to detailed reanalysis-based historical weather data from up to 1940 onward. This service uses multiple high-quality datasets to deliver comprehensive historical weather information for climate analysis, research, and historical weather inquiries.

## Core Capabilities

### **Historical Data Access**

- **Data Range**: Historical weather data from 1940 to present
- **Multiple Datasets**: Access to various reanalysis models and data sources
- **Global Coverage**: Worldwide historical weather data
- **High Resolution**: Detailed temporal and spatial resolution
- **Quality Assurance**: Reanalysis data provides consistent, validated historical records

### **Data Granularity**

- **Hourly Data**: Detailed hourly historical weather conditions
- **Daily Aggregations**: Daily weather summaries and extremes
- **Flexible Time Ranges**: Customizable start and end dates
- **Multiple Variables**: Access to 35+ weather variables

### **Selective Data Extraction**

- **Efficient Queries**: Extract only the historical weather variables you need
- **Reduced Payload**: Smaller responses for faster processing
- **Focused Analysis**: LLM gets targeted data instead of overwhelming JSON
- **Flexible Selection**: Choose single fields or multiple variables

**Examples:**

- Get temperature history: `"select": ["hourly.temperature_2m", "daily.temperature_2m_max"]`
- Get precipitation data: `"select": ["hourly.precipitation", "daily.precipitation_sum"]`
- Get wind patterns: `"select": ["hourly.wind_speed_10m", "hourly.wind_direction_10m"]`

## Data Sources (Reanalysis Models)

The historical weather service uses multiple high-quality reanalysis datasets to provide comprehensive historical weather data:

### **ECMWF IFS**

- **Region**: Global
- **Resolution**: 9 km
- **Temporal Resolution**: Hourly
- **Available From**: 2017 – Present
- **Update Frequency**: Daily (2-day delay)

### **ERA5**

- **Region**: Global
- **Resolution**: 0.25° (~25 km)
- **Temporal Resolution**: Hourly
- **Available From**: 1940 – Present
- **Update Frequency**: Daily (5-day delay)

### **ERA5-Land**

- **Region**: Global
- **Resolution**: 0.1° (~11 km)
- **Temporal Resolution**: Hourly
- **Available From**: 1950 – Present
- **Update Frequency**: Daily (5-day delay)

### **ERA5-Ensemble**

- **Region**: Global
- **Resolution**: 0.5° (~55 km)
- **Temporal Resolution**: 3-Hourly
- **Available From**: 1940 – Present
- **Update Frequency**: Daily (5-day delay)

### **CERRA**

- **Region**: Europe
- **Resolution**: 5 km
- **Temporal Resolution**: Hourly
- **Available From**: 1985 – June 2021
- **Update Frequency**: Static

### **ECMWF IFS Assimilation**

- **Region**: Global
- **Resolution**: 9 km
- **Temporal Resolution**: 6-Hourly
- **Available From**: 2024 – Present
- **Update Frequency**: Daily (2-day delay)

> 📌 **Note**: For long-term climate analysis, prefer **ERA5** or **ERA5-Land** to avoid version drift from model upgrades.

## API Endpoint

### **Historical Weather**

- **URL**: `https://api.open-meteo.com/v1/archive`
- **Method**: `GET`
- **Description**: Access detailed reanalysis-based historical weather data from up to 1940 onward

## Query Parameters

### **Required Parameters**

- **`latitude`, `longitude`** (Float / Float): WGS84 coordinates (comma-separated for batch mode)
- **`start_date`, `end_date`** (Date `yyyy-mm-dd`): Time interval of interest

### **Optional Parameters**

- **`elevation`** (Float, Default: DEM 90m): Manual override for elevation
- **`hourly`** (Array String): Hourly weather variables
- **`daily`** (Array String): Daily aggregations (requires `timezone`)
- **`temperature_unit`** (String, Default: `celsius`): Or `fahrenheit`
- **`wind_speed_unit`** (String, Default: `kmh`): `ms`, `mph`, `kn`
- **`precipitation_unit`** (String, Default: `mm`): Or `inch`
- **`timeformat`** (String, Default: `iso8601`): Or `unixtime` (UTC)
- **`timezone`** (String, Default: `GMT`): Use `auto` for local, or specify TZDB string
- **`cell_selection`** (String, Default: `land`): Options: `land`, `sea`, `nearest`
- **`apikey`** (String): Required for commercial use only

## Available Weather Variables

### **Hourly Variables (Partial List)**

- **`temperature_2m`** (Instant, °C/°F): Air temperature 2m above ground
- **`relative_humidity_2m`** (Instant, %): Relative humidity
- **`precipitation`** (Preceding hour sum, mm/inch): Total precipitation
- **`cloud_cover`** (Instant, %): Total cloud area fraction
- **`wind_speed_10m`** (Instant, km/h/mph): Wind speed at 10m
- **`wind_direction_10m`** (Instant, °): Wind direction at 10m
- **`shortwave_radiation`** (Preceding hour mean, W/m²): Solar radiation
- **`et0_fao_evapotranspiration`** (Preceding hour sum, mm): Reference evapotranspiration
- **`snow_depth`** (Instant, m): Estimated snow depth
- **`soil_temperature_0_to_7cm`** (Instant, °C/°F): Topsoil temperature
- **`vapour_pressure_deficit`** (Instant, kPa): Plant transpiration stress indicator

> **Full list includes ~35+ variables** for soil, cloud layers, snow, wind, and radiation.

### **Daily Variables (Aggregated)**

- **`temperature_2m_max`** (°C/°F): Daily maximum temperature
- **`temperature_2m_min`** (°C/°F): Daily minimum temperature
- **`precipitation_sum`** (mm): Total daily precipitation
- **`weather_code`** (WMO code): Most severe weather condition
- **`sunrise`, `sunset`** (iso8601): Local sunrise and sunset times
- **`wind_speed_10m_max`** (km/h): Maximum wind speed
- **`shortwave_radiation_sum`** (MJ/m²): Total solar energy
- **`et0_fao_evapotranspiration`** (mm): Plant irrigation need

## Example Requests

### **Basic Historical Weather Query**

```http
GET https://api.open-meteo.com/v1/archive?
latitude=40.71&longitude=-74.01&
start_date=2024-07-01&end_date=2024-07-10&
hourly=temperature_2m,precipitation&
timezone=auto
```

### **Comprehensive Historical Analysis**

```http
GET https://api.open-meteo.com/v1/archive?
latitude=40.71&longitude=-74.01&
start_date=2020-01-01&end_date=2020-12-31&
hourly=temperature_2m,relative_humidity_2m,precipitation,wind_speed_10m&
daily=temperature_2m_max,temperature_2m_min,precipitation_sum&
temperature_unit=fahrenheit&
timezone=America/New_York
```

## Example Response

### **Simplified Response**

```json
{
  "latitude": 40.71,
  "longitude": -74.01,
  "generationtime_ms": 12.5,
  "utc_offset_seconds": -14400,
  "timezone": "America/New_York",
  "timezone_abbreviation": "EDT",
  "elevation": 10.0,
  "hourly_units": {
    "time": "iso8601",
    "temperature_2m": "°C",
    "precipitation": "mm"
  },
  "hourly": {
    "time": ["2024-07-01T00:00", "2024-07-01T01:00", "2024-07-01T02:00", ...],
    "temperature_2m": [24.5, 23.9, 23.2, ...],
    "precipitation": [0.0, 0.0, 0.1, ...]
  }
}
```

### **Daily Aggregations Response**

```json
{
  "daily_units": {
    "time": "iso8601",
    "temperature_2m_max": "°C",
    "temperature_2m_min": "°C",
    "precipitation_sum": "mm"
  },
  "daily": {
    "time": ["2024-07-01", "2024-07-02", "2024-07-03", ...],
    "temperature_2m_max": [28.5, 29.1, 27.8, ...],
    "temperature_2m_min": [20.3, 21.1, 19.9, ...],
    "precipitation_sum": [0.0, 5.2, 0.0, ...]
  }
}
```

## Use Cases

### **Climate Research**

- **Long-term Climate Analysis**: Study weather patterns over decades
- **Climate Change Studies**: Analyze temperature and precipitation trends
- **Academic Research**: Support scientific studies and publications
- **Historical Comparisons**: Compare current weather to historical periods

### **Business Applications**

- **Agriculture Planning**: Analyze historical weather for crop planning
- **Energy Production**: Study historical patterns for renewable energy
- **Insurance Risk Assessment**: Evaluate historical weather risks
- **Construction Planning**: Understand seasonal weather patterns

### **Data Analysis**

- **Weather Pattern Recognition**: Identify recurring weather patterns
- **Statistical Analysis**: Perform statistical analysis on historical data
- **Machine Learning**: Train models on historical weather data
- **Forecasting Validation**: Validate current forecasts against historical data

## Technical Features

### **Data Quality**

- **Reanalysis Quality**: High-quality, validated historical data
- **Consistent Methodology**: Uniform processing across all datasets
- **Multiple Sources**: Redundant data sources for reliability
- **Quality Control**: Automated quality checks and validation

### **Performance**

- **Fast Retrieval**: Optimized for quick historical data access
- **Efficient Storage**: Compressed data storage for large datasets
- **Caching**: Intelligent caching for frequently requested data
- **Batch Processing**: Support for multiple location queries

### **Flexible Units**

- **Temperature**: Celsius, Fahrenheit
- **Wind Speed**: km/h, mph, m/s, knots
- **Precipitation**: mm, inch
- **Pressure**: hPa, mmHg, inHg

## Integration Benefits

- **Seamless Integration**: Works with other Open-Meteo APIs
- **No API Keys**: Free access without authentication requirements
- **CORS Support**: Cross-origin requests enabled for web applications
- **Reliable Service**: High availability with redundant infrastructure
- **Comprehensive Documentation**: Complete API reference and examples

## Common Applications

- Climate research platforms
- Agricultural planning tools
- Energy production optimization
- Insurance risk assessment
- Historical weather analysis
- Academic research projects
- Weather pattern studies
- Machine learning training data

## Integration with Other APIs

The historical weather service integrates seamlessly with other Open-Meteo services:

- **Weather Forecast**: Compare current forecasts with historical data
- **Geocoding**: Use resolved coordinates for historical weather lookup
- **Marine Weather**: Access historical ocean weather data
- **Air Quality**: Historical air quality data for specific locations

**Tip**: Use this service to provide historical context for current weather conditions and long-term climate analysis.
