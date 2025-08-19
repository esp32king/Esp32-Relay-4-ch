# 🔌 ESP32 & ESP8266 4-Relay Web Server

Control 4 relays via a web browser using **ESP32** or **ESP8266**! 🌐  
This project allows you to toggle relays ON/OFF over Wi-Fi with a simple web interface.

---

## ✨ Features
- Control 4 relays independently  
- Web-based control from any device on the same Wi-Fi  
- Compatible with ESP32 and ESP8266 boards  
- Mobile-friendly and lightweight  

---

## ⚡ Hardware Setup

### ESP32 Relay Pins
| Relay | GPIO |
|-------|------|
| Relay 1 | 23 |
| Relay 2 | 22 |
| Relay 3 | 21 |
| Relay 4 | 19 |

### ESP8266 Relay Pins
| Relay | GPIO |
|-------|------|
| Relay 1 | D1 |
| Relay 2 | D2 |
| Relay 3 | D3 |
| Relay 4 | D4 |

**Power:** VCC → 5V, GND → GND  

---

## 🖥 Step-by-Step Installation

### 1️⃣ Install Arduino IDE
- Download from [Arduino IDE](https://www.arduino.cc/en/software)  
- Install on your computer  

### 2️⃣ Install Board Packages

**ESP32:**
1. File → Preferences → Additional Boards Manager URLs https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

2. Tools → Board → Boards Manager → Search “ESP32” → Install  

**ESP8266:**
1. File → Preferences → Additional Boards Manager URLs:  http://arduino.esp8266.com/stable/package_esp8266com_index.json

2. Tools → Board → Boards Manager → Search “esp8266” → Install  

### 3️⃣ Select Your Board
- ESP32: Tools → Board → ESP32 Dev Module  
- ESP8266: Tools → Board → NodeMCU 1.0 (ESP-12E Module)  

### 4️⃣ Connect Your Board
- Plug in via USB  
- Tools → Port → Select correct port  

### 5️⃣ Open Code
- ESP32: `ESP32_4Relay_WebServer.ino`  
- ESP8266: `ESP8266_4Relay_WebServer.ino`  

### 6️⃣ Update Wi-Fi Credentials
```cpp
const char* ssid = "Your_SSID";
const char* password = "Your_PASSWORD";
