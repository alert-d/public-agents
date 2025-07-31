# Open-Meteo Geocoding Service

The Open-Meteo Geocoding service resolves human-readable place names (or postal codes) into structured location data with geographical coordinates. It supports fuzzy matching, localization, and country filtering, making it perfect for initializing weather queries and location-based applications.

## Core Capabilities

### **Forward Geocoding**

- **Place Name Resolution**: Convert city names, addresses, and landmarks to precise coordinates
- **Fuzzy Matching**: Find locations even with partial or misspelled names (minimum 3 characters)
- **Multi-language Support**: Works with place names in various languages
- **Country Filtering**: Limit results to specific countries or regions
- **Result Ranking**: Returns best matches with confidence scores

### **Reverse Geocoding**

- **Coordinate Resolution**: Convert latitude/longitude to nearest place names
- **Administrative Details**: Provide country, state, city, and district information
- **Localized Names**: Return place names in the user's preferred language
- **Multiple Formats**: Support for various output formats (JSON, protobuf)

## API Endpoints

### **Forward Geocoding (Search)**

- **URL**: `https://geocoding-api.open-meteo.com/v1/search`
- **Method**: `GET`
- **Purpose**: Convert place names to coordinates

### **Reverse Geocoding**

- **URL**: `https://geocoding-api.open-meteo.com/v1/reverse`
- **Method**: `GET`
- **Purpose**: Convert coordinates to place names

## Query Parameters

### **Forward Geocoding Parameters**

- **name** (String, Required): Search string (e.g. "Paris", "90210"). Minimum 3 characters for fuzzy matching.
- **count** (Integer, Optional, Default: 10): Max number of results to return (up to 100).
- **format** (String, Optional, Default: json): Output format: json or protobuf.
- **language** (String, Optional, Default: en): Two-letter language code for localization (e.g. fr, de, ja).
- **countryCode** (String, Optional): Filter by ISO 3166-1 alpha-2 country code (e.g. US, JP).
- **apikey** (String, Optional): Only required for commercial access.

## Example Requests

### **Basic City Search**

```http
GET https://geocoding-api.open-meteo.com/v1/search?name=tokyo&count=3
```

### **Localized Search with Country Filter**

```http
GET https://geocoding-api.open-meteo.com/v1/search?name=tokyo&count=3&language=ja&countryCode=JP
```

### **Postal Code Search**

```http
GET https://geocoding-api.open-meteo.com/v1/search?name=90210&count=1
```

## Example Response

```json
{
    "results": [
        {
            "id": 1850147,
            "name": "Tokyo",
            "latitude": 35.6895,
            "longitude": 139.6917,
            "country_code": "JP",
            "timezone": "Asia/Tokyo",
            "population": 8336599,
            "admin1": "Tokyo"
        },
        {
            "id": 1850144,
            "name": "Tokyo Prefecture",
            "latitude": 35.6895,
            "longitude": 139.6917,
            "country_code": "JP",
            "timezone": "Asia/Tokyo"
        }
    ]
}
```

## Use Cases

### **Weather Applications**

- **Location Input**: Allow users to search for weather by city name
- **Coordinate Validation**: Ensure weather queries use valid coordinates
- **Place Identification**: Identify locations from GPS coordinates
- **Address Resolution**: Convert street addresses to weather coordinates

### **Data Integration**

- **Location Services**: Support for mapping and navigation applications
- **Travel Planning**: Convert destination names to coordinates for weather lookup
- **Emergency Services**: Quickly identify locations for weather alerts
- **Research Applications**: Geocode locations for climate and weather studies

## Technical Features

### **Global Coverage**

- **Worldwide Database**: Comprehensive coverage of cities, towns, and landmarks
- **Regular Updates**: Database updated with new locations and name changes
- **High Accuracy**: Precise coordinate resolution for most locations

### **Performance**

- **Fast Response**: Sub-second response times for most queries
- **Caching Support**: Efficient caching for frequently requested locations
- **Rate Limiting**: Generous limits suitable for most applications

### **Data Quality**

- **Standardized Names**: Consistent naming conventions across languages
- **Hierarchical Data**: Administrative divisions (country, state, city)
- **Alternative Names**: Support for multiple names for the same location

## Integration Benefits

- **Seamless Weather Lookup**: Direct integration with Open-Meteo weather APIs
- **No API Keys**: Free access without authentication requirements
- **CORS Support**: Cross-origin requests enabled for web applications
- **Reliable Service**: High availability with redundant infrastructure
- **Documentation**: Complete API reference and examples

## Common Applications

- Weather apps and websites
- Travel planning tools
- Emergency notification systems
- Climate research platforms
- Location-based services
- Mapping and navigation applications

## Integration with Weather APIs

The geocoding service is designed to work seamlessly with other Open-Meteo APIs:

- **Weather Forecast**: Use coordinates to get weather data
- **Historical Data**: Retrieve past weather for specific locations
- **Marine Weather**: Get ocean weather for coastal locations
- **Air Quality**: Check air quality for resolved locations

**Tip**: Use this output to dynamically feed coordinates into `/forecast`, `/marine`, `/archive`, etc.
