[Javascript中==的类型转换详解，JS中相等比较（==）强制类型转换详解](https://blog.csdn.net/MFWSCQ/article/details/100867026)

[js学习之——数据类型间的转换以及==和===的理解](https://www.cnblogs.com/qiaoyun/p/10560273.html)

* [JavaScript 的怪癖 1：隐式类型转换](https://justjavac.com/javascript/2013/04/08/javascript-quirk-1-implicit-conversion-of-values.html)

# == 

* 如果 x 或 y 中有一个为 NaN，则返回 false；

* 如果 x 与 y 皆为 null 或 undefined 中的一种类型，则返回 true（null == undefined // true）；否则返回 false（null == 0 // false）；(null, undefined不会转换为其他类型)

* 如果 x,y 类型不一致，且 x,y 为 `String、Number、Boolean `中的某一类型，则将 x,y 使用 toNumber 函数转化为 Number 类型再进行比较；

  ```js
  '' == 0 // true 
  false == 0 // true
  false == '0' // true
  true == '1' // true
  ```

  

* 如果 x，y 中有一个为 Object，则首先使用 ToPrimitive 函数将其转化为**原始类型**，再进行比较。（日期对象转换成字符串，其它对象先尝试调用valueOf()方法再尝试使用toString()） 

  > 而在 ES6 中引入 Symbol 类型之后，JavaScript 会优先调用对象的 [Symbol.toPrimitive] 方法来将该对象转化为原始类型，那么方法的调用顺序就变为了：

  * 当 `obj[Symbol.toPrimitive](preferredType)` 方法存在时，优先调用该方法；
  * 如果 preferredType 参数为 String，则依次尝试 `obj.toString()` 与 `obj.valueOf()`；
  * 如果 preferredType 参数为 Number 或者默认值，则依次尝试 `obj.valueOf()` 与 `obj.toString()`。

```js
[].valueOf() // []
[].toString() // ""
[] == 0 // true
[] == '' // true
0 == '' // true
```



```javascript
// 为了更好地理解其工作原理，我们可以用 JavaScript 进行简单地实现：
var ToPrimitive = function(obj,preferredType){
  var APIs = {
    typeOf: function(obj){
      return Object.prototype.toString.call(obj).slice(8,-1);
    },
    isPrimitive: function(obj){
      var _this = this,
          types = ['Null','Undefined','String','Boolean','Number'];
      return types.indexOf(_this.typeOf(obj)) !== -1; 
    }
  };
  // 如果 obj 本身已经是原始对象，则直接返回
  if(APIs.isPrimitive(obj)) {return obj;}

  // 对于 Date 类型，会优先使用其 toString 方法；否则优先使用 valueOf 方法
  preferredType = (preferredType === 'String' || APIs.typeOf(obj) === 'Date' ) ? 'String' : 'Number';
  if(preferredType==='Number'){
    if(APIs.isPrimitive(obj.valueOf())) { return obj.valueOf()};
    if(APIs.isPrimitive(obj.toString())) { return obj.toString()};
  }else{
    if(APIs.isPrimitive(obj.toString())) { return obj.toString()};
    if(APIs.isPrimitive(obj.valueOf())) { return obj.valueOf()};
  }
  throw new TypeError('TypeError');
}
```

* isNaN()存在隐式转换，Number()

![isNaN的隐式转换][p0]

* isNaN来测试后，发现字符串，undefined，甚至对象，结果都返回真！！！但是，我们总不能说他们也是NaN吧？总而言之，得出的结论是：isNaN检测NaN并不可靠！！！

  幸运的是，有一种可靠的并且准确的方法可以检测NaN。我们都知道，只有NaN是自己不等自己的，那么，我们就以使用不等于号（！==）来判断一个数是否等于自身，从而，可以检测到NaN了.

  ```javascript
  NaN !== NaN //true
  function isReallyNaN(x) {
      return x !== x;
  }
  ```

  

# ===, Object.is()

===不仅要值相等，还需要类型相等才会相等。有两个特殊的情况，一是NaN===NaN为false，+0===-0为true。

为了避免这两种情况，es6引进了Object.is()方法，使得Object.is(NaN,NaN)为true, Object.is(-0,+0)为false。





[p0]: http://proudmodest.cn/img/type-implicit-conversion/toPrimitive.png



