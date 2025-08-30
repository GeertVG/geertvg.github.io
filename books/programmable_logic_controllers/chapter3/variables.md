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

## Symbolic representation according IEC 61131

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

## Structure of data types according IEC 61131
### ANY_INT

ANY_INT data types are used in comparison instructions and arithmetic instructions involving whole numbers and natural numbers<sup>1<sup/> <br>.
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
 
The set of ANY_INT numbers without a sign bit is finite and is limited by the number of BITS needed to construct the numerical value :
•	{0 , 1 , 2 , 3, … , 255} - USINT
•	{0 , 1 , 2 , 3, … , 65535} - UINT 
•	{0 , 1 , 2 , 3, … , 4294967295} - UDINT
•	{0 , 1 , 2 , 3, … , 18446744073709551615} - ULINT
 
 The set of integers   is infinite and extends from:
 	{…, -3, -2 , -1, 0 , 1 , 2 , 3, …}
 
The collection of ANY_INT numbers with sign bit is finite and is limited by the number of BITS needed to construct the numerical value : 
•	{-128, …, -2, -1, 0 , 1 , 2 , …, 127} - SINT
•	{-32768, …, -2, -1, 0 , 1 , 2 , …, 32767} - INT
•	{-2147483648, …, -2, -1, 0 , 1 , 2 , …, 2147483647} - DINT
•	{-9223372036854775808, …, -1, 0 , 1, …, 9223372036854775807} - LINT
```

<sup>1</sup> *Numbers without fractional or decimal components* <br>

### ANY_REAL

The ANY_REAL data types are used in comparison instructions and arithmetic instructions involving real numbers.

```Trivia
Is there a difference between real numbers and ANY_REAL numbers?
 
The set of real numbers   is infinite and contains rational and irrational  numbers.
The set of ANY_REAL numbers is finite, with the boundaries determined by the number of BITS. 
This allows an ANY_REAL  number to approximate an irrational number. 
 
An example of this is the irrational number π, which has an infinite number of digits after the decimal point:
•	With a REAL number, it is possible to approximate the irrational number π to 7 digits after the decimal point.
•	With an LREAL number, it is possible to approximate the irrational number π to 16 digits after the decimal point.
```

The structure of an ANY_REAL data type is described in the IEEE 754 standard and is shown in the figure below.

![Structure of an ANY_REAL data type](/images/any_real.png "Structure of an ANY_REAL data type")

The size of the exponent and mantissa is determined by the chosen data type:
-	REAL 	: Exponent = 8 BIT, mantissa = 23 BIT
-	LREAL 	: Exponent = 11 BIT, mantissa = 52 BIT

The exponent is constructed according to the binary number system, but a shift has been applied, which means that the decimal value must be reduced by a starting value, namely:
-	REAL 	: Start value of 127 	= 0 = (0111 1111)<sub>2</sub> 		
-	LREAL 	: Start value of 1023 	= 0 = (0011 1111 1111)<sub>2</sub> 	

The mantissa is constructed from left to right and always starts with the binary value 1, which is not present in the whole (called the hidden BIT).

![Structure of mantissa in an ANY_REAL data type](/images/mantissa.png "Structure of mantissa in an ANY_REAL data type")

The sign bit is 1 BIT in size and has the following meaning:
-	FALSE	= Positive number
-	TRUE 	= Negative number

The numerical value of the ANY_REAL number is determined using the following formula:
- +/- MANTISSA x 2 <sup>+/- EXPONENT</sup>

| Value (REAL)                       | Sign bit | Exponent | Mantissa                     |
|:-----------------------------------|:--------:|:--------:|:----------------------------:|
| 0,5 = 1 x 1 x 2<sup>-1</sup>       | 0        | 01111110 | **1**00000000000000000000000 |
| 50 = 1 x 1.5625 x 2<sup>5</sup>    | 0        | 10000100 | **1**10010000000000000000000 |
| \-5,1 = -1 x 1.275 x 2<sup>2</sup> | 1        | 10000001 | **1**01000110011001100110011 |

### TIME

The TIME data type is used for timer time instructions. The characteristics of the TIME data type are shown in the table below.

Time can be defined using one or more time units, which are applied in the correct order. It is not necessary to use all time units.
-	d: day
-	h: hour
-	m: minute
-	s: second
-	ms: millisecond

| Manufacturer | Notation               | Min. & max. value                                    |
|:------------:|:----------------------:|:----------------------------------------------------:|
| Beckhoff     | T\#10d20h30m20s630ms or TIME\#10d20h30m20s630ms         | T\#0ms to T\#71582m47s295ms                            |
| Siemens      | T\#10d_20h_30m_20s_630ms or TIME\#10d_20h_30m_20s_630ms | T\#-24d_20h_31m_23s_648ms to T\#+24d_20h_31m_23s_647ms |

### DATE, TIME_OF_DAY & DATE_AND_TIME

These data types are used when date and time need to be processed in the user program. The data types DATE, TIME_OF_DAY and DATE_AND_TIME can be used for this purpose. The structure of these data types depends on the manufacturer.

| Data type       | Manufacturer   | Characteristics                                                                                                                        |
|:-----------------:|:----------------:|:----------------------------------------------------------------------------------------------------------------------------------------:|
| DATE              | Beckhoff         | 4 BYTE / Year-month-day 1970-01-01 / 2106-02-07 notation: D\#1972-03-29                                                                  |
| DATE              | Siemens          | 2 BYTE / year-month-day 1990-01-01 / 2169-06-06 notation: D\#2009-12-31                                                                  |
| TIME_OF_DAY TOD   | Beckhoff Siemens | 4 BYTE / hour:min:sec:msec 00:00:00:000 / 23:59:59:999 notation: TOD\#15:36:30.123                                                       |
| DATE_AND_TIME DT  | Beckhoff         | 4 BYTE / year-month-day- hour:min:sec 1970-01-01, 00:00 / 2106-02-07, 06:28:15 notation: DT\#1996-05-06-15:36:30                         |
| DATE_AND_TIME DTL | Siemens S7-1200  | 12 BYTE / year-month-day- hour:min:sec:µsec 1970-01-01-00:00:00.0 / 2262-04-11-23:47:16.854775807 notation: DTL\#2008-12-16-20:30:20.250 |
| DATE_AND_TIME DT  | Siemens S7-300   | 8 BYTE / year-month-day- hour:min:sec:msec 1990-01-01-00:00:00.000 / 2089-12-31-23:59:59.999 notation: DT\#2008-10-25-08:12:34.567       |

```Examples
Examples of date and time applications in PLC user programs

•	Switching power on and off when no production is planned (e.g. weekends, holiday periods, public holidays, etc.)
•	Initializing a production machine at the start of a shift (e.g. resetting the number of parts produced to zero at the start of the shift)
```

### ANY_STRING

ANY_STRING data types are used for instructions relating to text.
A STRING is a collection of ASCII characters, with a maximum of 254 single BYTE characters stored in a single STRING. Each character is stored in a BYTE and is represented between single quotation marks. 

The first two BYTES of a STRING contain the “header”:
- The first BYTE contains the maximum length (default 256 BYTES)
- The second BYTE contains the number of BYTES used

![Structure of a STRING data type](/images/string.png "Structure of a STRING data type")

It is possible to specify the number of characters in a STRING so that its length can be limited. This is done by typing the length between square brackets.

A WSTRING is a collection of ASCII characters in which up to 254 double BYTE characters are stored in a single WSTRING. Compared to a STRING, a WSTRING stores 2 characters in a single WORD, which are displayed between double quotation marks. 
The first two WORDS of a WSTRING contain the “header”:
- The first WORD contains the maximum length (default 256 WORDS)
- The second WORD contains the number of WORDS used

![Structure of a WSTRING data type](/images/wstring.png "Structure of a WSTRING data type")

It is possible to specify the number of characters in a WSTRING so that its length can be limited. This is done by typing the length between square brackets.

##	Number systems
### Decimal number system

A number consists of a number of characters. The decimal number system is one of the best-known number systems, using 10 different characters, namely the digits 0 to 9.

However, there are other number systems besides the decimal number system that use more or fewer characters. In the field of (process) automation, the following are often used in addition to the decimal number system:
- The binary number system with 2 different characters
- The hexadecimal number system with 16 different characters

To avoid confusion between number systems, brackets and a base number are used to indicate the number system used:
-	Base number 2 = binary number system
-	Base number 10 = decimal number system
-	Base number 16 = hexadecimal number system

*(110)<sub>10</sub> \<\> (110)<sub>2</sub> \<\> (110)<sub>16</sub>*

When converting a non-decimal number system to the decimal number system, the following conversion formula can be used:

*(abc,de)<sub>X</sub> = (a.X<sup>2</sup> + b.X<sup>1</sup>> + C.X<sup>0</sup> + d.X<sup>-1</sup> + e.X<sup>-2</sup>)<sub>10</sub>*

```Examples
•	(321)₁₀ = 3·10² + 2·10ⁱ + 1·10⁰ = 300 + 20 + 1
•	(101)₁₀ = 1·10² + 0·10ⁱ + 1·10⁰ = 100 + 0 + 1
```

### Binary number system

The binary or two-part system has two different digits, namely 0 and 1, so the base number of this number system is 2. To represent numbers, digits are added in the same way as in the decimal number system.

| Decimal | Binary  |
|:-------:|:-------:|
| 0       | 0000 0000 |
| 1       | 0000 0001 |
| 2       | 0000 0010 |
| 3       | 0000 0011 |
| 4       | 0000 0100 |
| 5       | 0000 0101 |
| 6       | 0000 0110 |
| 7       | 0000 0111 |
| 8       | 0000 1000 |
| 9       | 0000 1001 |
| 10      | 0000 1010 |
| 11      | 0000 1011 |
| 12      | 0000 1100 |
| 13      | 0000 1101 |
| 14      | 0000 1110 |
| 15      | 0000 1111 |
| 16      | 0001 0000 |
| 17      | 0001 0001 |

To increase the readability of binary numbers, the digits are often grouped into groups of 4 digits.
Using the conversion formula, it is possible to determine the decimal value of a binary number.


### Hexadecimal number system 

In the hexadecimal number system, the base number is 16 and the characters used are the digits 0, 1, 2, 3, 4, 5...9 and the letters A, B, C, D, E and F.

The hexadecimal system is often used because it is easy to convert to the binary number system and because a relatively small number can represent many bits.

| Decimal | Binary  | Hexadecimal |
|:-------:|:-------:|:-----------:|
| 0       | 0000 0000 | 0         |
| 1       | 0000 0001 | 1         |
| 2       | 0000 0010 | 2         |
| 3       | 0000 0011 | 3         |
| 4       | 0000 0100 | 4         |
| 5       | 0000 0101 | 5         |
| 6       | 0000 0110 | 6         |
| 7       | 0000 0111 | 7         |
| 8       | 0000 1000 | 8         |
| 9       | 0000 1001 | 9         |
| 10      | 0000 1010 | A         |
| 11      | 0000 1011 | B         |
| 12      | 0000 1100 | C         |
| 13      | 0000 1101 | D         |
| 14      | 0000 1110 | E         |
| 15      | 0000 1111 | F         |
| 16      | 0001 0000 | 10        |
| 17      | 0001 0001 | 11        |

Since 4 bits can be combined in 16 possible ways, each hexadecimal digit can represent a group of 4 bits. This makes it easy to convert a hexadecimal number into a binary number.

![Hexadecimal numbers](/images/hexa.png)

To convert a hexadecimal number to a decimal number, you can use the conversion formula.

## Arranging bytes

Within the binary representation of a BYTE, the order of the BITS is fixed. The number is constructed from right to left.

![MSB and LSB bit in a BYTE](/images/msb_lsb.png "MSB and LSB bit in a BYTE")

Within a BYTE, it is possible to determine the BIT with
- The most significant value = MSB BIT = **M**ost **S**ignificant **B**IT
- The least significant value = LSB BIT = **L**east **S**ignificant **B**IT

```Trivia
How to determine the MSB and LSB BIT?

If we assume that all bits in a byte contain the value 0, then we can say that (0000 0000)₂ = (0)₁₀.
•	If only 1 BIT of state is changed to obtain the largest possible decimal number, the MSB BIT is determined, i.e. (1000 0000)₂ = (128)₁₀
•	If you change only 1 BIT of state to obtain the smallest possible decimal number,you have determined the LSB BIT, i.e. (0000 0001)₂ = (1)₁₀
```
The binary representation of a WORD, DWORD and LWORD is also fixed, but there are two different notations in use, namely:
- The Little Endian representation, which originated from Motorola processors
- The Big Endian representation, which originated from Intel processors

Here, the BYTES are structured internally in the same way (from right to left), but there is a difference in the location of the BYTES.

| Big Endian (Siemens) | Little Endian (Beckhoff) |
|:--------------------:|:------------------------:|
| ![Big Endian](/images/big_endian.png) | ![Little Endian](/images/little_endian.png) |

There are also examples of both systems in spoken language:
- The number 24 = Big Endian in English = twenty-four
- The number 24 = Little Endian in Dutch = vier-en-twintig (four-and-twenty)

Little Endian is often used in PCs because they use Intel processors (or similar). Because a Beckhoff PLC is equipped with a Microsoft Windows Embedded environment internally, these PLCs operate internally according to the Little Endian system.

![Example endian system at Beckhoff](/images/TwinCAT/endian.png)

Siemens PLCs, on the other hand, have used a Motorola processor (or similar) since their early years, which means that these PLCs operate internally according to the Big Endian system.

![Example endian system at Siemens](/images/TIA/endian.png)