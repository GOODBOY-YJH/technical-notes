# npm 和 yarn 换源

作为前端开发者我们经常会使用npm或yarn，我们都知道npm和yarn默认镜像在国外，国内访问这些镜像速度会比较慢，下面介绍修改npm和yarn源的方法

## 一. npm和yarn源的简单修改（以淘宝镜像为例）

### npm

###### 1. 临时修改（只生效一次）

```cpp
npm install 包的名字 --registry https://registry.npm.taobao.org
```

###### 2. 设置npm的配置项（全局配置）

查看npm源的当前地址

```csharp
npm config get registry
```

设置淘宝镜像

```cpp
npm config set registry https://registry.npm.taobao.org
```

### yarn

###### 1. 临时修改（只生效一次）

```cpp
yarn save 包的名字 --registry https://registry.npm.taobao.org/
```

###### 2. 设置yarn的配置项（全局配置）

查看yarn源的当前地址

```csharp
yarn config get registry
```

设置淘宝镜像

```cpp
yarn config set registry https://registry.npm.taobao.org/
```

## 二. 使用第三方软件快速修改、切换 npm和yarn的源（以淘宝镜像为例）

### （1）分别修改npm和yarn源（经实际测试，这种方法修改一个源另一个源也会同时修改）

### npm

nrm 是一个 NPM 源管理器，允许你快速地在如下 NPM 源间切换

###### 安装

```undefined
npm install -g nrm
```

###### 列出可选的源

```cpp
nrm ls

* npm ---- https://registry.npmjs.org/
  cnpm --- http://r.cnpmjs.org/
  taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
  rednpm - http://registry.mirror.cqupt.edu.cn/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
```

带 * 的是当前使用的源

###### 切换

切换到taobao镜像源

```cpp
nrm use taobao

   Registry has been set to: https://registry.npm.taobao.org/
```

###### 测试源的响应时间

测试所有源的响应时间：

```jsx
nrm test

  npm ---- 2930ms
  cnpm --- 300ms
* taobao - 292ms
  nj ----- Fetch Error
  rednpm - Fetch Error
  npmMirror  1626ms
  edunpm - Fetch Error
```

可以多次测量来得到更精确的结果
更多nrm使用方法访问nrm的gitHub仓库
[https://github.com/Pana/nrm](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FPana%2Fnrm)

### yarn

yrm 是一个 yarn源管理器，允许你快速地在yarn源间切换

###### 安装

```undefined
npm install -g yrm
```

###### 列出可选的源

```cpp
yrm ls

  npm ---- https://registry.npmjs.org/
  cnpm --- http://r.cnpmjs.org/
* taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
  rednpm - http://registry.mirror.cqupt.edu.cn/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
  yarn --- https://registry.yarnpkg.com
```

带 * 的是当前使用的源

###### 切换

切换到taobao镜像源

```cpp
yrm use taobao

   YARN Registry has been set to: https://registry.npm.taobao.org/
```

###### 测试源的响应时间

测试所有源的响应时间：

```jsx
yrm test

  npm ---- 784ms
  cnpm --- 290ms
* taobao - 297ms
  nj ----- Fetch Error
  rednpm - Fetch Error
  npmMirror  1353ms
  edunpm - Fetch Error
  yarn --- Fetch Error
```

可以多次测量来得到更精确的结果
更多yrm使用方法访问yrm的gitHub仓库
[https://github.com/i5ting/yrm](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fi5ting%2Fyrm)

## （2）使用双源管理工具cgr （特感谢[缤纷扫落叶](https://www.jianshu.com/u/eca29647fc48)推荐）

###### 安装

```undefined
npm install -g cgr
```

使用方法和前两种差别不大，下边附上使用方法网址
[https://www.npmjs.com/package/cgr](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2Fcgr)

【参考文章】
https://www.jianshu.com/p/309645729b2e
[http://www.16boke.com/article/detail/154](https://links.jianshu.com/go?to=http%3A%2F%2Fwww.16boke.com%2Farticle%2Fdetail%2F154)
[https://laravel-china.org/articles/15976/yarn-accelerate-and-modify-mirror-source-in-china](https://links.jianshu.com/go?to=https%3A%2F%2Flaravel-china.org%2Farticles%2F15976%2Fyarn-accelerate-and-modify-mirror-source-in-china)
[https://www.npmjs.com/package/cgr](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2Fcgr)

