# Actuators

The central processing unit will control the "machinery power" via the PLC outputs and the control actuators. The digital signal from the processing unit is converted to an analog signal by the PLC output modules.

## Conversion

Just as with sensors, digital and analog signals are defined based on the different states of the electrical signal:
- Electrical signals with two states that are converted from a logical 0 or a logical 1 are called digital output signals.
- Electrical signals with a continuous state between two limits that are converted from a series of 0s and 1s are called analog output signals.

Because a digital signal changes in steps, the electrical signal will also change in steps when converted to analog output signals.

![Overview automation output signals](/images/overview_output_signals.png "Overview automation output signals")

Within the EU, electrical output signals are defined by standards. The list below provides an overview of commonly used electrical signals in automated systems:
- 24 VDC and 0 VDC for digital signals and as a power supply for control signals
- 0–20 mA for analog signals
- 4–20 mA for analog signals
- 0–10 V for analog signals

## Actuator selection

The **choice** of a **control actuator** depends on the power output:
- Contactors for electrical power outputs, such as asynchronous motors and heating coils,
- Relays for electrical control outputs (e.g., NO contact ON to a frequency converter),
- Solenoid valves for hydraulic and pneumatic power outputs,
- Electro-pneumatic controllers, also called positioners, for control valves.

| ![Siemens SIRIUS 3RT contactor](/images/Siemens_3RT.png "Siemens SIRIUS 3RT contactor, ©2020 Siemens") | Siemens SIRIUS 3RT contactor <br> - For the control of electrical power <br> - Digital signal <br> - Expandable with timers and auxiliary contacts <br> - Available in different sizes (depending on the power to be switched) | 
| :---: | :--- |

| ![Siemens SIRIUS 3RQ3 relay](/images/Siemens_3RQ3.png "Siemens SIRIUS 3RQ3 relay, ©2020 Siemens") | Siemens SIRIUS 3RQ3 relay <br> - For the control of electrical control signals <br> - Digital signal <br> - Small design, small installation size | 
| :---: | :--- |

| ![Siemens SIPART PS2 positioner](/images/Siemens_PS2.png "Siemens SIPART PS2 positioner, ©2020 Siemens") | Siemens SIPART PS2 positioner <br> - For the control of electro-pneumatic control valves <br> - Analog signal (4 - 20mA) <br> - Available in various housings | 
| :---: | :--- |

## Operator control selection according IEC 60204

The color of an operator control is determined by its function.

| Color | Meaning | Declaration | Required action |
| :---: | :---: | :--- | :--- |
| Red | Emergency | Dangerous situation | Take immediate action in the event of a dangerous situation (e.g. switch off or keep a distance from the machine, be aware of the dangerous situation) |
| Yellow | Abnormal | Abnormal situation, situation may become critical | Monitoring and/or intervention (e.g. by restoring the intended function) |
| Blue | Commandment | Indication of a situation in which operators must act | Intervention is required |
| Green | Normal | Normal situation| If necessary |
| White | Neutral | Other situations <br>
Can be used when in doubt about the application of red, yellow, green, or blue | Monitoring |

| ![Siemens SIRIUS signal column 8WD4](/images/Siemens_8WD4.png "Siemens SIRIUS signal column 8WD4, ©2020 Siemens") | Siemens SIRIUS signal column 8WD4 <br> - For remote signaling <br> - Digital signal <br> - Modular design up to 4 modules <br> - Available in 5 different colors and one buzzer module <br> - Available for 24VDC, 115VAC and 230VAC  <br> - Available in 2 different dimensions | 
| :---: | :--- |

For signal columns, the order of colors used is preferably as follows:
- RED
- YELLOW
- BLUE
- GREEN
- WHITE

> **What does the Machinery Directive 2006/42/EG describes about signal devices?**
>
> The following items regarding signaling devices are included in the Machinery Directive:
> - The machinery must be equipped with signaling and indicating devices necessary for safe operation. The operator must be able to observe these signals and indications from the control position
> - From any control position, the operator must be able to ensure that no one is present in the danger zones, or the control system must be designed and constructed in such a way that starting the machinery is prevented as long as someone is present in the danger zones
> - If neither of these options is applicable, an audible and/or visual signal must be given before starting the machinery. Exposed persons must have sufficient time to leave the danger zones or prevent the machinery from starting
