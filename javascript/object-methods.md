# Object chart card

- [Object chart card](#object-chart-card)
  - [object.assign](#objectassign)
  - [object.keys](#objectkeys)

## object.assign

The Object.assign() method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

- Syntax:

  ```javascript
  Object.assign(target, ...sources)
  ```

- Examples:

  ```javascript
  const object1 = {
    a: 1,
    b: 2,
    c: 3
  };
  const object2 = Object.assign({c: 4, d: 5}, object1);
  console.log(object2.c, object2.d);
  // expected output: 3 5
  ```

  ```javascript
  var o1 = { a: 1 };
  var o2 = { b: 2 };
  var o3 = { c: 3 };

  var obj = Object.assign(o1, o2, o3);
  console.log(obj); // { a: 1, b: 2, c: 3 }
  console.log(o1);  // { a: 1, b: 2, c: 3 }, target object itself is changed.
  ```

  ```javascript
  var o1 = { a: 1, b: 1, c: 1 };
  var o2 = { b: 2, c: 2 };
  var o3 = { c: 3 };

  var obj = Object.assign({}, o1, o2, o3);
  console.log(obj); // { a: 1, b: 2, c: 3 }
  ```

---

- object.constructor
- object.create
- object.defineProperties
- object.defineProperty
- object.entries
- object.freeze
- object.getOwnPropertyDescriptor
- object.getOwnPropertyDescriptors
- object.getOwnPropertyNames
- object.getOwnPropertySymbols
- object.getPrototypeOf
- object.hasOwnProperty
- object.is
- object.isExtensible
- object.isFrozen
- object.isPrototypeOf
- object.isSealed

---

## object.keys

The Object.keys() method returns an array of a given object's own enumerable properties, in the same order as that provided by a for...in loop (the difference being that a for-in loop enumerates properties in the prototype chain as well).

- Syntax:

  ```javascript
  Object.keys(obj)
  ```

- Examples:

  ```javascript
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

- object.preventExtensions
- object.propertyIsEnumerable
- object.proto
- object.prototype
- object.seal
- object.setPrototypeOf
- object.toLocaleString
- object.toString
- object.unwatch
- object.valueOf
- object.values
- object.watch
