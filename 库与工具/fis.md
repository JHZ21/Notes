## fis3 构建

* [fis3文档](https://fis.baidu.com/fis3/index.html)

- fis-conf.js 配置文件
  - fis3 release -d <path>  构建发布路径
  - fis.match 匹配文件

```
fis.match(selector, props);
```

- - fis.meida  匹配运行环境，如生成环境

```
fis.media('prod').match('*.js', {

  optimizer: fis.plugin('uglify-js')

});
```

