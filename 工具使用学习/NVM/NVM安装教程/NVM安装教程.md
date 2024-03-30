# windows下通过nvm安装node(内含卸载node)

[JuvenileAndSea](https://juejin.cn/user/4080986139408637/posts)

日常开发中有时候会维护多个项目，随着时间跨度的增加而我们前端技术又日新月异，不可避免有些项目是不同的node版本依赖。这个时候我们就想要是有一个node的版本切换(管理)工具那就好了，事实上的确有那么一个工具那就是[nvm](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fcoreybutler%2Fnvm-windows)

#### 一.如果你已经安装了node，那么你需要先卸载node，如果你没有安装那直接跳过这一步到下一步

1.先看看我们是否安装了node，打开你的终端输入

```js
js
复制代码node -v
```

![查看否安装了node](image/4bc687c2bb274888b3b5fb182c77dfcatplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

2.打开控制面板=>打开程序和功能=>右上角搜索输入node

![程序和功能中找到node](image/ac87a3b7ad6c4652bc586ed78df6b86ctplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

3.找到之后右键卸载

![卸载node](image/ebe0f4bc74724acdbb09c4a6f56ebf8dtplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

再次查看node

```js
js
复制代码node -v
```

![再次查看node](image/87b3bfcbc0ae4bbda95a9269eed9739dtplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

4.可以看到node已经被卸载了，但是别慌为了确保彻底删除node在看看你的node安装目录默认是C:\Program Files中还有没有node文件夹，有的话一起删除

5.再看看C:\Users\用户名 文件夹下有没有.npmrc以及.yarnrc等等统统删除

6.再去看看你的环境变量有没有node相关的，有的话也一起删除了

#### 二.安装nvm

1.去github下载最新的[nvm](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fcoreybutler%2Fnvm-windows%2Freleases)找到nvm-setup.zip点击下载

![github的nvm](image/0fbbd55f04b44f4798ea645a72e4f5b8tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

2.解压缩安装

![安装包](image/d21a1941d92348c7a2447b9d27dcac8btplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

3.双击安装，最好让他安装到默认路径

![nvm安装路径](image/c861ed6510144448ae9a67974d17dfb0tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

4.选择node安装路径

![node安装路径](image/1b65a1cd76924e29ab0736c2e85a2b11tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

5.安装结束

![安装结束](image/9fa5e435c6374d3fad78ad528a9eab37tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

6.在终端中查看是否安装成功

```js
js
复制代码nvm version
```

成功出现版本号那么恭喜你安装nvm成功

![nvm](image/97b41da8d12443a097b4375f451321d1tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

#### 三.安装node

1.打开[node官网](https://link.juejin.cn/?target=https%3A%2F%2Fnodejs.org%2Fzh-cn%2F)查看最新版本复制一下最新版本号

![node官网](image/5830c114a75c47e789288306f3f83cf3tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

2.安装你复制的node版本

```js
js
复制代码nvm install 14.15.1
```

![安装node失败](image/a0513b15dde74b61873ecf49657461f0tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

3.可以看到安装失败了，因为这个资源我们访问失败了，不要着急接下来打开我们的nvm安装目录找到settings.txt

![找到setting](image/864ecb766c9944549f1873af6627753etplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

4.双击打开在后面添加淘宝的源地址，然后保存

```js
js复制代码node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

![setting.text](image/06ecedbad6c448128eb53999b3a2d7aftplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

5.再次尝试安装node

![再次安装node](image/06c5030e3d3d4eb4a858c101567f3f22tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

6.查看nvm中的node列表

```js
js
复制代码nvm list
```

![node列表](image/6924dfdc5b5f41d4839843053f5804f5tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

7.切换node版本nvm use 后面跟版本号就行

```js
js
复制代码nvm use 14.15.1
```

![切换node版本](image/aa9453f5f0554c6da39f542df537f682tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

8.再次查看nvm中的node列表，可以看见版本号前面有一个* 号，这个*号就是你当前的node版本

```js
js
复制代码nvm list
```

![再次查看node列表](image/6371d9b56ece44f0856662c11b08a94btplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

9.查看当前的node版本以及npm版本，可以看到我们现在的node是14.15.1 npm是6.14.8

```js
js复制代码node -v
npm -v
```

![查看当前的node版本以及npm版本](image/254982446d98448bb3328fa709c8b965tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

10.去node官网查看，这里我们复制了10.12.0的版本号[历史版本](https://link.juejin.cn/?target=https%3A%2F%2Fnodejs.org%2Fzh-cn%2Fdownload%2Freleases%2F) ![node历史版本](image/85998306608f4cf9a1449f98c2cc3616tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

10.安装10.12.0版node

```js
js
复制代码nvm install 10.12.0
```

![安装10.12.0版本node](image/8f3fad93a19f4a6db3211d11e8030893tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

12.查看现在的node列表

![查看现在的node列表](image/4ccd6ef65e2141d3a01dab6904493333tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

13.切换node版本为10.12.0，并查看node列表可以看到10.12.0的前面多了一个*

![切换node版本为10.12.0](image/e12e2f5f1b1042b9901e4059859d6408tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

![查看node列表](image/03a1de6d186e40bfa35b021a13f9686ftplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

14.验证当前node版本以及npm版本，可以看到以及成功node切换到10.12.0 npm到6.4.1

![验证当前node版本](image/b8408f1dbe564c33a863dac97c3ddfa0tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

#### 这样就通过nvm成功安装node自己想要的版本了，切可以随时切换node版本。再也不用担心别人让我们维护老掉牙的项目而我们却没有对应版本的node了





# Node.js 统一全局模块安装路径配置

## 1. nvm下载

## 2. nvm常用的几个命令

![img](image/webp.webp)

**修改nvm下载源**
 在nvm目录中找到 setting.txt 添加以下代码

```ruby
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

## 3. npm管理(pnpm同npm)

使用 nvm 时，默认的 prefix 是当前激活的 Node.js 版本的安装路径。
 带来一个问题是：切换版本之后，之前安装全局命令模块需要重新安装，非常不方便。
 解决方案是配置统一的全局模块安装路径。
 新建npm_global和npm_cache文件夹，分别用于npm包的全局安装路径和全局cache路径

**npm查看各种全局路径的命令**

- 查看当前npm包的全局安装路径

```swift
npm prefix -g 
```

- 查看当前npm包的全局cache路径

```csharp
npm config get cache
```

- 查看配置列表

```undefined
npm config ls
```

- 查看配置列表的全部信息

```undefined
npm config ls -l
```

**npm修改全局路径命令**

- 修改npm的包的全局安装路径

```swift
npm config set prefix "D:\Program Files\DevTools\npm\node_global"
```

- 修改npm的包的全局cache位置

```bash
npm config set cache "D:\Program Files\DevTools\npm\node_cache"
```

**配置环境变量**

- 将npm包全局安装路径配置在环境变量中

此电脑 -> 属性 -> 高级系统设置 -> 环境变量 -> 系统变量 -> path ->编辑 - > 新增路径 - D:\Program Files\DevTools\npm\node_global（路径可以根据npm prefix -g查看）

![img](image/webp-1711771319309-3.webp)

**注意pnpm环境变量配置**

![img](image/webp-1711771329557-6.webp)

## 4. yarn管理

**安装yarn**
 yarn的默认缓存和存储包的路径都在C盘，所以最好在安装后也进行修改

**yarn查看各种路径命令**

- 查看 yarn 全局bin位置(prefix)

```csharp
yarn global bin
```

- 查看 yarn 全局安装位置(folder)

```csharp
yarn global dir
```

- 查看 yarn 全局cache位置(cache)

```undefined
yarn cache dir
```

- 查看配置列表

```cpp
yarn config list
```

**yarn修改路径命令**

- 改变 yarn 全局bin位置(prefix)

```swift
yarn config set prefix "D:\Program Files\DevTools\npm\yarn_global\bin"
```

- 改变 yarn 全局安装位置(folder)

```csharp
yarn config  set global-folder "D:\Program Files\DevTools\npm\yarn_global"
```

- 改变 yarn 全局cache位置(cache)

```bash
yarn config set cache-folder "D:\Program Files\DevTools\npm\yarn_cache"
```

**配置环境变量**
 将 D:\Program Files\DevTools\node.js\yarn_global 添加到环境变量的path变量中，若该目录下自动生成了bin目录，则添加 D:\Program Files\DevTools\node.js\yarn_global\bin 到环境变量中





作者：刺猬丶
链接：https://www.jianshu.com/p/f5a7cedba59b
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。