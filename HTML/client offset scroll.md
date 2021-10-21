# client offset  scroll 

+ client 

  - clientTop:   border-top-width    元素上边框的厚度， 默认无border 则为0 
  - clientLeft :  border-left-width
  - clientHeight：  内容可视区域的宽度，不包含border, 不包含滚动条（除非它是不占居它空间，不属于它，如手机滚动条悬浮在上面）
  - clientWidth: 与上面类似

  

+ offset

  - offsetTop:  

    > 自身border外到父元素的border-top的下边缘  
    >
    > （自身的（top + margin-top） + 父元素的padding-top ）
    >
    > 获取对象相对于由offsetParent属性指定的父坐标(css定位的元素或body元素)距离顶端的高度。

  + offsetHeight:  width + padding + border

    > 获取对象相对于由offsetParent属性指定的父坐标(css定位的元素或body元素)的高度。
    >
    > IE、Opera 认为 offsetHeight = clientHeight + 滚动条 + 边框。
    >
    > FF 认为 offsetHeight 是网页内容实际高度，可以小于 clientHeight。
    >
    > offsetHeight在新版本的FF和IE中是一样的，表示网页的高度，与滚动条无关，chrome中不包括滚动条。

  

+ scroll

  + scrollTop: 	对象最顶端到窗口中可见内容的最顶端的距离，即滚动后被隐藏的高度。

  - scrollHeight:     对象内容实际高度

    > IE、Opera 认为 scrollHeight 是网页内容实际高度，可以小于 clientHeight。
    >
    > NS、FF 认为 scrollHeight 是网页内容高度，不过最小值是 clientHeight。

  

+ clienY:    

  相对于浏览器窗口可视区域的Y坐标（窗口坐标），可视区域不包括工具栏和滚动条。IE事件和标准事件都定义了这个属性。

  

+ screenY:  

  相对于用户显示器屏幕左上角的X,Y坐标。标准事件和IE事件都定义了这2个属性

  

+ pageY:  

   类似于event.clientY，但它们使用的是文档坐标而非窗口坐标。这个属性不是标准属性，但得到了广泛支持。IE事件中没有这个属性。

  

+ offsetY:  

  相对于事件源元素（target或srcElement）的X,Y坐标，只有IE事件有这个属性，标准事件没有对应的属性。

  





参考:

[js中的各种“位置”——“top、clientTop、scrollTop、offsetTop……"](https://blog.csdn.net/sdta25196/article/details/81195433)

