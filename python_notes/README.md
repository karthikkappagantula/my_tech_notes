# Table of Contents
- [Table of Contents](#table-of-contents)
- [Important URLs](#important-urls)
  - [Install Anaconda ](#install-anaconda)
  - [Jupyter Intro ](#jupyter-intro)
  - [Conditional Statements - if/elif/else ](#conditional-statements---ifelifelse)
  - [For Loops ](#for-loops)
  - [Data Structures](#data-structures)
    - [Lists](#lists)

# Important URLs
[Python Standard Libraries](https://docs.python.org/3/library/)

* * *
[Top](#table-of-contents)
* * * 
## Install Anaconda <a name="#install_anaconda"></a>
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
## Jupyter Intro <a name='jupyter_intro'> </a>
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
## Conditional Statements - if/elif/else <a name='ifelifelse'> </a>
* Indentation is used to determine the scope. 
* elif is nothing but an else if

example - 1
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
## For Loops <a name='forloops'> </a>

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
    *Output:*
    <pre>
    1
    5
    </pre>


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

