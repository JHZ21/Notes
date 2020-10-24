# this 

> `this`指向的是函数的**执行环境**，`this`取决于其被谁调用了，而不是被谁定义了。

## 好文

* [JavaScript中的this](https://juejin.im/post/59748cbb6fb9a06bb21ae36d)
* [apply/call/bind 自我实现](https://mp.weixin.qq.com/s?__biz=MzI5MjUxNjA4Mw==&mid=2247485110&idx=1&sn=97fd7d83e35495ca1077cb7d3745db50&chksm=ec017f2adb76f63c818c25a8b9cd3da6d5164521fd3572aa042d55b339331807acf4cd106cfe&mpshare=1&scene=23&srcid=&sharer_sharetime=1570782915792&sharer_shareid=4ecc76568e47f0902b9a60f7ac6e2b72#rd)



## 题目

```javascript
function setname(name) {
    this.name = name
}
setname.prototype.printName = function() {
    console.log(this.name)
}
let a = new setname("cc")
a.name = "dd"
a.__proto__.name = "ee"

a.__proto__.printName()  // ?
a.printName() // ?
```

**正解：** ee dd





## setTimeout this

> 由 setTimeout() 调用的代码运行在与所在函数完全分离的执行环境上。这会导致，这些代码中包含的 `this` 关键字在非严格模式会指向 `window` (或全局)对象，严格模式下为 undefined，这和所期望的`this`的值是不一样的。



## 1、默认指定

## 2、隐式指定

## 3、 显式指定

## 4、() => {}  箭头函数

* [js中this指向、箭头函数](https://www.cnblogs.com/ckAng/p/10595259.html)
* 箭头函数本身是没有this和arguments的，在箭头函数中引用this实际上是调用的是`定义`时的上一层作用域的this。
  这里强调的是上一层作用域，是因为`对象是不能`形成独立的作用域的。

## 5、 New 

* 箭头函数会捕获其`所在上下文`的 `this` 值，作为自己的 `this` 值
* new： 函数作为构造函数调用的时，上下文环境的this指向实例对象

* 手写 new

  `new`被调用后做了三件事情:

  1. 让实例可以访问到私有属性
  2. 让实例可以访问构造函数原型(constructor.prototype)所在原型链上的属性
  3. 如果构造函数返回的结果不是引用数据类型

  ```js
  function newFactory(ctor, ...args) {
      if(typeof ctor !== 'function'){
        throw 'newOperator function the first param must be a function';
      }
      let obj = new Object();
      // obj.__proto__.__proto__ = ctor.prototype
      // 中间隔一个原型， 相当于ctor子类，使得obj原型扩展内容时，不会污染到ctor.prototype
      obj.__proto__ = Object.create(ctor.prototype);
      let res = ctor.apply(obj, ...args);
      
      let isObject = typeof res === 'object' && typeof res !== null;
      let isFunction = typoof res === 'function';
      return isObect || isFunction ? res : obj;
  };
  ```

  

## 6、bind

* 手写bind

1. `bind` 与 `call/apply` 的区别就是返回的是一个待执行的函数，而不是函数的执行结果;
2. `bind` 返回的函数作为构造函数与 `new` 一起使用，绑定的 `this` 需要被忽略;

> 调用绑定函数时作为this参数传递给目标函数的值。如果使用new运算符构造绑定函数，则忽略该值。—— MDN

```js
Function.prototype.bind = function(context, ...initArgs) {
    // bind 调用的方法一定要是一个函数
    if (typeof this !== 'function') {
      throw new TypeError('not a function');
    }
    let self = this;
    let F = function() {};
    F.prototype = this.prototype;
    let bound = function(...finnalyArgs) {
      // 将前后参数合并传入
      return self.call(this instanceof F ? this : context || this, ...initArgs, ...finnalyArgs);
    }
    bound.prototype = new F();
    return bound;
}
```



## 7、call/apply

```js
Function.prototype.call = function(context, ...args) {
	const fn = Symbol('fn')
	context[fn] = this
	const result = eval('context.fn(...args)')
	delete context[fn]
	return result
}
```

```js
Function.prototype.apply = function(context, args) {
	const fn = Symbol('fn')
	context[fn] = this
	const result = eval('context.fn(...args)')
	delete context[fn]
	return result
}

```

