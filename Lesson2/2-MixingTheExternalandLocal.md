## Agenda
Things we will cover today
- Advanced DOM event
- Event Propagation
- DOM animations
  - Intervals and Timeouts
  - Activity: Countdown
- Dynamic content
  - Database Retrieval

## Recap on Lesson 1

1. Running JavaScript
2. Accessing the DOM
  - by Id
  - by Class
  - by tagName

3. Modifying the DOM
 - styles
 - attributes

4. Attaching/Detaching events to the DOM
 - functions

# Lesson 2 - Mixing the External and Local

## Advanced DOM events handling

Alright, through buttons, you now should know at least how a function is attached to the DOM event listener, ie. 'click' on a button element.


```js 
 function enlarge(){
    console.log('enlarge');
    image.style.transform= "scale(2)"
 }

 image.addEventListener('click',enlarge);
 // or image.onclick = enlarge();
```

Common DOM event listeners:
 - onmouseover: when cursor enters element
 - onmouseout: when cursor exits element
 - onmouseup: first event when mouse is released after held down
 - onmousedown: first event when mouse is clicked and held down
 - onclick: when mouseclick
 - onkeydown: when using keyboard
 - onfocus: when in element such as input

[DOM event references](https://www.w3schools.com/jsref/dom_obj_event.asp)

Just as a example, we will use explore this using onmouseover & onmouseout event to create the hover animated effect

As most beginners do, it is typical to create individual functions to attach to each event. But it is better practice to use only a single handler for both events. 

Here, we make use of a variable to emulate a stateful function
```js
 var mouseOver = false;
 var image = document.getElementById('cat');
 image.style.transformOrigin = "left top";
 image.style.transition = ".5s all";
 
 function imageHoverHandler(e){
    if(!mouseOver){
      e.target.style.transform= "scale(2)"
    }
    else{
      e.target.style.transform= "scale(1)"
    }
    mouseOver = !mouseOver
    
 }
 
 image.addEventListener('mouseover',imageHoverHandler);
 image.addEventListener('mouseout',imageHoverHandler);
 ```

### Introducing Transform and Transitions
NOTE: so what are we seeing that is unexpected?
- The image instantly scaled up from its center point and interferes with the previous text
- This is part of CSS which you should try to delve more into if you want to do smoother transistions and further animation

Transform uses pre-built functions to affect the current style of element without referencing start/end positions but rather the movement/translation, resulting an animation

Transition works on the timing aspect of the transformation, which can apply easing and timing adjustments on the duration for specific animations. 

Having no duration to a transformation results in instaneous movement/adjustments

```js
 image.style.transformOrigin = "left top";
 image.style.transition = ".5s all";
```

Just by adding these two lines we have created a smoother experience of the hover effect.

Before we proceed, we need to understand the difference of type of content in a web page. A Simple equivalent understanding would be: 
Static - relatively constant and hence only loads based on fixed input
Dynamic - fluctuates based on data input and hence can adjust accordingly

Another useful DOM event is the onload event and onunload event:
 - onload event: triggers when everything static on the page has loaded
 - onunload event: triggers when leaving page


```html
<script>
  function loadHandler{
    console.log("pageLoaded");
  }
  
</script>
<body onload="">
</>
```

You can also use the onload event on any other tags, ie. images, canvas.
However this should be reserved on any dynamic content in general.

```js
var img = new Image();
img.onload = function(){
  alert("I am loaded");
}
// or img.addEventListener('load',function(){alert("I am loaded");})
img.src = "";
```

Note: We can also add as many event handlers (functions) to one event to stack the effects but beware of possible conflicting scripted events. 

### Event Propagation
Note: Another situation that may happen is when you have inner elements that also have a similar function as the parent functions. Hence this is when we have to deal with event propagation.

This is especially important when we want to define the order of event handlers occuring and is seperated into 2 main ways.

1. Event Bubbling (Default)
   -  The inner-most element's event is handled first and then the outer: the <img> element's click event is handled first, then the <div> element's click event.

2. Event Capturing
   - The complete opposite where the outer-most element's event is handled first.

```js
 function enlarge(e){
  if(!divFirst){
    e.target.style.transform= "scale(2)"
  }
  alert("imgFirst");
  
 }

 function bubblingCapture(e){
  divFirst = true;
  alert("divFirst");
 }

 image.addEventListener('click',enlarge,true);
 document.getElementById('pictureDiv').addEventListener('click',bubblingCapture,true);
 ```

## DOM Animations

There are many ways which we can implement this - by CSS animations, by JSONLotties. However, through JS, we can make us of two important functions to create animated components

Default time measurement (ms ie.1000ms -> 1sec)
1. setTimeout()
   - sets up a function to trigger after a defined delay
2. setInterval()
   - sets up a funciton to recurringly trigger every X of time defined. 

```html
<button onclick="sayHello()">Say hello after 3</button> 



<script> 
function sayHello() { 
  var identity = setTimeout(alert("Hello"), 3000;
  }
</script> 
```

Activity: Make a countdown clock that start set a div to start at background red and changes it to green on finish;


## Dynamic content

There are many ways to make our webpage more dynamic in content.
One of various implementation is using public APIs to generate new content for your webpage

In the segment, we will make use of request and response objects which are involved in network request to help us pull external information that is out of our local bases

Tip: Read up on REST API in your own time, this will give you a better understanding in using them as well as maybe creating your own API requests and responses via ExpressJS, AWS, GCP. You will come across terms such as cross-site resources, promises and asynchronous functions which will help you to achieve better access and timing configuration for data input and other means

Moving on, the API we will be using is THE CAT API. This provides a images when we access the given link [https://api.thecatapi.com/v1/images/search](https://api.thecatapi.com/v1/images/search)

```js



function onLoadHandler(){
    loadJson("https://api.thecatapi.com/v1/images/search").then((response)=>{
      console.log(response);
      image.src = response[0]["url"]
    });
  }


  function loadJson(url) {
  return fetch(url)
    .then(response => {
      if (response.status == 200) {
        return response.json();
      } else {
        throw new HttpError(response);
      }
    })

```

We can see in our console that this shows a new file type - JSON. JSON stands for JavaScript Object Notation and is a file format very commonly used to intepret complex data since it is able to uses the attribute-value pair system. In this case, we are converting the response received into a JSON object so we can take the values we need

An alternative is using AJAX to access webservers from a web page
AJAX - Asynchronous JavaScript And XML

```js
  function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
     document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
```

```js
function loadJson(url) {
  return fetch(url)
    .then(response => {
      if (response.status == 200) {
        return response.json();
      } else {
        throw new HttpError(response);
      }
    })
  }
```

### Database Retrieval
Using this file format, we can also use that to interpret data from an online database and process it into information

1. Create a Database on Firebase Console
 - setup in Test Mode for learning purposes
   - This means that the data will be open and accessible easily by others but you should do in production mode for actual use 

2. Fill your collection
 - Every collection has a unique ID. Make use for this to keep distinct data apart for easy access by you


https://yourProjectID.firebaseio.com/test.json?auth=YOUR_AUTH_KEY


you get this key from your Project Settings -> Service Accounts -> Database Secrets -> show

Note: Do not use this method for any production as this exposes your authentication key which other people can use to access and manipulate your database. We are only using this to show how we can use setInterval to refresh the data placed the database

```js

  function getData(){
    function firebaseData(){
      loadJson("https://intro-to-js-52753.firebaseio.com/test.json?auth=FxJ8eRhZBI8ST5OhrfLzvJSKn9YLXE8wLqS3NMfQ").then((response)=>{
      alert(response);
    })
    }
  }

```
Optional Activity: 
Make the website recurringly take data from Firebase even though you changed it

### Q&A

