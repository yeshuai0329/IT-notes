# Object

## 1、概念：

1. `JavaScript` 中的构造函数，构造函数创建一个对象包装器。

## 2、描述：

​		在 `JavaScript` 中，几乎所有的对象都是 `Object` 类型的实例。他们都会从 `Object.prototype` 继承属性和方法。`Object` 构造函数为给定值创建一个对象包装器。`Object` 构造函数，会根据给定参数创建对象。

- 如果给定值是 `null` 或 `undefined`，将会创建并返回一个空对象。
- 如果传进去的是一个基本类型的值，则会构造其包装类型的对象
- 如果传进去的是引用类型的值，仍然会返回这个值，经他们复制的变量保有和源对象相同的引用地址。

## 3、Object  构造函数的属性

### 3.1、`Object.prototype`  

- 可以给所有 Object 的类型的对象添加属性。

### 3.2、`Object.assign()` 

- 通过一个对象或者多个对象来创建一个新的对象。

### 3.3、`Object.create()`

- 使用制定原型对象创建一个新的对象。

### 3.4、`Object.defineProperty()`

- 该方法直接在一个对象上定义一个新的属性，或者修改一个对象的现有属性，并返回此对象。
- 通过赋值操作添加的普通属性是可枚举的，在枚举对象属性时会被枚举到（`for...in)` 或 `Object.keys`方法）
- 默认情况下，使用 `Object.defineProperty()` 添加的属性值是不可修改（immutable）的。

- `Object.defineProperty(obj, prop, descriptor)`
  - `obj`  要定义属性的对象。
  - `prop`  要添加或者修改的属性的名称
  - `descriptor`  要定义或修改的属性的描述符。

```javascript
const object1 = {};
Object.defineProperty(object1, 'property1', {
  value: 42,
  writable: false
});
// 描述符的可选键值对
{
	configurable: 默认false， 为true时，该属性的描述符才能被改变，同时该属性才能从对应的对象上删除。
  writable: 默认 false， 为true时，该属性才被赋值运算符修改。
  enumerable: 默认 false， 为true时，该属性才能被枚举。
}
```

### 3.5、`Object.defineProperties()`

- 给对象添加多个属性并分别指定它们的配置，并返回该对象。

```javascript
var obj = {};
Object.defineProperties(obj, {
  'property1': {
    value: true,
    writable: true
  },
  'property2': {
    value: 'Hello',
    writable: false
  }
  // etc. etc.
});
```

### 3.6、`Object.entries()`

- 返回给定对象自身可枚举属性的 `[key, value]` 数组。

```javascript
const object1 = {
  a: 'somestring',
  b: 42
};

Object.entries(object1) // [[a, 'somestring'],[b, 42]]

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}
```

### 3.7、`Object.keys()`

- 返回一个包含所有给定对象**自身**可枚举属性名称的数组。

### 3.8、`Object.values()`

- 返回给定对象自身可枚举值的数组。

















