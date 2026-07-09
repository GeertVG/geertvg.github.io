# Device configuration
---
Adding and configuring an HMI display depends on the manufacturer, as shown in the following table.

|Manufacturer | Item |	Description |
| :---------: | :---: | :---------- |
| Beckhoff	| TwinCAT 3 PLC project	| Via ‘Visualisation’ in the PLC project. <br> Programming of HMI screens where the operating unit processes both the PLC project and the HMI project | 
| Beckhoff	| TwinCAT 3 HMI project	| Programming of HMI screens that work on third-party screens on which TwinCAT 3 PLC is not installed | 
| Beckhoff	| TwinCAT 3 HMI Web project	| Programming of HMI screens that work in a browser | 
| Siemens	| TIA Portal project |	Programming of Basic panels via ‘Add new device’ -> HMI | 
| Siemens	| WinCC V7 project |	Programming of Comfort and mobile HMI screens via WinCC Comfort or higher. <br> Programming of PC-based HMI screens that work on a Windows environment via WinCC Advanced or higher | 

> This e-book only covers HMI design of TwinCAT 3 PLC and TIA Portal projects.

![To add a Beckhoff HMI](/images/add_Beckhoff_hmi.png "Adding a ‘Visualisation’ in Beckhoff TwinCAT 3 PLC project") 

![To add a Siemens HMI](/images/add_Siemens_hmi.png "Adding a ‘Basic panel’ in Siemens TIA Portal") 

Please note that in the Siemens package, it is necessary to select the correct display. This creates an HMI project tailored to the screen in terms of screen size, library objects to be used, network settings, ... .

Beckhoff does not offer the option of selecting a display. This is because the ES environment is constantly being enlarged/reduced in the RT environment, which causes problems for small HMI screens.

In both packages, it is possible to set various parameters.
Beckhoff provides a ‘Visualisation manager’ in a TwinCAT PLC project for managing general settings, users, shortcut keys, ... .

![Beckhoff HMI visualization manager](/images/manager_Beckhoff_hmi.png "Beckhoff HMI “Visualization manager” in TwinCAT 3 PLC, © 2020 Beckhoff") 

Siemens provides various managers for the management of general settings, users, ... .

![Siemens HMI manager](/images/manager_Siemens_hmi.png "Siemens HMI manager in TIA Portal V15 SP1, © 2020 Siemens") 