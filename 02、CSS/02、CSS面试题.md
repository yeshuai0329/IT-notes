### 002、css sprite是什么,有什么优缺点？

- 概念： 将多个小图片拼接到一个图片中。通过`background-position`和元素尺寸调节需要显示的背景图案。

- 优点：
  - 减少`HTTP`请求数，极大地提高页面加载速度
  - 增加图片信息重复度，提高压缩比，减少图片大小
  - 更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现
- 缺点：
  - 图片合并麻烦
  - 维护麻烦，修改一个图片可能需要从新布局整个图片，样式



### 003、 `link`与`@import`的区别？

1. `link`是`HTML`方式， `@import`是CSS方式
2. `link`最大限度支持并行下载，`@import`过多嵌套导致串行下载，出现`FOUC`(文档样式短暂失效)
3. `link`可以通过`rel="alternate stylesheet"`指定候选样式
4. 浏览器对`link`支持早于`@import`，可以使用`@import`对老浏览器隐藏样式
5. `@import`必须在样式规则之前，可以在css文件中引用其他文件
6. 总体来说：`link`优于`@import`



### 004、`display: none;`与`visibility: hidden`的区别？

- 共同点：
  - 都能让元素显示隐藏
- 不同点：
  - `display：none` 会让元素完全从渲染树中消失，渲染的时候不占据任何空间， `visibility: hidden` 不会让元素从渲染树消失，渲染元素继续占据空间，只是内容不可见。
  - `display: none`;是非继承属性，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示,  `visibility: hidden;`是继承属性，子孙节点消失由于继承了`hidden`，通过设置`visibility: visible;`可以让子孙节点显式。
  - 修改常规流中元素的`display`通常会造成文档重排。修改`visibility`属性只会造成本元素的重绘。
  - 读屏器不会读取`display: none`;元素内容；会读取`visibility: hidden;`元素内容。

### 005、什么是FOUC?如何避免？

- `Flash Of Unstyled Content`：用户定义样式表加载之前浏览器使用默认样式显示文档，用户样式加载渲染之后再从新显示文档，造成页面闪烁。
- **解决方法**：把样式表放到文档的`<head>`

### 006、BFC

- `BFC(Block Formatting Context)`  块级格式化上下文，是一个独立的渲染区域，让处于 BFC 内部的元素与外部的元素相互隔离，使内外元素的定位不会相互影响。
- **触发条件 (以下任意一条)**
  - `float`的值不为`none`
  - `overflow`的值不为`visible`
  - `display`的值为`table-cell`、`tabble-caption`和`inline-block`之一
  - `position`的值不为`static`或则`releative`中的任何一个

### 007、BFC布局与普通文档流布局区别？

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



### 008、清除浮动的几种方式，各自的优缺点？

- 父级`div`定义`height`
- 结尾处加空`div`标签`clear:both`
- 父级`div`定义伪类`:after`和`zoom`
- 父级`div`定义`overflow:hidden`
- 父级`div`也浮动，需要定义宽度
- 结尾处加`br`标签`clear:both`
- 比较好的是第3种方式，好多网站都这么用



### 009、为什么要初始化CSS样式?

- 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对`CSS`初始化往往会出现浏览器之间的页面显示差异。
- 当然，初始化样式会对`SEO`有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化



### 010、css3有哪些新特性

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



### 011、CSS3新增伪类有那些？

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



### 012、display有哪些值？说明他们的作用？

- `block` 转换成块状元素。
- `inline` 转换成行内元素。
- `none` 设置元素不可见。
- `inline-block` 象行内元素一样显示，但其内容象块类型元素一样显示。
- `list-item` 象块类型元素一样显示，并添加样式列表标记。
- `table` 此元素会作为块级表格来显示
- `inherit` 规定应该从父元素继承 `display` 属性的值



### 013、介绍一下标准的CSS的盒子模型？

- 盒模型： 内容(content)、填充(`padding`)、边界(`margin`)、 边框(`border`)；
- IE 盒模型：盒子的宽度包括：  内容(content)+填充(`padding`)+边框(`border`) 
- W3C盒模型：盒子的宽度包括： 内容(content)



### 014、position定位

- `absolute`：生成绝对定位的元素，相对于 `static` 定位以外的第一个父元素进行定位
- `fixed`：生成绝对定位的元素，相对于浏览器窗口进行定位
- `relative`：生成相对定位的元素，相对于其正常位置进行定位
- `static` 默认值。没有定位，元素出现在正常的流中
- `inherit` 规定从父元素继承 `position` 属性的值



### 015、重绘和回流（重排）是什么，如何避免？

- 重绘：当渲染树中的元素外观（如：颜色）发生改变，不影响布局时，产生重绘
- 回流：当渲染树中的元素的布局（如：尺寸、位置、隐藏/状态状态）发生改变时，产生重绘回流
- 注意：JS获取Layout属性值（如：`offsetLeft`、`scrollTop`、`getComputedStyle`等）也会引起回流。因为浏览器需要通过回流计算最新值
- 回流必将引起重绘，而重绘不一定会引起回流





