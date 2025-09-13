# Blocks according IEC 61131
## Program organization units (POU/OB)

A program organization unit, abbreviated as POU, provides a logical collection of all programming elements (instructions, functions and function blocks) and the execution of these programming elements in RT, whereby the MAIN organization block is continuously run through if the CPU is in RUN mode. 
The naming of program organization units may vary depending on the manufacturer:
-	Beckhoff = Program Organization Unit = POU
-	Siemens = Organization block = OB

| Manufacturer |      |
| :----------: | :--- |
| Beckhoff     | ![Create POU](/images/TwinCAT/create_pou.png) |
| Siemens      | ![Create OB](/images/TIA/create_ob.png)       |

The execution of a program organization units is carried out by a task. This determines when and/or how often the block is run (if the CPU is in RUN mode).

| Beckhoff | Siemens  |
| :------: | :------: |
| ![Create POU](/images/TwinCAT/main_pou.png) | ![Create OB](/images/TIA/main_ob.png) |
| The MAIN program organization unit is linked to the PlcTask task, whose settings can be found under SYSTEM/Tasks | The task is linked to the number and description of the organization block |


## Functions (FC)

Functions, abbreviated as FC, are used to divide the user program into different sub-sections. This makes it possible to structure the ES software user program. Functions can be called up from program organization units, function blocks and other functions.

A characteristic feature of functions is that they do not have internal memories, they can be called up multiple times and they display a single output result (=Return). The data type of the output result must be determined by the user. However, it is permitted to add your own interface input and output variables.

| Without interface variables | With interface variables  |
| :-------------------------: | :-----------------------: |
| ![Function](/images/function1.png) | ![Function](/images/function2.png) |

By adding a condition for the EN input of the function, it can be called conditionally. In other words, the function is only executed if the result of the instructions on the EN input is TRUE. If no condition is added, the function is always executed.
Furthermore, it is possible to add instructions to the ENO output.

| Manufacturer |      |
| :----------: | :--- |
| Beckhoff     | ![Create FC](/images/TwinCAT/create_fc.png) |
| Siemens      | ![Create FC](/images/TIA/create_fc.png)     |

Finally, you have the option of adding your own input and output variables. This can be done by declaring the input and output variables in the building block interface field. This interface field is located at the top and can be shown/hidden using the arrow keys.

| Manufacturer |      |
| :----------: | :--- |
| Beckhoff     | ![Interface FC](/images/TwinCAT/interface_fc.png) |
| Siemens      | ![Interface FC](/images/TIA/interface_fc.png)     |

The necessary variables must be created in the interface field. A distinction is made between:
- **Input** parameters: Variables that the function can only read 
- **Output** parameters: Variables that the function can only write 
- **InOut** parameters: Variables that the function can read and write
- **Temp** parameters: Temporary variables
- **Constant** parameters: Defining constants

| Manufacturer |      |
| :----------: | :--- |
| Beckhoff     | ![Create interface variables](/images/TwinCAT/interface_create.png) |
| Siemens      | ![Create interface variables](/images/TIA/interface_create.png)     |

```Trivia
If the Sequential Function Chart (SFC) programming language is selected in a Beckhoff project, it is not possible to add a function.
```

```Trivia
When creating a function in Siemens TIA Portal, the output result is not displayed. This is because the data type ‘VOID’ is assigned by default.
VOID is not a data type, but rather means ‘not in use’. Assigning an elementary data type makes the output result visible.
```

## Function blocks (FB)

Function blocks, abbreviated as FB, are used in the same way as functions to divide the user programs into different sub-sections. This makes it possible to structure the ES software user program. Function building blocks can be called up from program organization units, functions and other function blocks.

Function blocks differ from functions with their internal memories. 
- Functions have no internal memories 
- Functions blocks have internal memories known as instances

An instance allows a function block to be called up multiple times, but the status of the internal variables will be unique.

| Without interface variables | With interface variables  |
| :-------------------------: | :-----------------------: |
| ![Function block](/images/function_block1.png) | ![Function block](/images/function_block2.png) |

By adding a condition for the EN input of the function block, it can be called conditionally. In other words, the function block is only executed if the result of the instructions on the EN input is TRUE. If no condition is added, the function block is always executed.

It is also possible to add instructions to the ENO output.

As with functions, it is possible to add your own input and output variables. The necessary variables must be created in the interface field. A distinction is made between:
- **Input** parameters: Variables that the function block can only read
- **Output** parameters: Variables that the function block can only write
- **InOut** parameters: Variables that the function block can read and write
- **Static** parameters: Variables that are retained even in the event of a power failure (if set)
- **Temp** parameters: Temporary variables
- **Constant** parameters: Defining constants

| Manufacturer |      |
| :----------: | :--- |
| Beckhoff     | ![Create FC](/images/TwinCAT/create_fb.png) |
| Siemens      | ![Create FC](/images/TIA/create_fb.png)     |

```Trivia
The definition of an instance varies greatly from manufacturer to manufacturer:
- At Beckhoff, the instance will be defined by the function block, i.e. the instance is of the type ‘Function block’. In the Beckhoff example below, the instance ID_PE_StartStop is defined as FB_PE_StartStop.
- At Siemens, the instance is defined as an ‘instance data block’ or DB, whereby a data block serves solely to store data. In the Siemens example below, the instance ID_PE_StartStop is defined as %DB6.
```

| Beckhoff | Siemens  |
| :------: | :------: |
| ![FB example](/images/TwinCAT/example_fb.png) | ![FB example](/images/TIA/example_fb.png) |

## Data blocks (DB)

The use of data blocks is not described in the IEC 61131 standard and is only used by Siemens.
These are blocks that only contain data and no software instructions, of which there are two types:
- Instance data blocks = Automatically created by the ES package
- Global data blocks = Created by the user
