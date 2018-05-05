# Object chart card

## Description

The object constructor creates an object wrapper.

- [ ] Not used.
- [x] Used.

## Methods

---

- [ ] object.assign
- [ ] object.constructor
- [ ] object.create
- [ ] object.defineProperties
- [ ] object.defineProperty
- [ ] object.entries
- [ ] object.freeze
- [ ] object.getOwnPropertyDescriptor
- [ ] object.getOwnPropertyDescriptors
- [ ] object.getOwnPropertyNames
- [ ] object.getOwnPropertySymbols
- [ ] object.getPrototypeOf
- [ ] object.hasOwnProperty
- [ ] object.is
- [ ] object.isExtensible
- [ ] object.isFrozen
- [ ] object.isPrototypeOf
- [ ] object.isSealed

---

- [x] object.keys
- The Object.keys() method returns an array of a given object's own enumerable properties, in the same order as that provided by a for...in loop (the difference being that a for-in loop enumerates properties in the prototype chain as well).

Syntax:

```js
Object.keys(obj)
```

Examples:

```js
var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // console: ['0', '1', '2']

// array like object
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.keys(obj)); // console: ['0', '1', '2']

// array like object with random key ordering
var anObj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(anObj)); // ['2', '7', '100']

// getFoo is property which isn't enumerable
var myObj = Object.create({}, {
  getFoo: {
    value: function () { return this.foo; }
  }
});
myObj.foo = 1;
console.log(Object.keys(myObj)); // console: ['foo']
```

---

- [ ] object.preventExtensions
- [ ] object.propertyIsEnumerable
- [ ] object.proto
- [ ] object.prototype
- [ ] object.seal
- [ ] object.setPrototypeOf
- [ ] object.toLocaleString
- [ ] object.toString
- [ ] object.unwatch
- [ ] object.valueOf
- [ ] object.values
- [ ] object.watch