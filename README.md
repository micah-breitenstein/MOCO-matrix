# MOCO-Matrix

Arduino firmware for the ESP32-S3 controlling a Waveshare 8×8 RGB LED matrix status display.

## Overview

MOCO-Matrix drives an 8×8 addressable RGB LED matrix to display motion control system status:
- Camera motion state (pan, tilt, swing, lift, focus)
- Emergency stop indicator
- System operational status
- Real-time feedback during motion capture

## Hardware

- **MCU**: ESP32-S3 with integrated WiFi/BLE
- **Display**: [Waveshare ESP32-S3 Matrix](https://a.co/d/0csbP7Bg) - 8×8 RGB LED matrix (WS2812B)
- **Interface**: GPIO data line to addressable LED strip

## Build & Flash

### Prerequisites
- Arduino IDE 1.8.19+ or Arduino CLI
- ESP32 board support installed
- Connected via USB to ESP32-S3 board

### Build with Arduino CLI
```bash
arduino-cli compile --fqbn esp32:esp32:esp32s3 .
```

### Flash with Arduino CLI
```bash
arduino-cli upload -p /dev/cu.usbmodem1201 --fqbn esp32:esp32:esp32s3 .
```

### Using Arduino IDE
1. Open `ESP32_S3_Matrix_Status.ino`
2. Select Board: ESP32-S3
3. Select Port: `/dev/cu.usbmodem1201`
4. Click Upload

## Configuration

Matrix pin and timing settings at the top of `ESP32_S3_Matrix_Status.ino`:
- LED data pin (GPIO)
- Number of LEDs (64 for 8×8)
- Color palette definitions
- Brightness levels

## Status Indicators

The 8×8 grid displays various status patterns:
- **Cyan**: Ready/idle
- **Green**: Motion in progress
- **Red**: Error/emergency stop
- **Yellow**: Warning/attention needed
- **Blue**: System initializing

Specific patterns indicate which axes are active (pan, tilt, swing, lift, focus).

## Communication

Receives status updates via serial (UART) from the Mega master controller:
- Motion state commands
- Emergency stop signals
- Brightness adjustments

## Project Structure

```
ESP32-S3-Matrix/
├── ESP32_S3_Matrix_Status.ino    # Main sketch
└── LICENSE                        # MIT License
```

## License

MIT License - See LICENSE file

