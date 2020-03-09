# RegExp

>  ### Regular Expression :  正则表示式



## `*` 星号

>匹配任何包含零个或多个 n 的字符串。

>错误(意外)使用：

```js
let string = "我的账户余额：2,235,467.20"
    
string.match(/[\d]*/)
> ["", index: 0, input: "我的账户余额：2,235,467.20", groups: undefined]
*: 零个也可以，也就可以匹配到`空`，而且没有g, 只匹配的第一个

string.match(/[\d]*/g)
> ["", "", "", "", "", "", "", "2", "", "235", "", "467", "", "20", ""]
```



```js
"123456789".replace(/(?!^)(?=(\d{3})+$)/g, ',')
>  "123,456,789"
```



## ( ) : 括号

> * 在被修饰匹配次数的时候，括号中的表达式可以作为`整体`被修饰
> *  取匹配结果的时候，括号中的表达式匹配到的内容可以被单独得到



* [正则表达式 | 菜鸟](https://www.runoob.com/regexp/regexp-syntax.html)
* [正则表达式到底是什么 | 掘金](https://juejin.im/post/5cdcd42551882568651554e6#heading-4)
* [JavaScript RegExp 对象的参考手册](https://www.runoob.com/jsref/jsref-obj-regexp.html)
* [RegExp | 菜鸟](https://www.runoob.com/jsref/jsref-obj-regexp.html)
* [RegExp | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

