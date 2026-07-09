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
| :----: | :---------: |
| ![GRAFCET](/images/Grafcet/diagram.png ) | A diagram is a collection of steps, actions, transition conditions, connections, ... that form a whole. Often abbreviated as GRAFCET. <br> The collection is represented by a rectangle that encompasses all elements of the GRAFCET diagram. |
| ![GRAFCET](/images/Grafcet/input_var.png )| Input variables are placed to the left of the rectangle and marked with an incoming arrow. <br> Example: Activate initial step and start installation
 	transition conditions |
| ![GRAFCET](/images/Grafcet/output_var.png )| Output variables are placed tot the write of the rectangular and marked with an outgoing arrow. <br> Example: Forward and backward control |
| ![GRAFCET](/images/Grafcet/comment.png )| Comments which clarifies the operation of a specific section, is written between double quotation marks, with the asterisk symbol replaced by the description. <br> Example: Stop the drain pump if the level is too low |

### Step

### Connecting elements

### Transition

### Action

### Structures

### Operation

### Example

## GRAFCET programming in LAD/FBD using BOOL

The GRAFCET is programmed in the LAD or FBD programming language in a function block (%FB). This allows the use of STATIC parameters that can retain their status even when the power is disabled (RETAIN).

## GRAFCET programming in LAD/FBD using INT

The GRAFCET is programmed in the LAD of FBD programming language in a function block (%FB). This allows the use of STATIC parameters that can retain their status even when the power is disabled (RETAIN).

## GRAFCET programming in ST

The GRAFCET is programmed in the ST programming language in a function block (%FB). This allows the use of STATIC parameters that can retain their status even when the power is disabled (RETAIN).