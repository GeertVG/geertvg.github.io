# Intro
---
In a programmable logic controller, it is possible to program software code using the ES software package, allowing one to develop strategies for (semi-)automated operation of machines/installations.

The software code can be divided into several parts, namely:
- The representation and definition of variables, possibly with a link to the PLC inputs and outputs
- Instructions to read and change the status of variables
- Building blocks to compile a set of instructions

![Blocks, instructions, variables and data types](/images/blocks_to_datatypes.png "Blocks, instructions, variables and data types")

The following chapters explain the various building blocks, instructions, and data types based on the IEC 61131 standard. As a rule of thumb, we can state that:
- Siemens is not 100% built according to the IEC 61131 standard. This is due to its history: Siemens is one of the pioneers in the field of PLCs and was already producing PLCs before the IEC 61131 standard even existed. Siemens doesn't simply discard "old" technologies, but ensures that a transition from old to new remains possible.
- Beckhoff is 100% built according to the IEC 61131 standard. Beckhoff is a relatively new player in the PLC market and entered the scene when the IEC 61131 standard already existed. Consequently, Beckhoff has had the opportunity to build its products entirely around the standard.

Not only is programming is possible; creating and editing modules and industrial networks is also possible in the ES software package.