A modern Home Assistant dashboard built on Material Design 3 (MD3) principles, featuring dynamic colors, transparent and adaptive card layouts, and a sleek, clean UI for an elegant smart home experience. 

This comprehensive dashboard unifies control and monitoring for **lights, switches, temperature and humidity sensors, rainfall, wind, UV index, radar, weather forecasts, alarms, Hue scenes, cameras, heat pumps, door and window sensors, and irrigation control** - all presented in one cohesive, visually refined interface designed for both functionality and aesthetic harmony.

This update aligns the mobile experience with the previously shared tablet layout, using the same updated structures and design patterns.

[_v4.2.0 release_](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/releases/tag/v4.2.0) focuses on visual flexibility and customization. With full dark and light mode support, refreshed wallpapers, and improved color logic across buttons and chip cards, the dashboard now adapts more naturally to different themes. We’ve also expanded streamline_templates to give you more control over icons and states when customizing your setup.

I have also readded the _[full dashboard yaml](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/dashboard.yaml)_, one of the most requested feature over the communities.

# ✨ Features

**🎨 MD3 Theme Engine**

Unlock unlimited color combinations with a simple color picker - thanks to the amazing work of Material You Theme repository.

**👥 Per-User Styling**

Each family member can have their own unique style and colors. Perfect for customizing your phone, tablets, and shared devices.

**💡Community Inspired**

Several cards are inspired by the incredible work of others in the Home Assistant community. Credit will be detailed below.

# 🖼️ Dashboard Walkthrough

<img width="1920" height="1080" alt="Untitled design" src="https://github.com/user-attachments/assets/3476388b-ce66-4ca3-9fc9-9f4a709dc188" />


**Overview Page**


The Overview page gives you a quick view and control of what matters most. At the top, it displays the [current date and time, your alarm status, and a notification bell](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/greeting%2C%20alarmo%2C%20and%20notification%20bell) that highlights important alerts.

Next, there is a [personalized greeting](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/personalized%20greeting%20example) with current weather temperature and condition, including wind speed, high and low temp.
Below it, there are [three tabs: Home, Events, and Active](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/overview%20page%20tab).

**_Home Tab_**

The Home tab features cards designed for quick interaction. The first card shows indoor and outdoor temperatures with built-in climate controls in a clean, unified layout. Below this is a swipeable section where you can toggle room occupancy for climate control, room presence for lighting, and security cameras for quick on/off. These controls are used daily to interact with the backend automations. 

Underneath, there’s a “Now Playing” music card and a [floating navigation bar](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/assets). The calendar is hidden behind this bar and can be accessed by swiping on the screen.

**_Events Tab_**

The Environment tab provides Google Calendar events from multiple calendar sources.

**_Active Tab_**

The Active tab filters and displays entities that are currently on or active. For example, it can show lights left on, open doors, and other active devices such lights, doors, windows, fans, light swiches, and curtains.

<img width="1920" height="1080" alt="2" src="https://github.com/user-attachments/assets/72b46932-4eb4-45bb-a0e6-3d9a1a318460" />


**Pop Up Cards**

Pop-up cards are hidden within the Overview page and appear when you tap specific buttons or cards.

The [Now Playing music card](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/now%20playing%20pop%20up%20card) can be accessed by tapping the floating music control mentioned earlier.
The [Notifications card](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/notification%20center%20example) displays important items defined in your templates.yaml, such as chore management, active timers, live camera feeds when a door is opened, and sprinkler status.
The [Alarmo card](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/alarmo%20card%20example) is opened by tapping the alarm icon in the top-right corner, allowing you to quickly arm or disarm the alarm system.

<img width="1920" height="1080" alt="3" src="https://github.com/user-attachments/assets/bebcf071-fe25-4b25-81c8-e15757413009" />

**Room Card Overview**

[The Room Card Overview](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/Room%20Card%20example) gives you a quick snapshot of each room’s temperature and humidity, with the card color dynamically reflecting the current room status. Each card includes up to four customizable quick-action buttons for controls such as climate, lights, windows, doors, curtains, and fans. Tapping the room name takes you directly to that room’s dedicated page.

v4.1.0 introduces streamlined [room toggle controls](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/Room%20selector%20toggle), allowing you to quickly switch between rooms without needing to swipe through long lists. This significantly improves usability in larger homes with 10+ rooms, where excessive scrolling previously became cumbersome. This will require [input_boolean](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/room%20toggle%20input_boolean), [automation](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/room%20toggle%20automation), and [script](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/room%20toggle%20script).

<img width="1920" height="1080" alt="4" src="https://github.com/user-attachments/assets/43d77496-9d59-43ca-b49a-7f02c60e5c5b" />

**Lighting Control**

I love Philips Hue, but I decided not to use the bridge. Instead, I connected the lights directly to Zigbee2MQTT (Z2M) and rely on [Hass Scene Preset](https://github.com/Hypfer/hass-scene_presets) to make the effects work without the bridge.
To activate a scene, I simply click the [image representing the effect](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/hue%20scene%20image%20example) and select a room. This setup is made possible using a combination of powerful HACS components, automations, scripts, input booleans, input_number, and input texts. Check this [folder](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/hue%20asset) to set it up.

<img width="1920" height="1080" alt="5" src="https://github.com/user-attachments/assets/479330eb-2234-419e-844b-8f2c8637e16c" />

**Individual Room Page**

I have transitioned away from dedicated room sections in favor of a Boolean-triggered Popup system. Now, for the above example, I have three buttons to show / hide more contents (Other Lights, Kitchen, Media) that stay hidden until called upon, keeping the main view focused.
Further down, there are [three tabs](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/individual%20room%20page%20tabs):

- Room Tab: Contains light entities and a popup card for additional lights, as well as other elements like covers, media, switch, or anything else relevant to the room.

- Climate Tab: Displays climate controls for the room and shows humidity levels. In this example, the humidity is too high, so the indicator color appears red.

- Active Tab: This tab only appears when something in the room is active - such as an open door or window.

<img width="1920" height="1080" alt="7" src="https://github.com/user-attachments/assets/f0708e53-fc84-4068-915f-ae4a233e0b5d" />

<img width="1920" height="1080" alt="8" src="https://github.com/user-attachments/assets/4ad91fdc-9814-4558-b82d-15a0949f1cbd" />


**Weather Panel**

The [comprehensive weather panel](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/weather%20panel) is a popup card accessible by clicking any of the weather forecast buttons at the top of the Overview page (as mentioned earlier).
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

<img width="1920" height="1080" alt="9" src="https://github.com/user-attachments/assets/4b3454c9-9dc4-4ca5-88c4-b5ef8d60967e" />

**Camera**

The [Cameras](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/camera%20tabs%20example) displays live camera feeds from each area, showing the last detected activity along with controls for nearby lights for quick actions.

**Irrigation**

The irrigation page shows the current weather restriction level, along with [tabs for different irrigation zones](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/irrigation%20page). It includes details such as each zone’s water valve status, the last run time, and direct controls for each valve - all presented with a clear, visually rich graph.

Below that, the system displays soil moisture levels, color-coded according to dryness, as well as the soil temperature for each zone.

Additionally, automations and scripts are used to control the valves, including phone notifications when the sprinklers turn on or off.



**Server Overview**

The Server Overview provides [system performance data and graphs](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/server%20visuals), including Home Assistant updates, CPU usage, memory consumption, network speed, and more - giving a complete snapshot of your server’s health and activity.



# 🚀 Requirements / Dependencies

Card Related Stuffs:
- [Alarmo Card](https://github.com/nielsfaber/alarmo-card)
- [Apex Charts Card](https://github.com/RomRider/apexcharts-card?tab=readme-ov-file#series-options)
- [Bubble Card](https://github.com/Clooos/Bubble-Card)
- [Button-Card](https://github.com/custom-cards/button-card)
- [Calendar Card Pro](https://github.com/alexpfau/calendar-card-pro)
- [Expander Card](https://github.com/MelleD/lovelace-expander-card/tree/main/examples)
- [LLM Vision Card](https://github.com/valentinfrlch/llmvision-card)
- [Mediocre Hass Media Player Cards](https://github.com/antontanderup/mediocre-hass-media-player-cards)
- [Mini-Graph-Card](https://github.com/kalkih/mini-graph-card)
- [Mushroom](https://github.com/piitaya/lovelace-mushroom)
- [Navbar Card](https://github.com/joseluis9595/lovelace-navbar-card)
- [Simple Swipe Card](https://github.com/nutteloost/simple-swipe-card)
- [Simple Tabs Card](https://github.com/agoberg85/home-assistant-simple-tabs)
- [Timer Bar Card](https://github.com/rianadon/timer-bar-card)
- [Web RTC Camera](https://github.com/AlexxIT/WebRTC)

Theming / ETC:
- [Auto-Entities](https://github.com/thomasloven/lovelace-auto-entities)
- [Card-Mod](https://github.com/thomasloven/lovelace-card-mod)
- [Config Template Card](https://github.com/iantrich/config-template-card)
- [Kiosk Mode](https://github.com/maykar/kiosk-mode)
- [Layout-Card](https://github.com/thomasloven/lovelace-layout-card)
- [Lovelace Material Components](https://github.com/giovannilamarmora/lovelace-material-components)
- [Material Symbols](https://github.com/beecho01/material-symbols)
- [Material You Theme](https://github.com/Nerwyn/material-you-theme)
- [Material You Utilities](https://github.com/Nerwyn/material-you-utilities)
- [My Cards Bundle](https://github.com/AnthonMS/my-cards)
- [Paper Buttons Row](https://github.com/jcwillox/lovelace-paper-buttons-row)
- [Stack In Card](https://github.com/custom-cards/stack-in-card)
- [Streamline Card](https://github.com/brunosabot/streamline-card)
- [Scene Presets](https://github.com/Hypfer/hass-scene_presets)
- [Vertical Stack In Card](https://github.com/ofekashery/vertical-stack-in-card)

Weather Related:
- [Lunar Phase Card](https://github.com/ngocjohn/lunar-phase-card)
- [Lunar Phase Integration](https://github.com/ngocjohn/lunar-phase)
- [World's Air Quality Index](https://www.home-assistant.io/integrations/waqi/)
- [Weather Card Extended](https://github.com/Thyraz/weather-forecast-extended)
- [Clock Weather Card HUI Icons](https://github.com/pkissling/clock-weather-card)

# Installation

**For new user:**
- Copy all the code from _[full dashboard yaml](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/dashboard.yaml)_ to a new dashboard raw configuration editor to jumpstart your experience.
- Install the required HACS components (such as simple swipe card, stack-in-card, popup-card, etc. - see your setup for what’s needed).
- To unlock the full functionality (like weather icons, notification counts, and more), you’ll need to add the corresponding [sensors](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/template%20sensor) to your config.
- For the Hue scene, you'll need to have the automation, scripts, input boolean, input text, and input number in your system that you can find in [hue asset folder](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/hue%20asset). For the images, you can get them from [here](https://github.com/Hypfer/hass-scene_presets/blob/master/custom_components/scene_presets/assets/Readme.md).
- Apply the MD3 theme and select your preferred colors. It is accessible from Overview page > More > Bucket Fill Icon
- Apply [wallpaper](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/wallpaper/) (optional)
- Set the companion app to full screen (optional)

**For existing user:**
- Review the [streamline_template](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/blob/main/assets/streamline_templates) to see if you want to add / modify the previous version to the new version.
- Choose which card / visuals that you like to be added to your installation by clicking the hyperlink provided in the description above.
- Apply [wallpaper](https://github.com/ElementZoom/Material-Design-3-Dynamic-Mobile-Dashboard/tree/main/wallpaper/) (optional)
- Set the companion app to full screen (optional)

# 📚 Credits

This project builds upon the work of:
- Nerwyn – [Material You Theme](https://github.com/Nerwyn/material-you-theme) & [Material You Utilities](https://github.com/Nerwyn/material-you-utilities)
- [MySmartHome](https://www.youtube.com/@My_Smart_Home) - for the new simple tabs card, button cards styling, sliders, etc
- Other community members who kindly shared their cards

# 💖 Support My Work  

If you want to hire me to make your personal dashboard, you can hit me up on one of these social media platforms below:
- Email at  _reynaldi.sutrisno.rs16@gmail.com_
- [Reddit](https://www.reddit.com/u/ElementZoom/s/dr4NN0mTtj)
- [Facebook](https://www.facebook.com/profile.php?id=61578092475703)

Or you can support me on [Ko-fi](https://ko-fi.com/ElementZoom).
Your support helps me keep creating and sharing more awesome open-source tools! Thank you for being part of this journey 🚀
