# go

* [go 入门介绍](https://studygolang.com/articles/21513)
* [go | 官网](https://golang.org/)

* [go | 中文文档](http://docscn.studygolang.com/doc/)

* [golang标准库中文文档](https://studygolang.com/pkgdoc)



## 安装go

* Mac 
  * 下载 http://docscn.studygolang.com/doc/install
  * vi ~/.bash_profile    添加环境变量

  ```
  export GOROOT=/usr/local/go
  export GOPATH=/Users/bytedance/Desktop/learning/go_project
  export PATH=$PATH:$GOROOT/bin
  ```

  * ```
    source  ~/.bash_profile   // 生效
    ```

  * ```
     go version    // 是否成功
     go env  
    ```



## func

![function-syntax](../images/go/function-syntax.png)



## := 

> 声明+赋值

```go
message := fmt.Sprintf("Hi, %v. Welcome!", name)
// 等于, 变量类型为右边结果类型
var message string
message = fmt.Sprintf("Hi, %v. Welcome!", name)
```

