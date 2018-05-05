# Array chart card

## Description

The JavaScript Array object is a global object that is used in the construction of arrays;which are high-level, list-like objects.

- [ ] Not used.
- [x] Used.

## Methods

---

- [x] array.concat
- The concat() method is used to merge two or more arrays.
- This method does not change the existing arrays, but instead returns a new array.

Syntax:

```javascript
var new_array = old_array.concat(value1[, value2[, ...[, valueN]]])
```

Examples:

```javascript
var num1 = [1, 2, 3],
    num2 = [4, 5, 6],
    num3 = [7, 8, 9];

var nums = num1.concat(num2, num3);
console.log(nums);
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```javascript
var alpha = ['a', 'b', 'c'];

var alphaNumeric = alpha.concat(1, [2, 3]);
console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]
```

```javascript
var num1 = [[1]];
var num2 = [2, [3]];

var nums = num1.concat(num2);
console.log(nums);
// results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);
console.log(nums);
// results in [[1, 4], 2, [3]]
```

---

- [ ] array.copyWithin
- [ ] array.entries
- [ ] array.every
- [ ] array.fill
- [ ] array.filter
- [ ] array.find
- [ ] array.findIndex

---

- [x] array.forEach
- The forEach() method executes a provided function once for each array element.

Syntax:

```javascript
arr.forEach(function callback(currentValue, index, array) {
    //your iterator
}[, thisArg]);
```

Example:

```javascript
var a = ['a', 'b', 'c'];

a.forEach(function(element) {
    console.log(element);
});

// a
// b
// c
```

---

- [ ] Array.from

---

- [x] array.includes
- The includes() method determines whether an array includes a certain element, returning true or false as appropriate.
- ECMAScript 2016. Don't support IE.

Syntax:

```javascript
arr.includes(searchElement)
arr.includes(searchElement, fromIndex)
```

Examples:

```javascript
[1, 2, 3].includes(2);    // true
[1, 2, 3].includes(4);    // false
[1, 2, 3].includes(3, 3); // false
[1, 2, 3].includes(3, -1);// true
[1, 2, NaN].includes(NaN);// true
```

---

- [x] array.indexOf
- The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.

Syntax:

```javascript
arr.indexOf(searchElement[, fromIndex])
```

Examples:

```javascript
var array = [2, 9, 9];
array.indexOf(2);    // 0
array.indexOf(7);    // -1
array.indexOf(9, 2); // 2
array.indexOf(2, -1);// -1
array.indexOf(2, -3);// 0
```

---

- [x] Array.isArray
- The Array.isArray() function determines whether the passed value is an Array.

Syntax:

```javascript
Array.isArray(obj)
```

Examples:

```javascript
// all following calls return true
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
// Little known fact: Array.prototype itself is an array:
Array.isArray(Array.prototype);

// all following calls return false
Array.isArray();
Array.isArray({});
Array.isArray(null);
Array.isArray(undefined);
Array.isArray(17);
Array.isArray('Array');
Array.isArray(true);
Array.isArray(false);
Array.isArray({ __proto__: Array.prototype });
```

---

- [ ] array.join
- [ ] array.keys
- [ ] array.lastIndexOf

---

- [x] Array.length
- The length property of an object which is an instance of type Array sets or returns the number of elements in that array.
- The value is an unsigned, 32-bit integer that is always numerically greater than the highest index in the array.

Examples:

```javascript
var items = ['shoes', 'shirts', 'socks', 'sweaters'];
items.length;

// returns 4
```

---

- [x] array.map
- The map() method creates a new array with the results of calling a provided function on every element in the calling array.

Syntax:

```javascript
var new_array = arr.map(function callback(currentValue, index, array) {
    // Return element for new_array
}[, thisArg])
```

Examples:

```javascript
var numbers = [1, 5, 10, 15];
var doubles = numbers.map(function(x) {
   return x * 2;
});
// doubles is now [2, 10, 20, 30]
// numbers is still [1, 5, 10, 15]

var numbers = [1, 4, 9];
var roots = numbers.map(Math.sqrt);
// roots is now [1, 2, 3]
// numbers is still [1, 4, 9]
```

```javascript
var kvArray = [{key: 1, value: 10},
               {key: 2, value: 20},
               {key: 3, value: 30}];

var reformattedArray = kvArray.map(function(obj) {
   var rObj = {};
   rObj[obj.key] = obj.value;
   return rObj;
});

// reformattedArray is now [{1: 10}, {2: 20}, {3: 30}],

// kvArray is still:
// [{key: 1, value: 10},
//  {key: 2, value: 20},
//  {key: 3, value: 30}]
```

---

- [ ] Array.of
- [ ] array.pop
- [ ] Array.prototype

---

- [x] array.push
- The push() method adds one or more elements to the end of an array and returns the new length of the array.

Syntax:

```javascript
arr.push([element1[, ...[, elementN]]])
```

Examples:

```javascript
var numbers = [1, 2, 3];
numbers.push(4);
console.log(numbers);// [1, 2, 3, 4]

numbers.push(5, 6, 7);
console.log(numbers);// [1, 2, 3, 4, 5, 6, 7]
```

---

- [ ] array.reduce
- [ ] array.reduceRight
- [ ] array.reverse
- [ ] array.shift
- [ ] array.slice
- [ ] array.some
- [ ] array.sort
- [ ] array.splice
- [ ] array.toLocaleString
- [ ] array.toString
- [ ] array.unshift
- [ ] array.values