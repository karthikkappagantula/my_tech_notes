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
    - [Destructuring](#destructuring)
    - [Reference and Primitive Types](#reference-and-primitive-types)
    - [Array Functions](#array-functions)
  - [React Core Concepts](#react-core-concepts)
    - [Setting local build workflow](#setting-local-build-workflow)
      - [Directory/File details -](#directoryfile-details--)
      - [Uderstanding JSX](#uderstanding-jsx)
        - [Embedding Expressions in JSX](#embedding-expressions-in-jsx)
        - [Specifying Attributes with JSX](#specifying-attributes-with-jsx)
        - [Specifying Children with JSX](#specifying-children-with-jsx)
        - [JSX Prevents Injection Attacks](#jsx-prevents-injection-attacks)
        - [JSX Represents Objects](#jsx-represents-objects)
        - [JSX Restrictions](#jsx-restrictions)
    - [Creating a Function/Class Component](#creating-a-functionclass-component)
      - [Outputting Dynamic Content](#outputting-dynamic-content)
      - [Props & State](#props--state)
      - [Props](#props)
      - [State](#state)
      - [DOM events that app can listen](#dom-events-that-app-can-listen)

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

* * *
[Top](#table-of-contents)
* * * 
  
## Javascript refresher for React

### let and const
	
* Use let and const instead of var.<br>
* Use let for variables values.<br>
* Use const for constant values.<br>
	
### Arrow Functions

Regular function -

```JSX
function myFnc() {
…
…
}
```

Arrow function -
```JSX
const myFnc = () => {
…
…
}
```

* No more issues with the 'this' keyword.<br>
* Arrow Functions maintain the context.

Details about Syntax - 

let/const <name> = (arg1, arg2, … ) { <function-body> }

* Use let if you would use the same variable used for function elsewhere, otherwise use const
* Function body is wrapped around curly braces { }.
* Arguments are wrapped around round braces ( ).
  * If no args, just use ()
    ```JSX
    let myFnc = () => { 
    …
    }
    ```
  * If only one arg, braces can be removed.
  * If the function body only returns some value but does not contain any other statements, you can remove curly braces and return keyword


### Exports & Imports (Modules)
	 
* Allows for modular programming so that we can reuse other modules 
* Imports default and ONLY export of the file Name in the receiving file is uo to you

Example:
*person.js*
```JSX
const person = {
	name: 'Max'
}

export default person;                         //default export
```
*utility.js*
```JSX
export const clean = () => { ….};              //named export
export const baseDate = 10;
```

*app.js*
```JSX
import person from './person.js'              //imports default element exported elsewhere and you can use any file name while importing
import prs from './person.js'

import { baseData } from './utility.js'       //imports individual elements exported elsewhere without default.
import { clean } from './utility.js'
```

### Classes

* Create blueprints for javascript objects with properties and methods(functions).
* Instantiated using 'new' keyword using constructor function.
* Supports inheritance.

Example:
```JSX
class Person {
	constructor() {
		this.name = 'Karthik';
	}
	
	printMyName() {
		console.log(this.name);
	}

const person = new Person();
person.printMyName();
```

* Properties ==>  "variables attached to classes/objects".

ES6 way - 
```JSX
constructor() {
    this.myProperty = 'value'
}
```

ES7 way - 
```JSX
myProperty = 'value'
```	

* Methods ==> "functions  attached to classes/objects"

ES6 way - 
```JSX 
myMethod() { …… } 
```
	
ES7 way - Arrow function like a property value
```JSX
myMethod = () => { … }
```
	
### Spread & Rest Operators
Operator is three dots (…) changes based on usage and context.

* Spread --> used to split up array elements OR object properties (creates new objects)
```JSX
const newArray = […oldArray, 1, 2]
const newObject = {…oldObject, newProp:5}
```

Example:
```JSX
const numbers = [1, 2, 3];
const newNumbers1 = [numbers, 4];
const newNumbers2 = […numbers, 4];
const person = {
  name: 'Max'
};
const newperson = {
  ...person,
  age:29
}

console.log(newNumbers1);      //Output = [[1, 2, 3], 4]
console.log(newNumbers2);      //Output = [1, 2, 3, 4]
console.log(newPerson);        //Outputs new object with both age and name
```
	
* Rest --> used to merge a list of function arguments into an array
```JSX
function sortArgs(…args) {
    return args.sort()
}
```

Examples:
```JSX
const filter = (...args) => {
  return args.filter(el => el === 1);
}

console.log(filter(1, 2, 3));   //Outputs [1]
```

### Destructuring
Allows to easily extract array elements or objects properties and store them as varaibles.
* Array Destructuring

Examples:
  ```JSX
    [a, b] = ['Hello', 'Max'];
    console.log(a);   //Outputs 'Hello'
    console.log(b);   //Outputs 'Max'
  ```

  ```JSX
    const numbers = [1, 2, 3];
    [num1, num2] = numbers;
    //[num1, , num3] = numbers; // Should leave out the non referenced element as blank
    console.log(num1, num2);    // Outputs 1 and 2
    //console.log(num1, num3);  // Outputs 1 and 3
  ```

* Object Destructuring
  ```JSX
    {name} = {name:'Max', age:28};
    console.log(name);   //Outputs 'Max'
    console.log(age);    //Ouputs undefined - as no variable is defined for age
  ```

### Reference and Primitive Types
* Objects and Arrays are Reference types. 
* Strings, numbers etc are Primitive types.

* * *
[Top](#table-of-contents)
* * * 
  
### Array Functions

[Array Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

**Particularly important are:**

[map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

[find()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

[findIndex()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

[filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

[reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce?v=b)

[concat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat?v=b)

[slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

[splice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

* * *
[Top](#table-of-contents)
* * * 
  
## React Core Concepts

### Setting local build workflow

* Why?
  * Optimize code
  * Use Next-gen Javascript features
  * Be more productive

* How?
  * Use dependency management tool such as npm or yarn
  * Use bundler such as Webpack
  * Use compiler (next-gen javascript) such as Babel + Presets
  * Use a Development Server

Setting up local for React app, you can either use -
* [facebook community](https://github.com/facebook/create-react-app)
* Setup everything for react from Scratch

#### Directory/File details - 

Directories/Files on root-level
* package.json
  * Dependencies required for the project.
  * Scripts for npm commands.

* node_modules
All dependency modules required for react application.

* public folder contains index.html file where we have the div tag for "root" (module for react app). Usually required to be edited if we are building multi-page app or to import any libraries.

* src folder has all the files we will edit and work on. React application files we work on.
  * index.js - has the access to root id from index.html to render react app.
  React app entry point - 
  ```JSX
  ReactDOM.render(<App />, document.getElementById('root'));
  ```
  * App.js - react components. 
    * App class having render() method.  
    * App class is default exported which is imported in index.js
    * Returns JSX code
  * App.css - css file for React app.
  * App.test.js - unit test for React components.
  
* * *
[Top](#table-of-contents)
* * * 


#### Uderstanding JSX
* JSX is syntax extention to JavaScript
* It is recommended way to desscribe what the UI should look like.
* React instead of seperating technologies by putting markup and logic in seperate files, seperates concerns with loosely couped units called "components"
* React does not require JSX, but most people find it helpful as a visual aid when working with UI inside the Javascript code. 
* It allows React to show more useful error and warning messages.

Example:
  ```JSX
  const element = <h1>Hello, world!</h1>;
  ```

##### Embedding Expressions in JSX

* You can put Javascript expression inside the curly braces in JSX. Example: 2 + 2, user.firstName, or formatName(user) are all valid JSX.
  ```JSX
  function formatName(user) {
    return user.firstName + ' ' + user.lastName;
  }

  const user = {
    firstName: 'Harper',
    lastName: 'Perez'
  };

  const element = (
    <h1>
      Hello, {formatName(user)}!
    </h1>
  );

  ReactDOM.render(
    element,
    document.getElementById('root')
  );
  ```
* After compilation, JSX becomes regular JavaScript function calls and evaluate to JavaScript objects.
* You can use JSX inside conditions and loops, assign it to variables, accept it as arguments and return it from frunctions.
  ```JSX
  function getGreeting(user) {
    if (user) {
      return <h1>Hello, {formatName(user)}!</h1>;
    }
    return <h1>Hello, Stranger.</h1>;
  }
  ```
##### Specifying Attributes with JSX

* Either use quotes or curly braces to embed a JSX in an attribute.
  ```JSX
  const element = <div tabIndex="0"></div>;
  ```

  or
  ```JSX
  const element = <img src={user.avatarUrl}></img>;
  ```

* JSX is closer to JavaScript than to HTML, React DOM uses camelCase property naming convention instead of HTML attribute names.

For example, class becomes className in JSX, and tabindex becomes tabIndex.

##### Specifying Children with JSX

JSX tags may contain childres 
  ```JSX
  const element = (
    <div>
      <h1>Hello!</h1>
      <h2>Good to see you here.</h2>
    </div>
  );
  ```
##### JSX Prevents Injection Attacks

* It is safe to embed user input in JSX
  ```JSX
      const title = response.potentiallyMaliciousInput;
      // This is safe:
      const element = <h1>{title}</h1>;
  ```  
* React DOM escapes any values embdedded in JSX before rendering them. This ensures that you can never inject anything that's not explicitly written in your application.

##### JSX Represents Objects

* Babel compiles JSX down to 
  ```JSX
  React.createElement() 
  ```

Both the below two examples are identical:
  ```JSX
      const element = (
        <h1 className="greeting">
          Hello, world!
        </h1>
      );

      const element = React.createElement(
        'h1',
        {className: 'greeting'},
        'Hello, world!'
      );
  ```
* React.createElement() performs a few checks to help you write bug-free code but essentially it creates an object like this:
  ```JSX
      // Note: this structure is simplified
      const element = {
        type: 'h1',
        props: {
          className: 'greeting',
          children: 'Hello, world!'
        }
      };
  ```
* These objects are called “React elements”. You can think of them as descriptions of what you want to see on the screen. React reads these objects and uses them to construct the DOM and keep it up to date.

##### JSX Restrictions
* Use className instead of class.
* Can only have one root element.

* * *
[Top](#table-of-contents)
* * * 
### Creating a Function/Class Component
* Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. 
* A typical React app therefore could be depicted as a component tree - having one root component ("App") and then an potentially infinite amount of nested child components.
* Each component needs to return/ render some JSX code - it defines which HTML code React should render to the real DOM in the end.
* The simplest way to define a component is to write a JavaScript function:
  ```JSX
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  }
  ```
We call such components “function components” because they are literally JavaScript functions.
* You can define class component:
  ```JSX
  class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
   }
  }
  ```
* The above two components are equivalent from React’s point of view.

* JSX is just syntactic sugar for JavaScript, allowing you to write HTMLish code instead of nested React.createElement(...) calls.
* When creating components, you have the choice between two different ways:
  1. Functional components (also referred to as "presentational", "dumb" or "stateless" components 
  ```JSX
  const cmp = () => { return <div>some JSX</div> }
  ``` 
  (using ES6 arrow functions as shown here is recommended but optional)

   2. class-based components (also referred to as "containers", "smart" or "stateful" components) 
  ```JSX 
  class Cmp extends Component { render () { return <div>some JSX</div> } } 
  ```

#### Outputting Dynamic Content
* Wrap the dynamic content portion (function/methods) in single curly braces in the JSX.
      import React from 'react';
  ```JSX
  const person = () => {
      return <p>I'm a Person! and I am {Math.floor(Math.random()*30)} years old</p>
  }

  export default person;
  ```

* * *
[Top](#table-of-contents)
* * * 
#### Props & State

* ```props``` and ```state``` are CORE concepts of React.
* Actually, only changes in props  and/ or state  trigger React to re-render your components and potentially update the DOM in the browser

#### Props

* ```props```  allow you to pass data from a parent (wrapping) component to a child (embedded) component.


Example:
*app.js*
```JSX
import React, { Component } from 'react';
import Person from './Person/Person'
import './App.css';

class App extends Component {

  render() {
    return (
      <div className="App">
        <h1>Hi, I'm a React App</h1>
        <Person name="Eeshan" age="4"> My Hobbies: Acting </Person>
      </div>
    );
    // return React.createElement('div', {className: 'App'}, React.createElement('h1', null, 'Hi, I\'m a Reach App!!'));
  }
}

export default App;
```
*person.js*
```JSX
import React from 'react';

const person = (props) => {
    return (
        <div>
            <p>I'm {props.name} and I am {props.age} years old</p>
            <p>{props.children}</p>
        </div>
    )
}
export default person;
```
* Whatever you mention after opening tag of the function component in app.js will/can be exported to and imported in to function(child) component as arguments(*props*).

  ```<Person .../>```
* In above example props.name and props.age are values passed from App.js to Person.js.
  
*Name of the receiving argument can be anything. props can be a just plain x.*

* Anything you mention between the opening and closing tags can be accessed as children (*props.children*)
* In above example 'My Hobbies: Acting' from App.js can be accessed in Person.js using props.children.

#### State

* Whilst props allow you to pass data down the component tree (and hence trigger an UI update), state is used to change the component, well, state from within. Changes to state also trigger an UI update.

Example:
*NewPost.js*
```JSX
class NewPost extends Component { // state can only be accessed in class-based components!
    state = {
        counter: 1
    };  
 
    render () { // Needs to be implemented in class-based components! Needs to return some JSX!
        return (
            <div>{this.state.counter}</div>
        );
    }
}
```
Here, the ```NewPost```  component contains ```state``` . Only class-based components can define and use ```state``` . You can of course pass the ```state```  down to functional components, but these then can't directly edit it.

```state```  simply is a property of the component class, you have to call it ```state```  though - the name is not optional. You can then access it via ```this.state```  in your class JSX code (which you return in the required ```render()```  method).

Whenever ```state```  changes (taught over the next lectures), the component will re-render and reflect the new state. The difference to ```props```  is, that this happens within one and the same component - you don't receive new data (```props```) from outside!

* Change state only using setState React function but not directly using assignment operator.
```JSX
switchNameHandler = () => {
    // console.log('Was Clicked!');
    // DON'T DO THIS -> this.state.persons[0].name = 'Kappagantula';
    this.setState({persons: [ 
      { name: 'laddu', age: 36},
      { name: 'pandu', age: 30},
      { name: 'kutlu', age: 4},
      { name: 'kuchku', age: 1},
    ]})
  }

```

* * *
[Top](#table-of-contents)
* * * 
#### DOM events that app can listen

You can find a list of supported events [here] (https://reactjs.org/docs/events.html#supported-events)

1. **Clipboard Events**

Event names:

```onCopy``` ```onCut``` ```onPaste```

Properties:

```DOMDataTransfer clipboardData```

2. **Composition Events**

Event names:

```onCompositionEnd onCompositionStart onCompositionUpdate```

Properties:

```string data```

3. **Keyboard Events**

Event names:

```onKeyDown onKeyPress onKeyUp```

Properties:

```
boolean altKey
number charCode
boolean ctrlKey
boolean getModifierState(key)
string key
number keyCode
string locale
number location
boolean metaKey
boolean repeat
boolean shiftKey
number which 
```

4. **Focus Events**

Event names:

```onFocus onBlur```

These focus events work on all elements in the React DOM, not just form elements.

Properties:

```DOMEventTarget relatedTarget```

5.**Form Events**

Event names:

```onChange onInput onInvalid onSubmit```


For more information about the onChange event, see Forms.

6. **Mouse Events**

Event names:

```onClick onContextMenu onDoubleClick onDrag onDragEnd onDragEnter onDragExit```
```onDragLeave onDragOver onDragStart onDrop onMouseDown onMouseEnter onMouseLeave```
```onMouseMove onMouseOut onMouseOver onMouseUp```

The onMouseEnter and onMouseLeave events propagate from the element being left to the one being entered instead of ordinary bubbling and do not have a capture phase.

Properties:

```
boolean altKey
number button
number buttons
number clientX
number clientY
boolean ctrlKey
boolean getModifierState(key)
boolean metaKey
number pageX
number pageY
DOMEventTarget relatedTarget
number screenX
number screenY
boolean shiftKey
```

7.**Selection Events**

Event names:

```onSelect```

8.**Touch Events**

Event names:

```onTouchCancel onTouchEnd onTouchMove onTouchStart```

Properties:

```
boolean altKey
DOMTouchList changedTouches
boolean ctrlKey
boolean getModifierState(key)
boolean metaKey
boolean shiftKey
DOMTouchList targetTouches
DOMTouchList touches
```

9. **UI Events**

Event names:

```onScroll```

Properties:
```
number detail
DOMAbstractView view
```

10.**Wheel Events**

Event names:

```onWheel```

Properties:
```
number deltaMode
number deltaX
number deltaY
number deltaZ
```

11.**Media Events**

Event names:
```onAbort onCanPlay onCanPlayThrough onDurationChange onEmptied onEncrypted```
```onEnded onError onLoadedData onLoadedMetadata onLoadStart onPause onPlay```
```onPlaying onProgress onRateChange onSeeked onSeeking onStalled onSuspend```
```onTimeUpdate onVolumeChange onWaiting```

12.**Image Events**

Event names:

```onLoad onError```

13.**Animation Events**

Event names:

```onAnimationStart onAnimationEnd onAnimationIteration```

Properties:
```
string animationName
string pseudoElement
float elapsedTime
```

14.**Transition Events**

Event names:

```onTransitionEnd```

Properties:
```
string propertyName
string pseudoElement
float elapsedTime
```

15.**Other Events**

Event names:
```onToggle```

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 

* * *
[Top](#table-of-contents)
* * * 
