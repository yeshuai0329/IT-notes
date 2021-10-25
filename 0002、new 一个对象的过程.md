# new 一个对象的过程

## 1、new 以后我们的到了什么？

> 直观的感觉，当我们new一个构造函数，得到的实力继承了 `构造器的属性` 以及`原型上的属性和方法`

```javascript
// ES5构造函数
let Parent = function (name, age) {
    this.name = name;
    this.age = age;
};
Pepole.prototype.sayName = function () {
    console.log(this.name);
};

const child = new Parent('李四'， 23)
child.sayName() // 李四
```

```javascript
//ES6 class类
class Parent {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    sayName() {
        console.log(this.name);
    }
};
const child = new Parent('李四', 23);
child.sayName() // 李四
```

​		**比较直观的感觉，当我们new 一个构造函数，得到的实例继承了 `构造器的构造属性`  和 `原型上的属性`。**

## 2、new 的过程中发生了什么？

**当我们new构造器有三个步骤：**

- 创建一个空对象，将它的引用赋给 this , 继承函数的原型。
- 通过 this 将属性和方法添加至这个对象。
- 最后返回 this 指向新的对象， 也就是这个实例。

```javascript
// ES5构造函数
let Parent = function (name, age) {
    //1.创建一个新对象，赋予this，这一步是隐性的，
    // let this = {};
    //2.给this指向的对象赋予构造属性
    this.name = name;
    this.age = age;
    //3.如果没有手动返回对象，则默认返回this指向的这个对象，也是隐性的
    // return this;
};
const child = new Parent();
```

​		**现在应该知道 new 过程中会`新建对象`，此对象会继承`构造器的原型`与`原型上的属性`，最后它会被作为`实例`返回这样一个过程。**

## 3、简单实现一个new的方法

```javascript
const customNew = function (Parent, ...rest) {
  // 1. 以构造器的 prototype 为原型，创建对象。
  const child = Object.create(Parent.prototype)
  // 2. 将 this 和调用参数传给构造器执行
  const result = Parent.apply(child, rest)
  // 3.如果构造器没有手动返回对象，则返回第一步的对象
  return typeof result  === 'object' ? result : child;
}

//创建实例，将构造函数Parent与形参作为参数传入
const child = customNew(Parent, 'echo', 26);
child.sayName() //'echo';
```



