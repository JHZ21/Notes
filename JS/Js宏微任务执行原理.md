# js执行原理

[Excues me?这个前端面试在搞事！](https://blog.csdn.net/sinat_36521655/article/details/80320519)

[这一次，彻底弄懂JavaScript执行机制](https://juejin.im/post/59e85eebf265da430d571f89)

[JavaScript的执行原理](https://blog.csdn.net/gy_u_yg/article/details/72869315)

[Tasks, microtasks, queues and schedules]( https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/ )  文章里的可交互动画太强了

 [图解搞懂 JavaScript 引擎 Event Loop —— 掘金](https://juejin.im/post/5a6309f76fb9a01cab2858b1) （图解更详细，逻辑上，也讲透了一些点）



[微任务、宏任务、同步、异步、Promise、Async、await](https://www.cnblogs.com/jiangyuzhen/p/11064408.html)





* 微任务执行时，产生新的微任务，会投入队列，并按序执行它
* 主程序执行一遍，执行**全部**微任务，执行**一个**宏任务，执行全部微任务，执行一个宏任务



### **宏任务**

| #                     | 浏览器 | Node |
| --------------------- | ------ | ---- |
| setTimeout            | √      | √    |
| setInterval           | √      | √    |
| setImmediate          | x      | √    |
| requestAnimationFrame | √      | x    |
| MessageChannel        | √      |      |
| postMessage           | √      |      |
| setImmediate          | √      |      |

* 异步请求
* UI rendering
* 事件绑定 addEventListener

* [MessageChannel是什么，怎么使用 | 简书](https://www.jianshu.com/p/4f07ef18b5d7)
* 

### **微任务**

| #                          | 浏览器 | Node |
| -------------------------- | ------ | ---- |
| process.nextTick           | x      | √    |
| MutationObserver           | √      | x    |
| Promise.then catch finally | √      | √    |
|                            |        |      |
|                            |        |      |

### async await

> 旦遇到await 就立刻让出线程,阻塞后面的代码
>
> 等候之后,对于await来说分两种情况



* 不是promise 对象

> await func();
>
> func 会执行, 但await 会阻塞async 函数内 后续代码,先执行async 外的同步代码,同步代码执行完毕后,在回到async内部,把promise的东西,作为await表达式的结果
>
> 微任务.

* 是promise对象

> 它等到的是一个 promise 对象，await 也会暂停async后面的代码，先执行async外面的同步代码，等着 Promise 对象 fulfilled，然后把 resolve 的参数作为 await 表达式的运算结果。



### UI渲染

>  **宏任务** > 微任务> UI渲染 > **宏任务** > ...



# Node

[Node.js中的执行顺序（微任务与事件循环）](https://blog.csdn.net/xgangzai/article/details/89647029)

事件循环最阶段最详细的讲解:  [nodejs事件循环 | 官网](https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/#setimmediate-vs-settimeout)

* timers阶段

  次阶段包括setTimeout()和setInterval()

* IO callbacks

  大部分的回调事件，普通的caollback

* poll阶段

  网络连接，数据获取，读取文件等操作

* check阶段

  setImmediate()在这里调用回调

* close阶段
  一些关闭回调，例如socket.on(‘close’, …)
