# Human Machine Interface (HMI)
---
The interaction between humans and machinery is enabled by adding a Human Machine Interface, or HMI for short. This interface primarily consists of the following components:
- Push buttons and switches,
- Potentiometers,
- Lamps,
- Light columns,
- Horn or buzzer,
- BCD<sup>1</sup> displays,
- Thumb wheel switches.

These components can be expanded and/or replaced using a programmable screen equipped with a processor, memory, and the necessary network connections. The term "HMI display" is often used to refer solely to the screen.

![Basic Siemens HMI](/images/siemens_basic_hmi.png "Siemens Basic Panels, ©2020 Siemens") 

Using an HMI display allows you to visually represent a machine/installation and display its status with dynamic colors. It is also possible to provide additional information. The following functionalities are programmable:
- Displaying current alarms in a summary table and/or banner (**=Alarming**)
- Displaying current messages in a summary table and/or banner (**=Events**)
- Displaying analog measurements in graph form (**=Trending**)
- Securing access and operation by adding users and passwords (**=Security**)
- Viewing information such as alarms and graphs from the past (e.g., one day ago) to detect errors (**=Historical data**)

> Dynamic colors = Colours that change depending on the status (e.g. red = fault / green = actuator on)

![CP62xx Beckhoff HMI](/images/Beckhoff_hmi1.png "CP62xx Beckhoff HMI, ©2020 Beckhoff") ![CP62xx Beckhoff HMI](/images/Beckhoff_hmi2.png "CP62xx Beckhoff HMI, ©2020 Beckhoff") ![CP62xx Beckhoff HMI](/images/Beckhoff_hmi3.png "CP62xx Beckhoff HMI, ©2020 Beckhoff") ![CP62xx Beckhoff HMI](/images/Beckhoff_hmi4.png "CP62xx Beckhoff HMI, ©2020 Beckhoff") 

HMI displays are available in various sizes, ranging from 4 inches to 24 inches, and include features such as USB ports, function keys, industrial network connections, and single-touch, dual-touch, or multi-touch operation.

Programming an HMI display is performed using the manufacturer's ES software package. For Beckhoff and Siemens software packages, the ES-HMI software package is integrated into the overarching ES software package (e.g., Beckhoff TwinCAT / Siemens TIA Portal).

<sup>1</sup> *BCD = **B**inary **C**oded **D**ecimal = Coding system for decimal numbers (often used in older displays)*