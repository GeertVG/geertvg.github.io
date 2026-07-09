# GRAFCET
---
Designing software for an automatic machine/installation requires the necessary analyses, including a description of the desired operation.

The automatic operation can be carried out via a continuous, sequential or batch process.

For a **sequential process,** the graphical **GRAFCET**<sup>1</sup> **design language**can be used to describe the operation and behavior of the inputs and the way in which the outputs respond.

<sup>1</sup> *GRAFCET = Graphe Fonctionnel de Commande des Étapes et Transitions* <br>

The GRAFCET design language is characterized by various graphical elements and text that displays information about the variables. By connecting these
different elements and text, the behavior of an automatic machine/installation (or part thereof) is described.

The operation is broken down into different steps with corresponding actions. The steps are then linked together and provided with transition conditions (e.g.
which sensors must be activated to start an actuator).

The sequential process will be carried out as follows:
-   A GRAFCET is executed from top to bottom
-   A GRAFCET starts from its initial step or a source step
-   A transition condition is represented as a mathematical Boolean expression
-   The result of a transition condition is TRUE or FALSE
-   During the execution of a GRAFCET, at least one step is active
-   Only the actions associated with the active step(s) can be executed
-   Other steps can be activated provided that they are connected to an active step and if the result of the corresponding transition condition is TRUE.

![Graphical representation of a sequential part of a process](/images/Grafcet/grafcet.png "Graphical representation of a sequential part of a process")

The IEC 61131 standard includes five programming languages, including the SFC programming language. This SFC programming language is inspired by the GRAFCET design language, but there are differences:
-	SFC is a programming language
-	GRAFCET is a design language
-	The SFC programming language uses other programming languages and other abbreviations to program transition conditions and actions, which means that the representation in SFC differs from that in GRAFCET
-	Performing an OR convergence if all transition conditions are TRUE differs in the SFC programming language and the GRAFCET design language

> **Conclusions**
> -	It is possible to convert GRAFCET into software code in a programming language of your choice
> -	The SFC programming language is very similar to the GRAFCET design language but is not 100% the same

## Structure of a GRAFCET according to IEC 60848
### GRAFCET diagram

| Symbol | Description |
| :----: | :---------- |
| ![GRAFCET](/images/Grafcet/diagram.png ) | A diagram is a collection of steps, actions, transition conditions, connections, ... that form a whole. Often abbreviated as GRAFCET. <br> <br> The collection is represented by a rectangle that encompasses all elements of the GRAFCET diagram. |
| ![GRAFCET](/images/Grafcet/input_var.png )| Input variables are placed to the left of the rectangle and marked with an incoming arrow. |
| ![GRAFCET](/images/Grafcet/output_var.png )| Output variables are placed tot the write of the rectangular and marked with an outgoing arrow. |
| ![GRAFCET](/images/Grafcet/comment.png )| Comments which clarifies the operation of a specific section, is written between double quotation marks, with the asterisk symbol replaced by the description. |

### Step

A step represents a specific state of the sequential process. A step can take two values, namely:
- Active
- Not active

At a given moment during the evolution of the sequential process:
- A step is either active or inactive
- The set of active steps determines the state of the process
- The GRAFCET determines which step or steps can become active

| Symbol | Description |
| :----: | :---------- |
| ![GRAFCET](/images/Grafcet/step.png ) | A step is represented graphically by a square with a unique label. For practical reasons, a, for the diagram, unique numerical label is used to replace the asterisk symbol. |
| ![GRAFCET](/images/Grafcet/intial_step.png ) | The initial step characterises the initial state and is represented by a double square. If an initial step is active, all other steps in the GRAFCET are inactive. <br> <br> The agreements relating to a step apply. <br> <br> The use of multiple initial steps is permitted, but often only one initial step is used. |
| ![GRAFCET](/images/Grafcet/encl_step.png ) | An enclosed step indicates that this step contains multiple internal steps. As soon as the transition condition after an enclosed step is TRUE, the program moves on to the next steps and all internal steps will be inactive. <br> <br>  An enclosed step may contain multiple GRAFCET diagrams, but the enclosed internal steps can only belong to one enclosed step. <br> <br> The agreements regarding a step apply. |
| ![GRAFCET](/images/Grafcet/encl_intial_step.png ) | An enclosed initial step indicates that this step contains multiple internal steps and that it participates in the initial state. <br> <br> An enclosed initial step contains at least one internal initial step and may contain multiple GRAFCET diagrams. <br> <br> The agreements regarding a step apply.  |
| ![GRAFCET](/images/Grafcet/macro_step.png ) | A macro step indicates that this step contains multiple internal steps, whereby a macro can be described as a clearly defined piece of software code. A macro is not designed as stand-alone software; its purpose is to support another piece of software code. <br> <br> The internal steps always start with a source step and always end with an end step. The macro can only be exited if the end step is active. <br> <br> Unlike an embedded step, a macro contains a maximum of one GRAFCET diagram and the asterisk symbol is replaced by a unique label that may differ from the step labels and numbering. |
| ![GRAFCET](/images/Grafcet/active_step.png ) | If it is necessary to indicate an active step, this will be done by means of a dot placed under the label. |

### Connecting elements

| Symbol | Description |
| :----: | :---------- |
| ![GRAFCET](/images/Grafcet/ver_line.png ) | Connecting elements are lines in the network that connect the various steps. |
| ![GRAFCET](/images/Grafcet/hor_line.png ) | Both horizontal and vertical lines may be used. <br> <br> Diagonal connections should be avoided; they are permitted, but only to promote clarity. |
| ![GRAFCET](/images/Grafcet/line_dir.png ) | The direction of a connection is always from top to bottom. Arrows are only used if this convention cannot be followed or to promote clarity. |
| ![GRAFCET](/images/Grafcet/next_page.png ) | If a connection needs to be interrupted (e.g. when multiple pages are required or in the case of complex GRAFCET), the label of the next step will be indicated. <br> <br> If the next step is on a different page, the page number will be added. |

### Transition

| Symbol | Description |
| :----: | :---------- 
| ![GRAFCET](/images/Grafcet/transition.png ) | A transition between two steps is represented by a horizontal crossbar on the connecting line. <br> <br> A transition is active when the preceding step is active. <br> <br> Only one transition is allowed between two steps. |
| ![GRAFCET](/images/Grafcet/transition_ver.png ) | For graphic reasons, it is permissible to place a vertical crossbar over a horizontal connecting line. |
| ![GRAFCET](/images/Grafcet/transition_cond.png ) | Each transition has a transition condition. This is a mathematical Boolean expression composed of variables, which replaces the asterisk symbol and can be TRUE or FALSE. <br> <br> The transition condition is always placed to the right of the transition. <br> <br> Of all the available information at a given moment, the transition condition contains only that which is necessary for crossing that transition.  |
| ![GRAFCET](/images/Grafcet/transition_label.png ) || A transition may optionally be provided with a unique numeric label in brackets placed to the left of the transition. |
| ![GRAFCET](/images/Grafcet/transition_true.png ) | A transition condition that is always TRUE is represented by an underlined number 1|
| ![GRAFCET](/images/Grafcet/transition_state.png )| The status of a step (active or inactive) can be added to a transition condition using the letter X, whereby the asterisk symbol is replaced by the label of the step. |
| ![GRAFCET](/images/Grafcet/transition_re.png )| The representation of a rising edge in a variable is shown using an upward arrow. |
| ![GRAFCET](/images/Grafcet/transition_fe.png )|| The representation of a falling edge in a variable is shown using a downward arrow.|
| ![GRAFCET](/images/Grafcet/transition_comp.png )| A comparison instruction is written between square brackets, with the asterisk symbol replaced by the comparison. <br> <br> The result of a comparison instruction is TRUE or FALSE. |
| ![GRAFCET](/images/Grafcet/transition_to.png )| The representation of a variable that is time-dependent is displayed using the ‘/’ symbol. <br> <br> Here, the transition condition is TRUE after a rise delay and remains TRUE with a fall delay. <br> <br> It is permitted to simplify the notation by removing the fall delay if it is not applicable. |
| ![GRAFCET](/images/Grafcet/transition_source.png )| A source transition condition is a transition condition without a preceding step. Whenever the transition condition is TRUE, the following step will become active. <br> <br> It is recommended to provide the transition condition with a rising or falling edge to avoid continuous activation of the next step. |
| ![GRAFCET](/images/Grafcet/transition_end.png )| An end transition condition is a transition condition that is not followed by a step. Whenever the transition condition is TRUE, all upward steps will be deactivated |

**Example**

The example shows 
- The use of mathematical expressions to connect boolean tags (eg. iStsStared AND iSen2)
- The use of a rising edge on the initialization command
- The use of a 5s on-delay if iSen1=FALSE

![GRAFCET](/images/Grafcet/example1.png )

Explanation on GRAFCET initialization. On a rising edge of iCmdInit
- The current active step is deactivated by iCmdInit after step 3 == All upward steps are deactivated
- The initial step is activated by iCmdInit before step 0 == Activate the following step

Explanation of symbolic tags in the example
-	iCmdInit = digital input – Initialisation command
-	iStsStarted = digital input – Result of a basic start stop control circuit
-	iSen1 = digital input – Sensor 1
-	iSen2 = digital input – Sensor 2

### Action

### Structures

### Operation

In general, it can be said that a GRAFCET operates step by step.

If a step is active, the next step can only become active if the status of the transition condition is TRUE. As soon as the next step is active, the current step is deactivated.

However, it is possible that, due to the status of various transition conditions, the operation of a GRAFCET does not appear to proceed step by step. It is the designer's task to avoid this operation, which can lead to unstable operation of, for example, actions.


### Example

The following example shows a GRAFCET for the operation of a conveyor on which a box is placed and moved back and forth five times before stopping. After this, the conveyor must be restarted.



## GRAFCET programming in LAD/FBD using BOOL

The GRAFCET is programmed in the LAD or FBD programming language in a function block (%FB). This allows the use of STATIC parameters that can retain their status even when the power is cut-off  (RETAIN).

## GRAFCET programming in LAD/FBD using INT

The GRAFCET is programmed in the LAD of FBD programming language in a function block (%FB). This allows the use of STATIC parameters that can retain their status even when the power is cut-off  (RETAIN).

## GRAFCET programming in ST

The GRAFCET is programmed in the ST programming language in a function block (%FB). This allows the use of STATIC parameters that can retain their status even when the power is cut-off (RETAIN).