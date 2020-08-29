# traversal 遍历

* [ES6中的迭代器(Iterator)和生成器(Generator)](https://www.cnblogs.com/xiaohuochai/p/7253466.html)





## generator

* [generator | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Generator)
* 



## iterator

> ES6 规定，默认的 Iterator 接口部署在数据结构的 **Symbol.iterator** 属性，或者说，一个数据结构只要具有**Symbol.iterator**属性，就可以认为是“可遍历的”（iterable）。
>
> **Symbol.iterator** 属性本身是一个函数，就是当前数据结构默认的遍历器生成函数。
>
> [ES6 iterator | 简书](https://www.jianshu.com/p/886354c26ec9)

* Iterator 的遍历过程:
  * 创建一个指针对象，指向当前数据结构的起始位置。也就是说，遍历器对象本质上，就是一个指针对象。
  * 第一次调用指针对象的next方法，可以将指针指向数据结构的第一个成员。
  * 第二次调用指针对象的next方法，指针就指向数据结构的第二个成员。
  * 不断调用指针对象的next方法，直到它指向数据结构的结束位置。
     每一次调用next方法，都会返回数据结构的当前成员的信息。具体来说，就是返回一个包含value和done两个属性的对象。其中，value属性是当前成员的值，done属性是一个布尔值，表示遍历是否结束。
* iterator function
  * 初阶

```js
function createIterator(items) {
    var i = 0;
    return {
        next: function() {
            var done = (i >= items.length);
            var value = !done ? items[i++] : undefined;
            return {
                done: done,
                value: value
            };
        }
    };
}
var iterator = createIterator([1, 2, 3]);
console.log(iterator.next()); // "{ value: 1, done: false }"
console.log(iterator.next()); // "{ value: 2, done: false }"
console.log(iterator.next()); // "{ value: 3, done: false }"
console.log(iterator.next()); // "{ value: undefined, done: true }"
... ...
console.log(iterator.next()); // "{ value: undefined, done: true }"
```

​      中级

```js
function createIterator(items) {
    let i = 0
    return {
        next: function () {
            let done = (i >= items.length)
            let value = !done ? items[i++] : undefined
            return {
                done: done,
                value: value
            }
        }
        [Symbol.iterator]: function () {
        	return this
    	}
    }
}
let iterator = createIterator([1, 2, 3])
...iterator		// 1, 2, 3
```

* iterator 高级版
  * for...of...接收可迭代对象,能强制转换或包装可迭代对象的值;
  * 遍历时，for...of会获取可迭代对象的'Symbol.iterator'，对该迭代器逐次调用next()，直到迭代器返回对象的done属性为true时，遍历结束，不对该value处理;
  * 所以可以利用 for...of...封装到原型链上.

```js
Object.prototype[Symbol.iterator] = function* () {
    for (const key in this) {
        if (this.hasOwnProperty(key)) {
            yield [key, this[key]]
        }
    }
}
```



* rangeIterator class 

```js
// class 版
class RangeIterator {
  constructor(start, stop) {
    this.value = start;
    this.stop = stop;
  }

  [Symbol.iterator]() { return this; }

  next() {
    var value = this.value;
    if (value < this.stop) {
      this.value++;
      return {done: false, value: value};
    }
    return {done: true, value: undefined};
  }
}

function range(start, stop) {
  return new RangeIterator(start, stop);
}

for (var value of range(0, 3)) {
  console.log(value); // 0, 1, 2
}
```





## Object.keys()

> Object.keys() 方法会返回一个由一个给定对象的`自身可枚举`属性组成的数组，数组中属性名的排列顺序和正常循环遍历该对象时返回的顺序一致 。

* 语法

```js
Object.keys(obj)
// [,,,]
```





## for  in

> 遍历所有可遍历属性，包括`原型链上`的

