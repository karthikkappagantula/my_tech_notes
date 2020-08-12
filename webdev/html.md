# Table of Contents
- [Table of Contents](#table-of-contents)
- [Code Editors](#code-editors)
- [What is HTML](#what-is-html)
- [Important tags](#important-tags)
- [Inline vs Block Level Elements](#inline-vs-block-level-elements)
- [Headings](#headings)
- [Paragraph](#paragraph)
- [Text formatting](#text-formatting)
- [Div/Span tags](#divspan-tags)
- [Attributes](#attributes)
- [Image tag](#image-tag)
- [Anchor tag](#anchor-tag)
  
# Code Editors
* VS Code
* SublimeText
* Notepad++

# What is HTML
* HyperText Markup Language
* Content - What You See
* Not a Programming language
* It is a Markup Language

# Important tags
* ```<!DOCTYPE html>```
  Tells the browser what html version is used.
* ```<html> ... </html>```
  Main content for html page
  * ```<head>...</head>```
    Contains meta data or information about the page
    * ```<meta>``` - meta data used by SEO
    * ```<title>...</title>``` - title of the page
  * ```<body>...</body>```
    Content front end users view

# Inline vs Block Level Elements

* Inline 
  * Do not start a new line
  * Only take needed width
  * ```<span>, <img>, <a>```
* Block 
  * Starts a new line
  * Take full width available
  * ```<h1> to <h6>, <p>```

# Headings

* ```<h1>...</h1>```
* ```<h2>...</h2>```
* ```<h3>...</h3>```
* ```<h4>...</h4>```
* ```<h5>...</h5>```
* ```<h6>...</h6>```
  
# Paragraph

* ```<p>...</p>```
* adds a paragraph as block.
* any line breaks can be done using ```<br>```

# Text formatting

* ```<strong>...</strong>``` - bold
* ```<em>...</em>``` - italic
* ```<mark>...</mark>``` - highlights
* ```<small>...</small>``` - appears as small
* ```<del>...</del>``` - strikethrough
* ```<ins>...</ins>``` - underline
* ```<sub>...</sub>``` - subscript
* ```<sup>...</sup>``` - superscript
* ```<hr>``` - horizontal line

# Div/Span tags

* helps in separating the content in to sections
* a block level tag

# Attributes

* Provides additional information about HTML elements
* Declared on opening tag
* Key-Value pairs
* Value should be wrapped in double quotes.

# Image tag

* Self-closing tag used to add images to HTML pages.
* src tag provide information of the image file name.
* alt tag provide alternative description for screen readers.
* width determines the image width on the page.

Example:

```<img src="filename.jpg" alt="description of image" width="400">```

# Anchor tag

* used to add hyperlinks to HTML pages to other pages or pages on internet.
* href attribute is the destination page.
* target attribute will allow you to open new window when the URL is clicked.

Example:

```<a href="https://www.google.com" target="_blank"> Google </a>```
