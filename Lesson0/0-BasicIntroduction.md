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
