# Promise

## 1.概述

> ​		浏览器 JavaScript 引擎是单线程的，避免耗时的任务阻塞线程。所以需要异步编程。
>
> ​		Promise 是异步编程的解决方案，从语法上讲，Promise是一个对象，可以获取异步操作的信息。

## 2.目的 

- 避免回调地狱的问题
- Promise 对象提供了简介的Api， 是的异步操作更加的容易。

## 3.Promise的 三种状态

1. `pendding`   正在处理

   ```javascript
   console.log(new Promise((resovle, reject) => {}))
   ```

   打印

   ![image-20220811091446800](C:\Users\YE\Desktop\front-notes\assets\image-20220811091446800.png)

2. `fulfilled`    成功

   ```javascript
   console.log(new Promise((resovle, reject) => { resovle()}))
   ```

   打印

   ![image-20220811091600792](C:\Users\YE\Desktop\front-notes\assets\image-20220811091600792.png)

3. `rejected`    失败

   ```javascript
   console.log(new Promise((resovle, reject) => { reject()}))
   ```

   打印

   ![image-20220811091855984](C:\Users\YE\Desktop\front-notes\assets\image-20220811091855984.png)

## 4. Promise 的微任务执行机制

看代码

```javascript
new Promise((resovle, reject) => {
    // Promise 这个区域的代码是同步代码
    // Promise 的状态只能改变一次，也就是说这个区域只能写 resovle() 或者 reject() 一个
    console.log('b')
        resovle('执行成功后的结果')
        // reject('执行失败的原因')
})
    .then(
    	// then 函数内的代码会放进微任务队列
        result => console.log(result),
        reason => console.log(reason)
	)
    .then(
        result => console.log(result),
        reason => console.log(reason)
    )
console.log('a')
// 此代码执行后打印顺序为 'b' -> 'a' -> '执行成功后的结果' -> undefined
// 原因是因为 js代码自上而下执行，当遇见同步代码的时候直接放进调用栈执行，遇见异步代码的时候放进异步模块执行，异步代码执行完毕会把结果放进异步结果的任务队列里，当调用栈内所有的同步任务执行完，再从异步结果任务队列里轮询放进调用栈执行。
```

执行结果

![image-20220811093340687](C:\Users\YE\Desktop\front-notes\assets\image-20220811093340687.png)

## 5. 微任务与宏任务执行机制

>  		js 先执行微任务，再执行宏任务，then() 方法是微任务 ， setTimeout() 是宏任务。

案例1：

```javascript
setTimeout(() => {
    console.log('setTimeout')
})

new Promise((resovle, reject) => {
    // Promise 这个区域的代码是同步代码
    // Promise 的状态只能改变一次，也就是说这个区域只能写 resovle() 或者 reject() 一个
    console.log('b')
        resovle('执行成功后的结果')
        // reject('执行失败的原因')
})
    .then(
        result => console.log(result),
        reason => console.log(reason)
	)
    .then(
        result => console.log(result),
        reason => console.log(reason)
    )
console.log('a')
```

![image-20220811094304709](C:\Users\YE\Desktop\front-notes\assets\image-20220811094304709.png)

案例2：

```javascript
setTimeout(() => {
    console.log('setTimeout1')
})

new Promise((resovle, reject) => {
    console.log('b')
        resovle('执行成功后的结果')
    setTimeout(() => {
    	console.log('setTimeout2')
	})
})
    .then(
        result => console.log(result),
        reason => console.log(reason)
	)
    .then(
        result => console.log(result),
        reason => console.log(reason)
    )
console.log('a')
```

打印

![image-20220811094457577](C:\Users\YE\Desktop\front-notes\assets\image-20220811094457577.png)

案例3：

```javascript
setTimeout(() => {
    console.log('setTimeout1')
})

new Promise((resovle, reject) => {
    console.log('b')
    setTimeout(() => {
    	console.log('setTimeout2')
        resovle('执行成功后的结果')
	})
})
    .then(
        result => console.log(result),
        reason => console.log(reason)
	)
    .then(
        result => console.log(result),
        reason => console.log(reason)
    )
console.log('a')
```

打印

![image-20220811094703575](C:\Users\YE\Desktop\front-notes\assets\image-20220811094703575.png)

案例4:

```javascript
setTimeout(() => {
    console.log('setTimeout1')
})

new Promise((resovle, reject) => {
    console.log('b')
    setTimeout(() => {
        resovle('执行成功后的结果')
    	console.log('setTimeout2')
	})
})
    .then(
        result => console.log(result),
        reason => console.log(reason)
	)
    .then(
        result => console.log(result),
        reason => console.log(reason)
    )
console.log('a')
```

打印

![image-20220811094840487](C:\Users\YE\Desktop\front-notes\assets\image-20220811094840487.png)

## 6.Promise的单一状态与状态中转

```javascript
let p1 = new Promise((resovle, reject) => {
    resovle('成功')
})

new Promise((resovle, reject) => {
    resovle(p1)
})
    .then(
        result => console.log(`这是成功的状态----${result}`),
        reason => console.log(`这是失败的状态----${reason}`)
	)
console.log('a')
```

打印

![image-20220811095307607](C:\Users\YE\Desktop\front-notes\assets\image-20220811095307607.png)

## 7.then()方法

> ​		then 是 Promise 的成功和失败情况的回调函数。

```javascript
new Promise((resovle, reject) => {
    resovle('大帅B')
})
.then() // 如果then没有对成功或者失败的状态进行处理，那么成功或者失败的原因向下传递
.then(
    result => {
        console.log(`这是成功的状态----${result}`) 
    },  // 对成功状态的处理，result成功的结果
    reason => {
        console.log(`这是失败的状态----${reason}`)
    }  // 对失败状态的处理，reason失败的原因
)
```

> ​	每个 then 函数的返回值也是一个Promise

```javascript
let p1 = new Promise((resovle, reject) => {
    resovle('大帅B')
})
let p2 = p1.then(
    result => {
        console.log(`这是成功的状态----${result}`) 
    },  // 对成功状态的处理，result成功的结果
    reason => {
        console.log(`这是失败的状态----${reason}`)
    }  // 对失败状态的处理，reason失败的原因
)
setTimeout(() => {
    console.log(p1)
    console.log(p2)
})
```

打印

![image-20220811100740338](C:\Users\YE\Desktop\front-notes\assets\image-20220811100740338.png)