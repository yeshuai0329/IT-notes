# learn webpack
## 1. 目标
> 1. 基于 webpack5.0 学习, 深入学习webpack的使用以及 `webpack` 的原理, 详细文档请看: [webpack官网](https://webpack.docschina.org/concepts/)
> 2. 从 0 到 1 构建一个基于 `react-ts-eslint-webpack` 的应用
> 3. 学习 `Typescript` 语法, 以及在如何在已有的项目中加入 `Typescript` 并且配置 `Typescript`



## 2. 初始化项目
### 2.1 创建项目文件夹
```bash
$ mkdir learn-webpack  // learn-webpack 是创建的项目文件夹
$ cd learn-webpack  // learn-webpack 项目文件夹
$ mkdir public // 创建静态资源文件夹
$ mkdir src // 创建src文件夹
```



### 2.2 git 管理文件夹
```bash
$ git init 
$ touch .gitignore // 添加git忽略文件
```



### 2.3 初始化项目
```bash
$ npm init -y // 初始化项目,生成package.json文件,记录项目信息以及项目包依赖
```
## 3. 引入 `webpack`,  配置打包项目
### 3.1 引入依赖
```bash
$ npm i webpack webpack-cli -D
or
$ yarn add webpack webpack-cli -D
```


### 3.2 创建 webpack 配置文件
```bash 
$ mkdir webpack.config.js // 项目根目录创建 webpack.config.js 文件
```



## 4. webpack 核心

### 4.1 webpack 核心概念-entry

> ​		entry 是webpack打包器的入口。指示 webpack 应该使用哪个模块，来作为构建其内部依赖图的开始。进入入口起点后，webpack 会找出有哪些模块和库是入口起点（直接和间接）依赖的。
>
> ​		默认值是 `./src/index.js`，可以通过 `webpack.config.js`这个配置文件中的 `entry` 来配置来指定一个（或多个）不同的入口起点。

**webpack.config.js**

```javascript
// 单入口应用， entry 的值是入口文件路径字符串
module.exports = {
  entry: './src/index.js',
}
// 多入口应用， entry 的值是对象
module.exports = {
  entry: {
  	app: './src/app.js',
    admin: './src/index.js'
  }
}
```



### 4.2 webpack 核心概念-output

> ​		output 是用来告诉 webpack 如何将编译后的文件输出到磁盘上。
>
> ​		主要输出文件的默认值是 `./dist/main.js`，其他生成文件默认放置在 `./dist` 文件夹中。

**webpack.config.js**

```javascript
const path = require('path')
// 单入口应用， output  的值是对象,path是输出的目录，filename 是输出的文件名。
module.exports = {
  output: {
  	path: path.resolve(__dirname, './dist')
    filename:  'bundle.js' 
  }
}

// 多入口应用， entry 的值是对象,path是输出的目录，filename 是输出的文件名。通过[name]占位符确保文件名称的唯一性。
module.exports = {
  output: {
  	path: path.resolve(__dirname, './dist')
    filename:  '[name].js'
  }
}
```



### 4.3 webpack 核心概念-loader

> ​		webpack 只能理解 JavaScript 和 JSON 文件，这是 webpack 开箱可用的自带能力。**loader** 让 webpack 能够去处理其他类型的文件，并将它们转换为有效模块，以供应用程序使用，以及被添加到依赖图中。

在 webpack 的配置中，**loader** 有两个属性：

1. `test` 属性，识别出哪些文件会被转换。
2. `use` 属性，定义出在进行转换时，应该使用哪个 loader。

**webpack.config.js**

```javascript
module.exports = {
  module: {
    rules: [
      { test: /\.css$/, use: 'css-loader' },
      { test: /\.ts$/, use: 'ts-loader' },
    ],
  },
}
```

**常用的 loader有哪些？**

| 名称         | 描述                     |
| ------------ | ------------------------ |
| bable-loader | 转化ES6+ 等语法          |
| css-loader   | 支持.css文件的加载和解析 |
| less-loader  | 将less文件转化成css文件  |
| ts-loader    | 将TS文件转化成js         |
| file-loader  | 将图片文字等打包         |
| raw-loader   | 将文件以字符串的形式导入 |
| tread-loader | 多进程打包js和css        |

#### 4.3.1 webpack 解析ES6 / React jsx

> ​		需要下载一下babel插件解析ES6

```bash
$ npm i @babel/core @babel/preset-env babel-loader -D
or
$ yarn add @babel/core @babel/preset-env babel-loader -D
```

> ​		需要下载 `'@babel/preset-react` 来解析 react jsx

**在项目根目录生成一个` .babelrc` 的文件**

```javascript
{
    "presets": [
        '@babel/preset-env' // 解析ES6
        '@babel/preset-react' // 解析jsx
    ]
}
```

**webpack.config.js**

```javascript
module.exports = {
  module: {
    rules: [
      { test: /\.js$/, use: ['babel-loader'] },
    ],
  }
}
```

#### 4.3.2 webpack 解析图片文件 / 字体文件等 

> ​		解析图片文件、字体文件等需要依赖 file-loader 插件

```bash
$ npm i file-loader -D
or
$ yarn add file-loader -D
```

**webpack.config.js**

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(jpg|png|gif|jpeg)$/i,
        use: ["file-loader"]
      }， // 解析图片
      {
         test: /\.(woff|ttf|)$/i,
         use: ["file-loader"]
      } // 字体解析
    ],
  }
}
```



> 解析图片文件、字体文件等也可以使用 url-loader ,其原理是 url-loader 内部还是使用了 file-loader 插件。url-loader可以对小图片资源进行base64转换。减少http请求。

```bash
$ npm i url-loader -D
or
$ yarn add url-loader -D
```

**webpack.config.js**

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(jpg|png|gif|jpeg)$/i,
        use: [
          {
            loader: "file-loader",
            options:{
                limit: 10240
            }
          }
        ]
      }， // 解析图片，并且把小于10K的图片转化base64
    ],
  }
}
```



### 4.4 webpack 核心概念-plugins

> ​		插件用于bundle文件的优化，资源管理，和环境变量注入，作用于整个构建过程。

**常用的 plugins 有哪些？**

| 名称                     | 描述                                         |
| ------------------------ | -------------------------------------------- |
| CommonsChunkPlugin       | 将chunks相同的模块代码提取成公共的js         |
| CleanWebpackPlugin       | 清理构建目录                                 |
| ExtractTextWebpackPlugin | 将css从bundle文件里提取成为一个独立的css文件 |
| CopyWebpackPlugin        | 将文件或文件夹拷贝到构建的输出目录           |
| HtmlWebpackPlugin        | 创建html模板                                 |
| UglifyjsWebpackPlugin    | 压缩js                                       |
| ZipWebpackPlugin         | 将打包成的资源生成一个zip包                  |



### 4.5 webpack 核心概念-mode

> ​		mode 用来指定当前构建环境是： production、development、none
>
> ​		设置 mode 可以使用 webpack 内置的函数，默认值为 production

**mode 的内置函数功能：**

| 选项        | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| development | 设置 `process.env.NODE_ENV === development`,将会开启 `NamedChunksPlugin` 和`NamedModulesPlugin` |
| production  | 设置 `process.env.NODE_ENV === production`,  webpack 将会开启一些插件，优化构建。 |
| none        | 不开启任何优化选项                                           |



### 4.6 webpack 中的文件监听

> ​		文件监听是在发现源码发生变化时，自动重新构建出新的输出文件。

**`webpack` 开启监听模式，有两种方法：**

1. 启动  `webpack`  命令时， 带上 `--watch` 参数
2. 在配置 `webpack.config.js `中设置  `watch:true`

**唯一缺陷：构建完成，需要手动刷新浏览器，不会自动刷新浏览器更新。**

**文件监听的原理分析：**

> ​		轮询判断文件的最后编辑时间是否变化，某个文件发生了变化，并不会立刻告诉监听者，而是先缓存起来，等过了`aggregateTimeout`时间

**webpack.config.js**

```javascript
module.exports = {
  // 默认 watch： false，也就是不开启。
  watch: true,
  自己偶有开启监听模式时，watchOptions 才有意义
  watchOptions: {
      // 忽略监听的文件或者文件夹，支持正则，默认为空
      ignored: /node_modules/,
      // 监听到变化后300ms再去执行，默认是300ms
      aggregateTimeout: 300,
      // 判断文件是否发生变化时通过不停的向系统询问特定文件是否发生变化，默认每秒询问1000次
      poll: 1000
  }
}
```



### 4.7 webpack 中的热更新

> ​		webpack 中的热更新需要依赖 `webpack-dev-server`

```bash
// 下载
$ npm i webpack-dev-server -D
or
$ yarn add webpack-dev-server -D

配置脚本命令，package.json
"start": 'webpack-dev-server --open' // 开启本地服务，并打开一个浏览器页面
```

**webpack.config.js**

```javascript
const { HotModuleReplacementPlugin } = require('webpack')
module.exports = {
  plugins: [
    new HotModuleReplacementPlugin()
  ],
  devServer: {
     // contentBase: './dist',   webpack5.0 以后这个变量不需要写了
     // 代码压缩
     compress: true,
     // 配置热更新
     hot: true,
     // 端口默认：8080
     port: 8080，
     client: {
      // 允许在浏览器中设置日志级别，例如在重载之前，在一个错误之前或者 热模块替换 启用时。
      // 'log' | 'info' | 'warn' | 'error' | 'none' | 'verbose'
      logging: 'info',
      当出现编译错误或警告时，在浏览器中显示全屏覆盖。
      overlay: {
        errors: true,
        warnings: false,
      },
      progress: true,
    },
  }
}
```

