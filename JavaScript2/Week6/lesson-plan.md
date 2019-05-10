# Lesson plan
```
> Focus on having lots of in class exercises.

> DONT teach everything, let the students investigate topics on their own aswell!

> Focus on how to read documentation, google answers and google errors!!

> Teach towards the students being able to solve the homework
```

Remember to add the code you wrote in the class to the relevant class branch's class work folder. If the branch has not been created just create and push it :) If you dont have access, write to one from the core team. You can see an example below!

To find examples of what teachers have taught before go to the class branches in the classwork folder, Fx [class 07](https://github.com/HackYourFuture-CPH/JavaScript/tree/class07/JavaScript1/Week1/classwork)

If you find anything that could be improved then please create a pull request! We welcome changes, so please get involved if you have any ideas!!!

---

- Callback function
  - Calling a function with a function
  - Function as variable
    - [Code inspiration](#function-as-a-variable)
    - [Code inspiration](#function-as-parameter)
  - Anonomyous function vs named function
    - [Code inspiration](#callback-functions)
- Asyncronicity
  - setTimeout - Let students investigate and explain how works
  - addEventListener
  - [Code inspiration](#timers)
- [Exercise 1](#button-magic), [exercise 2](#page-onload),[exercises 3](#mouse-position)
- Scope - Only if the students needs this! Ask to their abilities!

The students should after the class **feel comfortable with callback functions** and the fact that a **function works just like a variable** that can be passed around. Also hammer in the point of the difference between:

```js
document.querySelector('button', logOuttext);
document.querySelector('button', logOuttext());
```

Good example of practical example of callbacks: https://github.com/HackYourFuture-CPH/JavaScript/blob/class08/JavaScript2/Week5/classwork/extra_examples.md

At this point good coding practices is starting to get very important! Check our [coding best practices](https://github.com/HackYourFuture-CPH/curriculum/blob/master/review/review-checklist.md#javascript) and use these both when live coding but also in reviews.

## Code inspiration

### Callback functions 
```js
/*
Events
Events in javascript are thing like:
A timer has just finished, a user clicked a button, our page has loaded,
someone types into an input element or we have just gotten some data from a server. 
When these events happen, we usually want to add some functionality. 
Fx when a user clicks the like button (event), we want to increment the like counter and color the like button blue.
Or when someone clicks "Close cookies" (event) we want to remove the cookie div.
Lets first try to create some js that waits for 2 seconds and the console.logs out "2 seconds has elapsed!"
In javascript we use the word eventlistener to listen  
*/

setTimeout(function() {
    console.log("2 seconds has elapsed!");
}, 2000);


// Cool, now lets make a function as a variable:
const fourSecondLog = function() {
    console.log("4 seconds has elapsed!");
}

setTimeout(fourSecondLog, 4000);


// Now lets try and log out "button clicked!" when a button is clicked.
// To check if a button gets clicked we use a what is called an eventlistener.
// Imagine a person listening to the click of a button and everytime he hears a click he yells out "CLICKED".

const buttonElement = document.querySelector('button');
buttonElement.addEventListener('click', function() {
    console.log("Button clicked!");
});


const buttonClicked = function(){
    console.log("Button clicked as a variable!");
}
// Cool man! Lets try and add that function as a variable.
buttonElement.addEventListener('click', buttonClicked);




//Callbacks 
// Now lets learn about callbacks!
// Well actually you have already made callbacks!
// When you give a function to an event listener or a timer or when fetching data you are using a callback function

// Lets create a callback function when someone writes in a input element
const callback = function() {
    console.log("Someone is writing!!");
}

document.querySelector('input').addEventListener('input', callback);

```


### Function as a variable

```js
var someElement = document.querySelector('#btn')
// var myFunctionAsVar
// function myFunction () { ... }
console.log(myFunctionAsVar)
console.log(myFunction())

// myFunction here is a reference
document.body.addEventListener('click', function (event) {
  event.target // <= Original source of the event
  event.currentTarget // <= The current node that the event is bubbling through

  console.log(event.target)
  console.log(event.currentTarget)
})

// Can only have one listener at a time, while addEventListener can have multiple
someElement.onclick = myFunction

// Can check if there is an exisiting event listener
if (someElement.onclick != null) {} // do something

// ***********

// Named function
function myFunction () {
  console.log('myFunction')
}

// Anonymous function, assigned to a variable
var myFunctionAsVar = function () {
  console.log('myFunctionAsVar')
}


document.body.addEventListener('click', myFunctionAsVar)
document.body.addEventListener('click', myFunction)


function findShortestWord (arr) {
  // function wordLength () { ... }
  return arr.reduce(wordLength, arr[0])

  function wordLength (currentShortest, nextWord) {
    // ...
  }
}
```

### Function as parameter
```js
var words = ['Hej', 'Ø', 'København', 'Hack Your Future']

function forEach (arr, func) {
  for (var i = 0; i < arr.length; i++) {
    func(arr[i])
  }
}

var shortestWord = words[0]
forEach(words, function (word) {
  if (word.length < shortestWord.length) {
    shortestWord = word
  }
})

```

### Timers

```js
// Set a timer that will call `fn` in the future, after at least `milliseconds`
// var timer = setTimeout(fn, milliseconds)
//
// var interval = setInterval(fn, milliseconds)

var timer = setTimeout(function () {
  console.log('Wake up')
}, 1000)

clearTimeout(timer)


var counter = 0
var interval = setInterval(function () {
  if (counter > 7) return clearInterval(interval)

  counter++
  console.log('Wake up')
}, 5000)

console.log('Before')

setTimeout(function () {
  console.log('Inside')
}, 0)

console.log('After')
```

## Exercises

### Button magic
Create an `index.html` file with two buttons: 
- One with the text "Count up". When the button is clicked it should first log out 0. The next time it is clicked it should log out 1, etc.
- One with the text "Log in 5 seconds". When it is clicked it should wait 3 seconds and then console log the text "Log this message 3 seconds after click".

### Page onload
First create a callback function as a variable that logs this out: "DOM fully loaded and parsed"
This callback function should be called when the DOM is fully loaded.
To find what this function is called go to google! What should we search for???

### Mouse position
Create a handler, that prints the x,y coordinate of the mouse event.

#### Mouse position online tool
Say we want to create an online tool where businesses can see where their users' mouse is most of the time. Businesses can now figure out if they have designed their website correctly. 

 Lets create some js that will get the average `x` and `y` position of a user after 30 seconds. 

Before starting with this exercise, create a plan for how you will implement this! Maybe together with your mentor. 
