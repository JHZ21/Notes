# npm



### [手把手教你用npm发布包](https://blog.csdn.net/taoerchun/article/details/82531549) 

> 按教程来，vue init ...
>
> webpack.config.js 配好，入出口等等，paskage.json 的main等
>
> 改version 才能提交，
>
> 最后，dist要有。别人引用直接读dist里现成的。



## npm install

- npm  生产与开发依赖的安装

* * npm i -s xxxx   本地安装生成依赖  /  npm i -S xxx   /  npm i --save xx

* npm i -D xxxx 本地安装开发依赖  /  npm i --save-dev xxx

* npm 查看已安装包

  - 查看当前项目的依赖模块如下：

    npm ls --depth 0

  - 查看全局依赖模块命令如下：

    npm ls -g --depth 0

    

## npm registry

```
设置淘宝的是：
npm config set registry https://registry.npm.taobao.org


不想用他们的，再设置回原来的就可以了：

npm config set registry https://registry.npmjs.org
```



* npm ERR! exited with error code: 128

```
git config --global url."https://".insteadOf git://
再 npm install 
```

