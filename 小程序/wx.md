# wx 微信小程序



## 生命周期

> js文件中定义了一些页面生命周期函数，下面简述下这些生命周期函数的方法作用

* onLoad：首次进入页面加载时触发，可以在 onLoad 的参数中获取打开当前页面路径中的参数。
*  onShow：加载完成后、后台切到前台或 重新进入页面时触发
*  onReady：页面首次渲染完成时触发
*  onHide：从前台切到后台或进入其他页面触发
*  onUnload：页面卸载时触发



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