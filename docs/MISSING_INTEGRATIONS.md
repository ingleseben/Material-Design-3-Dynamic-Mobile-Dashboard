# Missing Integrations Guide

This guide covers optional integrations that are referenced in the dashboard but not currently active. Each section explains what the integration does, how to set it up, and how to enable the corresponding dashboard features.

---

## Overview

The dashboard was adapted from a comprehensive template with many features. Some features are commented out because the required integrations or hardware are not yet available. This guide helps you enable them when ready.

| Integration | Dashboard Feature | Priority | Status |
|-------------|-------------------|----------|--------|
| Weather (BOM/OpenWeather) | Weather panel, forecasts | Medium | Alternative available |
| Philips Hue / Scene Presets | Dynamic lighting scenes | Medium | Commented (🔜) |
| Security Cameras | Camera view, notification feeds | Low | Commented (⚠️) |
| Alarmo | Alarm panel, armed/disarmed status | Low | Commented (⚠️) |
| Robot Vacuum (map) | Vacuum map card | Low | Basic control active |
| Media Players (advanced) | Spotify, multi-room audio | Low | Basic control active |
| Climate / HVAC | Thermostat controls, climate tab | Low | Commented (⚠️) |
| Covers / Blinds | Curtain and blind controls | Low | Commented (⚠️) |
| Irrigation | Zone control, soil moisture | Low | Commented (⚠️) |

---

## Weather Alternatives

The dashboard includes a comprehensive weather panel with forecasts, wind, UV, rainfall, and radar.

### Option 1: Bureau of Meteorology (Australia)

If you are in Australia, the BOM integration provides the most accurate local data.

1. Install via HACS > Integrations:
   - Search for "Bureau of Meteorology"
   - Or add custom repository: `https://github.com/bremor/bureau_of_meteorology`

2. Configure with your location

3. Entities created:
   ```yaml
   weather.your_location          # Main weather entity
   sensor.your_location_temp      # Current temperature
   sensor.your_location_humidity  # Current humidity
   ```

### Option 2: OpenWeatherMap

Available worldwide with a free API tier.

1. Get a free API key from [openweathermap.org](https://openweathermap.org/api)

2. Add via **Settings > Devices & Services > Add Integration**:
   - Search for "OpenWeatherMap"
   - Enter your API key

3. Entities created:
   ```yaml
   weather.openweathermap         # Main weather entity
   sensor.openweathermap_temperature
   sensor.openweathermap_humidity
   sensor.openweathermap_wind_speed
   sensor.openweathermap_uv_index
   ```

### Option 3: Met.no (Default HA Weather)

Pre-installed with Home Assistant, uses Norwegian Meteorological Institute data (works globally).

1. Usually auto-configured based on your HA location settings
2. Entity: `weather.home`

### Enabling Weather in the Dashboard

After setting up a weather integration:

1. Open `config/dashboards/mobile-dashboard.yaml`
2. Search for `# ⚠️ WEATHER` or weather-related commented sections
3. Uncomment the weather card sections
4. Update entity IDs to match your integration:
   ```yaml
   # Replace template references:
   entity: weather.your_location
   ```

### Weather Template Sensors

The `template sensor/` directory contains weather-related template sensors:

- **Weather Condition Icon Sensor** - Maps conditions to Material icons
- **Weather Forecast Components** - Extracts forecast data for cards
- **Get Forecast Template Sensor** - Processes forecast attributes
- **Timestamp Sensor** - Time-based formatting for weather display

Add these to your configuration to enable the full weather panel:

```yaml
# In configuration.yaml or a package file
template: !include_dir_list template_sensors/
```

---

## Philips Hue Scenes

The dashboard supports Philips Hue dynamic scene effects using the Scene Presets custom component, which works without the Hue bridge.

### Prerequisites

- Zigbee-compatible Philips Hue bulbs
- Zigbee2MQTT or ZHA integration
- Bulbs paired directly (not through Hue bridge)

### Setup

1. **Install Scene Presets:**
   - HACS > Integrations > Custom Repositories
   - Add: `https://github.com/Hypfer/hass-scene_presets`
   - Install and restart HA

2. **Copy Hue asset files** from the `hue asset/` directory:

   | File | Purpose | HA Location |
   |------|---------|-------------|
   | `Apply Selected Dynamic Scene to Room Automation.yaml` | Automation trigger | `/config/automations.yaml` |
   | `Apply Selected Dynamic Scene to Room Script.yaml` | Scene application script | `/config/scripts.yaml` |
   | `Toggle or Apply Dynamic Scene to Room Script.yaml` | Toggle script | `/config/scripts.yaml` |
   | `Input Boolean for Room Selector.yaml` | Room selection helpers | `/config/configuration.yaml` |
   | `Input Number Components for Room Selector.yaml` | Brightness/speed controls | `/config/configuration.yaml` |
   | `Input Text for Room Selector.yaml` | Scene name storage | `/config/configuration.yaml` |

3. **Copy scene images:**
   - Copy `hue asset/scene images/` to `/config/www/scene_images/`
   - Or get official images from the [Scene Presets repo](https://github.com/Hypfer/hass-scene_presets/blob/master/custom_components/scene_presets/assets/Readme.md)

4. **Enable the Scenes view:**
   - Open `config/dashboards/mobile-dashboard.yaml`
   - Search for `# 🔜 SCENES VIEW`
   - Uncomment the entire scenes view section
   - Update room names to match your setup

---

## Security Cameras

The dashboard includes a dedicated Camera view with live feeds and motion detection overlays.

### Setup

1. **Add camera integration** for your camera brand:
   - Reolink, Unifi Protect, Amcrest, Generic RTSP, etc.
   - Via Settings > Devices & Services > Add Integration

2. **Install WebRTC Camera** (for low-latency streams):
   - HACS > Frontend > WebRTC Camera
   - HACS > Integrations > WebRTC (the backend component)
   - Configure go2rtc for your camera streams

3. **Entity naming convention:**
   ```yaml
   camera.front_door
   camera.backyard
   camera.garage
   camera.driveway
   ```

4. **Enable the Camera view:**
   - Search for `# ⚠️ CAMERA VIEW` in the dashboard YAML
   - Uncomment the camera view section
   - Update entity IDs to match your cameras
   - Add camera cards with WebRTC for live streaming

---

## Alarmo Security System

The dashboard has an alarm panel accessible from the Overview page header.

### Setup

1. **Install Alarmo:**
   - HACS > Integrations > Search "Alarmo"
   - Install and restart HA

2. **Configure Alarmo:**
   - Settings > Devices & Services > Alarmo
   - Set up zones, sensors, and codes
   - Configure arm modes (home, away, night)

3. **Install Alarmo Card:**
   - HACS > Frontend > Alarmo Card
   - Already listed in HACS dependencies

4. **Enable in dashboard:**
   - Search for `# ⚠️ ALARMO` in the dashboard YAML
   - Uncomment the alarmo popup card
   - Uncomment the alarm icon in the Overview header
   - Entity: `alarm_control_panel.alarmo`

---

## Robot Vacuum (Advanced)

Basic vacuum controls are already active in the Living Room view. For advanced features:

### Vacuum Map Card

1. **Install Vacuum Card** (if not already):
   - HACS > Frontend > Search for your vacuum brand's card
   - Popular options: Xiaomi Vacuum Map Card, Valetudo Map Card

2. **Configure map:**
   - Your vacuum integration should provide a `camera.vacuum_map` entity
   - Or use the Valetudo integration for custom firmware vacuums

3. **Add to dashboard:**
   - Add a map card to the Living Room view
   - Reference your vacuum map entity

---

## Media Players (Advanced)

Basic media player controls are active. For enhanced media features:

### Spotify Integration

1. **Add Spotify integration:**
   - Settings > Devices & Services > Add Integration > Spotify
   - Authorize with your Spotify account

2. **Dashboard features:**
   - Now Playing card will show Spotify playback
   - The notification panel includes a Spotify app link

### Multi-Room Audio

1. **Group media players:**
   ```yaml
   # In configuration.yaml
   media_player:
     - platform: group
       entities:
         - media_player.bedroom_roku
         - media_player.living_room_tv
       name: "All Speakers"
   ```

2. **The Mediocre Media Player Cards** already support multi-room display

---

## Climate / HVAC Control

The dashboard includes climate controls in each room's Climate tab.

### Setup

1. **Add your climate integration:**
   - Smart thermostat (Nest, Ecobee, etc.)
   - Heat pump controller
   - Smart AC controller (Sensibo, Midea, etc.)

2. **Entity naming convention:**
   ```yaml
   climate.bedroom
   climate.kitchen
   climate.living_room
   climate.desk
   ```

3. **Enable climate cards:**
   - Search for `# ⚠️ CLIMATE` in the dashboard YAML
   - Uncomment climate control sections in each room view
   - Update entity IDs to match your devices

---

## Covers / Smart Blinds

The dashboard supports curtain and blind controls in room views.

### Setup

1. **Add cover integration** for your devices:
   - Zigbee blinds via Zigbee2MQTT/ZHA
   - Wi-Fi blinds (SwitchBot, SOMA, etc.)

2. **Entity naming convention:**
   ```yaml
   cover.bedroom_curtain
   cover.living_room_curtain
   cover.desk_blind
   ```

3. **Enable cover cards:**
   - Search for `# ⚠️ COVER` in the dashboard YAML
   - Uncomment cover control sections
   - Update entity IDs

---

## Irrigation System

The dashboard includes a full irrigation view with zone controls and soil moisture monitoring.

### Setup

1. **Add irrigation integration:**
   - Smart irrigation controller (RainMachine, Rachio, OpenSprinkler, etc.)
   - Or use smart valves with Zigbee/Z-Wave

2. **Entity naming convention:**
   ```yaml
   switch.irrigation_zone_1    # or valve entities
   switch.irrigation_zone_2
   sensor.zone_1_soil_moisture
   sensor.zone_1_soil_temperature
   ```

3. **Enable irrigation view:**
   - Search for `# ⚠️ IRRIGATION VIEW` in the dashboard YAML
   - Uncomment the entire irrigation view
   - Update entity IDs to match your zones
   - Configure ApexCharts cards for soil data visualization

---

## Gradual Enablement Strategy

You do not need to set up everything at once. Here is a recommended order:

### Phase 1: Immediate (Current)
Already working:
- 6 lights with group controls
- 3 media players
- 1 vacuum
- Navigation and theming

### Phase 2: Sensors (When Hardware Arrives)
Enable these first for maximum impact:
1. Temperature and humidity sensors (visible on room cards)
2. Motion sensors (automatic light triggers)
3. Door/window sensors (security awareness)
4. Smart plugs (energy monitoring)

### Phase 3: Weather
Medium effort, high visibility:
1. Choose and configure a weather integration
2. Add weather template sensors
3. Enable weather panel cards
4. Enable the weather forecast buttons on Overview

### Phase 4: Scenes and Lighting
If using Philips Hue or compatible bulbs:
1. Set up Scene Presets
2. Copy Hue asset configurations
3. Enable the Scenes view
4. Test scene activation per room

### Phase 5: Security and Automation
When ready for advanced features:
1. Alarmo for security (requires door/window sensors from Phase 2)
2. Cameras for surveillance
3. Climate control for HVAC
4. Covers for blinds/curtains

### Phase 6: Outdoor and Extras
Long-term additions:
1. Irrigation system
2. Garage controls
3. Additional rooms
4. Energy monitoring dashboard

---

## Finding Commented Sections

Use these search patterns in the dashboard YAML to find features to enable:

| Search Term | Meaning |
|-------------|---------|
| `# 🔜` | High priority - enable when hardware/sensors arrive |
| `# ⚠️` | Low priority - optional feature, enable when ready |
| `# COMMENTED:` | Section description explaining what is disabled |
| `# TO ENABLE:` | Instructions for re-enabling the section |

### Bulk Enablement

To enable all sensor-ready features at once:

1. Open the dashboard YAML in a text editor
2. Search for `# 🔜`
3. Read the instruction comment for context
4. Remove the comment markers from the YAML block
5. Update entity IDs if different from the defaults
6. Validate YAML: `ha core check`
7. Refresh the dashboard in your browser
