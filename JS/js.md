# Js 对象

* [JavaScript 和 HTML DOM 参考手册 | RUNOOB](https://www.runoob.com/jsref/jsref-tutorial.html)
* [JavaScript 参考手册 | W3school](https://www.w3school.com.cn/jsref/index.asp)



## Array

* [concat()](https://www.runoob.com/jsref/jsref-concat-array.html)

* [copyWithin()](https://www.runoob.com/jsref/jsref-copywithin.html)

* [entries()](https://www.runoob.com/jsref/jsref-entries.html)

* [fill()](https://www.runoob.com/jsref/jsref-fill.html)

* [filter()](https://www.runoob.com/jsref/jsref-filter.html)
* [find()](https://www.runoob.com/jsref/jsref-find.html)
* [findIndex()](https://www.runoob.com/jsref/jsref-findindex.html)
* [forEach()](https://www.runoob.com/jsref/jsref-foreach.html)
* [from()](https://www.runoob.com/jsref/jsref-from.html)
* [includes()](https://www.runoob.com/jsref/jsref-includes.html)
* [indexOf()](https://www.runoob.com/jsref/jsref-indexof-array.html)
* [isArray()](https://www.runoob.com/jsref/jsref-isarray.html)
* [join()](https://www.runoob.com/jsref/jsref-join.html)
* [keys()](https://www.runoob.com/jsref/jsref-keys.html)
* [lastIndexOf()](https://www.runoob.com/jsref/jsref-lastindexof-array.html)
* [map()](https://www.runoob.com/jsref/jsref-map.html)
* [pop()](https://www.runoob.com/jsref/jsref-pop.html)
* [push()](https://www.runoob.com/jsref/jsref-push.html)
* [reduce()](https://www.runoob.com/jsref/jsref-reduce.html)
* [reduceRight()](https://www.runoob.com/jsref/jsref-reduceright.html)
* [reverse()](https://www.runoob.com/jsref/jsref-reverse.html)
* [shift()](https://www.runoob.com/jsref/jsref-shift.html)
* [slice()](https://www.runoob.com/jsref/jsref-slice-array.html)
* [some()](https://www.runoob.com/jsref/jsref-some.html)
* [sort()](https://www.runoob.com/jsref/jsref-sort.html)
* [splice()](https://www.runoob.com/jsref/jsref-splice.html)
* [toString()](https://www.runoob.com/jsref/jsref-tostring-array.html)
* [unshift()](https://www.runoob.com/jsref/jsref-unshift.html)
* [valueOf()](https://www.runoob.com/jsref/jsref-valueof-array.html)



## Boolean

* [toString()](https://www.w3school.com.cn/jsref/jsref_toString_boolean.asp)

* [valueOf()](https://www.w3school.com.cn/jsref/jsref_valueOf_boolean.asp)



## Date()



## Math

> [JavaScript Math 对象](https://www.w3school.com.cn/jsref/jsref_obj_math.asp)



* [max(x,y)](https://www.w3school.com.cn/jsref/jsref_max.asp)

* [min(x,y)](https://www.w3school.com.cn/jsref/jsref_min.asp)

* [abs(x)](https://www.w3school.com.cn/jsref/jsref_abs.asp)





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

> 四舍五入，正入正，负如负

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



### Number.toFixed()

> 可把 Number 四舍五入为指定小数位数的数字



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

>  [JS String](https://www.w3school.com.cn/jsref/jsref_obj_string.asp)

* [anchor()](https://www.w3school.com.cn/jsref/jsref_anchor.asp)
* [charAt()](https://www.w3school.com.cn/jsref/jsref_charAt.asp)
* [charCodeAt()](https://www.w3school.com.cn/jsref/jsref_charCodeAt.asp)
* [concat()](https://www.w3school.com.cn/jsref/jsref_concat_string.asp)
* [fromCharCode()](https://www.w3school.com.cn/jsref/jsref_fromCharCode.asp)
* [indexOf()](https://www.w3school.com.cn/jsref/jsref_indexOf.asp)
* [lastIndexOf()](https://www.w3school.com.cn/jsref/jsref_lastIndexOf.asp)
* [match()](https://www.w3school.com.cn/jsref/jsref_match.asp)
* [replace()](https://www.w3school.com.cn/jsref/jsref_replace.asp)
* [search()](https://www.w3school.com.cn/jsref/jsref_search.asp)
* [slice()](https://www.w3school.com.cn/jsref/jsref_slice_string.asp)
* [small()](https://www.w3school.com.cn/jsref/jsref_small.asp)
* [split()](https://www.w3school.com.cn/jsref/jsref_split.asp)
* [substr()](https://www.w3school.com.cn/jsref/jsref_substr.asp)
* [substring()](https://www.w3school.com.cn/jsref/jsref_substring.asp)
* [toLocaleLowerCase()](https://www.w3school.com.cn/jsref/jsref_toLocaleLowerCase.asp)
* [toLocaleUpperCase()](https://www.w3school.com.cn/jsref/jsref_toLocaleUpperCase.asp)
* [toLowerCase()](https://www.w3school.com.cn/jsref/jsref_toLowerCase.asp)
* [toUpperCase()](https://www.w3school.com.cn/jsref/jsref_toUpperCase.asp)
* [toString()](https://www.w3school.com.cn/jsref/jsref_toString_string.asp)
* [valueOf()](https://www.w3school.com.cn/jsref/jsref_valueOf_string.asp)



## RegExp

* [compile](https://www.w3school.com.cn/jsref/jsref_regexp_compile.asp)
* [exec](https://www.w3school.com.cn/jsref/jsref_exec_regexp.asp)
* [test](https://www.w3school.com.cn/jsref/jsref_test_regexp.asp)



## Functions

* [parseFloat()](https://www.w3school.com.cn/jsref/jsref_parseFloat.asp)
* [parseInt()](https://www.w3school.com.cn/jsref/jsref_parseInt.asp)
* [escape()](https://www.w3school.com.cn/jsref/jsref_escape.asp)
* [unescape()](https://www.w3school.com.cn/jsref/jsref_unescape.asp)
* [eval()](https://www.w3school.com.cn/jsref/jsref_eval.asp)



## Evetns

> [JS Events](https://www.w3school.com.cn/jsref/jsref_events.asp)





# Browser 对象



## Window

>Window 对象表示浏览器中打开的窗口。
>
>[Window](https://www.w3school.com.cn/jsref/dom_obj_window.asp)
>
>

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



## Screen



## History

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

* [History | mdn](https://developer.mozilla.org/zh-CN/docs/Web/API/History)



## Location

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





# HTML DOM 对象



## Document

>每个载入浏览器的 HTML 文档都会成为 Document 对象。
>
>Document 对象使我们可以从脚本中对 HTML 页面中的所有元素进行访问。
>
>**提示：**Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。
>
>[DOM Document](https://www.w3school.com.cn/jsref/dom_obj_document.asp)



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
>[DOM Event](https://www.w3school.com.cn/jsref/dom_obj_event.asp)



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

  