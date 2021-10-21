# HTML5



## svg

### 使用

* [使用SVG symbols建立图标系统](https://www.cnblogs.com/liangxuru/p/7159850.html)

```html
<body>
    <svg style="display: none;">
        <symbol viewBox="0 0 24 24" id="heart">
            <path fill="#E86C60" d="M17,0c-1.9,0-3.7,0.8-5,2.1C10.7,0.8,8.9,0,7,0C3.1,0,0,3.1,0,7c0,6.4,10.9,15.4,11.4,15.8 c0.2,0.2,0.4,0.2,0.6,0.2s0.4-0.1,0.6-0.2C13.1,22.4,24,13.4,24,7C24,3.1,20.9,0,17,0z"></path>
        </symbol>
    </svg>

    <svg>
        <use xlink:href="#heart"/> <!-- this is our visible icon -->
    </svg>
</body>
```



## input

* [input type="file"属性详解](https://www.w3h5.com/post/181.html)

* Ios 上传视频input, 设置capture="camcorder" ，系统可以直接调用摄像机

### img 的 alt 和 title

* alt是给搜索引擎识别，在图像无法显示时的替代文本
* title是关于元素的注释信息，主要是给用户解读



## 单页面与多页面间的区别及优缺点

* [单页面与多页面间的区别及优缺点 ](https://www.cnblogs.com/yunyea/p/8824178.html)



## 块级元素、行内元素

### 块级元素

> 一般都是从新行开始，它可以容纳行内元素和其他块元素

* div
* p 定义段落
* form
* h1-h6

* ol ul  li
* table tbody td th thead tr thead tfoot
* var 定义变量
* 

### 行内元素

> 一般只能容纳文本或者其他内联元素。

* span 组合文档中的行内元素

* a 链接 锚
* img
* label
* input textarea select
* abbr  缩写
* b big i strong  sub sup

* 

### 两者的区别





内联元素：

* 设置 width, height 属性无无效

* padding-left, padding-right 有边距效果,padding-top, padding-bottom，无边距效果，但会影响背景

* margin的left,rigth 会生效， top, bottom: 不会生效

* 块级元素会独占一行，其宽度自动填满其父元素宽度
  行内元素不会独占一行，相邻的行内元素会排列到同一行里，直到一行排不下，才会换行，其宽度随元素的内容变化而变化，

  
  
* 一般情况下，块级元素可以设置width,height属性，行内元素设置width,height无效

  ​	（注意，块级元素设置了width宽度属性后仍然是独占一行的）

* 块级元素可以设置margin,padding属性

  行内元素的水平方向的padding-left和padding-right都会产生边距效果，但是竖直方向上的padding-top和padding-bottom都不会产生边距效果
