# HACS Dependencies

Complete list of all HACS frontend cards and custom components required by the Material Design 3 Dynamic Mobile Dashboard.

---

## Overview

| Category | Count | Status |
|----------|-------|--------|
| Core Cards (Tier 1) | 4 | Required |
| Layout & Structure (Tier 2) | 6 | Required |
| UI Components (Tier 3) | 5 | Required |
| Data & Media (Tier 4) | 7 | Required |
| Optional/Feature-Specific (Tier 5) | 7 | As needed |
| Custom Components | 1 | Optional |
| **Total** | **30** | |

---

## Tier 1: Core Cards (Install First)

These cards form the foundation of the dashboard. Install them before anything else.

### 1. Mushroom Cards

| Field | Value |
|-------|-------|
| **HACS Name** | Mushroom |
| **Repository** | [piitaya/lovelace-mushroom](https://github.com/piitaya/lovelace-mushroom) |
| **Card Type** | Frontend |
| **Used For** | Primary card framework - clean, modern card designs for entities |
| **Dashboard Usage** | Extensively used for entity cards, chips, and control interfaces |
| **Required** | Yes - critical dependency |

### 2. Card-Mod

| Field | Value |
|-------|-------|
| **HACS Name** | card-mod |
| **Repository** | [thomasloven/lovelace-card-mod](https://github.com/thomasloven/lovelace-card-mod) |
| **Card Type** | Frontend |
| **Used For** | CSS styling customization for all cards |
| **Dashboard Usage** | Applied to nearly every card for MD3 visual consistency |
| **Required** | Yes - critical dependency |

### 3. Streamline Card

| Field | Value |
|-------|-------|
| **HACS Name** | Streamline Card |
| **Repository** | [brunosabot/streamline-card](https://github.com/brunosabot/streamline-card) |
| **Card Type** | Frontend |
| **Used For** | Template card system for reusable card configurations |
| **Dashboard Usage** | 333 template instances across the entire dashboard |
| **Required** | Yes - critical dependency |

### 4. Material You Theme

| Field | Value |
|-------|-------|
| **HACS Name** | Material You Theme |
| **Repository** | [Nerwyn/material-you-theme](https://github.com/Nerwyn/material-you-theme) |
| **Card Type** | Frontend (Theme) |
| **Used For** | MD3 dynamic color theming engine |
| **Dashboard Usage** | Provides all `--md-sys-color-*` CSS variables |
| **Required** | Yes - critical dependency |

---

## Tier 2: Layout & Structure

These cards handle layout, navigation, and card organization.

### 5. Layout Card

| Field | Value |
|-------|-------|
| **HACS Name** | layout-card |
| **Repository** | [thomasloven/lovelace-layout-card](https://github.com/thomasloven/lovelace-layout-card) |
| **Card Type** | Frontend |
| **Used For** | Advanced layout control (grid, horizontal, vertical) |
| **Dashboard Usage** | Page-level layout management |
| **Required** | Yes |

### 6. Stack In Card

| Field | Value |
|-------|-------|
| **HACS Name** | stack-in-card |
| **Repository** | [custom-cards/stack-in-card](https://github.com/custom-cards/stack-in-card) |
| **Card Type** | Frontend |
| **Used For** | Grouping multiple cards into a single card container |
| **Dashboard Usage** | Card grouping throughout all views |
| **Required** | Yes |

### 7. Vertical Stack In Card

| Field | Value |
|-------|-------|
| **HACS Name** | vertical-stack-in-card |
| **Repository** | [ofekashery/vertical-stack-in-card](https://github.com/ofekashery/vertical-stack-in-card) |
| **Card Type** | Frontend |
| **Used For** | Vertical card grouping within a single card |
| **Dashboard Usage** | Room view card stacking |
| **Required** | Yes |

### 8. Simple Swipe Card

| Field | Value |
|-------|-------|
| **HACS Name** | Simple Swipe Card |
| **Repository** | [nutteloost/simple-swipe-card](https://github.com/nutteloost/simple-swipe-card) |
| **Card Type** | Frontend |
| **Used For** | Swipeable card sections for touch navigation |
| **Dashboard Usage** | Overview page swipeable sections, room toggle controls |
| **Required** | Yes |

### 9. Simple Tabs Card

| Field | Value |
|-------|-------|
| **HACS Name** | Simple Tabs Card |
| **Repository** | [agoberg85/home-assistant-simple-tabs](https://github.com/agoberg85/home-assistant-simple-tabs) |
| **Card Type** | Frontend |
| **Used For** | Tab-based content switching (Home/Events/Active tabs) |
| **Dashboard Usage** | Overview page tabs, individual room page tabs |
| **Required** | Yes |

### 10. Navbar Card

| Field | Value |
|-------|-------|
| **HACS Name** | Navbar Card |
| **Repository** | [joseluis9595/lovelace-navbar-card](https://github.com/joseluis9595/lovelace-navbar-card) |
| **Card Type** | Frontend |
| **Used For** | Floating bottom navigation bar |
| **Dashboard Usage** | Main navigation between dashboard views |
| **Required** | Yes |

---

## Tier 3: UI Components

Visual components and icon libraries.

### 11. Button Card

| Field | Value |
|-------|-------|
| **HACS Name** | button-card |
| **Repository** | [custom-cards/button-card](https://github.com/custom-cards/button-card) |
| **Card Type** | Frontend |
| **Used For** | Highly customizable interactive buttons |
| **Dashboard Usage** | Room cards, light controls, scene activation, navigation buttons |
| **Required** | Yes |

### 12. Material Symbols

| Field | Value |
|-------|-------|
| **HACS Name** | Material Symbols |
| **Repository** | [beecho01/material-symbols](https://github.com/beecho01/material-symbols) |
| **Card Type** | Frontend |
| **Used For** | Google Material Symbols icon set |
| **Dashboard Usage** | Icons throughout the dashboard for MD3 consistency |
| **Required** | Yes |

### 13. Material You Utilities

| Field | Value |
|-------|-------|
| **HACS Name** | Material You Utilities |
| **Repository** | [Nerwyn/material-you-utilities](https://github.com/Nerwyn/material-you-utilities) |
| **Card Type** | Frontend |
| **Used For** | Additional MD3 utility functions and helpers |
| **Dashboard Usage** | Color calculation and theme utilities |
| **Required** | Yes |

### 14. Lovelace Material Components

| Field | Value |
|-------|-------|
| **HACS Name** | Lovelace Material Components |
| **Repository** | [giovannilamarmora/lovelace-material-components](https://github.com/giovannilamarmora/lovelace-material-components) |
| **Card Type** | Frontend |
| **Used For** | MD3-styled UI components (sliders, switches, etc.) |
| **Dashboard Usage** | Form controls and interactive elements |
| **Required** | Yes |

### 15. Paper Buttons Row

| Field | Value |
|-------|-------|
| **HACS Name** | Paper Buttons Row |
| **Repository** | [jcwillox/lovelace-paper-buttons-row](https://github.com/jcwillox/lovelace-paper-buttons-row) |
| **Card Type** | Frontend |
| **Used For** | Button row layouts for quick actions |
| **Dashboard Usage** | Room card quick-action buttons |
| **Required** | Yes |

---

## Tier 4: Data & Media

Cards for data visualization and media control.

### 16. Mini Graph Card

| Field | Value |
|-------|-------|
| **HACS Name** | mini-graph-card |
| **Repository** | [kalkih/mini-graph-card](https://github.com/kalkih/mini-graph-card) |
| **Card Type** | Frontend |
| **Used For** | Compact sensor history graphs |
| **Dashboard Usage** | Temperature, humidity, and climate trend displays |
| **Required** | Yes |

### 17. Apex Charts Card

| Field | Value |
|-------|-------|
| **HACS Name** | apexcharts-card |
| **Repository** | [RomRider/apexcharts-card](https://github.com/RomRider/apexcharts-card) |
| **Card Type** | Frontend |
| **Used For** | Advanced interactive data charts |
| **Dashboard Usage** | Weather panel charts, irrigation graphs, wind speed charts |
| **Required** | Yes |

### 18. Auto Entities

| Field | Value |
|-------|-------|
| **HACS Name** | auto-entities |
| **Repository** | [thomasloven/lovelace-auto-entities](https://github.com/thomasloven/lovelace-auto-entities) |
| **Card Type** | Frontend |
| **Used For** | Dynamically generated entity cards based on filters |
| **Dashboard Usage** | Active tab (shows currently active entities) |
| **Required** | Yes |

### 19. Config Template Card

| Field | Value |
|-------|-------|
| **HACS Name** | config-template-card |
| **Repository** | [iantrich/config-template-card](https://github.com/iantrich/config-template-card) |
| **Card Type** | Frontend |
| **Used For** | Dynamic card configuration using templates |
| **Dashboard Usage** | Conditional card rendering |
| **Required** | Yes |

### 20. Kiosk Mode

| Field | Value |
|-------|-------|
| **HACS Name** | kiosk-mode |
| **Repository** | [maykar/kiosk-mode](https://github.com/maykar/kiosk-mode) |
| **Card Type** | Frontend |
| **Used For** | Hides header bar and sidebar for full-screen display |
| **Dashboard Usage** | Mobile-optimized full-screen experience |
| **Required** | Yes (for intended mobile experience) |

### 21. Mediocre Media Player Cards

| Field | Value |
|-------|-------|
| **HACS Name** | Mediocre Hass Media Player Cards |
| **Repository** | [antontanderup/mediocre-hass-media-player-cards](https://github.com/antontanderup/mediocre-hass-media-player-cards) |
| **Card Type** | Frontend |
| **Used For** | Enhanced media player card with now-playing display |
| **Dashboard Usage** | Now Playing card, media controls in room views |
| **Required** | Yes |

### 22. My Cards Bundle

| Field | Value |
|-------|-------|
| **HACS Name** | My Cards Bundle |
| **Repository** | [AnthonMS/my-cards](https://github.com/AnthonMS/my-cards) |
| **Card Type** | Frontend |
| **Used For** | Collection of utility cards (slider, popup, etc.) |
| **Dashboard Usage** | Popup card functionality, slider controls |
| **Required** | Yes |

---

## Tier 5: Optional / Feature-Specific

Install these based on which features you plan to use.

### 23. Alarmo Card

| Field | Value |
|-------|-------|
| **HACS Name** | Alarmo Card |
| **Repository** | [nielsfaber/alarmo-card](https://github.com/nielsfaber/alarmo-card) |
| **Card Type** | Frontend |
| **Used For** | Alarm control panel interface |
| **Dashboard Usage** | Alarmo popup card in Overview (currently commented) |
| **Required** | Only if using Alarmo alarm integration |

### 24. Bubble Card

| Field | Value |
|-------|-------|
| **HACS Name** | Bubble Card |
| **Repository** | [Clooos/Bubble-Card](https://github.com/Clooos/Bubble-Card) |
| **Card Type** | Frontend |
| **Used For** | Pop-up cards with animations and floating buttons |
| **Dashboard Usage** | Pop-up card system for notifications, music, alarmo |
| **Required** | Yes (used for pop-up functionality) |

### 25. Calendar Card Pro

| Field | Value |
|-------|-------|
| **HACS Name** | Calendar Card Pro |
| **Repository** | [alexpfau/calendar-card-pro](https://github.com/alexpfau/calendar-card-pro) |
| **Card Type** | Frontend |
| **Used For** | Google Calendar event display |
| **Dashboard Usage** | Events tab on Overview page |
| **Required** | Only if using calendar integrations |

### 26. Timer Bar Card

| Field | Value |
|-------|-------|
| **HACS Name** | Timer Bar Card |
| **Repository** | [rianadon/timer-bar-card](https://github.com/rianadon/timer-bar-card) |
| **Card Type** | Frontend |
| **Used For** | Visual timer progress bars |
| **Dashboard Usage** | Active timers in notification center |
| **Required** | Only if using timer entities |

### 27. WebRTC Camera

| Field | Value |
|-------|-------|
| **HACS Name** | WebRTC Camera |
| **Repository** | [AlexxIT/WebRTC](https://github.com/AlexxIT/WebRTC) |
| **Card Type** | Frontend + Integration |
| **Used For** | Low-latency camera streaming |
| **Dashboard Usage** | Camera view, notification camera feeds |
| **Required** | Only if using security cameras |

### 28. Lunar Phase Card

| Field | Value |
|-------|-------|
| **HACS Name** | Lunar Phase Card |
| **Repository** | [ngocjohn/lunar-phase-card](https://github.com/ngocjohn/lunar-phase-card) |
| **Card Type** | Frontend |
| **Used For** | Moon phase visualization |
| **Dashboard Usage** | Weather panel - Lunar tab |
| **Required** | Only if using weather panel |

### 29. Weather Forecast Extended

| Field | Value |
|-------|-------|
| **HACS Name** | Weather Forecast Extended |
| **Repository** | [Thyraz/weather-forecast-extended](https://github.com/Thyraz/weather-forecast-extended) |
| **Card Type** | Frontend |
| **Used For** | Extended weather forecast display |
| **Dashboard Usage** | Weather panel - Forecast tab |
| **Required** | Only if using weather panel |

---

## Custom Components (Non-Frontend)

### 30. Scene Presets

| Field | Value |
|-------|-------|
| **HACS Name** | Scene Presets |
| **Repository** | [Hypfer/hass-scene_presets](https://github.com/Hypfer/hass-scene_presets) |
| **Card Type** | Integration (custom component) |
| **Used For** | Philips Hue dynamic scene effects without Hue bridge |
| **Dashboard Usage** | Scenes view (currently commented with 🔜) |
| **Required** | Only if using Hue scene effects |
| **Install Via** | HACS > Integrations > Custom Repositories |

---

## Weather Integrations (Native HA)

These are native Home Assistant integrations, not HACS cards:

| Integration | URL | Used For |
|-------------|-----|----------|
| Lunar Phase | [ngocjohn/lunar-phase](https://github.com/ngocjohn/lunar-phase) | Lunar data for weather panel |
| World Air Quality Index | [Built-in](https://www.home-assistant.io/integrations/waqi/) | Air quality monitoring |

---

## Installation Verification

After installing all cards, verify the installation:

### Quick Check

1. Navigate to any dashboard page
2. Open browser DevTools (F12) > Console
3. No "Custom element doesn't exist" errors should appear

### Card-by-Card Verification

You can verify individual cards are loaded by checking in DevTools Console:

```javascript
// Check if a card is registered
customElements.get('mushroom-entity-card')  // Should not be undefined
customElements.get('hui-button-card')       // Built-in card
```

### Troubleshooting Installation Issues

| Problem | Solution |
|---------|----------|
| Card not found in HACS | Add as custom repository manually |
| Card installed but not loading | Clear browser cache, hard refresh (Ctrl+Shift+R) |
| "Custom element doesn't exist" | Restart HA, then refresh browser |
| HACS shows update but card is current | Re-download the card from HACS |
| Card causes dashboard error | Check HACS for card updates, check card's GitHub Issues |

### Adding Custom Repositories

If a card is not found in the default HACS repository:

1. Open HACS > Frontend
2. Click the three dots menu (top right)
3. Select **Custom repositories**
4. Paste the GitHub URL
5. Select category: **Lovelace**
6. Click **Add**
7. The card will appear in the download list
