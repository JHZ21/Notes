# Vuex



## dispatch

> 调用 mutation
>
> ```js
> this.$store.dispatch('fnc', value)
> ```



## commit 

> 调用 action
>
> ```js
> this.$store.dispatch('fnc', value)
> ```





# Vuex + Typescript



## 调用关系

#### Mutation 和 Getter 里不能调用 Vuex里的异步函数

> 但可以调用外部的(异步)函数

### Action  可以调用 Action、Mutation、Getter







## 普通函数无效

> 必须是@Mutation, @Action
>
> 请给函数，添加合适的装饰器



##  @Action 

> 异步，如果想要返回值，请使用 async await (推荐)