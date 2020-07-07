# koa



## koa-static

> [koa-static | npm](https://www.npmjs.com/package/koa-static)

* opts.maxage

```js
app.use(require('koa-static')(__dirname + '/public', {
	maxage: 31536000000 // 强制缓存一年 单位为ms
}))
```

