# Device configuration

The creation and editing of the available modules, such as CPU, digital input
modules, analogue input modules, digital output modules, etc., is done in the
‘**Device configuration**’ or hardware configurator of the ES software package.

The possible settings (also referred to as parameters) depend on the module.

- For input and output modules, it is possible to assign a unique absolute address to each PLC input and each PLC output
- For analogue input modules, it is possible to set a filter that cancels out the influence of alternating current (50 Hz, 60 Hz, etc.)
- For some analogue input and output modules, it is possible to set the electrical quantity (0 .. 10V, 0 .. 20 mA, 4 20mA, Pt100, etc.).
- For network connections on CPUs and communication modules, it is possible to set the network address. For serial networks, it is possible to set the communication speed.
- For some CPUs, it is possible to activate system bits (e.g. flash bits, BIT always TRUE, BIT always FALSE, etc.)

![Device configuration in TIA Portal](/images/TIA/device_config1.png "Device configuration in TIA Portal, ©2020 Siemens")
![Device configuration in TIA Portal](/images/TIA/device_config2.png "Device configuration in TIA Portal, ©2020 Siemens")

The absolute addresses at Siemens are displayed in the columns ‘I address’ and ‘Q address’. Beckhoff displays the absolute addresses in the columns ‘>Address’.

Modules can be added using the hardware catalogue, where a module can be dragged to the device configuration. The permitted locations are displayed with a blue square.

![TIA Portal hardware catalogue in TIA Portal](/images/TIA/hw_catalog1.png "TIA Portal hardware catalogue in TIA Portal, ©2020 Siemens") ![TIA Portal hardware catalogue in TIA Portal](/images/TIA/hw_catalog2.png "TIA Portal hardware catalogue in TIA Portal, ©2020 Siemens")

![Device configuration in TwinCAT 3](/images/TwinCAT/hw_catalog1.png "Device configuration in TwinCAT 3, ©2020 Beckhoff") ![Device configuration in TwinCAT 3](/images/TwinCAT/hw_catalog2.png "Device configuration in TwinCAT 3, ©2020 Beckhoff")

Modules can be added by selecting the desired device in the Devices tree structure to which a module is to be added. Then, right-click to open a context menu and select ‘Add new item’. The Beckhoff catalogue will then be displayed. Please note that the catalogue only shows the permitted modules (and therefore not all modules).

![TwinCAT 3 hardware catalogue](/images/TwinCAT/hw_catalog3.png "TwinCAT 3 hardware catalogue, ©2020 Beckhoff")
![TwinCAT 3 hardware catalogue](/images/TwinCAT/hw_catalog4.png "TwinCAT 3 hardware catalogue, ©2020 Beckhoff")

When starting a new project where the CPU type is unknown, it is possible to
upload the data of the CPU and the connected modules at a later stage.

| Manufacturer |    |                                                      |
|:------------:|:---|:----------------------------------------------------:|
| Beckhoff     | ![Scan](/images/TwinCAT/scan.png) | Upload device configuration via I/O / Devices / Scan |
| Siemens      | ![Detect](/images/TIA/detect.png) | Adding an Unspecific CPU via *“Add new device”*      |
