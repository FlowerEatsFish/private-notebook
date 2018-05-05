# ./webpack.config.js

## 使用套件：

```json
{
  "devDependencies": {
    "babel-core": "*",
    "babel-loader": "*",
    "babel-polyfill": "*",
    "babel-preset-env": "*",
    "babel-preset-react": "*",
    "css-loader": "*",
    "image-webpack-loader": "*",
    "extract-text-webpack-plugin": "^3",
    "node-sass": "*",
    "sass-loader": "*",
    "style-loader": "*",
    "url-loader": "*",
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

### 安裝指令：

```shell
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
    polyfill: 'babel-polyfill',
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
      {
        test: /\.(jpe?g|png|gif|svg)$/,
        use: [
          'url-loader',
          'image-webpack-loader',
        ],
      },
    ],
  },
  plugins: [
    new webpack.optimize.CommonsChunkPlugin({
      name: ['redux', 'react', 'polyfill'],
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

```markdown
project
├─┬ dist
│ ├─┬ js
│ │ ├── bundle.js
│ │ ├── polyfill.js
│ │ ├── react.js
│ │ └── redux.js
│ └── bundle.css
├─┬ src
│ └── master.jsx
├── package.json
└── webpack.config.js
```
