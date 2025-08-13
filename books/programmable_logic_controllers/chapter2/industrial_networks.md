# Industrial networks
---
It is often necessary to provide a PLC with one or more industrial networks in order to establish communication with other devices (e.g. HMI display).

![EtherCAT network](/images/ethercat.png "EtherCAT network ©2020 Beckhoff") 

The purpose of an industrial network is
- To reduce the number of cables (and therefore the cable length) between sensors/actuators and input/output modules,
- To establish communication with IO devices (status inputs, output controls, module settings, and diagnostics),
- To establish communication with other PLCs and/or PCs for data exchange,
- To establish communication with HMI displays,
- To establish communication with the ES package (uploading, downloading, online monitoring).

> IO devices = A group of input and/or output modules on one mounting rail without a CPU
> Data exchange = Moving digital information (=data) from one information system to another

Usually, a communications module (even if provided on the CPU itself) is equipped with its own processor so as not to put an additional load on the central processing unit.

![PROFIBUS-DP and PROFINET networks](/images/profi_networks.png "PROFIBUS-DP and PROFINET networks ©2020 Siemens") 

If there is no communication port available on the central processing unit, a PLC can be expanded with one or more communication modules.

![EL6731 PROFIBUS master](/images/el6731.png "EL6731 PROFIBUS master ©2020 Beckhoff") ![CM1243-5 PROFIBUS master](/images/cm1243_5.png "CM1243-5 PROFIBUS master ©2020 Siemens") 