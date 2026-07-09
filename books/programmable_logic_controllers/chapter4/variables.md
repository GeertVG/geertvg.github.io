# Variables
---
As with programmable controllers, variables, also called tags, are used to identify data objects by means of a symbolic representation and the use of a data type. These variables can be linked to HMI objects such as push buttons, text fields, lamps, ... to create an interactive environment.

![HMI tags](/images/hmi_tags.png "HMI tags in Siemens TIA Portal and Beckhoff TwinCAT 3") 

There are two types of variables:
-	Internal variables that can only be used by the HMI screen
-	External variables that are linked to a variable from a programmable controller

Both Beckhoff TwinCAT 3 and Siemens TIA Portal use symbolic representation, whereby external variables automatically adopt the symbolic name from the programmable controller. Furthermore, if this symbolic name changes in the programmable controller, it will be automatically updated in the HMI ES software package after compilation.

Depending on the type of screen, it is possible to set optional properties for external variables.
-	Refresh time<sup>1</sup>  : How often should the status of a variable be updated?
-	Refresh method: When should the status of a variable be updated?


For example, a variable can be refreshed continuously every 1 second (time & method) or every 100 milliseconds only when the linked object is displayed (time & method). If these optional properties are not available, the variables are continuously updated at the shortest possible refresh time.

![Siemens HMI variables](/images/vars_Siemens_hmi.png "HMI variables in TIA Portal V15 SP1, ©2020 Siemens") 

<sup>1</sup> *Also referred to as refresh rate or acquisition cycle*