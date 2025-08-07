# Programmable logic controller

A PLC is the "brain" of automated machinery. It is therefore equipped with a programmable controller that uses logical instructions, like AND & OR gates, to create the intelligence.

## Rack

A PLC is primarily mounted in an electrical control cabinet. This involves a modular PLC assembly on a mounting rail.
- If this is a standard DIN C rail, it is called a **mounting rail**.
- Otherwise, it is called a **rack**. Such a rack is designed by the manufacturer and often intended for mounting a specific PLC series.


![CX PLC on standard DIN C rail](/images/CX_on_rail.png "CX PLC on standard DIN C rail, ©2020 Beckhoff")

![S7-1200 PLC on standard DIN C rail](/images/S7_1200_on_rail.png "S7-1200 PLC on standard DIN C rail, ©2020 Siemens") ![S7-1200 PLC on standard DIN C rail](/images/S7_1200_on_rail_bottom.png "S7-1200 PLC on standard DIN C rail, ©2020 Siemens")

Some racks are equipped with electronic connectors. These provide the connection between the various modules and the processing unit. If this is not provided, this task is performed by a connector supplied by the manufacturer, or the modules are equipped with connectors that are automatically connected during installation.

![S7-1500 PLC on rack](/images/S7_1500_on_rack.png "S7-1500 PLC on rack, ©2020 Siemens")

## Central Processing Unit

The processing unit, or CPU<sup>1</sup>, consists of several parts. It not only executes the software code but also maintains the user program and the status of various variables and parameters.

| Part | Description |
| :--- | :--- |
| Processor | The processing of the user program is done by the processor |
| Internal memory | The internal memory stores the user program and the status of various variables and parameters |
| External memory | External memory is not included on every PLC type. If it is, it: <br> - Sometimes supplements the internal memory and can ensure that the status of variables is retained during a power failure <br> - Sometimes serves as a backup of the user program and is automatically downloaded when power is restored <br> - In some PLCs, it is necessary for the correct operation of the processing unit <br> <br> External memory is often offered in the form of an SD<sup>2</sup> or CF<sup>3</sup> card. |

A manufacturer often has several processing units available that have the same basic functionality, but differ in processing speed, software code capabilities, internal memory, external memory, communication capabilities, etc.
It is equipped with various status LEDs. These LEDs indicate the operating mode and status. The operating mode can be set using a switch and/or the associated software package.

| LED              | Description                                                 |
|:-----------------|:------------------------------------------------------------|
| *Siemens PLC*    |                                                             |
| RUN (green)      | ONLINE user program is executed                             |
| STOP (orange)    | ONLINE user program is not executed                         |
| SF (red)         | System fault                                                |
| FRCE (red)       | At least one variable is forced                             |
| MAINT (orange)   | Maintenance necessary                                       |
| ERROR (red)      | Error                                                       |


| LED              | Description                                                 |
|:-----------------|:------------------------------------------------------------|
| *Beckhoff PLC*   |                                                             |
| PWR (green)      | Power on                                                    |
| TC (red)         | STOP: ONLINE user program is not executed                   |
| TC (green)       | RUN: ONLINE user program is executed                        |
| TC (blue)        | TwinCAT in Config mode                                      |
| ERR (red)        | Error                                                       |

Depending on the type, a CPU is equipped with one or more industrial network connections. These connections allow users to download, upload, and debug a user program using the ES package. External components, such as HMI displays, can also be connected.

![CX9020 CPU at a glance](/images/CX_at_a_glance.png "CX9020 CPU at a glance, ©2020 Beckhoff")

Depending on the manufacturer and type, a processing unit is equipped with a battery. This ensures that the ONLINE user program is retained and that the internal clock continues to operate when the power supply is switched off. If there is no battery, this function is taken over by an internal capacitor, but then its functionality is a limited in time (a few days).

![S7-1200 CPU at a glance](/images/S7_1200_at_a_glance.png "S7-1200 CPU at a glance, ©2020 Siemens")

Siemens S7-1500 processing units are equipped with a display as standard. This display allows you to configure the processing unit and view its status:
- Configure network settings
- View faults
- Adjust operating mode
- …

![S7-1500 CPU at a glance](/images/S7_1500_at_a_glance.png "S7-1500 CPU at a glance, ©2020 Siemens")

Furthermore, the operating mode switch, SD memory, and Ethernet/PROFINET connection(s) are only accessible by removing the front panel.
Finally, in both the Siemens and Beckhoff processing units, the other modules are primarily installed to the right of the processing unit.

<sup>1</sup> *CPU = **C**entral **P**rocessing **U**nit* <br>
<sup>2</sup> *SD = **S**ecure **D**igital* <br>
<sup>3</sup> *CF = **C**ompact **F**lash* <br>

## Inputs
### Digital input modules

A digital input module must enable the processing unit to read the logic state of sensors connected to the input module.
Digital input modules are available with 2, 4, 8, 16, or 32 digital inputs (depending on the manufacturer and PLC series) and are often referred to by the abbreviation DI<sup>4</sup>.

![Digital input conversion](/images/di_signals.png "Digital input conversion") 

A digital input processes an "all" or "nothing" signal. This is called a **BIT**. The status of a BIT is often indicated as follows:
- TRUE / FALSE
- 1 / 0
- ON / OFF

The state of each digital input signal is displayed using an indicator LED on the digital input module. A green LED will be activated if the state is TRUE.

There is a small time interval (in the order of µs/ms) between sensor activation (e.g., status changes from FALSE to TRUE) and its registration by the processing unit. The length of this time interval is determined by the internal electronics in the input module:
- Electronics to convert the analog signal to a digital signal
- Filter to suppress interference pulses

![KL1408/8 x DI in detail](/images/kl1408.png "KL1408/8 x DI in detail, ©2020 Beckhoff") ![SM1223/16 x DI in detail](/images/sm1223.png "SM1223/16 x DI in detail, ©2020 Siemens")

![SM521/32 x DI in detail](/images/sm521.png "SM521/32 x DI  in detail, ©2020 Siemens")

<sup>4</sup> *DI = **D**igital **I**nput* <br>

### Analog input modules

An analog input module allows the conversion of physical quantities such as voltage (V), current (I), or resistance (RTD<sup>5</sup> or TC<sup>6</sup>) into a digital signal. These physical quantities are defined within the EU using the SI<sup>7</sup> system (SI system, 2006).

The list below provides an overview of commonly used quantities:
- 0 to 20 mA: electrical current signal without cable break monitoring
- 4 to 20 mA: electrical current signal with cable break monitoring
- 0 to 10 V: electrical voltage signal without cable break monitoring
- -10 to +10 V: electrical voltage signal without cable break monitoring
- 1 to 5 V: electrical voltage signal with cable break monitoring
- Pt100: resistance measurement

A physical quantity consisting of negative and positive values (e.g., -10 V to +10 V) is called a bipolar signal.
A physical quantity consisting only of positive values (e.g., 0 to 10 V) is called a unipolar signal. A unipolar signal may be equipped with a cable break detection. In this case, the lower limit is not equal to zero (e.g., 4 mA instead of 0 mA), and one can conclude that if no current flows, the electrical circuit is faulty.

Analog input modules are available with 2, 4, or 8 analog inputs (depending on the manufacturer and PLC series) and are often referred to by the abbreviation AI<sup>8</sup>.

![Analog input conversion](/images/ai_signals.png "Analog input conversion") 

An analog input produces a consecutive sequence of 16 bits. This is called a **WORD**.

Such a WORD can be represented arithmetically in several ways:
- Binary (numbers with only 0s and 1s)
- Decimal (integers)
- …

Using a WORD, an analog input can process a decimal integer between two limits, namely -32768 and +32767. The integer changes in steps:
- By converting a physical quantity (decimal places) to an integer (no decimal places)
- By the resolution of the analog input module, which determines how many BITs are used; unused BITs remain permanently set to 0.

| Analog value    |         |       |      |      |      |      |     |     |     |    |    |    |    |    |    |    |
|:----------------|:--------|:-----:|:----:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Bits            | 15      | 14    | 13   | 12   | 11   | 10   | 9   | 8   | 7   | 6  | 5  | 4  | 3  | 2  | 1  | 0  |
| Weight          | S       | 2<sup>14</sup>   | 2<sup>13</sup>  | 2<sup>12</sup>  | 2<sup>11</sup>  | 2<sup>10</sup>  | 2<sup>9</sup>  | 2<sup>8</sup>  | 2<sup>7</sup>  | 2<sup>6</sup> | 2<sup>5 | 2<sup>4 | 2<sup>3</sup> | 2<sup>2</sup> | 2<sup>1</sup> | 2<sup>0</sup> |
| Numerical value | \+/-    | 16384 | 8192 | 4096 | 2048 | 1024 | 512 | 256 | 128 | 64 | 32 | 16 | 8  | 4  | 2  | 1  |

The resolution of an analog input module is expressed in number of BITs and indicates how many BITs are used for the conversion to a decimal integer.

![Analog input resolution](/images/ai_resolution.png "Analog input resolution")

The unused BITs have the value FALSE / 0 (denoted by an x in the following table) for positive numbers.

| Resolution in bits | Accuracy | Analog value  |
|:---------------------:|:------------------:|:-------------------:|
| 8                     | 128                | S000 0000 1xxx xxxx |
| 9                     | 64                 | S000 0000 01xx xxxx |
| 10                    | 32                 | S000 0000 001x xxxx |
| 11                    | 16                 | S000 0000 0001 xxxx |
| 12                    | 8                  | S000 0000 0000 1xxx |
| 13                    | 4                  | S000 0000 0000 01xx |
| 14                    | 2                  | S000 0000 0000 001x |
| 15                    | 1                  | S000 0000 0000 0001 |


<sup>5</sup> *RTD = **R**esistance **T**emperature **D**etector* <br>
<sup>6</sup> *TC = **T**hermo**c**ouple* <br>
<sup>7</sup> *SI = **S**ystéme **I**nternational* <br>
<sup>8</sup> *AI = **A**nalog **I**nput* <br>

## Outputs
### Digital output modules


### Analog output modules


## Internal communication
