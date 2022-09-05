

> HTTP Cookie（也叫 Web Cookie 或浏览器 Cookie）是服务器发送到用户浏览器并保存在本地的一小块数据，它会在浏览器下次向同一服务器再发起请求时被携带并发送到服务器上。通常，它用于告知服务端两个请求是否来自同一浏览器，如保持用户的登录状态。Cookie 使基于无状态的HTTP协议记录稳定的状态信息成为了可能。

## 1、曾经Cookie 主要用于以下三个方面：

- 会话状态管理（如用户登录状态、购物车、游戏分数或其它需要记录的信息）
- 个性化设置（如用户自定义设置、主题等）
- 浏览器行为跟踪（如跟踪分析用户行为等）

**！！！注意：** Cookie 曾一度用于客户端数据的存储，因当时并没有其它合适的存储办法而作为唯一的存储手段，但现在随着现代浏览器开始支持各种各样的存储方式，Cookie 渐渐被淘汰。由于服务器指定 Cookie 后，浏览器的每次请求都会携带 Cookie 数据，会带来额外的性能开销（尤其是在移动环境下）。新的浏览器API已经允许开发者直接将数据存储到本地



## 2、创建 cookie

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



## 3、cookie 的声明周期

-  会话期 Cookie 是最简单的 Cookie：浏览器关闭之后它会被自动删除，也就是说它仅在会话期内有效。会话期Cookie不需要指定过期时间（`Expires`）或者有效期（`Max-Age`）。需要注意的是，有些浏览器提供了会话恢复功能，这种情况下即使关闭了浏览器，会话期Cookie 也会被保留下来，就好像浏览器从来没有关闭一样，这会导致 Cookie 的生命周期无限期延长。
- 持久性 Cookie 的生命周期取决于过期时间（`Expires`）或有效期（`Max-Age`）指定的一段时间。



## 4、Cookie 的作用域

> `Domain` 和 `Path` 标识定义了Cookie的*作用域：*即允许 Cookie 应该发送给哪些URL。

### 4.1 Domain 属性

​		`Domain` 指定了哪些主机可以接受 Cookie。如果不指定，默认为 origin，**不包含子域名**。如果指定了`Domain`，则一般包含子域名。因此，指定 `Domain` 比省略它的限制要少。但是，当子域需要共享有关用户的信息时，这可能会有所帮助。 

​		例如，如果设置 `Domain=mozilla.org`，则 Cookie 也包含在子域名中（如`developer.mozilla.org`）。

### 4.2 Path 属性

​		`Path` 标识指定了主机下的哪些路径可以接受 Cookie（该 URL 路径必须存在于请求 URL 中）。以字符 `%x2F` ("/") 作为路径分隔符，子路径也会被匹配。

例如，设置 `Path=/docs`，则以下地址都会匹配：

- `/docs`
- `/docs/Web/`
- `/docs/Web/HTTP`

## 5、SameSite 

​		Cookie 允许服务器要求某个 cookie 在跨站请求时不会被发送，其中  [Site (en-US)](https://developer.mozilla.org/en-US/docs/Glossary/Site) 由可注册域定义），从而可以阻止跨站请求伪造攻击（[CSRF](https://developer.mozilla.org/zh-CN/docs/Glossary/CSRF)）。

`SameSite `可以有下面三种值：

- **`None`**。浏览器会在同站请求、跨站请求下继续发送 cookies，不区分大小写。
- **`Strict`。**浏览器将只在访问相同站点时发送 cookie。（在原有 Cookies 的限制条件上的加强，如上文 “Cookie 的作用域” 所述）
- **`Lax`。**与 **`Strict`** 类似，但用户从外部站点导航至URL时（例如通过链接）除外。 在新版本浏览器中，为默认选项，Same-site cookies 将会为一些跨站子请求保留，如图片加载或者 frames 的调用，但只有当用户从外部站点导航到URL时才会发送。如 link 链接

`SameSite` 默认值是 `Lax`,也可以设置成  `None ` 和 ` Strict` 。















