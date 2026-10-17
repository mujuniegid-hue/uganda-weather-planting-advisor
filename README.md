# Uganda Weather and Planting Advisor

A free, mobile-friendly web app that helps smallholder farmers and agricultural extension workers in Uganda use local weather forecasts to decide **when to plant, irrigate, spray crops and harvest**.

**Live demo:** https://mujuniegid-hue.github.io/uganda-weather-planting-advisor/

## The problem

Farmers in Uganda need accessible, location-specific weather information to time farm work. A badly timed spray can be washed off by rain, and seeds planted before heavy rain can be washed away.

## Who it is for

- Smallholder farmers
- Agricultural extension workers and NGO field staff

## What it does

1. The farmer **selects a district**, or **searches for a town, sub-county, parish or village**.
2. They choose a **crop** and a **farming activity** (planting, irrigating, spraying or harvesting).
3. The app fetches live forecast data and shows:
   - A 7-day, location-specific forecast (rain chance, rainfall, temperature, wind, gusts, water loss)
   - Current conditions
   - **Rain alerts** (heavy rain, likely rain, mostly dry week)
   - **Practical advice** for the chosen activity, rated GOOD, CAUTION or AVOID for each day
   - A plain-language explanation of **forecast uncertainty**, plus a confidence label per day

## Data sources

| Source | Used for |
|---|---|
| [Open-Meteo Forecast API](https://open-meteo.com/) | Weather forecast data (no API key needed) |
| [Open-Meteo Geocoding API](https://open-meteo.com/en/docs/geocoding-api) | Turning place names into coordinates |
| [OpenStreetMap Nominatim](https://nominatim.org/) | A second place search that knows many small villages |

Weather data by Open-Meteo.com. Place data by OpenStreetMap contributors.

## How the advice works

The app applies simple rules to each day's forecast. These thresholds are **teaching defaults, not official agronomy values**.

| Activity | GOOD | AVOID |
|---|---|---|
| Planting | 2 to 20 mm rain (moist soil) | 20 mm or more (seeds washed away, waterlogging) |
| Irrigating | Dry day and water loss of 4 mm or more | 10 mm or more of rain |
| Spraying | Low rain chance, light wind | 2 mm or more rain, 60% or more rain chance, or gusts of 30 km/h or more |
| Harvesting | Dry day, low rain chance | 5 mm or more rain, or 60% or more rain chance |

Everything in between is CAUTION. The rules are not crop-specific.

## Limitations (please read)

- **Forecasts can be wrong**, especially for days 5 to 7. The app says so, and shows a confidence label.
- The weather model covers squares several kilometres wide. Hills, lakes and mountains can make a farm differ from the forecast.
- The advice thresholds have **not been reviewed by an agronomist**. Real farmers should treat the advice as a guide and talk to an extension officer.
- Some villages may be missing from the map databases, or labelled with an older district name (Uganda has created many new districts).
- The district list was compiled without an official data file, so a newly created district may be missing. Use the place search for anything not listed.
- The crop list covers common crops and has an "Other" option. It is not every crop grown in Uganda.
- The map services are free public services meant for light use. A large deployment needs a paid or self-hosted service.

## How to run it

No installation or API key is needed.

1. Download or clone this repository.
2. Open `index.html` in a web browser (Chrome, Edge, Firefox, Safari).
3. You need an internet connection to get forecasts.

```
git clone https://github.com/mujuniegid-hue.github.io/uganda-weather-planting-advisor.git
```

## How it was built

- HTML, CSS and plain JavaScript (no frameworks, no libraries, no secrets)
- Responsive layout that works on phones and desktops
- Error handling: offline detection, 10-second timeout, plain-language messages, missing-data protection
- Accessibility: text labels as well as colours, large tap targets, screen-reader announcements

## Test checklist

- [ ] District selection gives a forecast
- [ ] Place search gives labelled matches, and a forecast
- [ ] Crop and activity choices appear in the results
- [ ] Rain alerts show for rainy weeks
- [ ] Advice changes for each of the four activities
- [ ] Uncertainty box and confidence labels show
- [ ] Phone layout has no sideways scrolling
- [ ] Offline shows a friendly message

## Project structure

```
index.html   The whole app (HTML, CSS and JavaScript in one file)
README.md    This file
```

## Possible future improvements

- Crop-specific rules reviewed by agronomists
- Local-language support (for example Luganda, Runyankole, Luo, Ateso)
- SMS or WhatsApp alerts for farmers without smartphones
- Offline saving of the last forecast
- A verified official list of districts, sub-counties and villages

## Author

Built by Egidio.K.Ham