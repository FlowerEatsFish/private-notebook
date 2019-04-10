# Unit Test

- [Unit Test](#unit-test)
  - [Jest](#jest)

## Jest

```javascript
describe('Validation of Taiwanese ID', () => {
  const isValidId = id => id.match(/^[A-Z][1-2]\d{8}$/) != null;

  it('Standard ID', () => {
    expect(isValidId('A123456789')).toBeTruthy();
  });
  it('Lowercase character should be invalid', () => {
    expect(isValidId('a123456789')).toBeFalsy();
  });
  it('Short number should be invalid', () => {
    expect(isValidId('A12345678')).toBeFalsy();
  });
  it('Long number should be invalid', () => {
    expect(isValidId('A1234567890')).toBeFalsy();
  })
  it('Unkown gender should be invalid', () => {
    expect(isValidId('A323456789')).toBeFalsy();
  })
});
```
