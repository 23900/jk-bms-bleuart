The Bluetooth management interface of JK-BMS poses significant security risks. It's hard to imagine that a system overseeing tens of thousands of ampere-hours of energy can freely modify various battery data through an insecure wireless connection. Besides the potential damage to the battery cells, there is even a risk of battery overcharging leading to combustion.

To address this, I initially added a physical power switch to the Bluetooth module. After configuring the parameters through Bluetooth, I would then turn off its wireless functionality using this switch.

![power-switch](images/power-switch-Bluetooth-module.jpg "power-switch")

Next, I will modify the Bluetooth connection to enable control of Bluetooth and BMS through software. Special thanks to @syssi for the assistance.

```
                UART-TTL
┌──────────┐                ┌─────────────┐                ┌──────────┐
│          │<----- RX ------│tx1       rx2│<----- RX ------│          │
│  JK-BMS  │------ TX ----->│rx1 ESP32 tx2│------ TX ----->│ JK-BMS   │
│          │<----- BLE -----│             │<----- BLE------│ Bluetooth│
│          │------ 3.3v---->│             │------ 3.3v---->│ module   │
│          │<----- GND ---->│             │<----- GND----->│          │
│          │                │             │                │          │
└──────────┘                └─────────────┘                └──────────┘

```


