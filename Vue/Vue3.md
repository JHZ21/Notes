# Vue 3

* [v3中文文档](https://v3.cn.vuejs.org/guide/introduction.html)

* [你可以手写Vue3的响应式原理吗？| 掘金 ｜前端森林](https://juejin.cn/post/6921530159099510791#comment)





## Computed

* 函数
  * 标准化函数: getter, setter
  * 创建副作用函数runner: 对getter做了一层封装
  * 创建computed对象并返回：该对象的getter会根据是否dirty来执行runner, 并做依赖收集，setter设置newValue
* 特点（空间换时间的优化思想）
  * 延迟计算：当我们访问计算属性时，才会真正运行输入的getter函数
  * 缓存：缓存上次的计算结果value(闭包)，只有当dirty为true, 才重新计算结果value 。



![vue3-computed](../images/Vue3/vue3-computed.png)

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



## watch 侦听器

* watch api
  * () => reactive()
  
    > 侦听一个 getter 函数,返回一个响应式对象: () => state.count

  * ref() 
  
    > 侦听一个响应式对象: count
  
  * [ref(), ref(), ...]
  
    > 侦听多个响应式对象: [count, count2]
  
* doWatch
  * 标准化 source 
  * 构造 applyCb 回调函数 
  * 创建 scheduler 时序执行函数 
  *  创建 effect 副作用函数 
  *  返回侦听器销毁函数 

* Watch 减少 traverse 次数

  * 侦听 state.count.a.b

  ```js
  // 
  watch(state.count.a, (newVal, oldVal) => { 
    console.log(newVal) 
  }) 
  // 更优
  watch(() => state.count.a.b, (newVal, oldVal) => { 
    console.log(newVal) 
  }) 
  ```

  

## 生命周期

```
beforeCreate -> 使用 setup() 
created -> 使用 use setup() 
beforeMount -> onBeforeMount 
mounted -> onMounted 
beforeUpdate -> onBeforeUpdate 
updated -> onUpdated 
beforeDestroy-> onBeforeUnmount 
destroyed -> onUnmounted 
activated -> onActivated 
deactivated -> onDeactivated 
errorCaptured -> onErrorCaptured
```

* 不要在 updated 钩子函数中更改数据，因为这样会再次触发组件更新，导致无限递归更新 。

* 新增 调试钩子

```
onRenderTracked 
onRenderTriggered
```



## Provide/inject

* Provide/inject和模块化差别

| 差异            | provide/inject                           | 模块化                           |
| --------------- | ---------------------------------------- | -------------------------------- |
| 作用域{}        | 局部作用域，注入后只有子孙节点可以发访问 | 全局作用域，可以在任何地方导入   |
| 数据来源不同    | 依赖注入，无需关心来源，只管注入即可     | 需要知道在哪个模块定义，而去导入 |
| 上下文不同 this | 组件实例，不同组件可以provide不同数据    | 没有上下文，但可以传参context    |

* 特点
  * 依赖注入与组件上下文关系 强相关，滥用将使重构变得困难
  * 推荐：与子孙组件上下文联系紧密时使用，在简单的层级重构时，仍能被正确访问（比 this.$parent 更通用）

## Composition Api & Mixin

* 都是逻辑复用的工具

* 但 Composition Api 更显示地表明数据的注入，

```html
<script> 
  import useMousePosition from './mouse' 
  export default { 
    setup() { 
      const { x, y } = useMousePosition() 
      return { x, y } 
    } 
  } 
</script>
```



## 模块解析：构造AST

### 解析template生成AST

* template =>

```html
<div class="app"> 
  <!-- 这是一段注释 --> 
  <hello> 
    <p>{{ msg }}</p> 
  </hello> 
  <p>This is an app</p> 
</div
```

* => AST
  * AST对象根节点

```json
// AST对象根节点：虚拟节点，不会映射到一个具体节点
{
  type: 0,
  children: [...],
  helpers: [],
  components: [],
  directives: [],
  hoists: [],
  imports: [],
  cached: 0,
  temps: 0,
  loc: {
    start: {
      column: 1,
      line: 1,
      offset: 0
    },
    end: {
      column: 7,
      line: 7,
      offset: 108
    },
    source:
      '<div class="app">\n  <!-- 这是一段注释 -->\n  <hello>\n    <p>{{ msg }}</p>\n  </hello>\n  <p>This is an app</p>\n</div>'
  }
}
```

* 一个node节点的AST对象

  | ast 字段 | 描述                 |
  | -------- | -------------------- |
  | type     | 节点的类型           |
  | tag      | 节点的标签           |
  | props    | 节点的属性           |
  | loc      | 节点对应代码相关信息 |
  | children | 向它的子节点对象数组 |

```json
// '<p>{{ msg }}</p>' 的AST对象
{
   type: 1,
   ns: 0,
   tag: 'p',
   tagType: 0,
   props: [],
   isSelfClosing: false,
   children: [
     {
       type: 5,
       content: {
         type: 4,
         isStatic: false,
         isConstant: false,
         content: 'msg',
         loc: {
           start: {
             column: 11,
             line: 4,
             offset: 56
           },
           end: {
             column: 14,
             line: 4,
             offset: 59
           },
           source: 'msg'
         }
       },
       loc: {
         start: {
           column: 8,
           line: 4,
           offset: 53
         },
         end: {
           column: 17,
           line: 4,
           offset: 62
         },
         source: '{{ msg }}'
       }
     }
   ],
   loc: {
     start: {
       column: 5,
       line: 4,
       offset: 50
     },
     end: {
       column: 21,
       line: 4,
       offset: 66
     },
     source: '<p>{{ msg }}</p>'
   }
 }
```

* **baseParse(content, options = {}) **

  ```js
  function baseParse(content, options = {}) { 
      // 创建解析上下文 
      const context = createParserContext(content, options)
      const start = getCursor(context) 
      // 解析子节点，并创建 AST  
      return createRoot(parseChildren(context, 0 /* DATA */, []), getSelection(context, start))
  } 
  ```
  * 创建解析上下文
    * createParserContext 
  * 解析子节点
    * parseChildren
      * parseComment
      * parseInterpolation  解析插值
      * parseText 
      * parseElement
        * parseTag
        * parseChildren => 递归...
      * ... ....
  * 创建 AST 根节点
    * createRoot





### AST转换



### 生成代码





## 实现原理

### props 

