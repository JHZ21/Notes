# Fetch

> 提供了一个全局 fetch() 方法，该方法提供了一种简单，合理的方式来跨网络异步获取资源。
>
> 使用了 Promise 来处理结果/回调

* 



## demo

```js
fetch('http://example.com/movies.json'，
    body: JSON.stringify(data), // must match 'Content-Type' header
    cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'same-origin', // include, same-origin, *omit
    headers: {
      'user-agent': 'Mozilla/4.0 MDN Example',
      'content-type': 'application/json'
    },
    method: 'POST', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, cors, *same-origin
    redirect: 'follow', // manual, *follow, error
    referrer: 'no-referrer', // *client, no-referrer
  )
  .then(function(response) {
    return response.json();  // parses response to JSON
  })
  .then(function(myJson) {
    console.log(myJson);
  });
```



## fetch 与 ajax 区别

* 即使接受到一个代表错误的HTTP 状态码时， 返回的 Promise不会被标记为 reject， 而是 **resolve **。  即使响应的 HTTP 状态码是 404 或 500。（但是会将 resolve 的返回值的 `ok` 属性设置为 false ）。

  仅当**网络故障**时或请求被阻止时，才会标记为 reject。

* fetch **默认不会发送 cookies**。除非你使用了*credentials* 的。 默认的 credentials 政策变更为 `same-origin`。



## credentials

> 请求凭据设置

* include

> 让浏览器发送包含凭据的请求（即使是跨域源）

* same-origin

> 只想在请求URL与调用脚本位于同一起源处时发送凭据

* Omit

> 让浏览器不在请求中包含凭据

