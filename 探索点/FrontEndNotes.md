# Html 、CSS 、 JS 

## 	Html、 Css

- **pointer-events** CSS 属性指定在什么情况下 (如果有) 某个特定的图形元素可以成为鼠标事件的 [target](https://developer.mozilla.org/zh-CN/docs/Web/API/event.target)。

  [*pointer-events* - CSS(层叠样式表) | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/pointer-events)

- ul li 的 小标点，不占位置需要设置padding: 0; line-style: none; 只能样式为空。
- [BFC](https://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html) 
- [内联元素和块级元素的区别](https://blog.csdn.net/xuanfuhuo4769/article/details/81326457)
- [inline-block](https://www.cnblogs.com/Ry-yuan/p/6848197.html)与inline, block, float的区别

* ~~~css
  text-overflow
    (属性规定当文本溢出包含元素时发生的事情)
  clip	修剪文本。
  ellipsis	显示省略符号来代表被修剪的文本。
  string	使用给定的字符串来代表被修剪的文本。
  ~~~

* ```css
  word-break
   （属性规定自动换行的处理方法）
  normal	使用浏览器默认的换行规则。
  break-all	允许在单词内换行。
  keep-all	只能在半角空格或连字符处换行。
  
  white-space 
    (属性设置如何处理元素内的空白）
  normal	默认。空白会被浏览器忽略。
  pre	空白会被浏览器保留。其行为方式类似 HTML 中的 <pre> 标签。
  nowrap	文本不会换行，文本会在在同一行上继续，直到遇到 <br> 标签为止。
  pre-wrap	保留空白符序列，但是正常地进行换行。
  pre-line	合并空白符序列，但是保留换行符。
  inherit	规定应该从父元素继承 white-space 属性的值。
  ```

* text-align 可以改变 < span >< /span>位置

* ```css
  position 
    (属性规定元素的定位类型)
    static		默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 
    				z-index 声明）。
    				
    relative	    生成相对定位的元素，相对于其正常位置进行定位。
  				因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。
                  
    absolute		生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。
  				元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
  		
    fixed			生成绝对定位的元素，相对于浏览器窗口进行定位。
  				元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
  				
    inherit	    规定应该从父元素继承 position 属性的值。
  ```

* ```css
  transform 转换
      2D变换方法：
      translate()：使转化(效果：移动)
      rotate()
      scale()
      skew()
      matrix()
      3D:....
      
  transition: 过渡，是元素从一种样式逐渐改变为另一种的效果
  animation: 动画，使元素从一种样式逐渐变化为另一种样式的效果
  				可以改变任意多的样式任意多的次数
      
  ```

  

* ul li 序列小黑点存在于 padding-left: 40px  里

* [ CSS样式表的继承性和层叠性]([https://github.com/qianguyihao/Web/blob/master/02-CSS/05-CSS%E6%A0%B7%E5%BC%8F%E8%A1%A8%E7%9A%84%E7%BB%A7%E6%89%BF%E6%80%A7%E5%92%8C%E5%B1%82%E5%8F%A0%E6%80%A7.md](https://github.com/qianguyihao/Web/blob/master/02-CSS/05-CSS样式表的继承性和层叠性.md))

* [css垂直居中的常见方法](https://www.cnblogs.com/yugege/p/5246652.html)

* 









## Js



> 位: bit 
>
> 字节：1 byte = 8 bit   (1 B = 8 b)
>
> 1 KB = 1024 B
>
> 1 MB = 1024 KB
>
> .......
>
> 

```javascript
arrayObject.splice(index,howmany,item1,.....,itemX)
// index	必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。
// howmany	必需。要删除的项目 _数量_。如果设置为 0，则不会删除项目。
// item1, ..., itemX	可选。向数组添加的新项目。
arrayObject.splice(index) 相当于arrayObject.splice(index, -1)

```

- [offsetTop, clientHeight 图解](https://blog.csdn.net/weixin_42776027/article/details/88568306)

- [帮你彻底搞懂JS中的prototype、__proto__与constructor（图解)](https://blog.csdn.net/cc18868876837/article/details/81211729)

- 根据timestamp 转化日期

  new Date(1500478373000).toLocaleString() ==> 2017/7/19 下午11:32:53

  现在时间戳，随着时间积累，已经13位了，如“1500478373” 只有10位的是精确为秒(s)的, 注意补“000”即可。

* parseInt( )

  - ![parseInt()][p0]

  

  








[p0]:http://proudmodest.cn/img/parseInt.png

