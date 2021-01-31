# Vue SSR

## 文档 

* [Vue SSR 指南](https://ssr.vuejs.org/zh/#%E4%BB%80%E4%B9%88%E6%98%AF%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AB%AF%E6%B8%B2%E6%9F%93-ssr-%EF%BC%9F)



* 数据响应
  * 预取数据 pre-fetching
  * 禁用响应式数据（响应式没必要）

* 生命周期，只有
  * beforeCreate
  * Created
  * 避免在以上两个阶段中，产生全局副作用的代码，因为生命周期不完整，像没有destroy阶段，销毁定时器的代码，将不会被执行。所以可以在mounted中写副作用代码

* 自定义指令，要直接操作DOM

  * 使用 render functioin
  * 在创建服务器 renderer 时，使用 [`directives`](https://ssr.vuejs.org/zh/api/#directives) 选项所提供"服务器端版本(server-side version)"

  ```typescript
  // v-show 实现
  const renderer = createRenderer({
    directives: {
      show(node, dir) {
        if (!dir.value) {
          const style = node.data.style || (node.data.style = {});
          if (Array.isArray(style)) {
            style.push({ display: "none" });
          } else {
            style.display = "none";
          }
        }
      },
    },
  });
  ```

* router.onReady
  
  * ​	需提前解析路由异步配置，才能正确调用组件内部的路由钩子



## 数据预期与状态

## 服务器端数据预取 (Server Data Fetching)

*  使用 router.getMatchedComponents() 获取匹配组件，再调用 asyncData，更新状态，然后将解析完的状态，更新到渲染上下文（render context) 
* 在template ，context.state 将作为 `window.__INIT_STATE__ `注入html ,而在客户端，store 会挂载之前，获取到 `window.__INIT_STATE__ `
* 

### 客户端数据预取 (Client Data Fetching)



* 在路由导航之前解析数据
  * router.beforeResolve(): 所有组件被解析（包括异步组件）, 调用 asyncData
* 匹配要渲染的视图后，再获取数据
  * beforeMounted, beforeRouteUpdate ，调用 asyncData

## store 拆分

* 在asyncData中，使用 `store.registerModule` 惰性注册
* 在destroyed中，使用 `this.$store.unregisterModule('foo') `注销

## 客户端激活

* 根元素上添加标记属性 data-server-rendered

```html
<div id="app" data-server-rendered="true">
```

* 向 `$mount` 函数的 `hydrating` 参数位置传入 `true`

```js
// 强制使用应用程序的激活模式
app.$mount('#app', true)
```



## Bundle Renderer 

## 构建配置

### 手动资源注入(Manual Asset Injection)

* renderToString 回调函数中，你传入的 `context` 对象会暴露以下方法：
  * context.renderStyles()
  * context.renderState(options?: Object)
  * context.renderScripts()
  * context.renderResourceHints()
  * context.getPreloadFiles()

## CSS 管理

### 启用CSS 提取

* 使用`vue-loader` 的 `extractCSS` 选项（需要 `vue-loader` 12.0.0+）

### 从依赖模块导入样式

## Head 管理

### 标题管理

* 从 $options 上获取 title 数据

  ```js
  function getTitle (vm) {
    // 组件可以提供一个 `title` 选项
    // 此选项可以是一个字符串或函数
    const { title } = vm.$options
    if (title) {
      return typeof title === 'function'
        ? title.call(vm)
        : title
    }
  }
  ```

* 客户端或服务端 获取数据

```js
const serverTitleMixin = {
  created () {
    const title = getTitle(this)
    if (title) {
      this.$ssrContext.title = title
    }
  }
}

const clientTitleMixin = {
  mounted () {
    const title = getTitle(this)
    if (title) {
      document.title = title
    }
  }
}

// 可以通过 `webpack.DefinePlugin` 注入 `VUE_ENV`
export default process.env.VUE_ENV === 'server'
  ? serverTitleMixin
  : clientTitleMixin
```

* 在路由组件中， 混入

```js
  mixins: [titleMixin],
```

* 使用相同的策略，你可以轻松地将此 mixin 扩展为通用的头部管理工具 (generic head management utility)。

## 缓存

### 页面级缓存

```js
const microCache = LRU({
  max: 100,
  maxAge: 1000 // 重要提示：条目在 1 秒后过期。
})
```

### 组件级缓存

* 

```js
const LRU = require('lru-cache')

const renderer = createRenderer({
  cache: LRU({
    max: 10000,
    maxAge: ...
  })
})
```

* 设置 serverCacheKey 函数来判断是否使用缓存

```js
export default {
  name: 'item', // 必填选项
  props: ['item'],
  serverCacheKey: props => props.item.id,
  render (h) {
    return h('div', this.item.id)
  }
}
```

* 何时使用组件缓存
  * 不应该使用
    * 依赖全局状态的子组件
    * 对渲染上下文产生副作用的子组件
  * 小心使用组件缓存来解决性能瓶颈
    * 在大的 `v-for` 列表中重复出现的组件

```js
serverCacheKey: props => props.item.id + '::' + props.item.last_updated
```

## 流式渲染

* 

## 在非node.js环境中使用

* 

