> 推荐使用 Typora 观看笔记，可以选择文件/大纲试图，更清晰的看清笔记结构，快速定位知识点！
>
> 本文档持续更新～

- 选择文件夹预览，可以呈现文件夹结构

> ![image-20220905231818402](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220905231818402.png)

- 选择具体的markdown文件

>![image-20220905232027325](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220905232027325.png)

- 再点击左上角切换大纲视图，就可以预览对应的markdown 的大纲预览了

> ![image-20220905232255568](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220905232255568.png)

# JavaScript 征服之路笔记-每日一题

### 001、变量提升、声明提升

```javascript
var name = 'null'
var age = 38
var length = 10
var say = 'speak'

function demo(arg) {
  console.log(obj1, arg)
  function arg() {}
  var obj1 = {
    name: '熊大',
    age: 88,
    say: function() {
      return (name,age) => {
        console.log(`我是${this.name},年龄：${age}`)
      }
    }
  }
  var length
  console.log(length) 
  length = 18
  console.log(length) 
  var obj2 = {
    name: '熊二',
    age: 58,
    say: obj1.say
  }
  if (console.log('undefined') || (!!'' + '1' && typeof typeof null && !!length)) {
    setTimeout(() => {
      obj1.say()('熊三', 88)
    })
    obj2.say()('光头强', 77)
  } else {
    setTimeout(() => {
      obj2.say()('肥波', 199)
    })
  }
}

new Promise((resolve) => {
  resolve(188)
}).then(age => {
  obj2.say()(('光头强', age))
})

demo(18)

    7// undefined, function arg() {}
    19// undefined
    21// 18
    27// udefined
    31// 我是熊二,年龄77
    29// 我是熊大,年龄88
    42// 报错： obj2 is  not defined

// 分析重点
// ！ 使用 var 定义的变量，会有变量提升，全局变量会提升到全局作用域的顶端，函数内的变量会提升到函数作用域的顶端
// ！ 使用函数声明的函数，全局函数会被提升到全局作用域的顶端，函数内的函数声明会提升到函数作用域的顶端   
// 预编译阶段做什么：
// 1.全局作用域
// 		- 查找全局的变量声明/函数声明，提升到作用域的顶端，如果函数声明和变量声明一样，则函数声明（函数是第一公民）会覆盖变量声明。
// 2.函数作用域内
//		-	查找函数内的变量声明，参数赋值，
//    - 函数内的函数声明，会提升到作用域的顶端，函数声明如果与变量声明一致，函数声明会覆盖变量声明。
```



### 002、





































