# Lesson 0: Introduction to HTML, CSS and Basic Programming: JavaScript


## Installation *(Highly Recommended)*

Using a code editor will greatly ease the learning curve and improve the efficiency of writing code with auto-completeness, syntax colouring, extensions, etc.

Some widely used code editors:
- [Visual Studio](https://code.visualstudio.com/)
- [Atom](https://atom.io/)
- [Sublime Text](https://www.sublimetext.com/)

## HTML - Hyper Text Markup Language

#### What is HTML?

- HTML is the standard markup language for creating Web pages
- HTML describes the structure of a Web page
- HTML consists of a series of elements
- HTML elements tell the browser how to display the content

#### HTML Element

An HTML element is defined by a start tag, some content, and an end tag:
``` <tagname>Content goes here...</tagname> ```

#### HTML code example:

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Page Title</title>
</head>
<body>

    <h1>My First Heading</h1>
    <p>My first paragraph.</p>

</body>
</html>
```

- The ```<!DOCTYPE html>``` declaration defines that this document is an HTML5 document
- The ```<html>``` element is the root element of an HTML page
- The ```<head>``` element contains meta information about the HTML page
- The ```<title>``` element specifies a title for the HTML page (which is shown in the browser's title bar or in the page's tab)
- The ```<body>``` element defines the document's body, and is a container for all the visible contents, such as headings, paragraphs, images, hyperlinks, tables, lists, etc.
- The ```<h1>``` element defines a large heading
- The ```<p>``` element defines a paragraph

#### HTML Attributes

- All HTML elements can have attributes
- Attributes provide additional information about elements
- Attributes are always specified in the start tag
- Attributes usually come in name/value pairs like: name="value"

#### Examples

The ```<a>``` tag defines a hyperlink. The href attribute specifies the URL of the page the link goes to:

``` html
<a href="https://sites.google.com/view/digitaldevs/about-us">This is a link</a>
```   

HTML images are defined with the ```<img>``` tag.
The source file (src), alternative text (alt), width, and height are provided as attributes:

``` html
<img src="example.jpg" alt="3dc" width="104" height="142">
```

The alternative text will appear in the event when the image source is not found.


## CSS - Cascading Style Sheets

#### What is CSS?

- CSS is used to define styles for your web pages, including the design, layout and variations in display for different devices and screen sizes.
- CSS describes how HTML elements are to be displayed on screen, paper, or in other media
- CSS saves a lot of work. It can control the layout of multiple web pages all at once
- External stylesheets are stored in CSS files (.css)

#### CSS Syntax

``` html
p {
  color: red;
  text-align: center;
}
```

- p is a selector in CSS (it points to the HTML element you want to style: ```<p>```).
- color is a property, and red is the property value
- text-align is a property, and center is the property value

#### CSS Selectors

- Element Selector

all ```<p>``` elements on the page will be center-aligned, with a red text colour.

``` html
p {
  color: red;
  text-align: center;
}
```

- ID Selector

The id selector uses the id attribute of an HTML element to select a specific element.

The id of an element is unique within a page, so the id selector is used to select one unique element.

```This is my text.``` will be center-aligned with a blue text colour.

``` html
#myText {
  text-align: center;
  color: blue;
}

<p id="myText">This is my text.</p>
```

- Class Selector

The class selector selects HTML elements with a specific class attribute.

```Important Header``` and ```This is important.``` will be bolded with a blue text colour.

``` html
.importantText {
  font-weight: bold;
  color: blue;
}

<h1 class ="importantText">Important Header</h1>
<p class="importantText">This is important.</p>
```

- Universal Selector

The universal selector (*) selects all HTML elements on the page.

``` html
* {
  text-align: center;
  color: blue;
}
```

#### Inserting CSS

- External CSS

External styles are defined within the ```<link>``` element, inside the ```<head>``` section of an HTML page:

(Main file: index.html)
``` html
<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

(CSS file: mystyle.css)
``` html
body {
  background-color: lightblue;
}

h1 {
  color: navy;
  margin-left: 20px;
}
```

- Internal CSS

Internal styles are defined within the ```<style>``` element, inside the ```<head>``` section of an HTML page:

``` html
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: blue;
}

h1 {
  color: maroon;
  margin-left: 40px;
}
</style>
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

- Inline CSS

Inline styles are defined within the ```style``` attribute of the relevant element:

``` html
<!DOCTYPE html>
<html>
<body>

<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>

</body>
</html>
```

## Basic Programming: JavaScript

#### What is JavaScript?

JavaScript is a text-based programming language used both on the client-side and server-side that allows you to make web pages interactive. Where HTML and CSS are languages that give structure and style to web pages, JavaScript gives web pages interactive elements that engage a user.

#### Variables

JavaScript variables are containers for storing data values.

``` js script
//String variables
var item1 = "carrot"
var item2 = "tomato"

//Numbers variables
var price1 = 5;
var price2 = 6;

var total = price1 + price2;
```

- ```//``` is used to declared a comment (won't be executed)
-    ```var``` is used to declared the variable (any data types: string, numbers, boolean, array, object)
- ```=``` is used to assign values to variables.
- ```;``` is use to separate JavaScript statements.
- ```item1``` stores the string: ```carrot```.
- ```item2``` stores the string: ```tomato```.
-  ```price1``` stores the number 5.
- ```price2``` stores the number 6.
- ```total``` stores the number 11.

#### Arithmetic Operators

![arithmetic](https://github.com/3DCdsc/Intro_to_JS_Workshop/blob/weeping/Lesson0/img/arithmetic_operator.png)

#### Assignment Operators

![assignment](https://github.com/3DCdsc/Intro_to_JS_Workshop/blob/weeping/Lesson0/img/assignment_operator.png)

#### Comparison Operators

![comparison](https://github.com/3DCdsc/Intro_to_JS_Workshop/blob/weeping/Lesson0/img/comparison_operator.png)

*Images source: https://www.w3schools.com/js/js_operators.asp*

#### Data Types

JavaScript has dynamic types. This means that the same variable can be used to hold different data types:

```js script
var x;           // Now x is undefined
x = 5;           // Now x is a Number
x = "John";      // Now x is a String
```

- String

``` js script
var carName1 = "Volvo XC60";   // Using double quotes
var carName2 = 'Volvo XC60';   // Using single quotes
```

- Numbers

``` js script
var x1 = 34.00;     // Written with decimals
var x2 = 34;        // Written without decimals
```

- Boolean

``` js script
var x = 5;
var y = 5;
var z = 6;
(x == y)       // Returns true
(x == z)       // Returns false
```

- Array (Taught in Lesson 1)
- Object (Taught in Lesson 1)

#### Functions

A JavaScript function is a block of code designed to perform a particular task.
A JavaScript function is executed when "something" invokes it (calls it).

``` js script
function myFunction(a, b) {
  return a * b;             // Function returns the product of a and b
}

var x = myFunction(4, 3);   // Function is called, return value will end up in x
//x will store the value 12.
```
- A JavaScript function is defined with the ```function``` keyword, followed by a name, followed by parentheses ``()``.
- The parentheses may include parameter names separated by commas: ```(parameter1, parameter2, ...)```
- The code to be executed, by the function, is placed inside curly brackets: ```{}```
- When JavaScript reaches a ```return``` statement, the function will stop executing and return the value as stated.

#### Conditions

- Use the ```if ```statement to specify a block of JavaScript code to be executed if a condition is true.
- Use the ```else``` statement to specify a block of code to be executed if the condition is false.
- Use the ```else if``` statement to specify a new condition if the first condition is false.

``` js script
if (condition1) {
  //  block of code to be executed if condition1 is true
} else if (condition2) {
  //  block of code to be executed if the condition1 is false and condition2 is true
} else {
  //  block of code to be executed if the condition1 is false and condition2 is false
}
```
## Contributor
[Wee Ping](https://github.com/GrimmWeeper)

## Reference
[W3Schools](https://www.w3schools.com/)

