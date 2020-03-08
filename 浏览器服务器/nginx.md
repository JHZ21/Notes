# nginx 



## nginx 的反向代理

> ### 充当中转服务器 ，简易又轻松的  前端跨域  手段
>
> ####  操作原理：将本地运行的项目域与服务器域相同，原理如下图

![nginx][p0]



### 代码实现（nginx.conf)

```nginx
server {

        listen      80; #监听80端口，可以改成其他端口

        server_name  localhost; # 当前服务的域名

        #charset utf-8;

        #access_log  logs/host.access.log  main;

        location / {

            proxy_pass http://localhost:81;

            proxy_redirect default;

        }

		location /apis { #添加访问目录为/apis的代理配置

		rewrite  ^/apis/(.*)$ /$1 break;

		proxy_pass  http://localhost:82;

      }
}
```

* 当用户发送localhost:80/时会被nginx转发到http://localhost:81服务；
* 当界面请求接口数据时，只要以/apis 为开头，就会被nginx转发到后端接口服务器上；
* 总结：nginx实现跨域的原理，实际就是把web项目和后端接口项目放到一个域中，这样就不存在跨域问题，然后根据请求地址去请求不同服务器（真正干活的服务器）；
* 



##  命令

*  nginx - t    #测试配置文件

*  nginx  -s  reload     #当配置信息修改，需要重新载入这些配置时使用此命令

*  nginx  -v   查看Nginx的版本号

*  start nginx  启动Nginx

*  nginx -s stop  快速停止或关闭Nginx

*  nginx -s quit  正常停止或关闭Nginx



## nginx 文件配置

```nginx
server {
    	
		listen 80;  #是对locahost监听的端口
   		
    	server_name www.hello.com; #监听的域名 
    
		charset UTF-8;
    
		location / {
			
			proxy_pass http://proudmodest.cn/;  # 返回内容的地址，可以继续添加加端口等

			proxy_set_header Host $host;

			proxy_set_header X-Real-IP $remote_addr;

		}
    
}
```



## server_name 

* 有用，可以用于区分同一个端口的不用域名的请求。使得端口可以重复利用，如 port 80；
* 域名解析，需配合hosts文件，否则访问不到
* 如果有bug，失效。 可能是启动了多个nginx程序，被旧的程序覆盖了，需清理多余程序



## hosts 文件

~~~host
	127.0.0.1	www.hello.com  # 设置该域名的ip地址，使其访问localhost，hosts优先于DNS
~~~





## [Nginx 初探](https://juejin.im/entry/5d9a925f6fb9a04e2e4b099f)



## [Nginx详解（正向代理、反向代理、负载均衡原理）](https://blog.csdn.net/tsummerb/article/details/79248015)  

> 正向代理，自建vpn



## [Nginx的配置文件详解 (超详细)](https://blog.csdn.net/wangbin_0729/article/details/82109693)





[p0]:   http://proudmodest.cn/img/nginx01.webp

