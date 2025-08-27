# Variables
## Direct representation according IEC 61131

**Variables** <sup>1</sup> Ensure the identification of data objects whose content may change. For example, a variable can provide the identification of inputs, outputs and memory data objects.

The **direct representation** of a variable creates a link to the absolute address in the PLC memory, to a PLC input or a PLC output. In other words, the direct representation allows you to check, for example, which PLC input a sensor
is connected to.

The direct address representation consists of several parts, namely:

- “%” character
- Operand
- Size
- Unique sequence number or a series of sequence numbers with a unique  combination

| Operand | Description operand  |
|:-------:|:---------------------|
| I       | Link to a PLC input  |
| Q       | Link to a PLC output |
| M       | Link to a PLC memory |

| Range | Size | Description size                          |
|:-----:|:------:|:----------------------------------------|
| X     | 1 bit  | 1 BIT = BOOL (Beckhoff/Siemens DBs<sup>2</sup>) |
| none  | 1 bit  | 1 BIT = BOOL (Siemens)                  |
| B     | 8 bit  | A set of 8 sequential BITs = **B**YTE   |
| W     | 16 bit | A set of 16 sequential BITs = **W**ORD  |
| D     | 32 bit | A set of 32 sequential BITs = **D**WORD |
| L     | 64 bit | A set of 64 sequential BITs = **L**WORD |

The structure of the absolute address is different:
- For a BOOL variable and a non-BOOL variable by adding a dot and the BIT address
- For a BOOL Beckhoff variable and a BOOL Siemens variable because a Beckhoff PLC uses the notation ‘X’ for the range and Siemens does not

![Structure of absolute address](/images/direct_address.png "Structure of absolute address")

```Examples
- %Q8.0 Output 8.0 (Siemens)
- %MD48 Double word on memory location 48
- %QB8 Output byte 8
- %IX75.0 Input bit 75.0 (Beckhoff)
```

If an absolute address is a collection of consecutive bits, e.g. a BYTE, then an
address consequently has multiple statuses, namely:

- 0000 0000
- 0000 0001
- 0000 0010
- 0000 0011
- 0000 0100
- 0000 0101
- …
- 1111 1111

Since a BYTE consists of 8 BITS, each of which has 2 states, a BYTE therefore consists of 256 statuses (2⁸ = 256). Assigning a data type to this collection determines its meaning. This is because the meaning of these statuses has not
yet been determined.

```Examples
- Is the status of the BYTE ‘1010 1010’ equal to the integer 170 [USINT] or
- Is the status of the BYTE ‘1010 1010’ equal to the integer -86 [SINT] or
- Is the status of the BYTE ‘1010 1010’ equal to the character ‘a’ [CHAR] or
- …
```

By assigning a data type, one determines the representation, which is always limited between a minimum and a maximum value, which in turn depend on the number of bits.
The following table shows the different **elementary data types, IEC 61131, 2003**, where the representation

- displays the minimum and maximum values for numeric data types
- provides an example for date, time and text data types

| Type      | Description                 | Number of BITs | Presentation       |
|:---------:|:---------------------------:|:--------------:|:-------------------|
| *Numerical data types*|                 |         |        |
| BOOL      | Boolean                     | 1 bit   | 0 of 1 |
| BYTE      | Set of 8 bits               | 8 bits  | ---    |
| WORD      | Set of 16 bits              | 16 bits | ---    |
| DWORD     | Set of 32 bits (Double WORD)| 32 bits | ---    |
| LWORD     | Set of 64 bits (Long WORD)  | 64 bits | ---    |
| SINT      | Short Integer               | 8 bits  | -(2<sup>8-1</sup>) .. (2<sup>8-1</sup>) – 1          |
| INT       | Integer                     | 16 bits | -(2<sup>16-1</sup>) .. (2<sup>16-1</sup>) – 1        |
| DINT      | Double Integer              | 32 bits | -(2<sup>32-1</sup>) .. (2<sup>32-1</sup>) – 1        |
| LINT      | Long Integer                | 64 bits | -(2<sup>64-1</sup>) .. (2<sup>64-1</sup>) – 1        |
| USINT     | Unsigned Short Integer      | 8 bits  | 0 .. (2<sup>8</sup>) – 1                             |
| UINT      | Unsigned Integer            | 16 bits | 0 .. (2<sup>16</sup>) – 1                            |
| UDINT     | Unsigned Double Integer     | 32 bits | 0 .. (2<sup>32</sup>) – 1                            |
| ULINT     | Unsigned Long Integer       | 64 bits | 0 .. (2<sup>64</sup>) – 1                            |
| REAL      | Real number                 | 32 bits | -3.40E<sup>+38</sup> tot -1.18E<sup>-38</sup> en 1.18E<sup>-38</sup> tot 3.40E<sup>+38</sup> |
| LREAL     | Long Real                   | 64 bits | -1.80E<sup>+308</sup> tot -4.94E<sup>-324</sup> en 4.94E<sup>-324</sup> tot 1.80E<sup>+308</sup> |
| *Date & time data types* |              |         |                                                      |
| TIME      | Time indication             | ---     | T\#0s                                                |
| DATE      | Date                        | ---     | D\#1997-12-01                                        |
| TIME_OF_DAY of TOD  | Time              | ---     | TOD\#23:59:59                                        |
| DATE_AND_TIME of DT | Date & time       | ---     | DT\#1997-12-01-23:59:59                              |
| *Textual data types*|                   |         |                                                      |
| CHAR<sup>3</sup>    | ASCII character<sup>4</sup> | 8 bits  | ‘A’                                        |
| STRING    | Set of 8 bits ASCII characters  | Variable | ‘TEXT’                                         |
| WSTRING   | Set of 16 bits ASCII characters | Variable | “TEXT”                                         |



<sup>1</sup> *Synonyms for variable = TAG, Symbol* <br>
<sup>2</sup> *DBs = The use of the letter ‘X’ as a range is only applied in data blocks in Siemens PLCs* <br>
<sup>3</sup> *The CHAR data type is not included in the IEC 61131-3 standard* <br>
<sup>4</sup> *ASCII = American Standard Code for Information Interchange = A table that defines text characters* 