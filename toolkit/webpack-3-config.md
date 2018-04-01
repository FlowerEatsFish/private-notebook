## 使用套件：

```json
{
  "devDependencies": {
    "babel-core": "*",
    "babel-loader": "*",
    "babel-preset-env": "*",
    "babel-preset-react": "*",
    "css-loader": "*",
    "extract-text-webpack-plugin": "^3",
    "node-sass": "*",
    "sass-loader": "*",
    "style-loader": "*",
    "webpack": "^3"
  },
  "dependencies": {
    "prop-types": "*",
    "react": "*",
    "react-dom": "*",
    "react-redux": "*",
    "redux": "*"
  }
}
```

#### 指令：

```
npm install prop-types react react-dom react-redux redux --save
npm install babel-core babel-loader babel-preset-env babel-preset-react css-loader extract-text-webpack-plugin@3 node-sass sass-loader style-loader webpack@3 --save-dev
```

## 原始碼：

```javascript
const path = require('path');
const webpack = require('webpack');
const ExtractTextPlugin = require('extract-text-webpack-plugin');

const extractPlugin = new ExtractTextPlugin({
  filename: 'bundle.css',
});

module.exports = {
  watch: true,
  entry: {
    app: './src/master.jsx',
    react: ['react', 'react-dom', 'prop-types'],
    redux: ['redux', 'react-redux'],
  },
  output: {
    path: path.join(__dirname, '/dist'),
    publicPath: 'dist/',
    filename: './js/bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.jsx?$/,
        loader: 'babel-loader',
        options: {
          presets: ['env', 'react'],
        },
      },
      {
        test: /\.css$/,
        use: [
          'style-loader',
          'css-loader',
        ],
      },
      {
        test: /\.scss$/,
        use: extractPlugin.extract({
          use: [
            'css-loader',
            'sass-loader',
          ],
        }),
      },
    ],
  },
  plugins: [
    new webpack.optimize.CommonsChunkPlugin({
      name: ['redux', 'react'],
      filename: './js/[name].js',
    }),
    new webpack.DefinePlugin({
      __REACT_DEVTOOLS_GLOBAL_HOOK__: '({ isDisabled: true })',
    }),
    extractPlugin,
  ],
};
```

## 打包結果：

```
project
├─┬ dist
│ ├─┬ js
│ │ ├── bundle.js
│ │ ├── react.js
│ │ └── redux.js
│ └── bundle.css
├─┬ src
│ └── master.jsx
├── package.json
└── webpack.config.js
```
