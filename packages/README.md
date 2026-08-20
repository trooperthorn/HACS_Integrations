# Home Assistant Usability Pack

A set of **packages** (helpers + scripts + automations) built from your installed
integrations and entity types. Each package is self-contained and can be enabled
or removed independently.

## Installation

1. Enable packages in `configuration.yaml`:

   ```yaml
   homeassistant:
     packages: !include_dir_named packages
   ```

2. Copy the `packages/` folder into your Home Assistant `config/` directory.

3. **Replace the placeholder entity IDs.** Every entity referenced in these files
   uses a descriptive placeholder (e.g. `sensor.airthings_living_room_radon`,
   `valve.phyn_main_water`). Search each file for `# TODO:` comments and swap in
   your real entity IDs (Developer Tools → States is the quickest way to find them).

4. Restart Home Assistant, or run **Developer Tools → YAML → Reload All YAML**.

## What's included

| Package | Integrations used | What it does |
| :--- | :--- | :--- |
| `helpers.yaml` | — | Modes (guest/vacation/quiet hours), thresholds you can tune from the UI, utility meters for daily/monthly energy |
| `safety.yaml` | Kidde HomeSafe, HomeKit Controller, UniFi Protect, Z-Wave JS | Smoke/CO emergency response: lights on, media off, everyone notified, TTS announcement |
| `water.yaml` | Phyn, Davis Vantage, Mopeka | Leak → auto shut-off valve + notify; freeze protection; propane tank low warning |
| `air_quality.yaml` | Airthings | Radon, CO₂, and VOC alerts with hysteresis; daily air quality summary |
| `energy.yaml` | Emporia Vue, SolarEdge, Forecast Solar, Powercalc, Shelly | High-usage alerts, solar production summary, "good time to run appliances" notification |
| `presence_security.yaml` | SleepIQ / Sleep Number, Z-Wave JS locks, ESPHome garage, Group, Keymaster, Mobile App, Proximity | Everyone-in-bed → house lockdown; garage/door left open alerts; welcome-home routine |
| `climate_comfort.yaml` | SwitchBot, Z-Wave JS covers, WeatherFlow, Sun | Sun/temperature-driven curtain + shade control, lux-based positions |
| `media.yaml` | Cast, Android TV Remote, Samsung TV, Yamaha YNCA, Monoprice, UniFi Protect | Movie-time script, whole-home announce script, auto-off for idle receivers |
| `maintenance.yaml` | Backup, Google Drive, System Monitor, Uptime Kuma, Mobile App, ESPHome / Shelly / UniFi / Phyn / Z-Wave JS updates, Bermuda / Govee BLE | Low-battery digest, stale-backup alert, firmware update digest, disk-space warning, phone-battery reminder |
| `commute.yaml` | Waze Travel Time, Mobile App | Leave-now notification when the commute is slow |

## Conventions used

- **Modern trigger syntax** (`triggers:` / `conditions:` / `actions:`, HA 2024.10+).
  If you're on an older release, rename to `trigger:` / `condition:` / `action:`
  and `platform:` instead of `trigger:` inside each trigger.
- All notifications go through `notify.notify` (your Mobile App devices). Change to a
  specific service such as `notify.mobile_app_your_phone` if you want targeting.
- Alerts that could fire repeatedly use `input_number` thresholds + hysteresis or
  `for:` durations to avoid spam.
- `mode: single` unless an automation must queue or restart.



I built a complete Home Assistant "usability pack" from your integration list and pushed it to the 10 package files plus a README.

What's in it (each package is a self-contained YAML file using modern HA 2024.10+ triggers:/actions: syntax):

- helpers.yaml — Guest/vacation/quiet-hours mode toggles, UI-tunable alert thresholds (CO₂, radon, power, battery, propane), a "lowest battery" template sensor, and utility meters for daily/monthly energy from your Emporia Vue and SolarEdge sensors.
- safety.yaml — A group of all Kidde/HomeKit/UniFi Protect smoke and CO sensors; on trigger it turns every light on, kills media, sends critical push notifications (bypasses Do Not Disturb), announces evacuation over your Cast speakers, and unlocks the Z-Wave locks. Also alerts on detector faults and an all-clear.
- water.yaml — Leak from Phyn or Davis moisture → automatically closes the Phyn valve; 20-minute continuous flow while nobody's home → actionable notification with a "Shut off water" button; freeze warnings from WeatherFlow temperature; Mopeka propane-low alert.
- air_quality.yaml — Airthings CO₂/radon/VOC alerts with hysteresis and recovery confirmations (radon uses a 6-hour hold so it never alerts on blips), plus a daily morning air-quality summary.
- energy.yaml — High-draw alert, a "solar surplus" binary sensor that pings you once a day when panels out-produce the house (good time for laundry/EV charging), an evening usage report with the Forecast Solar prediction, and Shelly fault alerts.
- presence_security.yaml — The big one: SleepIQ bed occupancy for both sides after 21:30 runs a Goodnight script (lights, media, locks, curtains, garage) exactly once per night via a latch; door/window-group open-at-bedtime check; garage-left-open with a "Close it" button; Proximity-based welcome home; last-person-leaves lockdown; UniFi Protect motion-while-away with camera snapshots.
- climate_comfort.yaml — SwitchBot curtains and Z-Wave shades driven by sunrise/sunset and WeatherFlow illuminance + heat (drops shades on hot bright afternoons), plus vacation-mode presence simulation.
- media.yaml — Movie time / movie over scripts (Yamaha + Samsung TV + dim lights + curtains), a quiet-hours-aware whole-home announce script, a Monoprice multi-zone party preset, auto-off for idle receivers, and TV auto-pause when the doorbell camera sees a person.
- maintenance.yaml — Saturday digests for low batteries and pending firmware updates (covers ESPHome, Shelly, UniFi, Phyn, Z-Wave JS automatically via the update domain), stale-backup alert tied to Google Drive, System Monitor disk warning, Uptime Kuma service-down alerts, Nabu Casa cloud-offline alert, and a phone-battery-low-while-away nudge.
commute.yaml — Checks Waze 45 minutes before your configured departure time on workdays and tells you how early to leave if traffic is 30%+ worse than normal.
One setup step matters: the files use descriptive placeholder entity IDs since I couldn't know your real ones. Search the files for # TODO: comments and swap in your actual entity IDs (Developer Tools → States), then enable packages: !include_dir_named packages in configuration.yaml — the README walks through it. All files are YAML-validated.
