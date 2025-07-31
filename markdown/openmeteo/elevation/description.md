# Open-Meteo Elevation API

## Overview

The Open-Meteo Elevation API provides terrain elevation data based on the Copernicus DEM 2021 release GLO-90 with 90 meters resolution. This API accepts geographical coordinates and returns the terrain elevation for those points.

## API Endpoint

- **Base URL**: `https://api.open-meteo.com/v1/elevation`
- **Method**: GET
- **Data Source**: Copernicus DEM 2021 GLO-90 (90-meter resolution)
- **License**: Free worldwide license

## Parameters

### Required Parameters

- **latitude**: Floating point array - Geographical WGS84 coordinates of the location
- **longitude**: Floating point array - Geographical WGS84 coordinates of the location

### Optional Parameters

- **apikey**: String - Only required for commercial use to access reserved API resources

### Parameter Details

- Multiple coordinates can be comma-separated
- Up to 100 coordinates can be requested at once
- Latitude must be in range of -90 to 90°
- Longitude must be in range of -180 to 180°

## Response Format

### Success Response

```json
{
    "elevation": [38.0]
}
```

The elevation array always contains values, even if only one coordinate is requested.

### Error Response

```json
{
    "error": true,
    "reason": "Latitude must be in range of -90 to 90°. Given: 522.52."
}
```

## Usage Examples

### Single Coordinate Request

```
GET https://api.open-meteo.com/v1/elevation?latitude=52.52&longitude=13.41
```

### Multiple Coordinates Request

```
GET https://api.open-meteo.com/v1/elevation?latitude=52.52,48.85&longitude=13.41,2.35
```

## Data Quality

- **Resolution**: 90 meters
- **Coverage**: Worldwide
- **Accuracy**: Based on Copernicus DEM 2021 GLO-90 dataset
- **Update Frequency**: Static dataset (no real-time updates)

## Rate Limits

- **Non-Commercial**: Less than 10,000 daily API calls
- **Commercial**: Requires API key for reserved resources

## Attribution Requirements

All users must provide:

1. Clear attribution to the Copernicus program
2. Reference to Open-Meteo

### Citation

For research publications using Copernicus DEM data:

```
https://doi.org/10.5270/ESA-c5d3d65
```

## Use Cases

- Terrain analysis
- Weather forecasting improvements
- Geographic applications
- Environmental modeling
- Hiking and outdoor applications
- Aviation and navigation

## Integration Notes

- API is stable with no planned changes to required parameters
- Additional optional parameters may be added in the future
- Error responses use HTTP 400 status code
- All coordinates must be valid WGS84 format

## Technical Specifications

- **Coordinate System**: WGS84
- **Elevation Units**: Meters
- **Data Format**: JSON
- **Character Encoding**: UTF-8
- **CORS**: Supported for web applications
