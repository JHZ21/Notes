# axios



## 跨域时, 默认不携带cookie





## use async/await

```js
// Want to use async/await? Add the `async` keyword to your outer function/method.
async function getUser() {
  try {
    const response = await axios.get('/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
!!! : async 函数调用时记得, 因为它也是异步等待， 要用await,才能真正同步
let data = await getUser()
```