# JavaScript 征服之路笔记

> 推荐使用 Typora 观看笔记，可以选择大纲试图，更清晰的看清笔记结构，快速定位知识点！
![image-20220901194209193](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220901194209193.png)

## 01、HTML

### 001、Doctype作用? 严格模式与混杂模式如何区分？它们有何意义?

- `<!DOCTYPE>` 声明位于文档中的最前面，处于 `<html>` 标签之前。告知浏览器的解析器， 用什么文档类型 规范来解析这个文档
- 严格模式的排版和 `JS` 运作模式是 以该浏览器支持的最高标准运行
- 在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。 `DOCTYPE`不存在或格式不正确会导致文档以混杂模式呈现

### 002、XHTML 和 HTML 有什么区别？

- 一个是功能上的差别
  - 主要是`XHTML`可兼容各大浏览器、手机以及`PDA`，并且浏览器也能快速正确地编译网页
- 另外是书写习惯的差别
  - `XHTML` 元素必须被正确地嵌套，闭合，区分大小写，文档必须拥有根元素

### 003、html5有哪些新特性？

- 语义化的标签： `header`、`footer`、`article`、`nav`、`section`
- 新增加了选择器： `document.querySelector` 和 `document.querySelectAll`
- 媒体播放标签： `audio`、 `video`
- 双全工通信协议L: `websocket`
- 跨窗口通信： `PostMessage`
- 绘画： `canvas`
- `Form Data` 对象
- 地理位置：` Geolocation`
- 增强了表单控件类型： `date`、`time`、`email`、`url`、
- 离线存储： `manifest`
- 拖放API:  `Drag`  和 `drop`

### 004、行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

- 行内元素有：`a b span img input select strong`
- 块级元素有：`div ul ol li dl dt dd h1 h2 h3 h4… p`
- 空元素：`<br> <hr> <img> <input> <link> <meta>`

### 005、行内元素和块级元素有什么区别？

- 行内元素不可以设置宽高，不独占一行
- 块级元素可以设置宽高，独占一行

### 006、Canvas和SVG有什么区别？

- `svg`绘制出来的每一个图形的元素都是独立的`DOM`节点，能够方便的绑定事件或用来修改。`canvas`输出的是一整幅画布
- `svg`输出的图形是矢量图形，后期可以修改参数来自由放大缩小，不会失真和锯齿。而`canvas`输出标量画布，就像一张图片一样，放大会失真或者锯齿

### 007、viewport

```html
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
    // width    设置viewport宽度，为一个正整数，或字符串‘device-width’
    // device-width  设备宽度
    // height   设置viewport高度，一般设置了宽度，会自动解析出高度，可以不用设置
    // initial-scale    默认缩放比例（初始缩放比例），为一个数字，可以带小数
    // minimum-scale    允许用户最小缩放比例，为一个数字，可以带小数
    // maximum-scale    允许用户最大缩放比例，为一个数字，可以带小数
    // user-scalable    是否允许手动缩放
```

### 008、meta 标签

```html
<meta charset=’utf-8′>    <!--声明文档使用的字符编码-->
<meta http-equiv=”X-UA-Compatible” content=”IE=edge,chrome=1″/>   <!--优先使用 IE 最新版本和 Chrome-->
<meta name=”description” content=”不超过150个字符”/>       <!--页面描述-->
<meta name=”keywords” content=””/>     <!-- 页面关键词-->
<meta name=”author” content=”name, email@gmail.com”/>    <!--网页作者-->
<meta name=”robots” content=”index,follow”/>      <!--搜索引擎抓取-->
<meta name=”viewport” content=”initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no”> <!--为移动设备添加 viewport-->
<meta name=”apple-mobile-web-app-title” content=”标题”> <!--iOS 设备 begin-->
<meta name=”apple-mobile-web-app-capable” content=”yes”/>  <!--添加到主屏后的标题（iOS 6 新增）
是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏-->
<meta name=”apple-itunes-app” content=”app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL”>
<!--添加智能 App 广告条 Smart App Banner（iOS 6+ Safari）-->
<meta name=”apple-mobile-web-app-status-bar-style” content=”black”/>
<meta name=”format-detection” content=”telphone=no, email=no”/>  <!--设置苹果工具栏颜色-->
<meta name=”renderer” content=”webkit”> <!-- 启用360浏览器的极速模式(webkit)-->
<meta http-equiv=”X-UA-Compatible” content=”IE=edge”>     <!--避免IE使用兼容模式-->
<meta http-equiv=”Cache-Control” content=”no-siteapp” />    <!--不让百度转码-->
<meta name=”HandheldFriendly” content=”true”>     <!--针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓-->
<meta name=”MobileOptimized” content=”320″>   <!--微软的老式浏览器-->
<meta name=”screen-orientation” content=”portrait”>   <!--uc强制竖屏-->
<meta name=”x5-orientation” content=”portrait”>    <!--QQ强制竖屏-->
<meta name=”full-screen” content=”yes”>              <!--UC强制全屏-->
<meta name=”x5-fullscreen” content=”true”>       <!--QQ强制全屏-->
<meta name=”browsermode” content=”application”>   <!--UC应用模式-->
<meta name=”x5-page-mode” content=”app”>   <!-- QQ应用模式-->
<meta name=”msapplication-tap-highlight” content=”no”>    <!--windows phone 点击无高亮
设置页面不缓存-->
<meta http-equiv=”pragma” content=”no-cache”>
<meta http-equiv=”cache-control” content=”no-cache”>
<meta http-equiv=”expires” content=”0″>
```

### 009、div+css的布局较table布局有什么优点？

- 项目更好维护，改版的时候更方便，只需要改css文件
- 页面加载速度会更快，结构化清晰，页面简洁
- 符合W3C规范，结构、表现、行为分离
- 易于SEO优化

### 010、img的alt与title有何异同？

- `title` ： 鼠标悬浮图片上的时候的提示信息
- `alt`:  用户网络不好的时候，图片加载失败的时候的对图片的描述信息。

### 011、strong与em的异同？

- `strong`:粗体强调标签，强调，表示内容的重要性
- `em`:斜体强调标签，更强烈强调，表示内容的强调点

### 012、简述一下src与href的区别？

- `src` 一般用于引用外部资源。
- `herf` 一般用于在站内当前文档和引用资源之间确立联系。
- `src`是`source`的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求`src`资源时会将其指向的资源下载并应用到文档内，例如`js`脚本，`img`图片和`frame`等元素

> <script src ="js.js"></script> 当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部

- `href`是`Hypertext Reference`的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，如果我们在文档中添加
- `<link href="common.css" rel="stylesheet"/>`那么浏览器会识别该文档为`css`文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用`link`方式来加载`css`，而不是使用`@import`方式

### 013、webp

- 一种网页图片格式，由谷歌开发推荐使用。
- 优点： 比普通图片格式体积更小，网页加载速度更快



## 02、CSS

### 001、css sprite是什么,有什么优缺点？

- 概念： 将多个小图片拼接到一个图片中。通过`background-position`和元素尺寸调节需要显示的背景图案。

- 优点：
  - 减少`HTTP`请求数，极大地提高页面加载速度
  - 增加图片信息重复度，提高压缩比，减少图片大小
  - 更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现
- 缺点：
  - 图片合并麻烦
  - 维护麻烦，修改一个图片可能需要从新布局整个图片，样式

### 002、 `link`与`@import`的区别？

1. `link`是`HTML`方式， `@import`是CSS方式
2. `link`最大限度支持并行下载，`@import`过多嵌套导致串行下载，出现`FOUC`(文档样式短暂失效)
3. `link`可以通过`rel="alternate stylesheet"`指定候选样式
4. 浏览器对`link`支持早于`@import`，可以使用`@import`对老浏览器隐藏样式
5. `@import`必须在样式规则之前，可以在css文件中引用其他文件
6. 总体来说：`link`优于`@import`

### 003、`display: none;`与`visibility: hidden`的区别？

- 共同点：
  - 都能让元素显示隐藏
- 不同点：
  - `display：none` 会让元素完全从渲染树中消失，渲染的时候不占据任何空间， `visibility: hidden` 不会让元素从渲染树消失，渲染元素继续占据空间，只是内容不可见。
  - `display: none`;是非继承属性，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示,  `visibility: hidden;`是继承属性，子孙节点消失由于继承了`hidden`，通过设置`visibility: visible;`可以让子孙节点显式。
  - 修改常规流中元素的`display`通常会造成文档重排。修改`visibility`属性只会造成本元素的重绘。
  - 读屏器不会读取`display: none`;元素内容；会读取`visibility: hidden;`元素内容。

### 004、什么是FOUC?如何避免？

- `Flash Of Unstyled Content`：用户定义样式表加载之前浏览器使用默认样式显示文档，用户样式加载渲染之后再从新显示文档，造成页面闪烁。
- **解决方法**：把样式表放到文档的`<head>`

### 005、BFC

- `BFC(Block Formatting Context)`  块级格式化上下文，是一个独立的渲染区域，让处于 BFC 内部的元素与外部的元素相互隔离，使内外元素的定位不会相互影响。
- **触发条件 (以下任意一条)**
  - `float`的值不为`none`
  - `overflow`的值不为`visible`
  - `display`的值为`table-cell`、`tabble-caption`和`inline-block`之一
  - `position`的值不为`static`或则`releative`中的任何一个

### 006、BFC布局与普通文档流布局区别？

- 普通文档流布局
  - 浮动的元素是不会被父级计算高度
  - 非浮动元素会覆盖浮动元素的位置
  - `margin`会传递给父级元素
  - 两个相邻元素上下的`margin`会重叠
- BFC布局规则
  - 浮动的元素会被父级计算高度(父级元素触发了`BFC`)
  - 非浮动元素不会覆盖浮动元素的位置(非浮动元素触发了`BFC`)
  - `margin`不会传递给父级(父级触发`BFC`)
  - 属于同一个`BFC`的两个相邻元素上下`margin`会重叠

### 007、清除浮动的几种方式，各自的优缺点？

- 父级`div`定义`height`
- 结尾处加空`div`标签`clear:both`
- 父级`div`定义伪类`:after`和`zoom`
- 父级`div`定义`overflow:hidden`
- 父级`div`也浮动，需要定义宽度
- 结尾处加`br`标签`clear:both`
- 比较好的是第3种方式，好多网站都这么用

### 008、为什么要初始化CSS样式?

- 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对`CSS`初始化往往会出现浏览器之间的页面显示差异。
- 当然，初始化样式会对`SEO`有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化

### 009、css3有哪些新特性

- 新增选择器 `p:nth-child(n){color: rgba(255, 0, 0, 0.75)}`
- 弹性盒模型 `display: flex;`
- 多列布局 `column-count: 5;`
- 媒体查询 `@media (max-width: 480px) {.box: {column-count: 1;}}`
- 个性化字体 `@font-face{font-family: BorderWeb; src:url(BORDERW0.eot);}`
- 颜色透明度 `color: rgba(255, 0, 0, 0.75);`
- 圆角 `border-radius: 5px;`
- 渐变 `background:linear-gradient(red, green, blue);`
- 阴影 `box-shadow:3px 3px 3px rgba(0, 64, 128, 0.3);`
- 倒影 `box-reflect: below 2px;`
- 文字装饰 `text-stroke-color: red;`
- 文字溢出 `text-overflow:ellipsis;`
- 背景效果 `background-size: 100px 100px;`
- 边框效果 `border-image:url(bt_blue.png) 0 10;`
- 转换
  - 旋转 `transform: rotate(20deg);`
  - 倾斜 `transform: skew(150deg, -10deg);`
  - 位移 `transform: translate(20px, 20px);`
  - 缩放 `transform: scale(.5);`
- 平滑过渡 `transition: all .3s ease-in .1s;`
- 动画 `@keyframes anim-1 {50% {border-radius: 50%;}} animation: anim-1 1s;`

### 010、CSS3新增伪类有那些？

- `p:first-of-type` 选择属于其父元素的首个`<p>`元素的每个`<p>` 元素。
- `p:last-of-type` 选择属于其父元素的最后 `<p>` 元素的每个`<p>` 元素。
- `p:only-of-type` 选择属于其父元素唯一的 `<p>`元素的每个 `<p>` 元素。
- `p:only-child` 选择属于其父元素的唯一子元素的每个 `<p>` 元素。
- `p:nth-child(2)` 选择属于其父元素的第二个子元素的每个 `<p>` 元素。
- `:after` 在元素之前添加内容,也可以用来做清除浮动。
- `:before` 在元素之后添加内容。
- `:enabled` 已启用的表单元素。
- `:disabled` 已禁用的表单元素。
- `:checked` 单选框或复选框被选中。

### 011、display有哪些值？说明他们的作用？

- `block` 转换成块状元素。
- `inline` 转换成行内元素。
- `none` 设置元素不可见。
- `inline-block` 象行内元素一样显示，但其内容象块类型元素一样显示。
- `list-item` 象块类型元素一样显示，并添加样式列表标记。
- `table` 此元素会作为块级表格来显示
- `inherit` 规定应该从父元素继承 `display` 属性的值

### 012、介绍一下标准的CSS的盒子模型？

- 盒模型： 内容(content)、填充(`padding`)、边界(`margin`)、 边框(`border`)；
- IE 盒模型：盒子的宽度包括：  内容(content)+填充(`padding`)+边框(`border`) 
- W3C盒模型：盒子的宽度包括： 内容(content)

### 013、position定位

- `absolute`：生成绝对定位的元素，相对于 `static` 定位以外的第一个父元素进行定位
- `fixed`：生成绝对定位的元素，相对于浏览器窗口进行定位
- `relative`：生成相对定位的元素，相对于其正常位置进行定位
- `static` 默认值。没有定位，元素出现在正常的流中
- `inherit` 规定从父元素继承 `position` 属性的值

### 014、重绘和回流（重排）是什么，如何避免？

- 重绘：当渲染树中的元素外观（如：颜色）发生改变，不影响布局时，产生重绘
- 回流：当渲染树中的元素的布局（如：尺寸、位置、隐藏/状态状态）发生改变时，产生重绘回流
- 注意：JS获取Layout属性值（如：`offsetLeft`、`scrollTop`、`getComputedStyle`等）也会引起回流。因为浏览器需要通过回流计算最新值
- 回流必将引起重绘，而重绘不一定会引起回流

## 03、JavaScript

### 001、JavaScript 数据类型

#### 一、前沿

   众所周知， `JavaScript` 的数据类型，可以分为两种： 原始数据类型（又叫基本数据类型、基础数据类型） 和 对象类型（又叫复杂数据类型）。

#### 二、运行时环境

要说清楚这两种类型最核心的区别，那必须从他们存储在内存中的结构说起。这是这两者最核心的区别。即栈和堆的存储结构。

栈和堆是`JavaScript`中，存储数据唯二的两种方式。是宿主环境V8引擎提供的。

- 栈

     栈空间在内存中，是一块连续的地址。因此查找效率非常高。因为栈空间想对来说比较小，所以想要分配很大一块连续内存，在内存中是很难的，一般 js 引擎会对其大小进行限制。

- 堆

     既然栈不能存储很大的数据，那么必然就需要另一种方式来进行存储很大的数据。这就是堆，堆与栈不同。堆在内存中的位置不需要连续的，也是正因为如此，所以堆的查找效率较低。但是他的容量很大。栈不能存储的数据都是在堆中存储的。

#### 三、数据类型

- **原始数据类型：** es6 中原始数据类型增加到了七种： `string`、 `number`、`boolean` 、`undefined`、  `null` 、 `symbol` 、 `bigInt` 。 他们是直接存储在栈中的。所以读取操作想对较快。
- **对象类型：** 对象一般可以分为 `内置对象`、`宿主对象`、`自定义对象`  。
  - `内置对象` : 执行引擎根据语言标准实现的一些对象，比如： `Math`   `Date`   `RegExp` 等一些在引擎内部定义的对象。
  - `宿主对象：` 执行环境提供的对象，比如：`document`   `Image`   `window`  等，由宿主环境提供的api 或者 对象，常见的宿主有 浏览器，node 等。
  - `自定义对象：`  即我们在运行时，使用内置构造器创建的一些new Array()数组实例，new Object()对象实例，new Parent()类实例等等。类似于以上，数据结构复杂，执行过程中可能会占用较大内存的数据类型。都统一存储在堆空间中。一般称之为引用型数据（在栈中保存了数据在堆中的内存起始地址指针）



---



### 002、深浅拷贝

   了解完 `JavaScript`数据类型，是对 JavaScript 的深浅拷贝学习的基础。

#### 一、前沿

- 深浅拷贝是针对 `JavaScript` 堆中的复杂数据类型来说的。
- 原始数据类型是没有深浅拷贝的，原始数据类型的拷贝是直接在栈中心分配一块新的地址，对齐进行赋值。原始数据类型比较只是比较值是否一样。

#### 二、复杂数据类型浅拷贝

```javascript
// example 1
let arr1 = [1,2,3]
let arr2 = arr1
console.log(arr1 === arr2) // true
arr2.splice(0,1)
console.log(arr1) // [2,3]
console.log(arr2) // [2,3]
// 解析： 
    1.这里arr1是复杂数据类型，在堆中开辟空间存储 [1,2,3]，起始地址指针赋值给栈中的 arr1 ，
    2.当把 arr1 赋值给 arr2的时候是浅拷贝，是吧arr1 的起始地址指针赋值给了arr2。即arr1,arr2的地址指针都指向堆中的[1,2,3]。
    3.当打印`console.log(arr1 === arr2)`的时候为true，
    4.当修改arr2的时候，`console.log(arr2)` 为 [2,3],`console.log(arr1)` 也为 [2,3]。 所以arr1和arr2指向堆中的同一份数据。
```

#### 三、复杂数据类型深拷贝

```javascript
// example 2
let arr1 = [1,2,3]
let arr2 = JSON.parse(JSON.stringify(arr1))
console.log(arr1 === arr2) // fase
arr2.splice(0,1)
console.log(arr1) // [1,2,3]
console.log(arr2) // [2,3]
// 解析： 
    1.这里arr1是复杂数据类型，在堆中开辟空间存储 [1,2,3]，起始地址指针赋值给栈中的 arr1 。
    2.当把 arr1 通过`JSON.parse(JSON.stringify(arr1))`赋值给 arr2的时候是深拷贝，是在堆中开辟了一块新的空间，然后复制arr1起始地址指针指向的堆中的值，给新的空间，然后新空间的起始地址指针赋值给了arr2。即arr1,arr2的地址指针不相同，且指向堆中的不同的[1,2,3]。
    3.当打印`console.log(arr1 === arr2)`的时候为false
    4.当修改arr2的时候，`console.log(arr2)` 为[2,3],`console.log(arr1)` 仍为 [1,2,3]。 所以arr1和arr2指向堆中的不同的数据。
```

#### 四、深拷贝的方法

- 使用递归实现深拷贝

```
//使用递归的方式实现数组、对象的深拷贝
function deepClone1(obj) {
  //判断拷贝的要进行深拷贝的是数组还是对象，是数组的话进行数组拷贝，对象的话进行对象拷贝
  var objClone = Array.isArray(obj) ? [] : {};
  //进行深拷贝的不能为空，并且是对象或者是
  if (obj && typeof obj === "object") {
    for (key in obj) {
      if (obj.hasOwnProperty(key)) {
        if (obj[key] && typeof obj[key] === "object") {
          objClone[key] = deepClone1(obj[key]);
        } else {
          objClone[key] = obj[key];
        }
      }
    }
  }
  return objClone;
}
```

- 使用`lodash`库，`cloneDeep`函数 - 原理 递归实现

```javascript
import _ from "lodash"
var objects = [{ 'a': 1 }, { 'b': 2 }];
var deep = _.cloneDeep(objects);
console.log(deep[0] === objects[0]); //false
```

- JSON 对象实现深拷贝

```javascript
function deepClone2(obj) {
  var _obj = JSON.stringify(obj),
    objClone = JSON.parse(_obj);
  return objClone;
}
// 无法实现对对象中方法的深拷贝
// 如果对象中key的值是 undefined，symbol,还有函数的时候会被忽略。
```

- `Object.assign()`深拷贝

```javascript
// 当对象中只有一级属性，没有二级属性的时候，此方法为深拷贝，但是对象中有对象的时候，此方法，在二级属性以后就是浅拷贝
```

- 通过jQuery的extend方法实现深拷贝

```javascript
var array = [1,2,3,4];
var newArray = $.extend(true,[],array);
```



-----



### 003、变量类型判断

#### 一、`typeof`

- `typeof`  返回的都是字符串形式。

```javascript
typeof 'aaa'  //string
typeof 12  // number
typeof true // boolean
typeof undefined // undefined
typeof null // object
typeof Math // object
typeof () => {} //function
```

#### 二、`instanceof`

- `instanceof` 后面一定要是对象类型，并且大小写不能错
- `instanceof` 可以正确的判断对象的类型，因为内部机制是通过判断对象的原型链中是不是能找到类型的 `prototype`。

```javascript
[] instanceof Array //true
[] instanceof Object //true
Math instanceof Object //true
'assd' instanceof Object //false

const str = new String('asd')
str instanceof Object //true

(() => {}) instanceof Function // true
```

#### 三、尝试手写`instanceof`方法：

```javascript
A instanceof B

function _instanceof(A,B) {
  // 获得类型的原型
  let bPrototype = B.prototype
  // 获得对象的原型
  let aPrototype = A.__proto__
  while (true) {
      if (aPrototype === null)
        return false
      if (bPrototype === aPrototype)
        return true
      aPrototype = aPrototype.__proto__
  }
}
```



#### 四、`constcuctor`

- null 和 undefined 没有构造函数，因此不会有constructor的存在。

##### 五、`Object.prototype.toString`

- 前提是  `Object.prototype.toString`  没有被重写

  ```javascript
  const num = 1
  const str = '1'
  const arr = []
  const obj = {}
  const null1 = null
  const undefined1 = undefined
  Object.prototype.toString.call(num) // [object Number]
  Object.prototype.toString.call(str) // [object String]
  Object.prototype.toString.call(arr) // [object Array]
  Object.prototype.toString.call(obj) // [object Object]
  Object.prototype.toString.call(null1) // [object Null]
  Object.prototype.toString.call(undefined1) // [object Undefined]
  ```




---------



### 004、`String` 类

#### 一、字符串的常用方法

1. `indexOf(s1,[s2])`

   - 返回字符串中检索指定字符第一次出现的位置，没找到就返回-1.
   - s1 ： 要查找的字符串（必填）
   - s2 ： 从哪个索引开始查找 （选填）

   ```javascript
   const str = 'abcabcddd'
   str.indexOf('abc') // 0
   str.indexOf('b') // 1
   str.indexOf('ddd') // 6
   str.indexOf('d') // 6
   ```

2. `search()`  查找

   - 主要检索与正则表达式相匹配的值
   - 一个参数，找到返回索引，没找到返回-1

   ```javascript
   const str = 'abcabcddd'
   str.search('abc') // 0
   ```

3. `trim() ` 去除前后空格

   ```javascript
   var str = "  abcde fg h ";
   console.log(str.length);//13
   console.log(str.trim().length);//10
   ```

4. `charAt()`  根据下标返回字符

   ```javascript
   var str = "abcde";
   console.log(str.charAt(0)) //a
   ```

5. `charCodeAt`  根据下标返回字符的ASCLL码

   ```javascript
   var str = "abcde";
   console.log(str.charCodeAt(0)) //97
   ```

6. `fromCharCode()`  将 ASCll 转化为字符

   ```javascript
   console.log(String.fromCharCode(97)) //a
   ```

7. `substr(s1,s2)`  截取字符串

   - 第一个参数是开始截取的索引，第二个参数要截取多少个
   - 只有一个参数，代表从开始截取的位置到最后
   - 返回值是截取的字符串

   ```javascript
   var str = "abcdef";
   console.log(str.substr(0, 5));//abcde
   console.log(str.substr(4));//ef--写一个参数为索引，默认截取字符串该索引后面的所有字符
   console.log(str.substr(-3,2))//从倒数第三个,截取2个
   ```

8. `substring(start,end)` 截取字符串

   * 作用:对字符串进行截取(包前不包后)
   * 参数:start表示截取开始的索引,end表示截取结束的索引,end要大于start,不允许负数
   * 返回:从start到end的字符串,不包含end

   ```javascript
   var str = "abcdef";
   console.log(str.slice(0, 4));//abcd
   console.log(str.slice(3));//def--等价于substring
   ```

9. `slice(start,end)`

   * 作用：对字符串截取，start表示截取的开始元素，end表示截取的截止元素，包前不包后。

   * 返回值：截取的字符串

   * ```javascript
     console.log(str.slice(0,4));//0是起始索引,4是结束索引,不包含4
     console.log(str.slice(4));//表示从4到结束
     console.log(str.slice(-3));//表示倒数第三到最后
     ```

10. `split(s1,s2)`  将字符串转化成数组

    - 第一个参数是根据什么截取，可以是字符串，可以是正则

    ```javascript
    var s3 = "abcdefg";
    console.log(s3.split('')) //转换为['a','b','c','d','e','f','g']
    var s4 = "a,b,cd,e,fg";
    console.log(s3.split(',')) //转换为['a', 'b', 'cd', 'e', 'fg']
    ```

11.`match()`  匹配符合正则的字符串

- 参数是正则表达式
- 返回值是null 或者符合正则的字符串数组

```javascript
var tel = 'dddaaadddcccdddd';
console.log(tel.match(/ddd/)) //['ddd', 'ddd', 'ddd']
```

12. `replace()`  替换

- `replace()`  方法是用替换值（replacement）替换部分子串，或者替换所有匹配的子串。返回值是替换以后的新字符串。

  **语法：**

```javascript
str.replace(regexp|substr, newSubStr|function)
// 第一个参数是： 字符串 或者 正则表达式
// 第二个参数是： 替换的字符串 | 每次都会执行的回调函数
```

- 当第一个参数是字符串的时候，仅第一个匹配项会被替换。

  ```javascript
  const str = 'abcde'
  const newStr = str.replace('a','c')  
  console.log(newStr) // 'cbcde'
  ```

- 当第二个参数是函数的时候，函数的返回值会作为替换的字符串。



#### 二、遍历字符串

1. #### `for` 循环

```javascript
const str = '0123456'
for(var i=0;i< str.length;i++){
  console.log(str[i]);//0 1 2 3 4 5 6
}
```

2. `for...in`

```javascript
for ( const key in str) {
   console.log(key);//0 1 2 3 4 5 6
}
```



------





### 005、`Number` 类

### 006、`Boolean` 类

### 007、`null` 

### 008、`undefined`

### 009、`symbol`

#### 010、`bigInt`



------



### 011、`Array`

#### 一、数组的常用方法

#####   1.1.增

- **`数组.unshift(item)`;** **从数组前面增加一个元素**
  - 作用:从数组前面增加一个元素
  - 参数:item要新增的那个元素
  - 返回值:数组的长度
  - 注意点:直接在原数组操作
- **`数组.push(item)`**：**从数组后面增加一个元素**
  - 作用:从数组后面增加一个元素
  - 参数:item要新增的那个元素
  - 返回值:数组的长度
  - 注意点:直接在原数组操作

##### 1.2.删

* **`数组.shift()`**：**删除数组中的第一个元素**

  * 作用：删除数组中的第一个元素。
  * 返回值：被删除的那个元素。 
  * 参数：无
  * 注意：直接在原数组操作，不会生成新数组。

* **`数组.pop()`**：**删除数组中的最后一个元素**

  * 作用：删除数组中的最后一个元素
  * 返回值：被删除的那个元素。
  * 参数：无
  * 注意：直接在原数组操作，不会生成新数组。

* **`数组.splice(start,n)`**：** **从数组的start位置开始删除n个元素**

  * 作用:从数组的start位置开始删除n个元素
  * 参数:start表示从哪个索引开始删除,n表示要删除几个元素
  * 返回值:被删除的元素的集合
  * 注意点:直接在原数组操作

  **`数组.splice(start,n,.....)`**：**从数组的start位置开始删除n个元素，然后再添加什么元素**

  * 作用:从数组的start位置开始删除n个元素,新增m个元素
  * 参数:start表示从哪个索引开始删除或者增加,n表示要删除几个元素,后面由m个参数,就是要增加要数组中的新元素,从索引是start位置开始增加。
  * 返回值:被删除的元素的集合
  * 注意点:直接在原数组操作

##### 1.3.截取

* **`数组.slice(start,end)`：从数组中截取一部分**
  * 作用:从数组中截取一部分
  * 参数:start表示开始截取的索引,end表示结束截取的索引,包start,不包end，（包前不包后）
  * 返回值:返回一个新的数组，包含从 start 到 end （不包括该元素）的 所有元素
  * 注意点:返回一个新数组,原数组不变

##### 1.4.**颠倒数组**

* **`数组.reverse()`**：**颠倒数组**
  * 作用:颠倒数组
  * 参数:无
  * 返回值:原数组
  * 注意点:直接在原数组操作

##### 1.5.**连接数组**

* **`数组1.concat(数组2,数组3,......)`：**
  * 作用:用于连接多个数组
  * 参数:要被连接的那些数组
  *  返回值:连接好的新数组
  * 注意点:不在原数组操作,会产生新数组

##### 1.6.数组变字符串

* 数组.join("分割符")：把数组变成字符串
  * 作用:把数组变成字符串
  * 参数:默认是逗号,分隔符
  * 返回值:生成的那个字符串
  * 注意点:不会改变原数组

##### 1.7.查询

* **数组.indexof(ele,start)**

  * 作用：查找数组中某个元素的索引

  * 返回值：如果没找到就返回-1，如果找到了就返回该元素的索引值。

  * 参数：第一个参数ele是：要查找的那个元素

      ​    第二个参数start：从哪里开始查找，默认从零开始找

* **数组.lastIndexof(ele,start)**

  * 作用：查找数组中某个元素的索引

  * 返回值：如果没找到就返回-1，如果找到了就返回该元素的索引值。

  * 参数：第一个参数ele是：要查找的那个元素

      ​    第二个参数start：从哪里开始查找，默认从零开始找

##### 1.8.数组排序

* **`数组.sort(fn)`**;

  * 作用:按照指定规则进行排序

  * 参数:如果不写参数,默认是按照字符编码的顺序进行排序,如果写参数,参数fn是表示排序  规则的函数

  * 返回值:返回值就是拍好序的数组

  * 注意点:直接在原数组操作

  * 有参数:参数是表示排序规则的函数

  * 示例“

    ```javascript
    arr.sort(function(a,b){
    
      return a-b;
    
    })由小到大排序
    
    arr.sort(function(a,b){
    
      return b-a;
    
    })由大到小排序
    ```

#### 二、数组的遍历

##### 1.for循环

```javascript
for(var i=0;i<arr.length;i++){
    console.log(arr[i])
}

```

##### 2.for in 循环

```javascript
for( var index in arr){
//固定写法,arr是要循环的数组,index是循环到的那个元素的索引
console.log("当前循环到的是第"+index+'个元素,元素的值是:'+arr[index])
}
```

##### 3.forEach()循环

```javascript
数组.forEach(function(value,index){
    要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
    console.log("当前循环到的是第"+index+'个元素,元素的值是:'+value)
})
//参数:要循环执行的函数,函数有两个形参,第一个形参实循环到的那个数组元素的值,第二个形参实循环到的那个数组元素的索引
//注意点:不会改变原数组
```

##### 4.map()循环

```javascript
数组.map(function(value,index){
    要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
    return value-1
})
//作用:循环数组
//参数:要循环执行的函数,函数有两个形参,第一个形参实循环到的那个数组元素的值,第二个形参实循环到的那个数组元素的索引
//返回值:整个map的返回值是每一次循环的函数的返回值的集合
//示例：
var arr = [23,45,43,78,23,12,46,28,97];
console.log(arr)
var newArr = arr.map(function(value,index){
    return value-1;
})
console.log(newArr)//newArr = [22,44,42,77,22,11,45,27,96]
```

##### 5.fliter()循环

```javascript
数组.fliter(function(value,index){
    //要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
    //符合条件的返回true
    //不符合条件的返回false
   if(value>40){
       return true
   }else{
       return false
   }
})
//作用：过滤数组中符合条件的元素，返回值是新的数组
```

##### 6.every()循环

```javascript
数组.every(function(value,index){
    //要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
})
//作用：判断数组中的每一个元素是否都符合条件，符合返回值true，不符合返回值false
//示例：
var arr = [1,15,26,48,45,25,14,44]
var res = arr.every(function(value,index){
    return value>30;
})
console.log(res)
```

##### 7.some()循环

```javascript
数组.some(function(value,index){
    //要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
})
//作用：判断数组中的每一个元素是否有符合条件，符合返回值true，不符合返回值false
//示例：
var arr = [1,15,26,48,45,25,14,44]
var res = arr.every(function(value,index){
    return value>30;
})
console.log(res)
```



------



### 012、`Object` 对象类

#### 一、概念：

1. `JavaScript` 中的构造函数，构造函数创建一个对象包装器。

#### 二、描述：

   在 `JavaScript` 中，几乎所有的对象都是 `Object` 类型的实例。他们都会从 `Object.prototype` 继承属性和方法。`Object` 构造函数为给定值创建一个对象包装器。`Object` 构造函数，会根据给定参数创建对象。

- 如果给定值是 `null` 或 `undefined`，将会创建并返回一个空对象。
- 如果传进去的是一个基本类型的值，则会构造其包装类型的对象
- 如果传进去的是引用类型的值，仍然会返回这个值，经他们复制的变量保有和源对象相同的引用地址。

#### 三、Object  构造函数的属性

##### 3.1、`Object.prototype`  

- 可以给所有 Object 的类型的对象添加属性。

##### 3.2、`Object.assign()` 

- 通过一个对象或者多个对象来创建一个新的对象。

##### 3.3、`Object.create()`

- 使用制定原型对象创建一个新的对象。

##### 3.4、`Object.defineProperty()`

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

##### 3.5、`Object.defineProperties()`

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

##### 3.6、`Object.entries()`

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

##### 3.7、`Object.keys()`

- 返回一个包含所有给定对象**自身**可枚举属性名称的数组。

##### 3.8、`Object.values()`

- 返回给定对象自身可枚举值的数组。



------



### 013、JavaScript的执行机制

#### 一、前言
>     众所周知，浏览器的JavaScript**解析引擎是单线程**的，也就是说每次只能执行一个任务，其他任务都得按照顺序排队等待被执行，只有当前任务执行完成以后才可以执行下一个任务。
#### 二、JavaScript的任务分为同步任务和异步任务
1.  同步任务
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
####  三、事件循环宏观流程介绍
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809100527541.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NzA3Njk4OQ==,size_16,color_FFFFFF,t_70)
步骤：
1.JavaScript代码自上而下一次依次解析
2.当遇见同步代码的时候直接扔进  **Call Stack  (调用栈)**  里，遇见异步代码的时候直接扔进  **webcore**  模块中
3.扔进**Call Stack  (调用栈)**里的代码依次执行，扔进**webcore**  模块中的代码依次执行把异步的结果扔进他task    queue，并不会直接执行
4.等待**Call Stack  (调用栈)**中所有的同步任务执行完毕以后，task queue 里的异步回调才会扔进**Call Stack  (调用栈)**，依次执行。

-   当一个脚本执行的时候，js引擎会解析这段代码，并将其中的同步代码按照执行顺序加入调用栈中，然后从头开始执行。
-   js引擎遇到一个异步事件后并不会一直等待其返回结果，而是会将这个事件挂起(其他模块进行处理)，继续执行执行栈中的其他任务。当一个异步事件返回结果后，js会将这个事件加入到事件队列。
-   被放入事件队列不会立刻执行其回调，而是等待当前执行栈中的所有任务都执行完毕， 主线程处于闲置状态时，主线程会去查找事件队列是否有任务。如果有，那么主线程会从中取出排在第一位的事件，并把这个事件对应的回调放入执行栈中，然后执行其中的同步代码...，如此反复，这样就形成了一个无限的循环。这个过程被称为“事件循环（Event Loop）”。

#### 四、事件循环微观流程介绍
-   以上的事件循环过程是一个宏观的表述，实际上因为异步任务之间并不相同，因此他们的执行优先级也有区别。
- 不同的异步任务被分为两类：微任务（micro task）和宏任务（macro task）。
```js
macro-task： 整体代码script、setTimeout、setInterval......
micro-task：Promises、Object.observe......
```
- 在一个事件循环中，异步事件返回结果后会被放到一个任务队列中。根据这个异步事件的类型，实际上会被放到宏任务队列或者微任务队列。当前调用栈执行完毕时会优先处理所有微任务队列中的事件，然后再去宏任务队列中取出一个事件。
![å](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NzA3Njk4OQ==,size_16,color_FFFFFF,t_70.png)

------



### 014、new 一个对象的过程

#### 一、new 以后我们的到了什么？

> 直观的感觉，当我们new一个构造函数，得到的实例继承了 `构造器的属性` 以及`原型上的属性和方法`

```javascript
// ES5构造函数
let Parent = function (name, age) {
    this.name = name;
    this.age = age;
};
Parent.prototype.sayName = function () {
    console.log(this.name);
};

const child = new Parent('李四'， 23)
child.sayName() // 李四
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

​       **比较直观的感觉，当我们new 一个构造函数，得到的实例继承了 `构造器的构造属性`  和 `原型上的属性`。**

#### 二、new 的过程中发生了什么？

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

​       **现在应该知道 new 过程中会`新建对象`，此对象会继承`构造器的原型`与`原型上的属性`，最后它会被作为`实例`返回这样一个过程。**

#### 三、简单实现一个new的方法

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



------



### 015、正则表达式

#### 一、正则表达式：

- 定义字符的规则，也可定义输入字符串的规则。由普通的字符和元字符组成。
- 通过构造函数定义正则表达式：`var reg = new RegExp(/lucy/)`或者`var reg = new RegExp('lucy')`
- 通过字面量来定义正则表达式：//里面都是字符串   `var reg = /lucy/`

#### 二、元字符：

- \d      元字符表示0-9
- \D     元字符表示非数字
- \w     元字符表示单词字符：字母数字下划线
- \W    元字符表示非单词字符：
- \s      元字符表示空白字符
- \S      元字符表示非空白字符
- .         元字符表示除\n\r以外的任意字符(元字符用于查找单个字符，除了换行和行结束符)
- \         表示转义

#### 三、标识符

- g     表示全局去找
- i    表示不区分大小写

#### 四、字符串的方法

- str.match(reg/字符) 字符串的方法
  - 找到一个或者多个字符
  - 返回值是找到的字符第一个字符的下标

```javascript
var str = 'aasjdhhfiiasd46af454as6f4a5s465464f6a5s445454saf64a56s4d'
str.match(/[0-9]+/g)
```

- str.search(reg/字符)
  - 参数可以是字符串或者正则表达式
  - 查找字符串中是否含有指定的字符
  - 返回值：如果找到就返回第一个的子串的下标，找不到返回-1
  - 只找第一个。g不起作用

#### 五、test(‘要检索的字符串’)方法

- 检索字符串中指定的值,返回值true和false

```javascript
var reg = /lucy/;
console.log(reg.test("hello lucy"))//true
```

#### 六、量词

- 指定字符出现的次数
  - 指定出现n次，在要出现的字符后面添加{n}
  - 指定出现m到n次，在要出现的字符后面添加{m,n}
  - 指定出现n次以上，在要出现的字符后面添加{n,}
  - 指定出现1次或者1次以上，在要出现的字符后面添加+或者{1，}
  - 指定出现0次或者1次，在要出现的字符后面添加？或者{0，1}
  - 指定出现0次或者多次，在要出现的字符后面添加*或者{0，}
  - 精确匹配n：^n$
  - 以n开头：^n
  - 以n结尾：n$  

#### 七、方括号

* [abc]   表示abc中的任意一个
* [^abc]    表示不包含abc中的任意一个
* [1-9]   表示1-9中的任意一个



------



### 016、函数

### 017、函数的作用域

### 017、函数的作用域链

### 017、函数的this指向

1. #### this指向函数的调用对象

   ```javascript
   let obj = {
       a: 1,
       foo: function() {
      console.log(this)
       }
   }
   obj.foo() // this => obj
   ```

2. #### this指事件的调用对象

3. #### 在构造函数中this指向示例对象

   ```javascript
   function Parent(name, age) {
       console.log(this)
       this.name = name
       this.age = age
   }
   let person = new Parent('小明', 19)
   // 在构造函数中this指向示例对象
   ```

4. #### 在prototype原型的方法中，this指向实例对象

   ```javascript
   function Parent(name, age) {
       this.name = name
       this.age = age
   }
   
   Parent.prototype.sayHi = function() {
           console.log(this) 
   }
   // 在prototype原型的方法中，this指向实例对象
   ```

5. #### 找不到函数的调用的this指向window

   ```javascript
   function test() {
    console.log(this)
   }
   test() // this => window
   
   let obj = {
       a: 1,
       foo: function() {
      console.log(this)
       }
   }
   var fn = obj.foo
   fn() // this => window
   ```

6. #### 箭头函数没有自己的this，它的this指向上下文中的this(即所处环境的this)



-----




### 018、call、apply、bind

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



--------



### 020、闭包

### 020、原型

### 021、原型链

### 021、`class` 类

### 022、继承

#### 一、原型继承

- 原型继承 => 就是通过改变原型链的方式来达到继承
  - `子类.prototype = 父类的实例`

```javascript
1.父类
function Person(name) {
  this.name = name
}
Person.prototype.sayHi = function (){
  console.log('hello world !')
}
2.子类
function Student(age) {
  this.age = age
}

3.实现Student 继承 Person
Student.prototype = new Person('jack')
var s1 = new Student(18)

//原理:
实例的__proto__ = 父类的prototype
实例对象点什么属性或方法,这个属性或者方法,要么是保存在父类函数体内,要么是在父类的prototype原型上
s1.__proto__ = Student.prototype
new Person()的时候,会出来实例对象,包含name属性和prototype上的sayHi方法
s1的实例能访问Student.prototype上的方法,又因为Student.prototype = new Person()
所以s1的原型上具有name和sayHi方法
```

- 缺点:
  1. 继承下来的属性没有继承在自己身上,而是在`__proto__`上
  2. 继承的目的主要是继承属性和方法,原型继承的参数要在多个位置传递
  3. 对于代码的书写和维护和阅读都不是很好,而且十分消耗性能

#### 二、借用继承

> 借用构造函数继承(借用继承/call继承)

**this 指向:**

- this 是一个使用在作用域的 关键字

  - 要么使用在全局
  - 要么使用在函数内部

- 当使用在全局的时候

  - this 指向window

- 当使用在函数内部的时候

  - 不管函数的定义方式,不管函数定义在哪里
  - 只看函数的调用方式(箭头函数除外)
  - 全局调用
    - 函数名(): this ---> window
  - 对象调用
    - 对象名.函数名() : this--->点前面是谁就是谁
  - 定时器处理函数
    - `setTimeout(function() {},1000)`:this指向window
    - `setInterval(function() {},1000)`:this指向window
  - 事件处理函数:
    - `xxx.onclick= function() {}`
    - `xxx.addEventListner('click',function(){})`
    - 以上两种函数里面 ,this指向事件源
  - 自调用函数
    - this指向window
  - 构造函数
    - this指向当前实例对象
  - 箭头函数
    - 箭头函数没有this
    - this指向上下文中父级的this

  **call:**

  - 强行改变this指向的方法
  - `call(this指向,参数,参数)`

  ```javascript
  1.父类
  function Person(name) {
    this.name = name
  }
  Person.prototype.sayHi = function (){
    console.log('hello world !')
  }
  2.子类
  function Student(age,name) {
    this.age = age
    Person.call(this,name)
  }
  
  3.实现Student 继承 Person
  var s1 = new Student(18,'jack')
  
  //原理:
  ```

  **借用继承的优缺点:**

  **优点:**

  1. 继承来的属性写在了自己身上,不需要去`__proto__`上找了
  2. 自己需要用到的两个属性值 ,在一个构造函数的时候传递

  **缺点:**

  1. 只能继承父类的属性
  2. 不能继承父类的原型上的方法
  3. 写在构造函数体内的都可以继承

#### 三、组合继承:

组合继承:

- 继承: 子类的实例使用父类的属性和方法
- 组合: 原型继承 + 借用继承
  - 利用借用构造函数继承,把属性继承在自己身上
  - 利用原型继承把父类 prototype上的属性和方法继承下来

**缺点:**

1. 原来子类原型上的方法就没有了

#### 四、es6语法继承

1. es6书写的类的语法叫 class
2. es6也有自己的继承关键字 extends
3. 书写子类的时候:
   1. `class 子类 extends 父类 {}`
   2. 在子类constructor里写super()

```javascript
1.父类
class Person {
  constructor(name) {
    this.name = name
  }
  //原型上的方法
  sayHi () {
    console.log('你好')
  }
}

2.子类
class Student extends Person {
  constructor(name){
    //super 必须写在自己的this前面
    super(name)
    this.age=age
  }
}
var s1 = new Student(18,jack)
```





---



### 016、**Promise**

#### 一、概述

>      浏览器 JavaScript 引擎是单线程的，避免耗时的任务阻塞线程。所以需要异步编程。
>
>      Promise 是异步编程的解决方案，从语法上讲，Promise是一个对象，可以获取异步操作的信息。

#### 二、目的 

- 避免回调地狱的问题
- Promise 对象提供了简介的Api， 是的异步操作更加的容易。

#### 三、Promise的 三种状态

1. `pendding`   正在处理

   ```javascript
   console.log(new Promise((resovle, reject) => {}))
   ```

   打印

   ![image-20220811091446800](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811091446800.png)

2. `fulfilled`    成功

   ```javascript
   console.log(new Promise((resovle, reject) => { resovle()}))
   ```

   打印

   ![image-20220811091600792](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811091600792.png)

3. `rejected`    失败

   ```javascript
   console.log(new Promise((resovle, reject) => { reject()}))
   ```

   打印

   ![image-20220811091855984](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811091855984.png)

#### 四、Promise 的微任务执行机制

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

![image-20220811093340687](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811093340687.png)

#### 五、微任务与宏任务执行机制

>       js 先执行微任务，再执行宏任务，then() 方法是微任务 ， setTimeout() 是宏任务。

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

![image-20220811094304709](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811094304709.png)

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

![image-20220811094457577](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811094457577.png)

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

![image-20220811094703575](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811094703575.png)

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

![image-20220811094840487](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811094840487.png)

#### 六.Promise的单一状态与状态中转

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

![image-20220811095307607](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811095307607.png)

#### 七.then()方法

>      then 是 Promise 的成功和失败情况的回调函数。

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

>  每个 then 函数的返回值也是一个Promise

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

![image-20220811100740338](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220811100740338.png)



--------



### 017、防抖节流

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



-------



## 04、Node.js

### 001、Node 基础

#### 一、Node - 简介

> 前端的发展至今短短十几年时间，技术迭代，人才累积，都发生了翻天覆地的变化，其实前端开发受到企业重视的时间并不太长，过去在很多技术人员的眼中，我们只是负责切切页面的切图仔罢了。

> 随着 Ajax 技术的兴起, html5、css3、es6等的蓬勃发展，使得前端这个岗位越来越备受瞩目。

> 再随着 NodeJS 的推出，使得前端开发能干得事情越来越多。

> 慢慢的，前端逐渐演变为“全端”



##### 1、Node.js 是什么？

> 简单的说 Node.js 就是运行在服务端的 JavaScript。

> Node.js是一个基于 Chrome V8 引擎的 JavaScript 运行环境.

由 **Ryan Dahl** 使用 **C++** 语言编写的。并在 **2009年** 推出第一个版本。

##### 2、为什么需要学习Node.js?

1. 前端上手快速
2. 为了 **Money**
3. 前端工程化的基石，Grunt、Gulp、Fis3、Webpack
4. 编写服务端接口
5. 熟悉前后端的交互

#### 二、Node - web服务

##### 1、快速搭建一个Web服务

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



##### 2、端口号的小知识

取值范围 0 - 65535

##### 3. 公认端口（默认端口）

- 0 - 1023 一般都已经被使用了。

- - http   80
  - https   443
  - ftp   21
  - ssh   22
  - mysql   3306

##### 4. 端口占用

TODO

#### 三、服务器相关

##### 1. 服务器是什么

> 服务器是计算机的一种，它比普通计算机运行更快、负载更高、价格更贵。服务器在网络中为其它客户机（如PC机、智能手机、ATM等终端甚至是火车系统等大型设备）提供计算或者应用服务。



> 简单来说，就是一台能够提供服务的计算机

##### 2. 使用手机浏览器访问本地电脑中启动的http服务

1. 确保手机与电脑处于同一个网络（连接同一个wifi）
2. 关闭电脑的防火墙

#### 四、Node - web服务升级

##### 1、处理中文乱码

```js
res.writeHead(200,{"Content-type":"text/html;charset=utf-8"})
```

##### 2、nodemon

- 每次修改服务代码，都需要重新运行，很麻烦

  1. 安装一个全局的工具模块    **nodemon**  

     ```bash
     $ npm install nodemon -g
     ```

  2. 启动node服务时，使用 nodemon 命令去替代 node 命令

**注意：**

1. 1. **有时候 cmd 会有些抽搐，需要敲打一下就好**
   2. **nodemon 只在运行服务的代码时去使用。其余普通的一个 nodejs 代码运行，还是使用 node 命令就好了。**

##### 3、处理post请求

-    post请求的参数在请求体上，所以不能用req.url去处理

  > 监听事件
  >
  >  eventName   要监听的事件名字（eventName 不是自己想的名字，是固定的名字）
  >
  >  callback          监听的这个事件被触发时要执行的回调函数 
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

  

#### 五、Node - 模块化

##### 1、传统引入文件的弊端

- 变量污染
- 代码复用性不高
- 代码可维护性不高
- 依赖关系管理不方便

##### 2、模块化

**1.什么是模块化？**

> 一个模块就是一个实现特定功能的文件，有了模块我们就可以更方便的使用别人的代码，要用什么功能就加载什么模块。

**2.模块化带来的好处**

- 变量污染
- 代码复用性不高
- 代码可维护性不高
- 依赖关系管理不方便

#### 六、CommonJS规范

##### 1. 概述

> 每个文件就一个模块，有自己的作用域。在一个文件里面定义的变量、函数、类，都是私有的，对其它文件不可见。



> CommonJS规范规定，每个模块内部，**module** 变量代表当前模块。这个变量是一个对象，它的 **exports** 属性（即**module.exports**）是对外的接口。加载某个模块，其实就是加载该模块的 **module.exports** 属性。



**require**方法用于加载模块。

CommonJS模块的特点如下：

- 所有代码都运行在模块作用域，不会污染全局作用域。
- 模块可以多次加载，但是只会在第一次加载时运行一次，然后运行结果就被缓存了，以后再加载，就直接读取缓存结果。要想让模块再次运行，必须清除缓存。
- 模块加载的顺序，按照其在代码中出现的顺序。

##### 2. module对象

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

##### 3. require命令

**1. 基本用法**

> **require**命令的基本功能是，读入并执行一个JavaScript文件，然后返回该模块的**module.exports**对象。如果没有发现指定模块，会报错。

##### **2. 加载规则**

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

**3. 目录的加载规则**

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

**4. 模块的加载机制**

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

#### 七、Node - 内置模块

##### 1.URL

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



##### 2.querystring 查询字符串

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



##### 3.path 模块 专门处理路径相关

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
   
   

-----



### 002、EXPRESS

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



## 05、Vue

### 001、Vue 2.0 基础

#### 1. 初识 Vue

1. 一套用于构建用户界面的渐进式框架
2. 核心思想是**数据驱动**：数据映射视图，数据的修改会自动引起视图的改变。
3. **双向数据绑定**：数据的改变会引起视图的变化，视图的变化也会引起数据的变化，这就是双向数据绑定。



#### 2. Vue的模板语法

##### 1. 插值语法

功能： 用于解析标签体内容

写法： {{ xxx }} ，xxx 是 js表达式，并且可以直接读取到 data 中的所有属性

##### 2. 指令语法

功能：用于解析标签（包括：标签属性、标签体内容、绑定事件.....）。



#### 3. Vue中的数据绑定方式

1. 单向绑定(v-bind)：数据只能从data流向页面。

2. 双向绑定(v-model)：数据不仅能从data流向页面，还可以从页面流向data。

   备注： 

   1. 双向绑定一般都应用在表单类元素上（如：input、select等）
   2. v-model:value 可以简写为 v-model，因为v-model默认收集的就是value值。



#### 4. data 与 el 的两种写法

##### 1. data 的两种写法

- 对象式 
- 函数式

##### 2. el 的两种写法

- new Vue 的时候配置 el 属性。
- 先创建Vue的实例对象，随后再通过 `vm.$mount('#root')`去指定el的值

备注： **由Vue管理的函数，一定不要写箭头函数，一旦写了箭头函数，this就不再是Vue实例了。**



#### 5.MVVM 模型

1. M： 模型（model）： 指 data 中的数据
2. V： 视图（view）： 指的是模板代码
3. VM： 视图模型（ViewModel）： Vue 的实例

分析：

1. M（模型） 中的数据发生改变以后 ，通过VM（视图模型）控制，引起页面V（视图模板代码）改变。
2. 页面V（视图模板代码）改变，通过VM（视图模型）控制，引起M（模型） 中的数据发生改变。



#### 6. 数据代理

##### 1.  ES5 中 的 `Object.defineProperty()`

```javascript
Object.defineProperty('修改的对象', '修改的key名'，配置对象)
let number = 18
let person = {
    name:'张三',
    sex:'男',
}
1. 第一种使用方式
Object.defineProperty(person,'age',{
    value:18,
    enumerable:true, //控制属性是否可以枚举，默认值是false
    writable:true, //控制属性是否可以被修改，默认值是false
    configurable:true //控制属性是否可以被删除，默认值是false
})
2. 第二种使用方式
Object.defineProperty(person,'age',{
    // enumerable:true, //控制属性是否可以枚举，默认值是false
    // writable:true, //控制属性是否可以被修改，默认值是false
    // configurable:true //控制属性是否可以被删除，默认值是false
    //当有人读取person的age属性时，get函数(getter)就会被调用，且返回值就是age的值
    get(){
      console.log('有人读取age属性了')
        return number
   },

    //当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值
    set(value){
        console.log('有人修改了age属性，且值是',value)
        number = value
    }
})
```

##### 2. Vue中的数据代理

- 通过vm对象来代理data对象中属性的操作（读/写），更加方便的操作data中的数据。
- 通过`Object.defineProperty()`把data对象中所有属性添加到vm上。
- 为每一个添加到vm上的属性，都指定一个getter/setter。
- 在getter/setter内部去操作（读/写）data中对应的属性。



#### 7. 事件处理

1. 使用方式以及注意事项
   1. 使用v-on:xxx 或 @xxx 绑定事件，其中xxx是事件名
   2. 事件的回调需要配置在methods对象中，最终会在vm上
   3. methods中配置的函数，不要用箭头函数！否则this就不是vm了
   4. methods中配置的函数，都是被Vue所管理的函数，this的指向是vm 或 组件实例对象
   5. `@click="demo"` 和 `@click="demo($event)" `效果一致，但后者可以传参
2. 事件修饰符
   1. prevent：阻止默认事件（常用）；
   2. stop：阻止事件冒泡（常用）；
   3. once：事件只触发一次（常用）；
   4. capture：使用事件的捕获模式；
   5. self：只有event.target是当前操作的元素时才触发事件；
   6. passive：事件的默认行为立即执行，无需等待事件回调执行完毕；



#### 8. native 事件修饰符

  - 作用：将事件绑定到组件的根元素上

  - 在调用组件时去绑定一些原生事件，比如 click dblclick mousedown。他们是不生效的。因为会将他们任何是自定义事件的监听

  - 解决方法：

    1. 子组件触发这个事件

       ```javascript
       <div id="app">
           <base-button @click="fn1">按钮1</base-button>
       </div>
       
       Vue.component("baseButton", {
           template: `
               <button @click="$emit('click')">
               <slot></slot>
               </button>
         `,
       });
       var vm = new Vue({
           el: "#app",
           methods: {
               fn1() {
                   console.log("fn1");
               },
           },
       });
       ```

    2. 使用 native 事件修饰符

       ```javascript
       <div id="app">
           <base-button @click.native="fn1">按钮1</base-button>
       </div>
       
       Vue.component("baseButton", {
           template: `
               <button>
               <slot></slot>
               </button>
         `,
       });
       var vm = new Vue({
           el: "#app",
           methods: {
               fn1() {
                   console.log("fn1");
               },
           },
       });
       ```
       
       

#### 9. 计算属性（computed）

1. 要用的属性不存在，要通过已有属性计算得来。
2. 原理：底层借助了Objcet.defineproperty方法提供的getter和setter。
3. get函数什么时候执行？
   - 初次读取时会执行一次。
   - 当依赖的数据发生改变时会被再次调用。
4. 优势： 与methods实现相比，内部有缓存机制（复用），效率更高，调试方便。
5. 备注：
   1. 计算属性最终会出现在vm上，直接读取使用即可。
   2. 如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生改变。

```javascript
1. 当计算属性需要被修改，则写成对象形式，写set函数去响应修改
new Vue({,
    data:{
        firstName:'张',
      lastName:'三',
    }
    computed:{
        fullName: {
            get(){
                console.log('get被调用了')
                // console.log(this) //此处的this是vm
                return this.firstName + '-' + this.lastName
            },
            //set什么时候调用? 当fullName被修改时。
            set(value){
                console.log('set',value)
                const arr = value.split('-')
                this.firstName = arr[0]
                this.lastName = arr[1]
            }
        }
    }
})
2. 当计算属性不需要被修改的时候，可以简写成函数型式
new Vue({,
    data:{
        firstName:'张',
      lastName:'三',
    }
    computed:{
        fullName() {
         return this.firstName + '-' + this.lastName
      } 
    }
})
```



#### 10.  监视属性（watch）

1. 当被监视的属性变化时, 回调函数自动调用, 进行相关操作
2.  监视的属性必须存在，才能进行监视
3. 监视的两种写法：

              (1).new Vue时传入watch配置

```javascript
.// 1.简写
const vm = new Vue({
    el:'#root',
    data:{
        isHot:true,
    },
    watch:{
      isHot(newValue,oldValue){
            console.log('isHot被修改了',newValue,oldValue,this)
        } 
    }
})

//2.完整写法
const vm = new Vue({
    el:'#root',
    data:{
        isHot:true,
    },
    watch:{
        isHot:{
            deep: ture 
            immediate:true, //初始化时让handler调用一下
            // handler什么时候调用？当isHot发生改变时。
            handler(newValue,oldValue){
                console.log('isHot被修改了',newValue,oldValue)
            }
        }
    }
})
注意事项：
1.Vue中的watch默认不监测对象内部值的改变（一层）,配置deep:true可以监测对象内部值改变（多层）
2.handler什么时候调用？当isHot发生改变时。
3.immediate:true, 初始化时让handler调用一下
```

​              (2).通过vm.$watch监视

```javascript

//1.简写
vm.$watch('isHot',(newValue,oldValue)=>{
    console.log('isHot被修改了',newValue,oldValue,this)
}) 
//2.完整写法
vm.$watch('isHot',{
    immediate:true, //初始化时让handler调用一下
    deep:true,//深度监视
    handler(newValue,oldValue){
        console.log('isHot被修改了',newValue,oldValue)
    }
})
```

4. computed和watch之间的区别：
   1. computed能完成的功能，watch都可以完成。
   2. watch能完成的功能，computed不一定能完成，例如：watch可以进行异步操作。
   3. computed 有缓存。



#### 11. 条件渲染

1. `v-show`

   写法：v-show="表达式"

   适用于：切换频率较高的场景

   特点：不展示的DOM元素未被移除，仅仅是使用样式隐藏掉

2. `v-if`

   写法：

   ​     (1).v-if="表达式"

   ​     (2).v-else-if="表达式"

   ​     (3).v-else="表达式"

   适用于：切换频率较低的场景。

   特点：不展示的DOM元素直接被移除。

   注意：1.v-if可以和:v-else-if、v-else一起使用，但要求结构不能被“打断”。

               2. v-if可以和template一起使用，v-show不可以。



#### 12. v-for指令

1. 用于展示列表数据
2. 语法：`v-for="(item, index) in xxx" `
3. 可遍历：数组、对象、字符串（用的很少）、指定次数（用的很少）



#### 13. 虚拟DOM

 虚拟DOM就是一个json对象，它用于对真实DOM进行描述。



#### 14. diff 运算

1. 当Vue实例中的数据发生变化时，Vue会获得一份对虚拟DOM的拷贝
2. 如此我们就有两份虚拟DOM，一份是数据变化前的虚拟DOM，一份是数据变化后的虚拟DOM
3. 所谓的Diff运算，就是对这两份虚拟DOM进行差异比较，从而找出它们的最小差异。再把这份最小的差异渲染到真实DOM中去。 
4. MVVM框架，基于这种虚拟DOM的Diff运算，大大地减少了DOM的频繁操作，减少DOM操作本身就是一种性能优化。所以MVVM框架有利于性能优化，非常适合数据化的产品应用开发。



#### 15.Vue 虚拟的Dom的key

##### 1. 虚拟DOM中key的作用：

- key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据【新数据】生成【新的虚拟DOM】
- 随后Vue进行【新虚拟DOM】与【旧虚拟DOM】的差异比较，比较规则如下

##### 2. 对比规则：

- 旧虚拟DOM中找到了与新虚拟DOM相同的key
  - 若虚拟DOM中内容没变, 直接使用之前的真实DOM！
  - 若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM。
- 旧虚拟DOM中未找到与新虚拟DOM相同的key
  - 创建新的真实DOM，随后渲染到到页面

##### 3. 用index作为key可能会引发的问题：

- 若对数据进行：逆序添加、逆序删除等破坏顺序操作:
- 会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低。
- 如果结构中还包含输入类的DOM，会产生错误DOM更新

##### 4. 开发中如何选择key?

- 最好使用每条数据的唯一标识作为key, 比如id、手机号、身份证号、学号等唯一值。
- 如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的。



#### 16. v-modle

1. `v-model` 对表单元素进行双向数据绑定
2. `v-mode` 的修饰符
   - lazy：失去焦点再收集数据
   - number：输入字符串转为有效的数字
   - trim：输入首尾空格过滤
3. `v-model`双向数据绑定原理背后操作
   1. v-bind绑定value属性的值
   2. v-on绑定input事件监听到函数中，函数会获取最新的值赋值到绑定的属性中

```html
<input type="text" v-model="account">
对比
<input type="text" :value="account" @input='inputHandler'>
```



#### 17.过滤器

定义：对要显示的数据进行特定格式化后再显示（适用于一些简单逻辑的处理）。

语法：

1. 注册过滤器：`Vue.filter(name,callback) 或 new Vue{filters:{}}`  
2. 使用过滤器：`{{ xxx | 过滤器名}}`  或 ` v-bind:属性 = "xxx | 过滤器名"`

备注:

1. 过滤器也可以接收额外参数、多个过滤器也可以串联
2. 并没有改变原本的数据, 是产生新的对应的数据

```javascript
//全局过滤器
Vue.filter('mySlice',function(value){
    return value.slice(0,4)
})
//组件过滤器
new Vue({
    el:'#root',
    data:{
        time:1621561377603, //时间戳
        msg:'你好，尚硅谷'
    },
    //局部过滤器
    filters:{
        timeFormater(value,str='YYYY年MM月DD日 HH:mm:ss'){
            // console.log('@',value)
            return dayjs(value).format(str)
        }
    }
})
```



#### 18. v-bind

1. `v-bind`(简写 ：)用于动态绑定html标签属性

   1. 语法：

      1. `v-bind:attrname="数据"`

      2. `:attrname="数据“`

      3. `v-bind=对象`

         1. `v-bind="{name:'张三',age:18}"==>v-bind:name="张三"  v-bind:age="18"`

         2. `v-bind="{name:name,age:age}"==>v-bind:name="name"  v-bind:age="age"`

            此时对象的值在这里是变量，是data里的变量

   2. Vue中class 属性是一个特殊的属性 ，使用v-bind绑定时有很多不同的用法

      1. `v-bind：class="'hello'"`

         1. 此时 hello为字符串 ，代表给class加上hello这个类名 

      2. `v-bind：class="hello"`

         1. 此时hello为vue实例中data的属性，代表给class加上hello代理属性对应的类名

      3. `v-bind：class="{key1:value1,key2:value2}"`

         1. 根据value1这个数据是否为真值，来控制是否要加上key1这个 类名

         2. 根据value2这个数据是否为真值，来控制是否要加上key2这个 类名

            ```javascript
            v-bind:class="{ active: isActive, 'text-danger': hasError }"
            v-bind:class="[isActive ? activeClass : '', errorClass]"
            ```

      4. 数组 `v-bind:class="[value1, 'value2',value3，{key:value}]"`

         1. 使用value1这个数据的值来作为其中一个l类名
         2. 使用value2这个字符串来作为其中一个l类名
         3. 使用value3这个数据的值来作为其中一个l类名
         4. 根据value这个数据是否为真值，来控制是否要加上key这个 类名

   3. Vue中style 属性是一个特殊的属性 ，使用v-bind绑定时有很多不同的用法

      1. `v-bind:style="color : red"`     **这种是错误的写法会报错**

      2. `v-bind：style="{key1:value1,key2:value2，key3：'value3'}"`

         key1、key2、key3、都是css的属性名

         value1的值作为key1这个css属性名的值

         value2的值作为key2这个css属性名的值

         value3这个字符串会作为key3这个css属性名的值 

         ```javascript
           v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"
         ```

      3. `v-bind:style="[value1, value2,{color:myColor}]"`

         使用value1这个数据来控制，data中的value1必须为对象{font-size：'20px'}

         使用value2这个数据来控制，data中的value2必须为对象{font-size：'20px'}

         使用myColor这个数据来控制color属性的值 
         
         

#### 19. 内置指令

1. `v-html`

   作用：向指定节点中渲染包含html结构的内容。

   与插值语法的区别：

   - `v-html`会替换掉节点中所有的内容，`{{xx}}`则不会。
   - `v-html` 可以识别html结构。

    严重注意：

   - v-html有安全性问题！！！！
   - 在网站上动态渲染任意HTML是非常危险的，容易导致XSS攻击。
   - 一定要在可信的内容上使用v-html，永不要用在用户提交的内容上！

2. `v-text`

   作用：向其所在的节点中渲染文本内容。

   与插值语法的区别：

   - `v-text`会替换掉节点中所有的内容，`{{xx}}`则不会。
   - `v-text` 不可以识别html结构。

3. `v-bind`  :单向绑定解析表达式, 可简写为 `:xxx`

4. `v-model` : 双向数据绑定

5. `v-for` : 遍历数组/对象/字符串

6. `v-on`  :绑定事件监听, 可简写为@

7. `v-if`  :条件渲染（动态控制节点是否存存在）

8. `v-else`  :条件渲染（动态控制节点是否存存在）

9. `v-show`  :条件渲染 (动态控制节点是否展示)

10. `v-cloak`  :（没有值）

    作用：

    - 本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉`v-cloak`属性。
    - 使用css配合v-cloak可以解决网速慢时页面展示出`{{xxx}}`的问题

11. `v-once`  :（没有值）

    作用：

    - v-once所在节点在初次动态渲染后，就视为静态内容了
    - 以后数据的改变不会引起v-once所在结构的更新，可以用于优化性能。

12. `v-pre`  :（没有值）

    作用：

    - 跳过其所在节点的编译过程。
    
    - 可利用它跳过：没有使用指令语法、没有使用插值语法的节点，会加快编译。
    
      

#### 20. 自定义指令 

1. 定义语法：

   - 局部指令

     ```javascript
     // 1. 回调函数写法
     new Vue({
         data:{
         price: 10
         }
         directives:{
            // 需求： 自定义将价格提高十倍的指令
            big10(element,binding){
                 // element: 指令所在的Dom元素
                 // binding： 绑定对象的信息
               element.innerText = binding.value * 10
         }
         }   
     })
     // 2.配置对象写法
     new Vue({
         data:{
         price: 10
         }
         directives:{
            // 需求： 自定义将价格提高十倍的指令
            fbind:{
                 //指令与元素成功绑定时（一上来）
                 bind(element,binding){
                     element.value = binding.value
                 },
                 //指令所在元素被插入页面时
                 inserted(element,binding){
                      element.focus()
                 },
                 //指令所在的模板被重新解析时
                 update(element,binding){
                      element.value = binding.value
                 }
      }
     })
     ```

   - 全局指令

     ```javascript
     // 1.回调函数写法
     Vue.directive('fbind',(element,binding) => {
         element.value = binding.value
     }) 
     
     // 2.配置对象写法
     Vue.directive('fbind',{
         //指令与元素成功绑定时（一上来）
         bind(element,binding){
             element.value = binding.value
         },
         //指令所在元素被插入页面时
         inserted(element,binding){
             element.focus()
         },
         //指令所在的模板被重新解析时
         update(element,binding){
             element.value = binding.value
         }
     }) 
     ```

2. 配置对象中常用的3个回调：

   - bind：指令与元素成功绑定时调用。
   - inserted：指令所在元素被插入页面时调用。
   - update：指令所在模板结构被重新解析时调用。

3. 备注：

   - 指令定义时不加v-，但使用时要加v-
   - 指令名如果是多个单词，要使用`kebab-case`命名方式，不要用`camelCase`命名
   
   

#### 21. 生命周期

1.  Vue 生命周期示意图

![](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png)

#### 22. mixin

1. 全局写法

```javascript
//引入Vue
import Vue from 'vue'
//引入App
import App from './App.vue'
import {hunhe,hunhe2} from './mixin'
//关闭Vue的生产提示
Vue.config.productionTip = false
Vue.mixin(hunhe)
Vue.mixin(hunhe2)

//创建vm
new Vue({
   el:'#app',
   render: h => h(App)
})
```

2. 局部写法

```javascript
import {hunhe,hunhe2} from './mixin'
export default {
    name:'Student',
    data() {
        return {
            name:'张三',
            sex:'男'
        }
    },
    mixins:[hunhe,hunhe2]
}
```

注意事项：

- mixin 是混入的意思
- mixin 实际上就是暴露出一个vue的options的配置项
- mixin 混入原则组件优先



#### 23. slot -插槽

##### 1. slot 插槽

- 调用组件时，写在组件标签内的内容，默认是不会被渲染的
- 如果需要写在组件标签内的内容显示出来，那么就需要solt插槽

##### 2. slot 相关话术

- 定义组件时要想好在哪个位置去渲染 solt 内容
- 在想好位置那里放置一个 slot 标签即可
- slot内容就会自动替换 slot 标签

##### 3. slot内容

调用组件时写在组件标签内的内容就叫slot内容

##### 4. slot标签

<slot></slot>  vue的内置组件

##### 5. slot 默认内容

slot标签内的内容就是slot的默认内容

##### 6.具名插槽

- 给slot标签设置一个name属性,这个slot标签就叫做具名slot标签
- slot 标签在一个组件内是可以使用多次的
- 给slot标签去了名字后,slot内容想要渲染到哪个slot里面的话,插槽内容就需要设置slot属性,属性的值就是slot标签name属性的值

##### 7. 插槽的编译作用域

1. 编译作用域：

   父级模板里的所有内容都是在父级作用域中编译的，子模板里的所有内容都是在作用域编译的。

   写在组件标签内的插槽内容不属于组件的template。只是用过slot可以让他渲染在子组件内。

2. 插槽的编译作用域

   虽说插槽内容最终渲染到子组件内,但是他的编译作用域还是要看插槽内容写在哪个组件内,而不是看插槽内容最终渲染到哪个组件的template里面

##### 8. 作用域插槽

- 希望  插槽内容  中使用子组件的作用域

  1.定义组件的slot的时候，将要在插槽内容中使用的数据，绑定在slot标签上（不能绑定name属性）

  ```js
  //组件内
  <slot :a'msg' :b='age'></slot>
  ```

  2.在插槽内容的标签上，设置 slot-scope属性，属性值随便写，这个属性值就是上一个步骤绑定出来的一个数据大对象

  ```js
  //插槽内容
  <p slot-scope='obj'>我是插槽内容 {{obj.a}} </p>
  ```

##### 9. 插槽新语法

- 2019年2月4号 2.6.0版本更新（2018年过年）
- 新语法插槽要在插槽内容外包裹template标签,在template标签上写`v-slot:xxx`,xxx是插槽标签的name的属性值

```js
<-----老语法具名插槽使用------->
  <hello>
   <p slot="top"> 我的天</p>

  </hello>
<-----新语法具名插槽使用------->
   <hello>
    <template v-slot:top>
        <p> 我的天</p>
    </template>
    <template v-slot:bottom>
            <p> 我的地</p>
    </template>
  </hello>
```

- 新语法作用域插槽 `v-slot:xxx = yyy`

```js
<-----老语法作用域插槽使用------->
  <hello>
   <p slot="top" slot-scope="{msg,age}"> 我的天{{msg,age}}</p>

  </hello>
<-----新语法作用域插槽使用------->
   <hello>
    <template v-slot:top="{msg,age}">
        <p> 我的天 {{msg,age}}</p>
    </template>
  </hello>
```

- 只有一个插槽标签时,组件标签的插槽内容可以不用template包裹,`v-slot`要写在组件标签上

  

#### 24. 事件总线

1. 在全局挂载$bus

```javascript
//创建vm
new Vue({
   el:'#app',
   render: h => h(App),
   beforeCreate() {
      Vue.prototype.$bus = this //安装全局事件总线
   },
})
```

2. 在组件挂在完成时监听一个自定义事件名,  组件销毁的时候要取消监听

```javascript
........
    mounted() {
        // console.log('School',this)
        this.$bus.$on('hello',(data)=>{
        console.log('我是School组件，收到了数据',data)
        })
    },   

    beforeDestroy() {
        this.$bus.$off('hello')
    },
........
```

3. 发布

```javascript
........
methods: {
    sendStudentName(){
        this.$bus.$emit('hello',this.name)
    }
},
........
```



#### 25. 配置代理

- 在`vue.config.js`的文件夹下配置

```javascript
//  开启代理服务器（方式一）
devServer: {
    proxy: 'http://localhost:5000'
},
说明：
1. 优点：配置简单，请求资源时直接发给前端（8080）即可。
2. 缺点：不能配置多个代理，不能灵活的控制请求是否走代理。
3. 工作方式：若按照上述配置代理，当请求了前端不存在的资源时，那么该请求会转发给服务器 （优先匹配前端资源）
//  开启代理服务器（方式二）
devServer: {
    proxy: {
        '/atguigu': {
            target: 'http://localhost:5000',
            pathRewrite:{'^/atguigu':''},
            // ws: true, //用于支持websocket
            // changeOrigin: true //用于控制请求头中的host值
        },
        '/demo': {
             target: 'http://localhost:5001',
             pathRewrite:{'^/demo':''},
             // ws: true, //用于支持websocket
             // changeOrigin: true //用于控制请求头中的host值
            }
    }
}
```



#### 26. $nexTick()

1. 语法：```this.$nextTick(回调函数)```
2. 作用：在下一次 DOM 更新结束后执行其指定的回调。
3. 什么时候用：当改变数据后，要基于更新后的新DOM进行某些操作时，要在nextTick所指定的回调函数中执行。



#### 27. ref

1. 被用来给元素或子组件注册引用信息（id的替代者）
2. 应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象（vc）
3. 使用方式：
   1. 打标识：```<h1 ref="xxx">.....</h1>``` 或 ```<School ref="xxx"></School>```
   2. 获取：```this.$refs.xxx```



#### 28. props

1. 功能：让组件接收外部传过来的数据

2. 传递数据：```<Demo name="xxx"/>```

3. 接收数据：

   1. 第一种方式（只接收）：```props:['name'] ```

   2. 第二种方式（限制类型）：```props:{name:String}```

   3. 第三种方式（限制类型、限制必要性、指定默认值）：

      ```js
      props:{
         name:{
         type:String, //类型
         required:true, //必要性
         default:'老王' //默认值
         }
      }
      ```

   > 备注：props是只读的，Vue底层会监测你对props的修改，如果进行了修改，就会发出警告，若业务需求确实需要修改，那么请复制props的内容到data中一份，然后去修改data中的数据。
   
   

#### 29. 非 prop 的 attribute (非 prop 的特性)

- 在调用组件时，设置的属性(attribute)如果这个组件中没有定义相应的prop。那么这个属性就叫做 非prop的attribute

```javascript
Vue.component('hello', {
        props: {
          name: String,
          age: Number
        },
        template: `<div>hello</div>`
      })
<hello name="张三" age="18" id="box" title="我的天" class="box1" style="color: red"></hello>
```

1. 这里 hello 组件调用时。设置的属性有：name、age、id、title、class、style
2. hello 组件中将 name、age 是规定为 prop 数据的
3. 那么 这里 id 和 title 这两个属性就叫做非prop的特性

**注意：class 与 style 不是非prop的特性。他们两个是非常非常特殊的一个属性**

- **非prop的attribute 的特点**

  1. 最主要的一个特点就是会继承到组件的根元素上
  2. 并且是一种**替换的操作**

- **class与style是非常特殊的**

  1. 他们有 非prop的attribute 的继承的特点
  2. 但是他们不是替换的操作，而是**拼接操作**

  注意：用处。调用别人的组件的时候，这个组件的源代码我不能修改，这时如果要修改样式，就可以在调用时

  设置自己的 class 或 style
  
  

#### 30. component 

-  Vue 中提供有一个内置的组件叫做 component 。这个组件就是动态组件。它需要设置 is 属性。is 属性的值就是需要渲染的组件的名字

-  component  不具备缓存能力，是一直在创建，销毁

```javascript
<component is="hello" ></component>     hello 组件替换这个内容
<component is="world" ></component>     world 组件替换这个内容
```

1. 如果组件不存在就会报错
2. 将is属性设置为一个可以变化的数据，就能实现组件的动态切换



#### 31. keep-alive

- Vue 中提供了一个 keep-alive 内置组件。可以实现组件的缓存。   
- 将要缓存的组件使用 keep-alive 包裹住即可。
- 被 keep-alive 缓存了的组件的特点：
  -  切换组件时，当前组件不会触发销毁的生命周期钩子。也就是说不会销毁了。
  - 切换回来时，也不会重新创建。（既然都没有被销毁，哪里来的重新创建呢）
  - 会多出两个生命周期的钩子函数
    - activated  缓存激活   第一次会触发、组件能被看到
      - 一般根 created 做一样的事情：请求数据
    - deactivated 缓存失活   组件不能被看到
      -  一般根 beforeDestroy 做一样的事情: 清除定时器、移除全局事件监听

```javascript
 <keep-alive>
     <component :is="curPage"></component>
</keep-alive>
```

- keep-alive 的更多属性设置:

  1. include  包含

     1. include="组件1,组件2"    **注意 逗号前后不要有空格**
     2. :include="[组件1, 组件2]"
     3. :include="/^hello/"

  2. exclude  排除

     1. exclude="组件1,组件2"    **注意 逗号前后不要有空格**
     2. :exclude="[组件1, 组件2]"
     3. :exclude="/^hello/"

  3.  max    规定最大能缓存组件的数量，默认是没有限制的

     1. max=2    规定最大能缓存组件的数量为2
2. 假定缓存队列是 [home, list]
     3. 现在进入about的时候 about 也会被缓存上，这时会将之前的第一个给排出去 [home, list, about] => [list, about]**先进先出原则**
     
        

#### 32.  组件自定义事件

1. 一种组件间通信的方式，适用于：<strong style="color:red">子组件 ===> 父组件</strong>

2. 使用场景：A是父组件，B是子组件，B想给A传数据，那么就要在A中给B绑定自定义事件（<span style="color:red">事件的回调在A中</span>）。

3. 绑定自定义事件：

   1. 第一种方式，在父组件中：```<Demo @atguigu="test"/>```  或 ```<Demo v-on:atguigu="test"/>```

   2. 第二种方式，在父组件中：

      ```js
      <Demo ref="demo"/>
      ......
      mounted(){
         this.$refs.xxx.$on('atguigu',this.test)
      }
      ```

   3. 若想让自定义事件只能触发一次，可以使用```once```修饰符，或```$once```方法。

4. 触发自定义事件：```this.$emit('atguigu',数据)```    

5. 解绑自定义事件```this.$off('atguigu')```

6. 组件上也可以绑定原生DOM事件，需要使用```native```修饰符。

7. 注意：通过```this.$refs.xxx.$on('atguigu',回调)```绑定自定义事件时，回调<span style="color:red">要么配置在methods中</span>，<span style="color:red">要么用箭头函数</span>，否则this指向会出问题！

   

#### 33. Vue封装的过度与动画

1. 作用：在插入、更新或移除 DOM元素时，在合适的时候给元素添加样式类名。

2. 写法：

   1. 准备好样式：

      - 元素进入的样式：
        1. v-enter：进入的起点
        2. v-enter-active：进入过程中
        3. v-enter-to：进入的终点
      - 元素离开的样式：
        1. v-leave：离开的起点
        2. v-leave-active：离开过程中
        3. v-leave-to：离开的终点

   2. 使用```<transition>```包裹要过度的元素，并配置name属性：

      ```vue
      <transition name="hello">
         <h1 v-show="isShow">你好啊！</h1>
      </transition>
      ```

   3. 备注：若有多个元素需要过度，则需要使用：```<transition-group>```，且每个元素都要指定```key```值。

#### 34.  Vuex

##### 1.概念

​     在Vue中实现集中式状态（数据）管理的一个Vue插件，对vue应用中多个组件的共享状态进行集中式的管理（读/写），也是一种组件间通信的方式，且适用于任意组件间通信。

##### 2.何时使用？

​     多个组件需要共享数据时

##### 3.搭建vuex环境

1. 创建文件：```src/store/index.js```

   ```js
   //引入Vue核心库
   import Vue from 'vue'
   //引入Vuex
   import Vuex from 'vuex'
   //应用Vuex插件
   Vue.use(Vuex)
   
   //准备actions对象——响应组件中用户的动作
   const actions = {}
   //准备mutations对象——修改state中的数据
   const mutations = {}
   //准备state对象——保存具体的数据
   const state = {}
   
   //创建并暴露store
   export default new Vuex.Store({
      actions,
      mutations,
      state
   })
   ```

2. 在```main.js```中创建vm时传入```store```配置项

   ```js
   ......
   //引入store
   import store from './store'
   ......
   
   //创建vm
   new Vue({
      el:'#app',
      render: h => h(App),
      store
   })
   ```

#####    4.基本使用

1. 初始化数据、配置```actions```、配置```mutations```，操作文件```store.js```

   ```js
   //引入Vue核心库
   import Vue from 'vue'
   //引入Vuex
   import Vuex from 'vuex'
   //引用Vuex
   Vue.use(Vuex)
   
   const actions = {
       //响应组件中加的动作
      jia(context,value){
         // console.log('actions中的jia被调用了',miniStore,value)
         context.commit('JIA',value)
      },
   }
   
   const mutations = {
       //执行加
      JIA(state,value){
         // console.log('mutations中的JIA被调用了',state,value)
         state.sum += value
      }
   }
   
   //初始化数据
   const state = {
      sum:0
   }
   
   //创建并暴露store
   export default new Vuex.Store({
      actions,
      mutations,
      state,
   })
   ```

2. 组件中读取vuex中的数据：```$store.state.sum```

3. 组件中修改vuex中的数据：```$store.dispatch('action中的方法名',数据)``` 或 ```$store.commit('mutations中的方法名',数据)```

   >  备注：若没有网络请求或其他业务逻辑，组件中也可以越过actions，即不写```dispatch```，直接编写```commit```

##### 5.getters的使用

1. 概念：当state中的数据需要经过加工后再使用时，可以使用getters加工。

2. 在```store.js```中追加```getters```配置

   ```js
   ......
   
   const getters = {
     //state - 当前模块的state
     //getters - 当前模块的getters
     //rootState - 跟模块的State数据，根据他可以去获取到其余模块的state数据
     getter1(state,getters,rootState){
       
     },
      bigSum(state){
         return state.sum * 10
      }
   }
   
   //创建并暴露store
   export default new Vuex.Store({
      ......
      getters
   })
   ```

3. 组件中读取数据：```$store.getters.bigSum```

##### 6.四个map方法的使用

1. <strong>mapState方法：</strong>用于帮助我们映射```state```中的数据为计算属性

   ```js
   computed: {
       //借助mapState生成计算属性：sum、school、subject（对象写法）
        ...mapState({sum:'sum',school:'school',subject:'subject'}),
            
       //借助mapState生成计算属性：sum、school、subject（数组写法）
       ...mapState(['sum','school','subject']),
   },
   ```

2. <strong>mapGetters方法：</strong>用于帮助我们映射```getters```中的数据为计算属性

   ```js
   computed: {
       //借助mapGetters生成计算属性：bigSum（对象写法）
       ...mapGetters({bigSum:'bigSum'}),
   
       //借助mapGetters生成计算属性：bigSum（数组写法）
       ...mapGetters(['bigSum'])
   },
   ```

3. <strong>mapActions方法：</strong>用于帮助我们生成与```actions```对话的方法，即：包含```$store.dispatch(xxx)```的函数

   ```js
   methods:{
       //靠mapActions生成：incrementOdd、incrementWait（对象形式）
       ...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
   
       //靠mapActions生成：incrementOdd、incrementWait（数组形式）
       ...mapActions(['jiaOdd','jiaWait'])
   }
   ```

4. <strong>mapMutations方法：</strong>用于帮助我们生成与```mutations```对话的方法，即：包含```$store.commit(xxx)```的函数

   ```js
   methods:{
       //靠mapActions生成：increment、decrement（对象形式）
       ...mapMutations({increment:'JIA',decrement:'JIAN'}),
       
       //靠mapMutations生成：JIA、JIAN（对象形式）
       ...mapMutations(['JIA','JIAN']),
   }
   ```

> 备注：mapActions与mapMutations使用时，若需要传递参数需要：在模板中绑定事件时传递好参数，否则参数是事件对象。

##### 7.模块化+命名空间

1. 目的：让代码更好维护，让多种数据分类更加明确。

2. 修改```store.js```

   ```javascript
   const countAbout = {
     namespaced:true,//开启命名空间
     state:{x:1},
     mutations: { ... },
     actions: { ... },
     getters: {
       bigSum(state){
          return state.sum * 10
       }
     }
   }
   
   const personAbout = {
     namespaced:true,//开启命名空间
     state:{ ... },
     mutations: { ... },
     actions: { ... }
   }
   
   const store = new Vuex.Store({
     modules: {
       countAbout,
       personAbout
     }
   })
   ```

3. 开启命名空间后，组件中读取state数据：

   ```js
   //方式一：自己直接读取
   this.$store.state.personAbout.list
   //方式二：借助mapState读取：
   ...mapState('countAbout',['sum','school','subject']),
   ```

4. 开启命名空间后，组件中读取getters数据：

   ```js
   //方式一：自己直接读取
   this.$store.getters['personAbout/firstPersonName']
   //方式二：借助mapGetters读取：
   ...mapGetters('countAbout',['bigSum'])
   ```

5. 开启命名空间后，组件中调用dispatch

   ```js
   //方式一：自己直接dispatch
   this.$store.dispatch('personAbout/addPersonWang',person)
   //方式二：借助mapActions：
   ...mapActions('countAbout',{incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
   ```

6. 开启命名空间后，组件中调用commit

   ```js
   //方式一：自己直接commit
   this.$store.commit('personAbout/ADD_PERSON',person)
   //方式二：借助mapMutations：
   ...mapMutations('countAbout',{increment:'JIA',decrement:'JIAN'}),
   ```
   
   

 #### 35. 路由

1. 理解： 一个路由（route）就是一组映射关系（key - value），多个路由需要路由器（router）进行管理。
2. 前端路由：key是路径，value是组件。

##### 1.基本使用

1. 安装vue-router，命令：```npm i vue-router```

2. 应用插件：```Vue.use(VueRouter)```

3. 编写router配置项:

   ```js
   //引入VueRouter
   import VueRouter from 'vue-router'
   //引入Luyou 组件
   import About from '../components/About'
   import Home from '../components/Home'
   
   //创建router实例对象，去管理一组一组的路由规则
   const router = new VueRouter({
      routes:[
         {
            path:'/about',
            component:About
         },
         {
            path:'/home',
            component:Home
         }
      ]
   })
   
   //暴露router
   export default router
   ```

4. 实现切换（active-class可配置高亮样式）

   ```vue
   <router-link active-class="active" to="/about">About</router-link>
   ```

5. 指定展示位置

   ```vue
   <router-view></router-view>
   ```

##### 2.几个注意点

1. 路由组件通常存放在```pages```文件夹，一般组件通常存放在```components```文件夹。
2. 通过切换，“隐藏”了的路由组件，默认是被销毁掉的，需要的时候再去挂载。
3. 每个组件都有自己的```$route```属性，里面存储着自己的路由信息。
4. 整个应用只有一个router，可以通过组件的```$router```属性获取到。

##### 3.多级路由（多级路由）

1. 配置路由规则，使用children配置项：

   ```js
   routes:[
      {
         path:'/about',
         component:About,
      },
      {
         path:'/home',
         component:Home,
         children:[ //通过children配置子级路由
            {
               path:'news', //此处一定不要写：/news
               component:News
            },
            {
               path:'message',//此处一定不要写：/message
               component:Message
            }
         ]
      }
   ]
   ```

2. 跳转（要写完整路径）：

   ```vue
   <router-link to="/home/news">News</router-link>
   ```

##### 4.路由的query参数

1. 传递参数

   ```vue
   <!-- 跳转并携带query参数，to的字符串写法 -->
   <router-link :to="/home/message/detail?id=666&title=你好">跳转</router-link>
               
   <!-- 跳转并携带query参数，to的对象写法 -->
   <router-link 
      :to="{
         path:'/home/message/detail',
         query:{
            id:666,
               title:'你好'
         }
      }"
   >跳转</router-link>
   ```

2. 接收参数：

   ```js
   $route.query.id
   $route.query.title
   ```

##### 5.命名路由

1. 作用：可以简化路由的跳转。

2. 如何使用

   1. 给路由命名：

      ```js
      {
         path:'/demo',
         component:Demo,
         children:[
            {
               path:'test',
               component:Test,
               children:[
                  {
                            name:'hello' //给路由命名
                     path:'welcome',
                     component:Hello,
                  }
               ]
            }
         ]
      }
      ```

   2. 简化跳转：

      ```vue
      <!--简化前，需要写完整的路径 -->
      <router-link to="/demo/test/welcome">跳转</router-link>
      
      <!--简化后，直接通过名字跳转 -->
      <router-link :to="{name:'hello'}">跳转</router-link>
      
      <!--简化写法配合传递参数 -->
      <router-link 
         :to="{
            name:'hello',
            query:{
               id:666,
                  title:'你好'
            }
         }"
      >跳转</router-link>
      ```

##### 6.路由的params参数

1. 配置路由，声明接收params参数

   ```js
   {
      path:'/home',
      component:Home,
      children:[
         {
            path:'news',
            component:News
         },
         {
            component:Message,
            children:[
               {
                  name:'xiangqing',
                  path:'detail/:id/:title', //使用占位符声明接收params参数
                  component:Detail
               }
            ]
         }
      ]
   }
   ```

2. 传递参数

   ```vue
   <!-- 跳转并携带params参数，to的字符串写法 -->
   <router-link :to="/home/message/detail/666/你好">跳转</router-link>
               
   <!-- 跳转并携带params参数，to的对象写法 -->
   <router-link 
      :to="{
         name:'xiangqing',
         params:{
            id:666,
               title:'你好'
         }
      }"
   >跳转</router-link>
   ```

   > 特别注意：路由携带params参数时，若使用to的对象写法，则不能使用path配置项，必须使用name配置！

3. 接收参数：

   ```js
   $route.params.id
   $route.params.title
   ```

##### 7.路由的props配置

  作用：让路由组件更方便的收到参数

```js
{
   name:'xiangqing',
   path:'detail/:id',
   component:Detail,

   //第一种写法：props值为对象，该对象中所有的key-value的组合最终都会通过props传给Detail组件
   // props:{a:900}

   //第二种写法：props值为布尔值，布尔值为true，则把路由收到的所有params参数通过props传给Detail组件
   // props:true
   
   //第三种写法：props值为函数，该函数返回的对象中每一组key-value都会通过props传给Detail组件
   props(route){
      return {
         id:route.query.id,
         title:route.query.title
      }
   }
}
```

##### 8.```<router-link>```的replace属性

1. 作用：控制路由跳转时操作浏览器历史记录的模式
2. 浏览器的历史记录有两种写入方式：分别为```push```和```replace```，```push```是追加历史记录，```replace```是替换当前记录。路由跳转时候默认为```push```
3. 如何开启```replace```模式：```<router-link replace .......>News</router-link>```

##### 9.编程式路由导航

1. 作用：不借助```<router-link> ```实现路由跳转，让路由跳转更加灵活

2. 具体编码：

   ```js
   //$router的两个API
   this.$router.push({
      name:'xiangqing',
         params:{
            id:xxx,
            title:xxx
         }
   })
   
   this.$router.replace({
      name:'xiangqing',
         params:{
            id:xxx,
            title:xxx
         }
   })
   this.$router.forward() //前进
   this.$router.back() //后退
   this.$router.go() //可前进也可后退
   ```

##### 10.缓存路由组件

1. 作用：让不展示的路由组件保持挂载，不被销毁。

2. 具体编码：

   ```vue
   <keep-alive include="News"> 
       <router-view></router-view>
   </keep-alive>
   ```

##### 11.两个新的生命周期钩子

1. 作用：路由组件所独有的两个钩子，用于捕获路由组件的激活状态。
2. 具体名字：
   1. ```activated```路由组件被激活时触发。
   2. ```deactivated```路由组件失活时触发。

##### 12.路由守卫

1. 作用：对路由进行权限控制

2. 分类：全局守卫、独享守卫、组件内守卫

3. 全局守卫:

   ```js
   //全局前置守卫：初始化时执行、每次路由切换前执行
   router.beforeEach((to,from,next)=>{
      console.log('beforeEach',to,from)
      if(to.meta.isAuth){ //判断当前路由是否需要进行权限控制
         if(localStorage.getItem('school') === 'atguigu'){ //权限控制的具体规则
            next() //放行
         }else{
            alert('暂无权限查看')
            // next({name:'guanyu'})
         }
      }else{
         next() //放行
      }
   })
   
   //全局后置守卫：初始化时执行、每次路由切换后执行
   router.afterEach((to,from)=>{
      console.log('afterEach',to,from)
      if(to.meta.title){ 
         document.title = to.meta.title //修改网页的title
      }else{
         document.title = 'vue_test'
      }
   })
   ```

4. 独享守卫:

   ```js
   beforeEnter(to,from,next){
      console.log('beforeEnter',to,from)
      if(to.meta.isAuth){ //判断当前路由是否需要进行权限控制
         if(localStorage.getItem('school') === 'atguigu'){
            next()
         }else{
            alert('暂无权限查看')
            // next({name:'guanyu'})
         }
      }else{
         next()
      }
   }
   ```

5. 组件内守卫：

   ```js
   //进入守卫：通过路由规则，进入该组件时被调用
   beforeRouteEnter (to, from, next) {
   },
   //离开守卫：通过路由规则，离开该组件时被调用
   beforeRouteLeave (to, from, next) {
   }
   ```

##### 13.路由器的两种工作模式

1. 对于一个url来说，什么是hash值？—— #及其后面的内容就是hash值。
2. hash值不会包含在 HTTP 请求中，即：hash值不会带给服务器。
3. hash模式：
   1. 地址中永远带着#号，不美观 。
   2. 若以后将地址通过第三方手机app分享，若app校验严格，则地址会被标记为不合法。
   3. 兼容性较好。
4. history模式：
   1. 地址干净，美观 。
   2. 兼容性和hash模式相比略差。
   3. 应用部署上线时需要后端人员支持，解决刷新页面服务端404的问题。
   
   

#### 36. `$route` 与 `$router` 的区别

1. `$route` 是当前匹配的路由信息对象，可以通过他获取一些当前路由的一些信息。比如 `params`动态参数。
2. `$router` 就是 `new VueRouter()` 生成的那个实例对象，vue 将他挂载到了 Vue 的原型上面, 所以每个组件都通过访问，然后使用来完成编程式导航的一些操作



#### 37. 数据更新检测

- Vue是数据驱动的，如果某个数据类型是数组类型，在一些数组的操作下是可以更新页面的，还有一些数组的操作不会引起页面的更新。
- 下面的数组方法是可以引起页面更新的(编译方法)
  - unshift()    前面增加
  - push()        后面增加
  - shift()      前面删除
  - pop()         后面删除
  - splice()       高级方法删除、添加、删除
  - sort()          排序
  - reverse()    倒序
- 下面两种方式修改数组是不会引起页面的更新的：
  - 直接通过下标的方式修改数组   vm.arr[10]=“halo”
  - 通过length修改数组  vm.arr.length=num
  - 解决办法：
    - 1.使用 `Vue.set(target,index,value)`的静态方法
    - 2.使用实例对象 `vm.$set(target,index,value)` 方法
      - `Vue.set(target,index,value)`
      - target     要修改的数据源
      - index      要修改的下表
      - value        要修改成什么样
- 对象更新检测的问题
  - 直接给对象新增一个属性是不会引起页面更新的
  - 解决办法：
    - 使用`Vue.set(target,key,value)`或者`vm.$set(target,key,value)` 
    - `Vue.set(target,key,value)`
    - target     要添加的数据源
    - key      要添加的key
    - value        要修改成什么样



-------



### 002、Vue 3.0 基础

#### 1.Vue3简介

- 2020年9月18日，Vue.js发布3.0版本，代号：One Piece（海贼王）
- 耗时2年多、[2600+次提交](https://github.com/vuejs/vue-next/graphs/commit-activity)、[30+个RFC](https://github.com/vuejs/rfcs/tree/master/active-rfcs)、[600+次PR](https://github.com/vuejs/vue-next/pulls?q=is%3Apr+is%3Amerged+-author%3Aapp%2Fdependabot-preview+)、[99位贡献者](https://github.com/vuejs/vue-next/graphs/contributors) 
- github上的tags地址：https://github.com/vuejs/vue-next/releases/tag/v3.0.0



#### 2.Vue3带来了什么

##### 1.性能的提升

- 打包大小减少41%

- 初次渲染快55%, 更新渲染快133%

- 内存减少54%

  ......

##### 2.源码的升级

- 使用Proxy代替defineProperty实现响应式

- 重写虚拟DOM的实现和Tree-Shaking

  ......

##### 3.拥抱TypeScript

- Vue3可以更好的支持TypeScript

##### 4.新的特性

1. Composition API（组合API）

   - setup配置
   - ref与reactive
   - watch与watchEffect
   - provide与inject
   - ......
2. 新的内置组件
   - Fragment 
   - Teleport
   - Suspense
3. 其他改变

   - 新的生命周期钩子
   - data 选项应始终被声明为一个函数
   - 移除keyCode支持作为 v-on 的修饰符
   - ......



#### 3. 创建Vue3.0工程

##### 1.使用 vue-cli 创建

官方文档：https://cli.vuejs.org/zh/guide/creating-a-project.html#vue-create

```bash
## 查看@vue/cli版本，确保@vue/cli版本在4.5.0以上
vue --version
## 安装或者升级你的@vue/cli
npm install -g @vue/cli
## 创建
vue create vue_test
## 启动
cd vue_test
npm run serve
```

##### 2.使用 vite 创建

官方文档：https://v3.cn.vuejs.org/guide/installation.html#vite

vite官网：https://vitejs.cn

- 什么是vite？—— 新一代前端构建工具。
- 优势如下：
  - 开发环境中，无需打包操作，可快速的冷启动。
  - 轻量快速的热重载（HMR）。
  - 真正的按需编译，不再等待整个应用编译完成。

```bash
## 创建工程
npm init vite-app <project-name>
## 进入工程目录
cd <project-name>
## 安装依赖
npm install
## 运行
npm run dev
```



#### 4. 常用 Composition API

官方文档: https://v3.cn.vuejs.org/guide/composition-api-introduction.html

##### 1.拉开序幕的setup

1. 理解：Vue3.0中一个新的配置项，值为一个函数。
2. setup是所有<strong style="color:#DD5145">Composition API（组合API）</strong><i style="color:gray;font-weight:bold">“ 表演的舞台 ”</i>。
4. 组件中所用到的：数据、方法等等，均要配置在setup中。
5. setup函数的两种返回值：
   1. 若返回一个对象，则对象中的属性、方法, 在模板中均可以直接使用。（重点关注！）
   2. <span style="color:#aad">若返回一个渲染函数：则可以自定义渲染内容。（了解）</span>
6. 注意点：
   1. 尽量不要与Vue2.x配置混用
      - Vue2.x配置（data、methos、computed...）中<strong style="color:#DD5145">可以访问到</strong>setup中的属性、方法。
      - 但在setup中<strong style="color:#DD5145">不能访问到</strong>Vue2.x配置（data、methods、computed...）。
      - 如果有重名, setup优先。
   2. setup不能是一个async函数，因为返回值不再是return的对象, 而是promise, 模板看不到return对象中的属性。（后期也可以返回一个Promise实例，但需要Suspense和异步组件的配合）

#####  2.ref函数

- 作用: 定义一个响应式的数据
- 语法: ```const xxx = ref(initValue)``` 
  - 创建一个包含响应式数据的<strong style="color:#DD5145">引用对象（reference对象，简称ref对象）</strong>。
  - JS中操作数据： ```xxx.value```
  - 模板中读取数据: 不需要.value，直接：```<div>{{xxx}}</div>```
- 备注：
  - 接收的数据可以是：基本类型、也可以是对象类型。
  - 基本类型的数据：响应式依然是靠``Object.defineProperty()``的```get```与```set```完成的。
  - 对象类型的数据：内部 <i style="color:gray;font-weight:bold">“ 求助 ”</i> 了Vue3.0中的一个新函数—— ```reactive```函数。

##### 3.reactive函数

- 作用: 定义一个<strong style="color:#DD5145">对象类型</strong>的响应式数据（基本类型不要用它，要用```ref```函数）
- 语法：```const 代理对象= reactive(源对象)```接收一个对象（或数组），返回一个<strong style="color:#DD5145">代理对象（Proxy的实例对象，简称proxy对象）</strong>
- reactive定义的响应式数据是“深层次的”。
- 内部基于 ES6 的 Proxy 实现，通过代理对象操作源对象内部数据进行操作。

##### 4. reactive对比ref

-  从定义数据角度对比：
   -  ref用来定义：<strong style="color:#DD5145">基本类型数据</strong>。
   -  reactive用来定义：<strong style="color:#DD5145">对象（或数组）类型数据</strong>。
   -  备注：ref也可以用来定义<strong style="color:#DD5145">对象（或数组）类型数据</strong>, 它内部会自动通过```reactive```转为<strong style="color:#DD5145">代理对象</strong>。
-  从原理角度对比：
   -  ref通过``Object.defineProperty()``的```get```与```set```来实现响应式（数据劫持）。
   -  reactive通过使用<strong style="color:#DD5145">Proxy</strong>来实现响应式（数据劫持）, 并通过<strong style="color:#DD5145">Reflect</strong>操作<strong style="color:orange">源对象</strong>内部的数据。
-  从使用角度对比：
   -  ref定义的数据：操作数据<strong style="color:#DD5145">需要</strong>```.value```，读取数据时模板中直接读取<strong style="color:#DD5145">不需要</strong>```.value```。
   -  reactive定义的数据：操作数据与读取数据：<strong style="color:#DD5145">均不需要</strong>```.value```。
   
   

#### 5. Vue3.0中的响应式原理

##### 1. vue2.x的响应式

- 实现原理：
  - 对象类型：通过```Object.defineProperty()```对属性的读取、修改进行拦截（数据劫持）。
  
  - 数组类型：通过重写更新数组的一系列方法来实现拦截。（对数组的变更方法进行了包裹）。
  
    ```js
    Object.defineProperty(data, 'count', {
        get () {}, 
        set () {}
    })
    ```

- 存在问题：
  - 新增属性、删除属性, 界面不会更新。
  - 直接通过下标修改数组, 界面不会自动更新。

##### 2. Vue3.0的响应式

- 实现原理: 
  - 通过Proxy（代理）:  拦截对象中任意属性的变化, 包括：属性值的读写、属性的添加、属性的删除等。
  - 通过Reflect（反射）:  对源对象的属性进行操作。
  - MDN文档中描述的Proxy与Reflect：
    - Proxy：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy
    
    - Reflect：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect
    
      ```js
      new Proxy(data, {
        // 拦截读取属性值
          get (target, prop) {
            return Reflect.get(target, prop)
          },
          // 拦截设置属性值或添加新属性
          set (target, prop, value) {
            return Reflect.set(target, prop, value)
          },
          // 拦截删除属性
          deleteProperty (target, prop) {
            return Reflect.deleteProperty(target, prop)
          }
      })
      
      proxy.name = 'tom'   
      ```
      
      

#### 6.setup的两个注意点

- setup执行的时机
  - 在beforeCreate之前执行一次，this是undefined。
  
- setup的参数
  - props：值为对象，包含：组件外部传递过来，且组件内部声明接收了的属性。
  - context：上下文对象
    - attrs: 值为对象，包含：组件外部传递过来，但没有在props配置中声明的属性, 相当于 ```this.$attrs```。
    - slots: 收到的插槽内容, 相当于 ```this.$slots```。
    - emit: 分发自定义事件的函数, 相当于 ```this.$emit```。
    
      


#### 7.计算属性与监视

##### 1.computed函数

- 与Vue2.x中computed配置功能一致

- 写法

  ```js
  import {computed} from 'vue'
  
  setup(){
      ...
    //计算属性——简写
      let fullName = computed(()=>{
          return person.firstName + '-' + person.lastName
      })
      //计算属性——完整
      let fullName = computed({
          get(){
              return person.firstName + '-' + person.lastName
          },
          set(value){
              const nameArr = value.split('-')
              person.firstName = nameArr[0]
              person.lastName = nameArr[1]
          }
      })
  }
  ```

##### 2.watch函数

- 与Vue2.x中watch配置功能一致

- 两个小“坑”：

  - 监视reactive定义的响应式数据时：oldValue无法正确获取、强制开启了深度监视（deep配置失效）。
  - 监视reactive定义的响应式数据中某个属性时：deep配置有效。
  
  ```js
  //情况一：监视ref定义的响应式数据
  watch(sum,(newValue,oldValue)=>{
    console.log('sum变化了',newValue,oldValue)
  },{immediate:true})
  
  //情况二：监视多个ref定义的响应式数据
  watch([sum,msg],(newValue,oldValue)=>{
    console.log('sum或msg变化了',newValue,oldValue)
  }) 
  
  /* 情况三：监视reactive定义的响应式数据
        若watch监视的是reactive定义的响应式数据，则无法正确获得oldValue！！
        若watch监视的是reactive定义的响应式数据，则强制开启了深度监视 
  */
  watch(person,(newValue,oldValue)=>{
    console.log('person变化了',newValue,oldValue)
  },{immediate:true,deep:false}) //此处的deep配置不再奏效
  
  //情况四：监视reactive定义的响应式数据中的某个属性
  watch(()=>person.job,(newValue,oldValue)=>{
    console.log('person的job变化了',newValue,oldValue)
  },{immediate:true,deep:true}) 
  
  //情况五：监视reactive定义的响应式数据中的某些属性
  watch([()=>person.job,()=>person.name],(newValue,oldValue)=>{
    console.log('person的job变化了',newValue,oldValue)
  },{immediate:true,deep:true})
  
  //特殊情况
  watch(()=>person.job,(newValue,oldValue)=>{
      console.log('person的job变化了',newValue,oldValue)
  },{deep:true}) //此处由于监视的是reactive素定义的对象中的某个属性，所以deep配置有效
  ```

##### 3.watchEffect函数

- watch的套路是：既要指明监视的属性，也要指明监视的回调。

- watchEffect的套路是：不用指明监视哪个属性，监视的回调中用到哪个属性，那就监视哪个属性。

- watchEffect有点像computed：

  - 但computed注重的计算出来的值（回调函数的返回值），所以必须要写返回值。
  - 而watchEffect更注重的是过程（回调函数的函数体），所以不用写返回值。

  ```js
  //watchEffect所指定的回调中用到的数据只要发生变化，则直接重新执行回调。
  watchEffect(()=>{
      const x1 = sum.value
      const x2 = person.age
      console.log('watchEffect配置的回调执行了')
  })
  ```

#### 8. 生命周期

- Vue3.0中可以继续使用Vue2.x中的生命周期钩子，但有有两个被更名：
  - ```beforeDestroy```改名为 ```beforeUnmount```
  - ```destroyed```改名为 ```unmounted```
- Vue3.0也提供了 Composition API 形式的生命周期钩子，与Vue2.x中钩子对应关系如下：
  - `beforeCreate`===>`setup()`
  - `created`=======>`setup()`
  - `beforeMount` ===>`onBeforeMount`
  - `mounted`=======>`onMounted`
  - `beforeUpdate`===>`onBeforeUpdate`
  - `updated` =======>`onUpdated`
  - `beforeUnmount` ==>`onBeforeUnmount`
  - `unmounted` =====>`onUnmounted`

#### 9.自定义hook函数

- 什么是hook？—— 本质是一个函数，把setup函数中使用的Composition API进行了封装。

- 类似于vue2.x中的mixin。

- 自定义hook的优势: 复用代码, 让setup中的逻辑更清楚易懂。



#### 10.toRef

- 作用：创建一个 ref 对象，其value值指向另一个对象中的某个属性。
- 语法：```const name = toRef(person,'name')```
- 应用:   要将响应式对象中的某个属性单独提供给外部使用时。


- 扩展：```toRefs``` 与```toRef```功能一致，但可以批量创建多个 ref 对象，语法：```toRefs(person)```

  


#### 11. 其它 Composition API

##### 1.shallowReactive 与 shallowRef

- shallowReactive：只处理对象最外层属性的响应式（浅响应式）。
- shallowRef：只处理基本数据类型的响应式, 不进行对象的响应式处理。

- 什么时候使用?
  -  如果有一个对象数据，结构比较深, 但变化时只是外层属性变化 ===> shallowReactive。
  -  如果有一个对象数据，后续功能不会修改该对象中的属性，而是生新的对象来替换 ===> shallowRef。

##### 2.readonly 与 shallowReadonly

- readonly: 让一个响应式数据变为只读的（深只读）。
- shallowReadonly：让一个响应式数据变为只读的（浅只读）。
- 应用场景: 不希望数据被修改时。

##### 3.toRaw 与 markRaw

- toRaw：
  - 作用：将一个由```reactive```生成的<strong style="color:orange">响应式对象</strong>转为<strong style="color:orange">普通对象</strong>。
  - 使用场景：用于读取响应式对象对应的普通对象，对这个普通对象的所有操作，不会引起页面更新。
- markRaw：
  - 作用：标记一个对象，使其永远不会再成为响应式对象。
  - 应用场景:
    1. 有些值不应被设置为响应式的，例如复杂的第三方类库等。
    2. 当渲染具有不可变数据源的大列表时，跳过响应式转换可以提高性能。

##### 4.customRef

- 作用：创建一个自定义的 ref，并对其依赖项跟踪和更新触发进行显式控制。

- 实现防抖效果：

  ```vue
  <template>
    <input type="text" v-model="keyword">
    <h3>{{keyword}}</h3>
  </template>
  
  <script>
    import {ref,customRef} from 'vue'
    export default {
      name:'Demo',
      setup(){
        // let keyword = ref('hello') //使用Vue准备好的内置ref
        //自定义一个myRef
        function myRef(value,delay){
          let timer
          //通过customRef去实现自定义
          return customRef((track,trigger)=>{
            return{
              get(){
                track() //告诉Vue这个value值是需要被“追踪”的
                return value
              },
              set(newValue){
                clearTimeout(timer)
                timer = setTimeout(()=>{
                  value = newValue
                  trigger() //告诉Vue去更新界面
                },delay)
              }
            }
          })
        }
        let keyword = myRef('hello',500) //使用程序员自定义的ref
        return {
          keyword
        }
      }
    }
  </script>
  ```

  

#### 12.provide 与 inject

- 作用：实现<strong style="color:#DD5145">祖与后代组件间</strong>通信

- 套路：父组件有一个 `provide` 选项来提供数据，后代组件有一个 `inject` 选项来开始使用这些数据

- 具体写法：

  1. 祖组件中：

     ```js
     setup(){
      ......
         let car = reactive({name:'奔驰',price:'40万'})
         provide('car',car)
         ......
     }
     ```

  2. 后代组件中：

     ```js
     setup(props,context){
      ......
         const car = inject('car')
         return {car}
      ......
     }
     ```
     
     

#### 12.响应式数据的判断

- isRef: 检查一个值是否为一个 ref 对象

- isReactive: 检查一个对象是否是由 `reactive` 创建的响应式代理

- isReadonly: 检查一个对象是否是由 `readonly` 创建的只读代理

- isProxy: 检查一个对象是否是由 `reactive` 或者 `readonly` 方法创建的代理

  

#### 13. Composition API 的优势

##### 1.Options API 存在的问题

使用传统OptionsAPI中，新增或者修改一个需求，就需要分别在data，methods，computed里修改 。

<div style="width:600px;height:370px;overflow:hidden;float:left">
    <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f84e4e2c02424d9a99862ade0a2e4114~tplv-k3u1fbpfcp-watermark.image" style="width:600px;float:left" />
</div>
<div style="width:300px;height:370px;overflow:hidden;float:left">
    <img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e5ac7e20d1784887a826f6360768a368~tplv-k3u1fbpfcp-watermark.image" style="zoom:50%;width:560px;left" /> 
</div>


















##### 2.Composition API 的优势

我们可以更加优雅的组织我们的代码，函数。让相关功能的代码更加有序的组织在一起。

<div style="width:500px;height:340px;overflow:hidden;float:left">
    <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bc0be8211fc54b6c941c036791ba4efe~tplv-k3u1fbpfcp-watermark.image"style="height:360px"/>
</div>
<div style="width:430px;height:340px;overflow:hidden;float:left">
    <img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6cc55165c0e34069a75fe36f8712eb80~tplv-k3u1fbpfcp-watermark.image"style="height:360px"/>
</div>




















#### 14. 新的组件

##### 1.Fragment

- 在Vue2中: 组件必须有一个根标签
- 在Vue3中: 组件可以没有根标签, 内部会将多个标签包含在一个Fragment虚拟元素中
- 好处: 减少标签层级, 减小内存占用

##### 2.Teleport

- 什么是Teleport？—— `Teleport` 是一种能够将我们的<strong style="color:#DD5145">组件html结构</strong>移动到指定位置的技术。

  ```vue
  <teleport to="移动位置">
    <div v-if="isShow" class="mask">
      <div class="dialog">
        <h3>我是一个弹窗</h3>
        <button @click="isShow = false">关闭弹窗</button>
      </div>
    </div>
  </teleport>
  ```

##### 3.Suspense

- 等待异步组件时渲染一些额外内容，让应用有更好的用户体验

- 使用步骤：

  - 异步引入组件

    ```js
    import {defineAsyncComponent} from 'vue'
    const Child = defineAsyncComponent(()=>import('./components/Child.vue'))
    ```

  - 使用```Suspense```包裹组件，并配置好```default``` 与 ```fallback```

    ```vue
    <template>
      <div class="app">
        <h3>我是App组件</h3>
        <Suspense>
          <template v-slot:default>
            <Child/>
          </template>
          <template v-slot:fallback>
            <h3>加载中.....</h3>
          </template>
        </Suspense>
      </div>
    </template>
    ```

#### 15. 其他

##### 1.全局API的转移

- Vue 2.x 有许多全局 API 和配置。
  - 例如：注册全局组件、注册全局指令等。

    ```js
    //注册全局组件
    Vue.component('MyButton', {
      data: () => ({
        count: 0
      }),
      template: '<button @click="count++">Clicked {{ count }} times.</button>'
    })
    
    //注册全局指令
    Vue.directive('focus', {
      inserted: el => el.focus()
    }
    ```

- Vue3.0中对这些API做出了调整：

  - 将全局的API，即：```Vue.xxx```调整到应用实例（```app```）上

    | 2.x 全局 API（```Vue```） | 3.x 实例 API (`app`)                        |
    | ------------------------- | ------------------------------------------- |
    | Vue.config.xxxx           | app.config.xxxx                             |
    | Vue.config.productionTip  | <strong style="color:#DD5145">移除</strong> |
    | Vue.component             | app.component                               |
    | Vue.directive             | app.directive                               |
    | Vue.mixin                 | app.mixin                                   |
    | Vue.use                   | app.use                                     |
    | Vue.prototype             | app.config.globalProperties                 |
  

2.其他改变

- data选项应始终被声明为一个函数。

- 过度类名的更改：

  - Vue2.x写法

    ```css
    .v-enter,
    .v-leave-to {
      opacity: 0;
    }
    .v-leave,
    .v-enter-to {
      opacity: 1;
    }
    ```

  - Vue3.x写法

    ```css
    .v-enter-from,
    .v-leave-to {
      opacity: 0;
    }
    
    .v-leave-from,
    .v-enter-to {
      opacity: 1;
    }
    ```

- <strong style="color:#DD5145">移除</strong>keyCode作为 v-on 的修饰符，同时也不再支持```config.keyCodes```

- <strong style="color:#DD5145">移除</strong>```v-on.native```修饰符

  - 父组件中绑定事件

    ```vue
    <my-component
      v-on:close="handleComponentEvent"
      v-on:click="handleNativeClickEvent"
    />
    ```

  - 子组件中声明自定义事件

    ```vue
    <script>
      export default {
        emits: ['close']
      }
    </script>
    ```

- <strong style="color:#DD5145">移除</strong>过滤器（filter）

  > 过滤器虽然这看起来很方便，但它需要一个自定义语法，打破大括号内表达式是 “只是 JavaScript” 的假设，这不仅有学习成本，而且有实现成本！建议用方法调用或计算属性去替换过滤器。

- ......

## 06、React

### 001、React 类组件基础

#### 1、react简介

>          React 起源于 Facebook 的内部项目，因为该公司对市场上所有 JavaScript MVC 框 架，都不满意，就决定自己写一套，用来架设Instagram 的网站。做出来以后，发现这套 东西很好用，就在2013年5月开源了。



#### 2、前端三大框架

| 框架名  | 出现时间 |   所属   |               一开始特色                |
| :-----: | :------: | :------: | :-------------------------------------: |
| Angular |  2009年  |   谷歌   |         指令系统、双向数据绑定          |
|  React  |  2013年  | Facebook |             虚拟DOM、组件化             |
|   Vue   |  2015年  |  尤玉溪  | 指令系统、双向数据绑定、虚拟DOM、组件化 |



#### 3、react 的特点

1. **组件** - 通过React构建组件，使得代码更加容易得到复用，能够很好的应用在大项目的开发中 
2. **高效** - React 通过对Dom的模拟（虚拟Dom),最大限度减少与Dom的交互
3. **单项响应的数据流** - React 实现了单项响应的数据流，从而减少了重复代码，这也是它为什么比传统的绑定更简单。
4. 声明式设计 - React采用声明范式，可以轻松描述应用
5. JSX - JSX 是 JavaScript 的语法扩展
6. 灵活 - React 可以与已知的库或框架很好的配合



#### 4、JSX

> ​		JSX 将 HTML 语法直接加入到 JavaScript 代码中，再通过翻译器转换到纯 JavaScript 后由浏览器执行。在实际开发中，JSX 在产品打包阶段都已经编译成纯 JavaScript，不会带来任何副作用，反而会让代码更加直观并易于维护。 编译过程由Babel 的 JSX 编译器实现。

**JSX 的特点：**

**1.  定义虚拟Dom的时候不要写引号**

**2.  只能有一个根标签**

**3.  给标签添加样式类名，不能用class 要使用 className**

**4.  标签中要混入js 表达式的时候，要用{}**

**5.  要使用双标签 或者 自闭标签**

**6.  标签首字母：**

  **（1）若小写字母开头，则将改标签为html中同名元素，若 html中没有改标签对应的元素则报错。**

  **（2）若大写字母开头，React就会渲染对应的组件，若组件没有定义，则报错**



#### 5、函数式编程的好处

1. 代码简洁，开发快速
2. 接近自然语言，易于理解
3. 更方便的代码管理
4. 易于"并发编程“
5. 代码的热升级

>       React把过去不断重复构建UI的过程抽象成了组件，且在给定参数的情况下约定渲染对应的UI界面。React能充分利用很多函数式方法去减少冗余代码。此外，由于它本身就是简单函数，所以易于测试。可以说，函数式编程才是React的精髓。



#### 6、react 起步

**1.全局安装 `create-react-app` 脚手架**

```bash
$ npm i -g create-react-app
```

**OR**

```bash
$ npx create-react-app xxxx  //xxxx 是项目文件夹的名称
```



  3.2.创建项目文件夹**

```bash
$ create-react-app xxxx  //xxxx 是项目文件夹的名称
```



#### 7、HOOKS

>        Hooks是一组函数API，16.7版本前 react 函数式组件不存在状态和生命周期，Hooks给函数式组件提供了类似class组件的api，使函数组件功能类似于class一样。但是在Class类内部，不可以使用hooks.

1. useState
2. uesRef
3. useCallback
4. useEffect/useLayoutEffect
5. useReducer/useContext



#### 8、受控组件

>       在React中，每当表单元素的状态发生变化时，都会被写入到组件的state中，这种组件在React被称为受控组件。



#### 9、antd

>        一个方便极速开发应用的插件 Ant Design ，这些相当于帮我们封装了常用的组件，我们直接拿来用就行。



#### 10、webpack

>       webpack可以看做是**模块打包机**：它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其打包为合适的格式以供浏览器使用。

webpack四大核心：

1. entry   //入口
2. output    //出口
3. loader    
4. pulgins    //插件
   1. `HtmlWebpackPlugin`
   2. `webpack.HotModuleReplacementPlugin`
   3. `webpack.NamedModulesPlugin`
   4. `webpack.HashedModuleIdsPlugin`
   5. `uglifyJsPlugin`
   6. `ExtractTextPlugin`



#### 11、平时还需下载哪些包

1.  `http-proxy-middleware`  //配置反向代理
2.  `axios`   //发送http请求
3.  `webpack-dev-server`
4.  `antd`
5.  `redux`
6.  `react-redux`
7.  `redux-promise`
8.  `redux-thunk`
9.  `echarts`



#### 12、声明式



#### 13、绑定事件

1. 绑定事件的属性的命名方式是采用的小驼峰式的命名方式，因为你react是更加的接近js而不是html 
2. 在绑定事件后面添加的名称不是字符串的形式，而是一个函数的方式。



#### 14、Flux

>       FLUX 是一种思想架构。专门解决软件的结构问题。它跟MVC架构是同一类东西，但是更加简单和清晰。
>
>       Redux  跟 React 是配合的最好的。



#### 15、单向数据流

>       React的特性中有一个概念叫做“单项数据流”，从而减少了重复代码，这也是它为什么比传统的绑定更简单。
>
>       在 React.js 中，数据是从上自下流动（传递）的，也就是一个父组件可以把它的 state / props 通过 props 传递给它的子组件，但是子组件不能修改 props - React.js 是单向数据流，如果子组件需要修改父组件状态（数据），是通过回调函数方式来完成的





--------



### 002、React Hooks 基础

### 003、React diff 算法

>    React 提供的声明式 API 让开发者可以在对 React 的底层实现并不了解的情况下编写应用。本文描述了在实现 React 的 “diffing” 算法过程中所作出的设计决策，以保证组件更新可预测，且在繁杂业务场景下依然保持应用的高性能。

#### 1、设计动机

- 当组件某一时间点调用 react 的 render() 方法以后，会创建一棵 React 元素的 dom 树。 在下一次state 或者 props 发生改变的时候，render() 会被重新调用，生成一棵新的 dom 树。React 需要根据两棵树之间的差别来判断如何高效的更新 UI ，以保证当前 UI 与最新的 dom 树保持同步。
- React 需要根据两棵树之间的差别来判断如何高效的更新 UI ，根据现有最优算法，复杂程度依然需要0(n^3) , 其中 n 是 dom 树种元素的数量。（此算法耗时很长，对dom 树的改动最小。）
- 于是 React 在以下两个假设的基础之上提出了一套0(n) 的算法方案：
  1. 两个不同类型的元素会产生出不同的树；
  2. 开发者可以通过设置 `key` 属性，来告知渲染哪些子元素在不同的渲染下可以保存不变；

#### 2、Diff 算法

>    当对比两棵 dom 树时，React 首先比较两棵树的根节点。不同类型的根节点元素会有不同的形态。对比不同类型的元素

##### 2.1 对比不同类型的元素

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

##### 2.2 对比同类型元素：

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

##### 2.3 对比同类型的组件元素：

- 当一个组件更新时，组件实例会保持不变，因此可以在不同的渲染时保持 state 一致。React 将更新该组件实例的 props 以保证与最新的元素保持一致，并且调用该实例的 `UNSAFE_componentWillReceiveProps()`、`UNSAFE_componentWillUpdate()` 以及 `componentDidUpdate()` 方法。
- 下一步，调用 `render()` 方法，diff 算法将在之前的结果以及新的结果中进行递归。

##### 2.4  子节点进行递归：no key

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

##### 2.5  子节点进行递归：have key

>    为了解决上述问题，React 引入了 `key` 属性。当子元素拥有 key 时，React 使用 key 来匹配原有树上的子元素以及最新树上的子元素。以下示例在新增 `key` 之后，使得树的转换效率得以提高：

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

#### 3、diff 算法面试问题：

##### 3.1 说一下虚拟dom？

- Virtual DOM 是一种编程概念。
- UI 以一种理想化的，或者说“虚拟的”表现形式被保存于内存中。
- 并通过如 ReactDOM 等类库使之与“真实的” DOM 同步。这一过程叫做协。调

##### 3.2 说一下react diff 算法？

-  `diff 算法`是` React `在某一时间会调用`render()`渲染函数，生成`React` 元素节点的 `dom` 树，当组件的 `state` 或者是 `props` 发生改变，重新调用`render()` 渲染函数，返回一棵不同的树。`React` 需要基于这两棵树之间的差别来判断如何高效的更新 UI，以保证当前 UI 与最新的树保持同步。

##### 3.3 说一下 diff 算法 key 的作用？

- diff 算法中使用的 key 是用来做标识符，提高 diff 算法的对比效率 。
- 当标识 key 以后，react 就知道具体那个key 发生了改变，对 dom 元素做增删改，不会重绘所有子元素。

##### 3.4 说一下 diff 算法 key 如果没有会怎么样？

- 开发环境会提示报错缺少 key 。
- 会导致子元素进行重绘，重走生命周期。消耗多余的性能。

##### 3.5 说一下 diff 算法 key 如果使用 index 合适吗？

- 这个 key 不需要全局唯一，但在列表中需要保持唯一。
- 不推荐使用 index 下标来充当子元素的 key。元素在进行重新排序时，如果有顺序修改，diff 就会变慢。
- 当子元素中含有非受控组件的时候，导致非受控组件的 state（比如输入框）可能相互篡改，会出现无法预期的变动。



-----------





## 07、小程序

## 08、移动端

### 001、ios Safari浏览器点击300ms延迟 ？

解决方法：



### 002、ios 全面屏高度百分百情况下会有安全区域，高度100vh会被浏览器遮挡？

解决方法：

在项目reset.css代码中添加一下代码

```css
/* // ios底部横条处理 */
@supports (bottom: env(safe-area-inset-bottom)) {
  .footer-ios {
    padding-bottom: env(safe-area-inset-bottom);
  }
}
```

在html中添加meta

```html
    <meta name="viewport" content="width=device-width, user-scalable=no,initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no, viewport-fit=cover" />

//  viewport-fit=cover
```

注意： 页面最外层不要写padding-bottom 会被覆盖



### 003、IOS移除橡皮筋功能

解决方法：

1. 下载`inobounce`的包

```bash
$ npm i inobounce -S
```

2. 在页面调用这个方法

```typescript
/**
 * 禁用ios橡皮筋
 */
React.useEffect(() => {
  const u = navigator.userAgent
  if (u.indexOf('iPhone') > -1) {
    inobounce.enable()
  }
  return () => {
    inobounce.disable()
  }
}, [])

```

3. 同时要在路由页面最外层加高度和样式 

```css
#root {
  height: 100%;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
}
```

## 09、数据结构与算法

### 001、栈结构

>    栈（Stack）是常见的数据结构。

- **数组**是一个线性结构，并且可以在数组的**任意位置**插入和删除元素。
- **栈（Stack）**和**队列**就是比较常见的受限的线性结构。
- 栈的特点为： 先进后出，后进先出（LIFO: last in first out）

#### 1、程序中的栈结构

- **函数调用栈：** A( B( C( D() ) ) ) :  即A函数中调用B，B调用C，C调用D；在A执行的过程中会将A压入栈，随后B执行时B也被压入栈，函数C和D执行时也会被压入栈。所以当前栈的顺序为：A->B->C->D（栈顶）；函数D执行完之后，会弹出栈被释放，弹出栈的顺序为D->C->B->A。
- **递归：** 为什么没有停止条件的递归会造成栈溢出？比如函数A为递归函数，不断地调用自己（因为函数还没有执行完，不会把函数弹出栈），不停地把相同的函数A压入栈，最后造成**栈溢出**（Stack Overfloat）。

#### 2、栈结构中常见的操作

- **`push(el)`:** 压栈，添加一个新元素到栈顶的位置。
- **`pop()`：** 出栈： 移除栈顶的元素，同时返回被移除的元素。
- **`peek()`：** 返回栈顶的元素，不对栈做任何的修改（该方法不会移除栈顶的元素，仅仅返回栈顶元素）。
- **`isEmpty()`：**如果栈里没有任何元素就返回true，否则返回false。
- **`size()`：** 返回栈内的元素个数。这个方法和数组的length属性类似。
- **`toString()`：**将站内的结构的内容以字符串的形式返回。

#### 3、基于JavaScript封装-栈(Stack)类

```javascript
// 封装 JavaScript Stack 结构
class Stack {
  constructor() {
    this.items=[]
  }
  // 1. push(item): 实现压栈方法 push, 没有返回值.
  push(item) {
    this.items.push(item)
  }

  // 2. pop(): 出栈的方法 pop, 返回值是出栈的元素
  pop() {
    return this.items.pop()
  }

  // 3. peek(): 查看一下栈顶元素
  peek() {
    return this.items[this.items.length - 1]
  }

  // 4. isEmpty(): 判断栈内是否为空
  isEmpty() {
    return !this.items.length
  }

  // 5. size(): 获取栈中元素的个数
  size() {
    return this.items.length
  }

  // 6. toString(): 以字符串形式输出栈内数据
  toString() {
    // 期望输出形式 20 10 12 8 
    return this.items.join(' ')
  }
}


// 解析一:
const stack1 = new Stack()
stack1.push(20)
stack1.push(10)
stack1.push(12)
stack1.push(8)

console.log(`stack1.pop()`, stack1.pop()) // 8
console.log(`stack1.pop()`, stack1.pop()) // 12
console.log(`stack1.peek()`, stack1.peek()) // 10
console.log(`stack1.isEmpty()`, stack1.isEmpty())  // false
console.log(`stack1.size()`, stack1.size()) // 2
console.log(`stack1.toString()`, stack1.toString())  // 20 10
```

#### 4、栈结构的应用

**4.1、封装函数将十进制转化成而二进制(十进制转二进制的运算最后倒序取余数的特点符合栈 '先进后出')**

```javascript
// 解析： 十进制转换二进制明白原理就OK，就是不断的进行除以2，将余数推进栈内，一直到商等于0。
// 最后从栈内去除数字拼接成字符串
const dec2bin = decNumber => {
  const Stack2 = new Stack()
  while(decNumber > 0) {
    Stack2.push(decNumber % 2)
    decNumber =  Math.floor(decNumber / 2)
  }
  let str = ''
  while(!Stack2.isEmpty()) {
    str += Stack2.pop()
  }
  return str
}

console.log(`dec2bin`, dec2bin(10))
console.log(`dec2bin`, dec2bin(100))
console.log(`dec2bin`, dec2bin(1000))
```

**4.2、有6个元素6，5，4，3，2，1按顺序进栈，问下列哪一个不是合法的出栈顺序？**

- A：5 4 3 6 1 2 （√）
- B：4 5 3 2 1 6 （√）
- C：3 4 6 5 2 1 （×）
- D：2 3 4 1 5 6 （√）

**分析: 题目所说的按顺序进栈指的不是一次性全部进栈，而是有进有出，进栈顺序为6 -> 5 -> 4 -> 3 -> 2 -> 1。**

- A: 6进栈,5进栈出栈,4进栈出栈,3进栈出栈,6出栈,2进栈,1进栈出栈,2出栈. √

- B: 65进栈,4进栈出栈,5出栈,3进栈出栈,2进栈出栈,1进栈出栈,6出栈.√

* C: 654进栈,3进栈出栈,4出栈,此时栈内还剩65,必须5先出栈,6才可以出栈.×

* D: 6543进栈,2进栈出栈,3出栈,4出栈,1进栈出栈,5出栈,6出栈.√

4.3、**编写一个函数，该函数接受一个括号字符串，并确定括号的顺序是否有效。如果字符串有效，函数应返回true；如果字符串无效，函数应返回false。**

```javascript
// 分析:
// 遇到左括号，就把做括号压入栈中
// 遇到右括号，判断栈是否为空，如果为空则说明没有左括号与之相对应，字符串括号不合法。如果栈不为空，则把栈顶元素移除，这对括号就抵消了。
// 当for循环结束，如果栈是空的，说明所有的左右括号都抵消了，如果栈力还有元素，则说明缺少右括号，字符串括号不合法。
const validParentheses = (str) => {
  // 先生成一个栈
  const stack = new Stack()
  let i = 0
  // 当i < str.length 的时候就一直执行
  while(i < str.length) {
    // 当遇到左括号的时候就推送的栈内
    if (str[i] === '(') {
      stack.push(str[i])
    // 当遇到有括号的时候,判断栈内是否还有左括号,如果有,抵消一个,如果没有就代表至少多出了一个右括号
    } else if(str[i] === ')'){
      // 栈内为空,就返回false
      if (stack.isEmpty()) {
        return false
      } else {
        // 栈内不为空就消除一个
        stack.pop()
      }
    }
    i++
  }
  // 循环完毕 如果栈内为空就返回true
  if (stack.isEmpty()) return true
  // 循环完毕 如果栈内为不为空就返回false
  if (!stack.isEmpty()) return false
}

console.log(`validParentheses`, validParentheses("()")) // true
console.log(`validParentheses`, validParentheses(")(()))")) // false
console.log(`validParentheses`, validParentheses("(")) // false
console.log(`validParentheses`, validParentheses("(())((()())())")) // true
console.log(`validParentheses`, validParentheses("((()))()()()()()(())()")) // true
```

#### 5、总结

- 实际上栈结构在JavaScript 中数组已经可以完全实现，那么为什么还要有栈结构这种数据结构呢？
- 分析： 栈的底层是不是使用了数组并不重要，重要的是栈的这种后进先出的特性。重要的是你只能操作栈顶的元素的限制。一定要忽略栈的底层实现，而关心栈的特性。栈结构只是解决一类问题的一个思想，通过对数组的二次封装，抽象成栈，只提供压栈出栈的api，方便使用。



-------





## 10、浏览器

### 001、http 和 https

#### 1、http

- http 是超文本传输协议。是一个简单的请求响应协议。是应用在Tcp/ip上的。
- http 的端口号是 80
- http 是无状态的，且是明文传输，传输过程不太安全，信息容易被劫持盗用。
- https 一个信道可以同时只能发送一个https请求

#### 2、https

- https 是超文本传输协议。是http + ssl 的结合体，是http协议 加上 ssl 加密认证的，比http 更加安全。
- https 的端口号是 443
- https 一个信道可以同时发送多个https请求

#### 3、SSL 证书

##### 1、SSL 证书的作用

- 认证用户和服务器、确保数据发送到正确的客户机和服务器。
- 加密数据以防止数据中途被窃取。
- 维护数据的完整性，确保数据在传输的过程中不被改变。

##### 2、SSL 证书申请的三个步骤

- 制作CSR文件
  - 制作CSR 证书请求文件，系统会生成两个文件，一个是公钥CSR文件，一个是私钥，存放在服务器上。
- 经过CA机构的认证。 一般是收费的。
- 证书安装



-----



### 002、HTTP 报文

#### 1、请求报文

> 概念： 一个HTTP请求报文由请求行（request line）、请求头部（header）、空行和请求体4个部分组成。

**大致结构：**

```javascript
＜request-line＞ //请求行

＜headers＞ //请求头

＜blank line＞ // 空行

＜request-body＞ //请求体
```

##### 1.1 请求行

>  **请求行由三部分组成：**请求方法，请求URL（不包括域名），HTTP协议版本

```javascript
POST /user HTTP/1.1 
```

> **请求方法：** `GET` `POST` `PUT` `DELETE` `HEAD` `OPTIIONS` `TRACE` `CONNECT`

**`GET` `POST` 的区别：**

1. GET在浏览器回退时是无害的，而POST会再次提交请求。
2. GET产生的URL地址可以被Bookmark，而POST不可以。
3. GET请求会被浏览器主动cache，而POST不会，除非手动设置。
4. GET请求只能进行url编码，而POST支持多种编码方式。
5. GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。
6. GET请求在URL中传送的参数是有大小限制的大约2kb，而POST没有。
7. 对参数的数据类型，GET只接受ASCII字符，而POST没有限制。
8. GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。POST放在Request body中。

> **HTTP/1.0:**  支持 `GET` `POST` `HEAD`

> **HTTP/1.1:**  新增了  `PUT` `DELETE` `HEAD` `OPTIIONS` `TRACE` `CONNECT` 五种方法。

！！！**注意： HTTP/1.1是当前正在使用的版本。该版本采用持久连接，并且能够很好的配和代理服务器工作。还支持以管道方式发送多个请求，以便降低线路负载，提高传输速度。**

##### 1.2 请求头

> 请求头部由关键字/值组成，每行一对。

- User-Agent: 请求设备类型
- Accept: 客户端需要的数据类型。
- Content-Type: 客户端发送实体数据的数据类型。
- Host: 请求的主机名，允许多个域名同处一个IP地址，即虚拟主机。

##### 1.2.1 Content-Type:

| text/html                         | html格式                                                     |
| --------------------------------- | :----------------------------------------------------------- |
| text/plain                        | 纯文本格式                                                   |
| text/css                          | CSS格式                                                      |
| text/javascript                   | js格式                                                       |
| image/gif                         | gif图片格式                                                  |
| image/jpeg                        | jpg图片格式                                                  |
| image/png                         | png图片格式                                                  |
| application/x-www-form-urlencoded | POST专用：普通的表单提交默认是通过这种方式。form表单数据被编码为key/value格式发送到服务器。 |
| application/json                  | POST专用：用来告诉服务端消息主体是序列化后的 JSON 字符串     |
| text/xml                          | POST专用：发送xml数据                                        |
| multipart/form-data               | POST专用：用以支持向服务器发送二进制数据，以便可以在 `POST` 请求中实现文件上传的功能。 |

##### 1.3 请求空行

> 请求头之后是一个空行，通知服务器以下不再有请求头。

##### 1.4 请求体

> `GET` 没有请求体，`POST`有



#### 2、响应报文

> HTTP响应报文和请求报文的结构差不多，也是由四个部分组成：

```javascript
＜status-line＞   //状态行

＜headers＞   //消息报头

＜blank line＞   //空行

＜response-body＞    //响应体
```

##### 2.1 状态行

> 状态行也由三部分组成：服务器HTTP协议版本，响应状态码，状态码的文本描述

```javascript
比如：HTTP/1.1 200 OK
```

##### 2.2 状态码 

> 由三位数字组成，第一个数字定义了响应的类别

- `1xx` :  指示信息，表示请求已接收，继续处理。

- `2xx` :  各种意义的请求成功。

  - `200 | OK` ： 客户端请求成功。
  - `204 No Content `： 无内容。服务器成功处理，但未返回内容。一般用在只是客户端向服务器发送信息，而服务器不用向客户端返回什么信息的情况。不会刷新页面。
  - `206 Partial Content`：服务器已经完成了部分GET请求（客户端进行了范围请求）。响应报文中包含Content-Range指定范围的实体内容

- `3xx` : 重定向

  - `301` : 永久重定向，表示请求的资源已经永久的搬到了其他位置。

  - `302 Found`: 临时重定向，表示请求的资源临时搬到了其他位置。

  - `303 See Other`：临时重定向，应使用GET定向获取请求资源。303功能与302一样，区别只是303明确客户端应该使用GET访问

  - `304 Not Modified`：如果客户端发送了一个带条件的GET （GET方法请求报文中的IF…）时请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个304状态码。简单的表达就是：服务端已经执行了GET，但文件未变化。虽然304被划分在3XX，但和重定向一毛钱关系都没有

    **一个304的使用场景：** 客户端向服务器请求某一个资源的时候，服务器返回的响应报文具有这样的字段：`Last-Modified:Wed,7 Sep 2011 09:23:24`，缓存器会保存这个资源的同时，保存它的最后修改时间。下次用户向缓存器请求这个资源的时候，缓存器需要确定这个资源是新的，那么它会向原始服务器发送一个HTTP请求（GET方法），并在请求头部中包含了一个字段：`If-Modified-Since:Wed,7 Sep 2011 09:23:24`，这个值就是上次服务器发送的响应报文中的最后修改时间。

  -  `307 Temporary Redirect`：临时重定向，和302有着相同含义。POST不会变成GET

- `4xx` : 客户端错误

  - `400 Bad Request`：客户端请求有语法错误，服务器无法理解。
  - `401 Unauthorized`：请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用。
  - `403 Forbidden`：服务器收到请求，但是拒绝提供服务。
  - `404 Not Found`：请求资源不存在。比如，输入了错误的url。
  - `415 Unsupported media type`：不支持的媒体类型。

- `5xx`：服务器端错误，服务器未能实现合法的请求。 

  - `500 Internal Server Error`：服务器发生不可预期的错误。
  - `503 Server Unavailable`：服务器当前不能处理客户端的请求，一段时间后可能恢复正常。



------



### 003、HTTP 缓存

> 概念： 客户端向服务端请求资源（比如图片、代码文件等）时，将资源缓存在客户端或者客户端和服务端中间节点（cdn、代理服务器等）的一种技术。

- 缓存的优点：
  - 复用以前获取的资源，显著提高网站和应用程序的性能。
  - 减轻服务端带宽压力和服务器请求数量。



#### 1、HTTP 配置缓存

> **HTTP 缓存相关的配置都是放在 request header  和 response header 中**

##### 关于缓存策略的设置：

- Expires 过期时间
  - 比如： `Expires: Wed, 21 Oct 2015 07:28:00 GMT`
- Cache-Control
  - 比如： `Cache-Control: no-store`  不允许缓存
  - 比如： `Cache-Control: max-age=xxx`  允许缓存，多少秒后过期，直接使用，不用再询问服务器
  - 比如： `Cache-Control: no-cache`  允许缓存，但是要先像服务器验证一下缓存是否过期，`max-age=0` 的效果和 `no-cache` 是一样的



##### 关于缓存地点的设置：

- `public`  中间节点和客户端均可以缓存
- `private`  只有客户端可以缓存，中间节点不能缓存

比如： `Cache-Control: public, max-age=604800`  表示允许客户端和中间节点的缓存有效期是七天。

！！！ **注意：** 如果同时设置了`Expires` 和` Cache-Control` 并且` Cache-Control`中包含 `no-cache` 或者`max-age=xxx` 这种和缓存时间有关的，那么`Expires`会被忽略，如果说只是设置了 `public` 那不影响`Expires`生效。



##### 协商缓存、强制缓存：

> 概念： 想要使用缓存资源之前，根据是否要先向服务端验证缓存是否有效的行为，将缓存区分为**协商缓存**和**强制缓存**。

- 协商缓存应用场景： 适用于请求同一个地址，对应的资源可能变化的场景，比如当浏览器访问 `http://reactjs.org` 时会请求的html 文件，就应该设置为协商缓存。
- 强制缓存应用场景： 如果一个URL对应的资源不会变更，那就用强制缓存，并且把过期时间设置的特别长，比如打包后带有hash的js\css文件和图片等。



##### 如果不设置 Expires 和 Cache-Control：

> 如果`max-age` 和 `Expires` 属性都没有，找一下`request header` 中的` last-Modified `字段，如果有值，那么浏览器就会缓存资源。缓存有效期就是`request header `中的 `Date` - `last-Modified `的值除以10（也就是10%）
>
> 也就是尽管你不设置缓存，浏览器还是会根据文件的最后修改时间来决定缓存的有效时间。



#### 2、服务端如何校验客户端缓存是否有效

- `response header`: ETag 或者 last-Modified
- `request header`： if-None-Match 或者if-Modified-Since

！！！ **注意：**1. 当客户端第一次发送请求的时候，服务端会返回一个`ETag` 或者`last-Modified` 字段。2.当客户端发送第二次请求的时候，浏览器会自动处理，为http请求，`request header` 中添加 `if-None-Match` 或者` if-Modified-Since` 字段。字段值是上次服务端返回的对应的` ETag` 或者`last-Modified` 字段的值。

！！！ **注意：** Nginx 服务器默认的`ETag` 只是根据文件的最后修改时间和文件的长度生成 `ETag`。 



#### 3、缓存相关文章

1.[图解http缓存](https://zhuanlan.zhihu.com/p/55623075)

2.[HTTP缓存知道这些就够了](https://cloud.tencent.com/developer/article/1870593)

3.[一文彻底掌握HTTP缓存](https://zhuanlan.zhihu.com/p/342774826)

4.[哔哩哔哩 http缓存](https://www.bilibili.com/video/BV17V411J78W?spm_id_from=333.999.0.0)



--------



### 004、Http cookies

> HTTP Cookie（也叫 Web Cookie 或浏览器 Cookie）是服务器发送到用户浏览器并保存在本地的一小块数据，它会在浏览器下次向同一服务器再发起请求时被携带并发送到服务器上。通常，它用于告知服务端两个请求是否来自同一浏览器，如保持用户的登录状态。Cookie 使基于无状态的HTTP协议记录稳定的状态信息成为了可能。

#### 1、曾经Cookie 主要用于以下三个方面：

- 会话状态管理（如用户登录状态、购物车、游戏分数或其它需要记录的信息）
- 个性化设置（如用户自定义设置、主题等）
- 浏览器行为跟踪（如跟踪分析用户行为等）

**！！！注意：** Cookie 曾一度用于客户端数据的存储，因当时并没有其它合适的存储办法而作为唯一的存储手段，但现在随着现代浏览器开始支持各种各样的存储方式，Cookie 渐渐被淘汰。由于服务器指定 Cookie 后，浏览器的每次请求都会携带 Cookie 数据，会带来额外的性能开销（尤其是在移动环境下）。新的浏览器API已经允许开发者直接将数据存储到本地



#### 2、创建 cookie

>  当服务器收到 HTTP 请求时，服务器可以在响应头里面添加一个`Set-Cookie`选项。浏览器收到响应后通常会保存下 Cookie，之后对该服务器每一次请求中都通过`Cookie` 请求头部将 Cookie 信息发送给服务器。另外，Cookie 的过期时间、域、路径、有效期、适用站点都可以根据需要来指定。

**服务器通过该头部告知客户端保存 Cookie 信息:**

```javascript
HTTP/1.0 200 OK
Content-type: text/html
Set-Cookie: yummy_cookie=choco
Set-Cookie: tasty_cookie=strawberry
```

**浏览器都会将之前保存的Cookie信息通过`Cookie`请求头部再发送给服务器:**

```javascript
GET /sample_page.html HTTP/1.1
Host: www.example.org
Cookie: yummy_cookie=choco; tasty_cookie=strawberry
```



#### 3、cookie 的声明周期

-  会话期 Cookie 是最简单的 Cookie：浏览器关闭之后它会被自动删除，也就是说它仅在会话期内有效。会话期Cookie不需要指定过期时间（`Expires`）或者有效期（`Max-Age`）。需要注意的是，有些浏览器提供了会话恢复功能，这种情况下即使关闭了浏览器，会话期Cookie 也会被保留下来，就好像浏览器从来没有关闭一样，这会导致 Cookie 的生命周期无限期延长。
- 持久性 Cookie 的生命周期取决于过期时间（`Expires`）或有效期（`Max-Age`）指定的一段时间。



#### 4、Cookie 的作用域

> `Domain` 和 `Path` 标识定义了Cookie的*作用域：*即允许 Cookie 应该发送给哪些URL。

##### 4.1 Domain 属性

   `Domain` 指定了哪些主机可以接受 Cookie。如果不指定，默认为 origin，**不包含子域名**。如果指定了`Domain`，则一般包含子域名。因此，指定 `Domain` 比省略它的限制要少。但是，当子域需要共享有关用户的信息时，这可能会有所帮助。 

   例如，如果设置 `Domain=mozilla.org`，则 Cookie 也包含在子域名中（如`developer.mozilla.org`）。

##### 4.2 Path 属性

   `Path` 标识指定了主机下的哪些路径可以接受 Cookie（该 URL 路径必须存在于请求 URL 中）。以字符 `%x2F` ("/") 作为路径分隔符，子路径也会被匹配。

例如，设置 `Path=/docs`，则以下地址都会匹配：

- `/docs`
- `/docs/Web/`
- `/docs/Web/HTTP`

##### 5、SameSite 

   Cookie 允许服务器要求某个 cookie 在跨站请求时不会被发送，其中  [Site (en-US)](https://developer.mozilla.org/en-US/docs/Glossary/Site) 由可注册域定义），从而可以阻止跨站请求伪造攻击（[CSRF](https://developer.mozilla.org/zh-CN/docs/Glossary/CSRF)）。

`SameSite `可以有下面三种值：

- **`None`**。浏览器会在同站请求、跨站请求下继续发送 cookies，不区分大小写。
- **`Strict`。**浏览器将只在访问相同站点时发送 cookie。（在原有 Cookies 的限制条件上的加强，如上文 “Cookie 的作用域” 所述）
- **`Lax`。**与 **`Strict`** 类似，但用户从外部站点导航至URL时（例如通过链接）除外。 在新版本浏览器中，为默认选项，Same-site cookies 将会为一些跨站子请求保留，如图片加载或者 frames 的调用，但只有当用户从外部站点导航到URL时才会发送。如 link 链接

`SameSite` 默认值是 `Lax`,也可以设置成  `None ` 和 ` Strict` 。



--------



### 005、CORS

> 概念： **跨域资源共享（CORS）**,是一种基于`HTTP `头的机制，该机制通过允许服务器标示除了它自己以外的其它`origin`（域，协议和端口），这样浏览器可以访问加载这些资源。跨源资源共享还通过一种机制来检查服务器是否会允许要发送的真实请求，该机制通过浏览器发起一个到服务器托管的跨源资源的"预检"请求。在预检中，浏览器发送的头中标示有HTTP方法和真实请求中会用到的头。

#### 1. CORS 头

- **`Access-Control-Allow-Origin`** ： 指示请求的资源能共享给哪些域。
  1. 一般产生跨域的时候，并且没有携带cookie的时候，后端进行设置 `Access-Control-Allow-Origin：’*‘` 就可以了 
  2. 一般产生跨域的时候，并且要求携带cookie的时候，前端设置 `withCredentials : true ` , 同事后端要设置 `Access-Control-Allow-Credentials : true` 和  `Access-Control-Allow-Origin：’指定源‘`
- **`Access-Control-Allow-Credentials`** ：指示当请求的凭证标记为 true 时，是否响应该请求。

- **`Access-Control-Allow-Headers`** ： 用在对预请求的响应中，指示实际的请求中可以使用哪些 HTTP 头。
  1. 指实际请求允许携带的自定义请求头。
- **`Access-Control-Allow-Methods`** ： 指定对预请求的响应中，哪些 HTTP 方法允许访问请求的资源。
  1. 指允许哪些实际请求的方式，要枚举出来，不行写 * 
  2. 比如： `Access-Control-Allow-Methods:'PUT,DELETE'`
- **`Access-Control-Expose-Headers`** :  指示哪些 HTTP 头的名称能在响应中列出。
  1. 后端想要response header 中暴露给前端的header头，要枚举在这里。
- **`Access-Control-Max-Age`** : 指示预请求的结果能被缓存多久。
- **`Access-Control-Request-Headers`**  :  用于发起一个预请求，告知服务器正式请求会使用那些 HTTP 头。
- **`Access-Control-Request-Method`**:  用于发起一个预请求，告知服务器正式请求会使用哪一种 [HTTP 请求方法](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods)。
- **`Origin`** : 指示获取资源的请求是从什么域发起的。

#### 2. 简单请求

> 概念： 某些请求不会触发**CORS预检请求（OPTION 请求）**，称这样的请求为简单请求。

**若请求满足所有下述条件，则该请求可视为“简单请求”：**

- 使用下列方法之一： 
  1. `GET`
  2. `POST`
  3. `HEAD`
- 除了被用户代理自动设置的首部字段（例如 [`Connection`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Connection) ，[`User-Agent`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/User-Agent)）和在 Fetch 规范中定义为 [禁用首部名称](https://fetch.spec.whatwg.org/#forbidden-header-name) 的其他首部，允许人为设置的字段为 Fetch 规范定义的:
  1. `Accept`
  2. `Accept-Language`
  3. `Content-Language`
  4. `Content-Type`
- `Content-Type` 仅限一下三者之一
  - `text/plain`
  - `multipart/form-data`
  - `application/x-www-form-urlencoded`
- 请求中的任意`XMLHttpRequestUpload` 对象均没有注册任何事件监听器；`XMLHttpRequestUpload` 对象可以使用 [`XMLHttpRequest.upload`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/upload) 属性访问。
- 请求中没有使用 [`ReadableStream`](https://developer.mozilla.org/zh-CN/docs/Web/API/ReadableStream) 对象。

#### 3. 预检请求

> “需预检的请求”要求必须首先使用 `OPTIONS`  方法发起一个预检请求到服务器，以获知服务器是否允许该实际请求。"预检请求“的使用，可以避免跨域请求对服务器的用户数据产生未预期的影响。

- 非简单请求之前一般会发送 options 请求来做预检请求。
- 可以用来检验某接口是否支持跨域。
- 可以检验某个接口是否支持哪些方法（post,put,delete, 等）
- 如果预检不通过，真实的接口请求就不会发送了



-------



### 006、浏览器的垃圾回收机制

#### 1、V8引擎内存如何分配

   ![image-20220821203833105](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821203833105.png)

- V8 引擎内存分为 Stack（栈） 和 Heap mempry（堆分成了很多部分）
- **堆中负责垃圾回收机制的只有两部分： `New Space（新生代空间）`  和  `Old Space(老生代空间)`**
- `Large object space`  大对象存储空间
- `Code space`  代码占用的内存

#### 2、**`New Space（新生代空间）`**

![image-20220821205144038](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821205144038.png)

- 新生代空间是严格对半分开的： `Semi space From`  和  `Semi space To`

- **新生代垃圾回收算法简单来说就是Copy（复制）Scavenge算法（新生代互换）**

  **解读Tips：**

  >    1.假如最开始`Semi space From`  空间中有四个对象， obj1， obj2， obj3， obj4，其中obj2和obj3和obj4，没有在代码中引用了，那么就是垃圾变量了。
  >
  >    2.浏览器会给 obj2，obj3，obj4标记为垃圾，但是并非实时回收。
  >
  >    当存储一个对象obj5的时候，且`Semi space From`空间已经占满了，那么就会把obj1 Copy 到 右侧`Semi space To`空间，obj5也会存储在右侧`Semi space To`空间。左侧`Semi space From`空间内被浏览器标记为垃圾变量的obj2，obj3，obj4便会清除。而且此时会对调空间。
  >
  >    3。此时左侧清空的`Semi space From`空间会更名为 `Semi space To`；
  >
  >    4.右侧此时保存了obj1，obj5 的 `Semi space To`空间会更名为`Semi space From`。 
  >
  >    新生代空间垃圾回收机制就是以上`Semi space From`和`Semi space To`来回复制还在引用的变量，清理`Semi space From`空间后，对调名称。

#### 3、**`Old Space(老生代空间)`**

​                             ![](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821205313739.png)

- 老生代空间是一个连续的空间，严格对半分开： `Old pointer space` 和 `Old data space`。
-  `Old pointer space` ： 一个对象有指针引用或者指向其他对象的话，大概率会保存在这里。
-  `Old data space` : 如果一个对象保存的是原始对象，没有指针引用的话，会保存在这里
- 所有老生代的对象都是由新生代对象晋升而来。
- **老生代垃圾回收算法就是早期使用标记整理（`Mark-Compact`）和现在使用标记清除（`Mark-Sweep`）**

#### 4、`New Space`和  `Old Space` 的内存大小

- 和操作系统有关： 64位的为1.4G（1464MB）, 32位的为 0.7G（732MB）
- 64位的新生代空间为64MB，老生代空间为1400MB
- 32位的新生代空间为32MB，老生代空间为700MB
- 最新版 node（v14）的内存为 2GB

#### 5、新生代为什么要采用复制这种形式呢？

- 牺牲空间来换时间
- Copy 复制 操作最简单时间最短。

#### 6、老生代为什么不采用复制这种形式呢？

- 老生代空间有1400MB，如果采用新生代的方式的话，那么会浪费大约700MB的空间

#### 7、新生代如何晋升到老生代

![image-20220821220902540](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821220902540.png)

- 判断新生代空间中`Semi space From` 的变量是否会经历过一次回收（至少会经历一次），如果为未经历过的话会转移到`Semi space To` 。
- 如果经历过Scavenge回收， 并且`Semi space To`空间已经用了超过25%，就会晋升到老生代空间。



#### 8、V8引擎如何回收垃圾

>    Tips: 
>
>     1.  垃圾回收机制回收一次1.5G堆内存，大约需要50ms
>       2.  nodejs 读写大文件都需要占用内存
>       3.  webpack 编译大型项目的代码环境，都会占用浏览器内存
>       4.  新生代和老生代垃圾回收机制算法完全不一样！！！

#### 9、新生代算法

- **新生代垃圾回收算法简单来说就是Copy（复制）Scavenge算法（新生代互换）**

**解读Tips：**

>    1.假如最开始`Semi space From`  空间中有四个对象， obj1， obj2， obj3， obj4，其中obj2和obj3和obj4，没有在代码中引用了，那么就是垃圾变量了。
>
>    2.浏览器会给 obj2，obj3，obj4标记为垃圾，但是并非实时回收。
>
>    当存储一个对象obj5的时候，且`Semi space From`空间已经占满了，那么就会把obj1 Copy 到 右侧`Semi space To`空间，obj5也会存储在右侧`Semi space To`空间。左侧`Semi space From`空间内被浏览器标记为垃圾变量的obj2，obj3，obj4便会清除。而且此时会对调空间。
>
>    3。此时左侧清空的`Semi space From`空间会更名为 `Semi space To`；
>
>    4.右侧此时保存了obj1，obj5 的 `Semi space To`空间会更名为`Semi space From`。 
>
>    新生代空间垃圾回收机制就是以上`Semi space From`和`Semi space To`来回复制还在引用的变量，清理`Semi space From`空间后，对调名称。

#### 10、老生代算法

##### 1.标记清除

- 广度扫描： 寻找有引用的变量，标记被声明，后期未被引用的标记为垃圾，GC开始工作的时候会清楚未被标记的垃圾变量。

##### 2、标记整理（先整理再清除）

- 广度扫描： 寻找有引用的变量，标记被声明，后期未被引用的标记为垃圾
- 标记完成以后整理被标记引用的变量到一起。
- GC开始工作的时候会清楚未被标记的垃圾变量。
- 最开始使用的是**全停顿标记**，后期使用的是**增量标记**和**三色标记法**
  - 全停顿标记： js是单线程的，所以是运行主线程--->垃圾回收---> 主线程----> 回收。运行主线程的时候会广度扫描，标记垃圾变量。
  - 增量标记：
  - 三色标记法：

##### 3、引用计数

- 曾经IE 和 网景 使用的

**Tips：**

>  为什么先整理再清除？
>
>  在整理标记变量的时候会顺带清除未被标记的垃圾变量。然后剩下的变量会一起清除掉。 这样做的操作较少（对比先清除所有的未被标记的垃圾变量，然后再移动标记变量。）

![image-20220821215859150](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821215859150.png)

![image-20220821215923693](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821215923693.png)



#### 11、如何查看V8内存使用情况

##### 1、通过浏览器`window.performance`

![image-20220821221642104](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821221642104.png)

- `memory` 中保存浏览器内存使用情况
- `jsHeapSizeLimit`  :  js 堆中使用的内存大小限制
- `totalJSHeapSize`: 可使用的内存
- `usedJSHeapSize`:   JS 对象（包括V8引擎内部对象）占用的内存，一定小于 totalJSHeapSize

##### 2、通过`process.memoryUsage()`

![image-20220821222320824](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220821222320824.png)

- node 使用内存情况
- `rss`  :  当前内存的占用
- `heapTotal`:  堆内存的总站用（包含使用和未使用的）
- `heapUsed`:  使用的堆内存
- `external`:  额外使用的内存（实际扩展的是底层c++的内存）
- `arrayBuffers`: 二进制使用的内存

```javascript
const os = require('os') // node 内置os模块
function getMemory() {
  let memory = process.memoryUsage()
    let format = function(bytes) {
        return `${(bytes/1024/1024).toFixed(2)} MB`
    }
    
    let totalM = os.totalmem // 获取电脑总的内存大小
    let freeM = os.freemem // 获取电脑空闲的内存大小
    console.log(`totalM: ${foramt(totalM)} \t freeM: ${foramt(freeM)}`)
    console.log(`
  heapTotal: ${foramt(memory.heapTotal)} \t heapUsed: ${foramt(memory.heapUsed)}
  `)
}
```

**Tips：**

>    nodejs 运行内存大约2g
>
>    当js程序运行占用内存超过2G ，服务器会dang 掉。

##### 3、如何扩展node内存

- 有两个全局变量 `max-old-space-size=2048(2048是默认值)` 和 `max-new-space-size`
- 扩展内存  一般最多接受电脑系统空闲内存的75%

```bash
node --max-old-space-size=4096 
```

- 启动服务node服务为4G

#### 12、内存优化实例

##### 1、为什么我们要关注内存

- 防止页面占用内存过大，引起客户端卡顿，甚至无响应。
- Node 使用的也是V8， 内存对于后端服务的性能至关重要，因为服务的持久性，后端更容易造成内存益处
- 高级前端必备知识

##### 2、避免内存溢出，我们该怎么做

>    全局对象会始终存活到程序结束。
>
>    局部变量当程序执行结束，且没有引用的时候就会消失。

- 尽量使用局部变量



---------



### 007、单页面应用搜索引擎的SEO优化

#### 1、SEO优化概念

>    搜索引擎优化(Search Engine Optimization，简称SEO)是一种利用搜索引擎的搜索规则来提高目的网站在有关搜索引擎内的排名的方式。所谓“针对搜索引擎作最佳化的处理”，是指为了要让网站更容易被搜索引擎接受。深刻理解是：通过SEO这样一套基于搜索引擎的营销思路，为网站提供生态式的自我营销解决方案，让网站在行业内占据领先地位，从而获得品牌收益。

#### 二、解决方法

##### 1. 语义化标签

- 遵循W3C的标准，标签语义化，可以更好的支持爬虫爬取关键信息。

##### 2. keywords

- meta 标签处的keywords 是爬虫收集网页信息的关键地方。

##### 3.SEO优化标签

- 可以利用position定位，z-index为负值；写SEO优化标签。

##### 4.关键信息标签，网页组件尽量嵌套不超过三层

##### 5.优化导航

##### 6.SSR（服务端渲染）

- 采用服务端渲染，爬虫可以支持爬取服务端渲染的页面。更好有利于SEO

##### 7.增加外链内链

##### 8.网址尽量语义化

##### 9.优化首页加载速度

##### 10. 使用https  谷歌搜索引擎对使用https的网站排名优先

##### 11.少使用iframe

##### 12.重要的内容不用js输出



---------



### 008、Http的几种请求方法用途

- `GET`方法
  - 发送一个请求来取得服务器上的某一资源
- `POST`方法
  - 向`URL`指定的资源提交数据或附加新的数据
- `PUT`方法
  - 跟`POST`方法很像，也是想服务器提交数据。但是，它们之间有不同。`PUT`指定了资源在服务器上的位置，而`POST`没有
- `HEAD`方法
  - 只请求页面的首部
- `DELETE`方法
  - 删除服务器上的某资源
- `OPTIONS`方法
  - 它用于获取当前`URL`所支持的方法。如果请求成功，会有一个`Allow`的头包含类似`“GET,POST”`这样的信息
- `TRACE`方法
  - `TRACE`方法被用于激发一个远程的，应用层的请求消息回路
- `CONNECT`方法
  - 把请求连接转换到透明的`TCP/IP`通道

### 009、从浏览器地址输入URL到显示页面的步骤

1. 在浏览器输入URL地址
2. 浏览器查找缓存资源，判定是否使用缓存资源:  浏览器缓存---> 系统缓存---> 路由器缓存
   - 如果资源未缓存，发起新的请求
   - 如果资源以缓存，并且新鲜，把缓存的资源发送给客户端，否则与服务端进行验证
   - 缓存新鲜通常有两个HTTP的头来控制 `Expiers`  和 `Cache-Control`
3. 浏览器解析URL 获取协议、域名、端口号、路径
4. 浏览器组装一个HTTP的请求报文
5. DNS 解析
6. 建立TCP/IP链接
7. 发送HTTP请求
8. 解析HTTP响应资源，解析HTML文档，构建DOM树，构建CSSOM树，执行JS脚本，加载显示页面

### 010、网站性能优化

- 技术选型方面：
  - React 对比 Vue 在构建大型项目的时候，项目的响应速度会更快。
  - 单页面应用应采用代码分割，路由组件懒加载。

- 网络连接方面：
  - 减少 `HTTP` 请求： 图片资源整合为雪碧图
  - 减少 `DNS` 解析： DNS 缓存。将资源分布到恰当数量的主机名
  - 使用 `HTTP` 缓存： 分为协商缓存和强缓存，由 `Expiers`  和 `Cache-Control` 控制
  - 使用 `HTTPS` 协议： `HTTPS`  协议传输效率更快，而且一个通道可以发送多个`https`请求
- 客户端方面：
  - 使用 HTTP 缓存资源
  - 减少浏览器的重绘与回流
  - 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢
- 服务端方面：
  - 服务器资源采用CDN加速优化
  - 服务器响应添加 Expires 或者 Cache-Control 报文头优化
  - 采用 Gzip 压缩优化
  - 网站配置 Etags 优化
  - 服务器 SSR 渲染
- `Cookie` 方面：
  - 减小 `cookie` 的大小
- css优化：
  - 网站把样式至于顶部
  - 压缩 css 代码
  - 网站使用HTML5 LINK标签代替@import
  - 使用 css 预加载 
- JS 优化：
  - 网站减少 JS Dom的操作
  - 压缩 JS代码
  - JS中使用过的变量赋值null，减少内存占用
- 图片优化：
  - 图片的懒加载
  - 可以使用SVG图

### 011、HTTP状态码及其含义

- `1xx`：信息状态码
  - `100 Continue` 继续，一般在发送`post`请求时，已发送了`http header`之后服务端将返回此信息，表示确认，之后发送具体参数信息
- `2xx`：成功状态码
  - `200 OK` 正常返回信息
  - `201 Created` 请求成功并且服务器创建了新的资源
  - `202 Accepted` 服务器已接受请求，但尚未处理
- `3XX`：重定向
  - `301 Moved Permanently` 请求的网页已永久移动到新位置。
  - `302 Found` 临时性重定向。
  - `303 See Other` 临时性重定向，且总是使用 `GET` 请求新的 `URI`。
  - `304 Not Modified` 自从上次请求后，请求的网页未修改过。
- `4XX`：客户端错误
  - `400 Bad Request` 服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。
  - `401 Unauthorized` 请求未授权。
  - `403 Forbidden` 禁止访问。
  - `404 Not Found` 找不到如何与 `URI` 相匹配的资源。
- `5xx`:服务器错误
  - `500 Internal Server Error` 最常见的服务器端错误。
  - `503 Service Unavailable` 服务器端暂时无法处理请求（可能是过载或维护）。

### 012、介绍一下你对浏览器内核的理解？

- 主要分成两部分：渲染引擎(`layout engineer`或`Rendering Engine`)  和`JS`引擎
- 渲染引擎：负责取得网页的内容（`HTML`、`XML`、图像等等）、整理讯息（例如加入`CSS`等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核
- `JS`引擎则：解析和执行`javascript`来实现网页的动态效果
- 最开始渲染引擎和`JS`引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎

### 013、请描述一下 `cookies`，`sessionStorage` 和 `localStorage` 的区别？

- `cookie`是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）
- cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递
- `sessionStorage`和`localStorage`不会自动把数据发给服务器，仅在本地保存
- 存储大小：
  - `cookie`数据大小不能超过4k
  - `sessionStorage`和`localStorage`虽然也有存储大小的限制，但比`cookie`大得多，可以达到5M或更大
- 有期时间：
  - `localStorage` 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据
  - `sessionStorage` 数据在当前浏览器窗口关闭后自动删除
  - `cookie` 设置的`cookie`过期时间之前一直有效，即使窗口或浏览器关闭

### 014、iframe有那些缺点？

- `iframe`会阻塞主页面的`Onload`事件
- 搜索引擎的检索程序无法解读这种页面，不利于`SEO`
- `iframe`和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载
- 使用`iframe`之前需要考虑这两个缺点。如果需要使用`iframe`，最好是通过`javascript`动态给`iframe`添加`src`属性值，这样可以绕开以上两个问题

### 015、常见的浏览器内核有哪些？

- `Trident`内核：`IE,MaxThon,TT,The World,360`,搜狗浏览器等。[又称MSHTML]
- `Gecko`内核：`Netscape6`及以上版本，`FF,MozillaSuite/SeaMonkey`等
- `Presto`内核：`Opera7`及以上。 [`Opera`内核原为：Presto，现为：`Blink`;]
- `Webkit`内核：`Safari,Chrome`等。 [ `Chrome`的`Blink`（`WebKit`的分支）]

### 016、cookie 的弊端

- 容易被黑客劫持，做跨站请求伪造，不安全
- cookie 的大小有限制，大约4KB

### 017、浏览器的缓存

- 缓存分为两种：强缓存和协商缓存，根据响应的 header 内容来决定。

- 强缓存相关字段有 expires，cache-control。如果 cache-control 与 expires 同时存 在的话， cache-control 的优先级高于 expires。
- 协商缓存相关字段有 Last-Modified/If-Modified-Since，Etag/If-None-Match





## 11、其他

>           本笔记适合已有一些 Git 基础的人来学习！  所有命令均可在 [Git文档官网](https://git-scm.com/book/zh/v2) 查询学习 

### 001、深入Git

#### 1.1、配置 Git

##### 1.1.1、配置 user 信息

```bash
$ git config --global user.name 'yeshuai'
$ git config --global user.email 'yeshuai0329@aliyun.com'
```

##### 1.1.2、config 的三个作用域

- 缺少等同于local

```bash
$ git config --local  // local只对某个git仓库有效
$ git config --global  // global 对当前用户所有git仓库有效
$ git config --system  // system 对系统所有登录的用户有效
```

##### 1.1.3、显示 config 的配置信息，加 --list

```bash
$ git config --local --list // local只对某个git仓库有效
$ git config --global --list // global 对当前用户所有git仓库有效
$ git config --system  --list// system 对系统所有登录的用户有效
```



#### 1.2、创建 Git 仓库

##### 1.2.1、 两种场景

**1.  把已有的项目纳入Git管理**

```bash
$ cd xxx  // xxx 是项目代码所在文件夹
$ git init // 初始化 git 仓库，会生成.git文件夹。
```

**2.  新建的项目直接用 Git 管理**

```bash
$ cd xxx  // xxx 是某个文件夹
$ git init your_project // 初始化 git 仓库 ,并且在该目录下创建和项目名称同名(your_project)的文件夹
$ cd your_project
```



#### 1.3 Git 工作流程

Git 仓库： 工作区 ----------> 暂存区 -----------> 版本历史区 ------------> 远端

- 工作区、暂存区、历史区 都是在计算机本地。远端是在互联网云端
- 在计算机本地修改代码的地方叫工作区，工作区的代码是未被追踪的。
- 通过 `git add xxx(文件,如果是所有文件可以用 . 表示)`  可以把工作区修改的代码,提交到暂存区。
- 通过 `git commit -m '提交信息'` 命令，可以把暂存区代码提交到版本历史区。
- 通过 `git push` 命令可以把已经提交的提示版本提交到远端



#### 1.4 Git 的命令

##### 1.4.1、创建本地仓库，会生成 .git 文件夹

```bash
$ git init
```

##### 1.4.2、将本地仓库的数据传输到暂存区

```bash
$ git add . (.提交所有改动的文件到暂存区)
$ git add style/long.css (提交style/long.css文件到暂存区)
```

##### 1.4.3、查询工作区和暂存区数据工作状态

```bash
$ git status
```

##### 1.4.4、将暂存区的改动提交到版本历史区

```bash
$ git commit -m 'xxxxx'   // xxxxx是对本次暂存区到版本历史区的改动描述
$ git commit -am 'xxxxx'   // 直接将工作区的改动提交到版本历史区
```

##### 1.4.5、修改版本历史commit 的 message

```bash
 git commit --amend // 修改最近一次 commit message // 写完以后w是写进去q是退出
```

##### 1.4.6、展示版本历史区的历史纪录

```bash
$ git log  // 会展示最近几次暂存区到版本历史区的改动
$ git log --oneline  // 会展示最近几次暂存区到版本历史区的改动(区别是每次改动是以一行的形式展示，展示数量多于git log)
$ git log -n4 --oneline // 简介的展示最近四条commit数据
```

##### 1.4.7、查看/创建/切换/删除分支

```bash
$ git barnch // 查看本地存在的分支
$ git barnch -a // 查看本地和远端所有的存在的分支
$ git barnch -r // 看远端所有的存在的分支
$ git barnch -av // 查看本地和远端所有的存在的分支,带commit记录
$ git barnch -rv // 查看本地和远端所有的存在的分支,带commit记录
$ git checkout fix/delname  // 创建一个fix/delname分支
$ git branch fix/delname  // 切换到fix/delname分支
$ git checkout -d fix/delname // 创建一个fix/delname分支，并且切换到fix/delname分支
$ git branch -D fix/delname  // 删除fix/delname分支
$ git branch -m fix/delname  fix/editname // 修改fix/delname分支,为fix/editname,远程也会被修改
```

##### 1.4.8、克隆仓库

```bash
$ git clone xxx (xxx是指的传输协议的地址，一般常用http 和 ssh)
```

##### 1.4.9、关联本地仓库和远端仓库

```bash
1. 查看是否连接成功
$ git remote -v
2. 添加关联地址
$ git remote add aaa bbb  // aaa 是给添加的地址的名字 ， bbb 是添加的地址
3. 删除关联的地址
$ git remote remove aaa  // aaa 是要删除的远端地址的名字
4. 第一次推送本地仓库到GitHub
$ git push -u origin main 
5. 以后推送本地仓库代码到main分支
$ git push
```

##### 1.4.10、从远端拉区代码

```bash
$ git fetch
$ git pull
// git fetch 从远端拉去最新代码回来以后不会自动合并，git pull 拉去代码回来以后会进行 merge 合并
```



#### 1.5 Git 使用过程中遇到的问题

##### 1.5.1、工作区和暂存区怎么比较文件差异

``` bash
$ git diff  // 默认比较工作区和暂存区的文件差异
```

##### 1.5.2、暂存区和HEAD指针怎么比较文件差异

```bash
$ git diff --cached  // 必须添加 --cached
```

##### 1.5.3、暂存区怎么恢复成HEAD指针一样的

```bash
$ git reset HEAD // 回复暂存区的文件和HEAD一致
```

##### 1.5.4、工作区怎么恢复成暂存区一样的

```bash
$ git checkout
```

##### 1.5.5、怎么修改最新的commit的message

```bash
$ git commit --amend // 修改最近一次 commit message // 写完以后w是写进去q是退出
```

##### 1.5.6、怎么消除最后几次的提交/版本的回退

```bash
$ git reset --hard HEAD^ // commit指针回退到上一次的commit状态
$ git reset --hard xxxxx // commit指针回退到xxxx的commit状态(xxxx 是commit哈希值)
```

##### 1.5.7、删除文件

```bash
$ git rm xxx  // 删除文件(xxx是被删除的文件)
```

##### 1.5.8、开发中临时加塞紧急任务

描述： 项目开发过程中，测试让紧急修复一些bug，但是当前分支工作区已经有了一些改动，那么我们就可以先把工作区的改动添加到暂存区。添加到暂存区以后使用`git stash`隐藏现在的改动，然后去修改bug，改完会后回来再使用 `git stash pop` 取出隐藏的改动

```bash
$ git stash  // 隐藏暂存区的改动
$ git stash  pop // 取出暂存区的改动
$ git stash  apply // 取出暂存区的改动
// （pop 和 apply）的区别是: git stash 相当于把暂存区的改动压入到一个stash栈内， 
git stash pop 是取出栈内的改动，同时stash栈内的改动就被移除了。但是apply是取
出站内的改动，但是站内依然存在改动，可以来重复使用。
$ git stash list // 可以查看 stash 栈内的改动
```

##### 1.5.9、合并代码解决冲突

1. **不同人修改了不同的文件**

   >           当不同的开发人员修改了同一个分支的不同的文件，在git push的时候先git pull 一下代码，git 会很智能的帮我们解决合并问题。

2. **不同的人修改了相同的文件**

   >           当不同的开发人员修改了同一个分支的相同的文件，在git push的时候先git pull 一下代码，git 会很智能的帮我们解决合并问题。

3. **不同的人修改了相同文件的相同区域的时候**

   >           当不同的开发人员修改了同一个分支的相同文件的相同区域的时候，在git push的时候先git pull 一下代码，但是此时git 不能够解决这种冲突，要开发人员手动解决冲突。选择当前本地的还是远端的。解决冲突以后，`git commit -m ''`  `git push`。4

4. **不同的人，一个变更了文件名一个变更文件内容**

   >           当一个开发人员修改了index.html为index.htm,push到远端， 另一个开发人员修改了index.html里面的内容，也push到远端，就会push不上去，因为本地不是最新的代码，要git pull 一下，git 会很智能的帮我们解决这类合并问题。这个跟git 存储文件，监控机制有关系。

5. **不同的人同时修改了文件名**

   >           当以个开发人员修改了 index.html为index1.html，并推送到了远端，另一个开发人员修改了index.html 为index2.html，并git push。因为本地不是最新的代码，要git pull 一下，此时会有git 冲突，git并不会为我们解决，需要两个开发人员一起讨论研究 具体如何修改代码。

##### 1.5.10、禁止向远端继承分支执行 push -f

```bash
$ git push -f  //禁止向远端继承分支执行 push -f, 此命令一执行，远端代码所有commit记录便会消失
```

##### 1.5.11、深聊git push
-  `git push` 默认情况下向远程推送本地所有新添加的 `commit` 记录到远端主机
- `git push` 的完整语法
```javascript
$ git push -f <remotename> <commit SHA>:<remotebranchname>
```
- `<remotename>` 远程仓库名，默认为origin,是在使用`git remote add <remotename> <remoteaddress>`连接本地和远程仓库的时候起的名字,自己定义的默认是origin
- <commit SHA> 提交的唯一码: `commit` 后生成的哈希值
- <remotebranchname> 远程分支名:要推送的分支名

!!! 注意: `git push -f`, 会清除远端主机所有的commit记录,`git push -f origin ac34f232e: master`, 会使origin远端主机仓库的master分支commit记录回退到ac34f232e.  慎用,禁止使用.
##### 1.5.12、分支合并
-  github gitlab 遵循fastfoward原则
-  git merge 合并,是将一个分支合并到当前分支,解决冲突以后会生成一个新的commit记录
-  git rebase 是变基操作,可以达到合并分支效果,是将一个分支合并到当前分支,解决冲突以后会生成一个新的commit记录

##### 1.5.12、配置ssh

1. `cd ~/.ssh` 检查是否电脑又ssh
2. `ssh-keygen -t rsa -C 'github邮箱地址'`
3. 三次回车
4. 根据提示到C盘找pub后缀文件，去vscode复制内容
5. 打开github 点击头像找setting
6. 找ssh ，复制进去。



-----------



### 002、moment 高频使用方法

#### 1、获取当前moment对象

```javascript
const nowTime = moment() // 返回的是moment时间对象
```

#### 2、获取时间戳

```javascript
# 精确到毫秒
// 输出自 Unix 纪元以来的毫秒数
moment().valueOf()
// 输出自 Unix 纪元以来的毫秒数的字符串
moment().format('x')

# 精确到秒
// 输出自 Unix 纪元以来的秒数
moment().unix()
// 输出自 Unix 纪元以来的秒数的字符串
moment().format('X')
```

#### 3、生成指定时间的moment

```javascript
moment("1995-12-25");
 
# 带格式
# 解析器会忽略非字母和数字的字符，因此以下两个都将会返回相同的东西。
moment("12-25-1995", "MM-DD-YYYY");
moment("12/25/1995", "MM-DD-YYYY");
```

#### 4、返回对象

```javascript
moment().toObject();
# 返回一个包括：年、月、日、时、分、秒、毫秒的对象
{
    years: 2020
    months: 2
    date: 14
    hours: 18
    minutes: 47
    seconds: 56
    milliseconds: 526
}
```

#### 5、format格式化

```javascript
moment().format(); // '2021-10-11T12:25:44+08:00'
moment().format('YYYY-MM-DD HH:mm:ss'); // '2020-03-14 19:23:29'
```

#### 6、获取时间

```javascript
// 获取今天0时0分0秒
moment().startOf('day')
 
// 获取本周第一天(周日)0时0分0秒
moment().startOf('week')
 
// 获取本周周一0时0分0秒
moment().startOf('isoWeek')
 
// 获取当前月第一天0时0分0秒
moment().startOf('month')
 
// 获取指定日期的0时0分0秒
moment('2019-10-20').startOf('day')
 
// 获取今天23时59分59秒
moment().endOf('day')
 
// 获取本周最后一天(周六)23时59分59秒
moment().endOf('week')
 
// 获取本周周日23时59分59秒
moment().endOf('isoWeek')
 
// 获取当前月最后一天23时59分59秒
moment().endOf('month')

// 获取当地时间
moment().format() // '2021-10-11T14:20:11+08:00'

// 获取国际标准时间
moment().utc().format() // '2021-10-11T06:20:00Z'

// 国际时间转当前时间
moment('2021-10-11T06:20:00Z').format() // '2021-10-11T14:20:11+08:00'

// 当前时间转国际时间
moment('2021-10-11T14:20:00+08:00').utc().format() // '2021-10-11T06:20:00Z'
```

#### 7、获取当月第一天是星期几

```javascript
// 用于获取星期几，其中星期日为 0、星期六为 6
moment().startOf('month').day() 
```

#### 8、获取前n天 / 后n天

```javascript
// 获取当前前n天 / 后n天
moment().add(7, 'days');
moment().subtract(7, 'days')
// 获取指定时间前n天 / 后n天
moment('2021-12-25').add(7, 'days');
moment('2021-12-25').subtract(7, 'days')
```

#### 9、比较两个时间的大小

```javascript
// 第二个参数用于确定精度，且不仅仅是要检查的单个值，因此使用 day 将会检查年份、月份、日期。
moment('2010-10-31').isBefore('2010-12-31', 'day'); // true
moment('2010-10-20').isBefore('2010-12-31', 'year'); // false
moment('2010-10-20').isAfter('2009-12-31', 'year'); // true
# 判断两个时间是否相等
moment('2010-10-20').isSame('2009-12-31', 'year'); 
# 需要注意的是， isBefore与isAfter 都是开区间，如果想使用闭区间，应使用
isSameOrBefore
isSameOrAfter
```

#### 10、计算两个时间相差几天

```javascript
moment([2008, 2, 27]).diff([2007, 0, 28], 'day'); // 424
moment('2021-12-22').diff('2015-12-22', 'day'); // 2192
```

#### 11、获取当月总天数

```javascript
// 获取当月天数
moment().daysInMonth()
// 获取指定月份的天数
moment('2021-9').daysInMonth()
```

#### 12、判断一个日期是否在两个日期之间

```javascript
// 两遍开区间
moment('2010-10-20').isBetween('2010-10-19', '2010-10-25') // true
moment('2010-10-19').isBetween('2010-10-19', '2010-10-25'); // false
moment('2010-10-25').isBetween('2010-10-19', '2010-10-25'); // false
// 第四个参数控制开闭区间
moment('2016-10-30').isBetween('2016-10-30', '2016-12-30', null, '()'); //false
moment('2016-10-30').isBetween('2016-10-30', '2016-12-30', null, '[)'); //true
moment('2016-10-30').isBetween('2016-01-01', '2016-10-30', null, '()'); //false
moment('2016-10-30').isBetween('2016-01-01', '2016-10-30', null, '(]'); //true
moment('2016-10-30').isBetween('2016-10-30', '2016-10-30', null, '[]'); //true
```

#### 13、判断时间是多久以前

```javascript
moment().fromNow() // 几秒前
moment([2007, 0, 29]).fromNow() //15年前
```

下表概述了每个时间长度显示的字符串的细分。

| 范围                   | 键   | 样本输出               |
| :--------------------- | :--- | :--------------------- |
| 0 至 44 秒             | s    | 几秒前                 |
| *未设定*               | ss   | 44 秒前                |
| 45 至 89 秒            | m    | 1 分钟前               |
| 90 秒至 44 分钟        | mm   | 2 分钟前 ... 44 分钟前 |
| 45 至 89 分钟          | h    | 1 小时前               |
| 90 分钟至 21 小时      | hh   | 2 小时前 ... 21 小时前 |
| 22 至 35 小时          | d    | 1 天前                 |
| 36 小时至 25 天        | dd   | 2 天前 ... 25 天前     |
| 26 至 45 天            | M    | 1 个月前               |
| 45 至 319 天           | MM   | 2 个月前 ... 10 个月前 |
| 320 至 547 天 (1.5 年) | y    | 1 年前                 |
| 548 天+                | yy   | 2 年前 ... 20 年前     |

更多使用方法请上 [moment ](http://momentjs.cn/) 官网查看
