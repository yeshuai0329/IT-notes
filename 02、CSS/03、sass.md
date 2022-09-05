#### 1.世界上最成熟、最稳定、最强大的专业级CSS扩展语言！

* `sass` 是一个 `css` 的预编译工具
* 也就是能够 **更优雅** 的书写 `css`
  * 可以定义变量
  * 可以定义函数
  * 可以有if语句，可以有for循环语句
* `sass` 写出来的东西 **浏览器不认识**，cass可以写 css代码。
* 依旧是要转换成 `css` 在浏览器中运行
* 这个时候就需要一个工具来帮我们做

#### 2.和css区别

* css文件后缀是.css
* sass文件后缀是.sass或者.scss

#### 3.sass和scss文件区别

* #### 在.scss文件里面和写css语法基本一致

* ```css
  h1 {
      width: 100px;
      height: 200px;
  }
  ```

* 在.sass文件里面没有大括号和分号，全部依靠缩进

* ```SAS
  h1
  	width: 100px
  	height: 200px
  ```

* 这两个文件被编译成css文件是一样的

#### 4.`sass` 安装卸载

* ```shell
  # 安装全局 sass 环境
  $ npm i -g  sass
  #卸载
  $ npm un -g sass
  
  ```

#### 5.sass 编译

* sass单文件编译
  * 你先写好.scss或者.sass后缀的文件
  * 输入指令 `sass  要编译的文件名  编译后的文件名`
  * 每次需要改sass都要重新编译一下
* sass单文件实时编译
  * 你先写好.scss或者.sass后缀的文件
  * 输入指令  `sass --watch 要编译的文件:编译后的文件名`
  * 如果sass有修改，sass实时编译

#### 6.sass常用语法

##### 6.1.sass变量

```SAS
$width = 400px;
$height = 200px;
h1{
	width:$width;
	height:$height
	background-color:#ccc;
}
```

##### 6.2.sass注释

* /*  */sass和css都认识的注释
* // 只有sass认识的注释，不会被编译到css文件中。

##### 6.3.嵌套语法

* 在Sass中，你可以像俄罗斯套娃那样在规则块中嵌套规则块。Sass允许将一套 CSS 样式嵌套进另一套样式中，内层的样式将它外层的选择器作为父选择器。

```SAS
#box{
    width:100px;
    height:100px;
    h1{
        text-align:center;
    }
    span{
        font-size:16px;
        a{
            color:blue
        }
    }
}
//编译后
#box {
    width: 100px;
    height: 100px;
}
#box h1 {
    text-align: center;
}
#box span {
    font-size: 16px;
}
#box span a {
    color: blue;
}
```

##### 6.4.父选择器标识符&

* 指向父选择器，

##### 6.5.@import

- 在css里
  - 在CSS里面 link是页面结构和样式同时加载，@import会等页面结构加载完成后，再加载css样式。
- 在sass里
  - sass的@import规则在生成css文件时就把相关文件导入进来。@import "sidebar";这条命令将把sidebar.scss文件中所有样式添加到当前样式表中。

##### 6.6.混合器（宏）@mixin

* 可以通过混合器让大段样式重用,@include 引入使用

  ```SAS
  @mixin no-bullets {
  	width:200px;
  	height:200px;
  	border:1px solid #ccc
  }
  #box1 {
  	@include no-bullets;
  	background-color:#fff;
  }
  #box2 {
  	@include no-bullets;
  	background-color:#000;
  }
  #box3 {
  	@include no-bullets;
  	background-color:#bbb;
  }
  ```

* 可以传参的混合器 @mixin name (){}

  ```SAS
  @mixin no-bullets ($width,$height) {
  	width:$width;
  	height:$height;
  	border:1px solid #ccc
  }
  #box1 {
  	@include no-bullets(200,400);
  }
  #box2 {
  	@include no-bullets(300,600);
  }
  #box3 {
  	@include no-bullets(300,800);
  }
  ```

##### 6.7.继承 @extend+选择器

```SAS
#box{
    width:100px;
    height:100px;
    h1{
        text-align:center;
    }
    span{
        font-size:16px;
        a{
            color:blue
        }
    }
}
#box2{
	@extend #box;
}
```

##### 6.8.颜色函数

* $color要改变的颜色，$amount取值范围是0~100%

  ```sas
  lighten($color, $amount) //颜色变浅函数；
  darken($color, $amount) //颜色变深函数；
  ```

##### 6.9. sass逻辑结构

* **@if**  当 @if 的表达式返回值不是 false 或者 null 时，条件成立，输出 {} 内的代码：

  ```sas
  p {
      @if 1 + 1 == 2 { border: 1px solid; }
      @if 5 < 3 { border: 2px dotted; }
      @if null { border: 3px double; }
  }
  // 编译为
  p {
      border: 1px solid;
  }
  ```

* **@for**  @for 指令可以在限制的范围内重复输出格式，每次按要求（变量的值）对输出结果做出变动。

  ```SAS
  //第一种写法
  @for $i from 1 through 3 {//循环三次
      
      .item-#{$i} { width: 2em * $i; }
  }
  //相当于
  .item-1{width:2em}
  .item-2{width:4em}
  .item-3{width:6em}
  
  //第二种写法
  @for $i from 1 to 3 {//循环三次
      
      .item-#{$i} { width: 2em * $i; }
  }
  //相当于
  .item-1{width:2em}
  .item-2{width:4em}
  .item-3{width:6em}
  ```

* **function**  Sass支持自定义函数，并能在任何属性值或Sass script中使用

  ```sas
  $grid-width: 40px;
  $gutter-width: 10px;
  @function grid-width($n) {
      @return $n * $grid-width + ($n - 1) * $gutter-width;
  }
  #sidebar1 { width: grid-width(5); }
  #sidebar2 { width: grid-width(4); }
  // 编译为
  #sidebar {
      width: 240px;
  }
  ```

#### 7.gulp-sass安装失败解决办法

1.安装gulp-sass需要依赖，node-sass

```linux
指令 ： npm install node-sass
```

2.node-sass 安装完成后，gulp-sass 的依赖问题也就解决了，然后跳出去 node_modules 目录继续安装 gulp

```linux
指令 ： npm install gulp-sass --save-dev
```





