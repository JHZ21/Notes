# vs code 经验



## 重启vs code 

> 打开：“命令面板”  :  `CTRL + SHITF + P`
>
> ```
> > Reload Window
> ```



## 预览Markdown

> 快捷键： `Ctrl + k  v`



## REST Client

>REST Client allows you to send HTTP request and view the response in Visual Studio Code directly.

> 在 xxx.txt 、 xxx.http  等文件内（只有格式不会报错） , 编写请求
>
> ``` http
> https://example.com/comments/1
> ```
>
> ``` http
> POST https://example.com/comments HTTP/1.1
> content-type: application/json
> 
> {
>     "name": "sample",
>     "time": "Wed, 21 Oct 2015 18:27:50 GMT"
> }
> ```
>
> 使用快捷键： `Ctrl+Alt+R`  ( `Cmd+Alt+R` for macOS)
>
> 即可在直接在编辑器内，看到response 内容



##  代码格式化配置

### 因地制宜(good!)

> 本地 .eslintrs.js +Prette 

* 不同项目可以本地生成 .eslintrc.js

  ```
  npm install eslint -g  // 全局安装
  eslint --init // 根据选择生成规则文件.eslintrc.js
  ```

* eslint 和 Prettier 插件安装好

* setttings.json配置项

  ```json
   // 格式化安装eslint规则
  "prettier.eslintIntegration": true,  
   // 保存时自动修复所有错误
  "editor.codeActionsOnSave": {
      "source.fixAll.eslint": true
  },  
  ```

* [vscode同时开两个前端项目，如何分别使用不同的eslint配置文件](https://segmentfault.com/q/1010000015798246)

* [vscode里面怎么根据eslint来格式化代码？](https://www.zhihu.com/question/52777843)





### settings.jon: vs code 配置文件

### 

>用于格式化( 快捷键: alt + shift + f )配置，与保存时自动修复设置
>
>此配置，Vetur 不用作格式化，只显示vue颜色
>
>

>！！！
>
>在保存时自动修复错误，按 .eslintrc.js 的规则， 没有格式化能力
>
>```json
>"editor.codeActionsOnSave": {
>    "source.fixAll.eslint": true
>  },
>```



```json
/* settings.json */

{
  "editor.detectIndentation": false,
  "editor.tabSize": 2,
  "terminal.integrated.rendererType": "dom",
  /* 文件格式化配置 */
  /* 重点！ 文件格式化选择的工具，在多个工具时，记得配置为相应工具，否则将导致该工具配置失效。*/
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[vue]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  /* 在保存时自动格式化：true */
  "editor.formatOnSave": true,
  /* eslint, 在保存时自动修复错误：true */
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  /* 分号：false */
  "prettier.semi": false,
  // // 单引号：false
  "prettier.singleQuote": false,
  /* 让函数(名)和后面的括号之间加个空格 */
  "javascript.format.insertSpaceBeforeFunctionParenthesis": false
}
```



### 项目内的 .eslintrc.js

> 只用于格式检测，并提示，没有格式化文件能力。

```javascript
/* .eslintrc.js */

module.exports = {
  root: true,
  env: {
    node: true
  },
  // extends: ["plugin:vue/essential", "@vue/prettier", "@vue/typescript"],
  extends: ["plugin:vue/essential", "@vue/typescript"],
  rules: {
    "no-console": process.env.NODE_ENV === "production" ? "error" : "off",
    "no-debugger": process.env.NODE_ENV === "production" ? "error" : "off",
    semi: ["error", "never"]
  },
  parserOptions: {
    parser: "@typescript-eslint/parser"
  }
}

```



### 项目内的  settings.json

>即 .vscode > settings.jon
>
>优先级高于vs code 里的配置，相当于本地配置，便于本地化与项目搬运时，格式配置不变。



### 项目里 .prettierrc 

> 用于质量检查

```json
//  .prettierrc

{
  "semi": false,
  "prettier.singleQuote": false
}
```



## js读取本地文件

>  读取本地文件，如json ,限制跨域问题

### 方法一，修改浏览器配置

### 方法二，安装  ```Debugger for Chrome``` 插件

>  f5 修改chrome配置文件，f5启动插件
>
> （安全性更高，随用随开)
>
> [VS Code - Debugger for Chrome调试js](https://www.cnblogs.com/mxk-star/p/7279785.html)
>
> [Vscode+Chrome调试直接读取本地文件解决方案](http://www.manongjc.com/article/36297.html)





