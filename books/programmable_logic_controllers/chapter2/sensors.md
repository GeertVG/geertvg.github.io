# Sensors
## Conversion

## Sensor selection

The **choice of a sensor** is determined by several factors:
- The properties of the object to be detected, such as shape and color
- The distance between the sensor and the object
- Environmental factors, such as dust and water
- Mounting options and electrical characteristics
- …

When selecting a sensor based on the distance between the sensor and the object, the measurement range should be considered, ensuring that the maximum and minimum distances between the sensor and the object are within the measurement range.

The nominal measuring range is limited by the minimum and maximum measurement limits. However, manufacturers often ensure that a sensor can handle slightly more, allowing measurements outside the nominal measuring range. The area outside the nominal measuring range is called the overrange measuring range.

## Operator control selection according IEC 60204

Controls, such as push buttons, allow an operator to start or stop an action. A switch, for example, allows you to select and/or activate a specific operating mode, with a choice of different functionalities:
- Two-position switch: 0-I
- Three-position switch: II-0-I
- Multi-position switch: …
- Key instead of a switch:
	- Key removable in all positions
	- Key removable in position 0
	- …
- Switch springs back to a specific position

![Siemens operator control and signaling 3SB3](/images/Software_parts.png "Operator control and signaling 3SB3 ©2020 Siemens") Siemens 3SB3 Operator control <br> - Push buttons and switches <br> - Digital signal <br> - Available for 24VDC, 115VAC and 230VAC <br> - Available in plastic or metal housing <br> - Available in different dimensions <br> - Available in different colors

The **color** of an **operator control** is determined by its function:
- The colors for START/ON controls must be WHITE, GREY, BLACK, or GREEN, with WHITE preferred. RED must not be used.
RED must be used for emergency stop and emergency control devices (including power interruption if intended for emergency use). If there is a background directly around the actuator, this background must be YELLOW. The combination of a RED actuator with a YELLOW background must only be used for emergency control devices.
- The colors for STOP/OFF controls must be BLACK, GREY, or WHITE, with BLACK preferred. GREEN must not be used. RED is permitted, but it is recommended that RED not be used near an emergency control device.
- White, gray, or black are the preferred colors for actuators that alternate between START/ON and STOP/OFF controls. RED, YELLOW, or GREEN must not be used. WHITE, GREY, or BLACK are the preferred colors for controls that activate when pressed and stop when released (e.g., dead-man controls). RED, YELLOW, or GREEN must not be used.
- Reset controls are BLUE, WHITE, GREY, or BLACK. Where they also function as a STOP/OFF control, WHITE, GREY, or BLACK are preferred, with BLACK being the primary preference. GREEN must not be used.
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

