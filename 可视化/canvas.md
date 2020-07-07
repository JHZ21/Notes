# Canvas

> `<canvas>` 是 `HTML5` 新增的，一个可以使用脚本(通常为 `JavaScript`) 在其中绘制图像的 `HTML` 元素。它可以用来制作照片集或者制作简单(也不是那么简单)的动画，甚至可以进行实时视频处理和渲染。

* [学习 HTML5 Canvas 这一篇文章就够了 | runoob](https://www.runoob.com/w3cnote/html5-canvas-intro.html)
* [Canvas 对象 参考手册| w3cschool](https://www.w3cschool.cn/jsref/dom-obj-canvas.html)



## 安全限制

> 基于安全考量，HTML5 Canvas规范允许绘制不属于自己的(也就是其他域中的)图
> 像，然而，你不能通过CanvasAPI保存或修改其他域中的图像。



## 颜色、样式和阴影

| 属性                                                         | 描述                                       |
| :----------------------------------------------------------- | :----------------------------------------- |
| [fillStyle](https://www.w3cschool.cn/jsref/prop-canvas-fillstyle.html) | 设置或返回用于填充绘画的颜色、渐变或模式。 |
| [strokeStyle](https://www.w3cschool.cn/jsref/prop-canvas-strokestyle.html) | 设置或返回用于笔触的颜色、渐变或模式。     |
| [shadowColor](https://www.w3cschool.cn/jsref/prop-canvas-shadowcolor.html) | 设置或返回用于阴影的颜色。                 |
| [shadowBlur](https://www.w3cschool.cn/jsref/prop-canvas-shadowblur.html) | 设置或返回用于阴影的模糊级别。             |
| [shadowOffsetX](https://www.w3cschool.cn/jsref/prop-canvas-shadowoffsetx.html) | 设置或返回阴影与形状的水平距离。           |
| [shadowOffsetY](https://www.w3cschool.cn/jsref/prop-canvas-shadowoffsety.html) | 设置或返回阴影与形状的垂直距离。           |



| 方法                                                         | 描述                                      | 语法                                                         |
| :----------------------------------------------------------- | :---------------------------------------- | ------------------------------------------------------------ |
| [createLinearGradient()](https://www.w3cschool.cn/jsref/met-canvas-createlineargradient.html) | 创建线性渐变（用在画布内容上）。          | ctx.createLinearGradient(*x0,y0,x1,y1*)                      |
| [createPattern()](https://www.w3cschool.cn/jsref/met-canvas-createpattern.html) | 在指定的方向上重复指定的元素。            | ctx.createPattern(*image*,"repeat\|repeat-x\|repeat-y\|no-repeat") |
| [createRadialGradient()](https://www.w3cschool.cn/jsref/met-canvas-createradialgradient.html) | 创建放射状/环形的渐变（用在画布内容上）。 | *c*tx.createRadialGradient(*x0,y0,r0,x1,y1,r1*)              |
| [addColorStop()](https://www.w3cschool.cn/jsref/met-canvas-addcolorstop.html) | 规定渐变对象中的颜色和停止位置。          |                                                              |

## 线条样式

| 属性                                                         | 描述                                       | 语法                 |
| :----------------------------------------------------------- | :----------------------------------------- | -------------------- |
| [lineCap](https://www.w3cschool.cn/jsref/prop-canvas-linecap.html) | 设置或返回线条的结束端点样式。             |                      |
| [lineJoin](https://www.w3cschool.cn/jsref/prop-canvas-linejoin.html) | 设置或返回两条线相交时，所创建的拐角类型。 |                      |
| [lineWidth](https://www.w3cschool.cn/jsref/prop-canvas-linewidth.html) | 设置或返回当前的线条宽度。                 | ctx.lineWidth=number |
| [miterLimit](https://www.w3cschool.cn/jsref/prop-canvas-miterlimit.html) | 设置或返回最大斜接长度。                   |                      |



## 矩形

| 方法                                                         | 描述                           | 语法                             |
| :----------------------------------------------------------- | :----------------------------- | -------------------------------- |
| [rect()](https://www.w3cschool.cn/jsref/met-canvas-rect.html) | 创建矩形。                     | ctx.rect(x,y,width,height)       |
| [fillRect()](https://www.w3cschool.cn/jsref/met-canvas-fillrect.html) | 绘制"被填充"的矩形。           | ctx.fillRect(x,y,width,height)   |
| [strokeRect()](https://www.w3cschool.cn/jsref/met-canvas-strokerect.html) | 绘制矩形（无填充）。           | ctx.strokeRect(x,y,width,height) |
| [clearRect()](https://www.w3cschool.cn/jsref/met-canvas-clearrect.html) | 在给定的矩形内清除指定的像素。 | ctx.clearRect(x,y,width,height)  |

## 路径

| 方法                                                         | 描述                                                     | 语法                              |
| :----------------------------------------------------------- | :------------------------------------------------------- | --------------------------------- |
| [fill()](https://www.w3cschool.cn/jsref/met-canvas-fill.html) | 填充当前绘图（路径）。                                   |                                   |
| [stroke()](https://www.w3cschool.cn/jsref/met-canvas-stroke.html) | 绘制已定义的路径。                                       |                                   |
| [beginPath()](https://www.w3cschool.cn/jsref/met-canvas-beginpath.html) | 起始一条路径，或重置当前路径。                           |                                   |
| [moveTo()](https://www.w3cschool.cn/jsref/met-canvas-moveto.html) | 把路径移动到画布中的指定点，不创建线条。                 |                                   |
| [closePath()](https://www.w3cschool.cn/jsref/met-canvas-closepath.html) | 创建从当前点回到起始点的路径。                           |                                   |
| [lineTo()](https://www.w3cschool.cn/jsref/met-canvas-lineto.html) | 添加一个新点，然后在画布中创建从该点到最后指定点的线条。 |                                   |
| [clip()](https://www.w3cschool.cn/jsref/met-canvas-clip.html) | 从原始画布剪切任意形状和尺寸的区域。                     |                                   |
| [quadraticCurveTo()](https://www.w3cschool.cn/jsref/met-canvas-quadraticcurveto.html) | 创建二次贝塞尔曲线。                                     | ctx.quadraticCurveTo(cpx,cpy,x,y) |
| [bezierCurveTo()](https://www.w3cschool.cn/jsref/met-canvas-beziercurveto.html) | 创建三次贝塞尔曲线。                                     |                                   |

## 转换

| 方法                                                         | 描述                                               | 语法                              |
| :----------------------------------------------------------- | :------------------------------------------------- | --------------------------------- |
| [scale()](https://www.w3cschool.cn/jsref/met-canvas-scale.html) | 缩放当前绘图至更大或更小。                         | ctx.scale(scalewidth,scaleheight) |
| [rotate()](https://www.w3cschool.cn/jsref/met-canvas-rotate.html) | 旋转当前绘图。                                     | ctx.rotate(*angle*)               |
| [translate()](https://www.w3cschool.cn/jsref/met-canvas-translate.html) | 重新映射画布上的 (0,0) 位置。（重设原点(0,0)位置） | ctx.translate(*x,y*)              |
| [transform()](https://www.w3cschool.cn/jsref/met-canvas-transform.html) | 替换绘图的当前转换矩阵。                           | ctx.transform(*a,b,c,d,e,f*)      |
| [setTransform()](https://www.w3cschool.cn/jsref/met-canvas-settransform.html) | 将当前转换重置为单位矩阵。然后运行 transform()。   | ctx.setTransform(*a,b,c,d,e,f*)   |

## 文本

| 属性                                                         | 描述                                       | 语法                                         |
| :----------------------------------------------------------- | :----------------------------------------- | -------------------------------------------- |
| [font](https://www.w3cschool.cn/jsref/prop-canvas-font.html) | 设置或返回文本内容的当前字体属性。         | ctx.font="italic small-caps bold 12px arial" |
| [textAlign](https://www.w3cschool.cn/jsref/prop-canvas-textalign.html) | 设置或返回文本内容的当前对齐方式。         |                                              |
| [textBaseline](https://www.w3cschool.cn/jsref/prop-canvas-textbaseline.html) | 设置或返回在绘制文本时使用的当前文本基线。 |                                              |



| 方法                                                         | 描述                         | 语法                                |
| :----------------------------------------------------------- | :--------------------------- | ----------------------------------- |
| [fillText()](https://www.w3cschool.cn/jsref/met-canvas-filltext.html) | 在画布上绘制"被填充的"文本。 | ctx.fillText(text,x,y,maxWidth)     |
| [strokeText()](https://www.w3cschool.cn/jsref/met-canvas-stroketext.html) | 在画布上绘制文本（无填充）。 | ctx.strokeText(*text,x,y,maxWidth*) |
| [measureText()](https://www.w3cschool.cn/jsref/met-canvas-measuretext.html) | 返回包含指定文本宽度的对象。 |                                     |

## 图像绘制

| 方法                                                         | 描述                           | 语法 |
| :----------------------------------------------------------- | :----------------------------- | ---- |
| [drawImage()](https://www.w3cschool.cn/jsref/met-canvas-drawimage.html) | 向画布上绘制图像、画布或视频。 |      |

| 重载                                     | 语法                                                     |
| ---------------------------------------- | -------------------------------------------------------- |
| 在画布上定位图像                         | ctx.drawImage(*img,x,y*)                                 |
| 在画布上定位图像，并规定图像的宽度和高度 | ctx.drawImage(*img,x,y,width,height*)                    |
| 剪切图像，并在画布上定位被剪切的部分     | ctx.drawImage(img,sx,sy,swidth,sheight,x,y,width,height) |

* 图例

![drawImage.jpg](D:\Data\front-end\Notes\images\drawImage.jpg)

| 参数      | 描述                                         |      |
| :-------- | :------------------------------------------- | ---- |
| *img*     | 规定要使用的图像、画布或视频。               |      |
| *sx*      | 可选。开始剪切的 x 坐标位置。                |      |
| *sy*      | 可选。开始剪切的 y 坐标位置。                |      |
| *swidth*  | 可选。被剪切图像的宽度。                     |      |
| *sheight* | 可选。被剪切图像的高度。                     |      |
| *x*       | 在画布上放置图像的 x 坐标位置。              |      |
| *y*       | 在画布上放置图像的 y 坐标位置。              |      |
| *width*   | 可选。要使用的图像的宽度（伸展或缩小图像）。 |      |
| *height*  | 可选。要使用的图像的高度（伸展或缩小图像）。 |      |

## 像素操作

| 属性                                                         | 描述                                                  |
| :----------------------------------------------------------- | :---------------------------------------------------- |
| [width](https://www.w3cschool.cn/jsref/prop-canvas-imagedata-width.html) | 返回 ImageData 对象的宽度。                           |
| [height](https://www.w3cschool.cn/jsref/prop-canvas-imagedata-height.html) | 返回 ImageData 对象的高度。                           |
| [data](https://www.w3cschool.cn/jsref/prop-canvas-imagedata-data.html) | 返回一个对象，其包含指定的 ImageData 对象的图像数据。 |



| 方法                                                         | 描述                                                        | 语法                                                         |
| :----------------------------------------------------------- | :---------------------------------------------------------- | ------------------------------------------------------------ |
| [createImageData()](https://www.w3cschool.cn/jsref/met-canvas-createimagedata.html) | 创建新的、空白的 ImageData 对象。                           | ctx.createImageData(imageData)                               |
| [getImageData()](https://www.w3cschool.cn/jsref/met-canvas-getimagedata.html) | 返回 ImageData 对象，该对象为画布上指定的矩形复制像素数据。 | ctx.getImageData(x,y,width,height)                           |
| [putImageData()](https://www.w3cschool.cn/jsref/met-canvas-putimagedata.html) | 把图像数据（从指定的 ImageData 对象）放回画布上。           | ctx.putImageData(imgData,x,y,dirtyX,dirtyY,dirtyWidth,dirtyHeight) |

## 合成

| 属性                                                         | 描述                                     |
| :----------------------------------------------------------- | :--------------------------------------- |
| [globalAlpha](https://www.w3cschool.cn/jsref/prop-canvas-globalalpha.html) | 设置或返回绘图的当前 alpha 或透明值。    |
| [globalCompositeOperation](https://www.w3cschool.cn/jsref/prop-canvas-globalcompositeoperation.html) | 设置或返回新图像如何绘制到已有的图像上。 |

## 其他

| 方法          | 描述                             |
| :------------ | :------------------------------- |
| save()        | 保存当前环境的状态。             |
| restore()     | 返回之前保存过的路径状态和属性。 |
| createEvent() |                                  |
| getContext()  |                                  |
| toDataURL()   |                                  |



## 标准属性和事件

Canvas 对象同样支持标准 [属性](https://www.w3cschool.cn/jsref/dom-obj-all.html) 和 [事件](https://www.w3cschool.cn/jsref/dom-obj-event.html)。

------



## 相关文章

HTML 参考手册：[HTML  标签](https://www.w3cschool.cn/htmltags/tag-canvas.html)





## ctx.arc

> 绘制圆弧

* 语法

  ```js
  ctx.arc(x, y, r, startAngle, endAngle, anticlockwise)
  ```

  > 以`(x, y)` 为圆心，以`r` 为半径，从 `startAngle` 弧度开始到`endAngle`弧度结束。`anticlosewise` 是布尔值，`true` 表示逆时针，`false` 表示顺时针(默认是顺时针)





## ctx.artTo

> 圆润角：根据给定的控制点和半径画一段圆弧，最后再以直线连接两个控制点
>
> 其实绘制的圆弧就是与这两条直线相切的圆弧

* 语法

  ```js
  ctx.arcTo(x1, y1, x2, y2, radius)
  ```




## ctx.isPointInPath

> isPointInPath() 方法返回 true，如果指定的点位于当前路径中；否则返回 false。

* 语法

  ```js
  ctx.isPointInPath(x,y)
  ```

  

## ctx.clip

> 从原始画布中剪切任意形状和尺寸

* 语法

  ```js
  context.clip()
  ```

  