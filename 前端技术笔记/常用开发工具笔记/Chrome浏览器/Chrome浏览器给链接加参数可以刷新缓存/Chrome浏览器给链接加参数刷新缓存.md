### 部署到CDN等服务器上的页面，可能会因为刷新问题，仍旧访问到上一次上传的页面缓存

#### 可以使用给页面链接加参数的方式获取最新上传的页面

例如：

https://xxxxxx.com/xxxx/index.html 

给页面链接后拼接一个随机参数，就可以强制获取最新的页面

https://xxxxxx.com/xxxx/index.html?x=9897