# [The Complete React Native and Redux Course](https://www.udemy.com/the-complete-react-native-and-redux-course/)

- [The Complete React Native and Redux Course](#the-complete-react-native-and-redux-course)
  - [Installing iOS or Android simulator for develpoing](#installing-ios-or-android-simulator-for-develpoing)
  - [The difference between Web and React Native](#the-difference-between-web-and-react-native)
  - [Migration from React to React Native](#migration-from-react-to-react-native)
  - [Styling components](#styling-components)
  - [Making content scrollable](#making-content-scrollable)

## [Installing iOS or Android simulator for develpoing](https://facebook.github.io/react-native/docs/getting-started)

## The difference between Web and React Native

|HTML|JavaScript|React Native|
|---|---|---|
|onClick|-|onPress|
|a.href|location.replace|Linking.openURL|
|input[type="password"]|-|TextInput.secureTextEntry={true}|
|input.autocomplete|-|TextInput.autoCorrect|

## Migration from React to React Native

- React:

  ```javascript
  // index.js

  import React from 'react';
  import ReactDOM from 'react-dom';

  import App from 'component/app';

  ReactDOM.render(
    <App />,
    document.getElementById('app')
  );
  ```

- React Native:

  ```javascript
  // index.js

  import React from 'react';
  import ReactNative from 'react-native';

  import App from 'component/app';

  ReactNative.AppRegistry.registerComponent(
    'Project Name',
    () => App
  );
  ```

## Styling components

```javascript
// component/header.js

import React from 'react';
import { Text, View } from 'react-native';

const Header = () => {
  const { textStyle, viewStyle } = styles;

  return (
    <View style={viewStyle}>
      <Text style={textStyle}>
        I'm header.
      </Text>
    </View>
  );
}

const styles = {
  textStyle: {
    fontSize: 48
  },
  viewStyle: {
    alignItems: 'center',
    backgroundColor: '#F8F8F8',
    height: 60, // To avoid the overlap with a status bar.
    justifyContent: 'center',
    paddingTop: 15,
    shadowColor: '#000',
    shadowOffset: {
      height: 1,
      width: 0
    },
    shadowOpacity: 0.2
  }
};

export default Header;
```

## Making content scrollable

```javascript
// component/app.js

import React from 'react';
import { View, ScrollView, Text } from 'react-native';

const Content = () => (
  <ScrollView> {/* To make this component scrollable */}
    <Text>
      blablablablabla...
    </Text>
  </ScrollView>
);

const App = () => (
  <View
    style={{ flex: 1 }} {/* To avoid auto-rollback */}
  >
    <Content />
  </View>
);

export default App;
```
