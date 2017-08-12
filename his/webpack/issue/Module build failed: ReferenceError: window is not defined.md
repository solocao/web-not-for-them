# Module build failed: ReferenceError: window is not defined

错误写法

```
const webpack = require('webpack');
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ExtractTextPlugin = require('extract-text-webpack-plugin');

module.exports = {
  entry: {
    app: path.resolve(__dirname, '../src/app.js')
  },
  output: {
    path: path.resolve(__dirname, '../dist'),
    filename: '[name].js',
    publicPath: '/'
  },
  devtool: '#source-map',
  module: {
    rules: [
      {
        test: /\.js$/,
        loader: 'babel-loader',
        exclude: /node_modules/
      },
      {
        test: /\.styl$/,
        use: ExtractTextPlugin.extract({
          fallback:'style-loader',
          use:['style-loader','css-loader','stylus-loader'],
          }
        )
      }
    ]
  },
  plugins: [
    new ExtractTextPlugin('[name].css'),
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, '../src/index.html')
    })
  ]
};

```

正确写法

```
const webpack = require('webpack');
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ExtractTextPlugin = require('extract-text-webpack-plugin');

module.exports = {
  entry: {
    app: path.resolve(__dirname, '../src/app.js')
  },
  output: {
    path: path.resolve(__dirname, '../dist'),
    filename: '[name].js',
    publicPath: '/'
  },
  devtool: '#source-map',
  module: {
    rules: [
      {
        test: /\.js$/,
        loader: 'babel-loader',
        exclude: /node_modules/
      },
      {
        test: /\.styl$/,
        use: ExtractTextPlugin.extract({
          fallback:'style-loader',
          use:['css-loader','stylus-loader'],
          }
        )
      }
    ]
  },
  plugins: [
    new ExtractTextPlugin('[name].css'),
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, '../src/index.html')
    })
  ]
};
```

解释

This is what [style-loader](https://webpack.js.org/loaders/style-loader/) do:

> Adds CSS to the DOM by injecting a <style> tag

& this is what [ExtractTextWebpackPlugin](https://webpack.js.org/plugins/extract-text-webpack-plugin/) do:

> extract text from a bundle, or bundles, into a separate file.

You'll probably never need to do both at one place but it's great to have inlining as a fallback to when ExtractTextWebpackPlugin fails.