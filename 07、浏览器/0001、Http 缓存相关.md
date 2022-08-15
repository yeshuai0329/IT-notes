## 1、HTTP 

>  概念：**超文本传输协议**（http）是一个用于传输超媒体文档的应用层协议。它是为web浏览器和web服务器之间的通信而设计的，但也可以用于其他目的。



## 2、HTTP 缓存

> 概念： 客户端向服务端请求资源（比如图片、代码文件等）时，将资源缓存在客户端或者客户端和服务端中间节点（cdn、代理服务器等）的一种技术。

- 缓存的优点：
  - 复用以前获取的资源，显著提高网站和应用程序的性能。
  - 减轻服务端带宽压力和服务器请求数量。



## 3、HTTP 配置缓存

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



## 4、服务端如何校验客户端缓存是否有效

- `response header`: ETag 或者 last-Modified
- `request header`： if-None-Match 或者if-Modified-Since

！！！ **注意：**1. 当客户端第一次发送请求的时候，服务端会返回一个`ETag` 或者`last-Modified` 字段。2.当客户端发送第二次请求的时候，浏览器会自动处理，为http请求，`request header` 中添加 `if-None-Match` 或者` if-Modified-Since` 字段。字段值是上次服务端返回的对应的` ETag` 或者`last-Modified` 字段的值。

！！！ **注意：** Nginx 服务器默认的`ETag` 只是根据文件的最后修改时间和文件的长度生成 `ETag`。 



## 5、缓存相关文章

1.[图解http缓存](https://zhuanlan.zhihu.com/p/55623075)

2.[HTTP缓存知道这些就够了](https://cloud.tencent.com/developer/article/1870593)

3.[一文彻底掌握HTTP缓存](https://zhuanlan.zhihu.com/p/342774826)

4.[哔哩哔哩 http缓存](https://www.bilibili.com/video/BV17V411J78W?spm_id_from=333.999.0.0)

