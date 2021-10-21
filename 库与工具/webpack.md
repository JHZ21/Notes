# Webpack

> [webpack  中文文档](https://www.webpackjs.com/)



* [面试官：webpack原理都不会? | 掘金](https://juejin.im/post/6859538537830858759#heading-18)



## peerDependencies

* [探讨npm依赖管理之peerDependencies](https://www.cnblogs.com/wonyun/p/9692476.html)



* [带你深度解锁Webpack系列(基础篇)](https://juejin.im/post/5e5c65fc6fb9a07cd00d8838)

* [webpack4---生产环境css样式丢失问题](https://blog.csdn.net/qq_37800886/article/details/87856352)

  ```json
  // package.json
  "sideEffects": ["*.scss", "*.css"],
  ```

  

* devServer 

  > 只在 development 开发模式有效， 因为需要 webpack-dev-server支持， 所有生产环境，无法使用该属性

