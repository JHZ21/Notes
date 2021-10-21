# CSS



## inline-block 之间的空隙

* 解决
  * Line-height: 0;
  * [inline-block空隙怎么解决](https://www.cnblogs.com/leena/p/6930175.html)



## 禁止文字被选中

* [css禁止选中文本怎么设置？](https://www.html.cn/qa/css3/13811.html)

* pc端：

```css
.not-select{
    -moz-user-select:none; /*火狐*/
    -webkit-user-select:none; /*webkit浏览器*/
    -ms-user-select:none; /*IE10*/
    -khtml-user-select:none; /*早期浏览器*/
    user-select:none;
}
```

* 移动：

```css
.no-touch {
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}
```



## 渐变圆角边框

* 原因：Border-image: 可以实现渐变，但border-raduis 圆角属性，则会失效。
* 方案
  * 可以外套盒子padding实现该边框
* 提升：如果还要内容背景有透明度
  * 那只能用边框图片 (border-image) 切图了，降低了自适应能力。



## 渐变 gradients

* [CSS3 渐变（Gradients）| runoob](https://www.runoob.com/css3/css3-gradients.html)
* 



## 布局模式

###  圣杯布局和双飞翼布局

* [两边固定中间自适应布局](https://www.cnblogs.com/moumoon/p/11001641.html)



> 圣杯布局和双飞翼布局基本上是一致的，都是两边固定宽度，中间自适应的三栏布局，其中，中间栏放到文档流前面，保证先行渲染。解决方案大体相同，都是三栏全部float:left浮动，区别在于解决中间栏div的内容不被遮挡上，

>  圣杯布局是中间栏在添加相对定位，并配合left和right属性，效果上表现为三栏是单独分开的（如果可以看到空隙的话），

> 而双飞翼布局是在中间栏的div中嵌套一个div，内容写在嵌套的div里，然后对嵌套的div设置margin-left和margin-right，效果上表现为左右两栏在中间栏的上面，中间栏还是100%宽度，只不过中间栏的内容通过margin的值显示在中间。

![](..\images\css-layout-mode.png)



## BFC 

> block formatting context 
>
> 简单来说，BFC 就是一种属性，这种属性会影响着元素的定位以及与其兄弟元素之间的相互作用。
>
> 中文常译为块级格式化上下文。是 W3C [CSS](https://www.2cto.com/kf/qianduan/css/) 2.1 规范中的一个概念，它决定了元素如何对其内容进行定位，以及与其他元素的关系和相互作用。 在进行盒子元素布局的时候，BFC提供了一个环境，在这个环境中按照一定规则进行布局不会影响到其它环境中的布局。



* [什么是BFC?形成 BFC 的条件是什么？BFC常见作用详解](http://www.10qianwan.com/articledetail/61505.html)

* [margin重叠与穿透问题](https://www.cnblogs.com/rencoo/p/11628775.html)

### 特点

* BFC是一个绝对的独立空间，它的内部元素是不会影响到外部元素的



### 形成条件

* 浮动元素, float 除 none 以外的值;
* 绝对定位元素, position ( absolute, fixed, sticky)
* display 为 inline-block, table-cell, table-caption, flex, inline-flex;
* overflow 除了 visible 以外的值 ( hidden, auto, scroll )
* 根元素或包含根元素的元素
*  `display: flow-root` 一个新的 `display` 属性的值，它可以创建**无副作用的BFC**。在父级块中使用 可以创建新的BFC。



## 背景与背景图片

* [背景与背景图片覆盖范围](https://www.cnblogs.com/cbza/p/7206444.html?utm_source=itdadao&utm_medium=referral)
* Background-color : border+ padding +  width
* Background-image:  padding + width



## flex

* flex: 1;

  > flex-grow: 1; flex-shrink: 1;flex-basis: 0%;
  >
  > 实现平均分配空间

* flex: 1 1 auto;

  > 根据原来自身大小，按比例分配空间

* flex: 0;

  > flex-grow: 0; flex-shrink: 1; flex-basis: 0%;



## block, inline 元素的width, height, padding, margin

* block 

  * width, height, padding, margin  皆有效
  * width 默认 100%

* inline

  * width, height 无效，

  * **padding-left, padding-right 有效**

    padding-top, padding-bottom **空间布局上无效**，但**背景面积**会受到影响

  * **margin-left, margin-right 有效**

    margin-top, margin-bottom 无效



## border-radius

> border-radius的数值超块方形的边长时，圆形大小不变了？



## line-height

* [line-height | w3school](https://www.w3school.com.cn/cssref/pr_dim_line-height.asp)

* [line-height 垂直居中](https://www.cnblogs.com/huchong-bk/p/11504834.html)

| 值       | 描述                                                 |
| :------- | :--------------------------------------------------- |
| normal   | 默认。设置合理的行间距。                             |
| *number* | 设置数字，此数字会与当前的字体尺寸相乘来设置行间距。 |
| *length* | 设置固定的行间距。                                   |
| *%*      | 基于当前字体尺寸的百分比行间距。                     |
| inherit  | 规定应该从父元素继承 line-height 属性的值。          |

* 指定了一个缩放因子, 后代元素会继承这个缩放因子而不是计算值



## CSS3实现0.5px的边框

[CSS3实现0.5px的边框](https://www.cnblogs.com/sese/p/7067961.html)

* translate: scale(0.5, 0.5)



## calc

> calc() 函数用于动态计算长度值。

- 需要注意的是，运算符前后都需要保留一个空格，例如：`width: calc(100% - 10px)`；
- 任何长度值都可以使用calc()函数进行计算；
- calc()函数支持 "+", "-", "*", "/" 运算；
- calc()函数使用标准的数学运算优先级规则；



## 居中（不忘初心）





## 伪类::before ::after

* 创建在元素内部的前后与后面，p : before





## 选择器优先级

* 遵守就近原则  ： 内联样式表 > 内部样式表 > 外部样式表
* id 选择器  > 类选择器 > 标签选择器
* !important > 内联样式 > ID选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 元素选择器 = 关系选择器(子代，后代) = 伪元素选择器 > 通配符选择器 > 继承
* 样式代码，后来者居上，类名顺序无关。



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

* z-index : 非默认值auto;  如：z-index: 0;
* CSS3: transform , 如：tranform: scale(1);

###  补充

* 元素成为定位元素，其z-indoex就会自动生效，值为默认的auto
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











## position

> left、top等，百分比都根据其定位元素宽高

| 值       | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| absolute | 生成绝对定位的元素，相对于 `static` 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 没有, 则相对html 定位 |
| fixed    | 生成固定定位的元素，相对于`浏览器窗口`进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 |
| sticky   | 粘性定位; 该定位基于用户滚动的位置; 它的行为就像 position:relative; 而当页面滚动超出目标区域时，它的表现就像 position:fixed;，它会固定在目标位置。 |
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



| 选择器                                                       | 例子                  | 例子描述                                            |
| ------------------------------------------------------------ | --------------------- | --------------------------------------------------- |
| [:first-of-type](https://www.w3school.com.cn/cssref/selector_first-of-type.asp) | p:first-of-type       | 选择其父元素的第一个 p 子元素。对其对应标签的查找。 |
| [:last-of-type](https://www.w3school.com.cn/cssref/selector_last-of-type.asp) | p:last-of-type        | 选择其父元素的最后一个 p 子元素。                   |
| [:only-of-type](https://www.w3school.com.cn/cssref/selector_only-of-type.asp) | p:only-of-type        | 选择其父元素的p子元素仅一个的p元素                  |
| [:only-child](https://www.w3school.com.cn/cssref/selector_only-child.asp) | p:only-child          | 选择其父元素仅有一个子元素的 p 元素。               |
| [:nth-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-child.asp) | p:nth-child(2)        | 选择其父元素的第二个子元素。                        |
| [:nth-last-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-child.asp) | p:nth-last-child(2)   | 同上，从最后一个子元素开始计数。                    |
| [:nth-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-of-type.asp) | p:nth-of-type(2)      | 选择属于其父元素第二个 p 元素的每个 p 元素。        |
| [:nth-last-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-of-type.asp) | p:nth-last-of-type(2) | 同上，但是从最后一个子元素开始计数。                |
| [:last-child](https://www.w3school.com.cn/cssref/selector_last-child.asp) | p:last-child          | 选择属于其父元素最后一个子元素每个 <p> 元素。       |

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