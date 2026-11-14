# Humidity Detector using 555 Timer

A capacitive-type humidity detector built with an **NE555 timer IC** and a **bank of high-pass filters**. The circuit shows the humidity level by lighting up LEDs: the higher the humidity, the fewer LEDs glow.


## Working Principle

1. **Sensing** – A capacitive humidity sensor changes its capacitance with the surrounding relative humidity.
2. **Frequency generation** – The sensor is part of the timing network of a 555 timer running in astable mode, which continuously produces a square wave. As humidity increases, the sensor capacitance increases and the **output frequency decreases**.
3. **Frequency detection** – The square wave is fed to several **high-pass filters**, each tuned to a different cutoff frequency. Each filter drives an LED that lights up **only if the input frequency is above that filter's cutoff**.
4. **Display** – The number of lit LEDs indicates the humidity level (low humidity → high frequency → more LEDs on).

```
Humidity Sensor ──► 555 Timer (astable) ──► High-pass filter 1 ──► LED 1
                                        ├─► High-pass filter 2 ──► LED 2
                                        ├─► High-pass filter 3 ──► LED 3
                                        └─► High-pass filter 4 ──► LED 4
```

## Key Formulas

**555 timer output frequency**

```
f = 1.44 / ((R1 + 2·R2) · C_sensor)
```

- `R1` – resistor between Vcc and discharge pin (7)
- `R2` – resistor between discharge pin (7) and threshold pin (6)
- `C_sensor` – variable capacitance of the humidity sensor

**High-pass filter cutoff frequency**

```
f_c = 1 / (2π R C)
```

## Components Used

| Component | Purpose |
|---|---|
| NE555 timer IC | Astable oscillator |
| Capacitive humidity sensor | Humidity-dependent capacitance |
| Resistors (e.g. 20 Ω, 680 Ω, 1 kΩ) | Timing network and filters |
| Capacitors (e.g. 1 nF, 10 nF) | Filter and timing network |
| LEDs | Humidity level indicators |
| 9 V battery | Power supply |
| Breadboard / perfboard, jumper wires | Prototyping and final build |

> Update this table with your exact component values and filter cutoff frequencies.


```

## Repository Structure

```
Humidity-Detector/
├── README.md
├── Humidity_Detector_group14.pptx   # Project presentation
└── images/                          # Circuit photos and diagrams
```

## How to Build

1. Build the 555 astable circuit with the humidity sensor as the timing capacitor.
2. Build the high-pass filter stages, each with a different cutoff frequency.
3. Connect each filter output to an LED (with a current-limiting resistor if needed).
4. Power the circuit with a 9 V battery.
5. Expose the sensor to different humidity levels and observe the LEDs.

## Future Improvements

- Add a microcontroller or ADC for numeric humidity readout
- Add buzzer or alarm for threshold humidity
- Calibrate against a commercial hygrometer
- Design a PCB version

