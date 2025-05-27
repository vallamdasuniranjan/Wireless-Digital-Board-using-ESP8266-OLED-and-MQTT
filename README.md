# Wireless MQTT Digital Display using ESP8266 & OLED

![MQTT](https://github.com/user-attachments/assets/d8319070-706c-4a8e-bbad-2d731d4c978c)


A simple yet powerful project to create a wireless digital message board. This project uses an **ESP8266** microcontroller to connect to a Wi-Fi network, subscribe to an **MQTT** topic, and display any messages it receives on a crisp **OLED screen**.

You can update the text on the display from anywhere in the world using any MQTT client, making it a perfect IoT beginner project for status displays, notification boards, or remote data monitors.

---

## 🚀 Features

* **Wireless Updates:** Change the displayed text remotely over Wi-Fi.
* **Real-Time:** Messages appear on the screen almost instantly.
* **Lightweight Protocol:** Uses MQTT, a standard for IoT communication that is efficient and reliable.
* **Low Cost:** Built with common and affordable hobbyist electronics.
* **Easy to Build:** Simple wiring and straightforward code make it perfect for beginners.

---

## 🛠️ Hardware Requirements

* **ESP8266 Development Board:** NodeMCU or Wemos D1 Mini is recommended.
* **0.96" I2C OLED Display:** SSD1306 driver (4-pin version).
* **Breadboard**
* **Jumper Wires**
* **Micro-USB Cable**

---

## 📦 Software & Libraries

* **[Arduino IDE](https://www.arduino.cc/en/software)**
* **ESP8266 Board Manager URL:** `http://arduino.esp8266.com/stable/package_esp8266com_index.json`
* **Required Arduino Libraries:**
    * `PubSubClient` by Nick O'Leary
    * `Adafruit_GFX` by Adafruit
    * `Adafruit_SSD1306` by Adafruit
* **[MQTTX Client](https://mqttx.app/)** (or any other MQTT client for testing).

---

## ⚙️ Setup & Installation

1.  **Hardware Connection:** Wire the components as follows:

| OLED Pin | NodeMCU Pin |
| :--- | :--- |
| `VCC` | `3V3` |
| `GND` | `GND` |
| `SCL` | `D1` (GPIO5) |
| `SDA` | `D2` (GPIO4) |

2.  **Arduino IDE Setup:**
    * Install the Arduino IDE and add the ESP8266 Board Manager URL via **File > Preferences**.
    * Go to **Tools > Board > Boards Manager**, search for `esp8266`, and install the package.
    * Go to **Sketch > Include Library > Manage Libraries** and install the three required libraries listed above.

3.  **Configure the Code:**
    * Open the `.ino` sketch file.
    * Update your Wi-Fi credentials:
        ```cpp
        const char* ssid = "YOUR_WIFI_SSID";
        const char* password = "YOUR_WIFI_PASSWORD";
        ```
    * (Optional) Change the `mqttTopic` if you wish to use a different one.
        ```cpp
        const char* mqttTopic = "display/text";
        ```

4.  **Upload:**
    * Select your board (e.g., "NodeMCU 1.0") and the correct COM port from the **Tools** menu.
    * Click the **Upload** button.

---

## ▶️ How to Use

Once the code is uploaded and the ESP8266 is running, it will automatically connect to Wi-Fi and the MQTT broker. The OLED will show "MQTT Connected!".

1.  **Open an MQTT Client** (like MQTTX).
2.  **Connect** to the public broker: `broker.emqx.io` on port `1883`.
3.  **Publish a message:**
    * **Topic:** `display/text` (or your custom topic)
    * **Payload:** The message you want to display (e.g., "Hello World!")
4.  Click **Publish**. The text will instantly appear on your OLED screen!

---
5.  **Results/output:**
![2](https://github.com/user-attachments/assets/487df6a9-dcc1-4028-8af6-334bfab7313e)
![3](https://github.com/user-attachments/assets/7109e40a-cb32-4934-a45a-5539676f0131)
![4](https://github.com/user-attachments/assets/45de0861-cc4f-4320-9e6a-ffafc9c9bab1)

## 🔧 Troubleshooting

* **Nothing on screen / No Wi-Fi:** Double-check your `ssid` and `password` in the code. Ensure you are in Wi-Fi range. Check your wiring.
* **OLED shows "MQTT Failed":** Your ESP8266 has Wi-Fi but cannot reach the MQTT broker. Check if your network has a firewall blocking port 1883.
* **Message not appearing:** Ensure the topic in your MQTT client is **exactly** the same as the `mqttTopic` in the code. Topics are case-sensitive.
