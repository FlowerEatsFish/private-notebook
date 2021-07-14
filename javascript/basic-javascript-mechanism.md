# Basic JavaScript mechanism

- [Basic JavaScript mechanism](#basic-javascript-mechanism)
  - [References](#references)
  - [Variable object (VO)](#variable-object-vo)
  - [Hoisting](#hoisting)
  - [Scoping](#scoping)
  - [The "this" keyword](#the-this-keyword)

## References

- [The Complete JavaScript Course 2018](https://www.udemy.com/the-complete-javascript-course/)
- [JavaScript Visualized: the JavaScript Engine](https://dev.to/lydiahallie/javascript-visualized-the-javascript-engine-4cdf/)
- [JavaScript Visualized: Hoisting](https://dev.to/lydiahallie/javascript-visualized-hoisting-478h)
- [JavaScript Visualized: Scope (Chain)](https://dev.to/lydiahallie/javascript-visualized-scope-chain-13pd/)

## Variable object (VO)

```js
yourName === window.yourName; // true
```

> [Back to top](#basic-javaScript-mechanism)

## Hoisting

```js
calculateAge(2000); // 18
function calculateAge(year) {
  console.log(2018 - year)
}

life(2000); // Uncaught TypeError: life is not a function
var life = function(year) {
  console.log(2018 - year);
}
life(2000); //18

console.log(age); // undefined
var age = 28;
function foo() {
  console.log(age); // undefined
  var age = 35;
  console.log(age); // 35
}
foo();
console.log(age); // 28
```

> [Back to top](#basic-javaScript-mechanism)

## Scoping

```js
var a = 'hello'; // a is defined
first();

function first() { // a, b are defined
  var b = 'hi';
  second();

  function second() { // a, b, c are defined
    var c = 'hey';
    third();
  }
}

function third() { // a, d are defined
  var d = 'hmm';
  console.log(a);
  console.log(b); // Uncaught ReferenceError: b is not defined
  console.log(c); // Uncaught ReferenceError: c is not defined
  console.log(d);
}
```

> [Back to top](#basic-javaScript-mechanism)

## The "this" keyword

```js
testThis(); // this = Windows object
function testThis() {
  console.log(this);
}

var flower = {
  name: 'plant',
  yearOfBirth: 1990,
  calculateAge: function() {
    console.log(this);
    console.log(2018 - this.yearOfBirth);

    function innerFunction() {
      console.log(this);
    }
    innerFunction();
  }
}
flower.calculateAge(); // this of calculateAge() = flower object; this of innerFunction() = Windows object

var fish = {
  name: 'animal',
  yearOfBirth: 1995,
};

fish.calculateAge = flower.calculateAge;
fish.calculateAge(); // this of calculateAge() = fish object; this of innerFunction() = Windows object
```

> [Back to top](#basic-javaScript-mechanism)
