# Snippet cheat sheet

- [Snippet cheat sheet](#snippet-cheat-sheet)
  - [Array snippets](#array-snippets)
    - [Chunk](#chunk)
    - [Compact](#compact)
    - [Deep flatten](#deep-flatten)
    - [Difference](#difference)
    - [Drop](#drop)
    - [Permutations](#permutations)
    - [Shuffle](#shuffle)
    - [Similarity](#similarity)
  - [Function snippets](#function-snippets)
    - [Sleep](#sleep)
  - [Math snippets](#math-snippets)
    - [Is divisible](#is-divisible)
    - [Is even](#is-even)
    - [Is prime](#is-prime)
    - [Primes](#primes)
    - [Random int array in range](#random-int-array-in-range)
    - [Round](#round)
    - [Sum](#sum)
  - [Node snippets](#node-snippets)
    - [Atob](#atob)
    - [Btoa](#btoa)
  - [Object snippets](#object-snippets)
    - [Lowercase keys](#lowercase-keys)
    - [Merge](#merge)
    - [Nest](#nest)
    - [Pick](#pick)
  - [String snippets](#string-snippets)
    - [Capitalize every word](#capitalize-every-word)
    - [From camel case](#from-camel-case)
    - [Mask](#mask)
    - [Pluralize](#pluralize)
    - [Yes or no](#yes-or-no)
  - [Type snippets](#type-snippets)
    - [Is nil](#is-nil)

## Array snippets

### Chunk

- Chunks an array into smaller arrays of a specified size.

```javascript
const chunk = (arr, size) =>
  Array.from({ length: Math.ceil(arr.length / size) }, (v, i) =>
    arr.slice(i * size, i * size + size)
  );
```

- Example:

```javascript
chunk([1, 2, 3, 4, 5], 2); // [[1,2],[3,4],[5]]
```

[Back to top](#ecmascript-cheat-sheet)

### Compact

- Removes falsey values from an array.

```javascript
const compact = arr => arr.filter(Boolean);
```

- Example:

```javascript
compact([0, 1, false, 2, '', 3, 'a', 'e' * 23, NaN, 's', 34]); // [ 1, 2, 3, 'a', 's', 34 ]
```

[Back to top](#ecmascript-cheat-sheet)

### Deep flatten

- Returns the difference between two arrays.

```javascript
const deepFlatten = arr => [].concat(...arr.map(v => (Array.isArray(v) ? deepFlatten(v) : v)));
```

- Example:

```javascript
deepFlatten([1, [2], [[3], 4], 5]); // [1,2,3,4,5]
```

[Back to top](#ecmascript-cheat-sheet)

### Difference

- Returns the difference between two arrays.

```javascript
const difference = (a, b) => {
  const s = new Set(b);
  return a.filter(x => !s.has(x));
};
```

- Example:

```javascript
difference([1, 2, 3], [1, 2, 4]); // [3]
```

[Back to top](#ecmascript-cheat-sheet)

### Drop

- Returns a new array with n elements removed from the left.

```javascript
const drop = (arr, n = 1) => arr.slice(n);
```

- Example:

```javascript
drop([1, 2, 3]); // [2,3]
drop([1, 2, 3], 2); // [3]
drop([1, 2, 3], 42); // []
```

[Back to top](#ecmascript-cheat-sheet)

### Permutations

- Generates all permutations of an array's elements (contains duplicates).

- **WARNING: This function's execution time increases exponentially with each array element. Anything more than 8 to 10 entries will cause your browser to hang as it tries to solve all the different combinations.**

```javascript
const permutations = arr => {
  if (arr.length <= 2) return arr.length === 2 ? [arr, [arr[1], arr[0]]] : arr;
  return arr.reduce(
    (acc, item, i) =>
      acc.concat(
        permutations([...arr.slice(0, i), ...arr.slice(i + 1)]).map(val => [item, ...val])
      ),
    []
  );
};
```

- Example:

```javascript
permutations([1, 33, 5]); // [ [ 1, 33, 5 ], [ 1, 5, 33 ], [ 33, 1, 5 ], [ 33, 5, 1 ], [ 5, 1, 33 ], [ 5, 33, 1 ] ]
```

[Back to top](#ecmascript-cheat-sheet)

### Shuffle

- Randomizes the order of the values of an array, returning a new array.

```javascript
const shuffle = ([...arr]) => {
  let m = arr.length;
  while (m) {
    const i = Math.floor(Math.random() * m--);
    [arr[m], arr[i]] = [arr[i], arr[m]];
  }
  return arr;
};
```

- Example:

```javascript
const foo = [1, 2, 3];
shuffle(foo); // [2,3,1], foo = [1,2,3]
```

[Back to top](#ecmascript-cheat-sheet)

### Similarity

- Returns an array of elements that appear in both arrays.

```javascript
const similarity = (arr, values) => arr.filter(v => values.includes(v));
```

- Example:

```javascript
similarity([1, 2, 3], [1, 2, 4]); // [1,2]
```

[Back to top](#ecmascript-cheat-sheet)

---

## Function snippets

### Sleep

- Delays the execution of an asynchronous function.

```javascript
const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));
```

- Example:

```javascript
async function sleepyWork() {
  console.log("I'm going to sleep for 1 second.");
  await sleep(1000);
  console.log('I woke up after 1 second.');
}
```

[Back to top](#ecmascript-cheat-sheet)

---

## Math snippets

### Is divisible

- Checks if the first numeric argument is divisible by the second one.

```javascript
const isDivisible = (dividend, divisor) => dividend % divisor === 0;
```

- Example:

```javascript
isDivisible(6, 3); // true
```

[Back to top](#ecmascript-cheat-sheet)

### Is even

- Returns true if the given number is even, false otherwise.

```javascript
const isEven = num => num % 2 === 0;
```

- Example:

```javascript
isEven(3); // false
```

[Back to top](#ecmascript-cheat-sheet)

### Is prime

- Checks if the provided integer is a prime number.

```javascript
const isPrime = num => {
  const boundary = Math.floor(Math.sqrt(num));
  for (var i = 2; i <= boundary; i++) if (num % i === 0) return false;
  return num >= 2;
};
```

- Example:

```javascript
isPrime(11); // true
```

[Back to top](#ecmascript-cheat-sheet)

### Primes

- Generates primes up to a given number, using the Sieve of Eratosthenes.

```javascript
const primes = num => {
  let arr = Array.from({ length: num - 1 }).map((x, i) => i + 2),
    sqroot = Math.floor(Math.sqrt(num)),
    numsTillSqroot = Array.from({ length: sqroot - 1 }).map((x, i) => i + 2);
  numsTillSqroot.forEach(x => (arr = arr.filter(y => y % x !== 0 || y === x)));
  return arr;
};
```

- Example:

```javascript
primes(10); // [2,3,5,7]
```

[Back to top](#ecmascript-cheat-sheet)

### Random int array in range

- Returns an array of n random integers in the specified range.

```javascript
const randomIntArrayInRange = (min, max, n = 1) =>
  Array.from({ length: n }, () => Math.floor(Math.random() * (max - min + 1)) + min);
```

- Example:

```javascript
randomIntArrayInRange(12, 35, 10); // [ 34, 14, 27, 17, 30, 27, 20, 26, 21, 14 ]
```

[Back to top](#ecmascript-cheat-sheet)

### Round

- Rounds a number to a specified amount of digits.

```javascript
const round = (n, decimals = 0) => Number(`${Math.round(`${n}e${decimals}`)}e-${decimals}`);
```

- Example:

```javascript
round(1.005, 2); // 1.01
```

[Back to top](#ecmascript-cheat-sheet)

### Sum

- Returns the sum of two or more numbers/arrays.

```javascript
const sum = (...arr) => [...arr].reduce((acc, val) => acc + val, 0);
```

- Example:

```javascript
sum(...[1, 2, 3, 4]); // 10
```

[Back to top](#ecmascript-cheat-sheet)

---

## Node snippets

### Atob

- Decodes a string of data which has been encoded using base-64 encoding.

```javascript
const atob = str => new Buffer(str, 'base64').toString('binary');
```

- Example:

```javascript
atob('Zm9vYmFy'); // 'foobar'
```

[Back to top](#ecmascript-cheat-sheet)

### Btoa

- Creates a base-64 encoded ASCII string from a String object in which each character in the string is treated as a byte of binary data.

```javascript
const btoa = str => new Buffer(str, 'binary').toString('base64');
```

- Example:

```javascript
btoa('foobar'); // 'Zm9vYmFy'
```

[Back to top](#ecmascript-cheat-sheet)

---

## Object snippets

### Lowercase keys

- Creates a new object from the specified object, where all the keys are in lowercase.

```javascript
const lowercaseKeys = obj =>
  Object.keys(obj).reduce((acc, key) => {
    acc[key.toLowerCase()] = obj[key];
    return acc;
  }, {});
```

- Example:

```javascript
const myObj = { Name: 'Adam', sUrnAME: 'Smith' };
const myObjLower = lowercaseKeys(myObj); // {name: 'Adam', surname: 'Smith'};
```

[Back to top](#ecmascript-cheat-sheet)

### Merge

- Creates a new object from the combination of two or more objects.

```javascript
const merge = (...objs) =>
  [...objs].reduce(
    (acc, obj) =>
      Object.keys(obj).reduce((a, k) => {
        acc[k] = acc.hasOwnProperty(k) ? [].concat(acc[k]).concat(obj[k]) : obj[k];
        return acc;
      }, {}),
    {}
  );
```

- Example:

```javascript
const object = {
  a: [{ x: 2 }, { y: 4 }],
  b: 1
};
const other = {
  a: { z: 3 },
  b: [2, 3],
  c: 'foo'
};
merge(object, other); // { a: [ { x: 2 }, { y: 4 }, { z: 3 } ], b: [ 1, 2, 3 ], c: 'foo' }
```

[Back to top](#ecmascript-cheat-sheet)

### Nest

- Given a flat array of objects linked to one another, it will nest them recursively. Useful for nesting comments, such as the ones on reddit.com.

```javascript
const nest = (items, id = null, link = 'parent_id') =>
  items
    .filter(item => item[link] === id)
    .map(item => ({ ...item, children: nest(items, item.id) }));
```

- Example:

```javascript
// One top level comment
const comments = [
  { id: 1, parent_id: null },
  { id: 2, parent_id: 1 },
  { id: 3, parent_id: 1 },
  { id: 4, parent_id: 2 },
  { id: 5, parent_id: 4 }
];
const nestedComments = nest(comments); // [{ id: 1, parent_id: null, children: [...] }]
```

[Back to top](#ecmascript-cheat-sheet)

### Pick

- Picks the key-value pairs corresponding to the given keys from an object.

```javascript
const pick = (obj, arr) =>
  arr.reduce((acc, curr) => (curr in obj && (acc[curr] = obj[curr]), acc), {});
```

- Example:

```javascript
pick({ a: 1, b: '2', c: 3 }, ['a', 'c']); // { 'a': 1, 'c': 3 }
```

[Back to top](#ecmascript-cheat-sheet)

---

## String snippets

### Capitalize every word

- Capitalizes the first letter of every word in a string.

```javascript
const capitalizeEveryWord = str => str.replace(/\b[a-z]/g, char => char.toUpperCase());
```

- Example:

```javascript
capitalizeEveryWord('hello world!'); // 'Hello World!'
```

[Back to top](#ecmascript-cheat-sheet)

### From camel case

- Converts a string from camelcase.

```javascript
const fromCamelCase = (str, separator = '_') =>
  str
    .replace(/([a-z\d])([A-Z])/g, '$1' + separator + '$2')
    .replace(/([A-Z]+)([A-Z][a-z\d]+)/g, '$1' + separator + '$2')
    .toLowerCase();
```

- Example:

```javascript
fromCamelCase('someDatabaseFieldName', ' '); // 'some database field name'
fromCamelCase('someLabelThatNeedsToBeCamelized', '-'); // 'some-label-that-needs-to-be-camelized'
fromCamelCase('someJavascriptProperty', '_'); // 'some_javascript_property'
```

[Back to top](#ecmascript-cheat-sheet)

### Mask

- Replaces all but the last num of characters with the specified mask character.

```javascript
const mask = (cc, num = 4, mask = '*') =>
  ('' + cc).slice(0, -num).replace(/./g, mask) + ('' + cc).slice(-num);
```

- Example:

```javascript
mask(1234567890); // '******7890'
mask(1234567890, 3); // '*******890'
mask(1234567890, -4, '$'); // '$$$$567890'
```

[Back to top](#ecmascript-cheat-sheet)

### Pluralize

- Returns the singular or plural form of the word based on the input number. If the first argument is an object, it will use a closure by returning a function that can auto-pluralize words that don't simply end in s if the supplied dictionary contains the word.

```javascript
const pluralize = (val, word, plural = word + 's') => {
  const _pluralize = (num, word, plural = word + 's') =>
    [1, -1].includes(Number(num)) ? word : plural;
  if (typeof val === 'object') return (num, word) => _pluralize(num, word, val[word]);
  return _pluralize(val, word, plural);
};
```

- Example:

```javascript
pluralize(0, 'apple'); // 'apples'
pluralize(1, 'apple'); // 'apple'
pluralize(2, 'apple'); // 'apples'
pluralize(2, 'person', 'people'); // 'people'

const PLURALS = {
  person: 'people',
  radius: 'radii'
};
const autoPluralize = pluralize(PLURALS);
autoPluralize(2, 'person'); // 'people'
```

[Back to top](#ecmascript-cheat-sheet)

### Yes or no

- Returns true if the string is y/yes or false if the string is n/no.

```javascript
const yesNo = (val, def = false) =>
  /^(y|yes)$/i.test(val) ? true : /^(n|no)$/i.test(val) ? false : def;
```

- Example:

```javascript
yesNo('Y'); // true
yesNo('yes'); // true
yesNo('No'); // false
yesNo('Foo', true); // true
```

[Back to top](#ecmascript-cheat-sheet)

---

## Type snippets

### Is nil

- Returns true if the specified value is null or undefined, false otherwise.

```javascript
const isNil = val => val === undefined || val === null;
```

- Example:

```javascript
isNil(null); // true
isNil(undefined); // true
```

[Back to top](#ecmascript-cheat-sheet)
