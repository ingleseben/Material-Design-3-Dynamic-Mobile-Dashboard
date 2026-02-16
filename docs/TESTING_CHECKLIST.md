# Testing Checklist

Comprehensive validation procedures for the Material Design 3 Dynamic Mobile Dashboard.

---

## Pre-Deployment Tests

Run these checks before deploying the dashboard to your Home Assistant instance.

### YAML Validation

- [ ] Run `ha core check` with no errors
- [ ] Dashboard YAML opens without errors in a YAML linter
- [ ] No duplicate keys in any YAML mapping
- [ ] All entity IDs follow naming convention (`domain.room_device`)

### File Verification

- [ ] `config/dashboards/mobile-dashboard.yaml` exists and is not empty
- [ ] `config/configuration.yaml` contains light groups and template sensors
- [ ] `.gitignore` excludes `secrets.yaml`, `ha-repos/`, and database files
- [ ] No secrets or credentials present in any committed file

### HACS Dependencies

- [ ] All 22 required HACS frontend cards installed (Tiers 1-4)
- [ ] No "Custom element doesn't exist" errors in browser console
- [ ] HACS shows all cards as up to date
- [ ] Browser cache cleared after card installation

---

## Configuration Tests

### Helper Entities

Verify in **Developer Tools > States**:

- [ ] `group.kitchen_lights` exists and lists correct entities
- [ ] `group.living_room_lights` exists and lists correct entities
- [ ] `sensor.bedroom_lights_count` returns a number
- [ ] `sensor.kitchen_lights_count` returns a number
- [ ] `sensor.living_room_lights_count` returns a number
- [ ] `sensor.desk_lights_count` returns a number

### Light Groups

Test group behavior:

- [ ] Turning on `group.kitchen_lights` activates both kitchen lights
- [ ] Turning off `group.kitchen_lights` deactivates both kitchen lights
- [ ] Turning on `group.living_room_lights` activates both living room lights
- [ ] Turning off `group.living_room_lights` deactivates both living room lights
- [ ] Light count sensors update within 5 seconds of state change

### Device Availability

Verify all devices show state other than "unavailable":

- [ ] `light.bedroom_light` - responds to toggle
- [ ] `light.kitchen_light_front` - responds to toggle
- [ ] `light.kitchen_light_rear` - responds to toggle
- [ ] `light.living_room_light_left` - responds to toggle
- [ ] `light.living_room_light_right` - responds to toggle
- [ ] `light.desk_light` - responds to toggle
- [ ] `media_player.bedroom_roku` - shows idle/playing state
- [ ] `media_player.bedroom_tv` - shows on/off state
- [ ] `media_player.living_room_tv` - shows on/off state
- [ ] `vacuum.vacuum` - shows idle/docked state

---

## Dashboard Tests

### Navigation

- [ ] Dashboard loads from the sidebar
- [ ] Overview page renders without errors
- [ ] Rooms page renders and shows room grid
- [ ] Tapping a room card navigates to that room's view
- [ ] Back button/navigation returns to Rooms or Overview
- [ ] Navbar is visible at the bottom of each page
- [ ] All navbar icons are correct and tappable
- [ ] Each navbar item navigates to the correct view

### Overview Page

- [ ] Personalized greeting displays correct time-based message
- [ ] Date and time display correctly
- [ ] Home tab is visible and selected by default
- [ ] Tabs switch content correctly (Home / Events / Active)
- [ ] Indoor temperature card displays (if climate sensors exist)
- [ ] Now Playing card shows media player state
- [ ] Floating navigation bar appears at bottom

### Rooms Page

- [ ] Room grid displays 4 rooms (Bedroom, Kitchen, Living Room, Desk)
- [ ] Room cards show room name and icon
- [ ] Room cards display temperature/humidity (when sensors available)
- [ ] Quick-action buttons on room cards work
- [ ] Tapping room name navigates to room detail view

### Individual Room Views

Test each room view: **Bedroom**, **Kitchen**, **Living Room**, **Desk**

- [ ] View loads without errors
- [ ] Room header displays correct room name
- [ ] Light controls toggle correctly
- [ ] Light brightness slider works (if applicable)
- [ ] Light count indicator updates on toggle
- [ ] Media controls visible (Bedroom, Living Room)
- [ ] Media play/pause works
- [ ] Vacuum controls visible (Living Room)
- [ ] Vacuum start/stop works
- [ ] Room tabs work (Room / Climate / Active) where applicable

---

## Integration Tests

### Theme Integration

- [ ] Material You theme is selected in Profile settings
- [ ] `--md-sys-color-*` CSS variables are populated
- [ ] Cards use themed colors consistently
- [ ] Switching theme colors updates dashboard appearance
- [ ] Dark mode and light mode both render correctly

### Card-Mod Styling

- [ ] Mushroom cards have custom styling applied
- [ ] Card borders and backgrounds match MD3 design
- [ ] Rounded corners display correctly
- [ ] Transparent/semi-transparent card backgrounds render
- [ ] No cards appear with default unstyled borders

### Streamline Templates

- [ ] Template-based cards render correctly
- [ ] `date_clock_text_card` displays time
- [ ] `spacer_card` creates proper spacing
- [ ] Room cards use streamline templates without errors

### Animations

- [ ] Card hover/tap animations work on desktop
- [ ] Touch feedback animations work on mobile
- [ ] `@keyframes` animations render (loading spinners, etc.)
- [ ] Transitions between views are smooth
- [ ] No animation jank or layout shifts

---

## HACS Card Tests

Verify each installed card type renders correctly.

### Core Cards

- [ ] Mushroom entity cards display with correct styling
- [ ] Card-mod CSS overrides apply correctly
- [ ] Streamline card templates resolve properly
- [ ] Material You theme variables work in card-mod

### Layout Cards

- [ ] Layout card grid columns render correctly
- [ ] Stack-in-card grouping works
- [ ] Vertical-stack-in-card grouping works
- [ ] Simple Swipe Card swiping is functional
- [ ] Simple Tabs Card tab switching works
- [ ] Navbar Card bottom bar renders and is interactive

### Data Cards

- [ ] Button Card custom buttons render and respond to taps
- [ ] Mini Graph Card shows history (when data available)
- [ ] ApexCharts Card renders charts (when data available)
- [ ] Auto Entities card dynamically populates
- [ ] Config Template Card resolves templates

---

## Automation Tests

### Greeting Card

- [ ] Morning greeting (6 AM - 12 PM): "Good Morning"
- [ ] Afternoon greeting (12 PM - 5 PM): "Good Afternoon"
- [ ] Evening greeting (5 PM - 9 PM): "Good Evening"
- [ ] Night greeting (9 PM - 6 AM): "Good Night"

### Active Tab

- [ ] Active entities appear when lights are turned on
- [ ] Active entities disappear when lights are turned off
- [ ] Multiple active entities display in a list
- [ ] Empty state shows when no entities are active

---

## Git Tests

### Repository Integrity

- [ ] `git status` shows clean working tree (no unexpected changes)
- [ ] `.gitignore` properly excludes `secrets.yaml`
- [ ] `.gitignore` properly excludes `ha-repos/`
- [ ] `.gitignore` properly excludes database files
- [ ] No binary files tracked unnecessarily (except wallpapers)

### Commit History

- [ ] Recent commits have descriptive messages
- [ ] No commits contain secrets or credentials
- [ ] Backup files are accessible in git history

---

## Performance Tests

### Load Time

- [ ] Dashboard initial load completes within 5 seconds
- [ ] Subsequent loads (cached) complete within 2 seconds
- [ ] View navigation transitions within 1 second
- [ ] No perceptible lag when switching tabs

### Resource Usage

- [ ] Browser memory usage stays under 500MB
- [ ] No memory leak after extended use (30+ minutes)
- [ ] No excessive network requests (check DevTools Network tab)
- [ ] CPU usage does not spike continuously

### Mobile Performance

- [ ] Dashboard renders correctly on mobile viewport (375px width)
- [ ] Touch interactions respond within 100ms
- [ ] Scrolling is smooth (60fps)
- [ ] No horizontal overflow or content cut-off
- [ ] Cards scale appropriately for screen size

---

## Post-Sensor Integration Tests

Run these tests after pairing sensors (when hardware arrives).

### Sensor Data

- [ ] `binary_sensor.bedroom_motion` updates on movement
- [ ] `binary_sensor.bedroom_presence` detects presence
- [ ] `sensor.bedroom_temperature` shows realistic temperature
- [ ] `sensor.bedroom_humidity` shows realistic humidity
- [ ] `binary_sensor.living_room_motion` updates on movement
- [ ] `sensor.living_room_temperature` shows realistic temperature
- [ ] `sensor.living_room_humidity` shows realistic humidity
- [ ] All door/window sensors toggle correctly

### Sensor Cards

- [ ] Temperature displays in room cards update
- [ ] Humidity displays in room cards update
- [ ] Motion-triggered cards appear when motion detected
- [ ] Climate tab shows temperature/humidity graphs
- [ ] Active tab shows open doors/windows

### Smart Plugs

- [ ] `switch.bedroom_plug` toggles on/off
- [ ] `switch.kitchen_plug` toggles on/off
- [ ] `switch.living_room_plug` toggles on/off
- [ ] `switch.desk_plug` toggles on/off
- [ ] Power consumption displays (if supported by plug)

---

## Validation Sign-Off

| Test Category | Pass/Fail | Date | Notes |
|---------------|-----------|------|-------|
| Pre-Deployment | | | |
| Configuration | | | |
| Dashboard Navigation | | | |
| Overview Page | | | |
| Room Views | | | |
| Theme & Styling | | | |
| HACS Cards | | | |
| Animations | | | |
| Performance | | | |
| Git Repository | | | |
| Post-Sensor (when ready) | | | |

**Tested By**: ____________________
**Date**: ____________________
**Dashboard Version**: 1.0
**HA Version**: ____________________
