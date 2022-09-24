

#### 1.`jQure`y的选择器

* `$(".box")`          通过类名
* `$("div")`       通过标签名
* `$("#box")`     通过id
* 特殊选择器
  * `$("li:first")`   获取li中的第一个
  * `$("li:last")`   获取li中的最后一个
  * `$("li:eq(3))`   获取li中索引是3的那一个
  * `$("li:odd")`   获取li中索引是奇数的li
  * `$("li:even")`   获取li中索引是偶数的li
* **转换：**
  * `var box = document.querySelector('#box')`; // js对象
  * `var $box = $('#box');` // jq对象
  * JQ获取DOM对象，转domj元素，操作样式
    * `$box[0].style.color = 'blue'`; // 转成 js 对象
    * `$box.get(0).style.color = 'blue'`;// 转成 js 对象
  * JS获取的DOM对象，转JQ对象
    * `$(box).css('color','red');`// 转成 jq 对象

#### 2.`jQurey`筛选器

- `first()`
  - 用法：`$(".box").first()`
  - 含义：.box类名集合下的第一个
- `last()`
  - 用法：`$(".box").last()`
  - 含义：.box类名集合下的最后一个
- `eq()`
  - 用法：`$(".box").eq(3)`
  - 含义：.box类名集合下的索引值为3的那一个
- `next()`
  - 用法：`$('span').next()`
  - 含义：.拿到span标签的下一个兄弟元素
- `nextAll()`
  - 用法：`$('span').nextAll()`
  - 含义：.拿到span标签后边的所有元素
- `nextUntil()`
  - 用法：`$('span').nextUntil(.box)`
  - 含义：.拿到span标签后边到.box元素的所有元素，不包含.box
- `prev()`
  - 用法：`$('span').prev()`
  - 含义：.拿到span标签的上一个兄弟元素
- `prevAll()`
  - 用法：`$('span').preAll()`
  - 含义：.拿到span标签前边的所有元素
- `prevUntil()`
  - 用法：`$('span').prevUntil(.box)`
  - 含义：.拿到span标签后边到.box元素的所有元素，不包含.box
- `parent()`
  - 用法：`$('span').parent()`
  - 含义：.找出span标签的父元素
- `parents()`
  - 用法：`$('span').parents()`
  - 含义：.找出span标签的所有父元素，直到html元素为止
- `parentsUntil()`
  - 用法：`$('span').parentsUntil(选择器)`
  - 含义：.找出span标签的所有父元素，直到`选择器`元素为止
- `children()`
  - 用法：`$('span').children()`
  - 含义：.筛选出元素所有的子级元素
  - 用法：`$('span').children(选择器)`
  - 含义：.筛选出span元素中所有的符合 `选择器` de 子级元素
- `sibilings()`
  - 用法：`$('span').sibilings()`
  - 含义：.筛选出span标签的所有的兄弟级元素
- `find()`
  - 用法：`$('span').find(.box)`
  - 含义：.筛选出span标签中所有子代元素里类名为`.box`的元素
    - 在一个元素的后代元素中查找对应选择器的元素
    - 在一个元素集合的每一个元素中, 查找后代元素
- `index()`
  - 用法：`$('span').index()`
  - 含义：.拿到span在其父元素的索引值

#### 3.`jQurey`操作文本内容

- `html()`
  - 语法：`$("div").html()`
  - 不传参数的时候，就是获取元素内部的超文本内容
  - 传递参数的时候，就是设置元素的超文本内容
- `text()`
  - 语法：`$("div").text()`
  - 不传参数的时候，就是获取元素内部的文本内容
  - 传递参数的时候，就是设置元素的文本内容
- `val()`
  - 语法：`$("div").val()`
  - 不传参数的时候，就是获取`input`标签的`value`值
  - 传递参数的时候，就是设置就`input`标签的`value`值
- 总结：
  - 获
    - `html()`:只能获取第一个元素的超文本内容
    - `text()`：能获取元素集合内所有元素的文本内容合
    - `val()`：只能获取第一个元素的 value 值
  - 设置：
    - `html()`:给元素集合内所有的元素设置超文本内容
    - `text()`：给元素集合内所有的元素设置文本内容
    - `val()`：给元素集合内所有的元素设置` value `值

#### 4.`jQurey`操作元素类名

- `addClass()`添加类名
  - 语法：`$("span").addclass("box")`
  - 注释：执行这个方法会给元素集合里面所有的元素添加上固定的类名，如果有就不添加了，没有才会添加
- `removeClass()`移除类名
  - 语法：`$('div').removeClass('box')`
  - 注释：移除div集合中含有类名.box的div的雷鸣
- ` toggleClass()`切换类名
  - 语法：`	$('div').toggleClass('container')`
  - 注释：执行这个方法会给所有元素加上这个类名，有的删除，没得加上
- ` hasClass()`判断有没有这个类名
  - 语法：`$('div').hasClass('box')`
  - 注释：会返回一个布尔值

#### 5.`jQurey`操作元素的样式

- `css("样式名称")`

  - 获取元素集合的第一个元素的样式值，不管是行内样式还是非行内样式都能获取

- `css("样式名称"，'样式的值')`

  - 设置元素的样式值, 元素集合能获取多少个元素就设置多少个元素
  - 设置的时候, 所有的单位都可以不写, 默认添加 px 为单位

- `css(对象)`

  - css({

    width：100，

    height：100，

    })

  - 批量设置 css 样式

  - 给元素集合里面的所有元素, 批量设置样式

#### 6.`jQurey`操作元素的属性

- `attr()`                `attribute`

  - attr(要读取的属性名),传递一个参数的时候是读取
  - attr(属性名, 属性值): 传递两个参数的时候是设置

  `removeAttr()`

  * 专门用来移除属性的

   **attr 这套方法的注意:**

  - 所有的属性都会显示在标签上(原生属性和自定义属性)
  - 不管你设置的是什么数据类型, 都会给你变成字符串
  - removeAttr 删除 attr 设置的属性, 有多少删除多少(针对自定义属性)

- `prop()`           `property`

  - prop(要读取的属性名): 传递一个参数的时候是读取
  - prop(属性名, 属性值): 传递两个参数的时候是设置

  ` removeProp()`

  -  专门用来移除属性的

   **prop 这套方法的注意:**

  -  非原生属性, 不会显示在标签上, 但是你可以获取使用
  -  你存储的是什么数据类型, 获取的时候就是什么数据类型
  -  removeProp 删除 prop 设置的属性, 有多少删除多少(针对自定义属性)
  -  removeProp() 不能删除原生属性 id class style 这样的

- `data()`

  - data(要读取的属性名): 传递一个参数的时候是读取
  - data(属性名, 属性值): 传递两个参数的时候是设置

   `removeData()`

  - 专门用来删除数据的

  **data 这套方法的注意:**

  * 和元素的原生属性没有关系, 可以设置 id, 但是和元素的 id 没关系
  * 就是在元素身上给你开辟一个地方, 存储一些数据
  * 你设置的是什么数据类型, 拿到的就是什么数据类型
  * removeData 删除 data 设置的属性
  * data() 方法也能读取写在标签上的 H5 标准自定义属性

  - 三个方法存储内容
    - attr 设置的自定义属性存储在标签身上
    - prop 设置的自定义属性存储在元素对象里面
    - data 设置的自定义属性存储在元素对象里面单独开辟的一个对象

#### 7.`jQurey`绑定事件

* `on()`

  * ` on('事件类型', 事件处理函数)`

    * 给元素集合内所有的元素绑定一个事件

    * ```javascript
      $('ul').on('click', function handlerA() { console.log('我是事件处理函数 ') })
      ```

  * `on('事件类型', '事件委托', 事件处理函数)`

    * 把 事件委托 位置的元素的事件 委托给了前面的元素集合

    * ```javascript
      $('ul').on('click', 'li', function () {
            console.log('我被点击了, 事件委托')
          })
      ```

  * `on('事件类型', 复杂数据类型, 事件处理函数)`

    * 给每一个元素绑定一个事件, 复杂数据类型是触发事件的时候传递的参数

    * ````javascript
      $('li').on('click', { name: 'Jack', age: 18 }, function (e) {
            console.log('我被点击了, li')
            console.log(e)
          })
      ````

  * ` on('事件类型', '事件委托', 任意数据类型, 事件处理函数)`

    * 做一个事件委托的形式, 第三个参数位置的数据

    * 是触发事件的时候, 可以传递进去的数据

    * ```javascript
      给 li 做一个事件委托, 委托给了 ul
            每一个 li 点击的时候都能得到一个传递进去的数据叫做 hello world
          $('ul').on('click', 'li', 'hello world', function (e) {
            console.log('我又被点击了')
            console.log(e)
            console.log(this) // 就是你点击的那一个 li
          })
      ```

  * `on(对象)`

    * 给一个元素绑定多个事件的方式

    * ```javascript
      给 ul 同时绑定三个事件
            这个时候就不能传递参数了
            这个时候就不要贪图事件委托了
          $('ul').on({
            click: function () { console.log('点击事件') },
            mouseover: function () { console.log('移入事件') },
            mouseout: function () { console.log('移出事件') }
          })
      ```

  * `off( event , selector , fnName )`  on()的反向操作，移除用on()绑定的事件

* **事件绑定及移除**

  * `bind( )` 为每个匹配的元素绑定一个或多个事件处理函数语法：bind( event , fn ) //不能给未来元素添加事件

    * ```javascript
      $("p").bind("click", function(){
          alert( $(this).text() );
      });
      
      $('h2').bind({
          mouseover: function (){
              alert('移上');
          },
          mouseout: function (){
              alert('移出');
          }
      })
      ```

  * `unbind( )` 与 `bind( )` 反向的操作，删除元素的一个或多个事件语法：`unbind(event , fnName )`

#### 8.事件对象

* 阻止冒泡/传播：e.stopPropagation()      return false;
* 阻止默认行为：e.preventDefault();        return false;
* 事件类型：
  * e.type触发事件的元素：
  * e.target ( 原生DOM节点 )
  * 指示按了哪个键或按钮：e.which 1 2 3
  * 鼠标的相对坐标：e.clientX/Y  e.pageX/Y
  * 事件发生时的时间戳：e.timeStamp（毫秒数）

#### 9.`jQurey`的节点操作

* 创建节点

  * ` $() `或者` jQuery()`
    * () 里面传递一个 html 格式文本的时候就是创建节点
    * () 里面传递一个选择器的时候, 就是获取页面中的 DOM 元素
    * () 里面传递一个选择器的时候, 就是获取页面中的 DOM 元素
    * () 里面传递一个 html 格式文本的时候, 就是创建一个 DOM 元素
    * 例子：`$('<div>我是一个创建出来的节点</div>')`

* 插入节点

  * 在页面元素内部插入

    - 语法：在后面插入
      1. `页面元素.append(要插入的元素)`
      2. `要插入的元素.appendTo(页面元素)`
    - 语法：在前面插入
      1. `页面元素.prepend(要插入的元素)`
      2. `要插入的元素.prependTo(页面元素)`

* 删除节点

  * 语法：
    1. `页面元素.empty()`-> 把自己变成空标签
    2. `页面元素.remove() `-> 把自己移除

* ##### 替换节点

  - 语法：
    1. `页面元素.replaceWith(替换元素)`
    2. `替换元素.replaceAll(页面元素)`

* ##### 克隆节点

  - 语法：`元素.clone()`
    1. 第一个参数: 自己的事件是否克隆
    2. 第二个参数: 子节点的事件是否克隆(当第一个参数为 false 的时候, 第二个参数没有意义)

  ​	注意：不管你是否传递参数, 都会把所有后代元素都克隆下来

#### 10.`jQurey`获取元素的尺寸

* 三套方法, 四种使用方式:
  * `width()`和 `height()`
    - 注释：获取元素的内容区域的尺寸（content）
  * `innerWidth() `和 `innerHeight()`
    - 注释：获取的元素的内容区域+padding区域的尺寸

  * `outerWidth() `和 `outerHeight()`
    - 注释：获取的元素的内容区域+padding区域+border的尺寸

  * `outerWidth(true) `和 `outerHeight(true)`
    - 注释：获取的元素的内容区域+padding区域+border+margin的尺寸

#### 11.`jQurey`获取元素的位置

* `offset()`
  * 语法：
    1. 不传递参数就是读取，读到的元素相对于页面的位置关系，返回值是一个对象 { left: xxx, top: xxx }
    2. 传递一个对象就是写入 { left: xxx, top: xxx }
* `position()`
  - 语法：
    1. 只读的方法,元素相对于定位父级的位置关系,得到的也是一个对象 { left: xxx, top: xxx }

#### 12.`jQurey`获取页面卷去的尺寸

* `scrollTop()`/`scrollLeft()`
  - 语法：
    1. 不传递参数的时候就是获取卷去的高度/宽度
    2. 传递一个参数就是设置卷去的高度/宽度

#### 13.`jQurey`的函数

* `ready()` 事件

  - 类似于 window.onload 事件
  - window.onload -> 会在页面所有资源加载完毕执行
  - ready() -> 会在页面 html 结构加载完毕后执行
  - 也叫做 jQuery 的入口函数
  - 有一个简写的形式`$(function () {})`

* `each()`方法

  - 类似于` forEach()`, 遍历数组的

  - jQuery 的元素集合, 是一个 jQuery 数组, 不是一个数组, 不能使用 forEach()

  - ```javascript
    $('div').each(function (index, item) {
       // index -> 就是索引
       // item -> 就是每一项
       console.log(index, item)
     })
    ```

#### 14.`jQurey`的动画

* 标准动画

  * `show()`        显示

    - 语法：show(时间, 运动曲线, 运动结束的函数)

    - ```javascript
      $('div').show(2000, 'linear', function () {
             console.log('显示结束')
           })
      ```

  * `hide()`        隐藏

    - 语法：hide(时间, 运动曲线, 运动结束的函数)

    - ```javascript
      $('div').hide(2000, 'linear', function () {
             console.log('隐藏结束')
           })
      ```

  * `toggle()`   切换(如果是隐藏就显示, 如果是显示就隐藏)

    - 语法：toggle(时间, 运动曲线, 运动结束的函数)

    - ```javascript
      $('div').toggle(2000, 'linear', function () {
             console.log('切换结束')
           })
      ```

* 折叠动画

  * `slideDown()` -> 下滑显示

    - 语法: slideDown(时间, 运动曲线, 运动结束的函数)

    - ```javascript
      $('div').slideDown(2000, 'linear', function () {
             console.log('下滑结束')
           })
      ```

  * `slideUp()` -> 上滑隐藏

    - 语法: slideUp(时间, 运动曲线, 运动结束的函数)

    - ```javascript
      $('div').slideUp(2000, 'linear', () => console.log('上滑结束'))
      ```

  * ` slideToggle() `-> 切换滑动显示和隐藏

    - 语法: slideToggle(时间, 运动曲线, 运动结束的函数)

    - ```javascript
      $('div').slideToggle(2000, 'linear', function () {
             console.log('切换结束')
           })
      ```

* 渐隐渐显动画

  * `fadeIn()` -> 渐渐的显示(贱贱的显示)
    -  语法: fadeIn(时间, 运动曲线, 运动结束的函数)
  * ` fadeOut()` -> 渐渐的消失
    - 语法: fadeOut(时间, 运动曲线, 运动结束的函数)
  * `fadeToggle()` -> 渐渐的切换显示和消失'
    - 语法: fadeToggle(时间, 运动曲线, 运动结束的函数)
  * `fadeTo()` -> 去到一个你指定的透明度
    - 语法: fadeTo(时间, 你指定的透明度, 运动曲线, 运动结束的函数)

* 综合动画

  * `animate()`

    * 基本上大部分的 css 样式都可以动画

    * transform 不行, 颜色不行

    * 语法: animate({}, 时间, 运动曲线, 运动结束的函数)

    * ```javascript
      $('button').click(() => {
           $('div').animate({
             width: 300,
             height: 300,
             left: 30,
             top: 50,
             borderRadius: '50%',
             opacity: 0.5
           }, 2000, 'linear', () => console.log('运动结束'))
         })
      ```

* 停止动画

  * `stop()`
    - 当这个函数触发的时候, 就会让运动立刻停下来
    - 你运动到哪一个位置了就停止在哪一个位置
  * `finish()`
    - 当这个函数触发的时候, 就会让运动立刻停下来
    - 不管你运动到了哪一个位置, 瞬间到达运动完成位置

#### 15.$符冲突问题

* **noConflict()方法**

  * `jQuery`中的`noConflict( )`方法的作用就是让`jQuery`放弃对$符的所有权当代码中调用该方法后，不可以使用$来调用`jQuery`方法

    * `$.noConflict( );`
      * ``$(‘#div’).click(....)`;  //无效
      * `jQuery(‘#div’).click(....)`;  //有效

  * `jQuery`中允许我们自定义`jQuery`的别名

    * `var jq=$.noConflict();`
      * `jq(‘#div’).click(....);` //有效
      * `jQuery(‘#div’).click(....);` //有效
      * `$(‘#div’).click(....);` //无效 报错

  * 如何继续使用$符

    * `$.noConflict( );`

    * ```javascript
      jQuery(function ($){    $(‘h1’).click( function (){ alert($(this).html( ) );});
      ```

#### 16.`jQuery`扩展 ( 插件开发接口 )

* **$.extend()方法**

  * `jQuery.extend（[boolean],target [，object1] [，objectN]）`

  * [boolean] 表示是否深拷贝，默认false 浅拷贝当提供两个或多个对象参数时，其他对象的属性将合并到目标对象。

  * ```javascript
    var obj1 = {a: 1, b: 2, c: {d: 4, e: 5}};
    var obj2 = {c: {g: 7}, d: 8};
    $.extend(obj1,obj2); //浅拷贝
    $.extend(true,obj1,obj2); //深拷贝
    
    for (var key in obj2){ //浅拷贝
        obj1[key] = obj2[key];
    }
    
    var obj3 = JSON.stringify(obj2); //深拷贝
    
    Object.assign(obj1,obj2); //浅拷贝
    
    console.log( obj1.c === obj2.c );
    ```

#### 17.`jQuery ajax`

* `$.ajax( options )` 通过 HTTP 请求加载远程数据

  * url：请求的url地址
    type：请求类型（get/post...）
    cache：是否读取缓存，默认true
    data：要发送给服务器的数据，示例："name=jack&age=19"string或Object{name:"jack",age:"19"}
    async：默认true，为异步请求
    dataType：服务器返回的数据类型特殊的格式JQ会进行预解析和兼容性修复。可选择的值："xml" , "html" , "script" , "json" , "text"，”jsonp”等
    timeout：设置超时（毫秒）
    success：请求成功的回调函数
    error：请求失败的回调函数
    complete：请求完成后的回调函数，无论成功与失败 
    beforeSend：发送请求前可以修改XMLHttpRequest对象的函数，例如添加自定义 HTTP头。在beforeSend中如果返回false可以取消本次ajax请求。XMLHttpRequest对象是惟一的参数。

  * ```javascript
    $('#login').click(function (){
        $.ajax({
            type:'get',
            url:'test.php',
            dataType:'json',
            cache:false, //不使用缓存
            success:function (json){
                $('h1').html(json.name+json.sex+json.age);
            },
            error:function (){
                alert('请求失败');
            }
        });
    })
    ```

* `serialize( )`

  * 将一个form表单内的所有数据转换为可以发送给服务器的字符串示例

    * ```javascript
      $("form").serialize()
      "name=小明&age=19&msg=abc"
      ```

* `$.get( url [, data] [, callback] [, dataType]);`

  * url : 请求的URL

    data ： 可选，发送至服务器的数据

    callback ： 可选，请求完成时的回调函数

    dataType ： 可选，参照$.ajax参数中的dataType

  * ```javascript
    $.get(“act.php”,{user:“cainiao”,pass:“123”},function (data){
        alert(data.msg);
    },“json”);
    ```

* `$.post()`

  * $.post 与 $.get 语法相同，唯一的不同就是请求是以post方式进行。

  * ```javascript
    $.post(“act.php”,{user:“cainiao”,pass:“123”},function (data){
        alert(data.msg);
    }, ”json”);
    ```

#### 18.`jsonp：`跨域请求

* ```javascript
  ipt.onkeyup=function (){
      $.ajax({
          type:'get',
          url:'http://suggestion.baidu.com/su?wd='+$('#ipt').val(),
          dataType:'jsonp',
          jsonp:'cb',
          // jsonpCallback:'mycallback',
          success:function (json){
              // $('#list').empty();
              $('#list').html('');
              for (var i = 0; i < json.s.length; i++) {
                  $('#list').append('<li>'+json.s[i]+'</li>');
              }
          }
      });
  }
  ```

