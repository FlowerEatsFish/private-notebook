# Object and function

- [Object and function](#object-and-function)
  - [References](#references)
  - [Primitive list](#primitive-list)
  - [The proptotype chain](#the-proptotype-chain)
    - [Prototype](#prototype)
    - [Instance](#instance)
  - [Everything is an Object](#everything-is-an-object)
    - [Object.create](#objectcreate)
    - [Primitives](#primitives)
    - [Objects](#objects)
    - [Functions](#functions)
  - [First class functions](#first-class-functions)
    - [Passing function as arguments](#passing-function-as-arguments)
    - [Funtions returning functions](#funtions-returning-functions)
  - [Immediately Invoked Function Expression (IIFE)](#immediately-invoked-function-expression-iife)
  - [Closures](#closures)
  - [Bind, Call, and Apply](#bind-call-and-apply)

## References

- [The Complete JavaScript Course 2018](https://www.udemy.com/the-complete-javascript-course/)
- [JavaScript Visualized: Prototypal Inheritance](https://dev.to/lydiahallie/javascript-visualized-prototypal-inheritance-47co/)

## Primitive list

- Number
- String
- Boolean
- Undefined
- Null

## The proptotype chain

### Prototype

- Code 1:

```js
var Person = function(name, yearOfBirth, job) {
  this.name = name;
  this.yearOfBirth = yearOfBirth;
  this.job = job;
  this.calcaulate = function() {
    console.log(2016 - this.yearOfBirth);
  };
}
```

- Code 2:

```js
var Person = function (name, yearOfBirth, job) {
  this.name = name;
  this.yearOfBirth = yearOfBirth;
  this.job = job;
}

Person.prototype.calcaulate = function() {
  console.log(2016 - this.yearOfBirth);
};
```

- Code 1 is equal to Code 2.

### Instance

- console.info(Object) metohd is used to check the Object's prototype.

```js
Person.prototype.lastName = 'Smith';

var john = new Person('John', 1990, 'teacher');
var jane = new Person('Jane', 1969, 'designer');
var mark = new Person('Mark', 1948, 'retired');

john.calcaulate(); // 26
jane.calcaulate(); // 47
mark.calcaulate(); // 68

console.log(john.lastName); // Smith
console.log(jane.lastName); // Smith
console.log(mark.lastName); // Smith

john.__proto__ === Person.prototype; // true

john.hasOwnProperty('job'); // true
john.hasOwnProperty('lastName'); // false

john instanceof Person; // true

var x = [2,4,6];
console.info(x); // used to check its prototype
```

## Everything is an Object

### Object.create

```js
var personProto = {
  calcaulate: function () {
    console.log(2018 - this.yearOfBirth);
  },
};

var john = Object.create(personProto);
john.name = 'John';
john.yearOfBirth = 1990;
john.job = 'teacher';

var jane = Object.create(personProto, {
  name: { value: 'Jane' },
  yearOfBirth: { value: 1969 },
  job: { value: 'designer' },
});
```

### Primitives

```js
var a = 23;
var b = a;

a = 46;

console.log(a); // 46
console.log(b); // 23
```

### Objects

```js
var obj1 = {
  name: 'John',
  age: 26,
};

var obj2 = obj1;

obj1.age = 30;

console.log(obj1.age); // 30
console.log(obj2.age); // 30
```

### Functions

```js
var age = 27;
var obj = {
  name: 'Jonas',
  city: 'Lisbon',
};

function change(a, b) {
  a = 30;
  b.city = 'San Francisco';
}

change(age, obj);

console.log(age); // 27
console.log(obj.city); // San Francisco
// function is an instance of the Object type
```

## First class functions

### Passing function as arguments

```js
var years = [1990, 1965, 1937, 2005, 1998];

function arrayCalc(arr, fnc) { // fnc means callback()
  var arrRes = [];
  for (var i = 0; i < arr; i++) {
    arrRes.push(fnc(arr[i]));
  }
  return arrRes;
}

function calcaulateAge(el) {
  return 2016 - el;
}

function isFullAge(el) {
  return el >= 18;
}

function maxHeartRate(el) {
  if (el >= 18 && el < 81) {
    return Math.round(206.9 - (0.67 * el));
  }
  return -1;
}

var ages = arrayCalc(years, calcaulateAge);
var fullAges = arrayCalc(ages, isFullAge);
var rates = arrayCalc(ages, maxHeartRate);

console.log(ages); // [26, 51, 79, 11, 18]
console.log(fullAges); // [true, true, true, false, false]
console.log(rates); // [109, 173, 154, -1, 195];
```

### Funtions returning functions

```js
function interviewQuestion(job) {
  if (job === 'designer') {
    return function(name) {
      console.log(name + ', can you please explain what UX design is?');
    }
  } else if (job === 'teacher') {
    return function(name) {
      console.log('What subject do you teach, ' + name + '?');
    }
  } else {
    return function(name) {
      console.log('hello ' + name + ', what do you do?');
    }
  }
}

var teacherQuestion = interviewQuestion('teacher');
var designerQuestion = interviewQuestion('designer');

teacherQuestion('John'); // What subject do you teach, John?
designerQuestion('John'); // John, can you please explain what UX design is?
designerQuestion('Mark'); // Mark, can you please explain what UX design is?

interviewQuestion('teacher')('Mark'); // What subject do you teach, Mark?
```

## Immediately Invoked Function Expression (IIFE)

```js
function game() {
  var score = Math.random() * 10;
  console.log(score >= 5); // true
}
game(); // true

(function () {
  var score = Math.random() * 10;
  console.log(score >= 5); // true or false
})();

console.log(score); // Uncaught ReferenceError: score is not defined
```

## Closures

```js
function retirement(retirementAge) {
  var a = ' years left until retirement.';
  return function(yearOfBirth) {
    var age = 2016 - yearOfBirth;
    console.log((retirementAge - age) + a);
  }
}

var retirementUS = retirement(66);
retirementUS(1990); // 40 years left until retirement.
// retirementAge = 66
// a = ' years left until retirement.'
retirement(66)(1990); // 40 years left until retirement.
// retirementAge = 66
// a = ' years left until retirement.'
// yearOfBirth = 1990
// age = 26

var retirementGermany = retirement(65);
var retirementIceland = retirement(67);
retirementGermany(1990); // 39
retirementIceland(1990); // 41
```

## Bind, Call, and Apply

```js
var john = {
  name: 'John',
  age: 26,
  job: 'teacher',
  presentation: function(style, timeOfDay) {
    if (style === 'formal') {
      console.log('Good ' + timeOfDay + ' Ladies and gentlemen! I\'m ' + this.name + ', ' + this.job + ' and ' + this.age + ' years old. Have a nice ' + timeOfDay + '.');
    } else if (style === 'friendly') {
      console.log('Hey! What\'s up? I\'m ' + this.name + ', ' + this.job + ' and ' + this.age + ' years old. Have a nice ' + timeOfDay + '.');
    }
  }
};

var emily = {
  name: 'Emily',
  age: 35,
  job: 'designer',
};

john.presentation('formal', 'morning'); // Good morning Ladies and gentlemen! I'm John, teacher and 26 years old. Have a nice morning.

john.presentation.call(emily, 'friendly', 'afternoon'); // Hey! What's up? I'm Emily, designer and 35 years old. Have a nice afternoon.
john.presentation.apply(emily, ['friendly', 'afternoon']); // Hey! What's up? I'm Emily, designer and 35 years old. Have a nice afternoon.

var johnFriendly = john.presentation.bind(john, 'friendly');
johnFriendly('morning'); // Hey! What's up? I'm John, teacher and 26 years old. Have a nice morning.
johnFriendly('night'); // Hey! What's up? I'm John, teacher and 26 years old. Have a nice night.

var emilyFormal = john.presentation.bind(emily, 'formal');
emilyFormal('afternoon'); // Good afternoon Ladies and gentlemen! I'm Emily, designer and 35 years old. Have a nice afternoon.
```
