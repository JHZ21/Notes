# mongodb

## 原子操作

> [ MongoDB 原子操作](https://www.runoob.com/mongodb/mongodb-atomic-operations.html)

### $inc

>对文档的某个值为数字型（只能为满足要求的数字）的键进行增减的操作。

```js
{ $inc : { field : value } }
```

### $unset

> 删除某个属性

```js
learnCards.updateMany({},{$unset: {__v: 0 }})
// __v:0 这属性值 0 随意
```