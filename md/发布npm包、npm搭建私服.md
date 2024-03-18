# 发布npm包、npm搭建私服

### 发布npm包

1. 创建一个npm账号并登录
2. 登录过后使用npm publish发布包(403)说明包名被占用

##### 发布npm的包的好处是什么

- 方便团队或者跨团队共享代码，使用npm包就可以方便的管理，并且还可以进行版本控制
- 做开源造轮子必备技术，否则你做完的轮子如何让别人使用难道是U盘拷贝？
- 面试题我面字节的时候就问到了这个
- 增加个人IP 让更多的人知道你的技术能力和贡献

##### 发布前准备工作

```js
npm adduser
```

首先先检查一下是否是npm源然后创建一个npm账号

![https://img-blog.csdnimg.cn/img_convert/0d50697f7ce9ebebec8244f0f0946e54.png](https://img-blog.csdnimg.cn/img_convert/0d50697f7ce9ebebec8244f0f0946e54.png)

创建完成之后使用npm login 登录账号

![](https://img-blog.csdnimg.cn/img_convert/0c04be817572beaf7f563a88a8ec9824.png)

登录完成之后使用`npm publish` 发布npm包

![](https://img-blog.csdnimg.cn/img_convert/6395d7400d574360d34a04037fdef90f.png)

发布成功 如果出现[403](https://so.csdn.net/so/search?q=403&spm=1001.2101.3001.7020)说明包名被占用了

![](https://img-blog.csdnimg.cn/img_convert/9238d32cc2db7e0d9b56f94d7de4e67e.png)

### 搭建npm私服

npm publish构建私服有什么收益吗？

- 可以离线使用，你可以将npm私服部署到内网集群，这样离线也可以访问私有的包。

- 提高包的安全性，使用私有的npm仓库可以更好的管理你的包，避免在使用公共的npm包的时候出现漏洞。
- 提高包的下载速度，使用私有 npm 仓库，你可以将经常使用的 npm 包缓存到本地，从而显著提高包的下载速度，减少依赖包的下载时间。这对于团队内部开发和持续集成、部署等场景非常有用

#### 如何搭建npm 私服

https://verdaccio.org/zh-CN/

Verdaccio 是可以帮我们快速构建npm私服的一个工具

```js
npm install verdaccio -g
```

使用方式非常简单

verdaccio 直接运行即可

###### 基本命令

```
#创建账号
npm adduser --registry http://localhost:4873/

# 账号 密码 邮箱
```

```
# 发布npm

npm publish --registry http://localhost:4873/
```

```
#指定开启端口 默认 4873
verdaccio --listen 9999
```

```
# 指定安装源
npm install --registry http://localhost:4873
```

```
# 从本地仓库删除包
npm unpublish <package-name> --registry http://localhost:4873
```