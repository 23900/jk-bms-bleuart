The Bluetooth management interface of the JK-BMS poses significant security risks. It's hard to believe that a system monitoring such a substantial amount of electrical capacity could be vulnerable to unrestricted modifications through an insecure wireless connection. Apart from the potential harm to individual battery cells, there is even a risk of overcharging that could lead to combustion.

I have made a request to the manufacturer to disable the bluetooth functionality. While waiting for the manufacturer to provide a solution, I have implemented a measure to deactivate the Bluetooth module in the circuit. Earlier, I added a physical power switch through which I could disable its wireless functionality after Bluetooth configuration. Now, I've incorporated an ESP32 placed between the Bluetooth module and the BMS, allowing me to toggle the Bluetooth functionality of the BMS on or off through home-assistant. In the future, I plan to eliminate the Bluetooth functionality of the JK-BMS and switch to using the Wi-Fi or Bluetooth of the ESP32 to manage the BMS.

![power-switch](images/power-switch-Bluetooth-module.jpg "power-switch")  <img src=https://raw.githubusercontent.com/23900/jk-bms-bleuart/main/images/JK_BMS_BLE_EN.png width=40% />

Next, I will modify the Bluetooth connection to enable control of Bluetooth and BMS through software. Special thanks to @syssi for the assistance.

```
                UART-TTL
┌──────────┐                ┌─────────────┐                ┌──────────┐
│          │<----- RX ------│tx1       rx2│<----- RX ------│          │
│  JK-BMS  │------ TX ----->│rx1 ESP32 tx2│------ TX ----->│ JK-BMS   │
│          │<----- BLE_EN --│             │<----- BLE_STA--│ Bluetooth│
│          │------ 3.3v---->│             │------ 3.3v---->│ module   │
│          │<----- GND ---->│             │<----- GND----->│          │
│          │                │             │                │          │
└──────────┘                └─────────────┘                └──────────┘

```


