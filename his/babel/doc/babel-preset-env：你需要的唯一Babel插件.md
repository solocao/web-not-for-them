# babel-preset-env：你需要的唯一Babel插件

`babel-preset-env `是一个新的 `preset`，可以根据配置的目标运行环境（environment）自动启用需要的 babel 插件。

目前我们写 javascript 代码时，需要使用 N 个 preset，比如：`babel-preset-es2015`、`babel-preset-es2016`。es2015 可以把 ES6 代码编译为 ES5，es2016 可以把 ES2016 代码编译为 ES6。babel-preset-latest 可以编译 stage 4 进度的 ECMAScript 代码。

问题是我们几乎每个项目中都使用了非常多的 preset，包括不必要的。例如很多浏览器支持 ES6 的 generator，如果我们使用 babel-preset-es2015 的话，generator 函数就会被编译成 ES5 代码。

babel-preset-env 的工作方式类似 babel-preset-latest，唯一不同的就是 babel-preset-env 会根据配置的 env 只编译那些还不支持的特性。

使用这个插件，你讲再也不需要使用 es20xx presets 了。