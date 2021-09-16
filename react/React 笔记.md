# React 笔记

## 一、React 简介

> React  是2013年由 Facebook 推出的一套用来构建用户界面的 JavaScript 库。
>
> React 主要是用来构建UI，很多人认为 React 是MVC中的V（视图）。

## 二、React 的特点

- **声明式设计** - React 采用声明范式，可以轻松描述应用。
- **高效**- React 通过对 DOM 的模拟，最大限度的减少与真实DOM的交互。
- **灵活** - React 可以与一直的库很好的配合。
- **JSX** - JSX 是 JavaScript 库的扩展
- **组件** - 通过 React 构建组件，是代码更容易的到复用，能够很好的应用在大项目中。
- **单向响应的数据流** - React 实现了单向响应的数据流，从而减少了重复代码，这也是它为什么比传统数据绑定更简单。

## 三、Virtual DOM

**传统的DOM更新：**

​		真实页面对应一个DOM树，在传统页面的开发模式中，每次需要更新页面时，都需要手动操作DOM来进行更新。

**虚拟DOM更新：**

​		真实页面对应一个DOM树，在页面更新之前会保存一份对现在真实DOM对应的虚拟DOM,是保存在JSON中，在每次更新页面的时候会对虚拟DOM进行操作，去做更新，当虚拟DOM完全更新完毕，再通过DIFF运算，把虚拟DOM更新的部分重绘到页面上。

## 四、React 开发环境搭建

### 1.script 标签引入方式

```javascript
// 开发环境
<script src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```



```javascript
// 生产环境
<script src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

- **react.js** - React 的核心库
- **react-dom.js** - 提供与DOM相关的功能的库
- **babel.min.js** - 用来编译 JSX 语法的babel库

### 2. creat-react-app 脚手架方式

1. 全局安装 `creat-react-app` 脚手架

```bash
$ npm i create-react-app -g
```

2. 创建项目

```bash
$ create-react-app xxxx   //xxx项目名称
```

## 五、webpack

###  1.安装webpack项目依赖

```bash
$ npm install webpack --save-dev //webpack核心
$ npm install webpack-cli --save-dev //webpack命令的一些东西
$ npm install webpack-dev-server --save-dev //webpack 开发过程中提供web服务的一些东西
```

### 2.手动搭建项目

**项目依赖：**

1. 支持sass 或者 less，需要的依赖

   ```bash
   css-loader/style-loader/sass-loader/node-sass   ------sass
   css-loader/style-loader/less-loader/less        ------less
   ```

2. 插件

```bash
copy-webpack-plugin   //public文件夹复制到dist
html-webpack-plugin   //dist文件夹自动引入html
```

3. babel转化

   ```bash
   //1.安装babel的预设
   $ npm install --save-dev @babel/core
   //2.安装专门处理react的babel的预设
   $ npm install --save-dev @babel/preset-react
   //3.安装 babel-loader
   $ npm install --save-dev babel-loader
   //4.配置 babel 的配置文件
   //配置文件有两种 1.babel.config.js 2. .babelrc
   //5.webpack,配置转换器规则
   {
   	test:/\.js$/,
   	use: ['babel-loader']
   }
   ```

   Babel.config.js

   ```js
   module.exports = {
     //预设
     presets: ['@babel/preset-react']
   }
   ```

   

   

### 3. webpack.config.js

```javascript
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')
const CopyWebpackPlugin = require('copy-webpack-plugin')

module.exports = {
  //打包模式，有两种选择
  //1.development（）
  //2.production(默认)
  mode：'development',
  //入口文件
  entry: './src/index.js'，
  //出口文件
  output：{
  	path: path.reslove(__dirname, './dist'),
    filename: 'app.js'
	},
  module: {
    //转化器规则
    rules： [
      //less转换css
      {
        test: /\./less$/,
        use: ['css-loader', 'style-loader', 'less-loader']
      },
      //jsx转换js
      {
        test:/\.js$/,
        use: ['babel-loader']
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(_dirname, './public/index.html')
    }),
    new CopyWebpackPlugin([
      {
        form: path.resolve(__dirname, './public')
      }
    ])
  ]
}
```

### 4.package.json

```json
"scripts": {
  "dev": "webpack-dev-server --development" , //项目开发阶段启动,不会生成实际dist文件夹，而是存在在内存中
  "build": "webpack" //项目上线打包时启动
}
```

## 六、create-react-app 搭建项目

### 1.安装

```bash
$ npx create-react-app xxx  //下载最新create-react-app以后再下载 xxx项目
```

## 七、JSX语法

- 必须要有一个根元素
- 单标签一定要闭合 <br/>
- img 标签必须加 alt 属性
- 标签都是小写字母，组件首字母大写
- class ->className
- For -> htmlFor

**jsx中的注释：**

```js
{
  /*<h2>这是注释</h2>*/  多行注释
}

{
  //<h2>这是注释</h2>    单行注释
}
```

PS：在差值表达式里{false}、{''}、{null}、{undefined} 都不会渲染出来任何内容

PS:  React 没有指令系统

PS：html内容转义-防止注入攻击：

```html
<div dangerouslySetInnerHTML= {{__html: str}}><div>
```

**JSX 的语法糖：**

```js
ReactDOM.render(
	<App/>,
  document.getElementById('root') 
)

转化：

ReactDOM.render(
	React.createElement('h1',null, '我的天')，
  document.getElementById('root')
)
```



```js
ReactDOM.render(
	<div>
    <h1>我的天</h1>
  </div>,
  document.getElementById('root') 
)

转化：

ReactDOM.render(
	React.createElement(
    'h1',
    null, 
    React.createElement(
      'h1',
      null, 
      '我的天')，
  )，
  document.getElementById('root')
)
```

## 八、React 路由

### 1.`react-router`和`react-router-dom`

> 1.他们都是 react 实现路由的模块。
>
> 2.`react-router-dom` 是基于 `react-router` 的，在 `react-router`  的基础上再添加了一些个组件而已。

### 2.组件化使用和配置化使用

- `vue-router` 是一种配置化使用
- `react` 路由是组件化使用的方式

### 3.使用步骤

1. 安装`react-router-dom`

   ```bash
   $ npm i react-router-dom --save
   ```

2. 使用`react-router-dom` 的 `BrowserRouter` 或 `HashRouter` 包裹住项目最外层。

   ```
   import { BrowserRouter, HashRouter } from 'react-router-dom'
   ```

   PS:`BrowserRouter`上线可能会出现刷新404问题。

3. 在项目中需要填坑的位置。防止`Router`组件，并配置他的一些属性。

   ```js
   <Router path="" component={} ></Router>
   //path: 指定url地址
   //component：当路由地址组件正确的时候，匹配这个组件
   //render： 不能与component一同使用，是一个函数，返回值是一个组件
   //exact: 精确匹配
   ```

4. 如果需要路由跳转，使用`Link` 或 `NavLink`

   > to：一般是字符串、或者是对象（{
   >
   > ​	pathname: '路由信息'，
   >
   > ​	search： '?name=张三$age=18',
   >
   > ​	state:{
   >
   > ​    a:3
   >
   > ​	}
   >
   > }）
   >
   > 获取search参数：props.location.search
   >
   > 获取动态参数：props.match.parms
   >
   > activeClassName（NavLink）修改NavLink高亮时的类名的。默认值是active

5. `Switch` 

   > 判断条件，一个规则只能从上往下，匹配到一个规则之后，就不在往下匹配

6. `Redirect`

   > 重定向
   >
   > to属性：到哪个路由
   >
   > from属性：从哪个路由来

7. 路由页面组件会自动接收到三个prop数据

   1. history  主要可以使用它来使用编程式导航
   2. location  主要可以用来获取search state参数
   3. match 主要用来获取动态路由的参数

8. 如何在不是路由组件使用这三个属性

   1. 使用 WithRouter 包裹一下不是路由组件

9. 路由拦截

```js
//1. 登录写入状态
window.localStorage.setItem('userInfo', 'asdasdasdsadas')
//2. 回到首页
let query = {}
let search = props.location.search
	? props.location.search.replace('?','') : ''
let arr = search.split('&')
arr.forEach( item => {
  query[item.split('=')[0]] = item.split('=')[1]
})
props.history.replace(query.redirect)
```



## 九、Redux

### 1.Redux 简介

​	Redux 是 JavaScript 状态管理器。功能作用于Vuex类似。

## 2.Redux三大原则

- **单一数据源**  整个应用的 state 被存储在一棵object tree中，并且这个 object tree 只存在唯一一个 store 中。
- **state 是只读的**  唯一改变 state 的方法就是触发 action， action 是一个用于描述已发生事件的普通对象。
- **使用纯函数来执行修改**  为了描述 action 如何改变 state tree，你需要编写 reducer。

### 3.使用步骤

1. 安装 redux

   ```bash
   $ npm i redux --save
   ```

2. 创建  src/store/index.js

   这个文件主要实现，创建 store 实例的工作，并暴露创建好的 store 实例。

   ```js
   import { createStore } from 'redux'
   import reducer from './reducer'
   const store =createStore(reducer)
   
   export default store
   ```

3. 在创建 store 的时候，需要一个 reducer 纯函数

   实现 reducer 纯函数，接收 defaultState 与 action 。并返回一份全新的 state 数据。

   最后暴露这个函数，给到 创建store时使用。

   ```js
   const defaultState ={}
   export default （state=defaultState, action）=> {
     return state
   }
   ```

   

   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   





