# Areas
## Areas of application

The entire system, consisting of processor(s), memory(s), and other electronic components, can be found in various configurations, designs, and sizes.
These include:
- Micro-controllers
- PLCs

A **micro-controller** consists of a printed circuit board built around a single chip containing the following components:
- A processor
- A memory for the user program
- A memory for storing data

The printed circuit board also includes:
- A connection to activate the user program
- A power supply connection
- The necessary connections for peripherals
- The necessary communication ports (e.g., USB port)

![Siemens IoT2000](/images/siemens_iot2000.png "IoT2000 micro-controller, ©2020 Siemens")

Micro-controllers are used when the system needs to be compact and/or where the number of sensors and actuators is limited, and are primarily integrated into electrical devices. Examples:
- Robot lawn mower
- Frequency controller
- Displays

A **PLC** system consists of a mounting rail on which various modules are mounted, such as:
- A processor module containing a processor, memory, and a network connection
- A power supply module
- An input module to which the sensors are connected
- An output module to which the actuators are connected
- A communications module if additional network connections are required

![Siemens S7-1500](/images/Siemens_s7_1500.png "S7-1500 PLC system, ©2020 Siemens") ![Beckhoff Cx](/images/Beckhoff_cx.png "CX PLC system, ©2020 Beckhoff")

PLC systems can be expanded by adding network components such as displays, frequency controllers, etc. They are primarily used in mechanical engineering and technical installations. Therefore, PLC systems are often installed in electrical cabinets.

> PLC = **P**rogrammable **L**ogic **C**ontroller

## Areas of expertise
Industrial automation can be divided into two disciplines:
- Automation
- Process automation (also called measurement and control technology)

Both disciplines share commonalities, but have their differences. The main difference lies in the required knowledge of the product being handled:
- With automation, the product doesn't need to be known in detail, as it's often packaged in boxes, containers, pallets, etc.
- With process automation, the product's properties must be thoroughly understood to prevent dangerous and/or unknown situations from arising when the actuators change their state.

The figures below illustrate both areas:
- The physical properties (boiling point, physical state, coefficient of expansion, water absorption, etc.) of the various ingredients must be known to produce a soft drink = Process automation
- Only the properties (weight, dimensions, material, etc.) of the bottles need to be known for processing (sorting, packaging, stacking on pallets, etc.) = Automation

![Process automation](/images/Siemens_process_automation.png "Process Automation - Preparing Soft Drinks, ©2019 Siemens")

![Automation](/images/Siemens_automation.png "Automation – Processing filled bottles (soft drinks) , ©2019 Siemens")