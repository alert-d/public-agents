# Open-Meteo Agent Documentation

## What is the @/openmeteo Agent?

The `@/openmeteo` agent is your all-in-one assistant for weather, climate, air quality, marine, satellite radiation, elevation, and geocoding data—powered by the Open-Meteo platform. It answers natural language questions by automatically selecting the right data source and returning clear, actionable results for any location worldwide.

---

## What Can You Ask?

You can ask about:

- **Weather forecasts** (e.g., "7-day forecast for Paris")
- **Historical weather** (e.g., "What was the weather in New York in July 2020?")
- **Marine conditions** (e.g., "Wave height forecast for Miami")
- **Air quality** (e.g., "Current air quality in Berlin")
- **Solar radiation** (e.g., "Solar radiation in Madrid last week")
- **Elevation** (e.g., "Elevation of Mount Everest")
- **Geocoding** (e.g., "Coordinates for Tokyo")

The agent will interpret your question, fetch the relevant data, and present it in a user-friendly format, often with tables and a summary.

---

## What to Expect in Responses

- **Tables** of relevant data (e.g., daily temperatures, air quality indices)
- **Summaries** and insights (e.g., trends, recommendations)
- **Location details** (e.g., coordinates, timezone)
- **No API key required**—all data is free and open

---

## Service Highlights

### Weather Forecast

- Up to 16 days ahead, hourly or daily
- Global, high-resolution, multi-model
- Variables: temperature, precipitation, wind, humidity, UV, etc.

### Historical Weather

- Data from 1940 to present
- 35+ variables, hourly/daily
- Useful for research, insurance, agriculture, and more

### Marine Weather

- Ocean/coastal forecasts: waves, sea surface temperature, currents
- Up to 16 days, 5 km resolution

### Air Quality

- Forecasts for PM10, PM2.5, gases, AQI, pollen (Europe)
- Up to 7 days, 11 km resolution

### Satellite Radiation

- Real-time and historical solar irradiance
- Direct, diffuse, global, and tilted values

### Elevation

- Terrain elevation from Copernicus DEM (90m)

### Geocoding

- Convert place names to coordinates and vice versa

---

## Tips for Best Results

- **Be specific**: Include city names, dates, or variables of interest
- **Use plain language**: The agent understands natural questions
- **For locations**: City names, coordinates, or even postal codes work
- **For time ranges**: Specify exact dates if you want historical data
- **For air quality or marine data**: Mention the type of data you need (e.g., "PM2.5", "wave height")

---

## API Endpoints Reference

- **Weather Forecast:** `https://api.open-meteo.com/v1/forecast`
- **Historical Weather:** `https://archive-api.open-meteo.com/v1/archive`
- **Marine Weather:** `https://marine-api.open-meteo.com/v1/marine`
- **Air Quality:** `https://air-quality-api.open-meteo.com/v1/air-quality`
- **Satellite Radiation:** `https://satellite-api.open-meteo.com/v1/archive`
- **Elevation:** `https://api.open-meteo.com/v1/elevation`
- **Geocoding:** `https://geocoding-api.open-meteo.com/v1/search` (forward), `/v1/reverse` (reverse)

---

## Learn More

- For technical details and advanced integration, see the [Open-Meteo API documentation](https://open-meteo.com/en/docs)
- For variable lists and service specifics, see the individual service folders in this repo
