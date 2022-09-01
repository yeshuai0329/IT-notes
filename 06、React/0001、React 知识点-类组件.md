# React

## 001、react简介

> ​			React 起源于 Facebook 的内部项目，因为该公司对市场上所有 JavaScript MVC 框 架，都不满意，就决定自己写一套，用来架设Instagram 的网站。做出来以后，发现这套 东西很好用，就在2013年5月开源了。

## 002、前端三大框架

| 框架名  | 出现时间 |   所属   |               一开始特色                |
| :-----: | :------: | :------: | :-------------------------------------: |
| Angular |  2009年  |   谷歌   |         指令系统、双向数据绑定          |
|  React  |  2013年  | Facebook |             虚拟DOM、组件化             |
|   Vue   |  2015年  |  尤玉溪  | 指令系统、双向数据绑定、虚拟DOM、组件化 |

## 003、react 的特点

1. **组件** - 通过React构建组件，使得代码更加容易得到复用，能够很好的应用在大项目的开发中 
2. **高效** - React 通过对Dom的模拟（虚拟Dom),最大限度减少与Dom的交互
6. **单项响应的数据流** - React 实现了单项响应的数据流，从而减少了重复代码，这也是它为什么比传统的绑定更简单。
4. 声明式设计 - React采用声明范式，可以轻松描述应用
5. JSX - JSX 是 JavaScript 的语法扩展
6. 灵活 - React 可以与已知的库或框架很好的配合

## 004、JSX 的特点

**1. 	定义虚拟Dom的时候不要写引号**

**2.	只能有一个根标签**

**3.	给标签添加样式类名，不能用class 要使用 className**

**4.	标签中要混入js 表达式的时候，要用{}**

**5.	要使用双标签 或者 自闭标签**

**6.	标签首字母：**

​	**（1）若小写字母开头，则将改标签为html中同名元素，若 html中没有改标签对应的元素则报错。**

​	**（2）若大写字母开头，React就会渲染对应的组件，若组件没有定义，则报错**

## 004.函数式编程的好处

1. 代码简洁，开发快速
2. 接近自然语言，易于理解
3. 更方便的代码管理
4. 易于"并发编程“
5. 代码的热升级

> ​		React把过去不断重复构建UI的过程抽象成了组件，且在给定参数的情况下约定渲染对应的UI界面。React能充分利用很多函数式方法去减少冗余代码。此外，由于它本身就是简单函数，所以易于测试。可以说，函数式编程才是React的精髓。

## 005.react 起步

**4.1.全局安装 `create-react-app` 脚手架**

```bash
$ npm i -g create-react-app
```

**OR**

```bash
$ npx create-react-app xxxx  //xxxx 是项目文件夹的名称
```



​	3.2.创建项目文件夹**

```bash
$ create-react-app xxxx  //xxxx 是项目文件夹的名称
```

## 006.HOOKS

>  		Hooks是一组函数API，16.7版本前 react 函数式组件不存在状态和生命周期，Hooks给函数式组件提供了类似class组件的api，使函数组件功能类似于class一样。但是在Class类内部，不可以使用hooks.

1. useState
2. uesRef
3. useCallback
4. useEffect/useLayoutEffect
5. useReducer/useContext

## 007.受控组件

> ​		在React中，每当表单元素的状态发生变化时，都会被写入到组件的state中，这种组件在React被称为受控组件。

## 008.antd

>  		一个方便极速开发应用的插件 Ant Design ，这些相当于帮我们封装了常用的组件，我们直接拿来用就行。

## 009.webpack

> ​		webpack可以看做是**模块打包机**：它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其打包为合适的格式以供浏览器使用。

webpack四大核心：

1. entry   //入口
2. output    //出口
3. loader    
4. pulgins    //插件
   1. `HtmlWebpackPlugin`
   2. `webpack.HotModuleReplacementPlugin`
   3. `webpack.NamedModulesPlugin`
   4. `webpack.HashedModuleIdsPlugin`
   5. `uglifyJsPlugin`
   6. `ExtractTextPlugin`

## 010.平时还需下载哪些包

1.  `http-proxy-middleware`  //配置反向代理
2.  `axios`   //发送http请求
3.  `webpack-dev-server`
4. `antd`
5. `redux`
6. `react-redux`
7. `redux-promise`
8. `redux-thunk`
9. `echarts`

## 011.声明式

## 012.绑定事件

1. 绑定事件的属性的命名方式是采用的小驼峰式的命名方式，因为你react是更加的接近js而不是html 
2. 在绑定事件后面添加的名称不是字符串的形式，而是一个函数的方式。

## 013.Flux

> ​		FLUX 是一种思想架构。专门解决软件的结构问题。它跟MVC架构是同一类东西，但是更加简单和清晰。
>
> ​		Redux  跟 React 是配合的最好的。

## 014.单向数据流

> ​		React的特性中有一个概念叫做“单项数据流”，从而减少了重复代码，这也是它为什么比传统的绑定更简单。
>
> ​		在 React.js 中，数据是从上自下流动（传递）的，也就是一个父组件可以把它的 state / props 通过 props 传递给它的子组件，但是子组件不能修改 props - React.js 是单向数据流，如果子组件需要修改父组件状态（数据），是通过回调函数方式来完成的

## 015.jsx

> ​		JSX 将 HTML 语法直接加入到 JavaScript 代码中，再通过翻译器转换到纯 JavaScript 后由浏览器执行。在实际开发中，JSX 在产品打包阶段都已经编译成纯 JavaScript，不会带来任何副作用，反而会让代码更加直观并易于维护。 编译过程由Babel 的 JSX 编译器实现。

016.