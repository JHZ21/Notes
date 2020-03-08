# 原型与实例



## `__proto__ ` 和 `prototype`

```javascript 
Function.__proto__ === Function.prototype
// true
Object.__proto__ === Function.prototype
// true
Function.prototype.__proto__ === Object.prototype
// true
Object.prototype.__proto__
// null 

Function.__proto__.__proto__ === Object.prototype
// true
Object.__proto__.__proto__ === Object.prototype
// true

Function.__proto__ === Object.prototype
// false
```

* 总所周知，`A.__proto__` 指向其父类A的prototype, 即 

  ``` javascript
   Object.__proto__ === Function.prototype // true 
  ```

* 所有函数的都是Function的实例，即所以函数的`__proto__`都指向`Function.prototype`, 包括 Array, Object, Function等

  ```javascript
  Function.__proto__ === Function.prototype
  // true
  Object.__proto__ === Function.prototype
  // true
  ```

* prototype 是对象，所以它的`__proto__`若不为`null`, 则指向`Object.prototype`

  ``` javascript
  Function.prototype.__proto__ === Object.prototype
  // true
  ```

  所以这就解释了，原型链最终会指向`Object.prototype`

* 而 `Object.prototype.__proto__`  为 `null`

  





## [一张图看懂 Function 和 Object 的关系及简述 instanceof 运算符](https://juejin.im/post/58358606570c35005e4142bd)

![Function与Object的关系图][p0]













[p0]: http://proudmodest.cn/img/Function-Object.png