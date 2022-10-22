# Array chart card

<!-- TOC -->

- [Array chart card](#array-chart-card)
  - [array.concat](#arrayconcat)
  - [array.every](#arrayevery)
  - [array.filter](#arrayfilter)
  - [array.forEach](#arrayforeach)
  - [array.includes](#arrayincludes)
  - [array.indexOf](#arrayindexof)
  - [Array.isArray](#arrayisarray)
  - [array.length](#arraylength)
  - [array.map](#arraymap)
  - [array.pop](#arraypop)
  - [array.push](#arraypush)
  - [array.reduce](#arrayreduce)
  - [array.shift](#arrayshift)
  - [array.slice](#arrayslice)
  - [array.toString](#arraytostring)
  - [array.unshift](#arrayunshift)

<!-- /TOC -->

## array.concat

The concat() method is used to merge two or more arrays.

This method does not change the existing arrays, but instead returns a new array.

- Syntax:

  ```javascript
  var new_array = old_array.concat(value1[, value2[, ...[, valueN]]])
  ```

- Examples:

  ```javascript
  var num1 = [1, 2, 3],
      num2 = [4, 5, 6],
      num3 = [7, 8, 9];

  var nums = num1.concat(num2, num3);
  console.log(nums); // [1, 2, 3, 4, 5, 6, 7, 8, 9]
  ```

  ```javascript
  var alpha = ['a', 'b', 'c'];

  var alphaNumeric = alpha.concat(1, [2, 3]);
  console.log(alphaNumeric); // ['a', 'b', 'c', 1, 2, 3]
  ```

  ```javascript
  var num1 = [[1]];
  var num2 = [2, [3]];

  var nums = num1.concat(num2);
  console.log(nums); // [[1], 2, [3]]

  // modify the first element of num1
  num1[0].push(4);
  console.log(nums); // [[1, 4], 2, [3]]
  ```

---

- array.copyWithin
- array.entries

---

## array.every

The every() method tests whether all elements in the array pass the test implemented by the provided function.

- Syntax:

  ```javascript
  arr.every(callback[, thisArg])
  ```

- Examples:

  ```javascript
  function isBigEnough(element, index, array) {
    return element >= 10;
  }
  
  [12, 5, 8, 130, 44].every(isBigEnough); // false
  [12, 54, 18, 130, 44].every(isBigEnough); // true
  ```

---

- array.fill

---

## array.filter

The filter() method creates a new array with all elements that pass the test implemented by the provided function.

- Syntax:

  ```javascript
  var newArray = arr.filter(callback(currentValue[, index[, array]])[, thisArg])
  ```

- Examples:

  ```javascript
  function isBigEnough(value) {
    return value >= 10;
  }

  var filtered = [12, 5, 8, 130, 44].filter(isBigEnough); // [12, 130, 44]
  ```

  ```javascript
  var fruits = ['apple', 'banana', 'grapes', 'mango', 'orange'];

  function filterItems(query) {
    return fruits.filter(function(el) {
      return el.toLowerCase().indexOf(query.toLowerCase()) > -1;
    })
  }

  console.log(filterItems('ap')); // ['apple', 'grapes']
  console.log(filterItems('an')); // ['banana', 'mango', 'orange']
  ```

---

- array.find
- array.findIndex

---

## array.forEach

The forEach() method executes a provided function once for each array element.

- Syntax:

  ```javascript
  arr.forEach(function callback(currentValue, index, array) {
    //your iterator
  }[, thisArg]);
  ```

- Examples:

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

- Array.from

---

## array.includes

The includes() method determines whether an array includes a certain element, returning true or false as appropriate.

**ECMAScript 2016. Don't support IE.**

- Syntax:

  ```javascript
  arr.includes(searchElement)
  arr.includes(searchElement, fromIndex)
  ```

- Examples:

  ```javascript
  [1, 2, 3].includes(2); // true
  [1, 2, 3].includes(4); // false
  [1, 2, 3].includes(3, 3); // false
  [1, 2, 3].includes(3, -1); // true
  [1, 2, NaN].includes(NaN); // true
  ```

---

## array.indexOf

The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.

- Syntax:

  ```javascript
  arr.indexOf(searchElement[, fromIndex])
  ```

- Examples:

  ```javascript
  var array = [2, 9, 9];
  array.indexOf(2); // 0
  array.indexOf(7); // -1
  array.indexOf(9, 2); // 2
  array.indexOf(2, -1); // -1
  array.indexOf(2, -3); // 0
  ```

---

## Array.isArray

The Array.isArray() function determines whether the passed value is an Array.

- Syntax:

  ```javascript
  Array.isArray(obj)
  ```

- Examples:

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

- array.join
- array.keys
- array.lastIndexOf

---

## array.length

The length property of an object which is an instance of type Array sets or returns the number of elements in that array.

The value is an unsigned, 32-bit integer that is always numerically greater than the highest index in the array.

- Examples:

  ```javascript
  var items = ['shoes', 'shirts', 'socks', 'sweaters'];
  console.log(items.length); // 4
  ```

---

## array.map

The map() method creates a new array with the results of calling a provided function on every element in the calling array.

- Syntax:

  ```javascript
  var new_array = arr.map(function callback(currentValue, index, array) {
    // Return element for new_array
  }[, thisArg])
  ```

- Examples:

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

- Array.of

---

## array.pop

The pop() method removes the last element from an array and returns that element. This method changes the length of the array.

- Syntax:

  ```javascript
  arr.pop()
  ```

- Examples:

  ```javascript
  var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
  var popped = myFish.pop();

  console.log(myFish); // ['angel', 'clown', 'mandarin' ]
  console.log(popped); // 'sturgeon'
  ```

---

- Array.prototype

---

## array.push

The push() method adds one or more elements to the end of an array and returns the new length of the array.

- Syntax:

  ```javascript
  arr.push([element1[, ...[, elementN]]])
  ```

- Examples:

  ```javascript
  var numbers = [1, 2, 3];
  numbers.push(4);
  console.log(numbers); // [1, 2, 3, 4]

  numbers.push(5, 6, 7);
  console.log(numbers); // [1, 2, 3, 4, 5, 6, 7]
  ```

---

## array.reduce

The reduce() method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

- Syntax:

  ```javascript
  arr.reduce(callback[, initialValue])
  ```

- Examples:

  ```javascript
  const array1 = [1, 2, 3, 4];
  const reducer = (accumulator, currentValue) => accumulator + currentValue;

  // 1 + 2 + 3 + 4
  console.log(array1.reduce(reducer)); // 10

  // 5 + 1 + 2 + 3 + 4
  console.log(array1.reduce(reducer, 5)); // 15
  ```

---

- array.reduceRight
- array.reverse

---

## array.shift

The shift() method removes the first element from an array and returns that removed element. This method changes the length of the array.

- Syntax:

  ```javascript
  arr.shift()
  ```

- Examples:

  ```javascript
  var myFish = ['angel', 'clown', 'mandarin', 'surgeon'];
  console.log('myFish before:', JSON.stringify(myFish)); // myFish before: ['angel', 'clown', 'mandarin', 'surgeon']

  var shifted = myFish.shift();
  console.log('myFish after:', myFish); // myFish after: ['clown', 'mandarin', 'surgeon']
  console.log('Removed this element:', shifted); // Removed this element: angel
  ```

---

## array.slice

The slice() method returns a shallow copy of a portion of an array into a new array object selected from begin to end (end not included). The original array will not be modified.

- Syntax:

  ```javascript
  arr.slice([begin[, end]])
  ```

- Examples:

  ```javascript
  var animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

  console.log(animals.slice(2)); // expected output: Array ["camel", "duck", "elephant"]
  console.log(animals.slice(2, 4)); // expected output: Array ["camel", "duck"]
  console.log(animals.slice(1, 5)); // expected output: Array ["bison", "camel", "duck", "elephant"]
  ```

---

- array.some
- array.sort
- array.splice
- array.toLocaleString

---

## array.toString

The toString() method returns a string representing the specified array and its elements.

- Syntax:

  ```javascript
  arr.toString()
  ```

- Examples:

  ```javascript
  var array1 = [1, 2, 'a', '1a'];

  console.log(array1.toString()); // expected output: "1,2,a,1a"
  ```

---

## array.unshift

The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.

- Syntax:

  ```javascript
  arr.unshift(element1[, ...[, elementN]])
  ```

- Examples:

  ```javascript
  var arr = [1, 2];

  arr.unshift(0); // result of call is 3, the new array length
  // arr is [0, 1, 2]

  arr.unshift(-2, -1); // = 5
  // arr is [-2, -1, 0, 1, 2]

  arr.unshift([-3]);
  // arr is [[-3], -2, -1, 0, 1, 2]
  ```

---

- array.values