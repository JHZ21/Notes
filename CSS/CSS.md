# CSS



## 居中（不忘初心）





## 伪类::before ::after

* 创建在元素内部的前后与后面，p : before





## 选择器优先级

* 遵守就近原则  ： 内联样式表 > 内部样式表 > 外部样式表
* id 选择器  > 类选择器 > 标签选择器

* !important > 内联样式 > ID选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 元素选择器 = 关系选择器(子代，后代) = 伪元素选择器 > 通配符选择器 > 继承



## text-indent

> text-indent 属性规定文本块中首行文本的缩进。
>
> [text-indent | w3school ](https://www.w3school.com.cn/cssref/pr_text_text-indent.asp)

* 允许使用负值。如果使用负值，那么首行会被缩进到左边
* em  大小根据从（父元素等）继承到的字号大小



[理解CSS3 transform中的Matrix(矩阵)](zhangxinxu.com/wordpress/2012/06/css3-transform-matrix-矩阵/)



## 动画

### transition 过渡动画

* 语法

```
transition: property duration timing-function delay;
```

| 值                                                           | 描述                                |
| :----------------------------------------------------------- | :---------------------------------- |
| [transition-property](https://www.w3school.com.cn/cssref/pr_transition-property.asp) | 规定设置过渡效果的 CSS 属性的名称。 |
| [transition-duration](https://www.w3school.com.cn/cssref/pr_transition-duration.asp) | 规定完成过渡效果需要多少秒或毫秒。  |
| [transition-timing-function](https://www.w3school.com.cn/cssref/pr_transition-timing-function.asp) | 规定速度效果的速度曲线。            |
| [transition-delay](https://www.w3school.com.cn/cssref/pr_transition-delay.asp) | 定义过渡效果何时开始。              |

### animation  动画

## 语法

```css
animation: name duration timing-function delay iteration-count direction;
```

| 值                                                           | 描述                                     |
| :----------------------------------------------------------- | :--------------------------------------- |
| *[animation-name](https://www.w3school.com.cn/cssref/pr_animation-name.asp)* | 规定需要绑定到选择器的 keyframe 名称。。 |
| *[animation-duration](https://www.w3school.com.cn/cssref/pr_animation-duration.asp)* | 规定完成动画所花费的时间，以秒或毫秒计。 |
| *[animation-timing-function](https://www.w3school.com.cn/cssref/pr_animation-timing-function.asp)* | 规定动画的速度曲线。                     |
| *[animation-delay](https://www.w3school.com.cn/cssref/pr_animation-delay.asp)* | 规定在动画开始之前的延迟。               |
| *[animation-iteration-count](https://www.w3school.com.cn/cssref/pr_animation-iteration-count.asp)* | 规定动画应该播放的次数。                 |
| *[animation-direction](https://www.w3school.com.cn/cssref/pr_animation-direction.asp)* | 规定是否应该轮流反向播放动画。           |

* 例子

```
div
{
animation:mymove 5s infinite;
-webkit-animation:mymove 5s infinite; /* Safari 和 Chrome */
}

@keyframes mymove
{
from {left:0px;}
to {left:200px;}
}
```



## 层叠规则

### z-index

可以设置z-index属性的元素

* 定位元素 position 不为 static 
* flex  元素

### 层叠顺序规则

* 内容
  * 正 z-index
  
  * z-index: auto， 
  
    或 z-index：0， 
  
    不依赖z-index的层叠上下文
  
  * inline 水平盒子
* 布局
  * float 浮动盒子
  * block 块状水平盒子
* 装饰
  * 负 z-index
  * 层叠上下文 background / border

### 层叠准则

* 谁大谁上 （如：z-index)
* 后来居上   · (DOM 流处于后面会覆盖前面的元素)

### 创建层叠上下文

* z-index : 非默认值aut;  如：z-index: 0;
* CSS3: transform , 如：tranform: scale(1);

###  补充

* 元素成为地位元素，其z-index就会自动生效，值为默认的auto
* 不支持z-index属性的元素,  天然是z-index: auto



## transition 过渡

* display 

> 冲突：当改变元素display属性时，过渡属性transition失效。
>
> 原因：display:none的时候，页面文档流中将不会存在该元素。transition无法对一个从有到无的元素产生过渡效果。
>
> 解决方法：
>
> ​    1.改变元素的宽/高为0px,达到隐藏的目的。
>
> ​    2.使用visibility替代display。



## padding, margin 百分比

> 论垂直还是水平，百分比值始终参考宽度
>
> [CSS 百分比 margin & padding](https://swordair.com/css-persentage-margin-and-padding/?utm_source=tuicool&utm_medium=referral)
>
> 



## 颜色

### rgba

> 可以配合scss等，变量替换

```
rgba(red, green, blue, alpha)
rgba(color, alpha) 
```





## display 元素显示的类型

* [CSS display 属性](https://www.w3school.com.cn/cssref/pr_class_display.asp)
* [display | mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)



## transform 变换

* [transform | mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform)

### translate 平移

```css
transform: translate(12px, 50%);
```

### scale 放缩

```css
transform: scale(2, 0.5);
```

### rotate 旋转

```css
tansform: rotate(0.5turn);  turn 转
tansform: rotate(180deg);
```

### skew 倾斜

```css
transform: skew(30deg, 20deg);
```

### matrix 矩阵变化

```
transform: martix(1, 2, 3, 4, 5, 6)
```

* [对CSS3中的transform：Matrix（）矩阵的一些理解](https://www.cnblogs.com/Ivy-s/p/6786622.html)











## postion

> left、top等，百分比都根据其定位元素宽高

| 值       | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| absolute | 生成绝对定位的元素，相对于 `static` 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 |
| fixed    | 生成绝对定位的元素，相对于`浏览器窗口`进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 |
| relative | 生成相对定位的元素，相对于`其正常位置`进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。" left: 50%", 向左移动50%`父元素宽带` |
| static   | 默认值。没有定位，元素出现在正常的流中（`忽略 `top, bottom, left, right 或者 z-index 声明）。 |
| inherit  | 规定应该从父元素`继承` position 属性的值。                   |



## 元素靠右

### margin-left: auto;

```css
display: block;
margin-left: auto;
width: 900px;
// 利用block的性质，与 margin: auto; 居中类似
// 左边距auto, 自适应，元素将靠左
```





## writing-mode 文本方向

> writing-mode属性, 不仅改变文本的显示方向，更直接改变了文本流的方向。如果其属性值改为vertical-rl，则文本流改成了垂直方向，则text-align变成了垂直对齐，vertical-align变成了水平对齐
>
> 值: horizontal-tb | vertical-rl | vertical-lr
>
> 初始值: horizontal-tb
>
> 应用于: 除表格类元素之外的所有元素
>
> 继承性: 有
>
> 更多属性请看 [CSS 文本方向](https://www.cnblogs.com/zhangkeyu/p/6645189.html)



## CSS 选择器

> [CSS 选择器参考手册 | W3school](https://www.w3school.com.cn/cssref/css_selectors.asp)



| 选择器                                                       | 例子                  | 例子描述                                      |
| ------------------------------------------------------------ | --------------------- | --------------------------------------------- |
| [:first-of-type](https://www.w3school.com.cn/cssref/selector_first-of-type.asp) | p:first-of-type       | 选择其父元素的第一个 p 子元素。               |
| [:last-of-type](https://www.w3school.com.cn/cssref/selector_last-of-type.asp) | p:last-of-type        | 选择其父元素的最后一个 p 子元素。             |
| [:only-of-type](https://www.w3school.com.cn/cssref/selector_only-of-type.asp) | p:only-of-type        | 选择其父元素的p子元素仅一个的p元素            |
| [:only-child](https://www.w3school.com.cn/cssref/selector_only-child.asp) | p:only-child          | 选择其父元素仅有一个子元素的 p 元素。         |
| [:nth-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-child.asp) | p:nth-child(2)        | 选择其父元素的第二个子元素。                  |
| [:nth-last-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-child.asp) | p:nth-last-child(2)   | 同上，从最后一个子元素开始计数。              |
| [:nth-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-of-type.asp) | p:nth-of-type(2)      | 选择属于其父元素第二个 p 元素的每个 p 元素。  |
| [:nth-last-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-of-type.asp) | p:nth-last-of-type(2) | 同上，但是从最后一个子元素开始计数。          |
| [:last-child](https://www.w3school.com.cn/cssref/selector_last-child.asp) | p:last-child          | 选择属于其父元素最后一个子元素每个 <p> 元素。 |

> 总结
>
> * type ：有类型要求
> * child：只需为子元素
> * only :  仅仅，个数要唯一
> * last  :  倒数







## CSS 穿透 作用于子组件

* [vue css >>> /deep/ 穿透](https://blog.csdn.net/Alex81320/article/details/86234369 )

* [Vue scoped CSS 与深度作用选择器 /deep/]( https://blog.csdn.net/qq_32340877/article/details/81164072 )



## css 中使用别名路径

你想要引用一个 npm 依赖中的文件，或是想要用 webpack alias，则需要在路径前加上 `~` 的前缀来避免歧义。



## webkit-scrollbar

* 美化滚动条样式，仅生效于chrome 浏览器

```scss
@mixin webkit-scrollbar {
  &::-webkit-scrollbar {
    width: 10px;  // 作用于竖轴
    height: 10px; // 作用于横轴
    background-color: transparent;
    opacity: 0.5;
  }

  &::-webkit-scrollbar-track {
    background-color: transparent;
  }

  &::-webkit-scrollbar-thumb {
    background: rgba(132, 208, 255, 0.5);
    ;
  }

  &::-webkit-scrollbar-button:start {
    // background: url(./imgs/up.png) no-repeat;
    background-color: transparent;
    background-size: 12px 12px;
  }

  &::-webkit-scrollbar-button:end {
    // background: url(./imgs/down.png) no-repeat;
    background-color: transparent;
    background-size: 12px 12px;
  }
}
```

* 其他情况，可以自己创造滚动条并监听滚动，以实现美丽的滚动条