---
title: JavaScript Questions
layout: layouts/page.njk
permalink: /questions/javascript-questions/index.html
---

* Can Javascript support multi-threading ?
  * Yes, with Web Workers. The web workers run on their own thread and communicates with main thread with messsages.
* Explain event delegation.
  - A technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it. 
 ```
 var form = document.querySelector('#hogwarts-application');

// Listen for changes to fields inside the form
form.addEventListener('input', function (event) {

	// Log the field that was changed
	console.log(event.target);

}, false);
 ```
* Describe event bubbling.
  * Using a form field as an example, the event would bubble up to the parent form, then any containers or divs the form was in, then the body, then the html element, then the document, then the window.Any listeners on any of those parent elements would get triggered as it bubbles up.
```
If you want to prevent bubbling from occurring, you can use the stopPropagation method:
```
* Describe event capturing.
  * Most events bubble. But some, like the focus event, do not. There’s a trick you can use to capture the event, though. The last argument in addEventListener() is called useCapture. We almost always set it to false.
```
document.addEventListener('focus', function (event) {
	console.log(event.target);
}, true);
```
* What is event loop? What is the difference between call stack and task queue?
  * Event loop is core part of Javascript. It's responsible for executing the code, collecting and processing events, executing queued sub-tasks. It's a loop which takes the tasks/events (can be synchronous or asynchronous functions) out of the task queue and executes those. Then it repeats until there is no task in queue, which is when it goes to sleep. When executing synchronous tasks it utilized the call stack to keep track of function chain. For asynchronous tasks it delegates the callback. Javascript also uses heap to allocate memory to objects (not primitive types).

* Explain how `this` works in JavaScript.
  * Can you give an example of one of the ways that working with `this` has changed in ES6?
* Explain how prototypal inheritance works.
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
    * null - is a value of type object and can be assigned to variable explicitly to suggest there is nothing 
    * undefined - is a type as well as value. when a variable is declared by not assigned a value, it's contain value undefined and it'll be of type 'undefined'
    * undeclared - when a variable isn't declared, it'll be of type 'undefined'
  * How would you go about checking for any of these states?
    ** a === null
    ** a === undefined
    ** try { a } catch(e) { }// if there is exception it's undeclared
* What is a closure, and how/why would you use one?
* What language constructions do you use for iterating over object properties and array items?
  * forEach 
* Can you describe the main difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?
  * map returns array after some operation on each element, forEach doesn't
* What's a typical use case for anonymous functions?
  * event listeners 
* What's the difference between host objects and native objects?
  * native objects are recognized by the Javascript interpreters like Object, Math, Date,string methods like indexOf and replace, array methods, 
  * host objects are supplied by the environment (browser, node) like window, setTimeout
* Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
* Can you explain what `Function.call` and `Function.apply` do? What's the notable difference between the two?
* Explain `Function.prototype.bind`.
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain "hoisting".
* What's the difference between an "attribute" and a "property"?
* What are the pros and cons of extending built-in JavaScript objects?
* What is the difference between `==` and `===`?
* Explain the same-origin policy with regards to JavaScript.
* Why is it called a Ternary operator, what does the word "Ternary" indicate?
* What is strict mode? What are some of the advantages/disadvantages of using it?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What are the differences between variables created using `let`, `var` or `const`?
  * let has lexical scope(or block scope), var has function scope. with const the value once assigned can't change.
* What are the differences between ES6 class and ES5 function constructors?
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?
* Can you give an example for destructuring an object or an array?
```
const user = {
    id: 42,
    isVerified: true
};
const {id, isVerified} = user;

// array
const colors = ['red', 'green', 'blue'];
const [red, green] = colors;
```
* Can you give an example of generating a string with ES6 Template Literals?
* Can you give an example of a curry function and why this syntax offers an advantage?
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
* How can you share code between files?
* Why you might want to create static class members?
* What is the difference between `while` and `do-while` loops in JavaScript?
* What is a promise? Where and how would you use promise?

## Coding questions
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* What will be returned by each of these?
```javascript
console.log("hello" || "world")
console.log("foo" && "bar")
```
* Write an immediately invoked function expression (IIFE)
