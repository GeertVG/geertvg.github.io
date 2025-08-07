# Programmable logic controller

A PLC is the "brain" of automated machinery. It is therefore equipped with a programmable controller that uses logical instructions, like AND & OR gates, to create the intelligence.

## Rack

A PLC is primarily mounted in an electrical control cabinet. This involves a modular PLC assembly on a mounting rail.
- If this is a standard DIN C rail, it is called a **mounting rail**.
- Otherwise, it is called a **rack**. Such a rack is designed by the manufacturer and often intended for mounting a specific PLC series.


![CX PLC on standard DIN C rail](/images/CX_on_rail.png "CX PLC on standard DIN C rail, ©2020 Beckhoff")

![S7-1200 PLC on standard DIN C rail](/images/S7_1200_on_rail.png "S7-1200 PLC on standard DIN C rail, ©2020 Siemens") ![S7-1200 PLC on standard DIN C rail](/images/S7_1200_on_rail_bottom.png "S7-1200 PLC on standard DIN C rail, ©2020 Siemens")

Some racks are equipped with electronic connectors. These provide the connection between the various modules and the processing unit. If this is not provided, this task is performed by a connector supplied by the manufacturer, or the modules are equipped with connectors that are automatically connected during installation.

![S7-1500 PLC on rack](/images/S7_1500_on_rack.png "S7-1500 PLC on rack, ©2020 Siemens")

## Central Processing Unit

The processing unit, or CPU <sup>1</sup>, consists of several parts. It not only executes the software code but also maintains the user program and the status of various variables and parameters.

| Part | Description |
| :--- | :--- |
| Processor | The processing of the user program is done by the processor |
| Internal memory | The internal memory stores the user program and the status of various variables and parameters |
| External memory | External memory is not included on every PLC type. If it is, it: <br> - Sometimes supplements the internal memory and can ensure that the status of variables is retained during a power failure <br> - Sometimes serves as a backup of the user program and is automatically downloaded when power is restored <br> - In some PLCs, it is necessary for the correct operation of the processing unit <br> <br> External memory is often offered in the form of an SD<sup>(2)</sup> or CF<sup>(3)</sup> card. |

A manufacturer often has several processing units available that have the same basic functionality, but differ in processing speed, software code capabilities, internal memory, external memory, communication capabilities, etc.
It is equipped with various status LEDs. These LEDs indicate the operating mode and status. The operating mode can be set using a switch and/or the associated software package.

| LED              | Description                                                 |
|:-----------------|:------------------------------------------------------------|
| *Siemens PLC*    |                                                             |
| RUN (green)      | ONLINE user program is executed                             |
| STOP (orange)    | ONLINE user program is not executed                         |
| SF (red)         | System fault                                                |
| FRCE (red)       | At least one variable is forced                             |
| MAINT (orange)   | Maintenance necessary                                       |
| ERROR (red)      | Error                                                       |


| LED              | Description                                                 |
|:-----------------|:------------------------------------------------------------|
| *Beckhoff PLC*   |                                                             |
| PWR (green)      | Power on                                                    |
| TC (red)         | STOP: ONLINE user program is not executed                   |
| TC (green)       | RUN: ONLINE user program is executed                        |
| TC (blue)        | TwinCAT in Config mode                                      |
| ERR (red)        | Error                                                       |

Depending on the type, a CPU is equipped with one or more industrial network connections. These connections allow users to download, upload, and debug a user program using the ES package. External components, such as HMI displays, can also be connected.

![CX9020 CPU at a glance](/images/CX_at_a_glance.png "CX9020 CPU at a glance, ©2020 Beckhoff")

Depending on the manufacturer and type, a processing unit is equipped with a battery. This ensures that the ONLINE user program is retained and that the internal clock continues to operate when the power supply is switched off. If there is no battery, this function is taken over by an internal capacitor, but then its functionality is a limited in time (a few days).

![S7-1200 CPU at a glance](/images/S7_1200_at_a_glance.png "S7-1200 CPU at a glance, ©2020 Siemens")

Siemens S7-1500 processing units are equipped with a display as standard. This display allows you to configure the processing unit and view its status:
- Configure network settings
- View faults
- Adjust operating mode
- …

![S7-1500 CPU at a glance](/images/S7_1500_at_a_glance.png "S7-1500 CPU at a glance, ©2020 Siemens")

Furthermore, the operating mode switch, SD memory, and Ethernet/PROFINET connection(s) are only accessible by removing the front panel.

Finally, in both the Siemens and Beckhoff processing units, the other modules are primarily installed to the right of the processing unit.

<sup>1</sup> *Central Processing Unit* <br>
<sup>2</sup> *Secure Digital* <br>
<sup>3</sup> *Compact Flash* <br>

## Inputs

## Outputs

## Internal communication
