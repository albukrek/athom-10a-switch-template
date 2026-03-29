# Athom 10A Switch (CB0110A) – ESPHome Template

A universal ESPHome configuration for **Athom 10A switch modules** (CB0110A‑like boards) using ESP8285 / ESP01.

This template is designed to work with most Athom 10A relays that originally came with Tasmota, so you can reuse it across multiple switches with minimal changes.

## What this template does

- **GPIO mapping (Athom CB0110A‑style)**
  - GPIO4 as the **LED indicator** (`Led_i 1`, inverted).  
  - GPIO3 as the **physical button** (pull‑up + inverted).  
  - GPIO13 as the **10A relay output**.

- **Features**
  - ESPHome API (`api`) for Home Assistant integration.  
  - OTA updates (`ota`) with password‑protected firmware push.  
  - Built‑in web server on port 80 (`web_server`).  
  - WiFi status feedback via LED:
    - Solid off when Wi‑Fi is connected and relay is off.  
    - On when relay is on and Wi‑Fi is connected.  
    - Fast blinking when the device has **lost Wi‑Fi** (helps see that it’s not online).

- **Extra info you get**
  - Wi‑Fi signal strength sensor.  
  - IP address (as a text sensor) for easy debugging.

## How to use this template

1. Copy `athom-10a-switch-template.yaml` into your ESPHome config folder.  
2. Open the file and edit `substitutions`:
   - `device_name` → your desired device name (for example, `garage-light-switch`).  
   - `friendly_name` → what you want it to appear as in Home Assistant.  
   - Optionally change `led_name` if you prefer a different LED name.

3. Make sure your secrets are set in `secrets.yaml` (if you use that), for:
   - `wifi_ssid`  
   - `wifi_password`  
   - `ota_password`

4. In ESPHome, compile and flash the `.bin` to your Athom 10A switch (via Tasmota OTA, serial, or ESPHome web install).

5. After flashing, the device will appear in Home Assistant and can be adopted as usual.

## Notes / limitations

- This template is designed for **ESP8285‑based Athom 10A switches** (like the CB0110A / “CB01‑TAS” family).  
- If you have a different Athom board (ESP32, multi‑channel, or wall‑touch switch), the GPIOs may differ; in that case, you can fork this project and adapt the pins.

## Contributing / sharing

If you:
- improve this template (for example, add deep sleep, power‑monitoring, or better LED logic),  
- or adapt it for another Athom board (2‑channel, wall switch, etc.),  

feel free to:
- Fork this repo.  
- Or create a **GitHub Gist** of your own variant and share the link in the ESPHome / Home Assistant communities.

---

Maintained by: Arik Albuklrek
