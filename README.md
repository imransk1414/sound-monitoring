# Sound Level Monitoring System

A real-time sound level monitoring and alert system built on the NodeMCU ESP8266 and an analog sound sensor. It samples ambient sound, converts it to an approximate decibel (dB) value, and switches on an LED when the level crosses a set threshold. Live readings are streamed to the Serial Monitor.

Author: Pathan Mohammad Shoaib Khan

---

## Features

- Real-time sound sampling using an analog sound sensor (electret microphone with amplifier)
- Peak-to-peak amplitude measurement over a 50 ms window
- Approximate dB calculation using a logarithmic conversion
- Threshold-based alerting (default: 60 dB) with an LED indicator
- Live dB readings and alert messages on the Serial Monitor
- Low cost, standalone, and ready to extend with Wi-Fi/IoT features

---

## Hardware Required

| Component | Role |
| --- | --- |
| NodeMCU ESP8266 | Sampling, dB calculation, threshold logic, serial output |
| Analog sound sensor module | Outputs an analog voltage proportional to sound intensity |
| LED (5 mm, any colour) | Visual alert when the threshold is exceeded |
| Jumper wires | Connections |
| Micro-USB cable | Power and serial communication |
| Laptop / PC with Arduino IDE | Upload firmware and view the Serial Monitor |

---

## Wiring

| NodeMCU pin | Connected to |
| --- | --- |
| A0 (Analog In) | AO (analog output) of the sound sensor |
| D1 (Digital Out) | LED anode (+), through a current-limiting resistor |
| 3V3 / VU | VCC of the sound sensor |
| GND | GND of the sensor and LED cathode |

---

## How It Works

1. **Sense:** The microphone picks up sound and the onboard amplifier feeds an analog signal to A0.
2. **Sample:** The firmware reads A0 repeatedly for 50 ms, tracking the maximum and minimum values.
3. **Process:** Peak-to-peak amplitude = max - min. It is converted to a voltage and then to an approximate dB value with a logarithmic formula.
4. **Compare:** If the dB value is above the threshold (60 dB), the LED on D1 turns ON and an alert is printed. Otherwise the LED stays OFF.
5. **Report:** Every computed dB value is printed to the Serial Monitor.

Note: The dB values are relative and empirically scaled, not laboratory-calibrated dB(SPL). They are best used for threshold comparison.

---

## Setup

1. Wire the sound sensor and LED to the NodeMCU as shown above.
2. Install the Arduino IDE and add the ESP8266 board package.
3. Open the project sketch, select the NodeMCU board and the correct COM port.
4. Upload the sketch.
5. Open the Serial Monitor at the baud rate set in the sketch to see live readings.
6. Adjust the threshold value in the sketch if needed.

---

## Test Results

| Test condition | Approx. level | LED state |
| --- | --- | --- |
| Silent room | ~25 dB | OFF |
| Normal speech near microphone | ~40-50 dB | OFF |
| Hand clap close to sensor | 63-68 dB | ON, alert printed |
| Loud shout / sharp sound | 70+ dB | ON, alert printed |

The system responds within a single 50 ms sampling window, so the alert is near-instant.

---

## Applications

- Library, classroom, or office noise monitoring
- Baby-room or hospital ward monitoring
- Industrial workplace noise alerts
- Smart-home sensing node
- Wi-Fi-connected IoT noise-logging dashboard

---

## Future Scope

- Wi-Fi connectivity to push data to a cloud platform or web dashboard
- Data logging to analyse noise trends over time
- Mobile or app notifications when the threshold is crossed
- Calibration against a reference sound level meter
- Multi-level alerts with different LED colours or a buzzer
- Smart-home integration

---

## Bill of Materials

| Item | Quantity |
| --- | --- |
| NodeMCU ESP8266 development board | 1 |
| Analog sound sensor module | 1 |
| LED (5 mm, any colour) | 1 |
| Jumper wires | As required |
| Micro-USB cable | 1 |

---

## Project Video

Add your demo video link here.
