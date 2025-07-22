# Open-Meteo Flood API Plans

This directory contains execution plans for querying flood data using the Open-Meteo Flood API. The Flood API provides river discharge data from the Global Flood Awareness System (GloFAS) with 5 km resolution.

## Available Plans

### CityToFlood.json

**Purpose**: Get flood data for a city by first geocoding the city name to coordinates.

**Flow**:

1. Geocode city name to coordinates
2. Query flood API with coordinates
3. Extract location and flood data
4. Provide LLM analysis

**Use Case**: When you have a city name and want flood risk assessment.

**Example Question**: "What's the flood risk for Oslo, Norway?"

### SingleFloodQuery.json

**Purpose**: Query flood data for a single coordinate pair.

**Flow**:

1. Query flood API with coordinates
2. Provide LLM analysis

**Use Case**: When you have specific coordinates and want flood data.

**Example Question**: "What's the flood risk at coordinates 59.91, 10.75?"

## API Details

- **Base URL**: `https://flood-api.open-meteo.com/v1/flood`
- **Data Source**: Global Flood Awareness System (GloFAS)
- **Resolution**: 5 km
- **Coverage**: Global
- **Forecast**: Up to 7 months
- **Historical**: From 1984

## Key Parameters

- `latitude`, `longitude`: Required coordinates
- `daily`: River discharge variables (river_discharge, river_discharge_mean, etc.)
- `forecast_days`: Number of forecast days (0-210, default 92)
- `past_days`: Number of past days to include
- `start_date`, `end_date`: Specific date range

## Data Structure

The API returns:

```json
{
    "latitude": 59.9,
    "longitude": 10.75,
    "timezone": "GMT",
    "daily_units": {
        "river_discharge": "m³/s"
    },
    "daily": {
        "time": ["2025-03-03", "2025-03-04", ...],
        "river_discharge": [8.04, 8.75, ...]
    }
}
```

## Notes

- Due to 5 km resolution, the closest river might not be selected correctly
- Varying coordinates by 0.1° can help get more representative discharge rates
- GloFAS website provides additional maps for river coverage understanding
