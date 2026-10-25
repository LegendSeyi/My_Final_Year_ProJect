# IoT-Driven Energy Optimisation System with AI-Based Occupancy Detection

Final year project, B.Sc. Systems Engineering, University of Lagos (2026).

A low-cost system that saves electricity by detecting whether a room is occupied and switching connected appliances off when nobody is there. A camera node feeds an AI object detector, and the result drives a smart plug through a home automation platform.

## How it works

```
ESP32-CAM  -->  Frigate NVR (OpenVINO person detection)  -->  Mosquitto MQTT
                                                                  |
                                      Zigbee smart plug  <--  Home Assistant automation
```

1. The **ESP32-CAM** streams video of the room.
2. **Frigate NVR** analyses the stream and uses **OpenVINO** for AI-based person detection.
3. Occupancy events are published over **MQTT** (Mosquitto broker).
4. **Home Assistant** subscribes to these events and runs the automation that switches the **Zigbee smart plug** on or off.

## Components

| Layer | Tool |
|---|---|
| Camera node | ESP32-CAM |
| Video analysis | Frigate NVR |
| AI inference | OpenVINO |
| Messaging | Mosquitto MQTT |
| Automation and dashboard | Home Assistant |
| Load control | Zigbee smart plug |

## Setup

1. Flash the ESP32-CAM with firmware that exposes a video stream, and confirm the stream opens in a browser or VLC.
2. Install Frigate and add the camera stream to its configuration. Select OpenVINO as the detector and enable person detection.
3. Run a Mosquitto broker and point Frigate and Home Assistant at it.
4. In Home Assistant, add the MQTT integration and the Zigbee smart plug.
5. Create an automation that turns the plug on when Frigate reports a person in the room and off after a set period with no detection.

Add your own configuration files in a `config/` folder (remove passwords and IP addresses first).

## Evaluation

The system was compared against a manual-control baseline. The manual control test ran from 7 to 13 February 2026.

| Scenario | Energy used (kWh) | Notes |
|---|---|---|
| Manual control | _add value_ | Week of 7–13 Feb 2026 |
| AI occupancy control | _add value_ | _add test dates_ |

Add the measured energy saving, detection accuracy and any false-trigger observations here.

## Repository structure

```
.
├── config/        # Frigate, Home Assistant and MQTT configuration (sanitised)
├── docs/          # Report chapters, block diagrams, presentation
├── firmware/      # ESP32-CAM code
└── README.md
```

## Limitations and future work

- Add the limitations you observed, such as low-light performance, camera placement and detection delay.
- Add planned improvements, such as more rooms, additional sensors or energy forecasting.

## Author

Adeyemi Oluwaseyi Emmanuel
[LinkedIn](https://www.linkedin.com/in/oluwaseyi-adeyemi004/) · [GitHub](https://github.com/LegendSeyi)

## License

Choose a licence (for example MIT) and add a `LICENSE` file.
