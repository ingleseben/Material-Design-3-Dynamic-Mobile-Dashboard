# Dashboard Structure Analysis

## File Statistics
- **Total Lines**: 10,982
- **Template Section**: Lines 1-1773 (PRESERVE ALL)
- **Room Selector**: Lines 1774-1920 (ADAPT - reduce rooms)
- **Views Section**: Lines 1921-10982 (ADAPT)
- **Total Views**: 16

## View Breakdown

### Views to KEEP and ADAPT (5 + 1 new = 6 total)

| View Name | Path | Lines | User Equivalent | Action Required |
|-----------|------|-------|-----------------|-----------------|
| Overview | overview | 2113-4549 | Overview | Simplify, comment sensors |
| Rooms | rooms | 4550-5061 | Rooms | Reduce to 4 rooms |
| Living Area | living-area | 7629-8186 | Living Room | Rename + adapt entities |
| Master Bedroom | master-bedroom | 8187-8754 | Bedroom | Adapt entities |
| Office | office | 10062-10398 | Desk | Adapt entities |
| **Kitchen** | kitchen | **NEW** | Kitchen | **Create from template** |

### Views to COMMENT - HIGH PRIORITY 🔜 (1 view)

| View Name | Path | Lines | Reason | When to Enable |
|-----------|------|-------|--------|----------------|
| Scenes | scenes | 5062-6073 | No Hue integration yet | If/when Hue is added |

### Views to REMOVE - LOW PRIORITY ⚠️ (9 views)

| View Name | Path | Lines | Reason |
|-----------|------|-------|--------|
| Camera | camera | 6074-6599 | No cameras |
| Irrigation | irrigation | 6600-7303 | No irrigation system |
| Garage | garage | 7304-7628 | Don't have garage |
| Baby Room | baby-room | 8755-9113 | Don't have baby room |
| Single Guest Room | single-guest-room | 9114-9453 | Don't have guest room |
| Multiple Guest Room | multiple-guest-room | 9454-9793 | Don't have guest room |
| Entrance | entrance | 9794-10061 | Don't have entrance sensors |
| Guest Bathroom | guest-bathroom | 10399-10716 | Don't have bathroom sensors |
| Driveway | driveway | 10717-10982 | Don't have driveway |

## Room Selector Template

**Location**: Lines 1774-1920

**Current Rooms** (10 total):
1. Garage
2. Living Area
3. Master Bedroom
4. Baby Room
5. Single Guest Room
6. Multiple Guest Room
7. Entrance
8. Office
9. Guest Bathroom
10. Driveway

**Target Rooms** (4 total):
1. Bedroom (was: Master Bedroom)
2. Kitchen (NEW)
3. Living Room (was: Living Area)
4. Desk (was: Office)

**Action**: Adapt lines 1802-1913 to show only 4 room cards

## Entity Mapping Matrix

### Current View → User's Setup

#### Bedroom (was: Master Bedroom, lines 8187-8754)
- `light.lights_mbr` → `light.bedroom_light`
- `media_player.jbl_bar_500` → `media_player.bedroom_roku`
- Add: `media_player.bedroom_tv`
- Add: `media_player.bedroom_tv_renderer`
- Comment sensors with 🔜: temperature, humidity, door, motion, presence

#### Kitchen (NEW - clone from Living Area structure)
- Use: `group.kitchen_lights`
- Use: `sensor.kitchen_lights_count`
- Comment sensors with 🔜: temperature, humidity, door

#### Living Room (was: Living Area, lines 7629-8186)
- `light.lights_la` → `group.living_room_lights`
- `media_player.living_room_tv` → `media_player.living_room_tv` (same)
- Add: `vacuum.vacuum` control
- Comment sensors with 🔜: temperature, humidity, door, motion, presence

#### Desk (was: Office, lines 10062-10398)
- `light.lights_or` → `light.desk_light`
- Comment sensors with 🔜: temperature, humidity, door, presence

## Streamline Templates Usage

**Total Uses**: 333 streamline-card instances

**Critical Templates** (must preserve):
- `date_clock_text_card` - Clock display
- `spacer_card` - Layout spacing
- `room_selector` - Room navigation popup
- Various entity control templates

**Action**: Preserve ALL template definitions (lines 1-1773), only modify entity references

## Sensor Integration Readiness

### Entities to Comment with 🔜 (arriving in 3-5 days)

**Binary Sensors** (12 total):
- `binary_sensor.bedroom_motion`
- `binary_sensor.bedroom_presence`
- `binary_sensor.bedroom_door`
- `binary_sensor.kitchen_door`
- `binary_sensor.living_room_motion`
- `binary_sensor.living_room_presence`
- `binary_sensor.living_room_door`
- `binary_sensor.desk_presence`
- `binary_sensor.desk_door`

**Regular Sensors** (4 entities from 2 physical devices):
- `sensor.bedroom_temperature`
- `sensor.bedroom_humidity`
- `sensor.living_room_temperature`
- `sensor.living_room_humidity`

**Switches** (4 smart plugs):
- `switch.bedroom_plug`
- `switch.kitchen_plug`
- `switch.living_room_plug`
- `switch.desk_plug`

**Additional Lights** (8 smart bulbs):
- `light.bedroom_bulb_1`, `light.bedroom_bulb_2`
- `light.kitchen_bulb_1`, `light.kitchen_bulb_2`
- `light.living_room_bulb_1`, `light.living_room_bulb_2`
- `light.desk_bulb_1`, `light.desk_bulb_2`

### Features to Comment with ⚠️ (long-term optional)

**Climate Control** (in all room views):
- `climate.bedroom`, `climate.kitchen`, `climate.living_room`, `climate.desk`
- Reason: No thermostat/HVAC system

**Covers/Blinds** (in room views):
- `cover.bedroom_curtain`, etc.
- Reason: No smart blinds

**Alarmo Security** (in Overview):
- `alarm_control_panel.alarmo`
- Reason: No alarm system

## Next Steps for Task #3

1. ✅ Copy template → DONE
2. ✅ Analyze structure → DONE
3. ✅ Create this structure map → DONE
4. Mark task complete
5. Unblock tasks #4, #5, #6 for adaptation work

## Validation Checkpoints

After adaptation complete, verify:
- [ ] streamline_templates intact (lines 1-1773)
- [ ] room_selector reduced to 4 rooms
- [ ] 6 views total (Overview, Rooms, Bedroom, Kitchen, Living Room, Desk)
- [ ] 10 views commented/removed with proper markers
- [ ] All entity references updated
- [ ] YAML syntax valid (`ha core check`)
- [ ] File size ~6000 active lines
