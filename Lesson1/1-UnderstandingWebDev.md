# Lesson 1 - Understanding Web Development

## Recap on 3 Basic Structures

HTML - Hypertext Markup Language

CSS - Cascading Stylesheets

JS -  JavaScript

## Understanding Structure
[Pesticide for Chrome/Edge](https://chrome.google.com/webstore/detail/pesticide-for-chrome/bblbgcheenepgnnajgfpiicnbbdmmooh) 
An extension for chrome that better outlines elements to more easily see position on the page. 

Lets head over to the provided [html file](../index.html)

We'll go through inspect page function in the web brower for CSS and HTML.

We'll make heavy references to [HTML and CSS references](../Lesson_0/0-BasicIntroduction.md)


## JavaScript
Let us start on a fresh html boilerplate to understand how we can do this.

*Note: the most important thing to remember in JavaScript is that you typically want the script to run once from top to botttom, setting up functions to trigger on events/intervals that you want to happen on your site.*

How to add JavaScript into the website to introduce interactivity?

For that, we add a 
```html
<script></script>
 ``` 

tag in the html code

The best place to add the tag is actually at the very bottom of the page right before your end body tag which will be explained later

In this tag, we can put any valid JavaScript such as 
```js
var two  = 1+1;
```

But nothing's happening on our webpage so lets do something that does.

To show that it is actually working we will use console.log()
Similar to other print functions in other language if you have coded before, this special functions output values into the console located in the browser which found under "Inspect element".

```js
var two  = 1+1;
console.log(two);
```

Now let me add to the page in JavaScript
```js
document.body.innerHTML = "I've changed your contents"
```
Our body text was replaced with our "message".
Basically it found our body text and replaced the content between the tag with this.

What if we took the script tag and placed it in head?
This is because the webpage evaluate the script tag before the body tag and hence it can manipulate since it doesnt know where body tag is yet.


### DOM

Moving forward, you will be hearing me say "DOM" alot

DOM - Document Object Model.
This is the way which browsers let devloeprs manipulate webpages with js.

The DOM parses all HTML and CSS into essentially one large JS object which contains all information about a webpage to be loaded

Therefore, when we are using the global variable,"document", we are accessing the DOM to access the properties and functions in it.

```html
  <p> There are two general steps to DOM manipulation:</p>
    <ol>
      <li>find the DOM node through an access method
   - If looking for body tag, is easy by using document.body</li>
   <li>Manipulate the DOM node by changing attributes/styles/inner HTML
   - inner HTML - between the start and end tags
   - attributes - properties
   - styles - presentation outlook 
     </li>
    </ol>
```
### DOM accessing methods
Refer to [file](../index.html)

Lets say i want a specific element such as the heading only
1. Find the DOM node containing that heading

- we see that the heading h1 has a id of "heading", this means on the page, heading should be the only one with that id
- hence its really easy to find nodes with an id
  
```js
var headingEl = document.getElementById("heading");
console.log(headingEl); //to see if we have found it
headingEl.innerHTML = "cats"; //lets change it
```

the other way is by classNames/tag.
Lets say we want to change all instances of the word "dog" into "cat"

we see that each of them is surrounded with a span tag with a class of "animal"

```js
var nameEls = document.getElementsByTagName();
console.log(nameEls);
```
What the console should show is a HTML Collection which is similar to an array. Hence we can access individual elements through the square bracket notation.

```js
var nameEls = document.getElementsByTagName();
console.log(nameEls[0]);
```

*Try to change innerHTML of nameEls* : Nothing happens
We have to use for loop:
```js
for (var i = 0; i < nameEls.length; i++) {
    nameEls[i].innerHTML = "hacker cat";
 }
```

Since they may be other span tags in our webpages that are not dog
we can pass in the class as the identifier for the collection

```js
 var nameEls = document.getElementsByClassName("animal");
```

#### CSS Selector
```js
var nameEls = document.querySelectorAll("p .animal");
```
This return a NodeList which has subtle differences but we will not cover in this lesson. Feel free to look it up as you do your exploration of web dev

#### Activity 1: DOM Access
Using what you havce learnt above, console.log() a HTML Collection of all the span tags in index.html.

### DOM Manipulation

#### Changing Attributes

Explaination of attribute

##### Images
Change images of dogs to cats
```js
 var imageEls = document.getElementsByTagName("img");
for (var i = 0; i < imageEls.length; i++) {
    imageEls[i].src = "https://www.google.com/url?sa=i&url=https%3A%2F%2Fimgur.com%2Fa%2F7ok4g&psig=AOvVaw1jiZ-kcxZQmmXAMh0t7chw&ust=1595752880562000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCJDfw_GA6OoCFQAAAAAdAAAAABAD";
}
```
##### Links
```js
var linkEls = document.querySelectorAll("a[href*="Dog"]")
for (var i = 0; i < linkEls.length; i++) {
    linkEls = "http://en.wikipedia.org/wiki/Cat"
}
```
#### Changing Styles
```js

nameEls[i].style.backgroundColor = "black";
nameEls[i].style.color = "orange";
```

#### Changing CSS classes
change directly
mainEl.className = "warning";
Overriding
mainEl.classList.add("warning");

Modifyling Innerhtml/textContext
mainEl.innerHTML = ```html"<strong>warning</strong>";```'
mainEl.textContext

#### create elements from scratch
var imgEl = document.createElement("img");
document.body.appendChild(imgEl);

Similarly, you can also use insertBefore, replaceChild, removeChild, and insertAdjacentHTML.

#### Activity 2: DOM Manipulation
Using what you have learnt above, use DOM manipulation to create an element with the p tag. Then, change the style of the paragraph to have an orange background.

### DOM Events

#### Event Listener for button
```js
var buttonEl = document.getElementById("clicker");
var onButtonClick = function() {
    console.log("Oh golly gosh, you clicked me");
};
buttonEl.addEventListener("click", onButtonClick);
```
If you are overriding click behavior on a link or submit behavior on a form, you may want to call event.preventDefault() to prevent the browser's default behavior.


#### Remove
Removing event listeners
If you no longer need a particular event listener, you can remove it using removeEventListener:
var faceEl = document.getElementById("face");
var onFaceClick = function(e) {
    console.log("You clicked " + e.clientX + " , " + e.clientY);
};
faceEl.addEventListener("click", onFaceClick);
// later...
faceEl.removeEventListener("click", onFaceClick);
}

### Functions
To show this, we will input functionality of a button using alert

Here, we will also cover functions which are a segmented block of code which intends to perform a specific function

### Code Example
We attached this function to the button through the onclick attribute

```html
<script>
alert("hello");

function buttonPressed(){
  alert("hello again");
}

//ES6 way
 
buttonPressed = () =>{
  alert("hello again");
}
</script>
<button onclick ="buttonPressed()"> 
```

#### Activity 3: DOM Events
Using what you have learnt, create a button that only executes an event on the first time the button is loaded.

#### Activity 4: Summary
Using everything you have learnt today, create 2 buttons. The first button creates a new element with the p tag. The second button bolds the text in all p tags.
