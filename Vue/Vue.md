# Vue 2.x

* [Vue.js 源码揭秘 ｜ 失效](https://ustbhuangyi.github.io/vue-analysis/)
* [30 道 Vue 面试题，内含详细讲解（涵盖入门到精通，自测 Vue 掌握程度）| 掘金](https://juejin.im/post/5d59f2a451882549be53b170)
* [手撕vue源码](https://github.com/canfoo/self-vue)

* [揭秘 Vue2 九个性能优化技巧](https://juejin.cn/post/6922641008106668045)





## vue 项目

* Vue核心技术 Vue+Vue-Router+Vuex+SSR实战精讲（无密版）

>链接: https://pan.baidu.com/s/1ts0-Cip4IInss28QjGkOWQ 提取码: be4y 复制这段内容后打开百度网盘手机App，操作更方便哦

* [vue-typescript-admin](https://armour.github.io/vue-typescript-admin-docs/zh/guide/#%E5%8A%9F%E8%83%BD)

* 幕客书城项目

> 链接: https://pan.baidu.com/s/1FN1K5RfytkFLM3fMOj91pQ 提取码: faxm 复制这段内容后打开百度网盘手机App，操作更方便哦

* Vue2.5开发去哪儿网App 从零基础入门到实战项目

> 链接: https://pan.baidu.com/s/1F32ys86-r7tnDOgZmPUVPw 提取码: gs6w 复制这段内容后打开百度网盘手机App，操作更方便哦

* Vue.js 源码全方位深入解析

> 链接: https://pan.baidu.com/s/1YB0_cwoZsvkox8TEDoqMmw 提取码: 4bhf 复制这段内容后打开百度网盘手机App，操作更方便哦

* 从基础到实战 手把手带你掌握新版Webpack4

>  链接: https://pan.baidu.com/s/1Tqf4RTQCy8GZ5BPu1Hgelw 提取码: npbj 复制这段内容后打开百度网盘手机App，操作更方便哦



## Vue.use & install

> Vue.use(A) , 就是 A.install(Vue)

```js
const component = {
    install:function(Vue){
        Vue.component('component-name',component)
    }  
}
// 导出该组件
export default component
```



## $nextTick





## Vue 虚拟dom (vdom)

* [虚拟dom](https://www.jianshu.com/p/af0b398602bc)
* 优势
* 首先是抽象，引入 vnode，可以把渲染过程抽象化，从而使得组件的抽象能力也得到提升。
* 其次是跨平台，因为 patch vnode 的过程不同平台可以有自己的实现，基于 vnode 再做服务端渲染、Weex 平台、小程序平台的渲染都变得容易了很多。
* 解决浏览器性能问题





# Vue 使用 函数调用组件 的方法

* [Vue 使用 函数调用组件 的方法](https://blog.csdn.net/dongcehao/article/details/104798097)

  

* 

# 实现对数组的监听

* [Object.defineProperty是如何实现对数组的监听](https://blog.csdn.net/lyh6665/article/details/107929324)
* 重写`Array`的原型方法



## diff  原理

* [详解vue的diff算法](https://www.cnblogs.com/wind-lanyan/p/9061684.html)

* 同层级比较

> 在采取diff算法比较新旧节点的时候，比较只会在同层级进行, 不会跨层级比较(不会比较children)

* 预判

> 首尾双指针比较
>
> `oldCh`和`vCh`各有两个头尾的变量`StartIdx`和`EndIdx`，它们的2个变量相互比较，一共有4种比较方式。如果4种比较都没匹配，如果设置了`key`，就会用`key`进行比较，在比较的过程中，变量会往中间靠，一旦`StartIdx>EndIdx`表明`oldCh`和`vCh`至少有一个已经遍历完了，就会结束比较。



## 双向绑定原理与实现

* [vue的双向绑定原理及实现 ｜ good](https://www.cnblogs.com/chenhuichao/p/10818396.html)
* 



## v-bind

* v-bind="obj"  传入 键值对

  > 传入对象，方便设置多个属性，子组件需用prop 接收

* V-bind:name = "value" 传入值 



## SSR vs Prerendering 

* [Vue.js 服务器端渲染指南](https://ssr.vuejs.org/zh/)

* 如果你使用 webpack，你可以使用 [prerender-spa-plugin](https://github.com/chrisvfritz/prerender-spa-plugin) 轻松地添加预渲染。



## 父子生命周期顺序

* [vue 父子组件的生命周期顺序](https://www.cnblogs.com/status404/p/8733629.html)

### 一、加载渲染过程

```repl
父beforeCreate->父created->父beforeMount->子beforeCreate->子created->子beforeMount->子mounted->父mounted
```

### 二、子组件更新过程

```repl
父beforeUpdate->子beforeUpdate->子updated->父updated
```

### 三、父组件更新过程

```repl
父beforeUpdate->父updated
```

### 四、销毁过程

```repl
父beforeDestroy->子beforeDestroy->子destroyed->父destroyed
```



## 组件间通信

>[前端面试之Vue中组件通信的方式 | 掘金](https://juejin.im/post/5e7f18706fb9a03c300f7caa)

* prop / $emit

  * 可以实现父子通信

  * 父子组件间数据传递, 有较特殊需求时，使用$refs, 直接调用子组件方法，属性，更加简便。props 和  $emit 能力有局限性。（如 限制: 传递的props 不能被修改）

    当然也可以使用Vuex

* .sync

  * 语法糖，增加实现子传父功能， 已达到所谓的同步

  * 单向：内部prop值不能自己主动改变，应该通过emit改变父组件prop，来改变子组件得到的值

  * 子组件通过 $emit("update:prop"， val)

  > ```vue
  > // 父组件内
  > <child :visible.sync="dialogVisible"></child>
  > || ||
  > \/ \/
  > <child :visible="dialogVisible" @update:visible="val => visible=val"></child>
  > ```
  >
  > ```js
  > //Child.vue
  > 
  > func(val) {
  > 	this.$emit('update:visible', val)
  > }
  > ```

  

* attrs / listeners

  > [vm.$attrs](https://cn.vuejs.org/v2/api/#vm-attrs)
  >
  > [vm.$listeners](https://cn.vuejs.org/v2/api/#vm-listeners)

  * 实现跨级通信，即父孙组件通信

  * 中间组件(子组件) 需要使用 `v-bind="$attrs" v-on="$listeners" `将属性与监听事件放下去

    > 就`中间组件`要有所处理，然后父孙就可以，通过像父子通信的方式通信
    >
    > 使用 $attrs ，传递属性
    >
    > 使用 $listeners , 传递事件

    ```vue
    //child.vue
    <template>
        <GrandChild v-bind="$attrs" v-on="$listeners"></GrandChild>
    </template>
    
    ```

    

* provide inject

* EventBus

* vuex

* $refs

* parent children







## slot 插槽

> [插槽 | 官网](https://cn.vuejs.org/v2/guide/components-slots.html)

* 具名插槽

```vue
// 父组件
<base-layout>
  <template v-slot:header>
    <h1>Here might be a page title</h1>
  </template>

  <p>A paragraph for the main content.</p>
  <p>And another one.</p>

  <template v-slot:footer>
    <p>Here's some contact info</p>
  </template>
</base-layout>

// 子组件
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>

```











### 父子组件数据传递

> 



## 变量命名

> because properties starting with "$" or "_" are not proxied in the Vue instance to prevent conflicts with Vue internals. 
>
> 不让以 $ 或者 _ 开头， 避免与内部属性冲突



## template

* 内不能引用普通函数，只能用自身的Vue的methods, datas等



## .native 事件修饰符

> 想在某个`组件`的根元素上监听一个原生事件。可以使用 `v-on` 的修饰符 .native 
>
> 就是在父组件中给子组件绑定一个原生的事件，就将子组件变成了普通的HTML标签，不加'. native'事件是无法触 发的。
>
> [vue中 '. native' 修饰符的使用](https://blog.csdn.net/qq_29468573/article/details/80771625)



## 生命周期

|   生命周期   | 响应类型                                                     |
| :----------: | ------------------------------------------------------------ |
| beforeCreate | 拿不到任何信息，无法篡改数据，一般做loding，这个时候的vue实例还什么都没有，但是$route对象是存在的，可以根据路由信息进行重定向之类的操作 |
|   created    | $el，没有初始化，数据已加载完成，阔以篡改数据，并更新，不会触发，，在这结束，还做一些初始化，实现函数自执行，ref属性内容为空数组 |
| beforeMount  | $el已被初始化,，数据已加载完成，阔以篡改数据，并更新，不会触发beforeUpdate，updated，在挂载开始之前被调用，beforeMount之前，会找到对应的template，并编译成render函数 |
|   mounted    | $el，已被初始化，数据已加载完成，阔以篡改数据，并更新，并且触发，，在这发起后端请求，拿回数据，配合路由钩子做一些事情，ref属性可以访问 |







## 传同步值，可以prop 传个对象

> 利用对象属性，同源，达到同步效果



## mixins

> 默认规则如下

* data 冲突，取组件的

* 钩子函数 和 watch （如，created）冲突,  `混用`

  混入对象先调用，组件再调用

* methods 、components 和 directives， 冲突时，取组件的

> 混入规则，可以自定义
>
> ```js
> Vue.config.optionMergeStrategies.myOption = function (toVal, fromVal) {
>   // 返回合并后的值
> }
> ```





## computed

>  当计算属性最终计算的值发生变化才会触发重新渲染
>
>  计算属性是属性，不能加（） 
>
>  method 需要加 （）



### (ts)响应属性(data)不赋初值，则视图层不会响应！！

```javascript
// lang=ts  
steps_objs: StepsObjType[] = [] // 数据修改时，视图面可以响应
 steps_objs!: StepsObjType[]  // 无初值， 则未监听，导致视图无响应
```

详情可看文章最后总结 [TypeScript显式赋值断言导致Vue属性非响应](https://blog.csdn.net/HermitSun/article/details/90386504)



## :key

> 使得数组元素对应的dom, 不会被复用。
>
> 使用有特征的，不会被被重复，如id,  或者 自己生成随机数，
>
> 不能用 index, 数组下标， dom仍会被复用



## 不要随意在别人的组件 slot 放元素，否则可能出奇怪的bug



##  prop：avoid mutating abug prop directly 

> since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value.
>
> * 不要直接重写prop的值,  若要重写， 应使用基于prop 值 的 data 或 computed 属性
> * 也不能赋默认值





## [使用函数便捷导入多个组件 代码](https://github.com/chrisvfritz/vue-enterprise-boilerplate/blob/master/src/components/_globals.js)



## watch

> 通过 $watch API 创建的侦听器 watcher 会返回一个 unwatch 函数，你可以随时执行它来停止这个 watcher 对数据的侦听
>
> 对于 watch 选项创建的侦听器，它会随着组件的销毁而停止对数据的侦听。

```javascript
watch:{
       a:{
           //执行的函数
           // 普通函数里的this 指向ueComponent对象, ()=>{} 箭头函数的this总是指向词				法作用域，也就是外层调用者obj。 所以用箭头函数，无法直接通过this获取vue对象
           handler: "print",  
           // 默认false,  true 时立即执行，即创建时也会执行一次函数    
           immediate: true,
           // 默认false, 只是浅监听一层，为true，则深度监听(许多层，及二层及以上的属性)，里面任何值变化，都			会执行函数    
           deep: true
       }
  },
```

```
  

   
* ## $attrs 和 $listeners

* ### .sync

  ![][p0]

  > props: 使得 foo -> bar , 父组件的值foo 流向子组件的值bar
  >
  > this.$emit("updata:foo", newValue) 使得, 子组件foo的新值, 通过函数复制给父组件的bar





[p0]:http://proudmodest.cn/img/vue/sync.jpg


```

```javascript
// vue数据层次太多，render函数没有自动更新慢
	Vue.set(object, key, value)

/*  this.$forceUpdate()虽然能解决但问题并不出现在这里.vue虽然是响应式的.但受到javascript的限制，Vue不能检测到对象属性的添加或删除，因为vue在初始化实列时将属性转为getter/setter，所以属性必须在data对象上才能让vue转换它。可以使用 Vue.set(object, key, value)方法将响应属性添加到嵌套的对象上.实现改变数据自动渲染 */
```



## ref

>ref 可以绑定元素对象，但当使用v-for时， 同一个 ref 绑定了 多个item时，只能通过数组形式来访问各个item，即

```javascript
this.$refs.itemRef[0];
this.$refs.itemRef[1];
.......
```

## ref.xxx  undefined

> 需要等待组件创建完毕，否则无法获得组件对象
>
> 可以调用时，判断下是否存在





