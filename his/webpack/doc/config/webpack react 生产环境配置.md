# webpack react 生产环境配置

production配置

主要分为两步

> Webpack.config.js 配置

```
new webpack.DefinePlugin({
  'process.env': {
     NODE_ENV: JSON.stringify(process.env.NODE_ENV),
   },
 }),
```

> Package.json 配置

```
"scripts": {
    "start": "node --harmony ./configrver/devServer.js --host 0.0.0.0",
    "test": "webpack-dev-server --config ./config/webpack.config.dev.js --colors",
    "build": "better-npm-run build"
  },
  "betterScripts": {
    "build": {
      "command": "set NODE_ENV=production &&  webpack --config ./config/webpack.config.js",
      "env": {
        "NODE_ENV": "production"
      }
    }
  },
```

