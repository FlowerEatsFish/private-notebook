# Unit Test

- [Unit Test](#unit-test)
  - [References](#references)
  - [Jest in simple method](#jest-in-simple-method)
  - [Jest in simple exception handler](#jest-in-simple-exception-handler)

## References

- [Expect](https://jestjs.io/docs/expect)
- [Mock Functions](https://jestjs.io/docs/mock-function-api)

## Jest in simple method

```javascript
describe('Validation of Taiwanese ID', () => {
  const isValidId = id => id.match(/^[A-Z][1-2]\d{8}$/) != null;

  test('Standard ID', () => {
    expect(isValidId('A123456789')).toBeTruthy();
  });
  test('Lowercase character should be invalid', () => {
    expect(isValidId('a123456789')).toBeFalsy();
  });
  test('Short number should be invalid', () => {
    expect(isValidId('A12345678')).toBeFalsy();
  });
  test('Long number should be invalid', () => {
    expect(isValidId('A1234567890')).toBeFalsy();
  })
  test('Unkown gender should be invalid', () => {
    expect(isValidId('A323456789')).toBeFalsy();
  })
});
```

## Jest in simple exception handler

```javascript
describe('Simple exception handler', () => {
  const foo = () => { throw new Error('bar') };

  test('Should throw an exception', () => {
    expect(() => foo()).toThrow();
  });
});
```
