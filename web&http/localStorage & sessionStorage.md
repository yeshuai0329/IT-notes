# localStorage

> ​		 `localStorage` 类似 [`sessionStorage`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/sessionStorage)，但其区别在于：存储在 `localStorage` 的数据可以长期保留；而当页面会话结束——也就是说，当页面被关闭时，存储在 `sessionStorage` 的数据会被清除 。



# sessionStorage

> ​		`sessionStorage` 属性允许你访问一个，对应当前源的 session [`Storage`](https://developer.mozilla.org/zh-CN/docs/Web/API/Storage) 对象。它与 [`localStorage`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/localStorage) 相似，不同之处在于 `localStorage` 里面存储的数据没有过期时间设置，而存储在 `sessionStorage` 里面的数据在页面会话结束时会被清除。

- 页面会话在浏览器打开期间一直保持，并且重新加载或恢复页面仍会保持原来的页面会话。
- 打开多个相同的URL的Tabs页面，会创建各自的`sessionStorage`。
- 关闭对应浏览器窗口（Window）/ tab，会清除对应的`sessionStorage`。 
- **在新标签或窗口打开一个页面时会复制顶级浏览会话的上下文作为新会话的上下文，**这点和 session cookies 的运行方式不同。

# html5的存储类型有什么区别？

```
cookies:服务器和客户端都可以访问，大小只有4KB左右，有有效期，过期后将会删除；
localStorage:将数据保存在本地的硬件设备，没有时间限制，关闭浏览器也不会丢失。永久保cun
sessionStorage:将数据保存在session对象中，关闭浏览器后数据也随之销毁。临时保存。
```

