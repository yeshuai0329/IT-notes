

### 1、请求报文

> 概念： 一个HTTP请求报文由请求行（request line）、请求头部（header）、空行和请求体4个部分组成。

**大致结构：**

```javascript
＜request-line＞ //请求行

＜headers＞ //请求头

＜blank line＞ // 空行

＜request-body＞ //请求体
```

#### 1.1 请求行

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

#### 1.2 请求头

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

#### 1.3 请求空行

> 请求头之后是一个空行，通知服务器以下不再有请求头。

#### 1.4 请求体

> `GET` 没有请求体，`POST`有



### 2、响应报文

> HTTP响应报文和请求报文的结构差不多，也是由四个部分组成：

```javascript
＜status-line＞   //状态行

＜headers＞   //消息报头

＜blank line＞   //空行

＜response-body＞    //响应体
```

#### 2.1 状态行

> 状态行也由三部分组成：服务器HTTP协议版本，响应状态码，状态码的文本描述

```javascript
比如：HTTP/1.1 200 OK
```

##### 2.1.1状态码 

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

