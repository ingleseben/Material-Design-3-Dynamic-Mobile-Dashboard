# Dynamic Dashboard Documentation

## Overview

This custom Home Assistant dashboard provides a comprehensive smart home interface optimized for a 4-room setup with dynamic automation features. The dashboard has been adapted from a template, reducing code from 10,982 lines to approximately 6,000 active lines while maintaining core functionality.

## Current Status

### Active Features (25% - Working Now)
- **Navigation & UI**: Full navigation system with 4 area-specific views
- **Lighting Control**: 6 WiZ smart lights with full control
- **Media Players**: 3 Roku/TV devices with playback controls
- **Vacuum Control**: Roborock integration with status and controls
- **System Monitoring**: Basic server stats and weather integration
- **Personalized Greeting**: Dynamic time-based greeting card

### Sensor-Ready Features (50% - Commented with 🔜)
- **Motion-Based Lighting**: Automation triggers ready for 8 motion sensors
- **Climate Monitoring**: Temperature/humidity displays ready for 8 sensors
- **Door/Window Monitoring**: Security status ready for 6 contact sensors
- **Presence Detection**: Room occupancy tracking infrastructure
- **Conditional Cards**: Show/hide based on motion, doors, climate

### Optional Future Features (25% - Fully Commented)
- Advanced automations requiring additional sensors
- Multi-zone climate control
- Security system integration
- Extended media automation

## Complete Dependency List

### Required HACS Frontend Cards (18 Total)

**Core Cards:**
1. `button-card` - Custom buttons for lights, scenes, navigation
2. `mushroom` - Clean, modern card designs
3. `mini-graph-card` - Compact sensor history graphs
4. `apexcharts-card` - Advanced charting for trends
5. `card-mod` - CSS styling customization

**Layout & Organization:**
6. `layout-card` - Advanced layout control
7. `vertical-stack-in-card` - Nested card grouping
8. `swipe-card` - Touch-friendly card swiping
9. `auto-entities` - Dynamic card generation

**Media & Entertainment:**
10. `mini-media-player` - Enhanced media player controls
11. `spotify-card` - Spotify integration (if used)

**Vacuum & Cleaning:**
12. `vacuum-card` - Visual vacuum map/controls

**Utility & Monitoring:**
13. `bar-card` - Progress bars for sensors
14. `multiple-entity-row` - Compact multi-entity display
15. `slider-entity-row` - Inline sliders for brightness/volume

**Advanced Features:**
16. `decluttering-card` - Template reusability
17. `state-switch` - Conditional view switching
18. `browser-mod` - Browser-specific features

### Installation Command
```bash
# Install all dependencies via HACS
# Search for each card name in HACS > Frontend
```

## Entity Reference

### Current Working Entities

**Lights (6 WiZ Devices):**
```yaml
light.bedroom_main          # Bedroom primary light
light.bedroom_accent        # Bedroom accent/mood lighting
light.kitchen_overhead      # Kitchen main overhead
light.kitchen_under_cabinet # Kitchen task lighting
light.living_room_main      # Living room primary
light.desk_lamp             # Desk workspace light
```

**Media Players (3 Devices):**
```yaml
media_player.bedroom_roku   # Bedroom Roku device
media_player.bedroom_tv     # Bedroom TV
media_player.living_room_tv # Living room TV
```

**Vacuum (1 Device):**
```yaml
vacuum.roborock            # Roborock vacuum cleaner
```

### Sensor Entities (Arriving in 3-5 Days)

**Motion Sensors (8 Expected):**
```yaml
binary_sensor.bedroom_motion
binary_sensor.kitchen_motion
binary_sensor.living_room_motion
binary_sensor.desk_motion
binary_sensor.hallway_motion
binary_sensor.bathroom_motion
binary_sensor.entry_motion
binary_sensor.closet_motion
```

**Contact Sensors (6 Expected):**
```yaml
binary_sensor.front_door
binary_sensor.back_door
binary_sensor.bedroom_window
binary_sensor.kitchen_window
binary_sensor.living_room_window
binary_sensor.bathroom_window
```

**Climate Sensors (8 Expected - Multi-Sensor Devices):**
```yaml
sensor.bedroom_temperature
sensor.bedroom_humidity
sensor.kitchen_temperature
sensor.kitchen_humidity
sensor.living_room_temperature
sensor.living_room_humidity
sensor.desk_temperature
sensor.desk_humidity
```

## Dashboard Structure

### Views (4 Active + 1 Home)

1. **Home/Overview** - Summary of all systems
2. **Bedroom View** - Bedroom-specific controls
3. **Kitchen View** - Kitchen lighting and appliances
4. **Living Room View** - Entertainment center
5. **Desk View** - Workspace controls

### File Locations

```
/config/dashboards/
├── dynamic_dashboard.yaml          # Main dashboard file (~6,000 lines)
├── DASHBOARD_README.md             # This file
├── SENSOR_INTEGRATION_GUIDE.md     # Sensor pairing instructions
└── CHANGELOG.md                    # Change tracking from template
```

## Key Features

### 1. Conditional Display Logic
Cards automatically show/hide based on:
- Motion detection (when sensors active)
- Door/window states
- Time of day
- Device availability

### 2. Personalized Greeting
Dynamic greeting card displays:
- Time-based salutation (Good Morning/Afternoon/Evening)
- Current weather conditions
- Quick status overview

### 3. Room-Specific Automation
Each room view includes:
- Local lighting controls
- Motion-based automation triggers
- Climate monitoring
- Media/device controls

### 4. Marker System
Features use markers for easy identification:
- `🔜` - Sensor-dependent feature (uncomment when sensors arrive)
- `# OPTIONAL:` - Future enhancement features
- No marker - Currently active

## Troubleshooting Guide

### Cards Not Displaying

**Issue:** Cards appear as "Custom element doesn't exist"
**Solution:**
1. Verify HACS card installation
2. Clear browser cache (Ctrl+F5)
3. Restart Home Assistant
4. Check browser console for specific errors

### Entities Showing "Unavailable"

**Issue:** Entity states show as unavailable
**Solution:**
1. Verify device is powered on and connected
2. Check integration configuration in Settings > Devices
3. Restart device integration
4. Check HA logs: Settings > System > Logs

### Motion Sensors Not Triggering

**Issue:** Sensor-based cards not appearing (when sensors active)
**Solution:**
1. Verify sensor entity names match dashboard configuration
2. Check sensor battery levels
3. Test sensor trigger in Developer Tools > States
4. Verify conditional card syntax

### Dashboard Not Loading

**Issue:** Dashboard shows errors or blank screen
**Solution:**
1. Check YAML syntax with built-in editor
2. Review HA logs for specific errors
3. Validate all entity IDs exist
4. Ensure all HACS dependencies installed

### Performance Issues

**Issue:** Dashboard slow to load or respond
**Solution:**
1. Reduce number of history graphs
2. Disable unused cards temporarily
3. Clear browser cache
4. Consider splitting into multiple dashboards

### Styling Issues

**Issue:** Cards don't match expected appearance
**Solution:**
1. Verify `card-mod` is installed and updated
2. Check theme compatibility
3. Clear browser cache
4. Review CSS syntax in card-mod configurations

## Quick Start Checklist

- [ ] Install all 18 HACS frontend dependencies
- [ ] Verify 6 lights are configured and responding
- [ ] Test 3 media players for control
- [ ] Confirm vacuum integration working
- [ ] Review personalized greeting displays correctly
- [ ] Navigate all 4 room views successfully
- [ ] Wait for sensors to arrive (3-5 days)
- [ ] Follow SENSOR_INTEGRATION_GUIDE.md when sensors arrive
- [ ] Uncomment 🔜 marked features after sensor pairing
- [ ] Test motion-based automations
- [ ] Validate climate monitoring displays

## Support & Resources

**Home Assistant Documentation:**
- Dashboard Configuration: https://www.home-assistant.io/dashboards/
- YAML Syntax: https://www.home-assistant.io/docs/configuration/yaml/

**HACS Card Documentation:**
- Search individual card names in HACS for official docs
- Most cards have GitHub repos with examples

**Community Support:**
- Home Assistant Community Forums
- Reddit: r/homeassistant
- Discord: Home Assistant community

## Version Information

- **Dashboard Version:** 1.0
- **Template Source:** Streamlined template (reduced 10,982 → 6,000 lines)
- **Last Updated:** 2026-02-15
- **HA Compatibility:** 2024.1+

## Future Enhancements

Potential additions when ready:
- Security camera integration
- Multi-zone audio system
- Advanced presence detection
- Energy monitoring dashboards
- Irrigation/garden automation
- Pet monitoring features

---

*For sensor integration instructions, see SENSOR_INTEGRATION_GUIDE.md*
*For change history from template, see CHANGELOG.md*
