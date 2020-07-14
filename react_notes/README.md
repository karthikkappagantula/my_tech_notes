# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Important URLs](#important-urls)
  - [Intro to React](#intro-to-react)
    - [React Alternatives:](#react-alternatives)
    - [SPA vs MPA - Two kinds of applications -](#spa-vs-mpa---two-kinds-of-applications--)
  - [Javascript refresher for React](#javascript-refresher-for-react)
    - [let and const](#let-and-const)
    - [Arrow Functions](#arrow-functions)
    - [Exports & Imports (Modules)](#exports--imports-modules)
    - [Classes](#classes)
    - [Spread & Rest Operators](#spread--rest-operators)

## Important URLs
[React Offical Page](https://reactjs.org/)
* * *
[Top](#table-of-contents)
* * * 
## Intro to React
* Popular JavaScript Library for building User Interfaces (using components)
* Run in the browser, not on Server

Way forward -
* Build using manageable components (header, sidebar, navigation cards, footer)

Why React - 
* UI Statement management is taken care by React
* Focus on Business logic
* Active community
* High performance

### React Alternatives:
* Angular
* Vue.js

### SPA vs MPA - Two kinds of applications - 
* Single Page Application (SPA)
  * One HTML page, content is (re)rendered on Client
* Multi Page Application (MPA)
  * Multiple HTML pages, Content is rendered on Server

## Javascript refresher for React

### let and const
	
* Use let and const instead of var.<br>
* Use let for variables values.<br>
* Use const for constant values.<br>
	
### Arrow Functions

Regular function -

<pre>
function myFnc() {
…
…
}
</pre>

Arrow function -
<pre>
const myFnc = () => {
…
…
}
</pre>

* No more issues with the 'this' keyword.<br>
* Arrow Functions maintain the context.

Details about Syntax - 

let/const <name> = (arg1, arg2, … ) { <function-body> }

* Use let if you would use the same variable used for function elsewhere, otherwise use const
* Function body is wrapped around curly braces { }.
* Arguments are wrapped around round braces ( ).
  * If no args, just use ()
    <pre>
    let myFnc = () => { 
    …
    }
    </pre>
  * If only one arg, braces can be removed.
  * If the function body only returns some value but does not contain any other statements, you can remove curly braces and return keyword


### Exports & Imports (Modules)
	 
* Allows for modular programming so that we can reuse other modules 
* Imports default and ONLY export of the file Name in the receiving file is uo to you

Example:
*person.js*
<pre>
const person = {
	name: 'Max'
}

export default person;                         //default export
</pre>
*utility.js*
<pre>
export const clean = () => { ….};              //named export
export const baseDate = 10;
</pre>

*app.js*
<pre>
import person from './person.js'              //imports default element exported elsewhere and you can use any file name while importing
import prs from './person.js'

import { baseData } from './utility.js'       //imports individual elements exported elsewhere without default.
import { clean } from './utility.js'
</pre>

### Classes

* Create blueprints for javascript objects with properties and methods(functions).
* Instantiated using 'new' keyword using constructor function.
* Supports inheritance.

Example:
<pre>
class Person {
	constructor() {
		this.name = 'Karthik';
	}
	
	printMyName() {
		console.log(this.name);
	}

const person = new Person();
person.printMyName();
</pre>

* Properties ==>  "variables attached to classes/objects".

ES6 way - 
<pre>
constructor() {
    this.myProperty = 'value'
}
</pre>

ES7 way - 
<pre>
myProperty = 'value'
</pre>	

* Methods ==> "functions  attached to classes/objects"

ES6 way - 
<pre> myMethod() { …… } </pre>
	
ES7 way - Arrow function like a property value
<pre>myMethod = () => { … }</pre>
	
### Spread & Rest Operators
Operator is three dots (…) changes based on usage and context.

* Spread --> used to split up array elements OR object properties
<pre>
const newArray = […oldArray, 1, 2]
const newObject = {…oldObject, newProp:5}
</pre>

Example:
<pre>
const numbers = [1, 2, 3];
const newNumbers1 = [numbers, 4];
const newNumbers2 = […numbers, 4];

console.log(newNumbers1);      //Output = [[1, 2, 3], 4]
console.log(newNumbers2);      //Output = [1, 2, 3, 4]
</pre>
	
* Rest --> used to merge a list of function arguments into an array
<pre>
function sortArgs(…args) {
    return args.sort()
}
</pre>



