# Downloading and debugging
---
## Siemens TIA Portal

Transferring the device configuration and the created software is done by downloading them.
After both are transferred, you can check the functioning of the hardware and software. The status is displayed with colors and/or icons.

| Downloading in TIA Portal | |
| :---: | :---: |
| Download hardware & software | ![Download](/images/TIA_download.png "Download") |
| Go online | ![Go online](/images/TIA_online.png "Go online") |

Debugging or troubleshooting relies heavily on the ES software package. The status of the devices (hardware) is displayed in the Siemens TIA Portal using icons.

| Icon | Description |
| :---: | :--- |
| ![OK icon](/images/TIA/icon1.png) | No error |
| ![Green maintenance icon](/images/TIA/icon2.png) | No error but maintenance is recommended |
| ![Yellow maintenance icon](/images/TIA/icon3.png) | No error but but maintenance is necessary |
| ![Red maintenance icon](/images/TIA/icon4.png) | Error, maintenance necessary  |
| ![Deactivated icon](/images/TIA/icon5.png) | The device or module is deactivated |
| ![No connection icon](/images/TIA/icon6.png) | The device or module can not be reached |
| ![No IO data icon](/images/TIA/icon7.png) | Their is no in- or output data available |
| ![No data icon](/images/TIA/icon8.png) | Their is no diagnostic data available because online and offline configuration is different |
| ![Not compatible icon](/images/TIA/icon9.png) | The device or module is available, but it is not compatible |
| ![Question icon](/images/TIA/icon10.png) | Their is connection with the device or module, but it's state is unknown |
| ![No diagnostic icon](/images/TIA/icon11.png) | Their is connection with the device or module, but diagnostic is not allowed |
| ![Error icon](/images/TIA/icon12.png) | Hardware fault. Can be showed in combination with other icons |

Icons are also used in Siemens TIA Portal for the status of operating modes.

| Icon | Description |
| :---: | :--- |
| ![RUN icon](/images/TIA/icon_run.png) | RUN |
| ![STOP icon](/images/TIA/icon_stop.png) | STOP |
| ![STARTUP icon](/images/TIA/icon_startup.png) | STARTUP |
| ![HOLD icon](/images/TIA/icon_hold.png) | HOLD |
| ![DEFECTIVE icon](/images/TIA/icon_defective.png) | DEFECTIVE |
| ![Unknown state icon](/images/TIA/icon_unkown.png) | Unknown state |
| ![No state display icon](/images/TIA/icon_nostate.png) | Device does not allow state display |

**User programs (SOFTWARE)** can be evaluated online for their functionality, but in Siemens TIA Portal this requires an additional action: the monitoring function must be enabled for each building block.

![Monitoring in Siemens TIA Portal](/images/TIA/monitoring.png "Monitoring in Siemens TIA Portal") 

After this, the status is displayed with colors and dotted lines.

|  Condition | Example | Description |
| :---: | :---: | :--- |
| Condition 1 | ![Dotted blue lines](/images/TIA/condition1.png) | Both input A and input B are deactivated, causing output R to have the status FALSE because the result of the OR gate is FALSE |
| Condition 2 | ![Full green lines](/images/TIA/condition2.png) | Input A is activated, causing output R to have a TRUE status because the result of the OR gate is TRUE |

In Siemens TIA Portal, you can compare the ES user program (OFFLINE) and the RT user program (ONLINE). The status is displayed as icons to the right of the building blocks.

| Icon | Description |
| :---: | :--- |
| ![Fault icon](/images/TIA/compare_icon1.png) | Software error, may also be displayed in combination with other icons |
| ![Difference icon](/images/TIA/compare_icon2.png) | There is a difference between the offline and online blocks |
| ![Only online icon](/images/TIA/compare_icon3.png) | Block only exists in the online version |
| ![Only offline icon](/images/TIA/compare_icon4.png) | Block only exists in the offline version |
| ![OK icon](/images/TIA/compare_icon5.png) | The offline and online blocks are the same |

Please note that in Siemens TIA Portal it is possible to make changes to both the ES user program (OFFLINE) and the RT user program (ONLINE).

## Beckhoff TwinCAT 3

Download in Beckhoff TwinCAT 3 is called *‘Activate configuration’*.

| Downloading in TwinCAT 3| |
| :---: | :---: |
| Activate configuration | ![Blue blocks button](/images/TwinCAT/activate_config.png "Activate configuration") |
| Restart in RUN mode| ![Green gear button](/images/TwinCAT/restart_run.png "Restart in RUN mode") |
| Login into RT environment| ![Green enter button](/images/TwinCAT/login.png "Login into RT environment") |
| Start | ![Play button](/images/TwinCAT/run.png "Start") |

What does "Activate configuration" do?
1. TwinCAT 3 Runtime is stopped
2. The "Device configuration" is downloaded
3. The software configuration is downloaded
4. TwinCAT 3 is restarted in Run Mode

In Beckhoff TwinCAT 3, there is less reliance on icons for device **(HARDWARE)** malfunctions and instead, you should consult the *‘device diagnostic inputs’*, where you will find a status description.

| Icon | Description |
| :---: | :--- |
| ![Input state](/images/TwinCAT/debug1.png) | S**EtherCAT Device** <br> <br> Inputs.DevState = status of Device 1 <br> - Link error detected <br> - I/O locked after link error (I/O reset required) <br> - At least one device indicates an error state <br> - … |
| ![Axis state](/images/TwinCAT/debug2.png) | **EtherCAT Device** <br> <br> InfoData.State = extra information from Axis 7 <br> - Invalid vendorId, productCode... read <br> - Slave not present <br> - Slave signals error <br> - … |
| ![Term state](/images/TwinCAT/debug3.png) | **EtherCAT Slave Device** <br> <br> WcState.WcState = status of Term 2 <br> - Status FALSE = EtherCAT connection OK <br> - Status TRUE = error EtherCAT connection |

Furthermore, it's possible to consult the error list after compiling, which displays device failures and errors in the user program. Double-clicking an error displays the corresponding error.

![TwinCAT 3 Error List](/images/TwinCAT/error_list.png "TwinCAT 3 Error List")

In TwinCAT 3, the status of the **user program (SOFTWARE)** is also displayed with colors and dotted lines. Logging in to the RT user program automatically activates the monitoring function for all building blocks.

In TwinCAT 3, it is not possible to compare the ES user program (OFFLINE) and the RT user program (ONLINE). It is also not possible to make changes in the RT user program (ONLINE).