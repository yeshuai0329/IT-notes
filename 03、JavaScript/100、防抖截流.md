#### 1.什么是ajax？

- AJAX是再一种无需重新加载整个页面的情况下，也能够更新网页部分的技术（局部刷新）
- AJAX是一个异步的代码，再程序中同步异步的区别就是，同步代码按照顺序执行，异步代码不按照顺序执行。

#### 2.ajax的优点？

- 页面无刷新更新数据：ajax最大的优点就是能够在不刷新网页的情况下与服务器通信维护数据；
- 异步与服务器通信：ajax使用异步方式与服务器通信 ，不需要打断用户的操作，具有更加迅速的响应能力；
- 前端和后端负载平衡：ajax可以把以前一些服务端负担的工作转嫁到客户端，减轻服务器和带宽的负担，节约空间和宽带租用成本；
- 基于标准被广泛支持：ajax基本标准化的并被广泛支持的技术，不需要下载浏览器插件；
- 界面与应用分离：ajax使WEB中的数据与呈现分离，有利于分工合作，提高效率。

#### 3.ajax的缺点

- #### ajax干掉了Back和History功能：即对浏览器机制的破坏，在动态页面的情况下，用户无法回到前面一个页面状态；

- ajax有安全问题：ajax技术给用户带来了很好的用户体验的同时也带来了新的安全威胁，ajax技术就如同对企业数据建立了一个直接的通道；

- 对搜索引擎支持较弱：对搜索引擎优化不太好；

- 破坏程序的异常处理机制：像Ajax。dll，Ajaxpro.dll这些Ajax框架是会破坏程序的异常机制；

- AJAX不能很好支持移动端设备；

#### 4.如何使用ajax

- 主流W3C标准浏览器都支持XMLHttpRequest对象

- 低版本IE浏览器使用的是 ActiveXObject

  ##### 4.1.创建ajax对象

  ```javascript
  var xhr = new XMLHttpRequest();//主流W3C标准浏览器
  //考虑兼容
  if(window.XMLHttpRequest){ // 非IE5 IE6
      var xhr=new XMLHttpRequest();
  }else{ // IE5 IE6
      var xhr=new ActiveXObject("Microsoft.XMLHTTP");
  };
  ```

  ##### 4.2.初始化ajax请求

  ```javascript
  xhr.open(method,url,async);
  //参数说明：
  method:请求数据类型 get/post
  url：文件在服务器上的位置
  async： 可选，默认ture（异步），false（同步）
  ```

  ##### 4.3发送请求

  ```javascript
  xhr.send(param);
  //参数说明：
  param:对于get请求，参数为null
  param：对于post请求，参数为发送到服务器的数据
  //为post请求时，需要在send()之前设置http请求头：作用模拟表单post来传递参数
  xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded")
  //get/post区别
  1.语义化不一样
  	GET倾向于从服务器获取数据
      post倾向于从服务器提交数据
  2.传递参数的方式
  	GET请求直接在地址栏后边拼接
      post请求在请求体里面传递
  3.参数大小限制 
  	GET请求一般理论上不大于2KB
      post请求理论上没有上线
  4.缓存能力
  	GET会被浏览器主动缓存
      POST不会被浏览器主动缓存
  5.安全性能
  	GET请求相对安全性较低
      POST请求相对安全性较高
  get/post本质上都是tcp连接
  ```

  ##### 4.4请求-响应状态

  ```javascript
  //readystate  属性存有XMLHttpRequest对象的状态，会从0-4发生变化；
  0：请求未初始化
  1：服务器连接已经建立
  2：请求已经接收
  3：请求处理中
  4：请求已经完成
  //当readystate改变时就会触发onreadystatechange事件
  //status:http请求状态码
  //下面是常见的Http请求状态码：
  200：请求成功
  301：网页被重定向到其他的url
  304：文件未被修改，使用缓存资源
  404：找不到此网页(指定的资源)
  500：服务器内部错误
  //当readyState为 4 且 status为 200 时，表示请求已完成，成功得到响应结果
  xhr.onreadystatechange=function (){
      if (xhr.readyState==4) { // 请求完成
          if (xhr.status==200) { //ok 成功
              alert( xhr.responseText ); // 得到响应结果
          } else{
              alert( xhr.status ); // 弹出失败的状态码
          };
      };
  }
  //xhr.responseText  获得文本形式的响应数据
  //xhr.responseXML  获得 XML 形式的响应数据
  ```

#### 5.封装ajax

##### 5.1封装ajax

```javascript
//封装ajax请求
function ajax(options){
    1.创建XMLHttpRequest对象
    var xhr = new XMLHttpRequest();
    //判断传入的参数类型，处理一下data，变成字符串数据
    //如果data为对象
    var data = "";
    if(typeof options.data === "string"){
        data = options.data;
    }
    if(typeof options.data === "object" && options.data!==null && options.data.constructor === Object){
        //{abc:123, ddd:777}转变成'abc=123&ddd=777'
        for(var key in options.data){
            data += key+"="+options.data[key]+"&";
        }
        //data='abc=123&ddd=777&'
        data = data.substring(0,data.length-1)
        //data='abc=123&ddd=777'
    }
    //判断请求类型
    if(options.type.toLowerCase()==='get'){
        2.初始化一个请求
        xhr.open(options.type,options.url+"?"+data+"&_="+Date.now())
        3.发送一个请求
        xhr.send()
    }else if (options.type.toLowerCase()==='post'){
        2.初始化一个请求
        xhr.open(options.type,options.url)      
        //设置请求头
		xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
        3.发送一个请求
		xhr.send(data)
    }els{
        alert('目前只支持 get和post 请求！')
    }
    4.请求-响应状态
    xhr.onreadystatechange = function () {
		if (xhr.readyState == 4) {
			if (xhr.status >= 200 && xhr.status < 300) {
				options.success(xhr.responseText)
			} else {
				options.error(xhr.status)
			}
		}
	}
}
//参数说明：
options：是一个参数对象
options ={
    type:"GET/POST", //请求的类型
    url：          , //请求的地址
    data:{
    	             //请求携带的参数，支持字符串类型，对象类型
	}，
    success：function(){
        //请求成功的回调，要执行的内容
    }
    error：function(){
        //请求失败的回调，要执行的内容
    }
}
```

##### 5.2.使用Promise封装ajax

```javascript
function promiseAjax(options){
    return new Promise(function(resolve,reject){
        // 1.创建XMLHttpRequest对象（数据交互对象）
        var xhr = new XMLHttpRequest();//w3c标准
        // var xhr = new ActiveXObject('Microsoft.XMLHTTP');//IE 5 6

        var data = '';
        if (typeof options.data === 'string'){
            data = options.data;
        }
        if (typeof options.data === 'object' && options.data !== null && options.data.constructor === Object){
            // 把{abc:123,ddd:777} 转成 'abc=123&ddd=777'
            for (var key in options.data){
                data += key+'='+options.data[key]+'&';
            }
            // data = 'abc=123&ddd=777&';
            data = data.substring(0,data.length-1);
            // console.log(data);
        }
        // return;

        // 判断请求方式
        if (options.method.toLowerCase() === 'get'){
            xhr.open(options.method,options.url+'?'+data+'&_='+Date.now(),true);
            xhr.send(null);// get请求
        } else if (options.method.toLowerCase() === 'post'){
            xhr.open(options.method,options.url,true);
            // 作用是模拟表单post来传递参数
            xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
            xhr.send(data);// post请求发送数据 
        } else {
            alert('目前只支持 get和post 请求！')
        }

        // 4.请求-响应 状态
        xhr.onreadystatechange = function (){
            // console.log(xhr.readyState);
            if (xhr.readyState == 4){//请求完成 （请求状态）
                if(xhr.status >= 200 && xhr.status < 300){// 得到响应数据 （响应状态）
                    resolve(xhr.responseText);
                } else{
                    reject(xhr.status);
                }
            }
        }
    });
}
```
