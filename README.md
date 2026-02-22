# ESP32 LED Strip Controller

A powerful and stable LED controller for ESP32 with support for 4 independent WS2812B (or compatible) LED strips.  
Features include multiple effects, scheduling, night mode, WiFi auto-reconnect with fallback AP, and persistent settings storage in EEPROM.

---

## Features

- **4 Zones** (GPIO 16, 17, 18, 19) – each with independent:
  - Brightness control
  - Speed control
  - Color selection
  - 30+ stunning effects
- **Three control modes**:
  - **Separate** – all zones independent
  - **2+3 Together** – zones 2 and 3 act as one continuous line (ideal for symmetrical layouts)
  - **All Together** – zones 1, 2, 3 synchronized, monitor (zone 4) independent
- **Monitor zone** (zone 4) – completely independent, not affected by any group mode
- **Schedule** (MSK time):
  - Set ON and OFF times
  - Lights turn off automatically, remembering previous state
- **Night mode**:
  - 23:00 – 06:00: brightness limited to 10%
  - User can override with confirmation button
- **WiFi**:
  - Connects to your network (SSID: `TP-Link`, password: `Tp13_Aqq` – change in code)
  - Auto-reconnect every 10 seconds if connection lost
  - If no connection for 20 seconds, starts fallback AP (`LED_Controller` / `12345678`)
  - Manual reconnect button in web interface
- **Persistent settings**:
  - All settings saved to EEPROM automatically 5 seconds after last change
  - Manual save button available
- **30+ Effects** including:
  - Basic: solid, rainbow, wave, fade, strobe, sparkle, fire, water, bounce, pulse, running, meteor
  - Advanced: chase, rainbowMeteor, sparkles, rainbowStripes, lightning, half, halfwave
  - Extra: sinelon, bpm, juggle, glitter, ripple, twinkle, theaterChase, confetti, noise, matrix, colorWaves
- **Modern responsive web interface**:
  - Works on phones, tablets, and desktops
  - Real-time brightness/speed sliders
  - Color picker for each zone
  - Schedule and night mode controls
  - Settings modal for LED counts

---

## Pinout

| Zone | GPIO | Description            |
|------|------|------------------------|
| 1    | 16   | Independent strip      |
| 2    | 17   | Left part of double    |
| 3    | 18   | Right part of double   |
| 4    | 19   | Monitor (independent)  |

**Important**: Connect **GND** of ESP32 to **GND** of all strips (common ground).  
Power strips from a suitable 5V power supply (current depends on LED count).

---

## Installation

1. Install [Arduino IDE](https://www.arduino.cc/en/software)
2. Add ESP32 board support (if not already):
   - File → Preferences → Additional Boards Manager URLs:  
     `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`
   - Tools → Board → Boards Manager → search "esp32" → install
3. Install required libraries:
   - **FastLED** (by Daniel Garcia)
   - **WiFi**, **WebServer**, **EEPROM** (built-in with ESP32 core)
4. Download the `.ino` file (or copy code into a new sketch)
5. Change WiFi credentials in the code if needed:
   ```cpp
   const char* ssid = "TP-Link";
   const char* password = "Tp13_Aqq";
