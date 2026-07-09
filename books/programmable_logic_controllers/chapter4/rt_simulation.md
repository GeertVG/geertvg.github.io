# RT Simulation
---
RT simulation is a useful tool during the design process. It allows the HMI design to be tested, either in combination with a programmable controller or without, without the need for a real HMI screen.

![TIA Portal HMI simulation](/images/simulation_Siemens_hmi.png  "TIA Portal HMI starting simulation, ©2020 Siemens") 

Siemens TIA Portal RT simulation options:
-	Start = External variables originating from a real CPU 
-	With tag simulator = Status of variables is adjusted manually
-	With script debugger = Only applicable if scripts are present

In Beckhoff TwinCAT 3 the RT simulation is started in a similar way to the simulation of a programmable controller:

-	Execute ‘Activate configuration’ to transfer changes from the ES environment to the RT environment

![Beckhoff TwinCAT 3 HMI simulation](/images/simulation1_Beckhoff_hmi.png  "Beckhoff TwinCAT 3 HMI simulation, ©2020 Beckhoff") 

-	Then restart TwinCAT 3 in ‘Run Mode’

![Beckhoff TwinCAT 3 HMI simulation](/images/simulation2_Beckhoff_hmi.png  "Beckhoff TwinCAT 3 HMI simulation, ©2020 Beckhoff") 

-	Afterwords log in on the RT-environment

![Beckhoff TwinCAT 3 HMI simulation](/images/simulation3_Beckhoff_hmi.png  "Beckhoff TwinCAT 3 HMI simulation, ©2020 Beckhoff") 

-	Finally restart all

![Beckhoff TwinCAT 3 HMI simulation](/images/simulation4_Beckhoff_hmi.png  "Beckhoff TwinCAT 3 HMI simulation, ©2020 Beckhoff") 
