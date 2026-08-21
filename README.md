# HACS Integrations Index - No clouds on this sunny day

## Focus, end all Cloud connections, reverse engineer data via TCP/IP, Bluetooth, Serial, etc.

A single landing page linking to every [Home Assistant](https://www.home-assistant.io/) custom integration maintained under this account. Use it to find and install any of them through [HACS](https://hacs.xyz/).

## Why this repo isn't itself a HACS repository

HACS custom repositories are added one at a time, and each "integration" category repository may only contain **one** integration (one folder under `custom_components/`) — HACS ignores any additional ones. There is no supported way for a single HACS custom repository to automatically pull in a set of other repositories.

So this repo is a directory, not a bundle: click a link below, HACS opens with that repository pre-filled, confirm the add, and repeat for whichever integrations you want. It's still one click per integration instead of hunting down and typing each repo URL by hand.

## Integrations

| Integration | Description | Add to HACS |
|---|---|---|
| [Phyn Smart Water Assistant](https://github.com/trooperthorn/ha_int_phyn) | Realtime water flow/pressure/temperature, leak detection and valve control for Phyn Plus and Kohler H2Wise+, with optional local (LAN) access. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_phyn&category=integration) |
| [Bond Pro](https://github.com/trooperthorn/ha_int_bond) | Modernized rework of the core Bond integration (domain `bond_pro`), built toward the Platinum quality scale with reauth/reconfigure flows and a self-healing local push connection. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_bond&category=integration) |
| [Yamaha (YNCA)](https://github.com/trooperthorn/ha_int_yamaha_ynca) | Control and monitor Yamaha AV receivers over the YNCA protocol. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_yamaha_ynca&category=integration) |
| [HomeKit Controller Pro](https://github.com/trooperthorn/ha-homekit-pro) | Fork of core's `homekit_controller` (domain `homekit_controller_pro`) with a forked `aiohomekit`, installable alongside stock HomeKit Controller for a clean fallback. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha-homekit-pro&category=integration) |
| [Davis Vantage Weather](https://github.com/trooperthorn/ha_int_davis) | Davis Vantage weather station support over serial or network, with LOOP2 protocol and detailed wind rose directions. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_davis&category=integration) |
| [Elk-M1 Control](https://github.com/trooperthorn/ha_int_elkm1) | Elk-M1 Gold / M1EZ8 security and automation panel integration over network (M1XEP) or serial/USB. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_elkm1&category=integration) |
| [Monoprice 6-Zone Amplifier](https://github.com/trooperthorn/ha_int_monoprice_6chan) | Rewritten Monoprice 6-zone amplifier integration with high-speed serial comms, dynamic hardware discovery, EQ, PA and Do Not Disturb control. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_monoprice_6chan&category=integration) |
| [Emporia Vue](https://github.com/trooperthorn/ha_int_emporia) | Emporia Vue energy monitor integration with full Energy dashboard support, per-channel sensors and EV charging control. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_emporia&category=integration) |
| [Catholic Calendar](https://github.com/trooperthorn/ha_int_catholic_calendar) | Catholic liturgical calendar sensor and calendar entity, based on the Liturgical Calendar API. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha_int_catholic_calendar&category=integration) |
| [HA SmartHub COOP Electric Usage](https://github.com/trooperthorn/ha-SmartHub_coop-electric-usage) | Downloads and displays electric usage data from the BlueBonnet SmartHub portal, polled every 15 minutes. | [![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=trooperthorn&repository=ha-SmartHub_coop-electric-usage&category=integration) |

## Manual install

If a badge above doesn't work for you (e.g. you're not on the Home Assistant instance HACS is linked to), add each repository by hand instead:

1. In Home Assistant, open **HACS** → the **⋮** menu (top right) → **Custom repositories**.
2. Paste the repository URL from the table above.
3. Set **Category** to **Integration**.
4. Click **Add**, then install the integration from the HACS store as usual.

See the [HACS documentation](https://hacs.xyz/docs/faq/custom_repositories/) for more detail.
