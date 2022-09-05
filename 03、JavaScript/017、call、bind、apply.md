### call、apply、bind

* call、apply、bind都是Function.prototype的方法，所以每个函数都有call、apply、bind属性。
* call、apply、bind的作用都可改变函数内部的this指向

#### 一、call

- call()的作用
  - 改变了原来函数的this指向
  - 绑定函数内部的this指向，this指向obj
  - 没有返回值，会执行当前函数。
  - 传参方式：call()里的第一个参数一个对象，后边参数是用逗号隔开的列表。
    - `fn.call(obj,2,3,4,5)`

#### 二、apply

- apply()的作用
  - 改变了原来函数的this指向
  - 绑定函数内部的this指向，this指向obj
  - 没有返回值，会执行当前函数。
  - 传参方式：apply()里只有两个参数，第一个参数是一个对象，第二个参数是一个数组
    - `fn.apply(obj,[2,3,4,5])`

#### 三、bind

- bind(obj)的作用

  - 改变了原来函数的this指向

  - 绑定函数内部的this指向，this指向obj

  - 返回值是调用bind方法的函数体本身，不会执行当前函数,要调用一下f()。

```javascript
var obj={
    a:1,
    b：2
}
function fn(){
    console.log(this)
}
var f = fn.bind(obj)
f()//{a:1,b:2}
```
**总结**

1. **call、apply和bind都可以改变函数的this指向**
2. **call、apply和bind第一个参数的是this要指向的对象**
3. **call、apply和bind都可以后续为函数传参，apply是将参数并成一个数组，call和bind是将参数依次列出。**
4. **call、apply都是直接调用，bind生成的this指向改变函数需要手动调用。**