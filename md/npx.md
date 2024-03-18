# npx

### npx是什么

npx是一个命令行工具，它是npm 5.2.0版本中新增的功能。它允许用户在不安装全局包的情况下，运行已安装在本地项目中的包或者远程仓库中的包。

npx的作用是在命令行中运行node包中的可执行文件，而不需要全局安装这些包。这可以使开发人员更轻松地管理包的依赖关系，并且可以避免全局污染的问题。它还可以帮助开发人员在项目中使用不同版本的包，而不会出现版本冲突的问题。

npx 的优势

1. 避免全局安装：npx允许你执行npm package，而不需要你先全局安装它。

2. 总是使用最新版本：如果你没有在本地安装相应的npm package，npx会从npm的package仓库中下载并使用最新版。
3. 执行任意npm包：npx不仅可以执行在package.json的scripts部分定义的命令，还可以执行任何npm package。
4. 执行GitHub gist：npx甚至可以执行GitHub gist或者其他公开的JavaScript文件。

#### [npm](https://so.csdn.net/so/search?q=npm&spm=1001.2101.3001.7020) 和 npx 区别

`npx`侧重于执行命令的，执行某个模块命令。虽然会自动安装模块，但是重在执行某个命令

`npm`侧重于安装或者卸载某个模块的。重在安装，并不具备执行某个模块的功能。

#### 示例

https://create-react-app.bootcss.com/docs/getting-started

![https://img-blog.csdnimg.cn/img_convert/137d4299a771ae15f73b08e0c6edf53e.png](https://img-blog.csdnimg.cn/img_convert/137d4299a771ae15f73b08e0c6edf53e.png)

例如创建一个react项目 在之前需要安装到全局

```js
npm install -g create-react-app
```

然后执行 create-react-app my-app 这样的话会有两个问题

- 首先需要全局安装这个包占用磁盘空间
- 并且如果需要更新还得执行更新命令

#### 示例2

```js
npm ls -g 查看全局安装的包
```

![](https://img-blog.csdnimg.cn/img_convert/1d6a78863c4c58394c3a962626365a6f.png)

我全局并没有安装vite

当前项目安装vite

```
npm i vite -D
```

![](https://img-blog.csdnimg.cn/img_convert/cb9301b047d676925597c26e3fbab717.png)

安装完成之后发现无法执行运行vite命令

这时候就可以使用`npx vite` 了

![](https://img-blog.csdnimg.cn/img_convert/224a48d1b3dd04c4a560b34d815753d4.png)

npx 的运行规则和npm 是一样的 本地目录查找.bin 看有没有 如果没有就去全局的node_moduels 查找，如果还没有就去下载这个包然后运行命令，然后删除这个包