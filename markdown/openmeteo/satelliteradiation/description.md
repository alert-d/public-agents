# Open-Meteo Satellite Radiation API

The Open-Meteo Satellite Radiation API provides real-time solar irradiance data from multiple geostationary satellites worldwide. This service delivers comprehensive solar radiation measurements including direct, diffuse, and global tilted irradiance at high resolution for solar energy applications, research, and environmental monitoring.

## Core Capabilities

### **Satellite Radiation Monitoring**

- **Real-time Data**: Live solar radiation data from geostationary satellites
- **Global Coverage**: Worldwide coverage with multiple satellite sources
- **High Resolution**: 5 km spatial resolution for detailed solar mapping
- **Multiple Time Steps**: 10, 15, or 30-minute temporal resolution
- **Instantaneous Values**: Both averaged and instantaneous radiation data

### **Data Granularity**

- **Hourly Data**: Backward-averaged solar radiation over preceding hour
- **Instantaneous Data**: Real-time radiation values at specific times
- **Daily Summaries**: Daily solar radiation statistics and sun position data
- **Historical Data**: Access to archived satellite radiation data

### **Selective Data Extraction**

- **Efficient Queries**: Extract only the radiation variables you need
- **Reduced Payload**: Smaller responses for faster processing
- **Focused Analysis**: LLM gets targeted data instead of overwhelming JSON
- **Flexible Selection**: Choose single fields or multiple variables

**Examples:**

- Get just global radiation: `"select": ["current.shortwave_radiation", "hourly.shortwave_radiation"]`
- Get solar components: `"select": ["daily.direct_radiation", "daily.diffuse_radiation"]`
- Get current conditions: `"select": ["current.shortwave_radiation", "current.direct_normal_irradiance"]`

## Available Radiation Variables

### **Global Solar Radiation**

- `shortwave_radiation`: Global horizontal irradiation (GHI)
- `shortwave_radiation_instant`: Instantaneous global horizontal irradiation

### **Direct Solar Radiation**

- `direct_radiation`: Direct solar radiation on horizontal plane
- `direct_radiation_instant`: Instantaneous direct radiation
- `direct_normal_irradiance`: Direct normal irradiance (DNI)
- `direct_normal_irradiance_instant`: Instantaneous DNI

### **Diffuse Solar Radiation**

- `diffuse_radiation`: Diffuse horizontal irradiance (DHI)
- `diffuse_radiation_instant`: Instantaneous diffuse radiation

### **Tilted Surface Radiation**

- `global_tilted_irradiance`: Global tilted irradiance (GTI)
- `global_tilted_irradiance_instant`: Instantaneous GTI

### **Terrestrial Radiation**

- `terrestrial_radiation`: Solar radiation at top of atmosphere
- `terrestrial_radiation_instant`: Instantaneous terrestrial radiation

### **Daily Solar Variables**

- `sunrise`: Daily sunrise time
- `sunset`: Daily sunset time
- `daylight_duration`: Duration of daylight
- `sunshine_duration`: Duration of sunshine
- `shortwave_radiation_sum`: Daily sum of shortwave radiation

## Use Cases

### **Solar Energy**

- Solar panel performance monitoring
- Solar power plant optimization
- Renewable energy forecasting
- Solar resource assessment
- PV system design and planning

### **Agriculture**

- Crop growth monitoring
- Evapotranspiration calculations
- Agricultural planning
- Greenhouse management
- Irrigation scheduling

### **Research and Analysis**

- Climate studies and research
- Solar radiation modeling
- Environmental monitoring
- Academic research projects
- Satellite data validation

### **Building and Architecture**

- Building energy modeling
- Passive solar design
- Daylighting analysis
- HVAC system optimization
- Green building certification

## Technical Features

### **Multi-Satellite Support**

- **EUMETSAT LSA SAF MSG**: Europe, Africa, South America (5 km resolution)
- **EUMETSAT CM SAF SARAH3**: Europe, Africa, South America (5 km resolution)
- **JMA JAXA Himawari-9**: Asia, Australia, New Zealand (5 km resolution)
- **IODC**: Europe, Africa, India (5 km resolution)

### **Geographic Coverage**

- **Europe**: High-resolution coverage with multiple satellites
- **Africa**: Comprehensive coverage for solar resource assessment
- **Asia-Pacific**: Detailed coverage including Australia and New Zealand
- **South America**: Land-based coverage for solar monitoring
- **Global**: Worldwide coverage with varying resolution

### **Data Quality**

- **Update Frequency**: Every 10-60 minutes depending on satellite
- **Temporal Resolution**: 10, 15, or 30-minute native resolution
- **Spatial Resolution**: 5 km resolution for detailed mapping
- **Data Delay**: 2 hours to 2 days depending on data source

## Solar Radiation Components

### **Global Horizontal Irradiance (GHI)**

- **Definition**: Total solar radiation on horizontal surface
- **Components**: Direct + Diffuse radiation
- **Units**: W/m²
- **Applications**: General solar resource assessment

### **Direct Normal Irradiance (DNI)**

- **Definition**: Direct solar radiation perpendicular to sun
- **Units**: W/m²
- **Applications**: Concentrated solar power, tracking systems

### **Diffuse Horizontal Irradiance (DHI)**

- **Definition**: Scattered solar radiation on horizontal surface
- **Units**: W/m²
- **Applications**: Building design, agriculture

### **Global Tilted Irradiance (GTI)**

- **Definition**: Total radiation on tilted surface
- **Requirements**: Tilt and azimuth parameters
- **Units**: W/m²
- **Applications**: Fixed solar panel systems

## Global Coverage

The service provides satellite radiation data for:

- **All continents** with varying coverage quality
- **Major solar regions** with high-resolution data
- **Remote locations** with satellite accessibility
- **Ocean areas** with limited coverage
- **Polar regions** with seasonal limitations

## Integration

### **API Endpoints**

- **Satellite Radiation**: `/v1/archive` - Main satellite radiation service
- **Geocoding**: `/v1/search` - Location coordinate lookup
- **Elevation**: `/v1/elevation` - Terrain data

### **Data Formats**

- **JSON**: Structured radiation data
- **CSV**: Tabular data export
- **GeoJSON**: Geospatial radiation data
- **Time Series**: Temporal data analysis

### **Forecast Durations**

- **Current**: Real-time radiation conditions
- **Hourly**: Up to 24 hours
- **Daily**: Daily solar summaries
- **Historical**: Up to 92 days in the past

## Important Notes

### **Regional Limitations**

- **North America**: NASA GOES satellites not yet integrated
- **Ocean Coverage**: Limited coverage over open oceans
- **Polar Regions**: Seasonal limitations due to low sun angles
- **Data Gaps**: Occasional gaps due to satellite maintenance

### **Data Considerations**

- **Time Averaging**: Backward-averaged values for energy calculations
- **Instantaneous Values**: Available for real-time monitoring
- **Tilt Parameters**: Required for global tilted irradiance
- **Satellite Scan Time**: Corrections applied for scan time differences

### **Solar Energy Applications**

- **PV Performance**: Use GHI for fixed horizontal systems
- **Tracking Systems**: Use DNI for optimal performance
- **Building Integration**: Use GTI with appropriate tilt/azimuth
- **Energy Modeling**: Use backward-averaged values

This service enables users to access professional-grade satellite radiation data for any location worldwide, supporting solar energy applications, research, and environmental monitoring with high-resolution, real-time data from multiple satellite sources.
