# Sensor Integration Guide

## Overview

This guide provides step-by-step instructions for integrating your 22 Zigbee sensors into the Home Assistant dashboard. The dashboard is pre-configured with sensor-ready features marked with 🔜 that can be activated once sensors are paired.

## Expected Sensor Inventory

### Motion Sensors (8 Devices)
- Bedroom motion sensor
- Kitchen motion sensor
- Living room motion sensor
- Desk motion sensor
- Hallway motion sensor
- Bathroom motion sensor
- Entry motion sensor
- Closet motion sensor

### Contact Sensors (6 Devices)
- Front door contact sensor
- Back door contact sensor
- Bedroom window contact sensor
- Kitchen window contact sensor
- Living room window contact sensor
- Bathroom window contact sensor

### Multi-Sensors with Climate (8 Devices)
Each providing temperature + humidity:
- Bedroom climate sensor
- Kitchen climate sensor
- Living room climate sensor
- Desk climate sensor
- Hallway climate sensor
- Bathroom climate sensor
- Entry climate sensor
- Closet climate sensor

**Total:** 22 Zigbee devices

## Pre-Integration Checklist

- [ ] Zigbee coordinator/hub is installed and operational
- [ ] Home Assistant Zigbee integration configured (ZHA or Zigbee2MQTT)
- [ ] Fresh batteries installed in all sensors
- [ ] Physical mounting locations planned for each sensor
- [ ] Backup of current dashboard configuration created

## Step 1: Pairing Sensors to Home Assistant

### Using ZHA (Zigbee Home Automation)

1. Navigate to **Settings > Devices & Services > Zigbee Home Automation**
2. Click **"Add Device"** or **"Configure"** > **"Add Device"**
3. Put sensor in pairing mode (usually hold reset button 5-10 seconds)
4. Wait for HA to discover the device (typically 30-60 seconds)
5. Assign a clear, descriptive name during pairing
6. Repeat for all 22 sensors

### Using Zigbee2MQTT

1. Open Zigbee2MQTT interface (usually port 8099)
2. Click **"Permit Join"** button
3. Put sensor in pairing mode
4. Wait for device to appear in device list
5. Rename device with clear identifier
6. Repeat for all 22 sensors

### Recommended Naming During Pairing

**Motion Sensors:**
- "Bedroom Motion Sensor"
- "Kitchen Motion Sensor"
- "Living Room Motion Sensor"
- "Desk Motion Sensor"
- "Hallway Motion Sensor"
- "Bathroom Motion Sensor"
- "Entry Motion Sensor"
- "Closet Motion Sensor"

**Contact Sensors:**
- "Front Door Contact"
- "Back Door Contact"
- "Bedroom Window Contact"
- "Kitchen Window Contact"
- "Living Room Window Contact"
- "Bathroom Window Contact"

**Climate Sensors:**
- "Bedroom Climate Sensor"
- "Kitchen Climate Sensor"
- "Living Room Climate Sensor"
- "Desk Climate Sensor"
- (etc. for remaining rooms)

## Step 2: Verify Entity IDs

After pairing, verify that entity IDs match dashboard expectations.

### Check Entity IDs

1. Navigate to **Developer Tools > States**
2. Search for newly paired sensors
3. Verify entity ID format matches expectations

### Expected Entity ID Format

**Motion Sensors:**
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

**Contact Sensors:**
```yaml
binary_sensor.front_door
binary_sensor.back_door
binary_sensor.bedroom_window
binary_sensor.kitchen_window
binary_sensor.living_room_window
binary_sensor.bathroom_window
```

**Climate Sensors:**
```yaml
sensor.bedroom_temperature
sensor.bedroom_humidity
sensor.kitchen_temperature
sensor.kitchen_humidity
sensor.living_room_temperature
sensor.living_room_humidity
sensor.desk_temperature
sensor.desk_humidity
# (additional rooms as applicable)
```

### Rename Entity IDs if Needed

If auto-generated entity IDs don't match expectations:

1. Go to **Settings > Devices & Services**
2. Find the sensor device
3. Click on the device
4. Click on the entity name
5. Click the gear icon (Settings)
6. Update **Entity ID** to match dashboard format
7. Click **Update**

**Example:**
- Auto-generated: `binary_sensor.motion_sensor_bedroom_occupancy`
- Rename to: `binary_sensor.bedroom_motion`

## Step 3: Test Sensor Functionality

Before uncommenting dashboard features, verify all sensors work correctly.

### Motion Sensor Testing

1. Open **Developer Tools > States**
2. Filter for `binary_sensor.*motion`
3. Trigger motion in front of each sensor
4. Verify state changes from `off` to `on`
5. Note reset time (when it returns to `off`)

### Contact Sensor Testing

1. Filter for `binary_sensor.*door` or `binary_sensor.*window`
2. Open/close each door or window
3. Verify state changes (`on` = open, `off` = closed)
4. Check that states update within 1-2 seconds

### Climate Sensor Testing

1. Filter for `sensor.*temperature` and `sensor.*humidity`
2. Verify readings are reasonable:
   - Temperature: typically 15-30°C (60-85°F)
   - Humidity: typically 30-60%
3. Sensors should update every 1-5 minutes

### Troubleshooting Sensor Issues

**Sensor Not Responding:**
- Check battery level in device info
- Move sensor closer to coordinator
- Re-pair the sensor
- Check Zigbee mesh interference

**Incorrect State:**
- Check sensor mounting position
- Verify sensitivity settings (if adjustable)
- Update device firmware if available

## Step 4: Bulk Uncommenting Strategy

Once all sensors are verified working, activate dashboard features.

### Method 1: Find and Replace (Recommended)

The dashboard uses `🔜` markers to indicate sensor-ready features.

**In Home Assistant YAML Editor:**

1. Open `dynamic_dashboard.yaml` in editor
2. Use Find & Replace (Ctrl+H or Cmd+H)
3. Find: `# 🔜`
4. Replace with: `` (empty string)
5. Review changes in preview
6. Click **Save**

**In External Editor (VS Code, Notepad++, etc.):**

1. Open `/config/dashboards/dynamic_dashboard.yaml`
2. Use Find & Replace
3. Find: `# 🔜`
4. Replace with: `` (empty string)
5. Save file
6. Reload dashboard in HA

### Method 2: Section-by-Section Uncommenting

For more controlled activation, uncomment by section:

**Priority Order:**

1. **Motion-Based Lighting** (highest impact)
   - Search for `# 🔜 motion` in file
   - Uncomment motion sensor references
   - Test in each room view

2. **Climate Monitoring** (visual feedback)
   - Search for `# 🔜 temperature` or `# 🔜 climate`
   - Uncomment climate cards
   - Verify readings display correctly

3. **Door/Window Status** (security)
   - Search for `# 🔜 door` or `# 🔜 window`
   - Uncomment contact sensor cards
   - Test open/close detection

4. **Conditional Cards** (dynamic display)
   - Search for `# 🔜 conditions:`
   - Uncomment conditional show/hide logic
   - Verify cards appear when motion detected

### Method 3: Manual Uncommenting

For complete control over each feature:

1. Search file for `# 🔜` marker
2. Read surrounding context to understand feature
3. Remove `# 🔜` prefix from relevant lines
4. Test feature immediately
5. Move to next marker

### Validation Checklist After Uncommenting

- [ ] Dashboard loads without errors
- [ ] All motion sensors display in room views
- [ ] Climate cards show current temperature/humidity
- [ ] Door/window status cards update in real-time
- [ ] Conditional cards appear when motion detected
- [ ] No "entity not found" errors in browser console
- [ ] All room views render correctly
- [ ] Navigation still works smoothly

## Step 5: Entity Name Customization (Optional)

If your entity IDs differ from dashboard expectations, use customization instead of bulk replace.

### Option A: Use Customize.yaml

Add to `/config/customize.yaml`:

```yaml
# Map actual entities to dashboard-expected names
binary_sensor.actual_bedroom_motion_sensor:
  friendly_name: Bedroom Motion

sensor.bedroom_temp_sensor:
  friendly_name: Bedroom Temperature
```

### Option B: Dashboard-Level Entity Substitution

Use YAML anchors for entity mapping:

```yaml
# At top of dynamic_dashboard.yaml
substitutions:
  bedroom_motion: &bedroom_motion binary_sensor.actual_bedroom_motion_id
  kitchen_motion: &kitchen_motion binary_sensor.actual_kitchen_motion_id

# Then use in cards:
entity: *bedroom_motion
```

### Option C: Global Find & Replace

If entity naming is consistently different:

**Example:** All motion sensors have `_occupancy` suffix

Find: `binary_sensor.bedroom_motion`
Replace: `binary_sensor.bedroom_motion_occupancy`

Repeat pattern for all mismatched entities.

## Step 6: Post-Integration Testing

### Functional Testing

**Motion-Based Automation:**
1. Walk into each room
2. Verify motion sensor triggers
3. Check that conditional cards appear
4. Confirm lighting automation suggestions display

**Climate Monitoring:**
1. Check each room view
2. Verify temperature/humidity cards display
3. Confirm readings update periodically
4. Test history graphs (if enabled)

**Door/Window Monitoring:**
1. Open and close each door/window
2. Verify status updates immediately
3. Check security overview shows correct states
4. Test notification triggers (if configured)

### Performance Testing

1. Navigate between all room views
2. Verify smooth transitions
3. Check dashboard load time is acceptable
4. Monitor browser console for errors
5. Test on mobile device if used

### Error Checking

**In Home Assistant:**
1. Go to **Settings > System > Logs**
2. Filter for errors related to dashboard
3. Address any entity not found errors
4. Fix YAML syntax issues if present

**In Browser Console:**
1. Press F12 to open developer tools
2. Check Console tab for JavaScript errors
3. Look for custom card errors
4. Verify all HACS dependencies loaded

## Step 7: Optimization and Fine-Tuning

### Adjust Sensor Sensitivity

Some sensors allow sensitivity configuration:

1. Go to device settings in HA
2. Look for sensitivity or timeout parameters
3. Adjust to reduce false triggers
4. Test new settings

### Customize Conditional Logic

Edit conditions for when cards appear:

```yaml
# Example: Only show motion card during daytime
conditions:
  - condition: state
    entity: binary_sensor.bedroom_motion
    state: "on"
  - condition: sun
    after: sunrise
    before: sunset
```

### Battery Monitoring Setup

Create automation to notify on low battery:

```yaml
automation:
  - alias: "Low Sensor Battery Alert"
    trigger:
      - platform: numeric_state
        entity_id:
          - sensor.bedroom_motion_battery
          - sensor.kitchen_motion_battery
          # (add all sensors)
        below: 20
    action:
      - service: notify.mobile_app
        data:
          message: "Sensor battery low: {{ trigger.entity_id }}"
```

## Common Issues and Solutions

### Issue: Entity Not Found After Uncommenting

**Symptoms:** Red "Entity not available" message
**Causes:**
- Entity ID mismatch
- Sensor not paired correctly
- Integration not loaded

**Solutions:**
1. Verify entity exists in Developer Tools > States
2. Check spelling and underscores vs. dashes
3. Re-pair sensor if necessary
4. Restart Home Assistant

### Issue: Motion Sensor Not Triggering Cards

**Symptoms:** Card doesn't appear when motion detected
**Causes:**
- Conditional logic incorrect
- Sensor state not updating
- Card syntax error

**Solutions:**
1. Test sensor state changes in Developer Tools
2. Verify conditional syntax in card
3. Check entity ID in condition matches sensor
4. Review browser console for errors

### Issue: Climate Readings Incorrect

**Symptoms:** Temperature shows wrong value or not updating
**Causes:**
- Sensor reporting in wrong units
- Sensor needs calibration
- Entity ID mismatch

**Solutions:**
1. Check sensor device settings for unit configuration
2. Apply calibration offset if available
3. Verify entity ID in dashboard matches sensor
4. Check sensor placement (away from heat sources)

### Issue: Dashboard Performance Degraded

**Symptoms:** Slow loading, laggy interface
**Causes:**
- Too many history graphs
- Excessive conditional cards
- Browser cache issues

**Solutions:**
1. Reduce number of graphs or history period
2. Disable some conditional cards temporarily
3. Clear browser cache (Ctrl+F5)
4. Consider splitting into multiple dashboards

## Next Steps

After successful sensor integration:

1. **Monitor Stability:** Run for 24-48 hours, check for issues
2. **Optimize Automations:** Fine-tune motion timeouts and conditions
3. **Add Advanced Features:** Consider uncommenting optional features
4. **Create Automations:** Build on sensor data for smart behaviors
5. **Document Changes:** Update CHANGELOG.md with modifications

## Reference: Complete Entity List After Integration

```yaml
# Motion Sensors (8)
binary_sensor.bedroom_motion
binary_sensor.kitchen_motion
binary_sensor.living_room_motion
binary_sensor.desk_motion
binary_sensor.hallway_motion
binary_sensor.bathroom_motion
binary_sensor.entry_motion
binary_sensor.closet_motion

# Contact Sensors (6)
binary_sensor.front_door
binary_sensor.back_door
binary_sensor.bedroom_window
binary_sensor.kitchen_window
binary_sensor.living_room_window
binary_sensor.bathroom_window

# Climate Sensors (16 entities from 8 devices)
sensor.bedroom_temperature
sensor.bedroom_humidity
sensor.kitchen_temperature
sensor.kitchen_humidity
sensor.living_room_temperature
sensor.living_room_humidity
sensor.desk_temperature
sensor.desk_humidity
sensor.hallway_temperature
sensor.hallway_humidity
sensor.bathroom_temperature
sensor.bathroom_humidity
sensor.entry_temperature
sensor.entry_humidity
sensor.closet_temperature
sensor.closet_humidity
```

## Support Resources

- **Home Assistant Zigbee Integration:** https://www.home-assistant.io/integrations/zha/
- **Zigbee2MQTT Documentation:** https://www.zigbee2mqtt.io/
- **Dashboard Troubleshooting:** See DASHBOARD_README.md
- **Change History:** See CHANGELOG.md

---

*Good luck with your sensor integration! The dashboard is ready to come alive with automation.*
