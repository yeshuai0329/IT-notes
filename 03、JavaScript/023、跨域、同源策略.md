### 防抖节流

#### 一、防抖                                                                                                                                                                                                                                                                      

>      概念：用户触发时间过于频繁，只要最后 一次事件的操作，通过`setTimeout`的方式，在一定时间内的多次触发变成 一次触发。

```javascript
// 防抖函数
let debounce = function(fn, delay) {
    let t = null
    return function() {
        if (t !== null) {
            clearTimeout(t)
        }
        t = setTimeout(() => {
            fn.apply(this, arguments)
        },delay)
    }
}
```

#### 二、节流

>      概念：用户先出发 一次，一定时间后才能 再触发

```javascript
let throttle = function (fn, delay) {
    let begin = 0 
    return function() {
        let cur = new Date().getTime()
        console.log(cur - begin)
        if (cur - begin > delay) {
            fn.apply(this, arguments)
            begin = cur
        }
    }
}
```



