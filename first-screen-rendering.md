## 骨架屏

* [vue骨架屏实践](https://www.jianshu.com/p/eacac700630e)
* [Vue页面骨架屏注入实践](https://segmentfault.com/a/1190000014832185)

* [浅谈script标签中的async和defer](https://www.cnblogs.com/jiasm/p/7683930.html)



## script

### defer 和 async

* 正常script脚本加载&执行的过程中，会阻塞`DOM`渲染

* 添加`async`和`defer`，这两个属性使得`script` 的加载不会阻塞`DOM`的渲染

* defer , 使得script在文档渲染完毕后再统一执行，并在严格安装原来先后顺序执行，script执行完，再调用DOMContentLoaded事件

* async, script 会异步的加载并在允许的情况下执行，

  script加载完就会执行，顺序不管先后，但script执行，当然还是会中断文档渲染，

  DOMContentLoaded的调用，不会理会async script，

#### 应用场景

* defer

  > 适用于你的脚本代码依赖于页面中的`DOM`元素（文档是否解析完毕），或者被其他脚本文件依赖。

  * 评论框
  * 代码语法高亮
  * `polyfill.js`

* async

  > 适用于你的脚本并不关心页面中的`DOM`元素（文档是否解析完毕），并且也不会产生其他脚本需要的数据。

  * 百度统计
  * 不太确定时, 用`defer`会比`async`稳定, 能保证script执行时，dom已经渲染完，而且可以保证脚本的执行顺序



