# Engineering software

Engineering software is bundled into a single software package for each manufacturer and can be divided into the following sections:
- Hardware configurator, where you can add and configure the various PLC modules
- Building block configurator, where you can add and edit building blocks and program software code
- Network configurator, which manages and configures the various network connections
- HMI configurator, where you can configure and program optional displays (e.g., touchscreens)

![Software parts](/images/Software_parts.png "Software parts")

Some parts allow you to modify, limited, settings from another configurator. This allows you to:
- Configure the network settings of an HMI in the HMI configurator
- Configure the network settings of the hardware in the hardware configurator

The table below provides a brief overview of:
- The ES packages included in this ebook
- The naming conventions in the ES packages by manufacturer

| | Siemens | Beckhoff |
| :--- | :---: | :---: |
| Engineering software | TIA Portal V15 SP1 <br> ![TIA Portal V15.1](/images/TIA_icon.png)| TwinCAT® 3 XAE (2013) <br> ![TwinCAT 3 XAE](/images/Twincat_icon.png) |
| Hardware configurator | Devices/PLC | I/O / Devices |
| Blocks configurator| Program blocks | PLC / POUs <sup>1</sup> |
| Network configurator| Networks | NA <sup>2</sup> |
| HMI configurator| Devices/HMI | TC3 HMI |

<sup>1</sup> *POU = **P**rogram **O**rganization **U**nit* <br>
<sup>2</sup> *NA = Not Available = The Beckhoff network configurator is integrated into the hardware configurator*

The configurations are worked out in projects which can contain multiple PLCs, HMIs and networks.

![Create a TwinCAT project](/images/Twincat_project1.png "Create a TwinCAT project ©2020 Beckhoff") ![Create a TwinCAT project](/images/Twincat_project2.png "Create a TwinCAT project ©2020 Beckhoff")

![Create a TIA Portal project](/images/TIA_project1.png "Create a TwinCAT project ©2020 Siemens") ![Create a TIA Portal project](/images/TIA_project2.png "Create a TwinCAT project ©2020 Siemens")

It is often possible to purchase expansion packages to enable:
- Use larger/complex HMI screens
- Integrate drives (e.g., servo drives)
- …

![TIA Portal overview](/images/TIA_overview.png "TIA Portal overview ©2020 Siemens") ![TwinCAT overview](/images/Twincat_overview.png "TwinCAT overview ©2020 Beckhoff")