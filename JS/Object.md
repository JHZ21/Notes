# Object 方法



## Object.assign

* [`Object.assign()| MDN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)

> Object.assgin() 拷贝的事对象的属性引用，而不是对象本身，第一位置对象参数，也是返回对象
>
> ```JS
> Object.assign(target, ...sources)
> ```



## Object.defineProperty

* [Object.defineProperty()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

```js
Object.defineProperty(obj, prop, descriptor)
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





## Object.freeze()

* [Object.freeze() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)

> 可以**冻结**一个对象。一个被冻结的对象再也不能被修改；冻结了一个对象则不能向这个对象添加新的属性，不能删除已有属性，不能修改该对象已有属性的可枚举性、可配置性、可写性，以及不能修改已有属性的值。此外，冻结一个对象后该对象的原型也不能被修改。`freeze()` 返回和传入的参数相同的对象。



## Object.seal()

* [Object.seal() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/seal)

> 封闭一个对象，阻止添加新属性并将所有现有属性标记为不可配置。当前属性的值只要原来是可写的就可以改变。



## Object.preventExtensions()

[Object.preventExtensions() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/preventExtensions)

> 让一个对象变的不可扩展，也就是永远不能再添加新的属性。



