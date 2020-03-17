# CSS



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