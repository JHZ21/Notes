# es6+



## ?.  ~~  |>

* [使用js操作符优化代码( ?. )( ~~ )( |＞ )](https://www.cnblogs.com/huangguofeng/p/13735856.html)



## Reflect

> * **Reflect** 是一个内置的对象，它提供拦截 JavaScript 操作的方法。`Reflect`不是一个函数，因此它是不可构造的。
>
> * `Reflect`的所有属性和方法都是静态的（就像[`Math`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math)对象）

* [Reflect ｜ mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect)

* 设计目的
  * 将`Object`对象的一些明显属于语言内部的方法（比如`Object.defineProperty`），放到`Reflect`对象上。
  * 让`Object`操作都变成函数行为。
  * 修改某些`Object`方法的返回结果，让其变得更合理。
  * `Reflect`对象的方法与`Proxy`对象的方法一一对应
  * [js-ES6学习笔记-Reflect ｜good](https://www.cnblogs.com/zczhangcui/p/6486582.html)



### get()

* [Reflect.get() | mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Reflect/get)

``` js
Reflect.get(target, propertyKey[, receiver])
```

> 等于target.propertyKey ，但转为函数形式，并可以传入receiver

* 如果`target`对象中指定了`getter`，`receiver`则为`getter`调用时的`this`值。

* examples

```js
// 获取属性
Reflect.get(['zero', 'one'], 1)  // "one"

// 传入 receiver
let obj = new Proxy(x, {
  get(t, prop, receiver) {
    return receiver[prop] + 'bar'  // Proxy get(target, prop, receiver)
  }
})
Reflect.get(obj, 'foo', y) // "3bar"
```



### set()

* [Reflect.set() | mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Reflect/set)

* ```js
  Reflect.set(target, propertyKey, value[, receiver])
  ```

* receiver 存在则替换掉 setter 调用时的 **this** 值。



## es2017

### async/await

* 在后端, 异步不去await等待，就不执行

* 与Promise.all 组合

```js
async () => {
    const members = await Promise.all(team.map(temmber => {
    	return  users.findOne({userId: temmber.userId})  // 异步函数(async)
    }))
}

```



* 与 forEach 问题

> 函数内部，将异步转为同步效果，等待
>
> 而自身变成了异步， 对外为async，对内await异步

* [async/await 与 forEach 问题](https://segmentfault.com/q/1010000009190129)

* async/awiat 可以对Promise 生效，等待其执行结束

```
async () => {
	await new Promse().then().catch()
	......
}
// 
```

> [Promise.all结合async/await](https://blog.csdn.net/Creabine/article/details/87344158)



## es6



### 模块化

```js
// ES Module
improt library from 'library'
// CommonJs
const library = require('library')
// AMD
require(['library'], function() {})

```





### flat

* [flat() | MDN](https://www.baidu.com/link?url=saBnGesuk0inSI52EKDOyFZki2AIAr6JPuQrZbfQwTopuH4u9PBgUPUhwNb3WoLpoPSwvxFiAuYb5BZmQ1You1m-4oehJYHQzvcMdbz0Nh8XVCGBjiIuTVYqZoCcpd63_3G8GhCex5XEwHKJINKu6_&wd=&eqid=e4ca32cd00076d9f000000055e91d2ed)

* 用法

  ```js
  var newArray = arr.flat([depth])
  ```

* 参数

  > `depth` 可选
  >
  > 提取嵌套数组的结构深度，默认值为 1
  >
  > 也可以 Infinity

* 返回值

  > 一个包含将数组与子数组中所有元素的新数组

* flat方法会移除数组中的空项 (: empty)



### Promise

* [手写Promise 20行](https://juejin.im/post/5e6f4579f265da576429a907)
* [异步编程二三事 | Promise/async/Generator实现原理解析 | 9k字](https://juejin.im/post/5e3b9ae26fb9a07ca714a5cc)

```js
function Promise(exec) {
	this.onResolvedCbs = []
	exec(value => {
		setTimeout(() => {
			this.data = value
			this.onResolvedCbs.forEach(item => item(value))
		})
	})
}
  
Promise.prototype.then = function(onResolved) {
	return new Promise(resolve => {
		this.onResolvedCbs.push(() => {
			const result = onResolved(this.data)
			result instanceof Promise ? result.then(resolve) : resolve(result)
		})
	})
}
```





### Object.freeze()

> **冻结**一个对象， 不能添加新的属性，
>
> 并将所有现有属性标记为不可配置,
>
> value也不能修改,
>
> 此外，该对象的原型也不能被修改，
>
> 浅冻结

* [Object.freeze() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)



### Object.seal()

> `封闭`一个对象, 阻止添加新属性，
>
> 并将所有现有属性标记为不可配置,
>
> 但原来是可写value的就可以改变
>
> 浅封闭
>
> 但可以被覆盖掉，obj= {}

* [Object.seal() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/seal)





### 元编程

* [元编程 | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Meta_programming)



## Promise 另建文档



## 解构赋值

> 可以将属性/值从对象/数组中取出,赋值给其他变量。
>
> ```js
> [a, b] = [10, 20]
> // 左边接受方，必须写明属性
> var x = [1, 2, 3, 4, 5];
> var [y, z] = x;
> ```

### 提取变量赋给新变量

```js
var o = {p: 42, q: true};
var {p: foo, q: bar} = o;
 
console.log(foo); // 42 
console.log(bar); // true 
```

### 解构对象时会查找原型链

```js
// 声明对象
var obj = {};
// 在原型链中定义一个属性 prot
obj.__proto__.prot = '456';
const {prot} = obj;
// prot "456"（访问到了原型链）
```







## export  and import

```javascript
// 导出不用 as xxx
export * from "./permission"

// 导入 需要 as xxx
import * as directives from "@/directives"
```

