# wx 微信小程序



## rpx 单位

> rpx（responsive pixel）: 可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx。如在 iPhone6 上，屏幕宽度为375px，共有750个物理像素，则750rpx = 375px = 750物理像素，1rpx = 0.5px = 1物理像素。



## 组件之间样式影响

### options.styleIsolation

> 设置自身组件的样式影响规则

* isolated  默认值

> class样式只由自身组件决定， 且自定义组件内外，使用 class 指定的样式将不会相互影响

* apply-shared

> 只有 **页面 wxss** 样式和设置了shared的组件 将影响到自身组件, 而自定义组件 wxss 样式不会影响页面
>
> * 



* shared 

> **页面 wxss**  样式会影响到自身组件。
>
> **自身组件 wxss** 中指定的样式也会影响页面和其他设置了 **apply-shared**  或 **shared** 的自定义组件。（这个选项在插件中不可用）
>
> 并可覆盖父组件样式。

* 页面 page 默认 shared



### externalClasses

> 组件可以接受外部传入的样式类

```js
externalClasses: ['my-class']
```



## event  bind & trigger

* Bind:  tap 事件 与 onTap 函数

```html
<!-- 在自定义组件中 -->
<button bindtap="onTap">点击这个按钮将触发“myevent”事件</button>
```

*  函数 与 triggerEvent

```js
 methods: {
    onTap: function(){
      var myEventDetail = {} // detail对象，提供给事件监听函数
      var myEventOption = {} // 触发事件的选项
      this.triggerEvent('myevent', myEventDetail, myEventOption)
    }
```

* eventOption

| 选项名       | 类型    | 是否必填 | 默认值 | 描述                                                         |
| :----------- | :------ | :------- | :----- | :----------------------------------------------------------- |
| bubbles      | Boolean | 否       | false  | 事件是否冒泡                                                 |
| composed     | Boolean | 否       | false  | 事件是否可以穿越组件边界，为false时，事件将只能在引用组件的节点树上触发，不进入其他任何组件内部 |
| capturePhase | Boolean | 否       | false  | 事件是否拥有捕获阶段                                         |



## selectComponent

* 参数：一个匹配选择器 `selector`

```js
this.selectComponent(".my-component")
```

* 自定义设置 组件的 selectComponet 返回值





## 生命周期

> 组件自身的一些函数, 在特殊的时间点或遇到一些特殊的框架事件时被自动触发。

### lifetimes

| 生命周期 | 参数           | 描述                                     |
| :------- | :------------- | :--------------------------------------- |
| created  | 无             | 在组件实例刚刚被创建时执行               |
| attached | 无             | 在组件实例进入页面节点树时执行           |
| ready    | 无             | 在组件在视图层布局完成后执行             |
| moved    | 无             | 在组件实例被移动到节点树另一个位置时执行 |
| detached | 无             | 在组件实例被从页面节点树移除时执行       |
| error    | `Object Error` | 每当组件方法抛出错误时执行               |

### pageLifetimes

| 生命周期 | 参数        | 描述                         |
| :------- | :---------- | :--------------------------- |
| show     | 无          | 组件所在的页面被展示时执行   |
| hide     | 无          | 组件所在的页面被隐藏时执行   |
| resize   | object Size | 组件所在的页面尺寸变化时执行 |



## Page(Object object)

注册小程序中的一个页面。接受一个 `Object` 类型参数，其指定页面的初始数据、生命周期回调、事件处理函数等。

#### 参数

##### Object object

| 属性                                                         | 类型     | 默认值 | 必填 | 说明                                                         |
| :----------------------------------------------------------- | :------- | :----- | :--- | :----------------------------------------------------------- |
| [data](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#data) | Object   |        |      | 页面的初始数据                                               |
| [onLoad](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onLoad-Object-query) | function |        |      | 生命周期回调—监听页面加载                                    |
| [onShow](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onShow) | function |        |      | 生命周期回调—监听页面显示                                    |
| [onReady](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onReady) | function |        |      | 生命周期回调—监听页面初次渲染完成                            |
| [onHide](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onHide) | function |        |      | 生命周期回调—监听页面隐藏                                    |
| [onUnload](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onUnload) | function |        |      | 生命周期回调—监听页面卸载                                    |
| [onPullDownRefresh](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onPullDownRefresh) | function |        |      | 监听用户下拉动作                                             |
| [onReachBottom](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onReachBottom) | function |        |      | 页面上拉触底事件的处理函数                                   |
| [onShareAppMessage](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onShareAppMessage-Object-object) | function |        |      | 用户点击右上角转发                                           |
| [onShareTimeline](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onShareTimeline) | function |        |      | 用户点击右上角转发到朋友圈                                   |
| [onAddToFavorites](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onAddToFavorites-Object-object) | function |        |      | 用户点击右上角收藏                                           |
| [onPageScroll](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onPageScroll-Object-object) | function |        |      | 页面滚动触发事件的处理函数                                   |
| [onResize](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onResize-Object-object) | function |        |      | 页面尺寸改变时触发，详见 [响应显示区域变化](https://developers.weixin.qq.com/miniprogram/dev/framework/view/resizable.html#在手机上启用屏幕旋转支持) |
| [onTabItemTap](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onTabItemTap-Object-object) | function |        |      | 当前是 tab 页时，点击 tab 时触发                             |
| 其他                                                         | any      |        |      | 开发者可以添加任意的函数或数据到 `Object` 参数中，在页面的函数中用 `this` 可以访问 |