# HTML5



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
