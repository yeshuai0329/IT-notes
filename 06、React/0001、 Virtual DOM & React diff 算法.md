# React diff 算法

> ​		React 提供的声明式 API 让开发者可以在对 React 的底层实现并不了解的情况下编写应用。本文描述了在实现 React 的 “diffing” 算法过程中所作出的设计决策，以保证组件更新可预测，且在繁杂业务场景下依然保持应用的高性能。

## 1、设计动机

- 当组件某一时间点调用 react 的 render() 方法以后，会创建一棵 React 元素的 dom 树。 在下一次state 或者 props 发生改变的时候，render() 会被重新调用，生成一棵新的 dom 树。React 需要根据两棵树之间的差别来判断如何高效的更新 UI ，以保证当前 UI 与最新的 dom 树保持同步。
- React 需要根据两棵树之间的差别来判断如何高效的更新 UI ，根据现有最优算法，复杂程度依然需要0(n^3) , 其中 n 是 dom 树种元素的数量。（此算法耗时很长，对dom 树的改动最小。）
- 于是 React 在以下两个假设的基础之上提出了一套0(n) 的算法方案：
  1. 两个不同类型的元素会产生出不同的树；
  2. 开发者可以通过设置 `key` 属性，来告知渲染哪些子元素在不同的渲染下可以保存不变；

## 2、Diff 算法

> ​		当对比两棵 dom 树时，React 首先比较两棵树的根节点。不同类型的根节点元素会有不同的形态。对比不同类型的元素

### 2.1 对比不同类型的元素

- 当根节点为不同类型的元素的时候，React 会拆卸原有的树并建立新的树。举个例子，当一个元素从 `<a>` 变成 `<img>`，从 `<Article>` 变成 `<Comment>`，或从 `<Button>` 变成 `<div>` 都会触发一个完整的重建流程。

- 当卸载一棵树时，对应的 DOM 节点也会被销毁。组件实例将执行 `componentWillUnmount()` 方法。当建立一棵新的树时，对应的 DOM 节点会被创建以及插入到 DOM 中。组件实例将执行 `UNSAFE_componentWillMount()` 方法，紧接着 `componentDidMount()` 方法。所有与之前的树相关联的 state 也会被销毁。

  ```javascript
  <div>
    <Counter />
  </div>
  
  <span>
    <Counter />
  </span>
  ```

  React 会销毁 `Counter` 组件并且重新装载一个新的组件。

### 2.2 对比同类型元素：

- 当对比两个相同类型的 React 元素时，React 会保留 DOM 节点，仅比对及更新有改变的属性。比如：
- 通过对比这两个元素，React 知道只需要修改 DOM 元素上的 `className` 属性。

```javascript
<div className="before" title="stuff" />

<div className="after" title="stuff" />
```

- 当更新 `style` 属性时，React 仅更新有所更变的属性。比如：
- 通过对比这两个元素，React 知道只需要修改 DOM 元素上的 `color` 样式，无需修改 `fontWeight`。

```javascript
<div style={{color: 'red', fontWeight: 'bold'}} />

<div style={{color: 'green', fontWeight: 'bold'}} />
```

- 在处理完当前节点之后，React 继续对子节点进行递归。

### 2.3 对比同类型的组件元素：

- 当一个组件更新时，组件实例会保持不变，因此可以在不同的渲染时保持 state 一致。React 将更新该组件实例的 props 以保证与最新的元素保持一致，并且调用该实例的 `UNSAFE_componentWillReceiveProps()`、`UNSAFE_componentWillUpdate()` 以及 `componentDidUpdate()` 方法。
- 下一步，调用 `render()` 方法，diff 算法将在之前的结果以及新的结果中进行递归。

### 2.4  子节点进行递归：no key

- 默认情况下，当递归 DOM 节点的子元素时，React 会同时遍历两个子元素的列表；当产生差异时，生成一个 mutation。
- 在子元素列表末尾新增元素时，更新开销比较小。比如：

```javas
<ul>
  <li>first</li>
  <li>second</li>
</ul>

<ul>
  <li>first</li>
  <li>second</li>
  <li>third</li>
</ul>
```

**当没有key 的时候 React 会先匹配两个 `<li>first</li>` 对应的树，然后匹配第二个元素 `<li>second</li>` 对应的树，最后插入第三个元素的 `<li>third</li>` 树。**

- 如果只是简单的将新增元素插入到表头，那么更新开销会比较大。比如：

```javascript
<ul>
  <li>Duke</li>
  <li>Villanova</li>
</ul>

<ul>
  <li>Connecticut</li>
  <li>Duke</li>
  <li>Villanova</li>
</ul>
```

**没有key的时候， React 并不会意识到应该保留 `<li>Duke</li>` 和 `<li>Villanova</li>`，而是会重建每一个子元素。这种情况会带来性能问题。**

### 2.5  子节点进行递归：have key

> ​		为了解决上述问题，React 引入了 `key` 属性。当子元素拥有 key 时，React 使用 key 来匹配原有树上的子元素以及最新树上的子元素。以下示例在新增 `key` 之后，使得树的转换效率得以提高：

- 这个 key 不需要全局唯一，但在列表中需要保持唯一。
- 你也可以使用元素在数组中的下标作为 key。这个策略在元素不进行重新排序时比较合适，如果有顺序修改，diff 就会变慢。
- 当基于下标的组件进行重新排序时，组件 state 可能会遇到一些问题。由于组件实例是基于它们的 key 来决定是否更新以及复用，如果 key 是一个下标，那么修改顺序时会修改当前的 key，导致非受控组件的 state（比如输入框）可能相互篡改，会出现无法预期的变动。

```javascript
<ul>
  <li key="2015">Duke</li>
  <li key="2016">Villanova</li>
</ul>

<ul>
  <li key="2014">Connecticut</li>
  <li key="2015">Duke</li>
  <li key="2016">Villanova</li>
</ul>
```

**现在 React 知道只有带着 `'2014'` key 的元素是新元素，带着 `'2015'` 以及 `'2016'` key 的元素仅仅移动了**

## 3、diff 算法面试问题：

### 3.1 说一下虚拟dom？

- Virtual DOM 是一种编程概念。
- UI 以一种理想化的，或者说“虚拟的”表现形式被保存于内存中。
- 并通过如 ReactDOM 等类库使之与“真实的” DOM 同步。这一过程叫做协。调

### 3.2 说一下react diff 算法？

-  `diff 算法`是` React `在某一时间会调用`render()`渲染函数，生成`React` 元素节点的 `dom` 树，当组件的 `state` 或者是 `props` 发生改变，重新调用`render()` 渲染函数，返回一棵不同的树。`React` 需要基于这两棵树之间的差别来判断如何高效的更新 UI，以保证当前 UI 与最新的树保持同步。

### 3.3 说一下 diff 算法 key 的作用？

- diff 算法中使用的 key 是用来做标识符，提高 diff 算法的对比效率 。
- 当标识 key 以后，react 就知道具体那个key 发生了改变，对 dom 元素做增删改，不会重绘所有子元素。

### 3.4 说一下 diff 算法 key 如果没有会怎么样？

- 开发环境会提示报错缺少 key 。
- 会导致子元素进行重绘，重走生命周期。消耗多余的性能。

### 3.5 说一下 diff 算法 key 如果使用 index 合适吗？

- 这个 key 不需要全局唯一，但在列表中需要保持唯一。
- 不推荐使用 index 下标来充当子元素的 key。元素在进行重新排序时，如果有顺序修改，diff 就会变慢。
- 当子元素中含有非受控组件的时候，导致非受控组件的 state（比如输入框）可能相互篡改，会出现无法预期的变动。















