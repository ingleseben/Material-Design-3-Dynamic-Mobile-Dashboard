# Deployment Guide

## Material Design 3 Dynamic Mobile Dashboard

Complete step-by-step deployment guide for the Home Assistant MD3 Dashboard.

---

## Prerequisites

Before starting deployment, ensure you have:

- **Home Assistant** 2024.1 or newer installed and running
- **HACS** (Home Assistant Community Store) installed — [installation guide](https://hacs.xyz/docs/use/)
- **File editor** access (VSCode Server addon, File Editor addon, or SSH)
- **Admin access** to your Home Assistant instance
- A working network connection for HACS downloads

### Hardware Currently Configured

| Device Type | Count | Details |
|-------------|-------|---------|
| WiZ Lights | 6 | Bedroom, Kitchen (x2), Living Room (x2), Desk |
| Media Players | 3 | Bedroom Roku, Bedroom TV, Living Room TV |
| Vacuum | 1 | Roborock |

### Hardware Arriving (Sensor-Ready)

| Device Type | Count | Details |
|-------------|-------|---------|
| Binary Sensors | 12 | Motion, presence, door/window contacts |
| Climate Sensors | 4 | Temperature and humidity (2 rooms) |
| Smart Plugs | 4 | One per room |
| Smart Bulbs | 8 | Two per room |

---

## Part 1: Initial Setup

### Step 1.1: Create secrets.yaml

If you do not already have a `secrets.yaml` file, create one in your Home Assistant config directory:

```yaml
# /config/secrets.yaml
# Store sensitive values here - this file is excluded from git

# Example entries (uncomment and fill in as needed):
# ha_url: "http://your-ha-ip:8123"
# latitude: "your_latitude"
# longitude: "your_longitude"
```

This file is listed in `.gitignore` and will never be committed to version control.

### Step 1.2: Install HACS

If HACS is not already installed:

1. Open a terminal/SSH session to your Home Assistant machine
2. Run the HACS installation script:
   ```bash
   wget -O - https://get.hacs.xyz | bash -
   ```
3. Restart Home Assistant
4. Go to **Settings > Devices & Services > Add Integration**
5. Search for "HACS" and follow the setup wizard
6. Authorize with your GitHub account when prompted

### Step 1.3: Copy Configuration Files

Copy the configuration file to your Home Assistant config directory:

```bash
# Copy the helper entities configuration
cp config/configuration.yaml /config/packages/dashboard_helpers.yaml
```

Or manually add the contents of `config/configuration.yaml` to your existing configuration:

- **Light Groups**: `group.kitchen_lights` and `group.living_room_lights`
- **Template Sensors**: Light count sensors for each room

If using the packages approach, ensure your `configuration.yaml` includes:

```yaml
homeassistant:
  packages: !include_dir_named packages/
```

---

## Part 2: Custom Component Installation

### Step 2.1: Install Scene Presets (Custom Component)

This is the only custom component (not a frontend card) required:

1. In HACS, go to **Integrations** (not Frontend)
2. Click the three dots menu > **Custom repositories**
3. Add: `https://github.com/Hypfer/hass-scene_presets`
4. Category: **Integration**
5. Click **Add**, then install the integration
6. Restart Home Assistant

> **Note**: Scene Presets is only needed if you plan to use Philips Hue dynamic scenes. You can skip this if you are not using Hue lighting effects.

---

## Part 3: HACS Frontend Card Installation

Install all required frontend cards through HACS. See [HACS_DEPENDENCIES.md](HACS_DEPENDENCIES.md) for the complete list with URLs and details.

### Installation Order

Install cards in this order to resolve dependencies correctly:

**Tier 1 - Core (install first):**

1. **Mushroom** - Base card framework
2. **Card-Mod** - CSS styling engine (used by nearly every card)
3. **Streamline Card** - Template card system (333 instances in dashboard)
4. **Material You Theme** - MD3 color theming

**Tier 2 - Layout & Structure:**

5. **Layout Card** - Advanced layout control
6. **Stack In Card** - Card grouping
7. **Vertical Stack In Card** - Vertical card grouping
8. **Simple Swipe Card** - Swipeable card sections
9. **Simple Tabs Card** - Tab-based navigation
10. **Navbar Card** - Bottom navigation bar

**Tier 3 - UI Components:**

11. **Button Card** - Custom interactive buttons
12. **Material Symbols** - Google Material icon set
13. **Material You Utilities** - Additional MD3 utilities
14. **Lovelace Material Components** - MD3 UI components
15. **Paper Buttons Row** - Button row layouts

**Tier 4 - Data & Media:**

16. **Mini Graph Card** - Sensor history graphs
17. **Apex Charts Card** - Advanced data charts
18. **Auto Entities** - Dynamic entity card generation
19. **Config Template Card** - Dynamic configuration
20. **Kiosk Mode** - Full-screen display mode
21. **Mediocre Media Player Cards** - Enhanced media controls
22. **My Cards Bundle** - Additional card utilities

**Tier 5 - Optional/Feature-Specific:**

23. **Alarmo Card** - Alarm panel (if using Alarmo)
24. **Bubble Card** - Pop-up card system
25. **Calendar Card Pro** - Calendar display
26. **Timer Bar Card** - Timer visualization
27. **WebRTC Camera** - Camera streaming (if using cameras)
28. **Lunar Phase Card** - Moon phase display (weather panel)
29. **Weather Forecast Extended** - Extended weather (weather panel)

### How to Install Each Card

For each card:

1. Open HACS in the Home Assistant sidebar
2. Go to **Frontend**
3. Click **Explore & Download Repositories** (bottom right)
4. Search for the card name
5. Click the card, then click **Download**
6. Accept any version prompts
7. After all cards are installed, **clear browser cache** and **refresh**

### Verify Installation

After installing all cards, verify they loaded correctly:

1. Open browser Developer Tools (F12)
2. Go to the Console tab
3. Look for any "Custom element doesn't exist" errors
4. If errors appear, the corresponding card needs reinstallation

---

## Part 4: Configuration Validation

### Step 4.1: Validate YAML Syntax

Before activating the dashboard, validate your configuration:

```bash
# Via SSH or Terminal addon
ha core check
```

Or use the built-in **Developer Tools > YAML** validation in the Home Assistant UI.

### Step 4.2: Verify Helper Entities

After restarting Home Assistant, confirm these entities exist in **Developer Tools > States**:

**Light Groups:**
- `group.kitchen_lights`
- `group.living_room_lights`

**Template Sensors:**
- `sensor.bedroom_lights_count`
- `sensor.kitchen_lights_count`
- `sensor.living_room_lights_count`
- `sensor.desk_lights_count`

### Step 4.3: Verify Device Entities

Confirm these entities are available and not showing "unavailable":

**Lights:**
- `light.bedroom_light`
- `light.kitchen_light_front`
- `light.kitchen_light_rear`
- `light.living_room_light_left`
- `light.living_room_light_right`
- `light.desk_light`

**Media Players:**
- `media_player.bedroom_roku`
- `media_player.bedroom_tv`
- `media_player.living_room_tv`

**Vacuum:**
- `vacuum.vacuum`

---

## Part 5: Dashboard Activation

### Step 5.1: Deploy the Dashboard File

Copy the adapted dashboard file to your Home Assistant dashboards directory:

```bash
cp config/dashboards/mobile-dashboard.yaml /config/dashboards/
```

### Step 5.2: Register the Dashboard

Add the dashboard to your Home Assistant configuration. In your `configuration.yaml`:

```yaml
lovelace:
  mode: yaml
  dashboards:
    mobile-dashboard:
      mode: yaml
      filename: dashboards/mobile-dashboard.yaml
      title: "Mobile Dashboard"
      icon: mdi:cellphone
      show_in_sidebar: true
      require_admin: false
```

Restart Home Assistant after adding this configuration.

### Step 5.3: Activate Material You Theme

1. Go to **Settings > Profile** (click your user avatar)
2. Under **Theme**, select **Material You**
3. Choose your preferred color scheme using the color picker
4. The dashboard will dynamically adapt to your chosen colors

### Step 5.4: Apply Wallpaper (Optional)

Wallpaper files are provided in the `wallpaper/` directory:

1. Copy your chosen wallpaper to `/config/www/`:
   ```bash
   cp wallpaper/*.webp /config/www/
   ```
2. Reference in your theme or dashboard configuration
3. Available options: Blue, Green, Monochrome, Purple, Yellow

### Step 5.5: Enable Kiosk Mode (Optional)

For a full-screen mobile experience without the header/sidebar:

1. Kiosk Mode is already included in the dashboard configuration
2. To customize, modify the kiosk-mode settings in the dashboard YAML
3. Access the sidebar by swiping from the left edge when needed

---

## Part 6: Customization

### Adding Rooms

To add a new room to the dashboard:

1. Clone an existing room view section from the dashboard YAML
2. Update entity references to match your new room's devices
3. Add the room to the Rooms overview grid
4. Add navigation entries in the navbar configuration

### Enabling Sensor Features

When sensors arrive, follow the marker system in the dashboard YAML:

- **Search for `# 🔜`** to find sensor-ready features
- Uncomment the relevant YAML blocks
- Update entity IDs to match your paired sensors
- See [SENSOR_INTEGRATION_GUIDE.md](config/dashboards/SENSOR_INTEGRATION_GUIDE.md) for detailed instructions

### Enabling Optional Features

For optional features marked with `# ⚠️`:

- **Alarmo**: Install Alarmo integration, then uncomment alarm sections
- **Cameras**: Add camera entities, then uncomment camera view
- **Climate**: Add thermostat integration, then uncomment climate controls
- **Hue Scenes**: Set up Scene Presets, then uncomment scenes view

See [docs/MISSING_INTEGRATIONS.md](docs/MISSING_INTEGRATIONS.md) for details on each optional integration.

---

## Part 7: GitHub Setup

For version control and backup of your dashboard configuration, see [docs/GITHUB_DEPLOYMENT.md](docs/GITHUB_DEPLOYMENT.md).

Key points:
- The `.gitignore` file is pre-configured to exclude secrets and sensitive data
- Never commit `secrets.yaml` or database files
- Use the VSCode Server addon for convenient git operations

---

## Testing Checklist

After completing deployment, verify each item:

### Core Functionality
- [ ] Dashboard loads without errors in browser console
- [ ] All 6 views are accessible (Overview, Rooms, Bedroom, Kitchen, Living Room, Desk)
- [ ] Navigation between views works correctly
- [ ] Bottom navbar is visible and functional

### Visual & Theming
- [ ] Material You theme is active and colors display correctly
- [ ] Card-mod styling renders properly (no unstyled cards)
- [ ] Animations are smooth
- [ ] Mobile header is hidden (kiosk mode active)
- [ ] Wallpaper displays correctly (if applied)

### Device Control
- [ ] All 6 lights toggle on/off
- [ ] Light brightness control works
- [ ] Light groups respond correctly
- [ ] All 3 media players show current state
- [ ] Media player controls work (play, pause, volume)
- [ ] Vacuum controls are functional

### Data Display
- [ ] Personalized greeting shows correct time of day
- [ ] Light count sensors update when toggling lights
- [ ] Room cards display correct information

See [docs/TESTING_CHECKLIST.md](docs/TESTING_CHECKLIST.md) for the comprehensive validation procedure.

---

## Rollback Procedure

If something goes wrong during deployment:

### Dashboard Issues

1. **Restore from backup:**
   ```bash
   cp config/dashboards/mobile-dashboard.yaml.backup config/dashboards/mobile-dashboard.yaml
   ```
2. Restart Home Assistant

### Configuration Issues

1. **Revert configuration changes:**
   ```bash
   # If using git
   git checkout -- config/configuration.yaml
   ```
2. Alternatively, remove the `packages/dashboard_helpers.yaml` file
3. Restart Home Assistant

### HACS Card Issues

1. Open HACS > Frontend
2. Find the problematic card
3. Click the three dots > **Reinstall**
4. Clear browser cache and refresh

### Complete Rollback

1. Remove the dashboard registration from `configuration.yaml`
2. Delete the dashboard file from `/config/dashboards/`
3. Restart Home Assistant
4. The default Lovelace dashboard will be used instead

---

## Support

### Common Issues

| Issue | Solution |
|-------|----------|
| "Custom element doesn't exist" | Reinstall the missing HACS card, clear cache |
| Entities show "unavailable" | Check device power and integration settings |
| Dashboard blank/error | Validate YAML syntax with `ha core check` |
| Theme not applying | Select theme in Profile settings, clear cache |
| Cards unstyled | Verify card-mod is installed and updated |

### Resources

- **Home Assistant Docs**: https://www.home-assistant.io/dashboards/
- **HACS Docs**: https://hacs.xyz/
- **Material You Theme**: https://github.com/Nerwyn/material-you-theme
- **Community Forum**: https://community.home-assistant.io/
- **Reddit**: r/homeassistant

### Project Documentation

- [HACS_DEPENDENCIES.md](HACS_DEPENDENCIES.md) - Complete card dependency list
- [VALIDATION_REPORT.md](VALIDATION_REPORT.md) - Implementation validation status
- [config/dashboards/SENSOR_INTEGRATION_GUIDE.md](config/dashboards/SENSOR_INTEGRATION_GUIDE.md) - Sensor setup guide
- [docs/TESTING_CHECKLIST.md](docs/TESTING_CHECKLIST.md) - Full testing procedures
- [docs/MISSING_INTEGRATIONS.md](docs/MISSING_INTEGRATIONS.md) - Optional integration guide
- [docs/GITHUB_DEPLOYMENT.md](docs/GITHUB_DEPLOYMENT.md) - Git workflow guide
