# Processing software
## Execution of blocks

The execution of blocks in RT starts in the program organization units (POU or OB) in which functions and function blocks are called up. The instructions are executed from top to bottom.
If a function or function block is present (e.g. FC1), the instructions in this block are first executed before the other instructions of the program organization unit are executed.

![Execution of blocks](/images/execution_blocks.png "Execution of blocks") 

It is permitted to call a function or function block within another function or function block (e.g. FB1 in FC2). 
As with program organization units, the instructions of the called function or function block are executed first before the remaining instructions are executed (e.g. instructions FC2 > instructions FB1 > instructions FC).

## Processing IO

During the execution of the user program, a snapshot is taken off the inputs statuses. This is known as the **process image input table**, abbreviated as **PII**. The reason for this is that during the execution of the RT user program, a sensor can change state, which can cause problems. 

The actuators are also controlled by means of a process image. The effective opening or closing of, for example, an output transistor will take place in the **process image output table**, abbreviated as **PIQ**, and not during the execution of the RT user program.

![Execution of inputs & outputs](/images/execution_io.png "Execution of inputs & outputs") 

The RT user program can only be executed, and the process images can only be created if the PLC is in RUN mode.

| Step   | Action                      |
|:------:|:----------------------------|
| 1      | Management tasks:<br> -   Working mode RUN? <br> -   Monitoring time OK? <br> -   Everything OK? So yes go to step 2 |
| 2      | Creation of the process image inputs table (PII)  |
| 3      | Execution of the user program                     |
| 4      | Creation of the process image outputs table (PIQ) |
|        | Go back to step 1                                 |

![Cycle time of old Siemens CPUs](/images/cycle_time_old_cpu.png "Cycle time of old Siemens CPUs") 

The above diagram provides a visual overview of the whole system and is referred to as a **cycle**. 

However, there is a disadvantage to this system, namely that in the very first cycle that is run after the CPU is started up (e.g. after a power failure), it is unclear whether the transistor or relay outputs are now closed or open (PIQ only comes at the end).

![Cycle time problem at old Siemens CPUs](/images/cycle_time_old_pf.png "Cycle time problem at old Siemens CPUs") 

This problem has been solved by shifting the process image of the outputs, making it possible to control the actuators immediately when the PLC starts up.

![Cycle time of current Beckhoff & Siemens CPUs](/images/cycle_time_new_cpu.png "Cycle time of current Beckhoff & Siemens CPUs") 

The scope of the PII and PIQ process images is determined by the CPU, whereby Siemens CPUs offer the option of not including inputs and outputs in the process image. To get the actual state of an input or output signal, directly within the RT program, you need to query the peripheral state. This can be processed by adding ‘:P’ to the absolute and symbolic address. Note that this is only permitted for 16-BIT and 32-BIT variables.

![To query the peripheral state of Siemens IO](/images/peripheral.png "To query the peripheral state of Siemens IO") 

## Cycle and reaction time

The total time required to complete one cycle is called the cycle time (order of magnitude ms).

![Cycle time](/images/cycle_time.png "Cycle time") 

The time required to run through the entire RT user program is called the **cycle time**. 
This time is not constant but depends on the length of the user program, the instruction set used (bit and word instructions) and the processing speed of the CPU. 

The **reaction time** is determined by the time between a sensor changing status and the time between the output of the corresponding actuator changing state, and is max. 2 times the cycle time.

![Reaction time](/images/reaction_time.png "Reaction time") 

In order to prevent excessive disruption in the event of a malfunction of the processor or the program, the processor is equipped with a monitoring system (watchdog function). The principle of this system is that the cycle time of a program must not exceed a certain value (default value of 150 ms for Siemens PLC). If the monitoring time is exceeded, this will cause the PLC to enter a STOP state.