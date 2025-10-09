# Programming according IEC 61131
## Programming languages

In a programmable logic controller, it is possible to work with different programming languages, which can be divided into:
- Graphic programming languages
- Textual programming languages

Graphical programming languages are easy to use but limited in their capabilities. Textual programming languages are more complex but more elaborate.

| Programming language        | Acronym       | Type       |
|:---------------------------:|:-------------:|-:---------:|
| Function Block Diagram      | FBD           | Graphic  |
| Ladder Diagram              | LD<sup>1</sup>| Graphic  |
| Sequential Function Chart   | SFC           | Graphic  |
| Instruction List            | IL<sup>2</sup>| Textual  |
| Structured Text             | ST<sup>3</sup>| Textual  |

<sup>1</sup> *Called LAD by Siemens* <br>
<sup>2</sup> *Called STL by Siemens (Statement List)* <br>
<sup>3</sup> *Called SCL by Siemens (Structured Control Language)* <br>

It is possible to use different programming languages together in a single PLC project, but only one programming language is permitted within a single block.

The **function block diagram** is a programming language whose graphic symbols are described in the IEC 60617-12 & 13 standard – Graphic symbols for binary logic & analogue elements, in which programming is done with AND, OR, etc. gates, with instructions being collected in networks.

![Example FBD programming language (Beckhoff)](/images/FBD.png "Example FBD programming language (Beckhoff)")

The **ladder diagram** is a programming language that bears strong similarities to electrical circuits, but its instruction set is rather limited. As with FBD, instructions are collected in networks.

![Example LD programming language (Siemens)](/images/LAD.png "Example LD programming language (Siemens)")

The **sequential function chart** programming language consists of a collection of different steps that are directly linked by transition conditions. Actions are linked to each step. Because the status of different elements (such as steps) must be retained, the programming language can only be used in function building blocks and/or organization building blocks. 

The SFC programming language bears strong similarities to GRAFCET but is not 100% identical:
- GRAFCET is a solution method for sequential processes that is programming language independent - IEC 60848
- SFC is a programming language - IEC 61131

The transition conditions are programmed in the SFC programming language using a programming language of your choice, but at Siemens these are limited to the LD and FBD programming languages.

![Example SFC programming language (Siemens)](/images/SFC.png "Example SFC programming language (Siemens)")

In the **instruction list** programming language, software instructions are programmed line by line and grouped into networks. The instructions often have an equivalent in the FBD and LD programming languages.

![Example IL programming language (Beckhoff)](/images/IL.png "Example IL programming language (Beckhoff)")

```Trivia
If the programming language instruction list is not available in Beckhoff TwinCAT 3, the following items must be activated in the Options > PLC Environment > FBD, LD and IL editor section: 
•	Show network title
•	Show network comment
•	Enable IL
```

Finally, the **structured text** programming language does not use FBD and LD equivalents but is based on the PASCAL computer programming language.

![Example ST programming language (Siemens)](/images/ST.png "Example ST programming language (Siemens)")

To detect programming errors, it is possible to display the status of variables and instructions online. To do this, it is necessary to connect to the CPU both physically (using a download cable) and virtually by connecting the ES project to the CPU. Detecting errors is called ‘debugging’.

Overview of establishing a virtual connection:
- Beckhoff
	- “Choose Target…” in the System map and next the preferred CPU
	![Beckhoff choose target](/images/TwinCAT/choose_target.png)
	- Log in on the CPU
	- Open the preferred building blocks
- Siemens
	- Select "Go Online"
	![Siemens go online](/images/TIA/go_online.png)
	- Open the preferred building blocks
	- Press the push button with the glasses symbol
	![Siemens monitor state](/images/TIA/monitor.png)

## Programming in LD/FBD
### General

**Instructions** can be inserted into building blocks using an instruction toolbox. Instructions can be dragged and dropped into the desired network.

If the desired instruction is not immediately visible in the instruction toolbox, it is possible to insert an ‘empty box’ or empty instruction. By clicking on the empty instruction, it is possible to select and insert the desired instruction from a list (Siemens) or to open various libraries (Beckhoff).
Using basic instructions (NOT, AND, OR, XOR, COIL, FlipFlop and edges), it is possible to design a user program (also known as programming) using only instructions that process BOOLs.

The following chapters explain the various basic logical instructions and use letters to represent a bit signal. Here, signals A and B are BOOL input signals and R is a BOOL output signal (the result).
The operation of different instructions is explained using a truth table that shows the result for each possible input combination.

| Beckhoff | Siemens |
|:--------:|:-------:|
| ![Beckhoff instructions toolbox](/images/TwinCAT/instructions.png)| ![Siemens instructions toolbox](/images/TIA/instructions.png)|

If you want to add time delays, you should use timers. Counters can be used to count individual items. Finally, you can use extensive instructions for mathematical operations and for converting one numerical data type to another.

```Trivia
Some basic instructions are not available in the Beckhoff toolbox (e.g. CTUD function block). 
Using an empty instruction, you can insert the missing instructions from the Function blocks > Tc2_Standard library. 
```

### NOT instruction (NOT)

The NOT-instruction ensures that a BOOL signal is inverted and represented by a ‘dot’. This can be placed before or after an instruction.

<u>Graphic representation</u>

|          | IEC view | Mathematical view              |
|:--------:|:--------:|:------------------------------:|
| Input    | ![NOT as input](/images/Prog/not_in.png)   | ![NOT](/images/Math/not.png)  |
| Output   | ![NOT as output](/images/Prog/not_out.png) |                    |

<u>Truth table</u>

| A   | R   |
|:---:|:---:|
| 0   | 1   |
| 1   | 0   |

<u>Programming examples</u>

| Manufacturer | FBD | LD equivalent |
|:------------:|:---:|:-------------:|
| Beckhoff     | ![NOT](/images/TwinCAT/fbd_not.png) | ![NOT](/images/TwinCAT/lad_not.png) |
| Siemens      | ![NOT](/images/TIA/fbd_not.png)     | ![NOT](/images/TIA/lad_not.png)     |

If you invert the same signal twice, you get the original signal.

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![NOT is //NOT](/images/Prog/not_is_not.png) | ![NOT is //NOT](/images/Math/not_is_not.png)  |

### AND instruction (AND)

With the AND instruction, all inputs must be TRUE to activate the output (R).

<u>Graphic representation</u>

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![AND](/images/Prog/and.png) | ![AND](/images/Math/and.png)  |

<u>Truth table</u>

| A   | B   | R   |
|:---:|:---:|:---:|
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

<u>Programming examples</u>

| Manufacturer | FBD | LD equivalent |
|:------------:|:---:|:-------------:|
| Beckhoff     | ![AND](/images/TwinCAT/fbd_and.png) | ![AND](/images/TwinCAT/lad_and.png) |
| Siemens      | ![AND](/images/TIA/fbd_and.png)     | ![AND](/images/TIA/lad_and.png)     |

It is possible to expand the number of input signals in FBD:
- Beckhoff: AND (3 inputs) or via pop-up menu
- Siemens: Add by clicking on the yellow star or via pop-up menu

The pop-up menu can be opened by selecting the AND instruction and then clicking on the other mouse button.

| Beckhoff | Siemens |
|:--------:|:-------:|
| ![Beckhoff expand input](/images/TwinCAT/expand_input.png)| ![Siemens expand input](/images/TIA/expand_input.png)|

If the number of input signals is insufficient (FBD), multiple AND gates can be connected together.

![Multiple ANDs](/images/TwinCAT/multiple_and.png)

If all input signals and the output signal of an AND gate are inverted, the result is the operation of an OR gate. 
An AND gate whose output signal is inverted is called a NAND gate.

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![NAND](/images/Prog/nand.png) | ![NAND](/images/Math/nand.png) |

### OR instruction (OR)

In the OR instruction, there must be at least one TRUE input to activate the output (R).

<u>Graphic representation</u>

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![OR](/images/Prog/or.png) | ![OR](/images/Math/or.png)  |

<u>Truth table</u>

| A   | B   | R   |
|:---:|:---:|:---:|
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 1   |

<u>Programming examples</u>

| Manufacturer | FBD | LD equivalent |
|:------------:|:---:|:-------------:|
| Beckhoff     | ![OR](/images/TwinCAT/fbd_or.png) | ![OR](/images/TwinCAT/lad_or.png) |
| Siemens      | ![OR](/images/TIA/fbd_or.png)     | ![OR](/images/TIA/lad_or.png)     |

It is possible to expand the number of input signals in FBD:
- Beckhoff: OR (3 inputs) or via pop-up menu
- Siemens: Add by clicking on the yellow star or via pop-up menu

If the number of input signals is insufficient (FBD), multiple OR gates can be connected together.

![Multiple ORs](/images/TwinCAT/multiple_or.png)

If all input signals and the output signal of an OR gate are inverted, the result is the operation of an AND gate. An OR gate whose output signal is inverted is called a NOR gate.

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![NOR](/images/Prog/nor.png) | ![NOR](/images/Math/nor.png) |

### Exclusive OR instruction (XOR)

With the XOR instruction, only one input signal may be TRUE in order to activate the output (R).

<u>Graphic representation</u>

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![XOR](/images/Prog/xor.png) | ![XOR](/images/Math/xor.png)  |

<u>Truth table</u>

| A   | B   | R   |
|:---:|:---:|:---:|
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |

<u>Programming examples</u>

| Manufacturer | FBD | LD equivalent |
|:------------:|:---:|:-------------:|
| Beckhoff     | ![XOR](/images/TwinCAT/fbd_xor.png) | ![XOR](/images/TwinCAT/lad_xor.png) |
| Siemens      | ![XOR](/images/TIA/fbd_xor.png)     | ![XOR](/images/TIA/lad_xor.png)     |

It is possible to expand the number of input signals in FBD at Siemens by clicking on the yellow star or by using the pop-up menu. The output result (R) will be TRUE if an odd number of input signals are TRUE.

If the number of input signals is insufficient (FBD), multiple XOR gates can be connected together.

![Multiple XORs](/images/TwinCAT/multiple_xor.png)

An XOR gate whose output signal is inverted is called an XNOR gate.

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![XNOR](/images/Prog/xnor.png) | ![XNOR](/images/Math/xnor.png) |

What if an XOR gate contains more than two input signals?
- The result is TRUE if the number of TRUE input signals is odd
- In all other cases, the result is FALSE

### Assignment (COIL)

The COIL instruction ensures that a PLC memory variable (%M) or a PLC output variable (%Q) of the BOOL data type continuously has the value TRUE or FALSE depending on the logical result for the COIL instruction.

<u>Programming examples</u>

| Manufacturer | FBD | LD equivalent |
|:------------:|:---:|:-------------:|
| Beckhoff     | ![COIL](/images/TwinCAT/fbd_coil.png) | ![COIL](/images/TwinCAT/lad_coil.png) |
| Siemens      | ![COIL](/images/TIA/fbd_coil.png)     | ![COIL](/images/TIA/lad_coil.png)     |

The COIL instruction does not exist in Beckhoff's FBD programming language, but it is possible to immediately assign a variable to an output result (e.g. AND instruction) using the ‘Assignment’ instruction, which has the same effect as the COIL instruction.

| Condition   | Online view | Comment |
|:-----------:|:---:|:-----------------------------------------------------------------------------------------------------------------------------:|
| Condition 1 | ![Condition 1](/images/TIA/cond1.png) | Both input A and input B are deactivated, <br> causing output R to have the status FALSE <br> because the result of the OR gate is FALSE |
| Condition 2 | ![Condition 2](/images/TIA/cond2.png) | Input A is activated, causing output R to <br> have the status TRUE because the result <br> of the OR gate is TRUE |
| Condition 3 | ![Condition 3](/images/TIA/cond3.png) | Input B is activated, output R retains the <br> TRUE status |
| Condition 4 | ![Condition 4](/images/TIA/cond4.png) | Input A and input B are deactivated, <br> causing output R to have the status FALSE <br> because the result of the OR gate is FALSE |
| Condition 5 | ![Condition 5](/images/TIA/cond5.png) | Input B is activated, causing output R to <br> have the status TRUE because the result of <br> the OR gate is TRUE |

It is possible to add a NOT instruction to a COIL instruction or to use a negating COIL instruction.

<u>Programming examples</u>

| Manufacturer | FBD | LD equivalent |
|:------------:|:---:|:-------------:|
| Beckhoff     | ![NOT COIL](/images/TwinCAT/fbd_ncoil.png) | ![NOT COIL](/images/TwinCAT/lad_ncoil.png) |
| Siemens      | ![NOT COIL](/images/TIA/fbd_ncoil.png)     | ![NOT COIL](/images/TIA/lad_ncoil.png)     |

### FlipFlop (SR/RS)

Using a flip-flop instruction, it is possible to assign the status TRUE or FALSE to a PLC memory (%M) or a PLC output variable (%Q) of the data type BOOL and to retain this status even if the logical result is no longer TRUE. This creates a kind of ‘memory function’.

To achieve this, a flip-flop is provided with two input variables:
- SET (S) = Activate the TRUE status
- RESET (R) = Activate the FALSE status

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![SR](/images/Prog/sr.png) | ![SR](/images/Math/sr.png) |

<u>Truth table</u>

| A (S1) | B (R)  | Q1   |
|:------:|:------:|:----:|
| 0      | 0      | On changed |
| 0      | 1      | 1   |
| 1      | X      | 1   |

As soon as one of the input variables has the status TRUE, the status of the flip-flop instruction is adjusted. If the status of both input variables is FALSE, the status of the flip-flop instruction will not be changed. 

If the status of both input variables is TRUE, the status of the flip-flop instruction will be determined by the priority input marked with the number 1.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![RS](/images/Prog/rs.png) | ![RS](/images/Math/rs.png) |

<u>Truth table</u>

| A (S1) | B (R)  | Q1   |
|:------:|:------:|:----:|
| 0      | 0      | On changed |
| X      | 1      | 0   |
| 1      | 0      | 1   |

<u>Programming examples</u>

| Manufacturer | Priority SET  | Priority RESET |
|:------------:|:-------------:|:--------------:|
| Beckhoff     | ![SR](/images/TwinCAT/sr.png)  | ![RS](/images/TwinCAT/rs.png) | 
| Siemens      | ![RS](/images/TIA/rs.png)      | ![SR](/images/TIA/sr.png)     | 

When creating a flip-flop in Beckhoff, the ES software package asks you to create the corresponding instance data, which is displayed above the flip-flop instruction. In Siemens, no instance data is created, but a free PLC memory (%M) BOOL variable must be assigned. However, the operation is similar to that of instance data (making the status of the internal variable unique). Using the instance data/free memory flag, the CPU can store the status of the flip-flop instruction during RT.

To link the output result of a flip-flop instruction to a PLC memory flag (%M) or a PLC output variable (%Q) of the BOOL data type, the COIL instruction must be used.

| Condition   | Online view | Comment |
|:-----------:|:---:|:-----------------------------------------------------------------------------------------------------------------------------:|
| Condition 1 | ![Condition 1](/images/TIA/flipflop1.png) | Input A, input B and output R are deactivated |
| Condition 2 | ![Condition 2](/images/TIA/flipflop2.png) | Output R is TRUE because the SET input of <br> the flip-flop has been activated. <br> This causes the status of the flip-flop <br> to become TRUE, which is presented at output Q |
| Condition 3 | ![Condition 3](/images/TIA/flipflop3.png) | The SET input of the flip-flop has the status <br> FALSE, but the status of the flip-flop remains TRUE! <br> As a result, the output R retains the status TRUE |
| Condition 4 | ![Condition 4](/images/TIA/flipflop4.png) | The status of output R is FALSE because the <br> RESET input of the flip-flop has been activated. <br> This causes the status of the flip-flop <br> to become FALSE, which is presented at output Q |

### Edge detection (R_TRIG/F_TRIG)

Flank detection is used to detect the change in state of a BOOL variable. A distinction is made between:
- Positive edge detection = variable that changes from FALSE to TRUE, also know as positive edge
- Negative edge detection = variable that changes from TRUE to FALSE, also know as negative edge

<u>Graphic representation</u>

|              | IEC view LD | IEC view FBD |
|:------------:|:-----------:|:------------:|
| Rising edge  | ![RE](/images/Prog/re_lad.png) | ![RE](/images/Prog/re_fbd.png) |
| Falling edge | ![FE](/images/Prog/fe_lad.png) | ![RE](/images/Prog/fe_fbd.png) |

The output of an edge instruction will only be TRUE at the moment the transition is detected (order of magnitude ms). To determine this, the instruction requires a PLC memory flag (%M) at Siemens. Beckhoff uses instance data.

<u>Programming examples</u>

| Manufacturer | FBD | LD equivalent |
|:------------:|:---:|:-------------:|
| Beckhoff     | ![RE & FE](/images/TwinCAT/fbd_trig.png) | ![RE & FE](/images/TwinCAT/lad_trig.png) |
| Siemens      | ![RE & FE](/images/TIA/fbd_trig.png)     | ![RE & FE](/images/TIA/lad_trig.png)     |

### Copy (MOVE)

Using the MOVE instruction, it is possible to copy the contents of an input variable to an output variable. The input and output variables are of the type BYTE, WORD, DWORD, LWORD or ANY_NUM, whereby the data types of both variables can be the same or different.

The MOVE instruction is executed as soon as the status of the AND input is TRUE. If no variable is assigned to the AND input, the instruction is executed continuously.

<u>Programming examples</u>

| Manufacturer | FBD & LD | 
|:------------:|:---:|
| Beckhoff     | ![MOVE](/images/TwinCAT/move.png) | 
| Siemens      | ![MOVE](/images/TIA/move.png)     | 

Siemens offers the option of expanding the number of output variables, making it possible to copy the value of the input variable to multiple output variables simultaneously.

### IEC Timers (TON/TOF/TP)

A timer with an on-delay or **on-delay timer** will ensure that the output [Q] is activated a certain time or Preset Time [PT] later than the input signal [IN].

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![TON](/images/Prog/ton.png) | ![TON](/images/Math/ton.png) |

![TON](/images/Math/ton_scheme.png)

<u>Programming examples</u>

| Manufacturer | Timer | FBD example | 
|:------------:|:-----:|:-----------:|
| Beckhoff     | ![TON](/images/TwinCAT/ton1.png) | ![TON](/images/TwinCAT/ton2.png) |  
| Siemens      | ![TON](/images/TIA/ton1.png)     | ![TON](/images/TIA/ton2.png) | 

When creating a timer, the ES software package asks you to create the corresponding instance data. Using the instance data, the CPU can store the remaining time in the PLC memory during RT.

```Example
In some cars, the low beam is automatically switched on by a light sensor. 
As soon as the light sensor no longer detects any light during a certain waiting period, the low beam is switched on.

The waiting period is necessary to prevent the low beam from being switched on every time you drive under a bridge, for example.
-	The low beams switch on with a delay 
```

A timer with delay or **off-delay timer** ensures that the output [Q] remains activated for a certain time or Preset Time [PT] after the input signal [IN] has been deactivated.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![TOF](/images/Prog/tof.png) | ![TOF](/images/Math/tof.png) |

![TOF](/images/Math/tof_scheme.png)

<u>Programming examples</u>

| Manufacturer | Timer | 
|:------------:|:-----:|
| Beckhoff     | ![TOF](/images/TwinCAT/tof.png) |  
| Siemens      | ![TOF](/images/TIA/tof.png)     | 

```Example
Some cars are equipped with a ‘Coming Home’ function. 
This causes the car's low beam headlights to remain on for about 30 seconds after the key has been removed from the ignition.
-	The low beams switch off with a delay.
```

A **pulse timer** ensures that the output signal [Q] is activated for exactly the set time or Preset Time [PT] as soon as the input signal [IN] is activated.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![TP](/images/Prog/tp.png) | ![TP](/images/Math/tp.png) |

![TP](/images/Math/tp_scheme.png)

<u>Programming examples</u>

| Manufacturer | Timer | 
|:------------:|:-----:|
| Beckhoff     | ![TP](/images/TwinCAT/tp.png) |  
| Siemens      | ![TP](/images/TIA/tp.png)     | 

```Example
If a car is driving too fast, it may be caught by a speed camera. 

The flash must work correctly. 
If it flashes for too short a time, the photo will be underexposed (the photo will be too dark = black will dominate), 
but if it flashes for too long, the photo will be overexposed (the photo will be too bright = white will dominate).
-	The flash lamp should not be too short or too long.
```

### IEC Counters (CTU/CTD/CTUD)

A counter is used to increment or decrement a decimal number by one. The decimal number can be of the following data types:
- INT – Integer
- DINT – Double integer
- LINT – Long integer
- UDINT – Unsigned double integer
- ULINT – Unsigned long integer

The minimum and maximum values of the decimal number depend on the selected data type.
An **up counter** will increment a decimal number by one whenever a rising edge signal (internal to the device) is detected at the count-up [CU] input. Once the current counter value is greater than or equal to the preset value [PV] input, the output [Q] will be activated.

The counter value can be set to 0 by activating the reset [R] input. The current counter value is provided at the current value [CV] output.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![CTU](/images/Prog/ctu.png) | ![CTU](/images/Math/ctu.png) |

```Example
A waiting room is often equipped with a display and a ticket machine. 
The next customer or patient's turn is shown on the display, which displays a queue number. 
Each customer or patient has taken a paper queue number from the ticket machine.
-	Each time the operator presses the ‘next customer’ button, the display increases by 1
-	When the maximum value is reached, it starts again with number 0 or 1
```

| Type      | Explanation                                      |
|:---------:|:-------------------------------------------------|
| CTU       | Counting up a INT number <br> *Count-Up INT*     |
| CTU_DINT  | Counting up a DINT number <br> *Count-Up DINT*   |
| CTU_LINT  | Counting up a LINT number <br> *Count-Up LINT*   |
| CTU_UDINT | Counting up a UDINT number <br> *Count-Up UDINT* |
| CTU_ULINT | Counting up a ULINT number <br> *Count-Up ULINT* |

<u>Programming examples</u>

| Manufacturer | Counter | FBD example | 
|:------------:|:-------:|:-----------:|
| Beckhoff     | ![CTU](/images/TwinCAT/ctu1.png) | ![CTU](/images/TwinCAT/ctu2.png) |  
| Siemens      | ![CTU](/images/TIA/ctu1.png)     | ![CTU](/images/TIA/ctu2.png) | 

When creating a counter, the ES software package prompts you to create the corresponding instance data. Using this instance data, the CPU can store the current counter value in the PLC memory during RT.

A **down counter** will decrease a decimal number by one whenever a rising edge signal (internally the module) is detected at the countdown [CD] input. As soon as the current counter value is less than or equal to zero, the output [Q] will be activated.

The counter value can be set to the preset value [PV] by activating the load [LD] input. The current counter value is presented at the current value [CV] output.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![CTD](/images/Prog/ctd.png) | ![CTD](/images/Math/ctd.png) |

| Type      | Explanation                                      |
|:---------:|:-------------------------------------------------|
| CTD       | Counting down a INT number <br> *Count-Down INT*     |
| CTD_DINT  | Counting down a DINT number <br> *Count-Down DINT*   |
| CTD_LINT  | Counting down a LINT number <br> *Count-Down LINT*   |
| CTD_UDINT | Counting down a UDINT number <br> *Count-Down UDINT* |
| CTD_ULINT | Counting down a ULINT number <br> *Count-Down ULINT* |

<u>Programming examples</u>

| Manufacturer | Counter | 
|:------------:|:-------:|
| Beckhoff     | ![CTD](/images/TwinCAT/ctd.png) | 
| Siemens      | ![CTD](/images/TIA/ctd.png)     | 

A **combination counter** is a combination of an upward and a downward counter.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------------:|
| ![CTUD](/images/Prog/ctud.png) | ![CTUD](/images/Math/ctud.png) |

| Type       | Explanation           |
|:----------:|-----------------------|
| CTUD       | *Count Up/Down INT*   |
| CTUD_DINT  | *Count Up/Down DINT*  |
| CTUD_LINT  | *Count Up/Down LINT*  |
| CTUD_UDINT | *Count Up/Down UDINT* |
| CTUD_ULINT | *Count Up/Down ULINT* |

<u>Programming examples</u>

| Manufacturer | Counter | 
|:------------:|:-------:|
| Beckhoff     | ![CTUD](/images/TwinCAT/ctud.png) | 
| Siemens      | ![CTUD](/images/TIA/ctud.png)     | 

```Example
Paid parking often have one or more displays showing how many empty parking spaces are available. 

The number of cars is counted at the point where they enter the lot (pass through the barrier and take a ticket) 
and at the point where they exit the lot (pass through the barrier and insert a paid ticket).
-	The number of empty parking spaces decreases every time a car enters the parking lot.
-	The number of empty parking spaces increases every time a car leaves the parking lot.
```

### Mathematical instructions

Mathematical instructions allows arithmetic operations to be performed on ANY_NUM variables.

When programming in LD/FBD, an arithmetic instruction is displayed as a box.
- The instruction type is indicated at the top of the box using an abbreviation.
- The inputs are displayed on the left side of the box.
- The output, with the arithmetic result, is displayed on the right side.
- All variables have the same data type.

Mathematical instructions can be divided into two groups:
- Operations on multiple integers (ANY_NUM variables)
- Operations on a single integer (ANY_REAL variables)

The group of operations on multiple integers includes addition, subtraction, division, multiplication, remainder after division, and working with exponents.

<u>Graphic representation</u>

| IEC view | Mathematical instruction |
|:--------:|:------------------------:|
| ![Math instructions](/images/Prog/math.png) | ![Math instructions](/images/Math/math.png) |

<u>Programming examples</u>

| Manufacturer | ADD | SUB | EXPT | 
|:------------:|:---:|:---:|:----:|
| Beckhoff     | ![ADD](/images/TwinCAT/add.png) | ![SUB](/images/TwinCAT/sub.png) | ![EXPT](/images/TwinCAT/expt.png) |
| Siemens      | ![ADD](/images/TIA/add.png) | ![SUB](/images/TIA/sub.png) | ![EXPT](/images/TIA/expt.png) |

Both Beckhoff and Siemens offer the option of expanding the number of inputs for mathematical instructions that can be performed on multiple numbers, with the exception of the EXPT and MOD instructions, where the number of inputs is limited to 2.

| Beckhoff | Siemens |
|:--------:|:-------:|
| ![Append input](/images/TwinCAT/add_input.png) | ![Insert input](/images/TIA/add_input.png) | 

An arithmetic instruction often has an AND/ENO input and output.
If the AND input is TRUE, or if no variable is provided, the instruction is executed. The ENO output becomes TRUE if the instruction is executed and is used to connect the various building blocks.

Beckhoff allows programming in the FBD language to work without an AND/ENO input and output. This allows the output result of one mathematical instruction to be connected to the input of another mathematical instruction.

|                | Mathematical instruction |
|:--------------:|:------------------------:|
| without EN/ENO | ![Without EN/ENO](/images/TwinCAT/without_eno.png)  |
| with EN/ENO    | ![With EN/EN](/images/TwinCAT/with_eno.png)  |

The group of mathematical operations on a single number includes trigonometric, exponential, and logarithmic instructions.

<u>Graphic representation</u>

| IEC view | Mathematical instruction |
|:--------:|:------------------------:|
| ![Math instructions](/images/Prog/math1.png) | ![Math instructions](/images/Math/math1.png) |

<u>Programming examples</u>

| Manufacturer | SIN | SQRT | EXP | 
|:------------:|:---:|:----:|:---:|
| Beckhoff     | ![SIN](/images/TwinCAT/sin.png) | ![SQRT](/images/TwinCAT/sqrt.png) | ![EXP](/images/TwinCAT/exp.png) |
| Siemens      | ![SIN](/images/TIA/sin.png) | ![SQRT](/images/TIA/sqrt.png) | ![EXP](/images/TIA/exp.png) |

It's not possible to increase the number of inputs for single-number mathematical instructions. The input variable must belong to the ANY_REAL group.
For trigonometric functions, the angle must be represented in radians instead of degrees.

![RAD conversion formula](/images/Math/rad_to_deg.png) 

### Comparison instructions

Comparison instructions are used to compare two numbers. The result of a comparison is either TRUE or FALSE and is therefore of the BOOL data type.
Comparison statements are executed between ANY_NUM variables of the same data type.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------:|
| ![Comparison instructions](/images/Prog/comp.png) | ![Comparison instructions](/images/Math/comp.png) |

It is not possible to expand the number of inputs for comparison instructions.

| Type instruction | Function            | Description              |
|:----------------:|:-------------------:|:-------------------------|
| GT_\*            | OUT := IN1 \> IN2   | Bigger then              |
| GE_\*            | OUT := IN1 \>= IN2  | Bigger than or equal to  |
| LT_\*            | OUT := IN1 \< IN2   | Smaller than             |
| LE_\*            | OUT := IN1 \<= IN2  | Smaller than or equal to |
| EQ_\*            | OUT := IN1 = IN2    | Equal to                 |
| NE_\*            | OUT := IN1 \<\> IN2 | Different then           |

### Conversion instructions

It is often necessary to convert ANY_NUM variables, which have a specific numeric data type, to another numeric data type. This can be done using conversion instructions.

<u>Graphic representation</u>

| IEC view | Explanation |
|:--------:|:-----------:|
| ![Conversion instructions](/images/Prog/conv.png) | ![Conversion instructions](/images/Math/conv.png) |

| Type instruction                   | Description                                                                    |
|:----------------------------------:|:-------------------------------------------------------------------------------|
| *General conversion instructions*  |                                                                                |
| IN**\_TO\_**OUT                    | E.g. from SINT to DINT = SINT_TO_DINT <br> E.g. from INT to REAL = INT_TO_REAL |
| *Specific conversion instructions* |                                                                                |
| ROUND                              | REAL to INT & round to the next whole (even) number                            |
| CEIL                               | REAL to INT & round to the upper integer                                       |
| FLOOR                              | REAL to INT & round to the lowest integer                                      |
| TRUNC                              | REAL to INT & dropping decimal places                                          |
| ABS                                | Absolute number                                                                |

The table below shows the different results when using specific conversion instructions.

| Number | ROUND | CEIL | FLOOR | TRUNC |
|:------:|:-----:|:----:|:-----:|:-----:|
| 1,01   | 1     | 2    | 1     | 1     |
| 1,00   | 1     | 1    | 1     | 1     |
| 0,99   | 1     | 1    | 0     | 0     |
| 0,51   | 1     | 1    | 0     | 0     |
| 0,50   | 0     | 1    | 0     | 0     |
| 0,49   | 0     | 1    | 0     | 0     |
| 0,00   | 0     | 0    | 0     | 0     |
| -0,49  | 0     | 0    | -1    | 0     |
| -0,50  | 0     | 0    | -1    | 0     |
| -0,51  | -1    | 0    | -1    | 0     | 
| -0,99  | -1    | 0    | -1    | 0     |
| -1,00  | -1    | -1   | -1    | -1    |
| -1,01  | -1    | -1   | -2    | -1    |

## Programming in ST
### General

### Structure

### Control structure IF ... THEN ... ELSE

### Control structure CASE ... OF ... ELSE

### Control structure WHILE ... DO

### Control structure REPEAT ... UNTIL

### Control structure FOR ... TO ... BY 
