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
 * In JavaScript, objects have a special hidden property [[Prototype]] (as named in the specification), that is either null or references another object. That object is called “a prototype”:
```
// using .prototype
function Person(name, age) {

    this.name = name;
    this.age = age;
    this.print = function() { console.log(this.name, this.age); }
}


Person.prototype.goodPrint = function() { console.log('name: ', this.name, ' age: ', this.age) };

let p = new Person('dipshrestha', 12);
p.print();
p.goodPrint();


/// using __proto__

let p = {
    age: '12',
    name: 'dipshrestha',
    print: function() { console.log(this.name, this.age) }
}

p.__proto__ = { goodPrint: function() { console.log('name: ', this.name, ' age: ', this.age) } }
p.print();
p.goodPrint();
```
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
  * the first one is function declaration and the second one is function expression.
```
Example: Function Expression
alert(foo()); // ERROR! foo wasn't loaded yet
var foo = function() { return 5; }
Example: Function Declaration
alert(foo()); // Alerts 5. Declarations are loaded before any code can run.
function foo() { return 5; }

* Function declarations load before any code is executed while Function expressions load only when the interpreter reaches that line of code.
* Similar to the var statement, function declarations are hoisted to the top of other code and have larger scope
Function expressions aren’t hoisted, which allows them to retain a copy of the local variables from the scope where they were defined.
* Function expression are suitable to pass as callbacks as the less pollute scope.
* Function expression are beneficial for IIFE.
```
* What's the difference between feature detection, feature inference, and using the UA string?
```
Feature detection checks a feature for existence, e.g.:

if (window.XMLHttpRequest) {
    new XMLHttpRequest();
}

Feature inference checks for a feature just like feature detection, 
but uses another function because it assumes it will also exist, e.g.:

if (document.getElementsByTagName) {
    element = document.getElementById(id);
}
Checking the UA string is an old practice and should not be used anymore. 
You keep changing the UA checks and never benefit from newly implemented features, e.g.:

if (navigator.userAgent.indexOf("MSIE 7") > -1){
    //do something
}
```
* Explain "hoisting"
  * only the actual declarations are hoisted, and that assignments are left where they are.
* What's the difference between an "attribute" and a "property"?
  * Attributes are additional information which we can put in the HTML to initialize certain DOM properties.
Properties are formed when the browser parses the HTML and generates the DOM. Each of the elements in the DOM have their own set of properties which are all set by the browser. Some of these properties can have their initial value set by HTML attributes. Whenever a DOM property changes which has influence on the rendered page, the page will be immediately re rendered.
```
<html>
<div id="foo" class="bar foobar">hi</div> <!-- id and class are attributes -->
<script>
  console.dir(document.getElementById('foo')// render list of DOM properties and values
</script>
</html>

```
* Explain the same-origin policy with regards to JavaScript.
  * The same-origin policy is a browser security feature that restricts how documents and scripts on one origin can interact with resources on another origin. It helps isolate potentially malicious documents, reducing possible attack vectors. For example, it prevents a malicious website on the Internet from running JS in a browser to read data from a third-party webmail service (which the user is signed into) or a company intranet (which is protected from direct access by the attacker by not having a public IP address) and relaying that data to the attacker.The same-origin policy controls interactions between two different origins, such as when you use XMLHttpRequest or an <img> element.  
  * Cross-Origin Resource Sharing (CORS) is a security mechanism that allows servers to specify trusted origins that can be used in cross-origin requests. A CORS request can be either Simple or Preflight.
* What is strict mode? What are some of the advantages/disadvantages of using it?
* Explain the difference between mutable and immutable objects. - value of mutable object can be changed while immutable object can't be.
  * What is an example of an immutable object in JavaScript? - string, number, boolean
  * What are the pros and cons of immutability? pros - predictability, thread safety; cons - they require a separate object for each distinct value
  * How can you achieve immutability in your own code?
```
const supportedLanguages = {
  'af': 'Afrikaans',
  'bn': 'Bengali',
  'de': 'German',
  'en': 'English',
  'fr': 'French'
}
const frozenSupportedLanguages = Object.freeze(supportedLanguages); // only in strict mode
```
* Explain the difference between synchronous and asynchronous functions.
  * synchronus - sequential, wait until one is done before begining another. asynchronous - don't wait for the result 
* What are the differences between variables created using `let`, `var` or `const`?
  * let has lexical scope(or block scope), var has function scope. with const the value once assigned can't change.
* What are the differences between ES6 class and ES5 function constructors?
```
// ES6
class User {
    constructor(name, age, gender) {
        this.name = name;
        this.age = age;
        this.gender = gender;
    }
    print() {
        console.log(`${this.name} has an age of 
            ${this.age} and gender of ${this.gender}`);
    }
}
const Roy = new User('Roy', '19', 'Male');
Roy.print();

// ES5
function User1(name, age, gender) {
    this.age = age;
    this.name = name;
    this.gender = gender;
    this.print = function() {
        console.log(
            `${this.name} has an age of ${this.age} 
                and gender of ${this.gender}`
        );
    };
}
const Roy1 = new User1('Roy1', '19', 'Male');
Roy1.print();
```
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?
  * Higher-order functions in JavaScript are a special category of functions that either accept functions as an argument or return functions. On the other side, if the function uses only primitives or objects as arguments or return values, these functions are first-order. Higher-order functions provide the reusability benefit: the main behavior is provided by the higher-order function itself, and by accepting a function as an argument you extend that behavior at your will.
```
function calculate(numbers) {
  let sum = 0;
  for (const number of numbers) {
    sum = sum + number;
  }
  return sum;
}
calculate([1, 2, 4]); // => 7
/////////////////////////////

// Below extends the calculate functionality by converting into higher-order function
function calculate(operation, initialValue, numbers) {
  let total = initialValue;
  for (const number of numbers) {
    total = operation(total, number);
  }
  return total;
}
function sum(n1, n2) {
  return n1 + n2;
}
function multiply(n1, n2) {
  return n1 * n2;
}
calculate(sum, 0, [1, 2, 4]);      // => 7
calculate(multiply, 1, [1, 2, 4]); // => 8

```
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
* Can you give an example of a curry function and why this syntax offers an advantage?
* How can you share code between files?
  * make modules and do import. or import js file directly.  
* What is a promise? Where and how would you use promise?
  * It's a proxy for the value not necessarily known when the Promise is created. Promise is used to make asynchronous programming easier. It allows us to associated a handler with an asynchronous action's success value or failure reason. A Promise is in one of these states:
pending: initial state, neither fulfilled nor rejected.
fulfilled: meaning that the operation was completed successfully.
rejected: meaning that the operation failed.
```
let promise = new Promise((resolve, reject)=> {
	
	let ran = Math.floor(Math.random() * 10)
	setTimeout(f=> {
		if(ran > 4) resolve('Resolved');
		else reject('rejected');
	},1000)
})

promise.then(value => console.log(value))
.catch(console.err)
.finally(()=>console.log('do cleannup'))
```
## Easy
* Can you explain what `Function.call` and `Function.apply` do? What's the notable difference between the two?
* Explain `Function.prototype.bind`.
* What is the difference between `==` and `===`?
* What are the pros and cons of extending built-in JavaScript objects?
* Why is it called a Ternary operator, what does the word "Ternary" indicate?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
* Can you give an example of generating a string with ES6 Template Literals?
* Why you might want to create static class members?
* What is the difference between `while` and `do-while` loops in JavaScript?

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
