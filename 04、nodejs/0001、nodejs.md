# Node.js 学习(二)

## 一、Node - 简介

### 1.前言

> 前端的发展至今短短十几年时间，技术迭代，人才累积，都发生了翻天覆地的变化，其实前端开发受到企业重视的时间并不太长，过去在很多技术人员的眼中，我们只是负责切切页面的切图仔罢了。



> 随着 Ajax 技术的兴起, html5、css3、es6等的蓬勃发展，使得前端这个岗位越来越备受瞩目。



> 再随着 NodeJS 的推出，使得前端开发能干得事情越来越多。



> 慢慢的，前端逐渐演变为“全端”



#### 2.Node.js 是什么？

> 简单的说 Node.js 就是运行在服务端的 JavaScript。

> Node.js是一个基于 Chrome V8 引擎的 JavaScript 运行环境.



由 **Ryan Dahl** 使用 **C++** 语言编写的。并在 **2009年** 推出第一个版本。



### 3.为什么需要学习Node.js?

1. 前端上手快速
2. 为了 **Money**
3. 前端工程化的基石，Grunt、Gulp、Fis3、Webpack
4. 编写服务端接口
5. 熟悉前后端的交互

## 二、Node - web服务

### 一、快速搭建一个Web服务

```js
// 引入 node 内置模块 http
const http = require('http');

/**
 * 创建http服务
 */
const server = http.createServer((req, res) => {
  // 设置状态码与响应头
  res.writeHead(200, {'Content-Type': 'text/html; charset=utf-8'});
  // 响应数据
  res.write('Hello Node');
  // 结束响应
  res.end();
})

/**
 * 监听端口
 */
server.listen(3000, () => {
  console.log('服务启动成功~');
})
```



### 二、端口号的小知识

#### 1. 取值范围

0 - 65535

#### 2. 公认端口（默认端口）

- 0 - 1023 一般都已经被使用了。

比如：

- - http   80
  - https   443
  - ftp   21
  - ssh   22
  - mysql   3306

#### 3. 端口占用

TODO

### 三、服务器相关

#### 1. 服务器是什么

> 服务器是计算机的一种，它比普通计算机运行更快、负载更高、价格更贵。服务器在网络中为其它客户机（如PC机、智能手机、ATM等终端甚至是火车系统等大型设备）提供计算或者应用服务。



> 简单来说，就是一台能够提供服务的计算机

#### 2. 使用手机浏览器访问本地电脑中启动的http服务

1. 确保手机与电脑处于同一个网络（连接同一个wifi）
2. 关闭电脑的防火墙

## 三、Node - web服务升级

### 一、处理中文乱码

```js
res.writeHead(200,{"Content-type":"text/html;charset=utf-8"})
```

### 二、nodemon

- 每次修改服务代码，都需要重新运行，很麻烦

  1. 安装一个全局的工具模块    **nodemon**  

     ```bash
     $ npm install nodemon -g
     ```

  2. 启动node服务时，使用 nodemon 命令去替代 node 命令

**注意：**

1. 1. **有时候 cmd 会有些抽搐，需要敲打一下就好**
   2. **nodemon 只在运行服务的代码时去使用。其余普通的一个 nodejs 代码运行，还是使用 node 命令就好了。**

### 三、处理post请求

-    post请求的参数在请求体上，所以不能用req.url去处理

  > 监听事件
  >
  > ​	eventName		要监听的事件名字（eventName 不是自己想的名字，是固定的名字）
  >
  > ​	callback       		监听的这个事件被触发时要执行的回调函数 
  >
  > req.on（eventName，callback）

  ```js
  /**
   *监听 req 的 data 事件 （请求传输事件）
   *这个data事件的回调函数时当请求体发送的时候触发。并且可能触发多次
   *原因时请求体特别大
   *chunk 是每次出发这个事件时传递的一部分请求体的内容
   
   */
  const http = require('http')
  const server = http.createServer((req,res)=>{
  	let raw=''
    req.on('data',(chunk)=>{
    	raw+=chunk
  	})//监听data的事件的回调是异步的，  
    req.on('end',()=>{
      console.log(raw)
      res.write('hello')
    	res.end()
    })
  
  })
  
  ```

  

## 四、Node - 模块化

### 一、传统引入文件的弊端

- 变量污染
- 代码复用性不高
- 代码可维护性不高
- 依赖关系管理不方便

### 二、模块化

#### 1.什么是模块化？

> 一个模块就是一个实现特定功能的文件，有了模块我们就可以更方便的使用别人的代码，要用什么功能就加载什么模块。

#### 2.模块化带来的好处

- 变量污染
- 代码复用性不高
- 代码可维护性不高
- 依赖关系管理不方便

### 三、规范与实现

- NodeJs   -   CommonJs规范
- RequireJS   -   AMD规范
- SeaJS   -   CMD规范

### 四、CommonJS规范

#### 1. 概述

> 每个文件就一个模块，有自己的作用域。在一个文件里面定义的变量、函数、类，都是私有的，对其它文件不可见。



> CommonJS规范规定，每个模块内部，**module** 变量代表当前模块。这个变量是一个对象，它的 **exports** 属性（即**module.exports**）是对外的接口。加载某个模块，其实就是加载该模块的 **module.exports** 属性。



**require**方法用于加载模块。

CommonJS模块的特点如下：

- 所有代码都运行在模块作用域，不会污染全局作用域。
- 模块可以多次加载，但是只会在第一次加载时运行一次，然后运行结果就被缓存了，以后再加载，就直接读取缓存结果。要想让模块再次运行，必须清除缓存。
- 模块加载的顺序，按照其在代码中出现的顺序。

#### 2. module对象

每个模块内部，都有一个 **module** 对象，代表当前模块。它有以下属性：

> - module.id 模块的识别符，通常是带有绝对路径的模块文件名。
> - module.filename 模块的文件名，带有绝对路径。
> - module.loaded 返回一个布尔值，表示模块是否已经完成加载。
> - module.parent 返回一个对象，表示调用该模块的模块。
> - module.children 返回一个数组，表示该模块要用到的其他模块。
> - module.exports 表示模块对外输出的值。



**module.exports**

> **module.exports** 属性表示当前模块对外输出的接口，其他文件加载该模块，实际上就是读取 **module.exports** 

**exports**

> 每个模块还提供有一个 **exports** 变量，指向 **module.exports** 。这等于在每个模块头部，有一行隐藏的如下代码：

```
var exports = module.exports;
```



造成的结果是，在对外暴露模块接口时，可以直接向 **exports** 添加属性和方法。

```
var name = '张三';

exports.name = name;

exports.sayHi = () => {
    console.log(`Hello, My Name is ${name}`);
}
```



注意，不能直接将exports变量指向一个值，因为这样等于切断了 **exports** 与 **module.exports** 的联系。

```
// a.js 切断了与module.exports的联系
exports = function(x) {console.log(x)};

// b.js hello方法没有被暴露，因为module.exports重新赋值了
exports.hello = function() {
  return 'hello';
};

module.exports = 'Hello world';
```



如果你觉得，**exports** 与 **module.exports** 之间的区别很难分清，一个简单的处理方法，就是放弃使用 **exports**，只使用 **module.exports**。

#### 3. require命令

##### 1. 基本用法

> **require**命令的基本功能是，读入并执行一个JavaScript文件，然后返回该模块的**module.exports**对象。如果没有发现指定模块，会报错。



##### 2. 加载规则

- 后缀名默认为 **.js**

```
var foo = require('foo');
//  等同于
var foo = require('foo.js');
```

- 如果参数字符串**以“/”开头（linux）或者以 “D:/”盘符开头（windows）**，则表示加载的是一个位于绝对路径的模块文件。比如，**require('/home/marco/foo.js')** 将加载 **/home/marco/foo.js** 
- 如果参数字符串**以“./”开头**，则表示加载的是一个位于**相对路径**（跟当前执行脚本的位置相比）的模块文件。比如，require('./circle') 将加载当前脚本同一目录的 circle.js
- 如果参数字符串**不以“./“或”/“开头**，则表示加载的是一个**默认提供的核心模块**（位于Node的系统安装目录中），或者一个位于各级node_modules目录的**已安装模块**（全局安装或局部安装）。
- 如果参数字符串**不以“./“或”/“开头，而且是一个路径**，比如 **require('example-module/path/to/file')**，则将先找到 example-module 的位置，然后再以它为参数，找到后续路径。
- 如果指定的模块文件没有发现，Node会尝试为文件名添加**.js、.json、.node**后，再去搜索。.js件会以文本格式的JavaScript脚本文件解析，.json文件会以JSON格式的文本文件解析，.node文件会以编译后的二进制文件解析。



##### 3. 目录的加载规则

通常，我们会把相关的文件会放在一个目录里面，便于组织。这时，最好为该目录设置一个入口文件，让 **require** 方法可以通过这个入口文件，加载整个目录。



在目录中放置一个 **package.json** 文件，并且将入口文件写入 **main** 字段。下面是一个例子。

```
// package.json
{ 
  "name" : "some-library",
  "main" : "./lib/some-library.js" 
}
```



**require** 发现参数字符串指向一个目录以后，会自动查看该目录的 **package.json** 文件，然后加载 **main** 字段指定的入口文件。如果 **package.json** 文件没有 **main** 字段，或者根本就没有 **package.json** 文件，则会加载**该目录下的index.js 文件 或者 index.json 文件 或者 index.node 文件**。



##### 4. 模块的加载机制



CommonJS 模块的加载机制是，输出拷贝。也就是说，一旦输出一个值，模块内部的变化就影响不到这个值。请看下面这个例子。



```
// lib.js
var counter = 3;
function incCounter() {
  counter++;
}
module.exports = {
  counter: counter,
  incCounter: incCounter,
};
```



上面代码输出内部变量counter和改写这个变量的内部方法incCounter。

然后，加载上面的模块。



```
// main.js
var counter = require('./lib').counter;
var incCounter = require('./lib').incCounter;
console.log(counter);  // 3
incCounter();
console.log(counter); // 3
```



上面代码说明，counter输出以后，lib.js模块内部的变化就影响不到counter了。

## 五、Node - 内置模块

### 1.URL

> url 模块，专门用来处理 url 相关的操作。

1. `url.parse(urlString[, parseQueryString])`
   * 第一个参数是url字符串
   * 第二个参数是布尔值，true表示返回参数对象
2. `url.format(urlObject)`

```js
{
  protocol: 'http:',
  slashes: true,
  auth: null,
  host: 'localhost:3000',
  port: '3000',
  hostname: 'localhost',
  hash: '#hash',
  search: '?name=zhagnsan&age=18',
  query: 'name=zhagnsan&age=18',
  pathname: '/foo/bar',
  path: '/foo/bar?name=zhagnsan&age=18',
  href: 'http://localhost:3000/foo/bar?name=zhagnsan&age=18#hash'
}
```



> WHATWG 组织规定了一套新的 url 规范
>
> 在 javascript 中，提供了一个 URL 构造函数，可以直接去使用，不需要引入
>
> 实例化一个url对象，返回的是新标准的url组成对象

```js
const urlStr = 'http://localhost:3000/foo/bar?name=zhagnsan&age=18#hash'
const urlObj = new URL(urlStr)

{
    href: 'http://localhost:3000/foo/bar?name=zhagnsan&age=18#hash',
    origin: 'http://localhost:3000',
    protocol: 'http:',
    username: '',
    password: '',
    host: 'localhost:3000',
    hostname: 'localhost',
    port: '3000',
    pathname: '/foo/bar',
    search: '?name=zhagnsan&age=18',
    searchParams: URLSearchParams { 'name' => 'zhagnsan', 'age' => '18' },
    hash: '#hash'
  }

//searchParams 取值需要通过 get 方法
console.log(urlObj.searchParams.get('age'))
//直接对 URL 的实例做 toString() 来得到 url字符串
console.log(urlObj.toString())
```



### 2.querystring 查询字符串

```js
/**
 * 对一个查询字符串，解析成查询对象
 * 
 * querystring.parse(str[, sep[, eq]])
 * 
 *  key1=value1&key2=value2 => { key1: value1 , key2: value2 }
 * 
 *  sep   规定 键值对之间的分隔符是什么，默认是 &
 * 
 *  eq    规定 键值之间的分隔符是什么，默认是 =
 */


/**
 * 将查询对象转换成查询字符串
 * 
 * querystring.stringify(obj[, sep[, eq]])
 * 
 * sep   规定 键值对之间的分隔符是什么，默认是 &
 * 
 * eq    规定 键值之间的分隔符是什么，默认是 =
 */
```



### 3.path 模块 专门处理路径相关

- `path.resolve('./day01-homework','./utils/index.js')`

- 结合成一个绝对路径返回

```javascript
const path = require('path')
const filePath=path.resolve('./day01-homework','./utils/index.js')
console.log(filePath)
```



- `path.join('./day01-homework','./utils/index.js')`

- 仅仅是把路径拼接起来

  ```javascript
  const path = require('path')
  const filePath=path.join('./day01-homework','./utils/index.js')
  console.log(filePath)
  ```

- `path.join()`与`path.resolve()`有什么区别？

  - 返回值不同，**path.resolve** 总是返回一个绝对路径，而**path.join**只是简单的将路径拼接。
  - 对于以 **/** 开始的路径片段，**path.join** 只是简单的将该路径片段进行拼接，而 **path.resolve** 将以 **/** 开始的路径片段作为根目录，在此之前的路径将会被丢弃

1. `__dirname`和`__filename`

   - `__dirname:`   当前模块的目录名的绝对路径
   - `__filename:`   当前模块的文件名

## 六、EXPRESS

### 一、前言

> 基于 Node.js 平台，快速、开放、极简的 Web 开发框架



#### 1.Node 相关的框架

1. express
2. koa
3. egg
4. thinkjs
5. adonisjs
6. nestjs

  .....

### 二、安装

```bash
$ npm install express
```



### 三、使用

- 创建index文件

```js
const express = require('express'); //引入express
const app = express();//注册express实例 

//路由信息（if有页面访问3000端口服务器）
app.get('/', function(req, res) {
  res.send('hello world');
});

//监听端口
app.listen(3000, () => {
  console.log('服务启动成功！ http://localhost:3000');
});
```



> **app** 是 express 的实例。
>
> **METHOD** 是小写的 HTTP 请求方式（GET、POST、PUT、PATCH、DELETE等）。
>
> **PATH** 是请求路径。（以 / 开头）
>
> **HANDLER** 是当路由匹配时执行的函数。

### 四、路由携带参数的获取

#### 1.get请求

`req.query`  可以直接用，是get方式参数对象

#### 2.post请求

`req.body`  不可以直接使用，要在用之前使用中间件

`app.use(express.json())`

`app.use(express.urlencoded(extended:true))`

#### 3.路由的动态参数

```js
//"http://localhost:3000/good/xxx"都可以进去/good/：abc这个路由中
app.get("/good/:abc",(req,res)=>{
  //使用req.params 来获取 =>{abc:xxx}
  res.send(`${req.params.abc}的详情页`)
})
```

