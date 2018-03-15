## Troubleshooting:

#### To lint Python files using pep8 on Visual Studio Code

Add a user setting to enable pep8:

```javascript
"python.linting.pep8Enabled": true
```

#### E1101: Module 'wx' has no '*' member

[Reference](https://stackoverflow.com/questions/20553551/how-do-i-get-pylint-to-recognize-numpy-members)

The word "wx" means [wxPython](https://pypi.python.org/pypi/wxPython/). If using Python extension for Visual Studio Code, add a user setting to whitelist wx:

```javascript
"python.linting.pylintArgs": [
  "--extension-pkg-whitelist=wx",
]
```
