# 异步

## Promise

### 解决回调地狱



+ ![][p0]

  
  
  - resolve() 与 reject() 执行后，无法改变状态，但剩下代码还是会继续运行。而throw err 抛出错误，则再它下面的代码不会再运行。
  
  - then(), catch() 是微任务，所以在console.log("lala")后立马执行。
  
    
  
+ Promise对象的错误具有“冒泡”性质，会一直向后传递，直到被捕获为止。也就是说，错误总是会被下一个`catch`语句捕获。

  

+  resolve() 参数 是 Promise 对象时，等待其状态改变。

  ![][p1]



[使用Promise,  在旧式回调 API 中创建 Promise ](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Using_promises)

[JavaScript Promise](https://www.cnblogs.com/rubylouvre/p/3495286.html)

```js
new Promise((resolve, reject)=>{
    resolve()
    reject()}).then(()=> console.log('resolve')).catch(()=>console.log('reject'))
> resolve
// reject()会执行但，状态不会改变
```

```js
new Promise((resolve, reject)=>{
    resolve()
    console.log('1')}).then(()=> console.log('resolve')).catch(()=>console.log('reject'))
> 1
> resolve
```





## async函数

* ES7提供了`async`函数，使得异步操作变得更加方便。`async`函数是什么？一句话，`async`函数就是Generator函数的语法糖。
* `async`函数返回的**Promise**对象，必须等到内部所有`await`命令的Promise对象执行完，才会发生状态改变。也就是说，只有`async`函数内部的异步操作执行完，才会执行`then`方法指定的回调函数。但，只要一个`await`语句后面的Promise变为`reject`，那么整个`async`函数都会中断执行。





​	[[译] 6个Async/Await使用的地方](https://zhuanlan.zhihu.com/p/26260061) 评论区中肯

​	[ES6系列文章 异步神器async-await](https://segmentfault.com/a/1190000011526612)





















[p0]: http://proudmodest.cn/img/promise/00.png
[p1]:   http://proudmodest.cn/img/promise/01.png



