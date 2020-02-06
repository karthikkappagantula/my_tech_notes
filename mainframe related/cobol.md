# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Basic Structure](#basic-structure)
  - [Basic Coding Rules](#basic-coding-rules)
  - [Identification Division](#identification-division)
  - [Environment Division](#environment-division)
    - [Working-Storage Section](#working-storage-section)
      - [Picture Clause](#picture-clause)
      - [Value Clauses](#value-clauses)
      - [Group items](#group-items)
      - [Accept statements](#accept-statements)
      - [Compute statements](#compute-statements)


* * *
[Top](#table-of-contents-)
* * *

## Basic Structure
* **Identification Division** identifies the program by giving the program name.
* **Environment Division** includes the *Input-Output Section*, which identifies the input and output files used by the program.
* **Data Division** includes the -
  * *File Section* describes the files identified in the Input-Output Section
  * *Working-Storage Section* defines other data items used by the program.
* **Procedure Division** contains the program logic. It is typically divided into procedures that contain the statements that do the
functions of the program.
## Basic Coding Rules

  | Columns      | Purpose        | Remarks  |
  | ------------ |:-------------|:-----------| 
  | 1-6      | Sequence | A sequence number is added to each line. Cannot be changed |
  | 7 | Indicator | '*' - Comment ,  '/' - listing on a new page  , '-' - continuation |
  | 8-11 | A margin | Division/Section/Procedure names, 77/01 level numbers should start in margin A |
  | 12-72 | B margin | Coding lines that don't start in A margin start here |
  | 73-80 | Identification | Not used by modern COBOL compilers |

## Identification Division

* Division header
* Program-ID paragraph followed by the program name.

*Syntax*
```
IDENTIFICATION DIVISION.
PROGRAM-ID. program-name.
```

## Environment Division

* Used to identify any disk files that are used by the program.
  
### Working-Storage Section

* Code the level number (77) in the A margin, and code the data name, its Picture (PIC) clause, and its Value clause (if any) in the B margin.
* Code the Value clause so it is consistent with the Picture clause for each data item (see figure 1-9 for more information
* Code a period at the end of each data item.
* You can use other level numbers when you want to group the items in working storage

*Syntax*
```
WORKING-STORAGE SECTION.
*
77 END-OF-SESSION-SWITCH
77 SALES-AMOUNT
77 SALES-TAX
```

#### Picture Clause

* The Picture clause (PIC) defines the format of the data that can be stored in the field.
* When coding a Picture clause, a number in parentheses means that the preceding character is repeated that number of times.
* When data is stored in an alphanumeric item, unused positions to the right are set to spaces. When data is stored in a numeric
item, unused positions to the left are set to zeros.

| Data type    | Character | Meaning  | Example  |
| ------------ |:----------|:--------|:----| 
| Alphanumeric | X | Any Character | PIC X |
| Numeric | 9 | Digits | PIC 9(2) |
|  | S | Sign | PIC S9(2) |
|  | V | Assumed decimal | PIC S9(2)v9(3) |
| Numeric edited | Z | Zero suppressed | PIC ZZ9 |
| | , | Inserted commas | PIC ZZZ,ZZZ |
| | . | Inserted decimal | PIC ZZZ.ZZZ |
| | - | Minus sign of negative | PIC ZZZ,ZZZ- |

#### Value Clauses

* The Value clause defines the value that is stored in the field when the program starts. As a result, the value should be consistent with the type of item that’s defined by the Picture clause.
* In contrast to the rest of the program, the characters between the quotation marks in an alphanumeric literal are case sensitive.
So the value of “End of Session” is: End of Session.
* If the Value clause defines a value that is smaller than the field defined by the Picture clause, an alphanumeric field is filled out with spaces on the right; a numeric field is filled out with zeroes on the left.
* If the Value clause defines a value that is larger than can be stored in the field defined by the Picture clause, a compiler error will
occur.
* Because a numeric edited item typically receives a value as the result of a Move statement, it usually is not defined with a Value
clause.

#### Group items

* To code group items, you use the level numbers 01 through 49. Typically you will start with 01, and then use multiples of 5, such
as 05 and 10. This allows you some room to add other levels later if you need to.
* Level 01 items must begin in the A margin. Other level numbers can begin in either the A or B margin.
* Whenever one data item has higher level numbers beneath it, it is a group item and the items beneath it are elementary items.
In the example below, USER-ENTRIES, WORK-FIELDS, and TODAYS-DATE are group items. All of the others are elementary
items.
* You can’t code a Picture clause for a group item, and you have to code a Picture clause for an elementary item.
* A group item is always treated as an alphanumeric item, no matter how the elementary items beneath it are defined.
* To make the structure of the data items easy to read and understand, you should align the levels as shown below. However, this indentation isn’t required.

```
 WORKING-STORAGE SECTION.
*
 01 USER-ENTRIES.
*
    05 NUMBER-ENTERED
    05 INVESTMENT-AMOUNT
    05 NUMBER-OF-YEARS
    05 YEARLY-INTEREST-RATE
*
 01 WORK-FIELDS.
*
    05 FUTURE-VALUE
    05 YEAR-COUNTER
    05 EDITED-FUTURE-VALUE
    05 TODAYS-DATE.
       10 TODAYS-MONTH
       10 TODAYS-DAY
       10 TODAYS-YEAR
```

#### Accept statements

* Accept statement gets its data from the SYSIN device

*Syntax*
```
ACCEPT data-name
```

#### Compute statements

* The Compute statement calculates the arithmetic expression to the right of the equals sign and stores the result in the variable to the left of the equals sign.
* Within the expression, you use the arithmetic operators for addition, subtraction, multiplication (*), division, and exponentiation
(**). Exponentiation means “raise to the power of” so A ** 2 is the same as A2.
* All variables in the arithmetic expression must be numeric items.
* The variable that will contain the result of the arithmetic expression can be a numeric edited item if that variable isn’t used in the arithmetic expression. Otherwise, it must be numeric.
* You can code the Rounded clause whenever the result of a calculation can have more decimal places than are specified in the
picture of the result field. If you don’t use the Rounded clause, the extra decimal places are truncated.
* You can code the On Size Error clause when there’s a chance that the result may be larger than the receiving field. If it is, the
statements in this clause are executed.

*Syntax*
```
COMPUTE data-name [ROUNDED] = arithmetic-expression
    [ON SIZE ERROR statement-group]
```

