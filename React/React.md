# React



## react 常见setState的原理解析

* [react 常见setState的原理解析 | 简书](https://www.jianshu.com/p/1e7e956ec1ee)

### batch update 批量更新



#### setState

- 在官方的描述中，setState操作并不保证是同步的，也可以认为是异步的。
- React在setState之后，会经对state进行diff，判断是否有改变，然后去diff dom决定是否要更新UI。
- 在短时间内频繁setState。React会将state的改变压入栈中，在合适的时机，批量更新state和视图，达到提高性能的效果。

### setState 参数  function

> 在setState的第一个参数中传入function，该function会被压入调用栈中，在state真正改变后，按顺序回调栈里面的function。该function的第一个参数为上一次更新后的state。这样就能确保你下一次的操作拿到的是你预期的值