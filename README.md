A modern Home Assistant dashboard built on Material Design 3 (MD3) principles, featuring dynamic colors, transparent and adaptive card layouts, and a sleek, clean UI for an elegant smart home experience. 

This comprehensive dashboard unifies control and monitoring for **lights, switches, temperature and humidity sensors, rainfall, wind, UV index, radar, weather forecasts, alarms, Hue scenes, cameras, heat pumps, door and window sensors, and irrigation control** - all presented in one cohesive, visually refined interface designed for both functionality and aesthetic harmony.

[_v.3.3.0_](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/releases/tag/v.3.3.0) The latest update includes several enhancements for improved usability and monitoring: a device status summary now shows the count of lights, switches, windows, and doors left open; room-specific pop-up cards reduce scrolling and simplify navigation; the weather panel has been refreshed with a more informative card; the irrigation panel now displays soil moisture and temperature data; and overall performance has been improved through decluttering templates for faster and more responsive app experience.

# ✨ Features

**🎨 MD3 Theme Engine**

Unlock unlimited color combinations with a simple color picker - thanks to the amazing work of Material You Theme repository.

**👥 Per-User Styling**

Each family member can have their own unique style and colors. Perfect for customizing your phone, tablets, and shared devices.


**💡Community Inspired**

Several cards are inspired by the incredible work of others in the Home Assistant community. Credit will be detailed below.

# 🖼️ Dashboard Walkthrough

<img width="1920" height="1080" alt="7" src="https://github.com/user-attachments/assets/82c34a8d-7574-47f8-b06f-5ddc0526b22b" />


**Overview Page**

The Overview page gives you a quick glance and control of what matters most to you. It starts by showing the date and time of the day, your alarm status, and a notification bell that highlights what’s important.
In this example, I have three notifications: Rubbish Day with a live camera feed that shows whether I’ve put the rubbish out or not, a reminder for chores, and a timer. I also have other items that can increase the count, such as the dryer, washer, and more.

**Weather Forecast Overview**

Next is the weather forecast section, which provides an overview of the current conditions, temperature, wind speed, and the day’s high and low temperatures.
When any of the colored buttons is clicked, a detailed weather panel will pop up - this will be explained later.

**Home Tab**

Moving down, there are three tabs that help you navigate through different areas.
In the Home tab, you can see the inside vs. outside temperature and manage climate control.
Below that is a swipeable area where I can place toggles for quick access - these can include booleans, automations, or any other types of toggles.

**Environment Tab**

The Environment tab gives an overview of the temperature and humidity levels for each area where I’ve placed sensors.

**Active Tab**

The Active tab is controlled by a template condition and only appears when any of the following are turned on or open:

- Lights

- Light Switches

- Door

- Windows

**Calendar & Navigation**

Lastly, there’s a calendar agenda, which is partially covered by the Now Playing music button. Clicking this button opens a large media card for full playback controls.
Below that, a floating navigation bar allows you to move freely between different pages.

<img width="1920" height="1080" alt="8" src="https://github.com/user-attachments/assets/6b51ad87-fe74-4fea-9d20-abe5b79864c0" />

**Room Card Overview**

The Room Card Overview gives you a snapshot of each room’s temperature and humidity level, highlighted by the color of the card itself. Each card includes up to four quick-action buttons for controls like climate, lighting, and door or window status.
Clicking the room’s name takes you directly to that room’s individual page.

**Individual Room Page**

The individual room page starts with a header displaying the room’s temperature, occupancy status, and the last time it was active.
Below that are quick buttons for toggling features such as room presence automation or activating Movie Mode (as shown in this example).

Further down, there are three tabs:

- Room Tab: Contains light entities and a popup card for additional lights, as well as other elements like covers, media, or anything else relevant to the room.

- Climate Tab: Displays climate controls for the room and shows humidity levels. In this example, the humidity is too high, so the indicator color appears red.

- Active Tab: This tab only appears when something in the room is active - such as an open door or window, or a switch that’s turned on.

<img width="1920" height="1080" alt="9" src="https://github.com/user-attachments/assets/3a01207e-4dba-42c5-a1d0-0726f7ea78e0" />

**Lighting Control**

I love Philips Hue, but I decided not to use the bridge. Instead, I connected the lights directly to Zigbee2MQTT (Z2M) and rely on [Hass Scene Preset](https://github.com/Hypfer/hass-scene_presets) to make the effects work without the bridge.
To activate a scene, I simply click the image representing the effect and select a room. This setup is made possible using a combination of powerful HACS components, automations, scripts, input booleans, input_number, and input texts. Check this [folder](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/hue%20asset) to set it up.

**Camera + Timeline**

The Camera + Timeline page displays live camera feeds from each area, showing the last detected activity along with controls for nearby lights for quick actions.
The timeline view is powered by an [LLM Vision](https://llmvision.org/), which automatically generates short descriptions for detected events - displaying up to 10 events at a time.

<img width="1920" height="1080" alt="10" src="https://github.com/user-attachments/assets/3be47a8b-17c9-459b-b70c-04f118d572f2" />
<img width="1920" height="1080" alt="11" src="https://github.com/user-attachments/assets/a011c45d-9ef5-4738-85f8-0bf686def53f" />

**Comprehensive Weather Panel**

The comprehensive weather panel is a popup card accessible by clicking any of the weather forecast buttons at the top of the Overview page (as mentioned earlier).
Some tabs may be hidden when there are no active events - for example, if there are no earthquakes or volcanic activities at the moment.

This panel includes the following components:

- Earthquake
- Volcano
- Warning
- Weather Forecast
- Rainfall
- UV
- Wind
- Radar
 -Lunar

Each section highlights the next significant forecasted event.
For example, the Wind section displays when the strongest forecasted wind is expected and its intensity, while the chart below shows the current wind speed in real time.

<img width="1920" height="1080" alt="12" src="https://github.com/user-attachments/assets/9a22ae61-fcf0-4879-bb24-a0e104b5f0ae" />

**Media Player**

A large media player displays the current music that’s playing, providing quick access to playback controls and track details.

**Irrigation**

The Irrigation page shows the current weather restriction level, along with tabs for different irrigation zones. It includes details such as each zone’s water valve status, the last run time, and direct controls for each valve - all presented with a clear, visually rich graph.

Below that, the system displays soil moisture levels, color-coded according to dryness, as well as the soil temperature for each zone.

Additionally, automations and scripts are used to control the valves, including phone notifications when the sprinklers turn on or off.

**Server Overview**

The Server Overview provides system performance data and graphs, including Home Assistant updates, CPU usage, memory consumption, network speed, and more - giving a complete snapshot of your server’s health and activity.


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
- [Mediocre Hass Media Player Cards](https://github.com/antontanderup/mediocre-hass-media-player-cards)
- [Mini-Graph-Card](https://github.com/kalkih/mini-graph-card)
- [Mushroomn](https://github.com/piitaya/lovelace-mushroom)
- [Navbar Card](https://github.com/joseluis9595/lovelace-navbar-card)
- [Simple Swipe Card](https://github.com/nutteloost/simple-swipe-card)
- [Simple Tabs Card](https://github.com/agoberg85/home-assistant-simple-tabs)
- [Timer Bar Card](https://github.com/rianadon/timer-bar-card)
- [Web RTC Camera](https://github.com/AlexxIT/WebRTC)
- [Weather Card Extended](https://github.com/Thyraz/weather-forecast-extended) - new in v3.3.0

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
- [Lunar Phase Integration](https://github.com/ngocjohn/lunar-phase)
- [World's Air Quality Index](https://www.home-assistant.io/integrations/waqi/)

Removed in v3.2.0:
- [MetService New Zealand Weather](https://github.com/ciejer/metservice-weather)

# Installation

- Create a blank dashboard to start fresh (optional) or copy some part of the codes or full codes from  [full_YAML](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/full_yaml) into your Home Assistant dashboard.
- Install the required HACS components (such as simple swipe card, stack-in-card, popup-card, etc. - see your setup for what’s needed).
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

If you want to hire me to make your personal dashboard, you can hit me up on one of these social media platforms below:
- [Discord](https://discord.gg/5tVugEbd)
- Email at  _reynaldi.sutrisno.rs16@gmail.com_
- [Reddit](https://www.reddit.com/u/ElementZoom/s/dr4NN0mTtj)
- [Facebook](https://www.facebook.com/profile.php?id=61578092475703)

Or you can support me on [Ko-fi](https://ko-fi.com/ElementZoom).
Your support helps me keep creating and sharing more awesome open-source tools! Thank you for being part of this journey 🚀
