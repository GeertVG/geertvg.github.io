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

<sup>1</sup> *Synonyms for variable = TAG, Symbol* <br>
<sup>2</sup> *DBs = The use of the letter ‘X’ as a range is only applied in data blocks in Siemens PLCs* <br>

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

<sup>3</sup> *The CHAR data type is not included in the IEC 61131-3 standard* <br>
<sup>4</sup> *ASCII = American Standard Code for Information Interchange = A table that defines text characters* 

## Symbolic representation according to IEC 61131

In a symbolic representation of a variable, there is no direct link to the logical or absolute address, but the variable is characterized by a unique text.

Not all punctuation marks and symbols are permitted (IEC 61131, 2003).

- A symbolic address is a text consisting of letters and/or numbers and/or an underscore ‘\_’,
- A symbolic variable begins with a letter or an underscore ‘\_’,
- No distinction is made between upper and lower case letters, so the symbolic variables abc, ABC, aBC and Abc are considered to be the same,
- A distinction is made when using an underscore ‘\_’, so the symbolic variables A_BC, AB_C and \_ABC are considered to be different.

```Trivia
Siemens allows the use of special characters when constructing symbolic variables but does not recommend it. 
So are the special characters ! \# \$ & ' ( ) \* , - . / : ; \< = \> ? \@ [ \\ ] \^ \` { \| } \~ ¡ ¢ £ ¤ ¥ ¦ § ¨ © ª « ¬ - ® ¯ ° ± ² ³ ´ μ ¶ · ¸ ¹ º » ¼ ½ ¾ ¿ + permitted. 
```
How is the link to a logical or direct address established? This depends on the manufacturer.

At Siemens, the direct and symbolic representations form a single entity. One cannot exist without the other because they are entered together in one or more tables under the folder called ‘PLC tags’.

![Creating and editing variables in TIA Portal](/images/TIA/tags1.png "Creating and editing variables in TIA Portal, ©2020 Siemens")
![Creating and editing variables in TIA Portal](/images/TIA/tags2.png "Creating and editing variables in TIA Portal, ©2020 Siemens")

Because tables are used, the structure is clearly defined by the column headings:
- Name = Symbolic name of the variable
- Data type = The data type assigned to the variable
- Address = The absolute start address of the variable
- Retain = If checked, the status is retained in the event of a power failure
- Visible in HMI engineering = Visibility in the Siemens HMI section
- Comment = Optional description of the variable

![Building a symbolic variable in a Siemens PLC](/images/TIA/symbolic_address.png "Building a symbolic variable in a Siemens PLC")

At Beckhoff, the symbolic representation is created with the assignment of a data type in a  ‘GVL’ text file. Adding an absolute address is possible but not recommended, as it is possible to ‘link’ a variable to an absolute address.

![Creating and editing variables in TwinCAT 3](/images/TwinCAT/tags1.png "Creating and editing variables in TwinCAT 3, ©2020 Beckhoff")
![Creating and editing variables in TwinCAT 3](/images/TwinCAT/tags2.png "Creating and editing variables in TwinCAT 3, ©2020 Beckhoff")
![Creating and editing variables in TwinCAT 3](/images/TwinCAT/tags3.png "Creating and editing variables in TwinCAT 3, ©2020 Beckhoff")

Because a text file is used, the structure is less clear but fixed:
- Name = Symbolic name of the variable followed by a space
- Address = The absolute address preceded by the AT instruction
- Data type = The data type assigned to the variable preceded by ‘:’
- Comment = Optional description of the variable preceded by ‘//’

![Creating a symbolic variable in a Beckhoff PLC (via direct address)](/images/TwinCAT/symbolic_address1.png "Creating a symbolic variable in a Beckhoff PLC (via direct address")

Note that the definition of a variable in Beckhoff always ends with a semicolon.

![Creating a symbolic variable in a Beckhoff PLC (via link)](/images/TwinCAT/symbolic_address2.png "Creating a symbolic variable in a Beckhoff PLC (via link)")

Both Beckhoff and Siemens offer the option of creating multiple PLC tags/GVL files within a single PLC project.

![Multiple variable files in TIA Portal](/images/gvl1.png "Multiple variable files TIA Portal, ©2020 Siemens") ![Multiple variable files in TwinCAT 3](/images/gvl2.png "Multiple variable files TIA Portal, ©2020 Beckhoff")

## Structure of data types according to IEC 61131
### ANY_INT

ANY_INT data types are used in comparison instructions and arithmetic instructions involving whole numbers and natural numbers<sup>1<sup/>.
The structure of an ANY_INT variable can be divided into two groups, namely:

-   De group of ANY_INT preceded by “+/-“ (signed)
-   De group of ANY_INT not preceded by “+/-“ (unsigned)

![Structure of an ANY_INT data type with a plus sign/minus sign](/images/any_int1.png "Structure of an ANY_INT data type with a plus sign/minus sign")

The group of ANY_INT data types with a sign bit is used when working with integers.
The group of ANY_INT data types without a sign bit is used when working with natural numbers.

![Structure of an ANY_INT data type without a plus sign/minus sign](/images/any_int2.png "Structure of an ANY_INT data type without a plus sign/minus sign")

```Trivia
Is there a difference between natural, whole numbers and ANY_INT numbers?
 
The set of natural numbers is infinite and extends from:
 	{0 , 1 , 2 , 3, …}
 
The set of ANY_INT numbers without a sign bit is finite and is limited by the number of BITS needed to construct the numerical value (see Table 4 4 : Elementary data types (IEC 61131, 2003):
•	{0 , 1 , 2 , 3, … , 255} - USINT
•	{0 , 1 , 2 , 3, … , 65535} - UINT 
•	{0 , 1 , 2 , 3, … , 4294967295} - UDINT
•	{0 , 1 , 2 , 3, … , 18446744073709551615} - ULINT
 
 The set of integers   is infinite and extends from:
 	{…, -3, -2 , -1, 0 , 1 , 2 , 3, …}
 
The collection of ANY_INT numbers with sign bit is finite and is limited by the number of BITS needed to construct the numerical value (see Table 4 4 : Elementary data types (IEC 61131, 2003): 
•	{-128, …, -2, -1, 0 , 1 , 2 , …, 127} - SINT
•	{-32768, …, -2, -1, 0 , 1 , 2 , …, 32767} - INT
•	{-2147483648, …, -2, -1, 0 , 1 , 2 , …, 2147483647} - DINT
•	{-9223372036854775808, …, -1, 0 , 1, …, 9223372036854775807} - LINT
```

<sup>1<sup/> *Numbers without fractional or decimal components* <br>

### ANY_REAL

The ANY_REAL data types are used in comparison instructions and arithmetic instructions involving real numbers.

```Trivia
Is there a difference between real numbers and ANY_REAL numbers?
 
The set of real numbers   is infinite and contains rational and irrational  numbers.
The set of ANY_REAL numbers is finite, with the boundaries determined by the number of BITS. This allows an ANY_REAL  number to approximate an irrational number. 
 
An example of this is the irrational number π, which has an infinite number of digits after the decimal point:
• With a REAL number, it is possible to approximate the irrational number π to 7 digits after the decimal point.
• With an LREAL number, it is possible to approximate the irrational number π to 16 digits after the decimal point.
```

The structure of an ANY_REAL data type is described in the IEEE 754 standard and is shown in the figure below.

![Structure of an ANY_REAL data type](/images/any_real.png "Structure of an ANY_REAL data type")

The size of the exponent and mantissa is determined by the chosen data type:
-	REAL 	: Exponent = 8 BIT, mantissa = 23 BIT
-	LREAL 	: Exponent = 11 BIT, mantissa = 52 BIT

The exponent is constructed according to the binary number system, but a shift has been applied, which means that the decimal value must be reduced by a starting value, namely:
-	REAL 	: Start value of 127 	= 0 = (0111 1111)<sub>2<sub/> 		
-	LREAL 	: Start value of 1023 	= 0 = (0011 1111 1111)<sub>2<sub/> 	

The mantissa is constructed from left to right and always starts with the binary value 1, which is not present in the whole (called the hidden BIT).

![Structure of mantissa in an ANY_REAL data type](/images/mantissa.png "Structure of mantissa in an ANY_REAL data type")

The sign bit is 1 BIT in size and has the following meaning:
-	FALSE	= Positive number
-	TRUE 	= Negative number

The numerical value of the ANY_REAL number is determined using the following formula:
- +/- MANTISSA x 2 <sup>+/- EXPONENT<sup/>

