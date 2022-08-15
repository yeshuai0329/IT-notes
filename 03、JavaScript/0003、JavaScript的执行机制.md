## 一、前言
>     众所周知，浏览器的JavaScript**解析引擎是单线程**的，也就是说每次只能执行一个任务，其他任务都得按照顺序排队等待被执行，只有当前任务执行完成以后才可以执行下一个任务。
## 二、JavaScript的任务分为同步任务和异步任务
1.	同步任务
```js
var t = Date.now();

console.log('Hi');

if (true){ console.log(123) }
```
2.异步任务
```js
setTimeout(function() { console.log(‘b’); }, 10)

dom.onclick = function () { alert(123) }

$.ajax({
    url: 'https://www.baidu.com',
    type: 'get',
    data: 'user=xiaocuo&pass=123456',
    dataType: 'json',
    success: function (d){
        console.log(d);
    }
});

var promise = new Promise(function(resolve, reject) {//这里是同步任务
    console.log(3);
    resolve();
})
promise.then(function() {//这里是异步任务
    console.log(4);
})
```
##  三、事件循环宏观流程介绍
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809100527541.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NzA3Njk4OQ==,size_16,color_FFFFFF,t_70)
步骤：
1.JavaScript代码自上而下一次依次解析
2.当遇见同步代码的时候直接扔进  **Call Stack  (调用栈)**  里，遇见异步代码的时候直接扔进  **webcore**  模块中
3.扔进**Call Stack  (调用栈)**里的代码依次执行，扔进**webcore**  模块中的代码依次执行把异步的结果扔进他task    queue，并不会直接执行
4.等待**Call Stack  (调用栈)**中所有的同步任务执行完毕以后，task queue 里的异步回调才会扔进**Call Stack  (调用栈)**，依次执行。

-	当一个脚本执行的时候，js引擎会解析这段代码，并将其中的同步代码按照执行顺序加入调用栈中，然后从头开始执行。
-	js引擎遇到一个异步事件后并不会一直等待其返回结果，而是会将这个事件挂起(其他模块进行处理)，继续执行执行栈中的其他任务。当一个异步事件返回结果后，js会将这个事件加入到事件队列。
-	被放入事件队列不会立刻执行其回调，而是等待当前执行栈中的所有任务都执行完毕， 主线程处于闲置状态时，主线程会去查找事件队列是否有任务。如果有，那么主线程会从中取出排在第一位的事件，并把这个事件对应的回调放入执行栈中，然后执行其中的同步代码...，如此反复，这样就形成了一个无限的循环。这个过程被称为“事件循环（Event Loop）”。

## 四、事件循环微观流程介绍
-	以上的事件循环过程是一个宏观的表述，实际上因为异步任务之间并不相同，因此他们的执行优先级也有区别。
- 不同的异步任务被分为两类：微任务（micro task）和宏任务（macro task）。
```js
macro-task： 整体代码script、setTimeout、setInterval......
micro-task：Promises、Object.observe......
```
- 在一个事件循环中，异步事件返回结果后会被放到一个任务队列中。根据这个异步事件的类型，实际上会被放到宏任务队列或者微任务队列。当前调用栈执行完毕时会优先处理所有微任务队列中的事件，然后再去宏任务队列中取出一个事件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809102628375.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NzA3Njk4OQ==,size_16,color_FFFFFF,t_70)