# mongodb



## $unset

> 删除某个属性

```js
learnCards.updateMany({},{$unset: {__v: 0 }})
// __v:0 这属性值 0 随意
```