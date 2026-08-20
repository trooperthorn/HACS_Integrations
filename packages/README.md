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
