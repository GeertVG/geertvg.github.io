# GRAFCET

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