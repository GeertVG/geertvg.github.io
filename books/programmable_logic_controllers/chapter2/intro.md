# Introduction

An **automated machine or technical installation** can be visualized schematically. 

![Stacker crane](/images/stacker_crane.png "Impression of a automated warehouse, ©2020 Realgames")

This clearly demonstrates the presence of feedback: when the actuators are activated, they influence the machine or system, causing the sensors to register a change.

![Schematic overview](/images/overview.png "Schematic overview of a automated system")

Sensor signals are processed by the PLC via PLC inputs. Actuators are controlled by the PLC via PLC outputs. The collection of PLC inputs and PLC outputs is called IO.

> IO or I/O = **I**nputs/**O**utputs

It can be noted that a distinction is made between:
- Control circuits and power circuits
- Operator interface and control circuits

A PLC is internally composed of electronic components, the electrical power that can be activated through the PLC outputs is rather limited. By using control circuits that control the power circuits, the following problems are solved:
- It is not possible to control large power levels via a PLC output
- It is not possible to control or regulate non-electrical power levels via a PLC output

The control circuits can be further divided into a section intended for the operator and a section for the automatic operation of the machine or installation.
Because automated machines and technical installations involve hazards, **safety** is a crucial issue. The Machinery Directive, which sets out the principles of safety, is mandatory for these machines and installations in the European Union.

The **programming section** can be divided as showed in the next figure.

| Overview | Item |
| :---: | :--- |
|![Schematic programming overview](/images/programming_overview.png "Schematic overview of the programming part") | 1 = Programming device <br> 2 = PLC <br> 3 = Siemens engineering application <br> 4 = Beckhoff engineering application <br> 5 = Download cable <br> 6 = Compile <br> 7 = Download <br> 8 = Upload |

The **user program** is designed in the manufacturer's ES package and stored in the programming device's memory (e.g., a computer's hard drive). This is called the OFFLINE user program.

Using a download cable, it is possible to transfer the OFFLINE user program to the PLC's memory. This is called **downloading**. The download is preceded by checking the user program for errors and preparing it for download. This is called **compiling**.
The user program transferred to the PLC is called the ONLINE user program.

> Compiling at the Beckhoff engineering application is called "Build"

If you don't have an offline user program, you can transfer an online user program to the programming device's memory. This is called **uploading**.