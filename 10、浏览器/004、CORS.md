

> 概念： **跨域资源共享（CORS）**,是一种基于`HTTP `头的机制，该机制通过允许服务器标示除了它自己以外的其它`origin`（域，协议和端口），这样浏览器可以访问加载这些资源。跨源资源共享还通过一种机制来检查服务器是否会允许要发送的真实请求，该机制通过浏览器发起一个到服务器托管的跨源资源的"预检"请求。在预检中，浏览器发送的头中标示有HTTP方法和真实请求中会用到的头。

## 1.1 CORS 头

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

## 1.2 简单请求

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

## 1.3 预检请求

> “需预检的请求”要求必须首先使用 `OPTIONS`  方法发起一个预检请求到服务器，以获知服务器是否允许该实际请求。"预检请求“的使用，可以避免跨域请求对服务器的用户数据产生未预期的影响。

- 非简单请求之前一般会发送 options 请求来做预检请求。
- 可以用来检验某接口是否支持跨域。
- 可以检验某个接口是否支持哪些方法（post,put,delete, 等）
- 如果预检不通过，真实的接口请求就不会发送了

