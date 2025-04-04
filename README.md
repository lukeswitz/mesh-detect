# Mesh Detect Flasher  
[![Drone Detection Version Check](https://github.com/lukeswitz/mesh-detect/actions/workflows/main.yml/badge.svg)](https://github.com/lukeswitz/mesh-detect/actions/workflows/main.yml)

[![Deepwoods Version Check](https://github.com/lukeswitz/mesh-detect/actions/workflows/deepwoodsVersion.yml/badge.svg)](https://github.com/lukeswitz/mesh-detect/actions/workflows/deepwoodsVersion.yml)

<p align="center">
  <img src="https://raw.githubusercontent.com/lukeswitz/T-Halow/refs/heads/master/firmware/ColonelPanicWiFiRID/img/art_purps.svg" alt="T-Halow WiFi RID Image" width="70%" />
</p>

## About  

Easily flash different firmware onto the **Colonel Panic Mesh Detect.** An automatic `esptool.py` flasher, no Arduino IDE required.

Validation: `shasum meshFlasher.sh d8d9686e430d3c4f3e0e2a94363194933d72e3b1`

![649EA86C-098F-4023-A037-B9BBEE91F57A](https://github.com/user-attachments/assets/fe2075fa-6190-497a-a4d6-735a12831484)


## Resources
*Hackster.io writeup/instructions
[Mesh-Detect](https://www.hackster.io/colonelpanic/mesh-detect-549cbe)*

Mesh Detect board can be found on my Tindie Store:
[mesh-detect board](https://www.tindie.com/products/colonel_panic/mesh-detect-2)

<a href="https://www.tindie.com/stores/colonel_panic/?ref=offsite_badges&utm_source=sellers_colonel_panic&utm_medium=badges&utm_campaign=badge_large">
    <img src="https://d2ss6ovg47m0r5.cloudfront.net/badges/tindie-larges.png" alt="I sell on Tindie" width="200" height="104">
</a>

## Firmware Options  

### 🎥 1. OUI Sniffer  
- [Official FW](https://github.com/colonelpanichacks/esp32-oui-sniffer/tree/Xiao-esp32-c3-serial)  
- Detects specific **OUI(s)** via Bluetooth scanning.  
- Alerts when targeted OUIs are detected.  
- Flash via **Arduino IDE**.  

  🔒 1a. [Privacy Version](https://github.com/lukeswitz/esp32-oui-sniffer/blob/Xiao-esp32-c3-serial/meshdetect__privacy.ino) 
  - Preset OUIs for Floc cameras, known snoops and other privacy invaders.
  - Flash via `meshFlasher.sh`


### 2. 🌲 Deepwoods Device Detection  
- [Deepwoods Device Detection](https://github.com/colonelpanichacks/deepwoods_device_detection)
- Scan WiFi and BT to form a baseline and alert to new devices.
- Detects and alerts on **new** devices.
- Flash via `meshFlasher.sh`

### 3. 🛸 Drone Remote ID to Meshtastic
*With Mesh-Mapper API 📡*
- [Drone Remote id to Meshtastic](https://github.com/colonelpanichacks/wifi-rid-to-mesh)
- Detects **WiFi RID drone signals**.  
- Sends drone detection messages with **ID, RSSI, MAC, Operator ID, Location**, and more.
- Flash via `meshFlasher.sh`

## Flashing Firmware

### Dependencies & Setup

Note: Latest Esptool is automatically downloaded to script directory, and firmware binaries are replaced to ensure they're up-to-date.

```bash
# Install required packages
sudo apt-get update
sudo apt-get install -y git python3 python3-pip wget

# Install Python dependencies
pip3 install esptool pyserial
```

### Flashing 

1. Download the script
```bash
wget https://raw.githubusercontent.com/lukeswitz/mesh-detect/refs/heads/main/meshFlasher.sh
```

2. Make executable
```
chmod +x meshFlasher.sh
```

3. Plug in your esp32 & run the script
```
./meshFlasher.sh
```

4. Follow the on-screen prompts. That’s it! The script will get your board flashed and running. 

> [!IMPORTANT]
> Power cycle the board after flashing to ensure no issues with the Heltec. 

## Configure Mesh Node

- Official Docs https://meshtastic.org/docs/configuration/module/serial/

#### Set the pcb mesh device to use serial mode, and configure the pins:

Ensure both the heltec and your receiver node are on the same channel. Set the pcb mesh settings to:
  - Serial enabled
  - 115200 baud rate
  - Text message mode
  - Pins defined RX/TX 19/20

![image](https://github.com/user-attachments/assets/1fee0617-447a-454c-ac78-10243ec7da5c)


## Troubleshooting

- If your esp32 is not being detected or giving any errors, hold the boot button and plug in the device.
- Make sure you are using a c3 esp32 module. 



Credit: Firmware for RID and flasher based on work by cemaxecuter aka alphafox02. Modded with help of Colonel Panic. 

- Original alphafox RID T-halow: https://github.com/alphafox02/T-Halow
- Thank you to Luke Switzer for the work on this project: https://github.com/lukeswitz/
