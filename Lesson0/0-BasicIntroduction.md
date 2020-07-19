# Lesson 0: Introduction to HTML, CSS and Basic Programming: Javascript


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
