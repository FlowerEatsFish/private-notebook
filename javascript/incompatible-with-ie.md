## ECMAScript 6 (or newest) support on Internet Explorer 9~11.

To avoid to waste time to rewrite code from ES6 (or newest) into ES5.

Explame of methods: includes() and find().

More info: [Features and browsers supported](https://polyfill.io/v2/docs/features/)

#### Troubleshooting:

Copy the code as follow to html file.

```html
<script src="https://cdn.polyfill.io/v2/polyfill.min.js"></script>
```



## [The includes() method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

Determines whether one string may be found within another string, returning true or false as appropriate.

```javascript
str.includes(searchString[, position])
```

#### Troubleshooting: [indexOf() method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)

The indexOf() method returns the index within the calling String object of the first occurrence of the specified value, starting the search at fromIndex. Returns -1 if the value is not found.

```javascript
str.indexOf(searchValue[, fromIndex])
```

#### Example

includes() method:

```javascript
var foo = 'hello world!';

if (foo.includes('hello')) {
  console.log('It is a polite variable.')
}
```

indexOf() method:

```javascript
var foo = 'hello world!';

if (foo.indexOf('hello') != -1) {
  console.log('It is a polite variable.')
}
```



## The "oninput" event of HTML elements

This event occurs when the value of an \<input> or \<textarea> element is changed.

#### Troubleshooting

Give same function to both "onchange" and "oninput" events.

The "oninput" event in Chrome work in real-time event, but the "onchange" event work after end an action. However, the "onchange" event in IE work in real-time event, but the "oninput" event doesn't work.

#### Example

```html
<input onchage="myFunction()" oninput="myFunction()">
```

```javascript
function myFunction() {
    // do something...
}
```
