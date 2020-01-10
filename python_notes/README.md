# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Important URLs](#important-urls)
  - [Install Anaconda](#install-anaconda)
  - [Jupyter Intro](#jupyter-intro)
  - [Keywords](#keywords)
  - [print output](#print-output)
    - [format output](#format-output)
  - [Taking Inputs](#taking-inputs)
  - [Strings](#strings)
  - [Conditional Statements - if/elif/else](#conditional-statements---ifelifelse)
  - [For Loops](#for-loops)
  - [Data Structures](#data-structures)
    - [Lists](#lists)
      - [Slicing Lists](#slicing-lists)

## Important URLs
[Python Standard Libraries](https://docs.python.org/3/library/)

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
    #importing "keyword" for keyword operations import keyword 
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
  * \\ -> backslash
  * \' -> single quote
  * \" -> double quote

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
    </pre>

  *Output*: 

    The string without repr() is : 
    I
    Love	Geeksforgeeks

    The string after using repr() is : 
    'I\nLove\tGeeksforgeeks'



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

* * *
[Top](#table-of-contents)
* * * 
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

*Ouput:*
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
  
  ***Example :***
  <pre> 
  list1 = [1, 2, 3, 4, 5] 
  print(list1)
  </pre>
  *Output:*
  <pre>
  [1, 2, 3, 4, 5]
  </pre>


* Lists can have elements of any type (numeric, alphabetic, string)

  ***Example :***
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
 ***Example :***
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
  
#### Slicing Lists

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