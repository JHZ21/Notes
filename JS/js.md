# Js 对象



## js 禁止上下文菜单，复制



* [JS实现网站内容的禁止复制和粘贴、另存为](https://www.cnblogs.com/web100/p/js-enable-copy.html)

```js
document.oncontextmenu=function(evt){
  evt.preventDefault();
}

document.onselectstart=function(evt){
 evt.preventDefault();
};
```





## 链接

* [JavaScript 和 HTML DOM 参考手册 | RUNOOB](https://www.runoob.com/jsref/jsref-tutorial.html)
* [JavaScript 参考手册 | W3school](https://www.w3school.com.cn/jsref/index.asp)



## ?.

* [可选链操作符 | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/%E5%8F%AF%E9%80%89%E9%93%BE)
* 在引用为空 (null 或者 undefined) 的情况下不会引起错误，该表达式短路返回值是 `undefined`

```JS
const adventurer = {
  name: 'Alice',
  cat: {
    name: 'Dinah'
  }
};

const dogName = adventurer.dog?.name;
console.log(dogName);
// undefined
console.log(adventurer.dogList?.[0]);
// undefined
console.log(adventurer.someNonExistentMethod?.());
// undefined
```



## ?? 

> ?? 和 || 很像
>
> 只是屏蔽掉 null, undefined
>
> 不会屏蔽掉 false, 0, NaN, '' 
>
> * [js 中的 ?? 是什么？| 简书](https://www.jianshu.com/p/77b8c7311aa9)

```js
null || 1
// 1
null ?? 1
// 1
undefined || 1
// 1
undefined ?? 1
// 1
false || 1
// 1
false ?? 1
// false
0 || 1
// 1
0 ?? 1
// 0
```



## ~~

* [我所理解的JS ~~运算符](https://blog.csdn.net/weixin_37710888/article/details/82587296)

* 去小数部分

```js
// 1、数字类型的字符串可以转化为纯数字
var a='123';
console.log(~~a); //输出123
// 2、字符串中带了其他字母，符号，或者其他除数字外的东西，一律输出 Number类型的0
var a='asd';
console.log(~~a); //输出0
// 3、任何boolen类型的，如果为TRUE则输出1，FALSE输出0；
var a=1==1;
console.log(~~a);//输出1
// 4、特殊类型，转化为Boolean是true的输出1，转化为boolean是false的输出0；
var a=undefined;
console.log(~~a);//输出0
var b=！undefined;
console.log(~~b);//输出1
```





## setTimeout

* [setTimetou | ronoob](https://www.runoob.com/jsref/met-win-settimeout.html)

* 语法

  ```js
  setTimeout(code, milliseconds, param1, param2, ...)
  // code: 代码串
  ```

  ```js
  setTimeout(function, milliseconds, param1, param2, ...)
  ```

  * 返回一个 ID（数字），可以将这个ID传递给 `clearTimeout`(id) 来取消执行

  

## setInterval

* [setInterval | ronoob](https://www.runoob.com/jsref/met-win-setinterval.html)

* 语法

  ```js
  setInterval(code, milliseconds);
  ```

  ```js
  setInterval(function, milliseconds, param1, param2, ...)
  ```

  * 返回一个 ID（数字），可以将这个ID传递给 `clearInterval`(id) 来取消执行



### try catch finally 执行顺序

* [try-catch-finally 在JS中的执行顺序](https://blog.csdn.net/qq_39237801/article/details/101109221)

> finally 内容总会运行，即使try, catch 有return；
>
> return 以第一次 reuten 变量为准，普通变量，则return 不会改变，但引用变量的内容可能会被修改；



## 按位操作符



* [按位操作符 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators)

  * & (按位与)
  * | (按位或)
  * 去小数部分

     ```js
  1|0 // 1
  1.5|0 //1
  -1|0 // -1
  1.5|0 // -1
     ```

  

  * ^ (按位异或)
  * ~ (按位非)

* 按位移动操作符

  * << (左移)

  * \>> (有符号右移)

  * \>>> (无符号右移)

    



## 运算符优先级

> [运算符优先级 ](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)



## 数据类型

* 值类型与

- 7 种原始类型
  
  - Boolean
  
  - Null
  
  - Undefined
  
  - Number
  
  - BigInt
  
  - String
  
  - Symbol
  
    > [Symbol | MDN](https://www.baidu.com/link?url=-zp7kGvfZKfGDZSrV4YUCmg2Ir_-WaR8NXK62ZAUhu8AVwBD6DNKWjeR_ODS4siQdlM9K8kOZWQdLptzIBILFd1C04Hmk_minwxuobcBL9Pdy-skIrew_AScukimYQCYawcIK1SSZSWRQ7vHxpFOC_&wd=&eqid=8db7d91600018109000000055e9f2459)
    >
    >```js
    >Symbol("foo") === Symbol("foo"); // false
    >```
  
- 引用类型

- Object



## instance.constructor

> 利用实例的构造函数属性，创造新实例
>
> 下面例子清晰展示了，实例原型的constructor 指向 构造函数

```js
let date = new Date()
> Thu Mar 26 2020 22:00:17 GMT+0800 (中国标准时间)

let date0 = new date.constructor()
> Thu Mar 26 2020 22:01:28 GMT+0800 (中国标准时间)
```

## typeof

> 返回字符串，表示未经计算的操作数的类型
>
> [typeof](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/typeof)

| 类型                                                         | 结果                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Undefined](https://developer.mozilla.org/zh-CN/docs/Glossary/undefined) | `"undefined"`                                                |
| [Null](https://developer.mozilla.org/zh-CN/docs/Glossary/Null) | `"object"` (见[下文](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/typeof#null)) |
| [Boolean](https://developer.mozilla.org/zh-CN/docs/Glossary/Boolean) | `"boolean"`                                                  |
| [Number](https://developer.mozilla.org/zh-CN/docs/Glossary/Number) | `"number"`                                                   |
| [BigInt](https://developer.mozilla.org/zh-CN/docs/Glossary/BigInt) | `"bigint"`                                                   |
| [String](https://developer.mozilla.org/zh-CN/docs/Glossary/字符串) | `"string"`                                                   |
| [Symbol](https://developer.mozilla.org/zh-CN/docs/Glossary/Symbol) (ECMAScript 2015 新增) | `"symbol"`                                                   |
| 宿主对象（由 JS 环境提供）                                   | *取决于具体实现*                                             |
| [Function](https://developer.mozilla.org/zh-CN/docs/Glossary/Function) 对象 (按照 ECMA-262 规范实现 [[Call]]) | `"function"`                                                 |
| 其他任何对象                                                 | `"object"`                                                   |

> es2015之前  typeof 能返回 `'undefined', 不会抛出错误.
>
> 但加入了块级作用域的 [let](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let) 和 [const](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const) 之后,  对其未被声明的变量使用 typeof ,就会抛出一个 [ReferenceError](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError)， class 声明也一样，也会有 “[暂存死区](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let)” 。

#### typeof 例外

当前所有的浏览器都暴露了一个类型为 `undefined` 的非标准宿主对象 [`document.all`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/all)。

```
typeof document.all
> "undefined"
// 然而
document.all
> HTMLAllCollection(1894) [html, head, meta, meta, script, title, meta, meta, link, link, link, link, link, link, link, link, script, style, script, script, script, script, script, script, meta, meta, meta, meta, meta, meta, meta, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, link, meta, meta, meta, meta, meta, meta, meta, link, script, body, script, div#react-container, div.loading-bar, ul#nav-access, li, a#skip-main, li, a#skip-language, li, a#skip-search, header.page-header, a.logo, svg, path, nav.main-nav, ul, li.top-level-entry-container, button.top-level-entry, span.main-menu-arrow, ul, li, a, li, a, li, a, li, a, li, a, li, a, li, …]
```

>尽管规范允许为非标准的外来对象自定义类型标签，但它要求这些类型标签与已有的不同。`document.all` 的类型标签为 `'undefined'` 的例子在 Web 领域中被归类为对原 ECMA JavaScript 标准的“故意侵犯”。



## Reflect

*  =>  es6





## Object

> [Object | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)





### set get 访问器属性

* [JavaScript 对象中的 set 和 get](https://blog.csdn.net/qq_42941302/article/details/109516914)

```js
var obj = {
    _num = 0,
    set num(value){	//set 方法有且仅有一个参数，不适用retrun返回内容
        this._num = value;
    },
    get num(){	// get 方法不能有参数，且必须用return返回内容
        return this._num;
    }
}
```

* 非成对出现时
  * 只有 get , 表示该属性只可读，不可写
  * 只有 set , 表示该属性只可写，不可读



### Object 的方法 



### hasOwnProperty

> 判断指示对象自身属性中是否具有指定的属性,
>
> 不包括原型链上的

* [hasOwnProperty | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)

* 语法

```js
obj.hasOwnProperty(prop)
// Boolean: true | false
```

```js
const a = {
	b: 1
}
a.hasOwnProperty('b')
// true
```



### Object.create()

* [Object.create() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
* 语法

```js
/* obj = {
	__proto__: argObj
} */
Object.create(proto[, propertiesObject])
```



### Object.keys()

> 一个表示给定对象自身的所有可枚举属性的字符串数组。

* [Object.keys() |mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
* 语法

```js
Object.keys(obj)
```

* examples

```js
let obj ={ a:1, b:[2,3], 1:1}
Object.keys(obj)
// ["1", "a", "b"]
```



### Object.values()

> 一个包含对象自身的所有可枚举属性值的数组

* [Object.values() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/values)



* 语法

```
Object.values(obj)
```

* examples

```js
let obj ={ a:1, b:[2,3], 1:1}
Object.values(obj)
// [1, 1, [2,3]]
```



### Object.assign()

* [`Object.assign()| MDN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)

> Object.assgin() 拷贝的事对象的属性引用，而不是对象本身，第一位置对象参数，也是返回对象
>
> ```JS
> Object.assign(target, ...sources)
> ```



### Object.defineProperty()

* [Object.defineProperty()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

```js
Object.defineProperty(obj, prop:string, descriptor)
```

* 数据描述符  和 存取描述符， 只能取其中之一，不能同时是两者

  * 两者都可以配置属性

    - `configurable`

      默认false: 属性无法被删除delete

    - `enumerable`

      默认 `false`

  * 数据描述符独有

    - `value`

    - `writable`

      当且仅当该属性的 `writable` 键值为 `true` 时，属性的值，也就是上面的 `value`，才能被[`赋值运算符`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Assignment_Operators)改变。 默认为 `false`。

  * 存取描述符独有

    * `get`

      该函数的返回值会被用作属性的值。
      默认为 undefined。

    * `set`

      该方法接受一个参数（也就是被赋予的新值），会传入赋值时的 `this` 对象。
      默认为 undefined



### Object.defineProperties()

* [Object.defineProperties | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperties)

> ```js
> Object.defineProperties(obj, props:object)
> ```



### Object.freeze()

* [Object.freeze() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)

> 可以**冻结**一个对象。一个被冻结的对象再也不能被修改；冻结了一个对象则不能向这个对象添加新的属性，不能删除已有属性，不能修改该对象已有属性的可枚举性、可配置性、可写性，以及不能修改已有属性的值。此外，冻结一个对象后该对象的原型也不能被修改。`freeze()` 返回和传入的参数相同的对象。



### Object.seal()

* [Object.seal() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/seal)

> 封闭一个对象，阻止添加新属性并将所有现有属性标记为不可配置。当前属性的值只要原来是可写的就可以改变。



### Object.preventExtensions()

[Object.preventExtensions() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/preventExtensions)

> 让一个对象变的不可扩展，也就是永远不能再添加新的属性。



## Object 子类



### Promise

> Promise 对象用于表示一个异步操作的最终完成 (或失败), 及其结果值.

* 语法

```js
new Promise( function(resolve, reject) {...} /* executor */  );
```

- [Promise.all(iterable)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

  > 这个方法返回一个新的promise对象，该promise对象在iterable参数对象里所有的promise对象都成功的时候才会触发成功，一旦有任何一个iterable里面的promise对象失败则立即触发该promise对象的失败。这个新的promise对象在触发成功状态以后，会把一个包含iterable里所有promise返回值的数组作为成功回调的返回值，顺序跟iterable的顺序保持一致；如果这个新的promise对象触发了失败状态，它会把iterable里第一个触发失败的promise对象的错误信息作为它的失败错误信息。Promise.all方法常被用于处理多个promise对象的状态集合

- [Promise.allSettled(iterable)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled)

  >  等到所有promises都完成（每个promise返回成功或失败）。 返回一个promise，该promise在所有promise完成后完成。并带有一个对象数组，每个对象对应每个promise的结果。

- [`Promise.any(iterable)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/any)

  > 接收一个Promise对象的集合，当其中的一个promise 成功，就返回那个成功的promise的值。

- [Promise.race(iterable)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)

  > 当iterable参数里的任意一个子promise被成功或失败后，父promise马上也会用子promise的成功返回值或失败详情作为参数调用父promise绑定的相应句柄，并返回该promise对象。

- [Promise.reject(reason)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject)

  > 返回一个状态为失败的Promise对象，并将给定的失败信息传递给对应的处理方法

- [Promise.resolve(value)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)

  > 返回一个状态由给定value决定的Promise对象。如果该值是thenable(即，带有then方法的对象)，返回的Promise对象的最终状态由then方法执行决定；否则的话(该value为空，基本类型或者不带then方法的对象),返回的Promise对象状态为fulfilled，并且将该value传递给对应的then方法。通常而言，如果你不知道一个值是否是Promise对象，使用Promise.resolve(value) 来返回一个Promise对象,这样就能将该value以Promise对象形式使用。





### Function 

> [Function |mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function)

* 普通的函数也是object，可以设置属性（值，引用）

```
function a() {

}
a.func =(){}
a.v = 1
```



* [length](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/length)

  > 指明函数的形参个数

* 

* [apply()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

  ```js
  func.apply(thisArg, [argsArray])
  ```

* [bind()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)

  * 调用方法

  ```js
  function.bind(thisArg[, arg1[, arg2[, ...]]])
  // 输出 function： 原函数的拷贝，并指定了this和部分初始参数
  ```

* [call()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

  * 调用方法

  ```js
  function.call(thisArg, arg1, arg2, ...)
  ```

  

* 



### Proxy

* [Proxy | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
* 语法

```js
const p = new Proxy(target:object, handler:object)
```

```js
let products = new Proxy({
  browsers: ['Internet Explorer', 'Netscape']
}, {
  get: function(obj, prop) {
    // 附加一个属性
    if (prop === 'latestBrowser') {
      return obj.browsers[obj.browsers.length - 1];
    }

    // 默认行为是返回属性值
    return obj[prop];
  },
  set: function(obj, prop, value) {
    // 附加属性
    if (prop === 'latestBrowser') {
      obj.browsers.push(value);
      return;
    }

    // 如果不是数组，则进行转换
    if (typeof value === 'string') {
      value = [value];
    }

    // 默认行为是保存属性值
    obj[prop] = value;

    // 表示成功
    return true;
  }
});

console.log(products.browsers); // ['Internet Explorer', 'Netscape']
products.browsers = 'Firefox';  // 如果不小心传入了一个字符串
console.log(products.browsers); // ['Firefox'] <- 也没问题, 得到的依旧是一个数组

products.latestBrowser = 'Chrome';
console.log(products.browsers);      // ['Firefox', 'Chrome']
console.log(products.latestBrowser); // 'Chrome'
```

### Set

> **`Set`** 对象允许你存储任何类型的唯一值，无论是[原始值](https://developer.mozilla.org/zh-CN/docs/Glossary/Primitive)或者是对象引用。
>
> [Set](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)

* [Set.prototype.add(value)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set/add)
* [Set.prototype.delete(value)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set/delete)
* [Set.prototype.has(value)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set/has)

```js
set = new Set([1,2,3])
// Set(3) {1, 2, 3}
set.forEach(console.log) // (v,v,set)
// 1 1 Set(3) {1, 2, 3}
// 2 2 Set(3) {1, 2, 3}
// 3 3 Set(3) {1, 2, 3}
```



### Map

> **`Map`** 对象保存键值对，并且能够记住键的原始插入顺序。
>
> 任何值(对象或者[原始值](https://developer.mozilla.org/zh-CN/docs/Glossary/Primitive)) 都可以作为一个键或一个值。
>
> [Map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map)

* 储存在Map `键名`，`键值`的数据，会形成对数据对象的引用，一旦不再需要这两个对象，我们就必须手动删除这个引用，否则垃圾回收机制就不会释放对象占用的内存。
* [Map.prototype.get(key)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map/get)
* [Map.prototype.set(key, value)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map/set)
* [Map.prototype.delete(key)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map/delete)
* 

### WeakMap

* `键名`是弱引用，所有键必须是对象，而值可以是任意的,  所有`键值`，依然是正常引用

* WeakMap的`键名`所引用的对象因为弱引用，即垃圾回收机制不将该引用考虑在内,

  因此，只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存。

* 如果你要往对象上添加数据，又不想干扰垃圾回收机制，就可以使用 WeakMap

  > 一个典型应用场景是，在网页的 DOM 元素上添加数据，就可以使用WeakMap结构。当该 DOM 元素被清除，其所对应的WeakMap记录就会自动被移除。

  ```js
  const wm = new WeakMap();
  const element = document.getElementsByTagName("div")[0];
  wm.set(element,"some information");
  console.log(wm.get(element));
  ```

  



### Array

#### 好文

> [【深度长文】JavaScript数组所有API全解密](https://link.zhihu.com/?target=http%3A//louiszhai.github.io/2017/04/28/array/)

#### 赋值(奇特值)

> ```js
> arr = [,,]
> > [empty × 2]
> arr[0]
> > undefind
> arr.length
> > 2
> arr = [undefined,]
> > [undefined]
> arr[0]
> > undefined
> arr = [,undefined]
> > [empty, undefined]
> arr.length 
> > 2
> ```
>
> 总结 ：
>
> * 数组末尾无值，则舍弃
>* 非末尾位无值，显示empty,  get 值为undefined
> * 输入 undefined, null 也算有输入值
> * empty. undefined, null 值，也算入数组长度计算

#### 循环对 empty, undefined, null 等值的态度

```js
// arr 赋值
let arr = [0, false, NaN ,null, , undefined]
[ 0, false, NaN, null, empty, undefined ]

// for in 测试
for(let i in arr){console.log(i, arr[i])}
0 0
1 false     
2 NaN       
3 null      
5 undefined 
// forEach 测试
arr.forEach((v, i) => console.log(i, v))
0 0
1 false     
2 NaN       
3 null      
5 undefined 
// filter 测试
arr.filter((v,i) => {
	console.log(i, v)
	return v
})
0 0
1 false     
2 NaN       
3 null      
5 undefined 
[]
// for () 测试s
for(let i=0;i<arr.length ; i++){console.log(i, arr[i])}
0 0
1 false     
2 NaN       
3 null      
4 undefined 
5 undefined 
```

总结：

* for in ，forEach ，filter 都遍历null, undefined , false等值  但对empty ，则会跳过
* filter 可用于清除数组里 这些值
* for () 会按照我们的设置,  遍历完所有值

* [concat()](https://www.runoob.com/jsref/jsref-concat-array.html)

  > ```js
  > arrayObject.concat(arrayX,arrayX,......,arrayX)
  > ```
  >
  > ```js
  > var a = [1,2,3]
  > a.concat(4,5)
  > // 1,2,3,4,5
  > ```
  >
  > ```js
  > var arr = new Array(3)
  > arr[0] = "George"
  > arr[1] = "John"
  > arr[2] = "Thomas"
  > 
  > var arr2 = new Array(3)
  > arr2[0] = "James"
  > arr2[1] = "Adrew"
  > arr2[2] = "Martin"
  > 
  > arr.concat(arr2)
  > //George,John,Thomas,James,Adrew,Martin
  > ```

#### Array方法

* [concat()](https://www.baidu.com/link?url=55ymuQUeT1zvurVAa9b6wkD-SqyqkZlFBbNNJ8E10UtdM6uRhqtrmpejhahtv8wwQP7QOBNIM3UWnr-ryfsZZFIEFfrDci04DnhMaHLeIsq&wd=&eqid=8ec1c2630002091f000000055e8eb1e9)

  > ```js
  > arrayObject.concat(arrayX,arrayX,......,arrayX)
  > // arrayX 可以是具体的值，也可以是数组
  > // 返回值：一个新数组，包含arrayObject，arrayX的所有元素
  > // arrayObject,不被修改
  > ```
  >
  > ```js
  > let arr=[1]
  > 
  > arr.concat(1,[2,3])
  > //[1,1,2,3]
  > arr
  > //[1]
  > ```

* [copyWithin()](https://www.runoob.com/jsref/jsref-copywithin.html)

* [entries()](https://www.runoob.com/jsref/jsref-entries.html)

* [every() | MDN](https://www.baidu.com/link?url=aIUXOe-2MUwRZERieVWN3PSjYlCuejM8Us3qpiMKD_t1S32SD2vYPQrGWw7JvURIkPGaeicu20kLou-ODh99esRYijxKsUxbOCQHWfDy6wIi1jQ1rjI3tWoaBdWDiEn5QSf9wR9SW23RQ0SG_gU9z_&wd=&eqid=90f8f7f700004d69000000055ea5a3a6)

* [fill()](https://www.runoob.com/jsref/jsref-fill.html)

  ```js
  arr.every(callback[, thisArg])
  // callback:
  callback(element, index?, array?)
  // ele:遍历的当前值,index: 当前值的索引，array: 调用every的数组，即arr 
  // thisArg : 执行callback的this 值
  ```

  

* [filter()](https://www.runoob.com/jsref/jsref-filter.html)

* [find()](https://www.runoob.com/jsref/jsref-find.html)

* [flat() | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)

  ```js
  var newArray = arr.flat([depth]);
  ```

  * depth 默认值 1
  * examples

  ```js
  var arr1 = [1, 2, [3, 4]];
  arr1.flat(); 
  // [1, 2, 3, 4]
  
  var arr2 = [1, 2, [3, 4, [5, 6]]];
  arr2.flat();
  // [1, 2, 3, 4, [5, 6]]
  
  var arr3 = [1, 2, [3, 4, [5, 6]]];
  arr3.flat(2);
  // [1, 2, 3, 4, 5, 6]
  
  //使用 Infinity，可展开任意深度的嵌套数组
  var arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
  arr4.flat(Infinity);
  // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
  ```

  

* [findIndex()](https://www.runoob.com/jsref/jsref-findindex.html)

* [forEach()](https://www.runoob.com/jsref/jsref-foreach.html)

* [from()](https://www.runoob.com/jsref/jsref-from.html)

  * 调用

  ```js
  Array.from(object, mapFunction?, thisValue?)
  // object: 需要转换微数组的对象
  // mapFunction: 数组中每个元素要调用的函数
  // thisValue: mapFunction 中的 this 对象
  ```

  

* [includes()](https://www.runoob.com/jsref/jsref-includes.html)

* [indexOf()](https://www.runoob.com/jsref/jsref-indexof-array.html)

* [isArray()](https://www.runoob.com/jsref/jsref-isarray.html)

* [join()](https://www.runoob.com/jsref/jsref-join.html)

* [keys()](https://www.runoob.com/jsref/jsref-keys.html)

```js
array.keys()
```

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var keys = fruits.keys();
// Array Iterator {}
keys.next()
// {value: 0, done: false}
keys.next()
// {value: 1, done: false}
... ...
```



* [lastIndexOf()](https://www.runoob.com/jsref/jsref-lastindexof-array.html)

* [map()](https://www.runoob.com/jsref/jsref-map.html)

* [pop()](https://www.runoob.com/jsref/jsref-pop.html)

* [push()](https://www.runoob.com/jsref/jsref-push.html)

  * 语法

    ```js
    array.push(item1, item2, ..., itemX)
    // 新数组长度 
    ```

    

* [reduce()](https://www.runoob.com/jsref/jsref-reduce.html)

  > 从左往右

  * 语法

    ```js
    array.reduce(function(total, currentValue, currentIndex, arr), initialValue)
    ```

    * 返回计算结果
    * Example

    ```js
    [1,2,3,4].reduce((a,b) => a+b)
    // 10
    ```

    

* [reduceRight()](https://www.runoob.com/jsref/jsref-reduceright.html)

* [reverse()](https://www.runoob.com/jsref/jsref-reverse.html)

* [shift()](https://www.runoob.com/jsref/jsref-shift.html)

  > ```js
  > array.shift()
  > //返回值： 数组原来的第一个元素的值（移除的元素）
  > ```

* [unshift | w3school](https://www.baidu.com/link?url=AV1osNNZbQ0Zw1cX9uCn6Evnv97vTUzbENdzqngde_IUfpdGe7Hp460ZWWYeLKESM-791t0K1T83G7R3T-5X7a&wd=&eqid=a9bd95c400001cb4000000055e8df593)

  > ```js
  > arrayObject.unshift(newelement1,newelement2,....,newelementX)
  > //返回值： arrayObject 的新长度。
  > ```

* [slice()](https://www.runoob.com/jsref/jsref-slice-array.html)

  > `array.slice(?start, ?end)`
  >
  > 不修改原数组，浅复制出新数组

* [some()](https://www.runoob.com/jsref/jsref-some.html)

* [sort()](https://www.runoob.com/jsref/jsref-sort.html)

```js
array.sort(sortfunction)
```

>  这种方法会改变原始数组！

* [splice()](https://www.runoob.com/jsref/jsref-splice.html)

  ```js
  array.splice(index,howmany,item1,.....,itemX)
  // 返回删除的项所组成的数组， [delete1,..,,deleteX]
  ```

  * itemX 插入 index 的前面

  

* [toString()](https://www.runoob.com/jsref/jsref-tostring-array.html)

* [unshift()](https://www.runoob.com/jsref/jsref-unshift.html)

* [valueOf()](https://www.runoob.com/jsref/jsref-valueof-array.html)

* [map](https://www.runoob.com/jsref/jsref-map.html)

```js
array.map(function(currentValue,index,arr), thisValue)
// thisValue:  可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。如果省略了 thisValue，或者传入 null、undefined，那么回调函数的 this 为全局对象。
```





## Boolean

* [toString()](https://www.w3school.com.cn/jsref/jsref_toString_boolean.asp)

* [valueOf()](https://www.w3school.com.cn/jsref/jsref_valueOf_boolean.asp)



## Date()

> [Date](https://www.w3school.com.cn/jsref/jsref_obj_date.asp)

* Date.now()

> 返回当前时间戳 ( number)

```js
d = new Date("1970-1-2") // 参数字符串
d.getTime()	// 57600000
getFullYear()	从 Date 对象以四位数字返回年份。
getMonth()	从 Date 对象返回月份 (0 ~ 11)。
getDate()	从 Date 对象返回一个月中的某一天 (1 ~ 31)。
getDay()	从 Date 对象返回一周中的某一天 (0 ~ 6)。
getHours()	返回 Date 对象的小时 (0 ~ 23)。
getMinutes()	返回 Date 对象的分钟 (0 ~ 59)。
getSeconds()	返回 Date 对象的秒数 (0 ~ 59)。
getTime()	返回 1970 年 1 月 1 日至今的毫秒数。
getTimezoneOffset()	返回本地时间与格林威治标准时间 (GMT) 的分钟差。
```



## Math

> [JavaScript Math 对象](https://www.w3school.com.cn/jsref/jsref_obj_math.asp)



* [max(x,y)](https://www.w3school.com.cn/jsref/jsref_max.asp)

  * 实例

    ```js
    Math.max() // -Infinity
    ```

* [min(x,y)](https://www.w3school.com.cn/jsref/jsref_min.asp)

  * 实例

    ```js
    Math.min() // Infinity
    ```

* [abs(x)](https://www.w3school.com.cn/jsref/jsref_abs.asp)

* [max() | MDN](https://www.baidu.com/link?url=sZKKlyKPnexT36IhZjI0n0EFYV2As_Y0If2sd9SMA6mczAcX7uXGZElzeZVgQlvE5HMfm70AIcmRyPuv70f5LfzCSUswIphQCzhej_ZdN2vj3TT7VtM0u4cPh5LL87oK_TMrmYNp6LjXLXM4C1nuDK&wd=&eqid=cfa9c7d3000118c0000000055ea6f9b2)

  > ```js
  > Math.max(value1[,value2, ...]) 
  > ```
  >
  > 



### Math.random()

>



### Math.ceil()

> 靠右(大) 取整

```javascript
Math.ceil(12.1)
> 13
Math.ceil(12.0)
> 12
Math.ceil(-12.2)
> -12
```



### Math.round()

> 四舍五入，舍靠0，正入正，负如负

```js
Math.round(0.5)
> 1
Math.round(0.4)
> 0
Math.round(0.4999)
0
Math.round(-0.001)
-0
Math.round(-0.5)
-0
Math.round(-0.6)
-1
```



### Math.floor() 

>  靠左(小) 取整

```js
Math.floor(0.3)
> 0
Math.floor(-0.3)
> -1
Math.floor(-0.000001)
> -1
```





## Number



* [parsetInt](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseInt)

  > js内置方法

  * 调用

    ```js
    parseInt(string, radix?);
    //string: 被解析的值
    //radix: 从 2 到 36，代表该进位系统的数字
    ```



### Number.toFixed()

> 可把 Number 四舍五入为指定小数位数的数字

* [Number.prototype.toFixed() | smdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed)

* 语法

```js
numObj.toFixed(digits)
```





### Number.isInteger()

> 在js的浮点数规则里，值与整数相等就行

```js
Number.isInteger("1")
> false
Number.isInteger(1111.)
> true
Number.isInteger(1111.0)
> true
Number.isInteger(1111.1)
> false
Number.isInteger(1111.00000000000000000000000000000000000000000000000000000000000000001)
> true
Number.isInteger(1111.00000000001)
> false
Number.isInteger(-1)
true
Number.isInteger(Infinity)
> false
Number.isInteger(NaN)
> false
```



## String

#### 好文

* [JS String](https://www.w3school.com.cn/jsref/jsref_obj_string.asp)
* [JavaScript字符串所有API全解密](https://link.zhihu.com/?target=http%3A//louiszhai.github.io/2016/01/12/js.String/)

### 不可见字符

* \u200b

#### String方法

* [anchor()](https://www.w3school.com.cn/jsref/jsref_anchor.asp)
* [charAt()](https://www.w3school.com.cn/jsref/jsref_charAt.asp)

> charAt() 方法可返回指定位置的字符

```js
stringObject.charAt(index)
```



* [charCodeAt()](https://www.w3school.com.cn/jsref/jsref_charCodeAt.asp)

* [concat()](https://www.w3school.com.cn/jsref/jsref_concat_string.asp)

  ```js
  stringObject.concat(stringX,stringX,...,stringX)
  ```

* [fromCharCode()](https://www.w3school.com.cn/jsref/jsref_fromCharCode.asp)

* [indexOf()](https://www.w3school.com.cn/jsref/jsref_indexOf.asp)

  > ```js
  > stringObject.indexOf(searchvalue,fromindex)
  > ```

* [lastIndexOf()](https://www.w3school.com.cn/jsref/jsref_lastIndexOf.asp)

* [match()](https://www.w3school.com.cn/jsref/jsref_match.asp)

  > [match() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/match)

* [replace()](https://www.w3school.com.cn/jsref/jsref_replace.asp)

  * 语法

  ```js
  stringObject.replace(regexp/substr,replacement)
  ```

  * replacement

  | 字符             | 替换文本                                            |
  | :--------------- | :-------------------------------------------------- |
  | $1、$2、...、$99 | 与 regexp 中的第 1 到第 99 个子表达式相匹配的文本。 |
  | $&               | 与 regexp 相匹配的子串。                            |
  | $`               | 位于匹配子串左侧的文本。                            |
  | $'               | 位于匹配子串右侧的文本。                            |
  | $$               | 直接量符号。                                        |

* [search()](https://www.w3school.com.cn/jsref/jsref_search.asp)

* [slice()](https://www.w3school.com.cn/jsref/jsref_slice_string.asp)

  > string 没有splice()
  >
  > ```js
  > stringObject.slice(start,end)
  > start,end 可负
  > ```
  >
  > 

* [small()](https://www.w3school.com.cn/jsref/jsref_small.asp)

* [split()](https://www.w3school.com.cn/jsref/jsref_split.asp)

* [substr()](https://www.w3school.com.cn/jsref/jsref_substr.asp)

  > ```js
  > stringObject.substr(start,length)
  > ```

* [substring()](https://www.w3school.com.cn/jsref/jsref_substring.asp)

  > ```js
  > stringObject.substring(start,stop = str.length)
  > start,stop 非负， 
  > 为负：则值为0，从大小顺序颠倒也无妨
  > ```

* [trim()  | 菜鸟教程](https://www.baidu.com/link?url=16cr_Kynk7pK4RtwcdOCYyLhVS_j2fodIky8MRPA1HGcXV7bsySJ5zfiaRy4cXGhK3EEfPn0QkRcqSsBA2E-2_&wd=&eqid=84478eb3000009cc000000055e9f1940)

  > 用于删除字符串的头尾空格。
  >
  > 不会改变原始字符串。

* [toLocaleLowerCase()](https://www.w3school.com.cn/jsref/jsref_toLocaleLowerCase.asp)

* [toLocaleUpperCase()](https://www.w3school.com.cn/jsref/jsref_toLocaleUpperCase.asp)

* [toLowerCase()](https://www.w3school.com.cn/jsref/jsref_toLowerCase.asp)

* [toUpperCase()](https://www.w3school.com.cn/jsref/jsref_toUpperCase.asp)

* [toString()](https://www.w3school.com.cn/jsref/jsref_toString_string.asp)

* [valueOf()](https://www.w3school.com.cn/jsref/jsref_valueOf_string.asp)

* 





## RegExp

* [compile](https://www.w3school.com.cn/jsref/jsref_regexp_compile.asp)

* [exec](https://www.w3school.com.cn/jsref/jsref_exec_regexp.asp)

  * 语法

  ```js
  RegExpObject.exec(string)
  ```

  * return value

  > 未匹配到：null
  >
  > 匹配到： 数组 arr
  >
  > arr = [ 
  >
  > "与正则表达式相匹配的文本", 
  >
  > "与 reg 第 1 个子表达式相匹配的文本(最后一个匹配到的)（如果有的话)",
  >
  > ... ... 
  >
  > "与 reg 第 n 个子表达式相匹配的文本(最后一个匹配到的)（如果有的话)",
  >
  > ]
  >
  > arr.index:  匹配文本的第一个字符的位置,
  >
  > arr.input:  被检索的字符串 string,

  * 全局 (g) 正则表达式时  (并作为变量，被复用)

  > 若匹配后，RegExpObject 的 lastIndex 属性设置为匹配文本的最后一个字符的下一个位置
  >
  > 当 exec() 再也找不到匹配的文本时，它将返回 null，并把 lastIndex 属性重置为 0

  * examples

  ```js
  /(\d)/.exec('12aw')
  // ["1", "1", index: 0, input: "12aw", groups: undefined]
  
  reg = new RegExp(/(\d)/,'g')
  reg.exec("12as12")
  // ["1", "1", index: 0, input: "12as12", groups: undefined]
  reg.exec("12as12")
  // ["2", "2", index: 1, input: "12as12", groups: undefined]
  ... ...
  reg.exec("12as12")
  null
  reg.exec("12as12")
  // ["1", "1", index: 0, input: "12as12", groups: undefined]
  ... ...
  ```

  



* [test](https://www.w3school.com.cn/jsref/jsref_test_regexp.asp)



## Functions

* [parseFloat()](https://www.w3school.com.cn/jsref/jsref_parseFloat.asp)
* [parseInt()](https://www.w3school.com.cn/jsref/jsref_parseInt.asp)
* [escape()](https://www.w3school.com.cn/jsref/jsref_escape.asp)
* [unescape()](https://www.w3school.com.cn/jsref/jsref_unescape.asp)
* [eval()](https://www.w3school.com.cn/jsref/jsref_eval.asp)



## Evetns

> [JS Events](https://www.w3school.com.cn/jsref/jsref_events.asp)



stopPropagration 

> 阻止事件的冒泡



preventDefault

> 阻止默认事件的方法



# BOM 对象



## Window

>Window 对象表示浏览器中打开的窗口。
>
>[Window](https://www.w3school.com.cn/jsref/dom_obj_window.asp)

* onload 

> 全部加载完后才执行

* DOMContentLoaded

> 当dom加载玩就执行,不等待所有内容加载完

* Window 对象集合

| 集合     | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| frames[] | 返回窗口中所有命名的框架。该集合是 Window 对象的数组，每个 Window 对象在窗口中含有一个框架或 <iframe>。属性 frames.length 存放数组 frames[] 中含有的元素个数。注意，frames[] 数组中引用的框架可能还包括框架，它们自己也具有 frames[] 数组。 |

* Window 对象属性

| 属性                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [closed](https://www.w3school.com.cn/jsref/prop_win_closed.asp) | 返回窗口是否已被关闭。                                       |
| [defaultStatus](https://www.w3school.com.cn/jsref/prop_win_defaultstatus.asp) | 设置或返回窗口状态栏中的默认文本。                           |
| [document](https://www.w3school.com.cn/jsref/dom_obj_document.asp) | 对 Document 对象的只读引用。请参阅 [Document 对象](https://www.w3school.com.cn/jsref/dom_obj_document.asp)。 |
| [history](https://www.w3school.com.cn/jsref/dom_obj_history.asp) | 对 History 对象的只读引用。请参数 [History 对象](https://www.w3school.com.cn/jsref/dom_obj_history.asp)。 |
| [innerheight](https://www.w3school.com.cn/jsref/prop_win_innerheight_innerwidth.asp) | 返回窗口的文档显示区的高度。                                 |
| [innerwidth](https://www.w3school.com.cn/jsref/prop_win_innerheight_innerwidth.asp) | 返回窗口的文档显示区的宽度。                                 |
| length                                                       | 设置或返回窗口中的框架数量。                                 |
| [location](https://www.w3school.com.cn/jsref/dom_obj_location.asp) | 用于窗口或框架的 Location 对象。请参阅 [Location 对象](https://www.w3school.com.cn/jsref/dom_obj_location.asp)。 |
| [name](https://www.w3school.com.cn/jsref/prop_win_name.asp)  | 设置或返回窗口的名称。                                       |
| [Navigator](https://www.w3school.com.cn/jsref/dom_obj_navigator.asp) | 对 Navigator 对象的只读引用。请参数 [Navigator 对象](https://www.w3school.com.cn/jsref/dom_obj_navigator.asp)。 |
| [opener](https://www.w3school.com.cn/jsref/prop_win_opener.asp) | 返回对创建此窗口的窗口的引用。                               |
| [outerheight](https://www.w3school.com.cn/jsref/prop_win_outerheight.asp) | 返回窗口的外部高度。                                         |
| [outerwidth](https://www.w3school.com.cn/jsref/prop_win_outerwidth.asp) | 返回窗口的外部宽度。                                         |
| pageXOffset                                                  | 设置或返回当前页面相对于窗口显示区左上角的 X 位置。          |
| pageYOffset                                                  | 设置或返回当前页面相对于窗口显示区左上角的 Y 位置。          |
| parent                                                       | 返回父窗口。                                                 |
| [Screen](https://www.w3school.com.cn/jsref/dom_obj_screen.asp) | 对 Screen 对象的只读引用。请参数 [Screen 对象](https://www.w3school.com.cn/jsref/dom_obj_screen.asp)。 |
| [self](https://www.w3school.com.cn/jsref/prop_win_self.asp)  | 返回对当前窗口的引用。等价于 Window 属性。                   |
| [status](https://www.w3school.com.cn/jsref/prop_win_status.asp) | 设置窗口状态栏的文本。                                       |
| [top](https://www.w3school.com.cn/jsref/prop_win_top.asp)    | 返回最顶层的先辈窗口。                                       |
| window                                                       | window 属性等价于 self 属性，它包含了对窗口自身的引用。      |
| screenLeftscreenTopscreenXscreenY                            | 只读整数。声明了窗口的左上角在屏幕上的的 x 坐标和 y 坐标。IE、Safari 和 Opera 支持 screenLeft |

* Window 对象方法

| 方法                                                         | 描述                                               |
| :----------------------------------------------------------- | :------------------------------------------------- |
| [alert()](https://www.w3school.com.cn/jsref/met_win_alert.asp) | 显示带有一段消息和一个确认按钮的警告框。           |
| [blur()](https://www.w3school.com.cn/jsref/met_win_blur.asp) | 把键盘焦点从顶层窗口移开。                         |
| [clearInterval()](https://www.w3school.com.cn/jsref/met_win_clearinterval.asp) | 取消由 setInterval() 设置的 timeout。              |
| [clearTimeout()](https://www.w3school.com.cn/jsref/met_win_cleartimeout.asp) | 取消由 setTimeout() 方法设置的 timeout。           |
| [close()](https://www.w3school.com.cn/jsref/met_win_close.asp) | 关闭浏览器窗口。                                   |
| [confirm()](https://www.w3school.com.cn/jsref/met_win_confirm.asp) | 显示带有一段消息以及确认按钮和取消按钮的对话框。   |
| [createPopup()](https://www.w3school.com.cn/jsref/met_win_createpopup.asp) | 创建一个 pop-up 窗口。                             |
| [focus()](https://www.w3school.com.cn/jsref/met_win_focus.asp) | 把键盘焦点给予一个窗口。                           |
| [moveBy()](https://www.w3school.com.cn/jsref/met_win_moveby.asp) | 可相对窗口的当前坐标把它移动指定的像素。           |
| [moveTo()](https://www.w3school.com.cn/jsref/met_win_moveto.asp) | 把窗口的左上角移动到一个指定的坐标。               |
| [open()](https://www.w3school.com.cn/jsref/met_win_open.asp) | 打开一个新的浏览器窗口或查找一个已命名的窗口。     |
| [print()](https://www.w3school.com.cn/jsref/met_win_print.asp) | 打印当前窗口的内容。                               |
| [prompt()](https://www.w3school.com.cn/jsref/met_win_prompt.asp) | 显示可提示用户输入的对话框。                       |
| [resizeBy()](https://www.w3school.com.cn/jsref/met_win_resizeby.asp) | 按照指定的像素调整窗口的大小。                     |
| [resizeTo()](https://www.w3school.com.cn/jsref/met_win_resizeto.asp) | 把窗口的大小调整到指定的宽度和高度。               |
| [scrollBy()](https://www.w3school.com.cn/jsref/met_win_scrollby.asp) | 按照指定的像素值来滚动内容。                       |
| [scrollTo()](https://www.w3school.com.cn/jsref/met_win_scrollto.asp) | 把内容滚动到指定的坐标。                           |
| [setInterval()](https://www.w3school.com.cn/jsref/met_win_setinterval.asp) | 按照指定的周期（以毫秒计）来调用函数或计算表达式。 |
| [setTimeout()](https://www.w3school.com.cn/jsref/met_win_settimeout.asp) | 在指定的毫秒数后调用函数或计算表达式。             |



* [window.resizeTo() | 菜鸟教程](https://www.baidu.com/link?url=sRj61R886D0OJJYagZSKWcegxkKsmKPuZ7xR1mfxqvlU_D006m1QeVcjSTxELGvPPvOJyda4bcPJMO66TmZ_ja&wd=&eqid=eeda6e720000f427000000055e9d48ab)

  * *window*.resizeTo(*width,height*)

  * 不能设置那些不是通过 window.open 创建的窗口或 Tab 的大小。

    当一个窗口里面含有一个以上的 Tab 时，无法设置窗口的大小。

    

### requestAnimationFrame

> [window.requestAnimationFrame](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/requestAnimationFrame)
>
> 在浏览器在下次重绘之前调用指定的回调函数



### 原生弹框

* alert() 警告框

  ```javascript
  alert("message") // 用户只选确认, 返回 undefined
  ```

* confirm() 确认框

  ```javascript
  let is_confirm:boolean = confirm("message")
  // is_confirm：用户选择取消还是确认
  ```

* prompt() 提示框

  ```javascript
  let input_val: string || null = prompt()
   // input_val: 用户选确认,则返回输入的值
   //			   用户选取消，则返回 null
  ```

  



## Navigator 

> 表示用户代理的状态和标识。 它允许脚本查询它和注册自己进行一些活动。

* [navigator | mdn](https://developer.mozilla.org/zh-CN/docs/Web/API/Navigator)



## Screen

> 表示一个屏幕窗口，往往指的是当前正在被渲染的window对象，可以使用 `window.screen` 获取它。

* [screnn | mdn](https://developer.mozilla.org/zh-CN/docs/Web/API/Screen)



## History

* [history |mdn](https://developer.mozilla.org/zh-CN/docs/Web/API/History)

  * [`History.length`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/length)
  * [`History.state`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/state)
  * [`History.scrollRestoration`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/scrollRestoration)

  

* ```js
  window.history.forward()
  ```

* ```js
  window.history.forward()
  ```

* ```js
  window.history.go(-1) // = back()
  window.history.go(1) // = forward()
  ```

### hash 模式

* ```js
  location.state // 获得hash
  ```

* ```js
  history.pushState(状态对象, 标题 (目前被忽略),一个URL(可选的))
  ```

* ```js
  history.replaceState(状态对象, 标题 (目前被忽略),一个URL(可选的))
  ```

* 



## Location

* [*Location*  | *MDN*](https://developer.mozilla.org/zh-CN/docs/Web/API/Location)

| 属性                                                         | 描述                                          |
| :----------------------------------------------------------- | :-------------------------------------------- |
| [hash](https://www.w3school.com.cn/jsref/prop_loc_hash.asp)  | 设置或返回从井号 (#) 开始的 URL（锚）。       |
| [host](https://www.w3school.com.cn/jsref/prop_loc_host.asp)  | 设置或返回主机名和当前 URL 的端口号。         |
| [hostname](https://www.w3school.com.cn/jsref/prop_loc_hostname.asp) | 设置或返回当前 URL 的主机名。                 |
| [href](https://www.w3school.com.cn/jsref/prop_loc_href.asp)  | 设置或返回完整的 URL。                        |
| [pathname](https://www.w3school.com.cn/jsref/prop_loc_pathname.asp) | 设置或返回当前 URL 的路径部分。               |
| [port](https://www.w3school.com.cn/jsref/prop_loc_port.asp)  | 设置或返回当前 URL 的端口号。                 |
| [protocol](https://www.w3school.com.cn/jsref/prop_loc_protocol.asp) | 设置或返回当前 URL 的协议。                   |
| [search](https://www.w3school.com.cn/jsref/prop_loc_search.asp) | 设置或返回从问号 (?) 开始的 URL（查询部分）。 |



| 方法                                                         | 描述                     |
| :----------------------------------------------------------- | :----------------------- |
| [assign()](https://www.w3school.com.cn/jsref/met_loc_assign.asp) | 加载新的文档。           |
| [reload()](https://www.w3school.com.cn/jsref/met_loc_reload.asp) | 重新加载当前文档。       |
| [replace()](https://www.w3school.com.cn/jsref/met_loc_replace.asp) | 用新的文档替换当前文档。 |



# DOM 对象



## Document

>每个载入浏览器的 HTML 文档都会成为 Document 对象。
>
>Document 对象使我们可以从脚本中对 HTML 页面中的所有元素进行访问。
>
>**提示：**Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。
>
>[DOM Document | W3school](https://www.w3school.com.cn/jsref/dom_obj_document.asp)



## Element

>在 HTML DOM 中，Element 对象表示 HTML 元素。
>
>Element 对象可以拥有类型为元素节点、文本节点、注释节点的子节点。
>
>NodeList 对象表示节点列表，比如 HTML 元素的子节点集合。
>
>[DOM Element](https://www.w3school.com.cn/jsref/dom_obj_all.asp)
>
>元素也可以拥有属性。属性是属性节点（参见下一节）。





### addEventListener

> [addEventListener | runoob](https://www.runoob.com/jsref/met-element-addeventlistener.html)

* 语法

```js
element.addEventListener(event, function, useCapture = false)
```

* 参数
  * event  事件名
  * function 
  * useCapture, true: 在捕获阶段执行， false: 在冒泡阶段执行
  
  

### removeEventListener

> removeEventListener() 方法用于移除由 addEventListener()方法添加的事件句柄。

* [removeEventListener](https://www.runoob.com/jsref/met-element-removeeventlistener.html)

* **注意：** 如果要移除事件句柄，addEventListener() 的执行函数必须使用**外部函数**，如下实例所示 (myFunction)。

  匿名函数，类似 "document.removeEventListener("*event*", function(){ *myScript* });" 该事件是无法移除的。

```js
// 向 <div> 元素添加事件句柄
document.getElementById("myDIV").addEventListener("mousemove", myFunction);

// 移除 <div> 元素的事件句柄
document.getElementById("myDIV").removeEventListener("mousemove", myFunction);
```



* 语法

```js
element.removeEventListener(event, function, useCapture)
```

| parameter  | description                                                  |
| ---------- | ------------------------------------------------------------ |
| useCapture | 可选。布尔值，指定移除事件句柄的阶段。  可能值：true - 在捕获阶段移除事件句柄; false- 默认。在冒泡阶段移除事件句柄 。 **注意:** 如果添加两次事件句柄，一次在捕获阶段，一次在冒泡阶段，你必须单独移除该事件。 |



### appendChild()

> [Node.appendChild() | mdn](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)

* 移动性（从原来父节点那剪切）



### insertBefore()

> [HTML DOM insertBefore | 菜鸟教程](https://www.baidu.com/link?url=eD4WRl0pALO_35KnqANfUKg9Kf1HeG0qJ5yQPv21Q8dE3OjDj33SC_n9Gd4_KMCjnK1i3SMGPFyQDOAlPyAFooqNYNxONkapZO_lycyN64u&wd=&eqid=fc9be1140004ba56000000055e9dbb5b)
>
> ```
> node.insertBefore(newnode,existingnode)
> ```



### nextSibling

> [HTML DOM nextSibling 属性 | 菜鸟教程](https://www.baidu.com/link?url=CKjs8uGOu7pos9kj05iXvLdhKNgOt9mdOdamPeo8J0GdBWaeosn2ftaRm2KHcliPlLZ_YECVwAR5swgrjorECB6H2na2pLP4AXDpR3q1mB3&wd=&eqid=bf18789b0004253c000000055e9dbd1f)
>
> ```js
> node.nextSibling
> ```
>
> nextSibling 属性可返回某个元素之后紧跟的节点（处于同一树层级中）。
>
> 返回节点以节点对象返回。
>
> **注意：** 如果元素紧跟后面没有节点则返回 *null*.



### nodeType

> 只读,  表示的是该节点的类型。
>
> [Node.nodeType](https://developer.mozilla.org/zh-CN/docs/Web/API/Node/nodeType)

| 常量                 | 值   | 描述                                                         |
| :------------------- | :--- | :----------------------------------------------------------- |
| `Node.ELEMENT_NODE`  | `1`  | 一个 [`元素`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 节点，例如 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 和 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div)。 |
| `Node.TEXT_NODE`     | `3`  | [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 或者 [`Attr`](https://developer.mozilla.org/zh-CN/docs/Web/API/Attr) 中实际的 [`文字`](https://developer.mozilla.org/zh-CN/docs/Web/API/Text) |
| `Node.COMMENT_NODE`  | `8`  | 一个 [`Comment`](https://developer.mozilla.org/zh-CN/docs/Web/API/Comment) 节点。 |
| `Node.DOCUMENT_NODE` | `9`  | 一个 [`Document`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document) 节点。 |
| ... ...              |      |                                                              |



### cloneNode()

```js
var dupNode = node.cloneNode(deep)
deep: 默认false
true: 后代节点也会被克隆
false: 只克隆本节点，舍弃后代节点
```



### getBoundingClientRect()

> 方法返回元素的大小及其相对于**视口**的位置。
>
> [Element.getBoundingClientRect() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/getBoundingClientRect)

* 语法

```js
rectObject = object.getBoundingClientRect();
```

```js
var boxPosition = document.getElementById('box');     // 获取元素
const top = box.getBoundingClientRect().top;     // 元素上边距离页面上边的距离
const right = box.getBoundingClientRect().right;    // 元素右边距离页面左边的距离
```



## Attribute

>所有 HTML 属性是属性节点
>
>在 HTML DOM 中，*Attr* 对象表示 HTML 属性。
>
>HTML 属性始终属于 HTML 元素。
>
>在 DOM 4 中，Attr 对象不再从 Node 继承。
>
>[DOM Attribute](https://www.w3school.com.cn/jsref/dom_obj_attributes.asp)



## Event

>Event 对象代表事件的状态，比如事件在其中发生的元素、键盘按键的状态、鼠标的位置、鼠标按钮的状态。
>
>事件通常与函数结合使用，函数不会在事件发生前被执行！
>
>[DOM Event | W3school](https://www.w3school.com.cn/jsref/dom_obj_event.asp)

### 标准 Event 属性

下面列出了 2 级 DOM 事件标准定义的属性。

| 属性                                                         | 描述                                           |
| :----------------------------------------------------------- | :--------------------------------------------- |
| [bubbles](https://www.w3school.com.cn/jsref/event_bubbles.asp) | 返回布尔值，指示事件是否是起泡事件类型。       |
| [cancelable](https://www.w3school.com.cn/jsref/event_cancelable.asp) | 返回布尔值，指示事件是否可拥可取消的默认动作。 |
| [currentTarget](https://www.w3school.com.cn/jsref/event_currenttarget.asp) | 返回其事件监听器触发该事件的元素。             |
| [eventPhase](https://www.w3school.com.cn/jsref/event_eventphase.asp) | 返回事件传播的当前阶段。                       |
| [target](https://www.w3school.com.cn/jsref/event_target.asp) | 返回触发此事件的元素（事件的目标节点）。       |
| [timeStamp](https://www.w3school.com.cn/jsref/event_timestamp.asp) | 返回事件生成的日期和时间。                     |
| [type](https://www.w3school.com.cn/jsref/event_type.asp)     | 返回当前 Event 对象表示的事件的名称。          |

### 标准 Event 方法

下面列出了 2 级 DOM 事件标准定义的方法。IE 的事件模型不支持这些方法：

| 方法                                                         | 描述                                     |
| :----------------------------------------------------------- | :--------------------------------------- |
| [initEvent()](https://www.w3school.com.cn/jsref/event_initevent.asp) | 初始化新创建的 Event 对象的属性。        |
| [preventDefault()](https://www.w3school.com.cn/jsref/event_preventdefault.asp) | 通知浏览器不要执行与事件关联的默认动作。 |
| [stopPropagation()](https://www.w3school.com.cn/jsref/event_stoppropagation.asp) | 不再派发事件。                           |



### MouseEvent

####  Click

* [click | mdn](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/click_event)

#### click / keyboard属性

| 属性                 | 类型                                                         | 描述                                                         |
| :------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| `target` 只读        | [`EventTarget`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget) | 事件对象 (位于DOM树最上面的元素).                            |
| `type` 只读          | [`DOMString`](https://developer.mozilla.org/en-US/docs/Web/API/DOMString) | 事件类型.                                                    |
| `bubbles` 只读       | [`Boolean`](https://developer.mozilla.org/en-US/docs/Web/API/Boolean) | 是否冒泡                                                     |
| `cancelable` 只读    | [`Boolean`](https://developer.mozilla.org/en-US/docs/Web/API/Boolean) | 是否可被取消                                                 |
| `view` 只读          | [`WindowProxy`](https://developer.mozilla.org/en-US/docs/Web/API/WindowProxy) | [`document.defaultView`](https://developer.mozilla.org/en-US/docs/Web/API/Document/defaultView) (该文档的`window` 对象) |
| `detail` 只读        | `long` (`float`)                                             | 在短时间内发生的连续点击次数的计数。                         |
| `currentTarget` 只读 | EventTarget                                                  | 被事件监听触发的节点.                                        |
| `relatedTarget` 只读 | EventTarget                                                  | 对于 `mouseover`, `mouseout`, `mouseenter` 和`mouseleave` 事件: 值为与其互补的事件(比如`mouseenter` 就为`mouseleave`). 否则为`null`. |
| `screenX` 只读       | long                                                         | 点击事件发生时鼠标对应的屏幕x轴坐标.                         |
| `screenY` 只读       | long                                                         | 点击事件发生时鼠标对应的屏幕y轴坐标.                         |
| `clientX` 只读       | long                                                         | 点击事件发生时鼠标对应的浏览器窗口的x轴坐标.                 |
| `clientY` 只读       | long                                                         | 点击事件发生时鼠标对应的浏览器窗口的y轴坐标.                 |
| `button` 只读        | unsigned short                                               | 点击时按下的鼠标按钮: 左键=0, 中间按钮=1 (如果实现的话), 右键=2. 对于配置为左手使用按钮的操作被反转的鼠标，这些值从右向左读取。 |
| `buttons` 只读       | unsigned short                                               | 当鼠标事件被触发时按钮的buttons: 左键=1, 右键=2, 中间按钮=4, 第四个按钮(通常是"返回")=8,第五个按钮(通常是"前进")=16.若有两个或以上的按钮按下,返回以逻辑或运算形成的合并值.例如左键右键同时按下就返回 3 (=1 \| 2). [更多信息](https://developer.mozilla.org/zh-CN/docs/Web/API/MouseEvent). |
| `mozPressure` 只读   | float                                                        | 压力应用于接触或tabdevice时生成的事件的数量；该值介于0（最小压力）和1（最大压力）。 |
| `ctrlKey` 只读       | boolean                                                      | 当事件被触发时ctrl按键被按下时为true，否则为false。          |
| `shiftKey` 只读      | boolean                                                      | 当事件被触发时shift按键被按下时为true，否则为false。         |
| `altKey` 只读        | boolean                                                      | 当事件被触发时alt按键被按下时为true，否则为false。           |
| `metaKey` 只读       | boolean                                                      | 当事件被触发时meta按键被按下时为true，否则为false。          |

#### mouse 

* [mouseup | mdn](https://developer.mozilla.org/zh-CN/docs/Web/Reference/Events/mouseup)
* [mousedown | mdn](https://developer.mozilla.org/zh-CN/docs/Web/Reference/Events/mousedown)
* [contextmenu](https://developer.mozilla.org/en-US/docs/Web/API/Element/contextmenu_event)
* 

| [onmousedown](https://www.w3school.com.cn/jsref/event_onmousedown.asp) | 鼠标按钮被按下。     |
| ------------------------------------------------------------ | -------------------- |
| [onmousemove](https://www.w3school.com.cn/jsref/event_onmousemove.asp) | 鼠标被移动。         |
| [onmouseout](https://www.w3school.com.cn/jsref/event_onmouseout.asp) | 鼠标从某元素移开。   |
| [onmouseover](https://www.w3school.com.cn/jsref/event_onmouseover.asp) | 鼠标移到某元素之上。 |
| [onmouseup](https://www.w3school.com.cn/jsref/event_onmouseup.asp) | 鼠标按键被松开。     |



### KeyboardEvent

| [onkeydown](https://www.w3school.com.cn/jsref/event_onkeydown.asp) | 某个键盘按键被按下。       |
| ------------------------------------------------------------ | -------------------------- |
| [onkeypress](https://www.w3school.com.cn/jsref/event_onkeypress.asp) | 某个键盘按键被按下并松开。 |
| [onkeyup](https://www.w3school.com.cn/jsref/event_onkeyup.asp) | 某个键盘按键被松开。       |



 ### event.stopPropagation( )

> 只阻止事件往上冒泡



### event.preventDefault( )

> 阻止默认事件

> `return false` 
>
> 不仅阻止了事件往上冒泡，而且阻止了事件本身(默认事件)

```
$("#div1").mousedown(function(event){
    var e=e||window.event;
    return false;
});
```



###   event.stopImmediatePropagation()

> 阻止剩下的事件处理程序被执行。如果一个元素上绑定了三个事件，在其中一个事件上调用了这个方法，那其他 的两个事件将不会被执行。



# 其他



## js中new实例化对象内部过程

> [js中new实例化对象内部过程](https://blog.csdn.net/qq_42535651/article/details/103336256)

* 没return时

```js
function Person () {
    this.name = name;
    this.age = age;
    this.job = job;
 
    this.sayName = function () {
        return this.name;
    };
}
 
var person = new Person("tom", 21, "WEB");
 
console.log(person.name);
```

* 输出

```
person
Person {name: "tom", age: 21, job: "WEB", sayName: ƒ}
name: "tom"
age: 21
job: "WEB"
sayName: ƒ ()
__proto__:
constructor: ƒ Person(name, age, job)
__proto__: Object
```

* 有return 时

> 仅返回return 值

```js
function Person (name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
 
    this.sayName = function () {
        return this.name;
    };
    return {
        name,
        age,
        job
    }
}
```

* 输出

```js
person
{name: "tom", age: 21, job: "WEB"}
name: "tom"
age: 21
job: "WEB"
__proto__:
constructor: ƒ Object()
....
```





## 反引号 

```javascript
`sds` 是 js的语法， 不是html的， 勿乱用 
```





### Object.assign()

```javascript
a = Object.assign(b, c);
// a === b, a !== c;
b = [1];
a = Object.assign([], b);
// a = [1]; a !== b;
// 但 a 、 b 时浅拷贝， 内部若有引用类型，则指向同一内存；

// 实现深拷贝
// Deep Clone 
obj1 = { a: 0 , b: { c: 0}}; 
let obj3 = JSON.parse(JSON.stringify(obj1)); 
obj1.a = 4; 
obj1.b.c = 4; 
console.log(JSON.stringify(obj3)); // { a: 0, b: { c: 0}}
```



## Iterator 迭代器属性

* 可迭代对象

>带有遍历器特性的对象(即有序对象): data[Symbol.iterator]存在
>
>有 Array, Map, Set, NodeList, String
>
>而{} 是无序的，没有[Symbol.iterator]属性

* 有[Symbol.iterator], 可以用 for  of  遍历值

  ```javascript
  str = "dafadf" 
  // > "dafadf"
  str[Symbol.iterator]()  
  // > StringIterator {}  // 返回各自的迭代器
  str[Symbol.iterator]().next()
  // > {value: "d", done: false}
  ```

  