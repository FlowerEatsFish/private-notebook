# React - Render Props vs. Higher-Order Component

- [React - Render Props vs. Higher-Order Component](#react---render-props-vs-higher-order-component)
  - [Render Props](#render-props)
  - [Higher-Order Component](#higher-order-component)

## Render Props

[DEMO](https://codesandbox.io/embed/7m2xwk33oj)

```javascript
import React from "react";
import ReactDOM from "react-dom";

const CenterBlock = ({ render, backgroundColor }) => (
  <div
    style={{
      backgroundColor,
      display: "flex",
      flexDirection: "column",
      alignItems: "center",
      marginBottom: "20px"
    }}
  >
    <h1>Block</h1>
    {render()}
  </div>
);

class App extends React.Component {
  renderBlock1 = () => (
    <>
      <h1>Hello</h1>
      <h2>World</h2>
    </>
  );

  render() {
    return (
      <div>
        <CenterBlock backgroundColor="seagreen" render={this.renderBlock1} />
        <CenterBlock
          backgroundColor="lavenderblush"
          render={() => (
            <>
              <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut
                enim ad minim veniam, quis nostrud exercitation ullamco laboris
                nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor
                in reprehenderit in voluptate velit esse cillum dolore eu fugiat
                nulla pariatur. Excepteur sint occaecat cupidatat non proident,
                sunt in culpa qui officia deserunt mollit anim id est laborum.
              </p>
              <ul>
                <li>a</li>
                <li>b</li>
                <li>c</li>
              </ul>
            </>
          )}
        />
      </div>
    );
  }
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

## Higher-Order Component

[DEMO](https://codesandbox.io/embed/94xxvrl0jr)

```javascript
import React from "react";
import ReactDOM from "react-dom";

const Page = ({ name, number }) => (
  <div>
    <h2>{name}</h2>
    <h3>{number}</h3>
  </div>
);

const numberAddOne = Component => ({ number, ...props }) => (
  <Component {...props} number={number + 1} />
);

const greetingWithName = greeting => Component => ({ name, ...props }) => (
  <Component {...props} name={`${greeting}, ${name}`} />
);

const addATitle = Component => props => (
  <React.Fragment>
    <h1>I'm Title</h1>
    <Component {...props} />
  </React.Fragment>
);

const App = addATitle(greetingWithName("Hello")(numberAddOne(Page)));

const rootElement = document.getElementById("root");
ReactDOM.render(<App name="Michelle" number={10} />, rootElement);
```
