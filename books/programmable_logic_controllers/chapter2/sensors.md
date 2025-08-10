# Sensors

The artificial senses of a machine or installation, called **sensors**, transmit the current status of machinery or technical installation to the central processing unit of the PLC via the PLC inputs.

## Conversion
---
A sensor measures a physical quantity and converts it into an electrical signal so it can be processed by an electronic device. PLC input modules convert the electrical signal into a signal consisting of 0s and 1s. Such a signal is called a digital signal because it changes in steps (through the 0s and 1s).

![Input conversion](/images/input_conversion.png "Input conversion")

The electrical signal is called an analog signal because it can take any value (the number of digits after the decimal point is theoretically infinite).

![Digital vs analog signals](/images/digital_vs_analog.png "Digital vs analog signals")

In automation, however, digital and analog signals are defined based on the different states of the electrical signal:
- Electrical signals with two states that are converted to a logical 0 or a logical 1 are called **digital input signals**.
- Electrical signals with a continuous state between two extreme limits that are converted to a series of 0s and 1s are called **analog input signals**.

![Overview automation input signals](/images/overview_input_signals.png "Overview automation input signals")

Because a digital signal changes in steps, some information is lost when converting analog input signals. Furthermore, one must always work between two extreme values, namely the minimum and maximum sensing limits.

Within the EU, electrical input signals are defined by standards and guidelines. The list below provides an overview of commonly used electrical signals in industrial automation:
- 24 VDC and 0 VDC for digital signals and as a power supply for control signals
- 0–20 mA and 4–20 mA for analog signals
- 0–10 V for analog signals
- Pt100: resistance measurement for analog signals

> Pt100 = Resistance measurement that is exactly 100 Ohm at 0 °C and where the resistance increases with increasing temperature

## Sensor selection
---
The **choice of a sensor** is determined by several factors:
- The properties of the object to be detected, such as shape and color
- The distance between the sensor and the object
- Environmental factors, such as dust and water
- Mounting options and electrical characteristics
- …

When selecting a sensor based on the distance between the sensor and the object, the sensing range should be considered, ensuring that the maximum and minimum distances between the sensor and the object are within the sensing range.

![Sensing range of a sensor](/images/sensor_distance.png "Sensing range of a sensor")

The nominal sensing range is limited by the minimum and maximum measurement limits. However, manufacturers often ensure that a sensor can handle slightly more, allowing measurements outside the nominal sensing range. The area outside the nominal sensing range is called overrange.

![Overrange of a sensor](/images/sensor_range.png "Overrange of a sensor")

| ![Siemens limit switch 3SE5](/images/Siemens_3SE5.png "Siemens limit switch 3SE5, ©2020 Siemens") | Siemens limit switch 3SE5 <br> - Detects presence using a lever switch <br> - Digital signal <br> - Available for 24VDC, 115VAC and 230VAC <br> - Available in plastic or metal housing <br> - Available in 5 different dimensions | 
| :---: | :--- |

| ![Siemens inductive sensor PXI400](/images/Siemens_PXI400.png "Siemens inductive sensor PXI400, ©2020 Siemens") | Siemens inductive sensor PXI400 <br> - Detects the presence of conductive metal objects without contact <br> - Digital signal <br> - Sensing range : 0 .. 5mm / 0 .. 12mm <br> - Cylindrical design | 
| :---: | :--- |

| ![Siemens capacitive sensor PXC200](/images/Siemens_PXC200.png "Siemens capacitive sensor PXC200, ©2020 Siemens") | Siemens capacitive sensor PXC200 <br> - Detects the presence of all objects without contact <br> - Digital signal <br> - Sensing range : 0 .. 5mm <br> - Cylindrical design | 
| :---: | :--- |

| ![Siemens photocell PXO500](/images/Siemens_PXO500.png "Siemens photocell PXO500, ©2020 Siemens") | Siemens photocell PXO500 <br> - Detects the presence of none-transparent objects without contact <br> - Digital signal <br> - Sensing range : 12 .. 15cm / 20 .. 50m | 
| :---: | :--- |

| ![Siemens SITRANS TS100 temperature sensor](/images/Siemens_TS100.png "Siemens SITRANS TS100 temperature sensor, ©2020 Siemens") | Siemens SITRANS TS100 temperature sensor <br> - Measures the temperature by resistance that depends on the temperature <br> - Analog signal <br> - Available for 24VDC, 115VAC and 230VAC <br> - Available with different connectors <br> - Available as Pt100 | 
| :---: | :--- |

| ![Siemens SITRANS P200 pressure sensor](/images/Siemens_P200.png "Siemens SITRANS P200 pressure sensor, ©2020 Siemens") | Siemens SITRANS P200 pressure sensor <br> - Measures the relative or absolute pressure <br> - Analog signal <br> - Available for 4 .. 20mA / 0 .. 10VDC control signals <br> - Sensing range : 0 .. 2.5bar / 0 .. 4 bar / 0 .. 6bar / ... <br> - Available with different connectors | 
| :---: | :--- |

## Operator control selection according IEC 60204
---
Controls, such as push buttons, allow an operator to start or stop an action. A switch, for example, allows you to select and/or activate a specific operating mode, with a choice of different functionalities:
- Two-position switch: 0-I
- Three-position switch: II-0-I
- Multi-position switch: …
- Key instead of a switch:
	- Key removable in all positions
	- Key removable in position 0
	- …
- Switch springs back to a specific position

| ![Siemens operator control and signaling 3SB3](/images/Siemens_SB3.png "Operator control and signaling 3SB3, ©2020 Siemens") | Siemens 3SB3 Operator control <br> - Push buttons and switches <br> - Digital signal <br> - Available for 24VDC, 115VAC and 230VAC <br> - Available in plastic or metal housing <br> - Available in different dimensions <br> - Available in different colors | 
| :---: | :--- |

The **color** of an **operator control** is determined by its function:
- The colors for **START/ON controls** must be WHITE, GREY, BLACK, or GREEN, with WHITE preferred. RED must not be used.
RED must be used for emergency stop and emergency control devices (including power interruption if intended for emergency use). If there is a background directly around the actuator, this background must be YELLOW. The combination of a RED actuator with a YELLOW background must only be used for emergency control devices.
- The colors for **STOP/OFF controls** must be BLACK, GREY, or WHITE, with BLACK preferred. GREEN must not be used. RED is permitted, but it is recommended that RED not be used near an emergency control device.
- White, gray, or black are the preferred colors for actuators that alternate between START/ON and STOP/OFF controls. RED, YELLOW, or GREEN must not be used. WHITE, GREY, or BLACK are the preferred colors for controls that activate when pressed and stop when released (e.g., dead-man controls). RED, YELLOW, or GREEN must not be used.
- **Reset controls** are BLUE, WHITE, GREY, or BLACK. Where they also function as a STOP/OFF control, WHITE, GREY, or BLACK are preferred, with BLACK being the primary preference. GREEN must not be used.
- YELLOW is reserved for use in abnormal conditions, for example, in the event of an abnormal process condition or to interrupt an automatic cycle.
Where the same WHITE, GREY, or BLACK color is used for different functions (e.g., WHITE for START/ON and STOP/OFF controls), additional coding (e.g., shape, position, or symbol) must be used to identify the controls.

> **What does the Machinery Directive 2006/42/EG describes about control devices?**
>
> The following items on control devices are included in the Machinery Directive. Control devices must:
> - Be clearly visible and identifiable and, where necessary, be provided with pictograms
> - Be positioned so that operation can be performed safely, without hesitation or loss of time, and without misunderstanding
> - Be designed in such a way that there is a logical relationship between the movement of the control device and its effect
> - Be located outside danger zones, except where necessary for certain control devices, such as emergency stops or overhead control stations
> - Be positioned so that their operation does not cause danger
