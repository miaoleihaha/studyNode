# Npm run 原理

#### [npm](https://so.csdn.net/so/search?q=npm&spm=1001.2101.3001.7020) run xxx 发生了什么

按照下面的例子npm run dev 举例过程中发生了什么

![https://img-blog.csdnimg.cn/img_convert/636ec321a584c30616b43054fd2816f3.png](https://img-blog.csdnimg.cn/img_convert/636ec321a584c30616b43054fd2816f3.png)

读取package json 的scripts 对应的脚本命令(dev:vite),vite是个可执行脚本，他的查找规则是：

1. 先从当前项目的node_modules/.bin去查找可执行命令vite

2. 如果没找到就去全局的node_modules 去找可执行命令vite
3. 如果还没找到就去环境变量查找
4. 再找不到就进行报错

如果成功找到会发现有三个文件

![https://img-blog.csdnimg.cn/img_convert/22713e4ef20da7b15eac11acf1c3168c.png](https://img-blog.csdnimg.cn/img_convert/22713e4ef20da7b15eac11acf1c3168c.png)

###### 因为nodejs 是跨平台的所以可执行命令兼容各个平台

- .sh文件是给Linux unix Macos 使用
- .cmd 给windows的cmd使用
- .ps1 给windows的powerShell 使用

#### npm 生命周期

```js
    "predev": "node prev.js",
    "dev": "node index.js",
    "postdev": "node post.js"
```

执行 npm run dev 命令的时候 predev 会自动执行 他的生命周期是在dev之前执行，然后执行dev命令，再然后执行postdev，也就是dev之后执行

运用场景例如npm run build 可以在打包之后删除dist目录等等post例如你编写完一个工具发布npm，那就可以在之后写一个ci脚本顺便帮你推送到git等等
谁用到了例如vue-cli
https://github.com/vuejs/vue-cli/blob/dev/[package.json](https://so.csdn.net/so/search?q=package.json&spm=1001.2101.3001.7020)

![](https://img-blog.csdnimg.cn/img_convert/610c086da7c404d4ce55f93ad879729c.png)