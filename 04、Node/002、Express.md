#### 一、前言

> 基于 Node.js 平台，快速、开放、极简的 Web 开发框架



##### 1.Node 相关的框架

1. express
2. koa
3. egg
4. thinkjs
5. adonisjs
6. nestjs

  .....

#### 二、安装

```bash
$ npm install express
```



#### 三、使用

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

#### 四、路由携带参数的获取

##### 1.get请求

`req.query`  可以直接用，是get方式参数对象

##### 2.post请求

`req.body`  不可以直接使用，要在用之前使用中间件

```
app.use(express.json())
app.use(express.urlencoded(extended:true))
```

##### 3.路由的动态参数

```js
//"http://localhost:3000/good/xxx"都可以进去/good/：abc这个路由中
app.get("/good/:abc",(req,res)=>{
  //使用req.params 来获取 =>{abc:xxx}
  res.send(`${req.params.abc}的详情页`)
})
```