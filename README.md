# 🖥️ ESP32 E-Paper Display Dashboard (ESPHome)

A minimalist **smart home status display** built with [ESPHome](https://esphome.io/) and an **ESP32** driving a **Waveshare 7.3" e-paper** panel.  
It displays **weather**, **calendar events**, and **status info** from **Home Assistant**, while consuming almost no power thanks to **deep sleep**.

---

## 🌤️ Features

- 🧠 **Home Assistant integration** – pulls weather, forecast, and calendar data.
- 📅 **2-Day weather forecast** – Today & tomorrow with icons and color accents.
- 🗓️ **Smart calendar view** – Up to 4 events with color-coded highlights.
- ⚠️ **Dynamic warnings** – Wind, UV, humidity, and storm alerts.
- 💤 **Deep sleep** – 60 min sleep / 90 s active runtime for long battery life.
- 🖋️ **Clean design** – German locale, clear typography, and subtle colors.
- 🔄 **Manual refresh** – Via hardware button or Home Assistant service.
- 🔐 **Encrypted local API + OTA updates**.

---

## 🔌 Pin Connections

| ESP32 GPIO | Function | Connected To | Notes |
|-------------|-----------|--------------|-------|
| **GPIO13** | SPI Clock (SCK) | E-Paper CLK | Shared SPI bus |
| **GPIO14** | SPI MOSI | E-Paper DIN | Shared SPI bus |
| **GPIO15** | Chip Select (CS) | E-Paper CS | Use `ignore_strapping_warning: true` |
| **GPIO27** | Data/Command (DC) | E-Paper DC | Required for control lines |
| **GPIO25** | Busy | E-Paper BUSY | Inverted logic (`inverted: true`) |
| **GPIO26** | Reset (RST) | E-Paper RST | Required |
| — | 3V3 / 5V | E-Paper VCC | Depending on module version |
| — | GND | E-Paper GND | Common ground |
| *(Optional)* | — | Push Button | Tied to any free GPIO (e.g. GPIO0) for manual refresh |

> ⚠️ Waveshare 7.3" F model requires 5 V power and logic compatibility.  
> For stability, use a **dedicated 5 V 1 A supply** (USB or external regulator).

---

## 🧩 Hardware Requirements

| Component | Description | Example |
|------------|--------------|----------|
| **ESP32 Dev Board** | Main controller | ESP32-DevKitC |
| **Waveshare 7.3" E-Paper (F)** | 800×480 px, 7-color display | SPI interface |
| **Power Supply** | 5 V / 1 A minimum | Stable updates |
| **Push Button** | Optional refresh trigger | Any GPIO input |
| **3D-Printed Frame** | Optional mount | Custom or MakerWorld design |

---

## ⚙️ Software Setup

1. **Install ESPHome**

   ```bash
   pip install esphome
