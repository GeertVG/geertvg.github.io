# Objects
---
## Screens
It is possible to add, remove and rename screens, and to adjust screen properties such as the background colour.

| Beckhoff | Siemens |
| :------: | :-----: |
| ![Beckhoff HMI](/images/add_Beckhoff_screen.png) | ![Siemens HMI](/images/add_Siemens_screen.png) |
| ![Beckhoff HMI](/images/add_Beckhoff_visualization.png)| ![Siemens HMI](/images/add_Siemens_template.png)  |

Siemens offers the option of working with ‘Templates’. These are backgrounds with static and/or dynamic objects that can optionally be displayed in other non-‘Template’ screens.

![Siemens HMI](/images/config_Siemens_template.png "Siemens HMI Template, ©2020 Siemens") 

## Static objects
Static elements are objects that do not change condition in RT and do not create new actions or conditions when clicked, for example. These elements are used to display information and include:
-	‘Flat’ text (=Label)
-	Lines, rectangles, circles, ... (=Line, rectangle, circle, ...)
-	Figures based on a graphic file (=Graphic view, Image)

In the ES software package, these elements are collected in a ‘Toolbox’ under the name ‘Basic objects’. 

| Beckhoff | Siemens |
| :------: | :-----: |
| ![Beckhoff HMI](/images/Beckhoff_basic_toolbox.png) | ![Siemens HMI](/images/Siemens_basic_objects.png) |

Adding a static element is done by selecting the object in the toolbox and then dragging it to the screen. Editing an object is done by selecting the object and then adjusting its properties.

Each object is unique and is defined by an ‘Element name’ or ‘Object name’ and by the screen on which it is displayed. In other words, the name is unique per screen. The location of the object is determined using X and Y coordinates, with the zero point located at the top left of the screen.

![Siemens HMI](/images/Siemens_properties.png "TIA Portal HMI toolbar & object properties, ©2020 Siemens") 

![Beckhoff HMI](/images/Beckhoff_properties.png "TwinCAT PLC Visualization toolbar & object properties, ©2020 Beckhoff")

## Dynamic objects
Dynamic objects are objects that change condition in RT or that create a new condition and/or start an action when triggered (e.g. by clicking on the object). These elements are used to display the status of a machine/installation and include:
-	Push buttons & switches
-	Lights & indicators
-	Alarm and notification tables
-	Graphs
-	User management
-	…

As with static objects, dynamic objects can be added from the toolbox and then modified using the ‘Properties’ windows. In addition to static properties (line colour, background colour, text properties, alignment, etc.), it is possible to assign dynamic properties such as:
-	Changing an object colour based on a variable (=Animations)
-	Changing the object location based on a variable (=Movements)
-	Showing or hiding an object based on a variable (=Visibility)
-	Changing object text based on a variable (=Text list)
-	Changing an object figure based on a variable (Graphic list)
-	Executing an instruction when clicking on an object (=Events)
-	Executing an instruction on a time basis (=Scheduled Tasks)
-	…

### Button
A ‘Button’ or push button allows an action to be started when an operator presses the push button or when he/she releases the push button. These are actions such as:
-	Changing screens
-	Resetting alarm(s)
-	Starting and stopping a machine or technical installation (or part thereof)
-	…



It is possible to use a figure instead of text to indicate the function of the push button.

### IO field / Text field
An ‘IO Field’ or ‘Text Field’ changes the content of a text field based on a numerical variable. Together with the numerical variable, a ‘Text list’ must be created in which the corresponding texts can be found.




Siemens TIA Portal offers the option of using a ‘Graphic IO Field’ in addition to a ‘Text Field’, which works in a similar way with figures.

### Switch
A ‘switch’ is a button that has two conditions:
-	An OFF condition
-	An ON condition

The ON and OFF conditions are displayed using two different symbols or two different texts. When the switch is operated once, it will change condition and remain in that condition until the switch is operated again.


### Bar
A ‘bar’ is often used to indicate the level in a liquid tank.



Static properties that can be set:
-	Background colour
-	Foreground colour
-	Axis settings (min. and max. label value, with/without indication, below/above indication or left/right indication)

### Alarm view / Event table
To use an ‘Event Table’ in Beckhoff TwinCAT 3, you must enable it in the ‘PLC project settings’. This adds the ‘Event table’ to the ‘Special controls’ toolbox.


This “Event table” Works together with the Beckhoff function block ‘FB_AdsReadEvents’, which is preferably programmed in the MAIN organisation block.

Alarm texts are created by adding a new ‘Event Class’ to the system (SYSTEM > TYPE SYSTEM > EVENT CLASSES > NEW).

Then open the new Event Class using the Edit push button.

Finally, add the necessary alarm and notification texts under ‘Events’.

By saving the ‘Event Class’, a variable list is automatically created or updated in the PLC project with the name GVL TC_Events, in which the alarms are processed. These variables can then be used during programming in the various building blocks.
Siemens TIA Portal uses an ‘Alarm view’ to display alarms and messages.

The alarms and notifications themselves are configured in the ‘HMI alarms’ section, where an absolute external WORD variable must be used.

Note that the HMI screen is ‘Little Endian’ oriented and the CPU is ‘Big Endian’ oriented. As a result, trigger  bit 8 is not %M1.0 but %M0.0 in the example.

###  Trend view / Histogram
A ‘Trend view’ or ‘Histogram’ is used to display graphs. This makes it possible to display multiple measured values on a single graph.

Static properties that can be set:
-	Background colour
-	Foreground colour
-	Font
-	Axis settings for the X-axis and Y-axis (min. and max. label value, with/without indication)

![Siemens HMI](/images/Siemens_trendview.png "HMI Trend view in TIA Portal V15 SP1, ©2020 Siemens") 

![Beckhoff HMI](/images/Beckhoff_histogram.png "HMI Histogram in TwinCAT 3, ©2020 Beckhoff")

## Tools
The ES software packages contain various tools that simplify screen design:
-	Use of a GRID on which objects are automatically aligned
-	Use of icons in the screen toolbar(s)
-	Use of ‘Wizards’ that allow step-by-step configuration of the HMI screen


