##### 1. 同步请求与异步请求是什么？

- 我的理解：同步请求意思是同一段时间内，只能执行一个请求，等该请求执行完毕以后才能执行其他请求；而异步请求是可以在同一时间内发起多个请求，不必等主线程请求执行完毕，就可以通过子线程发起新的请求。

##### 2. 前端请求后端接口的方式有哪些？

1.AJAX

AJAX（Asynchronous JavaScript and XML）是一种在不刷新整个页面的情况下向服务器发送 HTTP 请求和接受响应的技术。在 AJAX 中，前端通过 XMLHttpRequest 对象向后端发送 HTTP 请求，后端返回数据后又通过 JavaScript 进行处理。

2.Fetch

Fetch API 是一种使用 Promise 实现的新一代网络请求 API，它提供了一种更简单和更灵活的网络请求方式。Fetch API 的优点在于更加简洁易懂，能够发出更多类型的网络请求，并且支持多种类型的数据格式，如 JSON、XML、HTML 等。

3.WebSocket

WebSocket 是一种可以在浏览器和服务器之间建立持久连接的通信协议，它能够实现双向通信。WebSocket 的优点在于能够实时更新数据，同时能够极大地减少服务器的负载。

4.JSONP

JSONP（JSON with Padding）是一种在前端通过动态添加 `<script>` 标签的方式来向后端发送 HTTP 请求的技术。JSONP 对比 AJAX 的优点在于它可以跨域请求数据，缺点是不支持 POST 请求，并且需要对接口进行特殊处理。

5.Others

除了上述几种方式，还有许多其他请求后端接口的方式，如使用第三方 HTTP 库（如 Axios、jQuery、Superagent 等）进行请求，或者采用一些跨域解决方案（如 CORS、反向代理、Node.js 中间件等）进行请求。

总之，前端请求后端接口的方式有很多种，应该根据实际情况选择合适的方式来发送请求，并且考虑到网络安全和性能问题，做好相应的防护措施。

##### 3.怎么样同时发起多个请求，并同时获取到结果？

promise.all()方法。

##### 4.css 弹性盒子布局有哪些属性？

display、flex-direction、flex-wrap、justify-content、align-items、align-self 等。