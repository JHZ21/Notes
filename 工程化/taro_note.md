# taro 笔记

* [Taro gaun 文档](https://taro-docs.jd.com/taro/ )

## Vue 

### 入口组件生命周期

* onLaunch()

> 程序初始化完成时

* created()

> 程序初始化完成时

* onShow()

> 程序启动，或从后台进入前台时
>
> 可以

* onHide()

> 前台进入后台

* onError(String error)
  * H5/RN 尚未实现

> 程序发生脚步错误或api调用报错

* onPageNotFound(Object)
  * 仅微信/字节小程序实现了

> 程序要打开的页面不存在时





### 页面组件生命周期

* onReady

> 访问真实dom, 调用 `createCanvasContext` 或 `createselectorquery` 等 API 

* onLoad(options)

> 可以调用 ``getCurrentInstance().router``

* created()

> 页面加载时，但视图层dom还没准备好

* mounted()

> 初次渲染时，可以与视图层dom交互

* beforeUpdate()

> 页面即将更新

* updated(prevProps, prevState)

> 页面更新完毕

* beforeDestory()

> 页面卸载时触发，如redirectTo, navigateBack

* onShow()

> 页面显示/切入前台时

* onHide()

> 页面隐藏/切入后台时触发，如navigateTo 或底部tab 切换页面，小程序切入后台

### getCurrentInstance

* getCurrentInstance().rounter 

> 在任何生命周期中，可以获取当前页面路径的参数

### 事件

* stopPropagation() 阻止事件冒泡

### 其他限制

* 无法使用Vue``transition-grounp ``组件

> 因为小程序访问元素位置为异步api

* 无法使用``<style scoped>`` , 

> 因为小程序不支持，建议使用cssModules代替

* 组件**id** 必须保持唯一性（即使他们在不同页面），否则可能导致事件 不触发问题

## 配置

### 入口文件配置

* pages
  * String[]
  * required

> 页面路径列表，路径中文件不需要后缀名

* window
  * ....

* tabBar
* networkTimeout
* debug
* subPackages
* workers
* requiredBackgroundModes
* plugins
* preloadRule
* resizable
* navigateToMiniProgramAppIdList

### Taro.getApp(Object)

> 获取App实例，均有实现

### 页面配置

> 只能配置全局配置中window的部分配置，且会覆盖相同配置项

### 页面说明

> 页面样式文件建议放在页面js同级目录下，然后使用**es6** ``import`` 引入，
>
> 支持css预编译器，目前提供了``sass`` 预编译插件``@tarojs/plugin-sass``, 需要自行本地安装。

## 项目配置 project.xx.json

* 

## 路由

> Taro，自带路由功能

* Taro.navigateTo 打开并跳转到新页面

```js
Taro.navigateTo({
  url: '/pages/page/path/name'
})
```

* Taro.redirectTo

```js
Taro.redirectTo({
  url: '/pages/page/path/name'
})
```

## 设计稿及尺寸单位

* 建议使用``px``, ``百分比 %``

> 因为Taro 默认对样式的所有单位进行转换。100px, 在微信小程序中转换为``100rpx``,
>
> h5会转为 ``rem``
>
> 写为``Px`` 或``PX`` , 则表示不被转换。

* 默认以宽度``750px`` 作为换算标准
  * 修改 config/index.js   ``designWidth`` 配置，来修改换算标准, 并在``deviceRatio``中添加对应的换算规则

```js
const config = {
  designWidth: 375,
  deviceRatio: {
    375: 2 / 1,
    640: 2.34 / 2,
    750: 1,
    828: 1.81 / 2,
  }
  ....
}
```

* Taro.pxTransform()

> 用于 js 设置的行内样式的单位换算

```js
Taro.pxTransform(10) // 小程序：rpx，H5：rem
```

* 配置

```js
// 默认配置
{
  onePxTransform: true,
  unitPrecision: 5,
  propList: ['*'],
  selectorBlackList: [],
  replace: true,
  mediaQuery: false,
  minPixelValue: 0
}
```

* css 编译时过滤（忽略）

  * 例子

  ```css
  // 多行文本省略
  .textHide {
    display: -webkit-box;
    -webkit-box-orient: vertical;  // 这行样式编译时，会被taro移除，所以要让taro编译时忽略这行样式，不做处理
    -webkit-line-clamp:2;
    text-overflow: ellipsis;
    overflow: hidden;
  }
  ```

  

  * 忽略单个属性，最简单方式

  > 使用大写px。

  * 忽略样式文件

  > 文件头部包含注释 `/*postcss-pxtransform disable*/` 
  >
  > 这样，插件将不进行处理转换

  * 忽略下一行 

  ```css
  /* autoprefixer: ignore next */
  -webkit-box-orient: vertical;
  ```

  * 忽略多行

  ```css
  /* autoprefixer: off */
  -webkit-box-orient: vertical;
  /* autoprefixer: on */
  ```

  * 写成行内样式

  ## 静态资源引用

  > Taro 可以向web pack一样自由地引用静态资源，而且不需要安装任何loaders
  >
  > 使用 ES6 语法 ``import`` 来引用文件

  * 小程序不能直接引用本地资源问题

  > 在小程序的样式中，默认不能直接引用本地资源，只能通过网络地址、Base64 的方式来进行资源引用，为了方便开发，Taro 提供了直接在样式文件中引用本地资源的方式，其原理是通过 `PostCSS` 的 [`postcss-url`](https://github.com/postcss/postcss-url) 插件将样式中本地资源引用转换成 Base64 格式，从而能正常加载。

## 多端开发	

### 跨平台开发

* 内置环境变量
  * process.env.TARO_ENV

```
 weapp / swan / alipay / h5 / rn / tt / qq / quickapp 
```

* 多端文件
  * test.js  默认文件，编译到微信，百度，h5之外的端
  * test.js / test.h5.js / test.weapp.js / teat.swan.js / test.qq.js / test.quickapp.js
  * 引用的方式依然和之前保持一致，`import` 的是不带端类型的文件名，在编译的时候会自动识别并添加 **端类型后缀**

  
* MultiPlatformPlugin

> Taro3 中用来解析多端文件
>
> 它是一个 [enhanced-resolve](https://github.com/webpack/enhanced-resolve) 插件，taro 内部会默认加载它。但插件默认不解析 node_modules 中的文件。

* 解析含多端文件的依赖

```js
// /config/index.js
// mini 也可改为 h5，分别对应小程序与 h5 端配置
mini: {
  webpackChain (chain) {
    chain.resolve.plugin('MultiPlatformPlugin')
      .tap(args => {
        return [...args, {
          include: ['@taro-mobile'] // 需要被解析的npm依赖包
        }]
      })
  }
}
```

