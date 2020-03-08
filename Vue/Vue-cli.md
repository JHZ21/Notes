

# Vue-cli



## 访问静态文件



### 相对路径

> html 直接写相对路径

```html
<img src="../assets/xxx.png" alt="">  
<!-- 编译后，会自动对应打包后的文件路径 --> 
```



### require()

> js使用require() 去请求文件

```javascript
data() {
    return {
        src:require("../assets/xxx.png)"
    }
}  
```



### CSS url 导入图片

* url( 相对路径 )

* url("~@/assets/test.png")  

  >~ : 示意使用别名, 如 @ ,  `~` 的前缀来避免歧义。



### public 文件夹

>public 文件夹 不用经过webpack打包，只是简单复制转移。

``` 
<%= BASE_URL %>  默认，开发时：'/' ，生产模式 '' (''+reset.css 相当于’./reset.css')
```



