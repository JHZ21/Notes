# Promise



* [JavaScript Promise迷你书（中文版）](http://liubin.org/promises-book/#introduction)
* [前端工程师必知之Promise的实现 | mdn](https://juejin.im/post/5afd2ff26fb9a07aaa11786c#heading-6)
* ES6采用了 [Promise/A+ 规范](https://promisesaplus.com/)

* [Promise | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* 
* 

## Promise 状态

* pending
* fulfilled
* rejected



* rejected

> Promise 内部错误 或者reject() 没有被捕获，将抛出错误。



## 手撕promise

```js
// Promsie
function Promise(exec) {
    this.onResolvedCbs = []
    exec(value => {
        setTimeout(() => {
            this.data = vaue
       		this.onResolvedCbs.forEach(item => 
                item(vlaue)
            )
        })
    })
}
Promise.prototype.then = function(onResolved) {
    return new Promise(resolve => {
        this.onResolvedCbs.push(() => {
            const result = onResolved(this.data)
            result instanceOf Promise ? 
              result.then(resolve): resolve(result)
        })
    })
}
```





## Promise.then()

* [Promise.then()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)

* Promise.then() 具体的返回状态与值

| 函数内容      | 返回状态              | 返回参数                |
| ------------- | --------------------- | ----------------------- |
| 没有返回值    | fulfilled             | undefined               |
| 返回了一个值  | fulfilled             | 返回的值                |
| 抛出一个错误  | rejected              | 抛出的错误              |
| 返回了Promise | 就是返回Promise的状态 | 与返回Promise的参数一致 |



## Promise.all() 

* Promise.all 的实现

```js
Promise.all = function (promiseArrs) { //在Promise类上添加一个all方法，接受一个传进来的promise数组
    return new Promise((resolve, reject) => { //返回一个新的Promise
        let arr = []; //定义一个空数组存放结果
        let i = 0;
        function handleData(index, data) { //处理数据函数
            arr[index] = data;
            i++;
            if (i === promiseArrs.length) { //当i等于传递的数组的长度时 
                resolve(arr); //执行resolve,并将结果放入
            }
        }
        for (let i = 0; i < promiseArrs.length; i++) { //循环遍历数组
            promiseArrs[i].then((data) => {
                handleData(i, data); //将结果和索引传入handleData函数
            }, reject)
        }
    })
}
```

## Promise.race()

* Promise.race 实现

```
Promise.race = function (promises) {
    return new Promise((resolve, reject) => {
        for (let i = 0; i < promises.length; i++) {
            promises[i].then(resolve, reject);
        }
    })
}
```



