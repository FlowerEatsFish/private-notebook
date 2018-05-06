# ./package.json

- [./package.json](#packagejson)
  - [Global](#global)
    - [ESlint-related packages](#eslint-related-packages)
  - [DevDependencies](#devdependencies)
    - [Webpack-related packages](#webpack-related-packages)
    - [Babel-related packages](#babel-related-packages)
    - [Loader-related packages](#loader-related-packages)
  - [Dependencies](#dependencies)
    - [Electron-related packages](#electron-related-packages)
    - [React-related packages](#react-related-packages)
    - [XMLHttpRequests](#xmlhttprequests)

---

## Global

### ESlint-related packages

- List:

  - eslint
  - eslint-config-airbnb (for using Airbnb lint style)
  - eslint-plugin-import
  - eslint-plugin-jsx-a11y
  - eslint-plugin-react (for linting React components)

- Commands:

  ```shell
  sudo npm i -g eslint@latest eslint-config-airbnb@latest eslint-plugin-import@latest eslint-plugin-jsx-a11y@latest eslint-plugin-react@latest
  ```

[Top](#packagejson)

---

## DevDependencies

### Webpack-related packages

- List:

  - mini-css-extract-plugin
  - webpack (version 4 / main)
  - webpack-cli

- Commands:

  ```shell
  npm i -D mini-css-extract-plugin@latest webpack@4 webpack-cli@latest
  ```

[Top](#packagejson)

### Babel-related packages

- List:

  - babel-core
  - babel-loader
  - babel-polyfill
  - babel-preset-env
  - babel-preset-react

- Commands:

  ```shell
  npm i -D babel-core@latest babel-loader@latest babel-polyfill@latest babel-preset-env@latest babel-preset-react@latest
  ```

[Top](#packagejson)

### Loader-related packages

- List:

  - css-loader
  - image-webpack-loader
  - node-sass
  - sass-loader
  - url-loader

- Commands:

  ```shell
  npm i -D css-loader@latest image-webpack-loader@latest node-sass@latest url-loader@latest
  ```

[Top](#packagejson)

---

## Dependencies

### Electron-related packages

- List:

  - electron (main)

- Commands:

  ```shell
  npm i -P electron@latest
  ```

[Top](#packagejson)

### React-related packages

- List:

  - prop-types (main)
  - react (main)
  - react-dom (main)
  - react-redux
  - redux

- Commands:

  ```shell
  npm i -P react@16 react-dom@16 prop-types@latest react-redux@latest redux@latest
  ```

[Top](#packagejson)

### XMLHttpRequests

- List:

  - axios
  - fetch-jsonp

- Commands:

  ```shell
  # Axios
  $ npm i -P axios@latest

  # Fetch-Jsonp
  $ npm i -P fetch-jsonp@latest
  ```

[Top](#packagejson)
