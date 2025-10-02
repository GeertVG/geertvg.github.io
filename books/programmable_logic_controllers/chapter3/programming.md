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
|:--------:|:---------|:------------------------------:|
| Input    | ![NOT as input](/images/Prog/not_in.png)   | R = $\overline{A}$ |
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
| ![NOT is //NOT](/images/Prog/not_is_not.png) | A = $\overline\overline{A}$  |

### AND instruction (AND)

With the AND instruction, all inputs must be TRUE to activate the output (R).

<u>Graphic representation</u>

| IEC view | Mathematical view |
|:--------:|:-----------------:|
| ![AND](/images/Prog/and.png) | R = A.B  |

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
| ![NAND](/images/Prog/nand.png) | R=A+B=(A ̅.B ̅ ) ̅  |

### OR instruction (OR)

### Exclusive OR instruction (XOR)

### Assignment (COIL)

### FlipFlop (SR/RS)

### Edge detection (R_TRIG/F_TRIG)

### Copy (MOVE)

### IEC Timers (TON/TOF/TP)

### IEC Counters (CTU/CTD/CTUD)

### Mathematical instructions

### Comparison instructions

### Conversion instructions


## Programming in ST

