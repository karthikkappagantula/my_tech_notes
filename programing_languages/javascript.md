# Table of Contents
- [Table of Contents](#table-of-contents)
- [VS Code shortcuts](#vs-code-shortcuts)
- [Writing js code](#writing-js-code)
  - [Inline js](#inline-js)
  - [External js](#external-js)

# VS Code shortcuts

* cmd + N -> new file
* cmd + B -> close explorer
* for HTML :
  * Type 'doc' and tab for barebones HTML file.

# Writing js code
  
## Inline js

* Use ```<script>...</script>``` tags for inline js code.

Example:
```JSX
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Intro to HTML</h1>
    <p id="demo">In-line JS script</p>
    <script>
        alert('hello there!');                                              //alert window
        document.getElementById("demo").innerHTML = "hello again!";         //modify HTML
    </script>
</body>
</html>
```
## External js

* write js code in a seperate js file and use the ```<script src="">...</script>``` to use it in html file

Example

*index.html*

```JSX
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Intro to HTML</h1>
    <script src="intro_external.js"></script>
</body>
</html>
```

*intro_external.js*

```JSX
document.getElementById("demo").innerHTML = "external hello!";
```

## Comments

* // for single line comments.
* Block of code in between /* and */




* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

* * *
[Top](#table-of-contents-)
* * *

