# Promise - Reject vs. Throw

- [Promise - Reject vs. Throw](#promise---reject-vs-throw)
  - [References](#references)
  - [Schema](#schema)
  - [Reject vs. Throw](#reject-vs-throw)

## References

- [JavaScript Promises - reject vs. throw](https://stackoverflow.com/questions/33445415/javascript-promises-reject-vs-throw/)

## Schema

```javascript
const runResolve = () => Promise.resolve('I receive Promise.resolve.');

const runReject = () => Promise.reject('I receive Promise.reject.');

const runThrow = () => new Promise(() => { throw 'I throw an error.' });

const main = async () => {
  await console.log('\nTo run full code and receive resolve method.');
  await runResolve()
    .then(res => console.log(res), rej => console.log(rej))
    .catch(err => console.log(err));

  await console.log('\nTo run full code and receive reject method.');
  await runReject()
    .then(res => console.log(res), rej => console.log(rej))
    .catch(err => console.log(err));

  await console.log('\nTo have a lack of "catch" and receive reject method.');
  await runReject()
    .then(res => console.log(res), rej => console.log(rej));

  await console.log('\nTo have a lack of "reject" parameter on "then" and receive reject method.');
  await runReject()
    .then(res => console.log(res))
    .catch(err => console.log(err));

  await console.log('\nTo run full code and receive an error by "throw" method.');
  await runThrow()
    .then(res => console.log(res), rej => console.log(rej))
    .catch(err => console.log(err));
}

main();

// To run full code and receive resolve method.
// I receive Promise.resolve.

// To run full code and receive reject method.
// I receive Promise.reject.

// To have a lack of "catch" and receive reject method.
// I receive Promise.reject.

// To have a lack of "reject" parameter on "then" and receive reject method.
// I receive Promise.reject.

// To run full code and receive an error by "throw" method.
// I throw an error.
```

## Reject vs. Throw

```javascript
const runThrowForwardReject = () => new Promise((resolve, reject) => {
  throw 'I throw an error.';
  console.log('Hello.');
  reject('I receive Promise.reject.');
});

const runThrowBehindReject = () => new Promise((resolve, reject) => {
  reject('I receive Promise.reject.');
  console.log('Hello.');
  throw 'I throw an error.';
});

const main = async () => {
  await console.log('\nTo run full code and check "reject" and "throw" methods.');
  await runThrowForwardReject()
    .then(res => console.log(res), rej => console.log(rej))
    .catch(err => console.log(err));

  await console.log('\nTo run full code and check "reject" and "throw" methods.');
  await runThrowBehindReject()
    .then(res => console.log(res), rej => console.log(rej))
    .catch(err => console.log(err));
}

main();

// To run full code and check "reject" and "throw" methods.
// I throw an error.

// To run full code and check "reject" and "throw" methods.
// Hello.
// I receive Promise.reject.
```
