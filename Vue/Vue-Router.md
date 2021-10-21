# Vue-Router 

- router 对应路由的组件才可以触发 组件内守卫

## hash模式与history模式与实现

* [hash模式与history模式与实现 | 好文](https://www.cnblogs.com/8023-CHD/p/11383395.html)

* hash 模式

  ```js
  window.location.hash = 'qq' // 设置 url 的 hash，会在当前url后加上 '#qq'
   
  var hash = window.location.hash // '#qq' 
   
  window.addEventListener('hashchange', function(){
      // 监听hash变化，点击浏览器的前进后退会触发
  })
  ```

* history 模式

  ```js
  window.history.pushState(state, title, url)
  // state：需要保存的数据，这个数据在触发popstate事件时，可以在event.state里获取
  // title：标题，基本没用，一般传 null
  // url：设定新的历史记录的 url。新的 url 与当前 url 的 origin 必须是一樣的，否则会抛出错误。url可以是绝对路径，也可以是相对路径。
  //如 当前url是 https://www.baidu.com/a/,执行history.pushState(null, null, './qq/')，则变成 https://www.baidu.com/a/qq/，
  //执行history.pushState(null, null, '/qq/')，则变成 https://www.baidu.com/qq/
   
  window.history.replaceState(state, title, url)
  // 与 pushState 基本相同，但她是修改当前历史记录，而 pushState 是创建新的历史记录
   
  window.addEventListener("popstate", function() {
      // 监听浏览器前进后退事件，pushState 与 replaceState 方法不会触发             
  });
   
  window.history.back() // 后退
  window.history.forward() // 前进
  window.history.go(1) // 前进一步，-2为后退两步，window.history.lengthk可以查看当前历史堆栈中页面的数量
  ```

  

## 导航守卫

* 守卫是异步解析执行，此时导航在所有守卫 resolve 完之前一直处于 **等待中**。

  前置守卫 **确保要调用 next 方法，否则钩子就不会被 resolved。**

* 后置钩子 不会接受 `next` 函数也不会改变导航本身：

* ### 组件内的守卫

  - `beforeRouteEnter`

  - `beforeRouteUpdate` (2.2 新增)

  - `beforeRouteLeave`

  - 

    >`beforeRouteEnter` 守卫 **不能** 访问 `this`，因为守卫在导航确认前被调用,因此即将登场的新组件还没被创建。
    >
    >不过，你可以通过传一个回调给 `next`来访问组件实例。在导航被确认的时候执行回调，并且把组件实例作为回调方法的参数
    >
    >```javascript
    > next(vm => vm.setData(err, post))
    >```

* ### 完整的导航解析流程

1. 导航被触发。
2. 在失活的组件里调用离开守卫。
3. 调用全局的 `beforeEach` 守卫。
4. 在重用的组件里调用 `beforeRouteUpdate` 守卫 (2.2+)。
5. 在路由配置里调用 `beforeEnter`。
6. 解析异步路由组件。
7. 在被激活的组件里调用 `beforeRouteEnter`。
8. 调用全局的 `beforeResolve` 守卫 (2.5+)。
9. 导航被确认。
10. 调用全局的 `afterEach` 钩子。
11. 触发 DOM 更新。
12. 用创建好的实例调用 `beforeRouteEnter` 守卫中传给 `next` 的回调函数



## 注册路由的还原与增添

![][p0]

>vue-router 注册的路由信息都是存放在`matcher`之中的，所以当我们想清空路由的时候，我们只要新建一个空的`Router实例`，将它的`matcher`重新赋值给我们之前定义的路由就可以了。巧妙的实现了动态路由的清除。 
>
>**addRoutes** 可以动态挂载路由







[p0]: http://proudmodest.cn/img/vue/router.matcher.jpg

