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









































