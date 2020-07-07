## Promise

* [JavaScript Promise迷你书（中文版）](http://liubin.org/promises-book/#introduction)

* [前端工程师必知之Promise的实现 | mdn](https://juejin.im/post/5afd2ff26fb9a07aaa11786c#heading-6)

* ES6采用了 [Promise/A+ 规范](https://promisesaplus.com/)



### Promise.all() 

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



### Promise.race()

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



