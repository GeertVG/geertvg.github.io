# Basic control circuits
## Start-stop circuit

A start-stop circuit is used to start and stop actuators, an entire machine or a technical installation. It is equipped with at least one start button, one stop button and one output result.

Features of the start-stop switch:
-	The start push button is equipped with a normally open contact,
-	The stop push button is equipped with a normally closed contact,
-	When the start push button is pressed, the output result becomes TRUE. After this, the start push button no longer needs to be pressed,
-	The output result becomes FALSE as soon as the stop push button is pressed or if the stop push button is defective (contact is not closed),
-	The stop function has priority over the start function. In other words, if both push buttons are pressed simultaneously, the output result will be FALSE.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     | ![Start-stop circuit](/images/TwinCAT/start_stop_fbd.png) |
| Siemens      | ![Start-stop circuit](/images/TIA/start_stop_fbd.png) |

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     | ![Start-stop circuit](/images/TwinCAT/start_stop_lad.png) |
| Siemens      | ![Start-stop circuit](/images/TIA/start_stop_lad.png) |

```TAGs
•	iSB_DkStart_S1 = digital input – start push button [-S1] on the control panel
•	iSB_DkStop_S2 = digital input – stop push button [-S2] on the control panel
•	oSB_LmpStart_H1 = digital output – start lamp [-H1] on the control panel
•	mGestart = memory flag – started
```
| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     | ![Start-stop circuit](/images/TwinCAT/start_stop_fbd_call.png) |
| Siemens      | ![Start-stop circuit](/images/TIA/start_stop_fbd_call.png) |

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     | ![Start-stop circuit](/images/TwinCAT/start_stop_lad_call.png) |
| Siemens      | ![Start-stop circuit](/images/TIA/start_stop_lad_call.png) |

```TAGs
•	iSB_DkStart_S1 = digital input – start push button [-S1] on the control panel
•	iSB_DkStop_S2 = digital input – stop push button [-S2] on the control panel
•	oSB_LmpStart_H1 = digital output – start lamp [-H1] on the control panel
•	ID_Gestart = Instance data – started
```

> **What does the Machinery Directive 2006/42/EG describes about start-stop switches?**
> 
> Following items are listed in the machine directives:
> -	Machinery may only be started by an intentional action using a control device designed for this purpose (=start button)
> -	Machinery must be equipped with a control device that allows it to be stopped completely and safely (=stop button)
> -	The stop command to the machinery must take precedence over commands to start it (= the stop function has priority over the start function)
> -	When machinery or its hazardous functions have come to a standstill, the energy supply to the relevant actuators must be interrupted (= switch off contactors, valves, etc. so that the energy supply is interrupted)
> -	Stopping machinery must not be prevented if the stop command (= pressing the stop button) has already been given (= normally closed contact ensures that the installation stops in the event of a fault in the electrical stop control circuit)

## Reverse circuit

A reverse circuit is used for actuators where the movement or rotation is reversible.

Features of the reverse circuit:
-	The push buttons on the left and right are equipped with a normally open contact,
-	The stop push button is equipped with a normally closed contact,
-	There is a waiting time between switching the direction of rotation to prevent mechanical defects caused by reversing the direction of rotation too quickly,
-	Simultaneous activation of both rotary switches is not permitted; the first rotary switch activated has priority,
-	The output results become FALSE as soon as the stop push button is pressed or if the stop push button is defective (contact is not closed),
-	The stop function takes precedence over the left and right functions. In other words, if the stop button is pressed simultaneously with a left and/or right button, the output results will be FALSE.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	iSB_DkR_S1 = digital input – Clockwise push button [-S1] on the control panel
•	iSB_DkL_S2 = digital input – Counter clockwise push button [-S2] on the control panel
•	iSB_DkStop_S3 = digital input – stop push button [-S3] on the control panel
•	oSB_ConR_K1 = digital output – contact clockwise  [-K1] on the control panel
•	oSB_ConL_K2 = digital output – contact counter clockwise  [-K2] on the control panel
•	ID_TOF_L= Instance data – stop delay counter clockwise
•	ID_TOF_R = Instance data – stop delay clockwise
•	ID_SR_L and ID_RS_L = Instance data – Flipflop memory to the counter clockwise
•	ID_SR_R and ID_RS_R = Instance data – Flipflop memory to the clockwise
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

## Star-delta circuit

The star-delta circuit is used for three-phase asynchronous motors where the power of these motors is so high that a direct start-up in delta causes a voltage drop in the electrical supply network.

To this end, these motors are started up in star (start-up) mode, after which they switch to delta (normal operation) mode. This results in a lower inrush current and no voltage drop in the mains, but the motor can only be started up without load.

Features of the star-delta circuit:
-	The start push button is equipped with a normally open contact,
-	The stop push button is equipped with a normally closed contact,
-	The start-stop function is implemented using a start-stop circuit,
-	After starting, the motor will be activated in star configuration during the start-up time,
-	Between switching from star to delta, there is a transition time during which both the star and delta contactors are switched off. During this time, the motor will run in freewheel mode (under its own momentum) and simultaneous switching of the star and delta contactors is avoided (which can lead to sparking),
-	The output results become FALSE as soon as the stop push button is pressed or if the stop push button is defective (contact is not closed),
-	Restarting after a stop function is limited by a waiting time which limits the number of starts per hour,
-	The stop function has priority over the start function. In other words, if the stop push button is pressed simultaneously with the start push button, the output results will be FALSE.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	iSB_DkStart_S1 = digital input – start push button [-S1] on the control panel
•	iSB_DkStop_S3 = digital input – stop push button [-S3] on the control panel
•	oSB_ConL_K1 = digital output – main line contactor [-K1] on the control panel
•	oSB_ConS_K2 = digital output – star contactor  [-K2] on the control panel
•	oSB_ConD_K3 = digital output – delta contactor  [-K3] on the control panel
•	ID_TON_S = Instance data – startup time in star
•	ID_TON_SD= Instance data – idle time van star to delta
•	ID_TOF = Instance data – Holding time restart
•	ID_Gestart = Instance data – motor started
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

## Alarm circuit

An alarm represents an abnormal condition or a malfunction and is represented by a BIT. Consequently, an alarm has two states:
-	FALSE = No malfunction or abnormal condition active; the alarm is disabled
-	TRUE = The alarm and consequently the abnormal condition or malfunction is active

The list below provides an overview of common alarms and abnormal conditions:
-	Emergency stop activated
-	Safety relay not armed
-	Motor circuit breaker deactivated
-	Analogue measurement defective
-	Abnormal condition compressed air cylinder (e.g. both end position sensors activated)
-	Compressed air pressure too low
-	Level too high
-	Pressure too high
-	…

An alarm is activated by a cause (e.g. contact from a motor circuit breaker) and is deactivated by the operator. To do this, the operator must first resolve the cause of the alarm, after which the alarm is deactivated using a push button (e.g. reset push button). Activating the alarm has priority over deactivating the alarm. In other words, if the alarm is activated and deactivated simultaneously, the alarm must remain active.

An alarm is programmed using a flip-flop, with the SET instruction taking priority.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	iTB01_Mbv_Q1 = digital input – motor circuit breaker [-Q1] conveyor 1
•	mReset = memory flag – reset signal
•	mA003 = memory flag – alarm no. 003 = motor protection circuit breaker TB01 [-Q1] disabled
•	ID_A003 = Instance data - flipflop memory of alarm no. 3
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

> **What does the Machinery Directive 2006/42/EG  describes about alarms?**
> 
> -	A malfunction in the equipment or the programming of the control system must not lead to dangerous situations. (Alarms can be used to interlock actuators so that they are disabled by software.)
> -	Machinery must not restart unexpectedly. (=Because the operator is required to acknowledge an alarm using a reset push button or an ACK push button, an abnormal condition will not go unnoticed.)
> 
> In addition, alarms can be logged  using an HMI screen to simplify the search for errors and malfunctions.

## Event circuit

An event represents a specific status of machinery or technical installation or part of it. A notification is primarily informative but is often used to simplify software programming.

The following messages are often used:
-	Machinery started in automatic mode
-	Machinery stopped
-	Machinery in manual mode

Depending on the machinery, it is designed to operate fully or partially in manual mode (also known as hand mode). In this case, an operator or maintenance technician will switch off the automatic operation of certain actuators in order to decide for themselves whether or not to activate these actuators. This can be done:
-	By switching the entire machine/installation to manual mode. Stopping the installation is necessary here. This method is mainly used in the field of automation (e.g. conveyors) and for smaller machinery (e.g. machine construction).
-	By switching a specific actuator to manual mode. The other parts of the machinery or technical installation continue to operate according to the automatic operation. This method is mainly used in the field of process automation (e.g. petrochemicals) and in larger technical installations.

Operation in manual mode depends on the control design:
-	Start-stop control: The actuators are started and stopped with separate push buttons. When switching from automatic mode to manual mode, the last operating state of an actuator is retained (=Bump less control transfer).
-	Dead man's control: An actuator will only be activated when the corresponding push button is pressed. When switching from automatic mode to manual mode, the actuator will stop.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	iHAL_DkLmp_S10 = digital input – push button light in the hall [-S10]
•	oHAL_Lmp_H10 = digital output = lamp in the hall [-H10]
•	mHAL_PfLmp_S10 = memory flag – rising edge on the push button light in the hall
•	mHAL_Lmp_S10 = memory flag – switch on the lamp in the hall
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

## Latching circuit

With a latching circuit, it is possible to switch a light on and off using an impulse. To achieve this, a spring-return switch or a push button is used, whereby the push button is pressed once to switch the light on and again to switch it off.

The circuit is characterized by the use of an XOR instruction (only in FBD) in combination with a rising edge of the push button, whereby the result is fed back to the XOR instruction.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	iSB_SelAuto_S1 = digital input – switch automatic mode [-S1]
•	ID_TOF_M003 = Instance data – stop delay event no. 003
•	mM003 = memory flag – event no. 003 = installation in automatic mode
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

The operation can be explained using a truth table across multiple PLC cycles.

| **%I10.0**            | **%M10.1** | **XOR.IN1** | **XOR.IN2** | **XOR.OUT** | **%Q10.0 %M10.1** | **Cycle** |
|:---------------------:|:----------:|:-----------:|:-----------:|:-----------:|:-----------------:|:---------:|
| *Switch on the lamp*  |            |             |             |             |                   |           |
| 0                     | 0          | 0           | 0           | 0           | 0                 | n         |
| 1 ()                  | 0          | 1 (↑)       | 0           | 1           | 1                 | n+1       |
| 1 ()                  | 1          | 0           | 1           | 1           | 1                 | n+2       |
| 1 ()                  | 1          | 0           | 1           | 1           | 1                 | n+3       |
| 0                     | 1          | 0           | 1           | 1           | 1                 | n+4       |
| 0                     | 1          | 0           | 1           | 1           | 1                 | n+x       |
| *Switch off the lamp* |            |             |             |             |                   |           |
| 0                     | 1          | 0           | 1           | 1           | 1                 | n         |
| 1 ()                  | 0          | 1 (↑)       | 1           | 0           | 0                 | n+1       |
| 1 ()                  | 0          | 0           | 0           | 0           | 0                 | n+2       |
| 1 ()                  | 0          | 0           | 0           | 0           | 0                 | n+3       |
| 0                     | 0          | 0           | 0           | 0           | 0                 | n+4       |
| 0                     | 0          | 0           | 0           | 0           | 0                 | n+x       |

## Flashing light circuit

A flashing light circuit makes it possible to make a lamp flash. The time that the lamp is on can differ from the time that the lamp is off. The ratio between the time that the lamp is on and the total period of time is called the ‘duty cycle’.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	oLmp_H1 = digital output – Lamp [-H1]
•	ID_TON_Aan = Instance data – Time lamp on
•	ID_TON_Uit = Instance data – Time lamp off
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```Example
Cars are equipped with orange direction indicators to indicate a change of direction. 

If the right direction indicator is activated, the right direction indicators (front, rear and on the sides/mirrors) 
will be enabled and disabled at regular intervals.
-	The direction indicators flash (=flashing light) 
```

## On-off circuit

An on-off circuit is used to switch a loop manipulated value output LMN [BOOL] on or off depending on a process value PV [REAL] and a setpoint value SP [REAL]. The on-off circuit ensures that the actuator does not switch on and off too often by using two threshold values, namely:
-	The switch-on threshold value (lower limit)
-	The switch-off threshold value (upper limit)

The difference between the switch-on and switch-off threshold values is called hysteresis. The following mathematical formulas apply:

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	mHyst = memory flag = Hysteresis
•	mHystDiv2 = memory flag = Hysteresis/2.0
•	mW = memory flag = Setpoint
•	mBovengrens = memory flag = Switch off threshold or upper limit
•	mBovengrens = memory flag = Switch on threshold or lower limit
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

If the measured value is lower than the switch-on threshold, the control output will be switched on. As soon as the switch-off threshold is reached, the control output will be disabled.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	mX = memory flag = Process value
•	ID_Y = Instance data – Loop manipulated value
•	oY = analog output = Loop manipulated value
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

## Always TRUE & Always FALSE circuits

With the Always TRUE circuit it is possible to obtain a result that always has the value TRUE. An Always FALSE circuit, on the other hand, has a result that is always FALSE.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |


| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

## Normalization circuit

The normalization circuit, abbreviated NORM, is used to convert an INT number limited between a minimum and maximum value to a REAL number limited between the values 0.0 and 1.0 (or 0% and 100%).

To convert an INT number to a REAL number, a conversion instruction must be used. The mathematical formula below is then used to convert the number to a value between 0.0 and 1.0.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	mX = memory flag = Process value
•	ID_Y = Instance data – Loop manipulated value
•	oY = analog output = Loop manipulated value
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

## Scale circuit

The scale circuit is used to convert a REAL number bounded between the values 0.0 and 1.0 (or 0% and 100%) to a REAL number bounded between a minimum and maximum value.

The mathematical formula below is used to convert the number to a value between MIN and MAX.

The scale circuit is often used in combination with the normalization circuit to convert an analogue input value, which is a decimal integer between two extremes (-32768 and +32767), to a decimal number in an SI unit.

| Manufacturer | FBD                         |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |

```TAGs
•	mX = memory flag = Process value
•	ID_Y = Instance data – Loop manipulated value
•	oY = analog output = Loop manipulated value
```

| Manufacturer | LD                          |
|:------------:|:----------------------------|
| Beckhoff     |                             |
| Siemens      |                             |