A modern Home Assistant dashboard built on Material Design 3 (MD3) principles, featuring dynamic colors, transparent and adaptive card layouts, and a sleek, clean UI for an elegant smart home experience. 

This comprehensive dashboard unifies control and monitoring for **lights, switches, temperature and humidity sensors, rainfall, wind, UV index, radar, weather forecasts, alarms, Hue scenes, cameras, heat pumps, door and window sensors, energy monitoring, and irrigation control** — all presented in one cohesive, visually refined interface designed for both functionality and aesthetic harmony.

[_v3.2.0_](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/releases/tag/v.3.2.0) This update introduces a refreshed visual experience and several new features to make your smart home dashboard more intuitive and engaging. Enjoy seven new blurred gradient light wallpapers, a Now Playing music pop-up card, an all-new Irrigation Control page, and integrated Energy Monitoring with real-time insights. The Forecast section has been redesigned with clearer layouts and UV index details, while navigation is now smoother thanks to new title card links. The Camera section has been reworked with tab controls for faster performance, and new Template Sensors now provide more accurate device status tracking.

# ✨ Features

**🎨 MD3 Theme Engine**

Unlock unlimited color combinations with a simple color picker — thanks to the amazing work of Material You Theme repository.

**👥 Per-User Styling**

Each family member can have their own unique style and colors. Perfect for customizing your phone, tablets, and shared devices.

**📱 UI Components**

- Tab Navigations
- Light button sliders
- Other custom buttons
- Waterfall temp/humidity graphs
- Pop-up cards
- Tabs & swipe cards
- Expanders
- Gesture navigation

**💡Community Inspired**

Several cards are inspired by the incredible work of others in the Home Assistant community. Credit will be detailed below.

**🖼️ Screenshots**

<img width="1920" height="1080" alt="1" src="https://github.com/user-attachments/assets/25ba2d7d-46ff-4efc-993e-cc1a90f2816d" />
<img width="1920" height="1080" alt="2" src="https://github.com/user-attachments/assets/c3ea97af-61d6-4a18-98d0-635951fd81de" />
<img width="1920" height="1080" alt="3" src="https://github.com/user-attachments/assets/a3b7b040-5185-4b68-84da-82f25254297b" />

⚠️ Some elements are hidden due to conditional rules, so not everything is visible at once.”)

# 🚀 Requirements / Dependencies

Card Related Stuffs:
- [Alarmo Card](https://github.com/nielsfaber/alarmo-card)
- [Apex Charts Card](https://github.com/RomRider/apexcharts-card?tab=readme-ov-file#series-options)
- [Clock Weather Card HUI Icons](https://github.com/pkissling/clock-weather-card)
- [Bubble Card](https://github.com/Clooos/Bubble-Card)
- [Button-Card](https://github.com/custom-cards/button-card)
- [Calendar Card Pro](https://github.com/alexpfau/calendar-card-pro)
- [Expander-Card](https://github.com/MelleD/lovelace-expander-card)
- [LLM Vision Card](https://github.com/valentinfrlch/llmvision-card)
- [Mediocre Hass Media Player Cards](https://github.com/antontanderup/mediocre-hass-media-player-cards) - new in v3.2.0
- [Mini-Graph-Card](https://github.com/kalkih/mini-graph-card)
- [Mushroomn](https://github.com/piitaya/lovelace-mushroom)
- [Navbar Card](https://github.com/joseluis9595/lovelace-navbar-card)
- [Simple Swipe Card](https://github.com/nutteloost/simple-swipe-card)
- [Simple Tabs Card](https://github.com/agoberg85/home-assistant-simple-tabs)
- [Timer Bar Card](https://github.com/rianadon/timer-bar-card)
- [Web RTC Camera](https://github.com/AlexxIT/WebRTC)

Theming / ETC:
- [Auto-Entities](https://github.com/thomasloven/lovelace-auto-entities)
- [Card-Mod](https://github.com/thomasloven/lovelace-card-mod)
- [Config Template Card](https://github.com/iantrich/config-template-card)
- [Decluttering Card](https://github.com/custom-cards/decluttering-card)
- [Kiosk Mode](https://github.com/maykar/kiosk-mode)
- [Layout-Card](https://github.com/thomasloven/lovelace-layout-card)
- [Lovelace Material Components](https://github.com/giovannilamarmora/lovelace-material-components)
- [Material Symbols](https://github.com/beecho01/material-symbols)
- [Material You Theme](https://github.com/Nerwyn/material-you-theme)
- [Material You Utilities](https://github.com/Nerwyn/material-you-utilities)
- [My Cards Bundle](https://github.com/AnthonMS/my-cards)
- [Paper Buttons Row](https://github.com/jcwillox/lovelace-paper-buttons-row)
- [Stack In Card](https://github.com/custom-cards/stack-in-card)
- [Scene Presets](https://github.com/Hypfer/hass-scene_presets)
- [Vertical Stack In Card](https://github.com/ofekashery/vertical-stack-in-card)

Weather Related:
- [Lunar Phase Card](https://github.com/ngocjohn/lunar-phase-card)
- [Lunar Phase Integration](https://github.com/ngocjohn/lunar-phase) - new in v3.2.0
- [World's Air Quality Index](https://www.home-assistant.io/integrations/waqi/)

Removed in v3.2.0:
- [MetService New Zealand Weather](https://github.com/ciejer/metservice-weather)

# Installation

- Create a blank dashboard to start fresh (optional) or copy some part of the codes or full codes from  [full_YAML](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/full_yaml) into your Home Assistant dashboard.
- Install the required HACS components (such as simple swipe card, stack-in-card, popup-card, etc. — see your setup for what’s needed).
- You need to adjust the navbar card directory to suit your current dashboard (if you don't start fresh).
- To unlock the full functionality (like weather icons, notification counts, and more), you’ll need to add the corresponding [sensors](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/template%20sensor) to your config.
- For the Hue scene, you'll need to have the automation, scripts, input boolean, input text, and input number in your system that you can find in [hue asset folder](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/hue%20asset). For the images, you can get them from [here](https://github.com/Hypfer/hass-scene_presets/blob/master/custom_components/scene_presets/assets/Readme.md).
- Apply the MD3 theme and select your preferred colors. It is accessible from Overview page > More > Bucket Fill Icon

<img width="483" height="628" alt="image" src="https://github.com/user-attachments/assets/cd952dc4-30cd-4864-ab13-1a0c02b21e1b" />


- Select the Transparent option in Card Type to get the wide-system transparent cards
  
![Transparent Card](https://github.com/user-attachments/assets/7d0e3895-edd7-4cd3-88a0-e56f2dbc1ab5)

- Enjoy your personalized dynamic dashboard! 🎉

- Set the companion app to full screen (optional)

# 📚 Credits

This project builds upon the work of:
- Nerwyn – [Material You Theme](https://github.com/Nerwyn/material-you-theme) & [Material You Utilities](https://github.com/Nerwyn/material-you-utilities)
- [MySmartHome](https://www.youtube.com/@My_Smart_Home) - for the new simple tabs card, button cards styling, sliders, etc
- Other community members who kindly shared their cards

# 💖 Support My Work  

If you want to hire me to make your personal dashboard, you can hit me up in [Reddit](https://www.reddit.com/u/ElementZoom/s/dr4NN0mTtj)

Or you support me on [Ko-fi](https://ko-fi.com/ElementZoom).
Your support helps me keep creating and sharing more awesome open-source tools! ✨  

Thank you for being part of this journey 🚀
