# Vue 3





## new Proxy  & Object.defineProperty

* 两者单次执行只劫持 **对象本身**，不会劫持子对象的变化， 通过递归劫持内部所有对象。
* vue3 Proxy  在对象 **属性被访问** 时递归子对象执行 reactive, 是一种 **延迟** 定义子对象响应式的实现，性能优与 vue2,  vue2 的 Object.defineProperty 是在初始化阶段，即定义劫持对象时就已经递归执行了。



## initialVNode  & subTree

* initialVNode: 组件 vnode ,  如 ``<hello></hello> ``  所渲染生产的vnode
* subTree: 子树 vnode, Hello **组件内部** 整个Dom节点 经过 renderComponentRoot 渲染生成的 subTree



## 属性访问优先级

* setupState
* data
* props
* ctx