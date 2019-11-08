# M5-camera-homekit
esp32-homekit-cameraのビルド方法を日本語での情報がないので解説します。
HomebridgeやHomeHUBは不要で直接、HomeKitのアクセサリー登録ができます。

- M5 Camera Type B 単眼レンズ版
- M5 Camera 魚眼レンズ版
- M5 Camera Type Aは未対応、日本で販売されているものはType Bです。

## ダウンロード
```
cd ~/esp
git clone https://github.com/maximkulkin/esp32-homekit-camera.git
cd esp32-homekit-camera
git submodule update --init --recursive
```

## M5 Cameraの設定(macOSの場合)
```
menu config

- Serial flasher config
    - Default serial port = /dev/cu.SLAB_USBtoUART
    - Flash size = 4MB
- ESP32 HomeKit Camera
    - WiFi SSID and WiFi Password
    - Camera Pins
        - Select Camera Pinout = M5Stack Camera With PSRAM
        - Camera LED  = 14

- Partition Table
    - Partition Table = Custom partition table CSV
    - Custom partition CSV file = partitions.csv
- Component config
    - ESP32-specific
        - Support for external, SPI-connected RAM = check
        - SPI RAM config
            - Initialize SPI RAM when booting the ESP32 = check
            - SPI RAM access method = Make RAM allocatable using malloc() as well
    - Camera configuration
        - OV2640 Support = check
    - HomeKit
        - SPI flash address for storing HomeKit data = 0x3A0000
```

## 謝辞
Maxim Kulkin https://github.com/maximkulkin
