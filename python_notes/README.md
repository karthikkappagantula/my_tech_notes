# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Important URLs](#important-urls)
  - [Install Anaconda](#install-anaconda)
  - [Jupyter Intro](#jupyter-intro)
  - [Keywords](#keywords)
  - [Data Types in Python](#data-types-in-python)
    - [Integers](#integers)
- [define in base 2 / binary](#define-in-base-2--binary)
- [define in base 8 / octal](#define-in-base-8--octal)
- [define in base 16 / hexa](#define-in-base-16--hexa)
    - [Floating-Point](#floating-point)
    - [Complex Numbers](#complex-numbers)
    - [Strings](#strings)
    - [Booleans](#booleans)
  - [Arithmetic Operations](#arithmetic-operations)
  - [Math Functions](#math-functions)
  - [Printing output](#printing-output)
    - [Formatting output](#formatting-output)
  - [Taking Inputs](#taking-inputs)
  - [Strings](#strings-1)
    - [String functions](#string-functions)
  - [Conditional Statements - if/elif/else](#conditional-statements---ifelifelse)
  - [For Loops](#for-loops)
  - [Data Structures](#data-structures)
    - [Lists](#lists)
    - [Lists funtions](#lists-funtions)
    - [Slicing Lists](#slicing-lists)
    - [Tuples](#tuples)
    - [Dictionaries](#dictionaries)
  - [Functions](#functions)
  - [Exception handling](#exception-handling)
  - [Classes and Objects](#classes-and-objects)
    - [Inheritence](#inheritence)
  - [Regular Expressions](#regular-expressions)
  - [Modules and Packages](#modules-and-packages)
    - [PyPI and PIP](#pypi-and-pip)
  - [File Operations (Read/Write Operations)](#file-operations-readwrite-operations)
  - [Working with Directories](#working-with-directories)
  - [Date & Time](#date--time)
  - [How you code matters](#how-you-code-matters)

## Important URLs
[Python Standard Libraries](https://docs.python.org/3/library/)<br>
[Python Math Module](https://docs.python.org/3/library/math.html)<br>
[Python Module Index](https://docs.python.org/3/py-modindex.html)<br>
[Python Package Index](https://pypi.org/)<br>

* * *
[Top](#table-of-contents)
* * * 
## Install Anaconda 
* Install Anaconda - a data science platform that includes Jupyter notebook and is packed with important Python and Datascience libraries. <br />
https://www.anaconda.com/distribution/#download-section <br />

Idle3 is installed with Anaconda. Idle3 is a interative IDE that interprets each python statement as you use and execute them.

Sample code:
<pre>
Python 3.7.4 (default, Aug 13 2019, 15:17:50) 
[Clang 4.0.1 (tags/RELEASE_401/final)] on darwin
Type "help", "copyright", "credits" or "license()" for more information.
>>> print('Hello World!')
Hello World!
>>> from time import gmtime
>>> print(gmtime())
time.struct_time(tm_year=2019, tm_mon=12, tm_mday=31, tm_hour=16, tm_min=48, tm_sec=18, tm_wday=1, tm_yday=365, tm_isdst=0)
>>> 
</pre>

To kill Idle3 session -
<pre>
quit()
</pre>
* * *
[Top](#table-of-contents)
* * * 
## Jupyter Intro 
To Start Jupyter Notebook - 
<pre>
(base) Karthiks-MacBook-Air:~ karthikkappagantula$ jupyter notebook
[I 15:43:51.696 NotebookApp] JupyterLab extension loaded from /Users/karthikkappagantula/opt/anaconda3/lib/python3.7/site-packages/jupyterlab
[I 15:43:51.696 NotebookApp] JupyterLab application directory is /Users/karthikkappagantula/opt/anaconda3/share/jupyter/lab
[I 15:43:51.700 NotebookApp] Serving notebooks from local directory: /Users/karthikkappagantula
[I 15:43:51.700 NotebookApp] The Jupyter Notebook is running at:
[I 15:43:51.700 NotebookApp] http://localhost:8888/?token=3884620c15c49428c9fab4e74d55d9725600761a3331ca63
[I 15:43:51.700 NotebookApp]  or http://127.0.0.1:8888/?token=3884620c15c49428c9fab4e74d55d9725600761a3331ca63
[I 15:43:51.700 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 15:43:51.713 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///Users/karthikkappagantula/Library/Jupyter/runtime/nbserver-3154-open.html
    Or copy and paste one of these URLs:
        http://localhost:8888/?token=3884620c15c49428c9fab4e74d55d9725600761a3331ca63
     or http://127.0.0.1:8888/?token=3884620c15c49428c9fab4e74d55d9725600761a3331ca63

</pre>


After launching Jupyter notebook as above, a new browser is opened for Jupyter window.
![Jupyter_Intro](https://github.com/karthikkappagantula/my_tech_notes/blob/master/python_notes/resources/jupyter_intro.png)

For creating new python script : new -> select python version
![new script](https://github.com/karthikkappagantula/my_tech_notes/blob/master/python_notes/resources/newscript.png)
* Select each cell after typing code and run the cell using "Run/Play" button.
* To save the script, double click the file name on top (Untitled is default filename)
* You can download the file as a .py file using file -> download as .py file

***Keyboard shortcuts***
* select a cell and press control + enter -> to execute a cell
* select a cell and press shift + tab -> presents the tooltip with details of function used in the cell.

* * *
[Top](#table-of-contents)
* * * 

## Keywords
* Python language also reserves some of keywords that convey special meaning. Knowledge of these is necessary part of learning this language. 

  <pre>
    #importing "keyword" for keyword operations 
    import keyword 

    #printing all keywords at once using "kwlist()" 
    print ("The list of keywords is : ") 
    print (keyword.kwlist) 
  </pre>

  *Output*:
  <pre>
    The list of keywords is : 
    ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
  </pre>

* * *
[Top](#table-of-contents)
* * * 

## Data Types in Python

### Integers

* Whole numbers
* Default base used is base10, but can be converted or displayed in other bases.
* Any limit allowed up to memory limit of computer

  <pre>
  a = 10
  b = 5
  print(a, b)
  print(type(a), type(b))
  </pre>

  *Output:*
  <pre>
  10 5
  <class 'int'> <class 'int'>
  </pre>

* Defining different bases for integers
  
  <pre>
  # define in base 2 / binary
  c = 0b00110110
  print(c)
  print(type(c))
  # define in base 8 / octal
  d = 0o452300
  print(d)
  print(type(d))
  # define in base 16 / hexa
  e = 0x234A2B
  print(e)
  print(type(e))
  </pre>

  *Output*:
  <pre>
  54
  <class 'int'>
  152768
  <class 'int'>
  2312747
  <class 'int'>
  </pre>

* A given integer in base 10 decimal can be converted in to other bases using built-in functions such as *bin, oct, hex, etc.*.
  <pre>
  f = 1130
  print(bin(f))
  print(oct(f))
  print(hex(f))
  </pre>

  *Output*:
  <pre>
  0b10001101010
  0o2152
  0x46a
  </pre>

  
* Type conversion to String
  * A *TypeError* will be thrown when an mathematical operation is done on none integer.
  
    <pre>
    num1 = '4'
    num2 = 1
    print(type(num1), '|', type(num2))
    print(num1 + num2)
    </pre>

    *Output*:
    ```
    <class 'str'> | <class 'int'>
    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)
    <ipython-input-14-f86fc6987c79> in <module>
        2 num2 = 1
        3 print(type(num1), '|', type(num2))
    ----> 4 print(num1 + num2)

    TypeError: can only concatenate str (not "int") to str
    ```

  * Use data type conversion / type casting
    * Enclose the string within as *int(string-variable-name)*

    <pre>
    num1 = '4'
    num2 = 1
    print(type(num1), '|', type(num2))
    print(int(num1) + num2)
    </pre>

    *Output*:
    ```
    <class 'str'> | <class 'int'>
    5
    ```

### Floating-Point 

* Any number with a decimal point.
* Division result will be a float.
* Can be defined using scientific notations (0.09 as 9 x 10^-2)
  
  <pre>
  print(type(0.5))  #type is float if decimal is used
  print(type(0.5 + 0.4))
  print(type(10 / 2)) #result of division is a float
  print(type(10 // 2)) #integer division
  print(9e-3 , '==>', type(9e-3)) #scientific notation

  #Beware of the precision errors that may creep up with Floating point arithmetic
  print(0.2 + 0.1)
  </pre>

  *Output*:
  ```
  <class 'float'>
  <class 'float'>
  <class 'float'>
  <class 'int'>
  0.009 ==> <class 'float'>
  0.30000000000000004
  ```

### Complex Numbers

* A complex number is a number that can be expressed in the form a + bj, where a and b are real numbers, and j is a solution of the equation x2 = −1.

<pre>
print(2+3j)
print(type(2+3j))
</pre>

*Output*:
```
(2+3j)
<class 'complex'>
```
Python supports all artimetic operations on complex numbers. 

### Strings
Covered in a seperate section

### Booleans
* bool(x) -> bool
  Returns True when the argument x is true, False otherwise.
* The builtins True and False are the only two instances of the class bool.
* The class bool is a subclass of the class int, and cannot be subclassed.

<pre>
print(type('True'))
print(type(True))
</pre>

*Output*:
```
<class 'str'>
<class 'bool'>
```

* * *
[Top](#table-of-contents)
* * * 
## Arithmetic Operations

  Examples:
  <pre>
  print(5 + 3)  # Addition
  print(5 * 3)  # Multiplication
  print(5 - 3)  # Subtraction
  print(5 / 3)  # Division returns quotient in decimal number
  print(5 // 3) # Division returns quotient in whole number
  print(5 % 3)  # Modulo returns Remainder
  print(5 ** 3) # Exponent
  </pre>
  *Output*:
  <pre>
  8
  15
  2
  1.6666666666666667
  1
  2
  125
  </pre>

  +=  --> x = x + 5 can be written as x += 5 <br>
  -=  --> x = x - 5 can be written as x -= 5 <br>
  *=  --> x = x * 5 can be written as x *= 5 <br>
  /=  --> x = x / 5 can be written as x /= 5 <br>
  (Can be similarly used for other operators too)

  **Operator precedence follows same standard as in other programming languages BODMAS/PEMDAS**

## Math Functions

* Built-in math functions
  
  Example:
  <pre>
  x = 2.9
  print(round(x))    #rounds up
  print(abs(x * -1)) #asolute value
  </pre>

  *Output*:
  <pre>
  3
  2.9
  </pre>

* Use(import) **math** module for complex mathematical functions. 
  
  Example:
  <pre>
  import math
  print(math.ceil(2.9))  #ceil value
  print(math.floor(2.9)) #floor value
  print(math.factorial(3)) #factorial
  </pre>

  *Output*:
  <pre>
  3
  2
  6
  </pre>

*[Python Math Module](https://docs.python.org/3/library/math.html)*

## Printing output

* Python has a predefined format if you use print(a_variable) then it will go to next line automatically.

  <pre>
  Syntax: print(value(s), sep= ‘ ‘, end = ‘\n’, file=file, flush=flush)

  Parameters:
  value(s) : Any value, and as many as you like. Will be converted to string before printed
  sep=’separator’ : (Optional) Specify how to separate the objects, if there is more than one.Default is ’ ‘
  end=’end’: (Optional) Specify what to print at the end.Default is ‘\n’
  file : (Optional) An object with a write method. Default is sys.stdout
  flush : (Optional) A Boolean, specifying if the output is flushed (True) or buffered (False). Default is False
  </pre>

  **Examples**

  <pre>
    # Python 3.x program showing how to print data on a screen 
      
    # One object is passed 
    print("GeeksForGeeks") 
      
    x = 5
    # Two objects are passed 
    print("x =", x) 
      
    # code for disabling the softspace feature  
    print('G', 'F', 'G', sep ='') 
      
    # using end argument - does not print subsequent lines on a new line
    print("Python", end = '@')   
    print("GeeksforGeeks")  

    print('G','F', sep='', end='') 
    print('G') 
    #\n provides new line after printing the year 
    print('09','12', sep='-', end='-2016\n') 
  </pre>

  *Output*:
  <pre>
    GeeksForGeeks
    x = 5
    GFG
    Python@GeeksforGeeks
    GFG
    09-12-2016
  </pre>

* * *
[Top](#table-of-contents)
* * * 

### Formatting output

* **Formatting output using String modulo operator(%)** :

  The % operator can also be used for string formatting. It interprets the left argument much like a printf()-style format string to be applied to the right argument. 

  <pre>
    # Python program showing how to use string modulo operator(%) to print fancier output 
      
    # print integer and float value 
    print("Geeks : % 2d, Portal : % 5.2f" %(1, 05.333))  
      
    # print integer value 
    print("Total students : % 3d, Boys : % 2d" %(240, 120)) 
      
    # print octal value 
    print("% 7.3o"% (25)) 
      
    # print exponential value 
    print("% 10.3E"% (356.08977)) 
  </pre>

  *Output*:
  <pre>
    Geeks :  1, Portal :  5.33
    Total students :  240, Boys :  120
    031
    3.561E+02
  </pre>

* The general syntax for a format placeholder is:
  
  <pre> %[flags][width][.precision]type </pre>

  Let’s take a look at the placeholders in our example.

  The first placeholder “%2d” is used for the first component of our tuple, i.e. the integer 1. The number will be printed with 2 characters. As 1 consists only of one digits, the output is padded with 1 leading blanks.

  Our float number 05.333 has to be formatted with 5 characters. The decimal part of the number or the precision is set to 2, i.e. the number following the “.” in our placeholder. Finally, the last character “f” of our placeholder stands for “float”.

* **Formatting output using format method** :
  
  User use {} to mark where a variable will be substituted and can provide detailed formatting directives, but user also needs to provide the information to be formatted. This method lets us concatenate elements within an output through positional formatting. 

  *Examples*
  <pre>
    # using format() method 
    print('I love {} for "{}!"'.format('Geeks', 'Geeks')) 
      
    # using format() method and refering  
    # a position of the object 
    print('{0} and {1}'.format('Geeks', 'Portal')) 
      
    print('{1} and {0}'.format('Geeks', 'Portal')) 
  </pre>

  *Output*:
  <pre>
    I love Geeks for "Geeks!"
    Geeks and Portal
    Portal and Geeks
  </pre>

  <pre>
    # combining positional and keyword arguments 
    print('Number one portal is {0}, {1}, and {other}.'
        .format('Geeks', 'For', other ='Geeks')) 
      
    # using format() method with number  
    print("Geeks :{0:2d}, Portal :{1:8.2f}". 
          format(12, 00.546)) 
      
    # Changing positional argument 
    print("Second argument: {1:3d}, first one: {0:7.2f}". 
          format(47.42, 11)) 
      
    print("Geeks: {a:5d},  Portal: {p:8.2f}". 
        format(a = 453, p = 59.058)) 
  </pre>

  *Output*:
  <pre>
    Number one portal is Geeks, For, and Geeks.
    Geeks :12, Portal :    0.55
    Second argument:  11, first one:   47.42
    Geeks:   453, Portal:    59.06
  </pre>

  <pre>
    # Python program to show format () is used in dictionary 
      
    tab = {'geeks': 4127, 'for': 4098, 'geek': 8637678} 
      
    # using format() in dictionary 
    print('Geeks: {0[geeks]:d}; For: {0[for]:d}; '
        'Geek: {0[geek]:d}'.format(tab)) 
      
    data = dict(fun ="GeeksForGeeks", adj ="Portal") 
      
    # using format() in dictionary 
    print("I love {fun} computer {adj}".format(**data))    
    # remember to use '**' before dictionary data to be formatted.
  </pre>

  *Output*:
  <pre>
    Geeks: 4127; For: 4098; Geek: 8637678
    I love GeeksForGeeks computer Portal
  </pre>

* **Formatted String** 
  
  Example:
  <pre>
  first = 'John'
  last  = 'Wick'
  message = f'{first} {last} is a coder'  #formatted string
  print(message)
  </pre>

  *Ouput*:
  <pre>
  John Wick is a coder
  </pre>

* **Formatting output using String method**:
  In this output is formatted by using string slicing and concatenation operations. The string type has some methods that help in formatting a output in an fancier way. Some of method which help in formatting a output are str.ljust(), str.rjust(), str.centre()

  <pre>
    # Python program to format a output using string() method 
      
    cstr = "I love geeksforgeeks"
        
    # Printing the center aligned   
    # string with fillchr  
    print ("Center aligned string with fillchr: ")  
    print (cstr.center(40, '#'))  
      
    # Printing the left aligned   
    # string with "-" padding   
    print ("The left aligned string is : ")  
    print (cstr.ljust(40, '-')) 
      
    # Printing the right aligned string  
    # with "-" padding   
    print ("The right aligned string is : ")  
    print (cstr.rjust(40, '-')) 
  </pre>

  *Output*:
  <pre>
    Center aligned string with fillchr: 
    ##########I love geeksforgeeks##########

    The left aligned string is : 
    I love geeksforgeeks--------------------

    The right aligned string is : 
    --------------------I love geeksforgeeks
  </pre>

* * *
[Top](#table-of-contents)
* * * 

## Taking Inputs

Python provides us with two inbuilt functions to read the input from the keyboard.

* input ( prompt )  --> works in python 3.x
  <pre>
    # Python program showing a use of input() 
      
    val = input("Enter your value: ") 
    print(val) 
  </pre>

    Whatever you enter as input, input function convert it into a string. if you enter an integer value still input() function convert it into a string. You need to explicitly convert it into an integer in your code using typecasting.

  <pre>
    # Program to check input type in Python 
      
    num = input ("Enter number :") 
    print(num) 
    name1 = input("Enter name : ") 
    print(name1) 
      
    # Printing type of input value 
    print ("type of number", type(num)) 
    print ("type of name", type(name1)) 
  </pre>

    *Output*:
    ```    
    Enter number :hello
    hello
    Enter name : there
    there
    type of number <class 'str'\>
    type of name <class 'str'\>
    ```

* * *
[Top](#table-of-contents)
* * * 

## Strings
* Strings are a list of characters. So you can access each character using index from 0 or -1 (indexes from back)
  
  Examples:
    <pre>
    message="learning"
    print(message[0])   #prints first character
    print(message[-1])  #prints last character
    print(message[0:4]) #prints characters from index 0 to 4 (excludes character at index=4).
    print(message[:-1]) #prints all characters except last character
    print(message[0:])  #prints all characters
    print(message[:])   #prints all characters
    </pre>

  *Output*:
    <pre>
    l
    g
    lear
    learnin
    learning
    learning
    </pre>

* Strings that includes quotes/double quotes.

  Examples:
    <pre>
    #wrap message with single quotes in double quotes
    message="this is tom's message"    
    print(message)

    #wrap message with double quotes in single quotes
    message1='this is "python" notes'  
    print(message1)

    #use escape character followed by a quote ( \" or \' ).
    message2='this is \"python\" notes with tom\'s message'   
    print(message2)
    </pre>

    *Output*:
    <pre>
    this is tom's message
    this is "python" notes
    this is "python" notes with tom's message
    </pre>

* Escape characters
  * \n -> leaves a line
  * \t -> leaves a tab space
  * \\\ -> backslash
  * \\' -> single quote
  * \\" -> double quote

  Examples:
    <pre>
    ch = "I\nLove\tGeeksforgeeks"

    print ("The string after resolving escape character is : ") 
    print (ch) 
    </pre>

    *Output*:
    <pre>
    The string after resolving escape character is : 
    I
    Love	Geeksforgeeks
    </pre>

Using repr() -> This function returns a string in its printable format, i.e doesn’t resolve the escape sequences.

  Example:
    <pre>
    ch = "I\nLove\tGeeksforgeeks"
    print ("The string without repr() is : ") 
    print (ch) 
    print ("\r") 
    print ("The string after using repr() is : ") 
    print (repr(ch)) 
    ch2 = R"I\nLove\tGeeksforgeeks"     
    print ("The string after using R is : ") 
    print (ch2) 
    </pre>

    *Output*: 
    <pre>
    The string without repr() is : 
    I
    Love	Geeksforgeeks

    The string after using repr() is : 
    'I\nLove\tGeeksforgeeks'

    The string after using R is : 
    I\nLove\tGeeksforgeeks
    </pre>
* * *
[Top](#table-of-contents)
* * * 
### String functions

Examples:
  <pre>
  course = 'John Wick is breathtaking'
  print(len(course))
  print((course.upper())) #returns all chars in upper case
  print(course)           #but does not alter original value
  print((course.lower())) #returns all chars in lower case
  print((course.title())) #Makes first char of each word uppercase
  print((course.find('o'))) #returns first index of the char 'o'
  print((course.find('z'))) #returns -1 as 'z' does not exist in course
  print((course.find('j'))) #returns -1 as 'j' does not exist - find is case sensitive
  print((course.replace('Wick', 'Locke'))) #replaces the String found with new String
  print('John' in course) #verify if a string exists
  </pre>

  *Output*:
  <pre>
  25
  JOHN WICK IS BREATHTAKING
  John Wick is breathtaking
  john wick is breathtaking
  John Wick Is Breathtaking
  1
  -1
  -1
  John Locke is breathtaking
  True
  </pre>
  

* * *
[Top](#table-of-contents)
* * * 
  
## Conditional Statements - if/elif/else
* Indentation is used to determine the scope. 
* elif is nothing but an else if

Example
  <pre>
  #if/elif/else statement
  temp_num = 10
  if temp_num%3 == 0:
      print('Divisible by 3')
  elif temp_num%2 == 0:
      print('Divisible by 2')
  else:
      print('Default')
  </pre>

  *Output*:
  <pre> Divisible by 2 </pre>
* * *
[Top](#table-of-contents)
* * * 
  
## For Loops

* Index starts with 0
* break statement can be used to exit from the loop based on a condition
<pre>
    break;
</pre>
* continue statement can be used to continue to next iteration of the loop
<pre>
    continue;
</pre>


Examples:
<pre>
#for loops
for i in range(5):
    print(i)

*Ouput:* 
0
1
2
3
4
</pre>
* * *
<pre>
for i in range(5):
    random_num = random.randint(2,7)
    print(random_num)
    time.sleep(random_num)
    
    this_second = the_time().tm_sec
    #String formatting with the % operator
    print('This second: %s' %this_second)

*Ouput*:
2
This second: 31
6
This second: 37
4
This second: 41
2
This second: 43
3
This second: 46
</pre>
* * *
[Top](#table-of-contents)
* * * 
  
## Data Structures

### Lists

* Lists are like arrays with elements that can be accessed using indexes.
* Lists are created using comma separated elements with in Square brackets. <br>
  
  Example :
  <pre> 
  list1 = [1, 2, 3, 4, 5] 
  print(list1)
  </pre>
  *Output:*
  <pre>
  [1, 2, 3, 4, 5]
  </pre>


* Lists can have elements of any type (numeric, alphabetic, string)

  Example :
  <pre>
  list2 = [1, 'a', 'abcd'] 
  print(list2)
  </pre>
  *Output:*
  <pre>
  [1, 'a', 'abcd']
  </pre>

* Elements in the Lists can be accessed from both from and back using index.
* Index 0 or Index -1 gives access to first element.
  
  Example :
  <pre>
  list1 = [1, 2, 3, 4, 5] 
  print(list1[0])
  print(list1[-1])
  </pre>
  *Output*:
  <pre>
  1
  5
  </pre>

* * *
[Top](#table-of-contents)
* * * 
  
### Lists funtions

* There are many built in python functions that can be run against Lists.

  <pre>
  list1 = [1, 2, 3, 4, 5] 
  print(len(list1))
  </pre>
  *Output:*
  <pre>
  5
  </pre>

* Append and remove functions let you add and remove elements.

  <pre>
  list1 = [1, 2, 3, 4, 5] 
  print(len(list1))
  print(list1)
  print('_________________')
  list1.append(6)
  print(len(list1))
  print(list1)
  print('_________________')
  list1.remove(2)
  print(len(list1))
  print(list1)
  </pre>
  *Output:*

  <pre>
  5
  [1, 2, 3, 4, 5]
  _________________
  6
  [1, 2, 3, 4, 5, 6]
  _________________
  5
  [1, 3, 4, 5, 6]
  </pre>

* * *
[Top](#table-of-contents)
* * * 
  
* To remove an element from end, use pop function.
  
  <pre>
  list1 = [1, 2, 3, 4, 5]
  poppedValue = list1.pop()
  print('Popped value = %s' %poppedValue)
  print(list1)
  </pre>
  *Output:*
  <pre>
  Popped value = 5
  [1, 2, 3, 4]
  </pre>

* To insert an element at a particular index, use insert function.

  <pre>
  list1 = [1, 2, 3, 4, 5]
  print(list1)
  list1.insert(2, 3.5)
  print(list1)
  </pre>
  *Output:*
  <pre>
  [1, 2, 3, 4, 5]
  5
  [1, 2, 3.5, 3, 4, 5]
  6
  </pre>

* To extend an list with another list, use extend function.

  <pre>
  list1 = [1, 2, 3, 4, 5]
  print(list1)
  print(len(list1))
  list1.extend([6, 7, 8, 9])
  print(list1)
  print(len(list1))
  </pre>
  *Output:*
  <pre>
  [1, 2, 3, 4, 5]
  5
  [1, 2, 3, 4, 5, 6, 7, 8, 9]
  9
  </pre>

* * *
[Top](#table-of-contents)
* * * 

**2-Dimensional Lists**

* 2-Dimensional Matrix (or) lists with in list

  Example:
  <pre>
  twodlist = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
  ]
  print(twodlist)
  print(twodlist[0])
  print(twodlist[0][0])
  </pre>
  *Output*:
  <pre>
  [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
  [1, 2, 3]
  1
  </pre>

### Slicing Lists

* Start, Stop and Step notation can be used to extract elements from the list based on consistent increments

  <pre>
  list1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
  num_list_2 = list1[0:9:2]
  print(num_list_2)
  </pre>

  *Output:*
  <pre>
  [1, 3, 5, 7, 9]
  </pre>

* Few examples of slicing 
  
  <pre>
  list1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
  #prints all elements from index position 4 to end of list
  print(list1[4:])  
  #prints all elements from start till last element (Last element excluded due to mention of -1)    
  print(list1[:-1])  
  #prints elements starting from index 3 with increment of 2 until index 10   
  print(list1[3:10:2])  
  #prints the list in reverse order
  print(list1[::-1])    
  </pre>

  *Output:*
  <pre>
  [5, 6, 7, 8, 9, 10, 11, 12]
  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
  [4, 6, 8, 10]
  [12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
  </pre>

* Difference between list assignment and list.copy()
  
  <pre>
  list1 = ["hello","there"]
  print(list1)
  list2 = list1  #using assignment makes the list2 refer to same object(list1)
  print("list2:" + str(list2))
  list1.append("!")
  print("list1:" + str(list1))
  print("list2:" + str(list2))
  list3=list1.copy()
  print("list3:" + str(list3))
  list1.append(".")
  print("list1:" + str(list1))
  print("list3:" + str(list3))
  </pre>

  *Output:*
  <pre>
  ['hello', 'there']
  list2:['hello', 'there']
  list1:['hello', 'there', '!']
  list2:['hello', 'there', '!']
  list3:['hello', 'there', '!']
  list1:['hello', 'there', '!', '.']
  list3:['hello', 'there', '!']
  </pre>
* * *
[Top](#table-of-contents)
* * * 

### Tuples

* Unlike lists, tuples cannot be altered once defined.
* Tuples are immutable.
* Tuples are created using comma separated elements with in round brackets.

  <pre>
  tup = (1, 2, 3)
  print(tup)
  print(tup[0])
  tup[0] = 0    #generates TypeError
  </pre>
  *Output*:
  <pre>
  (1, 2, 3)
  1

  TypeError                                 Traceback (most recent call last)
  <ipython-input-8-1160e2902c2c> in <module>
    2 print(tup)
    3 print(tup[0])
  ----> 4 tup[0] = 0

  TypeError: 'tuple' object does not support item assignment
  </pre>

* **Unpacking**
  We can unpack tuples/lists in to set of variables as show below
  <pre>
  coordinates = (1, 2, 3)
  x, y, z = coordinates
  print('x: ' + str(x) + ' y: ' + str(y) + ' z: ' + str(z))
  </pre>
  *Output*:
  <pre>
  x: 1 y: 2 z: 3
  </pre>

* * *
[Top](#table-of-contents)
* * * 

### Dictionaries
* Datastructure based on Key-value pairs. Similar to JSON.
* Dictionaries are created using comma separated key-value pairs with in Curly brackets.
* Keys should be unique in the dictionaries.
  
<pre>
customer = {
    "name" : "John Wick",
    "age"  : 40,
    "is_awol" : True
}
print(customer)
print(customer["name"])  #to access value for key "name"
</pre>
*Output*:
<pre>
{'name': 'John Wick', 'age': 40, 'is_awol': True}
John Wick
</pre>

* * *
[Top](#table-of-contents)
* * * 

## Functions
* Create re-usable code in Functions
  
  <pre>
  def greet_user():
      print('Hi there!')
      print('Welcome aboard')


  print("Start")
  greet_user()
  print("Finish")
  </pre>
  *Output*:
  <pre>
  Start
  Hi there!
  Welcome aboard
  Finish
  </pre>

* You can pass argument to functions that can be used with in functions
* If you do not pass argument to a function that has parameters defined, the program fails with TypeError
  <pre>
  def greet_user(name):
      print(f'Hi there!, {name}')
      print('Welcome aboard')


  print("Start")
  greet_user("John Wick")
  greet_user("John Locke")
  greet_user()    **#this fails due to missing argument**
  print("Finish")
  </pre>

  *Output*:
  <pre>
  Start
  Hi there!, John Wick
  Welcome aboard
  Hi there!, John Locke
  Welcome aboard

  TypeError                                 Traceback (most recent call last)
  <ipython-input-11-68dab155bf9f> in <module>
    8 greet_user("John Wick")
    9 greet_user("John Locke")
  ---> 10 greet_user()
    11 print("Finish")

  TypeError: greet_user() missing 1 required positional argument: 'name'
  </pre>

* **Keyword Arguments** 
  * Arguments are passed as key-value pair. This improves readability. 
  * Order of keyword arguments does not matter as the mapping between arguments and parameters is done based on keys used.
  * When using both positional and keyword arguments, always use keyword arguments after positional arguments

  <pre>
  def greet_user(first_name, last_name):
      print(f'Hi there!, {first_name} {last_name}')
      print('Welcome aboard')

  print("Start")
  greet_user(last_name="Wick" , first_name="Wick")
  print("Finish")
  </pre>

  *Output*:
  <pre>
  Start
  Hi there!, John Wick
  Welcome aboard
  Finish
  </pre>

* **Return Statements**
  * Using return statement you can pass back values / results to invoking statement.
  <pre>
  def square(number):
      return number * number

  print(square(3))
  print(square(5))
  </pre>
  *Output*:
  <pre>
  9
  25
  </pre>

  * By default python always returns back 'None' value.
  
  <pre>
  def square(number):
      print(number * number)

  print(square(3))
  </pre>
  *Output*:
  <pre>
  9
  None
  </pre>

* * *
[Top](#table-of-contents)
* * * 

## Exception handling

* Exceptions occurs whenever there is a violation of acceptable functionality. Few sample exceptions:
  * Passing a character to a numeric variable (ValueError)
    <pre>
    age = int(input('Age:'))
    print(age)
    </pre>
    *Output*:
    <pre>
    Age:a
    ValueError                                Traceback (most recent call last)
    <ipython-input-18-a3ccad679065> in <module>
    ----> 1 age = int(input('Age:'))
      2 print(age)

    ValueError: invalid literal for int() with base 10: 'a'
    </pre>
  * Divide by zero (ZeroDivisionError)
    <pre>
    a = 10
    b = 0
    print (a/b)
    </pre>

    *Output*:
    <pre>
    ZeroDivisionError                         Traceback (most recent call last)
    <ipython-input-26-57a7363b4947> in <module>
      1 a = 10
      2 b = 0
    ----> 3 print (a/b)

    ZeroDivisionError: division by zero
    </pre>
  * Not passing the positional arguments to a function (TypeError) <br>
    Refer [Functions](#functions)
* These exceptions have to be handled to make the program end gracefully. Use 'try/except' blocks to handle this.
* It is always recommended to handle particular exceptions.
  
  <pre>
  try:
      age = int(input('Age:'))
      print(age)
      income = 1000
      print (income/age)
  except ValueError:
      print("Invalid value")
  except ZeroDivisionError:
      print("Age cannor be 0")
  </pre>

  *Output*:
  <pre>
  #When invalid value is passed to age
  Age:a
  Invalid value
  #When 0 is passed for Age
  Age:0
  0
  age cannor be 0
  </pre>

* * *
[Top](#table-of-contents)
* * * 

## Classes and Objects

* Classes are the templates that can be used to create complex data types called objects that have attributes and behaviour(methods)
* **'class'** keyword is used to create Class.
* Objects are created using <class-name>()
* Class variable - defined outside of any class methods, usually belongs to all instances of a class.
* Instance variable - defined inside methods of class and belongs to only particular instance.

  <pre>
  class Point:
    def move(self):
        print("move")

  def draw(self):
      print("draw")

  pointp = Point()
  pointp.move()
  pointp.draw()
  </pre>

  *Output*:
  <pre>
  move
  draw
  </pre>

* **Constructor** can be used to initialize an object when they are instantiated.
  
  <pre>
  class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
        
    def move(self):
        print("move")
        
    def draw(self):
        print("draw")
        
  pointp = Point(10, 20)
  print(pointp.x)
  print(pointp.y)
  </pre>

  *Output*:
  <pre>
  10
  20
  </pre>

  <pre>
  class Person:
    def __init__(self, name):
        self.name = name
        
    def talk(self):
        print("talking " + self.name )
        
    john = Person("John Wick")
    print(john.name)
    john.talk()
  </pre>

  *Output*:
  <pre>
  John Wick
  talking John Wick
  </pre>


* * *
[Top](#table-of-contents)
* * * 

### Inheritence
* Inheritence can be used to inherit the attributes and behaviour(functionality) of another class/object.
* Helps with easy maintenance of Python code.
* Few example scenarios:
  * A dad inheriting from granddad, and grandchild inheriting from dad and grandfather
  * A Cat or Dog inherting from a Mammal class
* Inheriting classes can have their own behavior that is specific to that class.

  <pre>
  class Mammal:
      def walk(self):
          print("walk")
          
  class Dog(Mammal):
      def bark(self):
          print("bow bow")
      
  class Cat(Mammal):
      def meow(self):
          print("meow meow")
      

  dog1 = Dog()
  dog1.walk()
  dog1.bark()

  cat1 = Cat()
  cat1.walk()
  cat1.meow()
  </pre>

  *Output*:
  <pre>
  walk
  bow bow
  walk
  meow meow
  </pre>

* Another Example:
  <pre>
  #!/usr/bin/python3

  class Parent:        # define parent class
    parentAttr = 100
    def __init__(self):
        print ("Calling parent constructor")

    def parentMethod(self):
        print ('Calling parent method')

    def setAttr(self, attr):
        Parent.parentAttr = attr

    def getAttr(self):
        print ("Parent attribute :", Parent.parentAttr)

  class Child(Parent): # define child class
    def __init__(self):
        print ("Calling child constructor")

    def childMethod(self):
        print ('Calling child method')

  c = Child()          # instance of child
  c.childMethod()      # child calls its method
  c.parentMethod()     # calls parent's method
  c.setAttr(200)       # again call parent's method
  c.getAttr()          # again call parent's method
  </pre>

  *Output*:
  <pre>
  Calling child constructor
  Calling child method
  Calling parent method
  Parent attribute : 200
  </pre>

* Overriding Methods: You can always override parent class methods.
  
  <pre>
  #!/usr/bin/python3

  class Parent:        # define parent class
    def myMethod(self):
        print ('Calling parent method')

  class Child(Parent): # define child class
    def myMethod(self):
        print ('Calling child method')

  c = Child()          # instance of child
  c.myMethod()         # child calls overridden method
  </pre>

  *Ouput*:
  <pre>
  Calling child method
  </pre>

* Data hiding - An object's attributes may or may not be visible outside the class definition. You need to name attributes with a double underscore prefix, and those attributes then will not be directly visible to outsiders.
  <pre>
  #!/usr/bin/python3

  class JustCounter:
    __secretCount = 0
    
    def count(self):
        self.__secretCount += 1
        print (self.__secretCount)

  counter = JustCounter()
  counter.count()
  counter.count()
  print (counter.__secretCount)
  </pre>

  *Output*:
  <pre>
  1
  2
  Traceback (most recent call last):
    File "test.py", line 12, in <module>
        print counter.__secretCount
  AttributeError: JustCounter instance has no attribute '__secretCount'
  </pre>

  Changing <pre> print (counter.__secretCount) </pre> to <pre> print (counter._JustCounter__secretCount) </pre> will produce output as below -
  <pre>
  1
  2
  2
  </pre>

* * *
[Top](#table-of-contents)
* * * 
  
## Regular Expressions
* A regular expression is a special sequence of characters that helps you match or find other strings or sets of strings, using a specialized syntax held in a pattern.
* Python has a built-in package called re, which can be used to work with Regular Expressions.
* The **re** module raises the exception **re.error** if an error occurs while compiling or using a regular expression.

* Search the string to see if it starts with "The" and ends with "Spain":
  <pre>
  import re

  txt = "The rain in Spain"
  x = re.search("^The.*Spain$", txt)

  if (x):
    print("YES! We have a match!")
  else:
    print("No match")
  </pre>

  *Output*:
  <pre>
  YES! We have a match!
  </pre>

* RegEx Functions
  
  | Function        | Description        | 
  | ------------ |:-------------| 
  | findall      | Returns a list containing all matches |
  | search       | Returns a Match object if there is a match anywhere in the string |
  | split        | Returns a list where the string has been split at each match |
  | sub          | Replaces one or many matches with a string |

* Metacharacters - characters with special meaning
  
  | Character    | Description        | Example  |
  | ------------ |:-------------| :-----|
  | []           | A set of characters | "[a-m]" |
  | \ |	Signals a special sequence (can also be used to escape special characters)	| "\d" |
  | .	| Any character (except newline character)|	"he..o" |
  | ^	| Starts with	| "^hello" |
  | $	| Ends with	| "world$" |
  | *	| Zero or more occurrences | "aix*" |
  | +	| One or more occurrences	| "aix+" |
  | {} |	Exactly the specified number of occurrences	| "al{2}" |
  |	\| |Either or	| "falls\|stays" |
  | () | Capture and group | |

* Special Sequences - \ followed by one of the characters and has a special meaning
  
  | Character    | Description        | Example  |
  | ------------ |:-------------| :-----|
  | \A |	Returns a match if the specified characters are at the beginning of the string |	"\AThe" |
  | \b | Returns a match where the specified characters are at the beginning or at the end of a word |	r"\bain" r"ain\b"	|
  | \B |	Returns a match where the specified characters are present, but NOT at the beginning (or at the end) of a word | r"\Bain" r"ain\B"	|
  | \d | Returns a match where the string contains digits (numbers from 0-9) | "\d"	|
  | \D | Returns a match where the string DOES NOT contain digits	| "\D" |
  | \s | Returns a match where the string contains a white space character | "\s"	|
  | \S | Returns a match where the string DOES NOT contain a white space character |	"\S"	|
  | \w | Returns a match where the string contains any word characters (characters from a to Z, digits from 0-9, and the underscore _ character) |	"\w"	|
  | \W | Returns a match where the string DOES NOT contain any word characters	| "\W"	|
  | \Z | Returns a match if the specified characters are at the end of the string	 | "Spain\Z" |

* Sets - set of characters inside a pair of square brackets [] with a special meaning
  
  | Set    | Description        | 
  | ------------ |:-------------| 
  | [arn]	| Returns a match where one of the specified characters (a, r, or n) are present |	
  | [a-n]	| Returns a match for any lower case character, alphabetically between a and n |
  | [^arn] | Returns a match for any character EXCEPT a, r, and n|
  | [0123] | Returns a match where any of the specified digits (0, 1, 2, or 3) are present	|
  | [0-9] |	Returns a match for any digit between 0 and 9	|
  | [0-5][0-9] |	Returns a match for any two-digit numbers from 00 and 59	|
  | [a-zA-Z] | Returns a match for any character alphabetically between a and z, lower case OR upper case	|
  | [+] |	In sets, +, *, ., |, (), $,{} has no special meaning, so [+] means: return a match for any + character in the string |
  
* **findall()** function returns a list containing all matches.
  
  <pre>
  import re

  txt = "The rain in Spain"
  x = re.findall("ai", txt)
  print(x)
  x = re.findall("India", txt)
  print(x)
  </pre>

  *Output*:
  <pre>
  ['ai', 'ai']
  []
  </pre>

* **search()** function searches the string for a match, and returns a Match object if there is a match.If there is more than one match, only the first occurrence of the match will be returned. If not found, **None** (NoneObject) is returned.
  
  * The Match object has properties and methods used to retrieve information about the search, and the result:
    * **.span()** returns a tuple containing the start-, and end positions of the match.
    * **.string** returns the string passed into the function
    * **.group()** returns the part of the string where there was a match.

    
  ```
  import re

  txt = "The rain in Spain"
  x = re.search("\s", txt)
  print(x)
  print("The first white-space character is located in position:", x.start())
  x = re.search("Portugal", txt)
  print(x)
  ```

  *Output*:
  ```
  <re.Match object; span=(3, 4), match=' '>
  The first white-space character is located in position: 3
  None
  ```

* **split()** function returns a list where the string has been split at each match.
  
  ```
  import re

  txt = "The rain in Spain"
  x = re.split("\s", txt)
  print(x)
  #Split the string only at the first occurrence
  x = re.split("\s", txt, 1)
  print(x)
  ```

  *Output*:
  ```
  ['The', 'rain', 'in', 'Spain']
  ['The', 'rain in Spain']
  ```
* **sub()** function replaces the matches with the text of your choice.
  
  ```
  import re

  txt = "The rain in Spain"
  x = re.sub("\s", "9", txt)
  print(x)
  #Replace the first 2 occurrences
  x = re.sub("\s", "9", txt, 2)
  print(x)
  ```

  *Output*:
  ```
  The9rain9in9Spain
  The9rain9in Spain
  ```


* * *
[Top](#table-of-contents)
* * * 
  
## Modules and Packages

* **Modules** - a file with python code in it.
  * Use '**import**' keyword to import the functions from an another module
    <pre> import module-name </pre>
  * Use '**from**' and '**import**' to import specific functions from an another module.
    <pre> from module-name import function-name </pre>

  * URL - [Python module list](https://docs.python.org/3/py-modindex.html)
  * Python has many useful built in modules that you can import and use in the programs.
  * Built-in modules can be found in External Libraries/Python 3.x.x/python3.x library root
  * External modules can be found in External Libraries/Python 3.x.x/Lib folder.

### PyPI and PIP

* Python Package Index (PyPI) is a repository of software for the Python programming language. You can search for packages and projects that you can reuse.
* URL - [Python Package Index](https://pypi.org/)

* There are many 3rd party external modules that can also be installed to the local machine using pip installer. Such installed modules are placed in to Libraries/Python 3.x.x/Lib/site-packages folder.
  <pre> pip install python-docx </pre>


* **Packages** - set of modules organized in to a categorical segregation.
  * Each package will have "\_\_init\_\_.py" file.
  * Prefix packagename for every import statement or function invocation statements.

Example:
Lets say a package named "ecommerce" has a module named "producs" that has functions such as "add", "delete" etc.

Now to import all the functions from products, you can either:
  <pre> 
  import ecommerce.products 
          
  ecommerce.products.add()
  ecommerce.products.delete()
  </pre>

  Or

  <pre>
  from ecommerce import products

  products.add()
  products.delete()
  </pre>

  Or

  <pre>
  from ecommerce.products import add, delete

  add()
  delete()
  </pre>

* * *
[Top](#table-of-contents)
* * * 

## File Operations (Read/Write Operations)

* To read from or write to a file in python you have to 'open' the file using open() function.
* open() takes 2 arguments. 
  * Target file name.
    * Use target file name if the file is in same directory as python file
    * Use absolute path of the file name if the file is not in same directory as python file.
  * Modes to open.
    * r - to read from the file
    * w - to write to the file
    * a - append to the file
    * r+ - to read from/write to file
* Every file opened to read/write should be closed using close() function.
* It is recommended to find if a file is readable before reading and writeable before writing. 
* Use try/except blocks as a general practice to catch exceptions.
  
**Examples - Reading from file**
  *employees.txt - input file to read. This file resides in same directory as app.py*
  <pre>
  karthik, learner, india
  john, teacher, us
  mark, doctor, uk
  </pre>

* **read()** function is used to read entire file in a single go.
  
  *app.py - python program that reads employees.txt file in the same directory*
  <pre>
  employee_file = open("employees.txt", "r")
  if(employee_file.readable()):
      print(employee_file.read())
  employee_file.close()
  </pre>

  *Output*:
  <pre>
  karthik, learner, india
  john, teacher, us
  mark, doctor, uk
  </pre>

* **readline()** function is used to read the file line by line.

  <pre>
  employee_file = open("employees.txt", "r")
  if(employee_file.readable()):
      print(employee_file.readline())
      print(employee_file.readline())
  employee_file.close()
  </pre>

  *Output*:
  <pre>
  karthik, learner, india
  john, teacher, us
  </pre>

* **readlines()** function reads the file an puts the content in to a list.

  <pre>
  employee_file = open("employees.txt", "r")
  if(employee_file.readable()):
      print(employee_file.readlines())
      print(employee_file.readlines()[0])
  employee_file.close()
  </pre>

  *Output*:
  <pre>
  ['karthik, learner, india\n', 'john, teacher, us\n', 'mark, doctor, uk\n']
  karthik, learner, india
  </pre>

* **write()** function is used to write content to the file.
* When 'w' mode is used, python program creates the file if does not exist.
* Write function does not add new line character. This should be handled programmatically.
* Write function can be used to create files with different extensions too, like html file etc.
  
**Examples - Write to File**
  <pre>
  employee_file = open("employees1.txt", "w")
  employee_file.write("de Kock, player, netherlands\n")
  employee_file.close()
  </pre>

  *Output of employee1.txt file*:
  <pre>
  de Kock, player, netherlands
  </pre>

**Examples - Append to File**

  * While appending to a file, you should be careful to rerun when needed as the data will being appended will duplicate.

  <pre>
  employee_file = open("employees.txt", "a")
  employee_file.write("knox, manager, france\n")
  employee_file.close()
  </pre>

  *Output of employee.txt file*:
  <pre>
  karthik, learner, india
  john, teacher, us
  mark, doctor, uk
  knox, manager, france
  </pre>

* * *
[Top](#table-of-contents)
* * * 

## Working with Directories 

* pathlib module can be used to work with directories (browse, create, delete etc). 

*Example - verify if a directory named 'education' exists*
<pre>
from pathlib import Path

path = Path("education")       #no args points to current directory
print(path.exists())
</pre>

*Output  -> if eduction directory exists*:
<pre>
True
</pre>

*Output  -> if eduction directory does not exist*:
<pre>
False
</pre>

*Example - creates a directory*
<pre>
from pathlib import Path

path = Path("schools")
print(path.mkdir())
</pre>

*Example - removes a directory*
<pre>
from pathlib import Path

path = Path("schools")
print(path.rmdir())
</pre>

*Example - file listing*
<pre>
from pathlib import Path

path = Path()
for file in path.glob('*'):
    print(file)
</pre>


<pre>
* - lists all files from all directories within the current directory
*.* - lists all files from current directory
</pre>

* * *
[Top](#table-of-contents)
* * * 

## Date & Time
* Python's time and calendar modules help track dates and times.
* **time** module available in Python which provides functions for working with times, and for converting between representations.
* The function time.time() returns the current system time in ticks since 12:00am, January 1, 1970(epoch).

  <pre>
  #!/usr/bin/python3
  import time;  # This is required to include time module.

  ticks = time.time()
  print("Number of ticks since 12:00am, January 1, 1970:", ticks)
  </pre>  

  *Output*:
  <pre>
  Number of ticks since 12:00am, January 1, 1970: 1579020431.6248808
  </pre>

* Many of Python's time functions handle time as a tuple of 9 numbers, as shown below −
  
  | Index        | Field        | Values  |
  | ------------ |:-------------| :-----|
  | 0            | 4-digit year | 2008    | 
  | 1            | Month        | 1 to 12 |
  | 2            | Day          | 1 to 31 |
  | 3            | Hour         | 0 to 23 |
  | 4            | Minute       | 0 to 59 |
  | 5            | Second       | 0 to 61(60 or 61 are leap-seconds)|
  | 6            | Day of Week  | 0 to 6 (0 is Monday) |
  | 7            | Day of Year  | 1 to 366 (Julian day) |
  | 8            | Daylight Savings | -1, 0, 1, -1 means library determines DST |
  
* Getting current time:
  To translate a time instant from seconds since the epoch floating-point value into a timetuple, pass the floating-point value to a function (e.g., localtime) that returns a time-tuple with all valid nine items.
  <pre>
  #!/usr/bin/python3
  import time

  localtime = time.localtime(time.time())
  print ("Local current time :", localtime)
  </pre>

  *Output*:
  <pre>
  Local current time : time.struct_time(tm_year=2020, tm_mon=1, tm_mday=14, tm_hour=22, tm_min=40, tm_sec=58, tm_wday=1, tm_yday=14, tm_isdst=0)
  </pre>

* Getting formatted time:
  Simple method to get time in a readable format is asctime()

  <pre>
  #!/usr/bin/python3
  import time

  localtime = time.asctime( time.localtime(time.time()) )
  print ("Local current time :", localtime)
  </pre>

  *Output*:
  <pre>
  Local current time : Tue Jan 14 22:45:51 2020
  </pre>

  * Getting calendar for a month
  <pre>
  #!/usr/bin/python3
  import calendar

  cal = calendar.month(2020, 1)
  print ("Here is the calendar:")
  print (cal)
  </pre>

  *Output*:
  <pre>
  Here is the calendar:
      January 2020
  Mo Tu We Th Fr Sa Su
        1  2  3  4  5
  6  7  8  9 10 11 12
  13 14 15 16 17 18 19
  20 21 22 23 24 25 26
  27 28 29 30 31
  </pre>

* Few **time** module functions:
  <pre>
  time.asctime([tupletime]) ➤ Accepts a time-tuple and returns a readable 24-character string such as 'Tue Dec 11 18:07:14 2008'. <br>

  time.clock( ) ➤ Returns the current CPU time as a floating-point number of seconds.<br>

  time.sleep(secs) ➤ Suspends the calling thread for secs seconds.<br>

  time.strptime(str,fmt = '%a %b %d %H:%M:%S %Y') ➤ Parses str according to format string fmt and returns the instant in time-tuple format.<br>

  time.time( ) ➤ Returns the current time instant, a floating-point number of seconds since the epoch
  </pre>
* Few **calendar** module functions:
  <pre>
  calendar.calendar(year,w = 2,l = 1,c = 6) ➤ Returns a multiline string with a calendar for year year formatted into three columns separated by c spaces. w is the width in characters of each date; each line has length 21*w+18+2*c. l is the number of lines for each week.<br>

  calendar.firstweekday( ) ➤ Returns the current setting for the weekday that starts each week. By default, when calendar is first imported, this is 0, meaning Monday.

  calendar.isleap(year) ➤ Returns True if year is a leap year; otherwise, False.

  calendar.month(year,month,w = 2,l = 1) ➤ Returns a multiline string with a calendar for month month of year year, one line per week plus two header lines. w is the width in characters of each date; each line has length 7*w+6. l is the number of lines for each week.

  calendar.setfirstweekday(weekday) ➤ Sets the first day of each week to weekday code weekday. Weekday codes are 0 (Monday) to 6 (Sunday).

  calendar.weekday(year,month,day) ➤ Returns the weekday code for the given date. Weekday codes are 0 (Monday) to 6 (Sunday); month numbers are 1 (January) to 12 (December).
 
  </pre>


* * *
[Top](#table-of-contents)
* * * 

## How you code matters

* Different ways of coding a greatest common divisor with each following approach reducing the number of loops or spaces.
  
  *Approach-1 with lists and multiple loops*
  <pre>
    def gcd(a, b):

      #Find all factors of a
      fa = []
      for i in range(1, a+1):
          if(a % i)==0:
              fa.append(i)
      print(fa)

      #Find all factors of b
      fb = []
      for j in range(1, b+1):
          if(b % j)==0:
              fb.append(j)
      print(fb)

      #Find the common value in both fa and fb
      global val
      for k in fa:
          if k in fb:
              val = k
      return val

      gcd(10, 18)
  </pre>

  *Approach-2 without lists looping only once*
  <pre>
    def gcd(a, b):
      global val
      for i in range(1, min(a, b) + 1):
          if ((a % i)==0 and (b % i)==0):
              val = i
      return val
              
    gcd(10, 18)
  </pre>

  *Approach-3 uses [Euclid's algorithm](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/the-euclidean-algorithm)
  <pre>
  def gcd(x, y): 
    while(y): 
       x, y = y, x % y 
    return x 
    
  print (gcd(10,18)) 
  </pre>
  
  *Approach-4 using math function
  <pre>
  import math
  print(math.gcd(10,18))
  </pre>
  
* * *
[Top](#table-of-contents)
* * * 
