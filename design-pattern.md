# design-pattern



* [design-pattern | github | jhz21](https://github.com/JHZ21/design-pattern)
* 

* [观察者模式和发布订阅模式的区别 | 简书](https://www.jianshu.com/p/594f018b68e7)
* [设计模式（三）：观察者模式与发布/订阅模式区别](https://www.cnblogs.com/lovesong/p/5272752.html)
* 



## 观察者模式

> 订阅者与发布者之间是存在依赖 ， 分而散

* Subject 对象
  * observers: 存储 observer : Array
  * add() : 添加 observer
  * remove() : 移除 observer
  * notify() : 通知所有observer update
* Observer 对象
  * update() : 更新操作



## 发布-订阅

> 统一由调度中心调度的， 大而统

* PubSub 对象
  * subscribers : 存储 subscriber 对象们 :  { [ event] :  function[] }
  * subscribe() : 订阅 event,  传入 callback
  * unsubscribe() : 解除订阅
  * pulish() : 发布 event, 传入参数 , 遍历调用 cbs

