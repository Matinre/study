## 概念

> 处理应用程序时，会递归地构建一个依赖关系图，其中包含应用程序需要的每个模块。然后将所有这些模块打包成一个或者多个bundle。
>
> **入口entry**
>
> 指示webpack应该使用哪个模块，来作为构建内部依赖图的开始。
>
> ```js
> //默认为./src
> module.exports = {
> entry: './path/to/my/entry/file.js'
> };
> ```
>
> **出口output**
>
> 告诉webpack在哪里输出它所创建的bundles，以及如何命名这些文件，默认值为./dist
>
> ```javascript
> //默认值为 ./dist
> //整个应用程序会被编译到指定的输出路径文件夹中
> const path = require('path');
> 
> module.exports = {
> entry: './path/to/my/entry/file.js',
> output: {
>  path: path.resolve(__dirname, 'dist'),
>  filename: 'my-first-webpack.bundle.js'
> }
> };
> ```
>
> **加载器loader（处理源文件）**
>
> 处理非js文件，将所有类型的文件转化为webpack能够处理的有效模块，其中，
>
> 1. `test` 属性，用于标识出应该被对应的 loader 进行转换的某个或某些文件。
>
> 2. `use` 属性，表示进行转换时，应该使用哪个 loader。
>
>    
>
>    **以上配置中，对一个单独的 module 对象定义了 `rules` 属性，里面包含两个必须属性：`test` 和 `use`。这告诉 webpack 编译器(compiler) 如下信息：**
>
>    **“嘿，webpack 编译器，当你碰到「在 `require()`/`import` 语句中被解析为 '.txt' 的路径」时，在你对它打包之前，先使用 `raw-loader` 转换一下。”**
>
> ```javascript
> const path = require('path');
> 
> const config = {
> output: {
>  filename: 'my-first-webpack.bundle.js'
> },
> module: {
>  rules: [
>    { test: /\.txt$/, use: 'raw-loader' }
>  ]
> }
> };
> 
> module.exports = config;
> ```
>
> **插件plugins（对整个构建过程起作用）**
>
> 插件用于打包过程前，过程后，或者某处，类似于你在vue的周期函数的操作。
>
> 想要使用一个插件，你只需要 `require()` 它，然后把它添加到 `plugins` 数组中。多数插件可以通过选项(option)自定义。你也可以在一个配置文件中因为不同目的而多次使用同一个插件，这时需要通过使用 `new` 操作符来创建它的一个实例。
>
> ```javascript
> const HtmlWebpackPlugin = require('html-webpack-plugin'); // 通过 npm 安装
> const webpack = require('webpack'); // 用于访问内置插件
> 
> const config = {
> module: {
>  rules: [
>    { test: /\.txt$/, use: 'raw-loader' }
>  ]
> },
> plugins: [
>  new HtmlWebpackPlugin({template: './src/index.html'})
> ]
> };
> 
> module.exports = config;
> 
> ```
>
> 

#### webpack优化

> - alias
>
>   > 属于resolve里面，是用来映射路径，能减少打包时间的主要原因是能够让webpack快速的解析文件路径，找到对应的文件
>   >
>   > ```js
>   > function resolve(dir) {
>   >   return path.join(__dirname, dir)
>   > }
>   > 
>   > resolve: {
>   >       alias: {
>   >         '@': resolve('src')
>   >       }
>   >     }
>   > ```
>   >
>   > 