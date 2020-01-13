# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Important URLs](#important-urls)
  - [Install Anaconda](#install-anaconda)
  - [Jupyter Intro](#jupyter-intro)
  - [Keywords](#keywords)
  - [Arithmetic Operations](#arithmetic-operations)
  - [Math Functions](#math-functions)
  - [print output](#print-output)
    - [format output](#format-output)
  - [Taking Inputs](#taking-inputs)
  - [Strings](#strings)
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
  - [Modules and Packages](#modules-and-packages)
    - [PyPI and PIP](#pypi-and-pip)
  - [File Operations (Read/Write Operations)](#file-operations-readwrite-operations)
  - [Working with Directories](#working-with-directories)

## Important URLs
[Python Standard Libraries](https://docs.python.org/3/library/)
[Python Math Module](https://docs.python.org/3/library/math.html)
[Python Module Index](https://docs.python.org/3/py-modindex.html)
[Python Package Index](https://pypi.org/)
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
## Arithmetic Operations

  Examples:
  <pre>
  print(5 + 3)  # Addition
  print(5 * 3)  # Multiplication
  print(5 - 3)  # Subtraction
  print(5 / 3)  # Division returns quotient in whole/fraction
  print(5 // 3) # Division returns quotient in whole only
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

* Use(import) Math module for complex mathematical functions. 
  
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

## print output
* Python has a predefined format if you use print(a_variable) then it will go to next line automatically.

  <pre>
  Syntax: print(value(s), sep= ‘ ‘, end = ‘\n’, file=file, flush=flush)

    Parameters:
    value(s) : Any value, and as many as you like. Will be converted to string before printed
    sep=’separator’ : (Optional) Specify how to separate the objects, if there is more than one.Default :’ ‘
    end=’end’: (Optional) Specify what to print at the end.Default : ‘\n’
    file : (Optional) An object with a write method. Default :sys.stdout
    flush : (Optional) A Boolean, specifying if the output is flushed (True) or buffered (False). Default: False
  </pre>

  **Examples**

  <pre>
    # Python 3.x program showing 
    # how to print data on 
    # a screen 
      
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

### format output

* **Formatting output using String modulo operator(%)** :

  The % operator can also be used for string formatting. It interprets the left argument much like a printf()-style format string to be applied to the right argument. 

  <pre>
    # Python program showing how to use 
    # string modulo operator(%) to print 
    # fancier output 
      
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
    # Python program to  
    # show format () is  
    # used in dictionary 
      
    tab = {'geeks': 4127, 'for': 4098, 'geek': 8637678} 
      
    # using format() in dictionary 
    print('Geeks: {0[geeks]:d}; For: {0[for]:d}; '
        'Geeks: {0[geek]:d}'.format(tab)) 
      
    data = dict(fun ="GeeksForGeeks", adj ="Portal") 
      
    # using format() in dictionary 
    print("I love {fun} computer {adj}".format(**data)) 
  </pre>

  *Output*:
  <pre>
    Geeks: 4127; For: 4098; Geeks: 8637678
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
    # Python program to 
    # format a output using 
    # string() method 
      
    cstr = "I love geeksforgeeks"
        
    # Printing the center aligned   
    # string with fillchr  
    print ("Center aligned string with fillchr: ")  
    print (cstr.center(40, '#'))  
      
    # Printing the left aligned   
    # string with "-" padding   
    print ("The left aligned string is : ")  
    print (lstr.ljust(40, '-')) 
      
    # Printing the right aligned string  
    # with "-" padding   
    print ("The right aligned string is : ")  
    print (rstr.rjust(40, '-')) 
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
* raw_input ( prompt )  --> works only in python 2.x
  <pre>
    # Python program showing  
    # a use of raw_input() 
      
    g = raw_input("Enter your name : ") 
    print g 
  </pre>

* input ( prompt )  --> works in python 3.x
  <pre>
    # Python program showing  
    # a use of input() 
      
    val = input("Enter your value: ") 
    print(val) 
  </pre>

    Whatever you enter as input, input function convert it into a string. if you enter an integer value still input() function convert it into a string. You need to explicitly convert it into an integer in your code using typecasting.

  <pre>
    # Program to check input  
    # type in Python 
      
    num = input ("Enter number :") 
    print(num) 
    name1 = input("Enter name : ") 
    print(name1) 
      
    # Printing type of input value 
    print ("type of number", type(num)) 
    print ("type of name", type(name1)) 
  </pre>

    *Output*:
  <pre>
    Enter number :hello
    hello
    Enter name : there
    there
    type of number <class 'str'>
    type of name <class 'str'>
  </pre>


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
    print(message[0:4]) #prints charcters from index 0 to 4 (excludes character at index=4).
    print(message[:-1]) #prints all characters
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
    message="this is tom's message"    #wrap message with single quotes in double quotes
    print(message)

    message1='this is "python" notes'  #wrap message with double quotes in single quotes
    print(message1)

    message2='this is \"python\" notes with tom\'s message'   #use escape character followed by a quote ( \" or \' ).
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

Example - 1
  <pre>
  #if/elif/else statement
  temp_num = 10
  if temp_num%3 == 0:
      print('Divisible by 3')
  elif temp_num%2 == 0:
      print('Divisible by 2')
  else:
      print('Default')

  *Output: Divisible by 2*
  </pre>
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

