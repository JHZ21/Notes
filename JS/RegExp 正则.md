# RegExp

>  ### Regular Expression :  正则表示式



## 题库

* [闯关学正则｜编程胶囊](https://www.codejiaonang.com/#/courses)

### thousandth 千分位

```js
function thousandth(str) {
  return str.replace(/\d{1,3}(?=(\d{3})+$)/g, "$&,");
}
```







## replace

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





## 贪婪与非贪婪 ？

* ?  匹配一个字符零次或一次，另一个作用是非贪婪模式

* 正则表达式默认是**贪婪模式**，即尽可能的匹配更多字符，而要使用**非贪婪模式**，我们要在**表达式后面加上 `?`号**。

* 例子：

  > \d{3,4}?
  >
  > \w+?

```js
// 默认 贪婪
'0721'.match(/\d{3,4}/)
// ["0721", index: 0, input: "0721", groups: undefined]
```

```js
// ？非贪婪
'0721'.match(/\d{3,4}?/)
// ["072", index: 0, input: "0721", groups: undefined]
```





## RegExp 对象方法

| 方法                                                         | 描述                                               | FF   | IE   |
| :----------------------------------------------------------- | :------------------------------------------------- | :--- | :--- |
| [compile](https://www.w3school.com.cn/jsref/jsref_regexp_compile.asp) | 编译正则表达式。                                   | 1    | 4    |
| [exec](https://www.w3school.com.cn/jsref/jsref_exec_regexp.asp) | 检索字符串中指定的值。返回找到的值，并确定其位置。 | 1    | 4    |
| [test](https://www.w3school.com.cn/jsref/jsref_test_regexp.asp) | 检索字符串中指定的值。返回 true 或 false。         | 1    | 4    |

## 支持正则表达式的 String 对象的方法

| 方法                                                         | 描述                             | FF   | IE   |
| :----------------------------------------------------------- | :------------------------------- | :--- | :--- |
| [search](https://www.w3school.com.cn/jsref/jsref_search.asp) | 检索与正则表达式相匹配的值。     | 1    | 4    |
| [match](https://www.w3school.com.cn/jsref/jsref_match.asp)   | 找到一个或多个正则表达式的匹配。 | 1    | 4    |
| [replace](https://www.w3school.com.cn/jsref/jsref_replace.asp) | 替换与正则表达式匹配的子串。     | 1    | 4    |
| [split](https://www.w3school.com.cn/jsref/jsref_split.asp)   | 把字符串分割为字符串数组。       | 1    | 4    |

## RegRexp



## stringObject

```js
stringObject.split(separator,howmany)
```





## String

### match(regexp)

* [String.prototype.match() | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/match)

* ```js
  str.match(regexp)
  ```

* 是否使用g标志

  * 如果使用g标志，则将返回

    * 完整正则表达式匹配的所有结果，`但不会返回捕获组`

  * 如果未使用g标志，则仅返回

    * 第一个完整匹配

    * 相关的捕获组。 
    * `index`: 匹配的结果的开始位置
    * `input`: 搜索的字符串.

    - `groups`: 一个捕获组数组 或 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)（如果没有定义命名捕获组）。

* examples

  ```js
  'ssad'.match(/s(a|d)/)
  // ["sa", "a", index: 1, input: "ssad", groups: undefined]
  ```

  ```js
  'ssad'.match(/s(a|d)/g)
  // ["sa"]
  ```

  ```js
  'ssad'.match(/aa/)
  // null
  ```

  ```js
  'ssasd'.match(/(s)(a|d)/)
  // ["sa", "s", "a", index: 1, input: "ssasd", groups: undefined]
  ```

  

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

### 获取匹配

* (pattern)

  ```js
  "Windows2000".match(/Windows(95|98|NT|2000)/)
  // ["Windows2000", "2000", index: 0, input: "Windows2000", groups: undefined]
  ```



### \N 分组的回溯引用

* \1 , \2 对应 获取的分组

```js
'<font>adafa</font>ad'.match(/<(\w+)>.*?<\/\1>/g)
// ["<font>adafa</font>"]
```







### 非获取匹配

> 不占用字符，匹配字符可重新匹配

* (?:pattern)

  > 会匹配 pattern，但不获取匹配结果

  ```js
  'abcd'.match(/a(?:b)/)
  // ["ab", index: 0, input: "abcd", groups: undefined]
  ```

  

* (?=pattern)

  > 正向肯定预查

  ```js
  "Windows2000".match(/Windows(?=95|98|NT|2000)/)
  // ["Windows", index: 0, input: "Windows2000", groups: undefined]
  ```

* (?!pattern)

  > 正向否定预查

* ?<=pattern)

  > 反向肯定预查

  ```js
  "2000Windows".match(/(?<=95|98|NT|2000)Windows/)
  // ["Windows", index: 4, input: "2000Windows", groups: undefined]
  ```

* (?<!pattern)

  > 反向否定预查



## []: 

* 字符集合

  > 匹配所包含的任意一个字符

  ```js
  'abc'.match(/[ba]/)
  // ["a", index: 0, input: "abc", groups: undefined]
  ```

* 非字符集合

  > [^xyz]

* 字符范围

  > [a-z]

* 非字符范围

  > [^a-z]



## .  除 \n 之外

>  匹配除 “\n” 之外的任何单个字符

* 要匹配包括 ‘\n’ 在内的任何字符，请使用像 [.\n]  [\d\D] [\s\S] 模式



## \b 单词边界

> 边界：非[A-Za-z0-9_]
>
> 匹配一个长度为`0`的子串



## \w 

> 匹配包括下划线的任何单词字符。等价于’[A-Za-z0-9_]’





## 好文

* [正则表达式 | 菜鸟](https://www.runoob.com/regexp/regexp-syntax.html)

* [正则表达式到底是什么 | 掘金](https://juejin.im/post/5cdcd42551882568651554e6#heading-4)

* [JavaScript RegExp 对象的参考手册](https://www.runoob.com/jsref/jsref-obj-regexp.html)

* [RegExp | 菜鸟](https://www.runoob.com/jsref/jsref-obj-regexp.html)

* [RegExp | mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

* [《JavaScript 正则表达式迷你书》问世了！| 掘金](https://link.zhihu.com/?target=https%3A//juejin.im/post/59cc61176fb9a00a437b290b)

  

